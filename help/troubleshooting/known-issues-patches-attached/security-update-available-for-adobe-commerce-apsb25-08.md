---
title: Säkerhetsuppdatering för Adobe Commerce - [!DNL APSB25-08]
promoted: true
description: Använd en Isolated-korrigering för att åtgärda [!DNL critical, important, and moderate vulnerabilities] för Adobe Commerce 2.4.8-beta1, 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11 och tidigare versioner.
feature: Compliance, Security
role: Developer
exl-id: 567e6ad2-704e-461f-a54d-75f6bd96e996
source-git-commit: f4a7a6ac538cf1199aea32875215709fcd165a08
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Säkerhetsuppdatering för Adobe Commerce - [!DNL APSB25-08]

11 februari 2025 publicerade Adobe en regelbundet schemalagd säkerhetsuppdatering för Adobe Commerce och Magento Open Source. Uppdateringen åtgärdar säkerhetsluckorna [[!DNL critical, important] och  [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html). Ett lyckat utnyttjande av dessa säkerhetsluckor kan leda till exekvering av godtycklig kod, åsidosättande av säkerhetsfunktioner och eskalering av behörigheter. Mer information finns i [Adobe säkerhetsbulletin ([!DNL APSB25-08]) här](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

>[!NOTE]
>
>**För att åtgärda [!DNL CVE-2025-24434], som listas i säkerhetsbulletinen ovan, så snabbt som möjligt har Adobe även släppt en isolerad korrigering som löser [!DNL CVE-2025-24434]. Detta gör att handlare kan tillämpa korrigeringen separat med färre risker för fördröjning på grund av potentiella integreringsproblem.**

**Använd de senaste säkerhetsuppdateringarna så snart som möjligt. Om du inte gör det kommer du att vara sårbar för dessa säkerhetsproblem, och Adobe har begränsade möjligheter att åtgärda problemet ytterligare.**

>[!NOTE]
>
>Kontakta supporttjänsterna om du råkar ut för problem med säkerhetspatchen/den isolerade patchen.

## Berörda produkter och versioner

Adobe Commerce i molninfrastrukturen, Adobe Commerce lokalt och Magento Open Source:

* 2.4.8-beta1 och tidigare
* 2.4.7-p3 och tidigare
* 2.4.6-p8 och tidigare
* 2.4.5-p10 och tidigare versioner
* 2.4.4-p11 och tidigare versioner

## ## Lösning för Adobe Commerce i molnet, Adobe Commerce lokalt och Magento Open Source

För att åtgärda säkerhetsluckan för de berörda produkterna och versionerna måste du tillämpa den isolerade korrigeringen [!DNL CVE-2025-24434], beroende på vilken version av Adobe Commerce/Magento Open Source du har.

## Information om isolerad lagning

Använd följande bifogade Isolerade patchar, beroende på vilken version av Adobe Commerce/Magento Open Source du har:

### För version 2.4.8-beta1:

* [vuln-28982-2-4-8x-v2-composer-patch.zip](assets/vuln-28982-2-4-8x-v2-composer-patch.zip)

### För version 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3:

* [vuln-28982-2-4-7x-v2-composer-patch.zip](assets/vuln-28982-2-4-7x-v2-composer-patch.zip)

### För versionerna 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8:

* [vuln-28982-2-4-6x-v2-composer-patch.zip](assets/vuln-28982-2-4-6x-v2-composer-patch.zip)

### För version 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10:

* [vuln-28982-2-4-5x-v2-composer-patch.zip](assets/vuln-28982-2-4-5x-v2-composer-patch.zip)

### För version 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p1 0, 2.4.4-p11:

* [vuln-28982-2-4-4x-v2-composer-patch.zip](assets/vuln-28982-2-4-4x-v2-composer-patch.zip)


## Så här applicerar du det isolerade plåstret

Zippa upp filen och se [Använda en kompositkorrigering från Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) i vår kunskapsbas för support för instruktioner.

## Endast för Adobe Commerce på molnhandlare - Hur du ser om de isolerade korrigeringarna har tillämpats

Eftersom det inte är enkelt att kontrollera om problemet har åtgärdats, kanske du vill kontrollera om den isolerade korrigeringen för [!DNL CVE-2025-24434] har tillämpats.

>[!NOTE]
>
><u>Du kan göra detta genom att utföra följande steg, med filen `VULN-27015-2.4.7_COMPOSER.patch` **som exempel**</u>:

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

* [Adobe säkerhetsbulletin ([!DNL APSB25-08])](https://helpx.adobe.com/security/products/magento/apsb25-08.html)
* [De senaste säkerhetsuppdateringarna för Adobe Commerce)](https://helpx.adobe.com/security/products/magento.html)
