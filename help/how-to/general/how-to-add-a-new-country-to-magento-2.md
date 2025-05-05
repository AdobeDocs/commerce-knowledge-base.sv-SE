---
title: Så här lägger du till ett nytt land i Adobe Commerce
description: I den här artikeln beskrivs hur du lägger till ett land som inte finns i Adobe Commerce och Zend Locale Library. Detta kräver kod- och databasändringar som utgör kundanpassningar enligt dina tillämpliga avtalsvillkor. Observera att exempelmaterialet i den här artikeln tillhandahålls i befintligt skick utan någon garanti av något slag. Varken Adobe eller någon anknuten enhet är skyldig att underhålla, korrigera, uppdatera, ändra, modifiera eller på annat sätt stödja dessa material. Här kommer vi att beskriva de grundläggande principerna för vad som behöver göras för att uppnå detta.
exl-id: af499add-4966-4a3a-972a-62a34c169a1b
feature: Build, Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1105'
ht-degree: 0%

---

# Så här lägger du till ett nytt land i Adobe Commerce

I den här artikeln beskrivs hur du lägger till ett land som inte finns i Adobe Commerce och Zend Locale Library. Detta kräver kod- och databasändringar som utgör kundanpassningar enligt dina tillämpliga avtalsvillkor. Observera att exempelmaterialet i den här artikeln tillhandahålls i befintligt skick utan någon garanti av något slag. Varken Adobe eller någon anknuten enhet är skyldig att underhålla, korrigera, uppdatera, ändra, modifiera eller på annat sätt stödja dessa material. Här kommer vi att beskriva de grundläggande principerna för vad som behöver göras för att uppnå detta.

