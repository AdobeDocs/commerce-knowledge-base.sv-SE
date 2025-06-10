---
title: Säkerhetsuppdatering för Adobe Commerce - [!DNL APSB25-50]
promoted: true
description: Använd en Isolated-korrigering för att åtgärda [!DNL critical and important vulnerabilities] för Adobe Commerce 2.4.8, 2.4.7-p5, 2.4.6-p10, 2.4.5-p12, 2.4.4-p13 och tidigare versioner.
feature: Compliance, Security
role: Developer
source-git-commit: 9df7dee77bec7ffe4323f21e44d555338a0b1934
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Säkerhetsuppdatering för Adobe Commerce - [!DNL APSB25-50]

Den 10 juni 2025 släppte Adobe en regelbundet schemalagd säkerhetsuppdatering för Adobe Commerce och Magento Open Source. Uppdateringen åtgärdar säkerhetsluckor i kategorierna [[!DNL critical]  och [!DNL important]](https://helpx.adobe.com/se/security/severity-ratings.html). Ett lyckat utnyttjande av dessa säkerhetsluckor kan leda till att säkerhetsfunktioner kringgås, eskalering av behörigheter och exekvering av godtycklig kod.

Mer information finns i [Adobe säkerhetsbulletin ([!DNL APSB25-50]) här](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

>[!NOTE]
>
>**För att åtgärda [!DNL CVE-2025-47110] som anges i säkerhetsbulletinen ovan så snabbt som möjligt har Adobe även släppt en isolerad korrigering som åtgärdar [!DNL CVE-2025-47110]. Detta gör att handlare kan tillämpa korrigeringen separat med färre risker för fördröjning på grund av potentiella integreringsproblem.**

**Använd de senaste säkerhetsuppdateringarna så snart som möjligt. Om du inte gör det kommer du att vara sårbar för dessa säkerhetsproblem, och Adobe har begränsade möjligheter att åtgärda problemet ytterligare.**

Du kan läsa mer om [vår isolerade process för distribution av korrigeringar här.](https://business.adobe.com/blog/introducing-enhanced-security-patch-deployment-and-communications-in-adobe-commerce)

>[!NOTE]
>
>För kunder som har Adobe Commerce på Managed Services kan din Customer Success Engineer ge ytterligare vägledning när det gäller att installera korrigeringsfilen.

>[!NOTE]
>
>Kontakta supporttjänsterna om du råkar ut för problem med säkerhetspatchen/den isolerade patchen.

Som påminnelse hittar du [de senaste säkerhetsuppdateringarna för Adobe Commerce här.](https://helpx.adobe.com/se/security/products/magento.html)

## Berörda produkter och versioner

Adobe Commerce (alla distributionsmetoder):

* 2.4.8
* 2.4.7-p5 och tidigare
* 2.4.6-p10 och tidigare versioner
* 2.4.5-p12 och tidigare versioner
* 2.4.4-p13 och tidigare versioner

## Problem

### I. CVE-2025-47110: Lagrad XSS via serversidesmallsinjektion i Adobe Commerce 2.4.7-p4

<u>Berörda produkter och versioner</u>:

Adobe Commerce (alla distributionsmetoder):

* 2.4.8
* 2.4.7-p5 och tidigare
* 2.4.6-p10 och tidigare versioner
* 2.4.5-p12 och tidigare versioner
* 2.4.4-p13 och tidigare versioner

<u>Lösning</u>:

För Adobe Commerce:

* 2.4.8
* 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3, 2.4.7-p4, 2.4.7-p5
* 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8, 2.4.6-p10
* 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10 0.4.5-p11, 2.4.5-p12
* 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p10 2.4.4-p11, 2.4.4-p12, 2.4.4-p13

**Använd följande isolerade korrigering eller uppgradering för den senaste säkerhetspatchen.**

* **[VULN-31609_2.4.X.patch](assets/VULN-31609_2.4.X_patch.zip)**

### II. VULN-31547: Speglad XSS i marketplace.magento.com + enklicksfel (ATO) som påverkar IMS-instanser

<u>Berörda produkter och versioner</u>:

Adobe Commerce (alla distributionsmetoder):

* 2.4.8

<u>Lösning</u>:

För Adobe Commerce:

* 2.4.8

**Använd följande isolerade korrigering eller uppgradering för den senaste säkerhetspatchen.**

* **[VULN-31547_2.4.8.patch](assets/VULN-31547_2.4.8_patch.zip)**

## Så här applicerar du det isolerade plåstret

Zippa upp filen och se [Använda en kompositkorrigering från Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=sv-SE) i vår kunskapsbas för support för instruktioner.

## Endast för Adobe Commerce på molnhandlare - Hur du ser om de isolerade korrigeringarna har tillämpats

Eftersom det inte är enkelt att kontrollera om problemet har åtgärdats, kanske du vill kontrollera om den isolerade korrigeringen [!DNL CVE-2025-47110] har tillämpats.

>[!NOTE]
>
><u>Du kan göra detta genom att utföra följande steg, med filen `VULN-27015-2.4.7_COMPOSER.patch` **som EXEMPEL**</u>:

1. [Installera verktyget för kvalitetskorrigeringar](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE).
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

* [Adobe säkerhetsbulletin ([!DNL APSB25-50])](https://helpx.adobe.com/security/products/magento/apsb25-50.html)
* [De senaste säkerhetsuppdateringarna för Adobe Commerce](https://helpx.adobe.com/se/security/products/magento.html)
