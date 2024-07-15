---
title: Fel vid installation av valfria exempeldata
description: I det här avsnittet beskrivs lösningar på fel som kan uppstå när du installerar valfria exempeldata.
exl-id: 14692e3a-188c-45f1-9df5-ac873cc9eff0
feature: Console, Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Fel vid installation av valfria exempeldata

I det här avsnittet beskrivs lösningar på fel som kan uppstå när du installerar valfria exempeldata.

## Symptom (filsystembehörigheter)

Fel i konsolloggen vid installation av exempeldata med hjälp av installationsguiden:

```php
Module 'Magento_CatalogRuleSampleData':
[ERROR] exception 'Magento\Framework\Exception\LocalizedException' with message 'Can't create directory /var/www/html/magento2/generated/code/Magento/CatalogRule/Model/.' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Generator.php:103

(more)

Next exception 'ReflectionException' with message 'Class Magento\CatalogRule\Model\RuleFactory does not exist' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Reader/ClassReader.php:29

(more)
```

Dessa undantag beror på filsystemets behörighetsinställningar.

### Lösning

[Ange ägarskap och behörigheter för filsystemet igen](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) som en användare med `root`-behörighet.

## Symptom (produktionsläge)

Om du är inställd för [produktionsläge](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html) misslyckas installationen av exempeldata om du använder kommandot [magento sampledata:deploy](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/sample-data/composer-packages.html):

```php
PHP Fatal error: Uncaught TypeError: Argument 1 passed to Symfony\Component\Console\Input\ArrayInput::__construct() must be of the type array, object given, called in /<path>/vendor/magento/framework/ObjectManager/Factory/AbstractFactory.php on line 97 and defined in /<path>/vendor/symfony/console/Symfony/Component/Console/Input/ArrayInput.php:37
```

### Lösning

Installera inte exempeldata i produktionsläge. Växla till utvecklarläge, rensa några `var`-kataloger och försök igen.

Ange följande kommandon i den ordning som visas som ägare av [Adobe Commerce-filsystemet](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/file-system/overview.html):

```php
cd <magento_root>
bin/magento deploy:mode:set developer
rm -rf generated/code/* generated/metadata/*
bin/magento sampledata:deploy
```

## Symptom (säkerhet)

Vid installation av valfria exempeldata visas ett meddelande som liknar följande:

```php
PHP Fatal error: Call to undefined method Magento\Catalog\Model\Resource\Product\Interceptor::getWriteConnection() in /var/www/magento2/app/code/Magento/SampleData/Module/Catalog/Setup/Product/Gallery.php on line 144
```

### Lösning

Under installationen av exempeldata inaktiverar du SELinux med en resurs som:

* [www.ibm.com](https://www.ibm.com/docs/ja/ahts/4.0?topic=t-disabling-selinux)
* [CentOS-dokumentation](https://docs.centos.org/en-US/docs/)

## Symptom (framkallningsgren)

Andra fel visas, t.ex.:

```php
[Magento\Setup\SampleDataException] Error during sample data installation: Class Magento\Sales\Model\Service\OrderFactory does not exist
```

### Lösning

Det finns kända problem med att använda exempeldata i Adobe Commerce framkallningsgren. Använd huvudgrenen i stället. Du kan växla till huvudgrenen på följande sätt:

```php
cd <magento_root>
git checkout master
git pull origin master
```

## Symptom (max_execution_time)

Installationen avbryts innan exempeldatainstallationen har slutförts. Ett exempel följer:

```php
(more)

Module 'Magento_CustomerSampleData':
Installing data...
```

Exempeldatainstallationen slutförs inte.

Det här felet inträffar när den maximala konfigurerade körningstiden för dina PHP-skript överskrids. Eftersom exempeldata kan ta lång tid att läsa in kan du öka värdet under installationen.

### Lösning

Som en användare med `root`-behörighet kan du ändra `php.ini` för att öka värdet för `max_execution_time` till 600 eller mer. (600 sekunder är 10 minuter. Du kan öka värdet till vad du vill.) Du bör ändra tillbaka `max_execution_time` till dess tidigare värde när installationen har slutförts.

Om du är osäker på var `php.ini` finns anger du följande kommando:

```php
php --ini
```

Värdet för `Loaded Configuration File` är det `php.ini` som du måste ändra.

>[!NOTE]
>
>Vi är medvetna om att den här artikeln fortfarande kan innehålla programtermer som är branschstandard och som vissa kan finna rasistiska, sexistiska eller förtryckande och som kan få läsaren att känna sig sårad, traumatiserad eller ovälkommen. Adobe arbetar med att ta bort dessa villkor från vår kod, dokumentation och användarupplevelse.
