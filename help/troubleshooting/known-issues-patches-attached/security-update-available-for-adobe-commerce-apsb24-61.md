---
title: Säkerhetsuppdatering för Adobe Commerce - [!DNL APSB24-61]
promoted: true
description: Använd en Isolated-korrigering för att åtgärda [!DNL CVE-2024-39397] för Adobe Commerce 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10 och tidigare versioner med endast  [!DNL Apache].
feature: Compliance, Security
role: Developer
source-git-commit: 76ff7669a0a57925a176e08031e0789ced0a7f0e
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Säkerhetsuppdatering för Adobe Commerce - [!DNL APSB24-61]

Den 13 augusti 2024 släppte Adobe en regelbundet schemalagd säkerhetsuppdatering för Adobe Commerce, Magento Open Source och Adobe Commerce Webhooks Plugin.
Uppdateringen åtgärdar säkerhetsluckorna [[!DNL critical, important] och  [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html). Ett lyckat utnyttjande kan leda till exekvering av godtycklig kod, läsning av godtyckliga filsystem, åsidosättande av säkerhetsfunktioner och eskalering av behörigheter. Bulletinen är [Säkerhetsbulletin för Adobe ([!DNL APSB24-61])](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

>[!NOTE]
>
>**[!DNL CVE-2024-39397], som listas i säkerhetsbulletinen ovan, är bara tillgängligt när du använder webbservern [!DNL Apache].** För att åtgärda problemet så snabbt som möjligt har Adobe också släppt en Isolerad korrigering som åtgärdar [!DNL CVE-2024-39397].

**Använd de senaste säkerhetsuppdateringarna så snart som möjligt. Om du inte gör det kommer du att vara sårbar för de här säkerhetsproblemen och Adobe har begränsade möjligheter att åtgärda dem.**

>[!NOTE]
>
>Kontakta supporttjänsterna om du råkar ut för problem med säkerhetspatchen/den isolerade patchen.

## Berörda produkter och versioner

Adobe Commerce i molnet, Adobe Commerce lokalt och Magento Open Source:

* 2.4.7-p1 och tidigare versioner
* 2.4.6-p6 och tidigare
* 2.4.5-p8 och tidigare
* 2.4.4-p9 och tidigare

## Lösning för Adobe Commerce i molnet, Adobe Commerce lokala program och Magento Open Source

För att åtgärda säkerhetsluckan för de berörda produkterna och versionerna måste du använda den isolerade korrigeringen [!DNL CVE-2024-39397].

## Information om isolerad lagning

Använd följande Isolerade plåster:

* [acsd-60551-composer-patch.zip](assets/acsd-60551-composer-patch.zip)

## Så här applicerar du det isolerade plåstret

Zippa upp filen och se [Använda en kompositkorrigering från Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) i vår kunskapsbas för support för instruktioner.

## Endast för Adobe Commerce på molnhandlare - Hur du ser om de isolerade korrigeringarna har tillämpats

Eftersom det inte är enkelt att kontrollera om problemet har åtgärdats, kanske du vill kontrollera om den isolerade korrigeringen för [!DNL CVE-2024-39397] har tillämpats.

<u>Du kan göra detta genom att utföra följande steg, med filen `VULN-27015-2.4.7_COMPOSER.patch` som exempel</u>:

1. [Installera verktyget för kvalitetskorrigeringar](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Kör kommandot:<br>
   ![cve-2024-34102-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Du bör se utdata som liknar detta, där VULN-27015 returnerar statusen *Används*:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

## Säkerhetsuppdateringar

Säkerhetsuppdateringar för Adobe Commerce:

* [Säkerhetsbulletin för Adobe ([!DNL APSB24-61])](https://helpx.adobe.com/security/products/magento/apsb24-61.html)