I det här exemplet skapar vi en ny Adobe Commerce-modul med en datakorrigering som tillämpas vid installation eller uppgradering av Adobe Commerce och lägger till ett abstrakt land med landskoden XX i Adobe Commerce. [Adobe Commerce-katalogen](https://developer.adobe.com/commerce/php/module-reference/module-directory/) skapar en lista med inledande länder och använder sedan konfigurationspatchar för att lägga till områden i listan. I den här artikeln beskrivs hur du skapar en ny modul som lägger till ett nytt land i listan. Du kan läsa koden för den befintliga Adobe Commerce Directory-modulen för referens. Detta beror på att följande exempelmodul fortsätter med katalogmodulens jobb att skapa en lista över länder och regioner och återanvänder delar av koden i Adobe Commerce Directory Module Setup Patches.

## Rekommenderad dokumentation

Du måste känna till Adobe Commerce modulutveckling för att kunna skapa en ny.

Läs följande avsnitt i utvecklardokumentationen innan du försöker skapa en ny modul:

* [Utvecklarhandbok för PHP](https://developer.adobe.com/commerce/php/development/)
* [Modulöversikt](https://developer.adobe.com/commerce/php/architecture/modules/overview/)
* [Skapa en ny modul](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/backend-development/create-module)
* [Modulkonfigurationsfiler](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/module-files)

## Nödvändig information

Ett nytt land måste ha ett unikt namn, lands-ID, ISO2- och ISO3-koder i hela Adobe Commerce.

## Modulstruktur

I det här exemplet ska vi skapa en ny modul med namnet \`Extracountries\` med följande katalogstruktur:

(Mer information om modulstrukturen finns i [Modulöversikt](https://developer.adobe.com/commerce/php/architecture/modules/overview/) i utvecklardokumentationen).

<pre>&lt;ExtraCountries>
 |
 &lt;etc>
 | |
 | config.xml
 | di.xml
 | module.xml
 |
 &lt;Plugin>
 | |
 | &lt;Framework>
 |   |
 |   &lt;Locale>
 |     |
 |     TranslatedListsPlugin.php
 |
 &lt;Setup>
 | |
 | &lt;Patch>
 |   |
 |   &lt;Data>
 |     |
 |     AddDataForAbstractCountry.php
 |
 disposition.json
 registration.php</pre>

>[!NOTE]
>
>Varje rubrikavsnitt i den här artikeln beskriver filer från modulstrukturavsnittet.

## ExtraCountries/etc/config.xml

En ny modulkonfiguration definieras i XML-filen. Följande konfigurationer och taggar kan redigeras för att justera de nya standardinställningarna för länder.

* `allow` - Om du vill lägga till det nyligen tillagda landet i listan&quot;Tillåt länder&quot; som standard, lägger du till den nya landskoden i slutet av tagginnehållet `allow` . Landskoder avgränsas med kommatecken. Observera att den här taggen skriver över data från `Directory`-modulens konfigurationsfil *(Directory/etc/config.xml)* `allow` -taggen. Därför upprepar vi alla koder här och lägger till den nya.
* `optional_zip_countries` - Om postnumret för det nyligen tillagda landet ska vara valfritt lägger du till landskoden i slutet av innehållet i `optional_zip_countries` -taggen. Landskoder avgränsas med kommatecken. Observera att den här taggen skriver över data från `Directory`-modulens konfigurationsfil *(Directory/etc/config.xml)* `optional_zip_countries` -taggen. Därför upprepar vi alla koder här och lägger till den nya.
* `eu_countries` - Om det nyligen tillagda landet måste vara en del av listan över EU-länder som standard lägger du till landskoden i slutet av innehållet i taggen `eu_countries` . Landskoder avgränsas med kommatecken. Observera att den här taggen skriver över data från `Store`-modulens konfigurationsfil *(\_Store/etc/config.xml\_)* `eu_countries` , vilket är orsaken till att alla koder här upprepas, plus att den nya koden läggs till.
* Exempel på filen `config.xml`

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <general>
            <country>
                <!-- append a new country codes to the end of this list -->
                <allow>AF,AL,DZ,AS,AD,AO,AI,AQ,AG,AR,AM,AW,AU,AT,AX,AZ,BS,BH,BD,BB,BY,BE,BZ,BJ,BM,BL,BT,BO,BQ,BA,BW,BV,BR,IO,VG,BN,BG,BF,BI,KH,CM,CA,CD,CV,KY,CF,TD,CL,CN,CX,CW,CC,CO,KM,CG,CK,CR,HR,CU,CY,CZ,DK,DJ,DM,DO,EC,EG,SV,GQ,ER,EE,ET,FK,FO,FJ,FI,FR,GF,PF,TF,GA,GM,GE,DE,GG,GH,GI,GR,GL,GD,GP,GU,GT,GN,GW,GY,HT,HM,HN,HK,HU,IS,IM,IN,ID,IR,IQ,IE,IL,IT,CI,JE,JM,JP,JO,KZ,KE,KI,KW,KG,LA,LV,LB,LS,LR,LY,LI,LT,LU,ME,MF,MO,MK,MG,MW,MY,MV,ML,MT,MH,MQ,MR,MU,YT,FX,MX,FM,MD,MC,MN,MS,MA,MZ,MM,NA,NR,NP,NL,AN,NC,NZ,NI,NE,NG,NU,NF,KP,MP,NO,OM,PK,PW,PA,PG,PY,PE,PH,PN,PL,PS,PT,PR,QA,RE,RO,RS,RU,RW,SH,KN,LC,PM,VC,WS,SM,ST,SA,SN,SC,SL,SG,SK,SI,SB,SO,ZA,GS,KR,ES,LK,SD,SR,SJ,SZ,SE,CH,SX,SY,TL,TW,TJ,TZ,TH,TG,TK,TO,TT,TN,TR,TM,TC,TV,VI,UG,UA,AE,GB,US,UM,UY,UZ,VU,VA,VE,VN,WF,EH,XK,YE,ZM,ZW,XX</allow>
​
                <!-- if added countries need to belong to the European Union Countries list by default, append their codes to the end of this list -->
                <eu_countries>AT,BE,BG,CY,CZ,DK,EE,FI,FR,DE,GR,HR,HU,IE,IT,LV,LT,LU,MT,NL,PL,PT,RO,SK,SI,ES,SE,GB,XX</eu_countries>
​
                <!-- if added countries are not require zip code, append it's code to the end of this list -->
                <optional_zip_countries>HK,IE,MO,PA,GB,XX</optional_zip_countries>
            </country>
        </general>
    </default>
</config>
```

Mer information om modulkonfigurationsfilerna finns i [PHP-utvecklarhandboken > Definiera konfigurationsfiler](https://developer.adobe.com/commerce/php/development/build/required-configuration-files/) i utvecklardokumentationen.

Observera att dessa ändringar är valfria och endast kommer att påverka standardinställningen i det nya landet i listorna&quot;Tillåt länder&quot;,&quot;Postnummer är valfritt&quot; och&quot;EU-länder&quot;. Om den här filen hoppas över från modulstrukturen kommer ett nytt land fortfarande att läggas till, men det måste konfigureras manuellt på sidan **Admin** > **Lagrar** > *Inställningar* > **Konfiguration** > **Allmänt** > **Inställningar för landsalternativ** .

### ExtraCountries/etc/di.xml

Filen `di.xml` konfigurerar vilka beroenden som matas in av objekthanteraren. Mer information om `di.xml` finns i <a>PHP Developer Guide > The di.xml</a> i vår utvecklardokumentation.

I vårt exempel måste vi registrera en `_TranslatedListsPlugin_` som översätter nyligen införda landskoder till fullständiga landsnamn, om det inte finns några koder i lokaliseringsdata för Zend Locale-biblioteket.

`di.xml`-exempel

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\Framework\Locale\TranslatedLists">
        <plugin name="Magento_Directory" type="VendorName\ExtraCountries\Plugin\Framework\Locale\TranslatedListsPlugin"/>
    </type>
</config>
```

### ExtraCountries/etc/module.xml

I modulregistreringsfilen måste vi ange beroendet för modulen&quot;Adobe Commerce-katalog&quot; så att modulen&quot;Extra countries&quot; registreras och körs efter modulen Katalog.

Mer information om modulberoenden finns i [Hantera modulberoenden](https://developer.adobe.com/commerce/php/architecture/modules/dependencies/#managing-module-dependencies) i utvecklardokumentationen.

`module.xml`-exempel

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
    <module name="VendorName_ExtraCountries" >
        <sequence>
            <module name="Magento_Directory"/>
        </sequence>
    </module>
</config>
```

### ExtraCountries/Plugin/Framework/Locale/TranslatedListsPlugin.php

I plugin-metoden `aroundGetCountryTranslation()` måste vi översätta en landskod till ett fullständigt landsnamn. Detta är ett obligatoriskt steg för länder som inte har ett fullständigt namn kopplat till en ny landskod i Zend Locale Library.

```php
<?php
namespace VendorName\ExtraCountries\Plugin\Framework\Locale;
​
use Magento\Framework\Locale\ListsInterface;
​
/**
 * Plugin to add full names of added countries that are not included in Zend Locale Data
 */
class TranslatedListsPlugin
{
    /**
     * Get the full name of added countries
     *
     * Since the locale data for the added country may not be present in the Zend Locale Library,
     * we need to provide full country name matching the added code
     *
     * @param ListsInterface $subject
     * @param callable $proceed
     * @param $value
     * @param null $locale
     * @return string
     */
    public function aroundGetCountryTranslation(
        ListsInterface $subject,
        callable $proceed,
        $value,
        $locale = null
    )
    {
        if ($value == 'XX') {
            return 'Abstract Country';
        }
​
        return $proceed($value, $locale);
    }
}
```

### ExtraCountries/Setup/Patch/Data/AddDataForAbstractCountry.php

Den här datakorrigeringen utförs under Adobe Commerce installations-/uppgraderingsprocess och en ny landspost läggs till i databasen.

Mer information om datapatchar finns i [Utveckla data och schemapatchar](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) i utvecklardokumentationen.

I exemplet nedan kan du se att arrayen `$data` för metoden `apply()` innehåller lands-ID, ISO2- och ISO3-koder för det nya landet, och dessa data infogas i databasen.

```php
<?php
namespace Magento\ExtraCountries\Setup\Patch\Data;
​
use Magento\Framework\Setup\ModuleDataSetupInterface;
use Magento\Framework\Setup\Patch\DataPatchInterface;
use Magento\Framework\Setup\Patch\PatchVersionInterface;
​
/**
 * Add Abstract Country data to the country list
 *
 * @package Magento\ExtraCountries\Setup\Patch
 */
class AddDataForAbstractCountry implements DataPatchInterface, PatchVersionInterface
{
    /**
     * @var ModuleDataSetupInterface
     */
    private $moduleDataSetup;
​
    /**
     * @param ModuleDataSetupInterface $moduleDataSetup
     */
    public function __construct(
        ModuleDataSetupInterface $moduleDataSetup
    ) {
        $this->moduleDataSetup = $moduleDataSetup;
    }
​
    /**
     * @inheritdoc
     */
    public function apply()
    {
        /**
         * Fill table directory/country
         */
        $data = [
            ['XX', 'XX', 'XX']
        ];
​
        $columns = ['country_id', 'iso2_code', 'iso3_code'];
        $this->moduleDataSetup->getConnection()->insertArray(
            $this->moduleDataSetup->getTable('directory_country'),
            $columns,
            $data
        );
    }
​
    /**
     * @inheritdoc
     */
    public static function getDependencies()
    {
        return [];
    }
​
    /**
     * @inheritdoc
     */
    public static function getVersion()
    {
        return '0.0.1';
    }
​
    /**
     * @inheritdoc
     */
    public function getAliases()
    {
        return [];
    }
}
```

### ExtraCountries/registration.php

Detta är ett exempel på filen registration.php. Mer information om modulregistrering finns i [PHP Developer Guide > Registrera din komponent](https://developer.adobe.com/commerce/php/development/build/component-registration/) i utvecklardokumentationen.

```php
<?php
use Magento\Framework\Component\ComponentRegistrar;
​
ComponentRegistrar::register(ComponentRegistrar::MODULE, 'VendorName_ExtraCountries', __DIR__);
```

### ExtraCountries/composer.json

Det här är ett exempel på filen Composer.json.

Mer information om Composer.json finns i [PHP Developer Guide > Filen Composer.json ](https://developer.adobe.com/commerce/php/development/build/composer-integration/) i utvecklardokumentationen.

```json
{
    "name": "vendor_name/module-extra-countries",
    "description": "A module that adds extra countries to magento directory",
    "type": "magento2-module",
    "license": [
    ],
    "require": {
        "php": "~7.3.0||~7.4.0",
        "lib-libxml": "*",
        "magento/framework": "*",
        "magento/module-directory": "*"
    },
    "autoload": {
        "files": [
            "registration.php"
        ],
        "psr-4": {
            "VendorName\\ExtraCountries\\": ""
        }
    },
    "config": {
        "sort-packages": true
    }
}
```

## Modulinstallation

Mer information om hur du installerar modulen finns i [Modulplatser](https://developer.adobe.com/commerce/php/architecture/modules/overview/#module-locations) i utvecklardokumentationen.

När modulkatalogen har placerats på rätt plats kör du `bin/magento setup:upgrade` för att tillämpa datapatcharna och registrera översättnings-plugin-programmet.

Du kan behöva rensa webbläsarens cache för att de nya ändringarna ska fungera.
