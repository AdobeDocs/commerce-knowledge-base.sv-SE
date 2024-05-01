---
title: 'ACSD-51630: Många systemmeddelanden tar lång tid att hämta administratörssidor'
description: Använd korrigeringsfilen ACSD-51630 för att åtgärda prestandaproblem i Adobe Commerce där en stor mängd systemmeddelanden gör att det går långsammare att hämta administratörssidor.
feature: Admin Workspace, System
role: Admin
exl-id: 28f85199-625e-4299-bbca-8d2fc75df602
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# ACSD-51630: Många systemmeddelanden tar lång tid att hämta administratörssidor

Korrigeringen ACSD-51630 åtgärdar ett prestandaproblem där ett stort antal systemmeddelanden gör att hämtningen av administratörssidor går långsammare. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.34 är installerat. Korrigerings-ID är ACSD-51630. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 &lt; 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Många systemmeddelanden tar lång tid att hämta administratörssidor

<u>Steg som ska återskapas</u>:

1. Gör ett stort antal förfrågningar (~50 kB) till DELETE `/rest/async/v1/products/ {sku}`.
1. Åtkomst till alla **Administratörssida**.

<u>Förväntade resultat</u>:

Sidan läses in vid en lämplig tidpunkt. Endast meddelanden som visas ska läsas in.

<u>Faktiska resultat</u>:

Det tar för lång tid att läsa in sidan. Alla befintliga meddelanden läses in från databasen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
