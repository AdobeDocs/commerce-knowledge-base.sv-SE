---
title: Felet "Klassen kan inte sparas i kodkatalogen"
description: I den här artikeln beskrivs hur du åtgärdar ett problem där du angav beroenden som förhindrar att klasser genereras automatiskt i farten, och du får felmeddelandet *"Klassen kan inte sparas i den genererade katalogen/kodkatalogen"*.
exl-id: e2c00d4d-31c3-4446-a317-a8ac92c707d5
feature: Configuration
role: Developer
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Felet &quot;Klassen kan inte sparas i kodkatalogen&quot;

I den här artikeln beskrivs hur du åtgärdar problemet där det sätt som du angav beroenden förhindrar att klasser genereras automatiskt i farten, och du får felmeddelandet *&quot;Klassen kan inte sparas i den genererade katalogen/kodkatalogen&quot;*.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur 2.2.0 eller senare

## Problem

<u>Steg som ska återskapas</u>

1. I den lokala miljön skriver du en anpassad klass med ett beroende på den automatiskt genererade klassen.
1. Kör scenariot, där din anpassade klass aktiveras, och se hur den fungerar korrekt.
1. Genomför och överför ändringarna till integreringsmiljön. Detta skulle utlösa distributionsprocessen. Distributionen har slutförts.
1. Kör scenariot där din anpassade klass utlöses i [integreringsmiljön](https://experienceleague.adobe.com/sv/docs/experience-cloud-kcs/kbarticles/ka-27242).

<u>Förväntat resultat</u>

Allt fungerar korrekt, på samma sätt som i din lokala miljö.

<u>Faktiskt resultat</u>

Ett fel uppstod när felmeddelandet om att din klass inte kan sparas i katalogen `generated/code` visades.

## Orsak

Orsaken till problemet är att klassen som du är beroende av inte genereras under distributionen och inte kan genereras senare när klassen aktiveras, eftersom katalogen `generated/code` inte kan skrivas när distributionen är klar.

Det finns två huvudorsaker till detta:

* Fall 1: Klassen med beroenden för automatiskt genererade klasser finns i startpunkten (som `index.php` ), som inte genomsöks efter beroenden under distributionen.
* Fall 2: Beroendet till den automatiskt genererade klassen anges direkt (jämfört med den rekommenderade användningen av konstruktorn för att deklarera beroende).

## Lösning

En vanlig lösning för båda fallen är att skapa en riktig fabrik i stället för den automatiskt genererade klassen.

Eller så finns det en speciell lösning för varje fall.

### Specifik lösning för fall 1

Flytta klasskoden från startpunkten till en separat modul och använd den sedan i startpunkten.

<u>Exempel</u>

Ursprunglig kod i, till exempel, `index2.php` :

```php
<?php
use YourVendor\SomeModule\Model\GeneratedFactory;

require realpath(__DIR__) . '/../app/bootstrap.php';
$bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);

class SomeClass
{
    private $generatedFactory;

    public function __construct(GeneratedFactory $generatedFactory)
    {
        $this->generatedFactory = $generatedFactory;
    }

// Some code here...
}

$someObject = $bootstrap->getObjectManager()->create(SomeClass::class);

// There is some code that uses $someObject
```

Du måste göra följande:

1. Flytta klassdefinitionen till `app/code/YourVendor/YourModule`:

   ```php
      <?php
       namespace YourVendor\YourModule;
       use YourVendor\YourModule\Model\GeneratedFactory;
       class YourClass
       {
           private $generatedFactory;
   
           public function __construct(GeneratedFactory $generatedFactory)
           {
               $this->generatedFactory = $generatedFactory;
           }
       // Some code here...
       }
   ```

1. Redigera startpunkten `my_api/index.php` så att den ser ut så här:

   ```php
     <?php
     use YourVendor\YourModule\YourClass;
         require realpath(__DIR__) . '/../app/bootstrap.php';
         $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
         $someObject = $bootstrap->getObjectManager()->create(YourClass::class);
     // Some code using $someObject
   ```

### Specifik lösning för fall 2

Flytta beroendedeklarationen till konstruktorn.

<u>Exempel</u>

Ursprunglig klassdeklaration:

```php
<?php
namespace YourVendor\YourModule;

use YourVendor\SomeModule\Model\GeneratedFactory;
use Magento\Framework\App\ObjectManager;

class YourClass
{
    private $generatedFactory;
    private $someParam;

    public function __construct($someParam)
    {
        $this--->someParam = $someParam;
        $this->generatedFactory = ObjectManager::getInstance()->get(GeneratedFactory::class);
    }

    // Some code here...
}
```

Du måste ändra konstruktorn så här:

```php
<?php
namespace YourVendor\YourModule;

use YourVendor\YourModule\Model\GeneratedFactory;
use Magento\Framework\App\ObjectManager;

class YourClass
{
    private $generatedFactory;
    private $someParam;

    public function __construct($someParam, GeneratedFactory $generatedFactory = null)
    {
        $this->someParam = $someParam;
        $this->generatedFactory = $generatedFactory ?: ObjectManager::getInstance()->get(GeneratedFactory::class);
    }

    // Some code here...
}
```

## Relaterad läsning

* [Kodgenerering](https://developer.adobe.com/commerce/php/development/components/code-generation/) i utvecklardokumentationen.
