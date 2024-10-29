---
title: Säkerhetsuppdatering för Adobe Commerce - [!DNL APSB24-73]
promoted: true
description: Använd en isolerad korrigering för att åtgärda [!DNL critical, important, and moderate vulnerabilities] för Adobe Commerce 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10 och tidigare versioner av instanser som bara körs i modulen  [!DNL B2B] .
feature: Compliance, Security
role: Developer
source-git-commit: 483589be81e55f818f5cf93cccff2ffcbb5763cf
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Säkerhetsuppdatering för Adobe Commerce - [!DNL APSB24-73]

Den 8 oktober 2024 släppte Adobe en regelbundet schemalagd säkerhetsuppdatering för Adobe Commerce och [!DNL Adobe Commerce Webhooks Plugin].
Uppdateringen åtgärdar säkerhetsluckorna [[!DNL critical, important] och  [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html). Ett lyckat utnyttjande kan leda till exekvering av godtycklig kod, läsning av godtyckliga filsystem, åsidosättande av säkerhetsfunktioner och eskalering av behörigheter. Bulletinen är [Säkerhetsbulletin för Adobe ([!DNL APSB24-73])](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

>[!NOTE]
>
>**[!DNL CVE-2024-45115], som listas i säkerhetsbulletinen ovan, är bara tillämpligt när du använder modulen [!DNL B2B].** För att åtgärda problemet så snabbt som möjligt har Adobe också släppt en Isolerad korrigering som åtgärdar [!DNL CVE-2024-45115].

**Använd de senaste säkerhetsuppdateringarna så snart som möjligt. Om du inte gör det kommer du att vara sårbar för de här säkerhetsproblemen och Adobe har begränsade möjligheter att åtgärda dem.**

>[!NOTE]
>
>Kontakta supporttjänsterna om du råkar ut för problem med säkerhetspatchen/den isolerade patchen.

## Berörda produkter och versioner

Adobe Commerce i molnet och Adobe Commerce lokalt:

* 2.4.7-p2 och tidigare
* 2.4.6-p7 och tidigare
* 2.4.5-p9 och tidigare
* 2.4.4-p10 och tidigare versioner

B2B:

* 1.4.2-p2 och tidigare
* 1.3.5-p7 och tidigare
* 1.3.4-p9 och tidigare
* 1.3.3-p10 och tidigare versioner


## Lösning för Adobe Commerce i molnet och Adobe Commerce lokala programvara

För att åtgärda säkerhetsluckan för de berörda produkterna och versionerna måste du använda den isolerade korrigeringen [!DNL CVE-2024-45115].

## Information om isolerad lagning

Använd följande Isolerade plåster:

[vuln-26510-composer-patch.zip](assets/vuln-26510-composer-patch.zip)

## Så här applicerar du det isolerade plåstret

Zippa upp filen och se [Använda en kompositkorrigering från Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) i vår kunskapsbas för support för instruktioner.

## Endast för Adobe Commerce på molnhandlare - Hur du ser om de isolerade korrigeringarna har tillämpats

Eftersom det inte är enkelt att kontrollera om problemet har åtgärdats, kanske du vill kontrollera om den isolerade korrigeringen för [!DNL CVE-2024-45115] har tillämpats.

<u>Du kan göra detta genom att utföra följande steg, med filen `VULN-27015-2.4.7_COMPOSER.patch` **som exempel**</u>:

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

* [Säkerhetsbulletin för Adobe ([!DNL APSB24-73])](https://helpx.adobe.com/security/products/magento/apsb24-73.html)
