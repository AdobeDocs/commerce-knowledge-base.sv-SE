---
title: 'ACSD-46815: statisk innehållsdistribution misslyckas med kompakt strategi'
description: Använd patchen ACSD-46815 för att åtgärda Adobe Commerce-problemet där statisk innehållsdistribution misslyckas när kompakt strategi används.
exl-id: e94a0911-5cd9-4866-a027-7ea3239555d3
feature: Deploy, Page Content, SCD
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-46815: statisk innehållsdistribution misslyckas när kompakt strategi används

Korrigeringen ACSD-46815 åtgärdar ett problem där distributionen av statiskt innehåll misslyckas när den kompakta strategin används. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://support.magento.com/hc/en-us/articles/360047139492) 1.1.20 är installerat. Korrigerings-ID är ACSD-46815. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Statisk innehållsdistribution misslyckas vid distribution med en kompakt strategi.

<u>Steg som ska återskapas</u>:

1. Distribuera statiskt innehåll med en kompakt strategi genom att köra följande kommando:

```bash
bin/magento setup:static-content:deploy -f -s compact
```

<u>Förväntade resultat</u>:

Distributionen av statiskt innehåll slutförs utan fel.

<u>Faktiska resultat</u>:

Statisk innehållsdistribution misslyckas med en kompakt strategi. Följande fel inträffar under distributionsprocessen: *Innehållet från /app/pub/static/adminhtml/Magento/base/default/./node_modules/@spectrum-css/vars/dist/spectrum-global.css går inte att läsa filen.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
