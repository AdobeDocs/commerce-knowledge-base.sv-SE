---
title: 'ACSD-53790: Flera RMA:er för en enskild produkt kan skapas via Rest API'
description: Använd korrigeringsfilen ACSD-53790 för att åtgärda Adobe Commerce-problemet där flera RMA-filer för en enskild produkt kan skapas via Rest API.
feature: REST, Products
role: Admin, Developer
exl-id: abb0c3d0-0f0d-4012-99c8-e97e81dba8c8
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# ACSD-53790: Flera RMA:er för en enskild produkt kan skapas via Rest API

Korrigeringsfilen ACSD-53790 åtgärdar ett problem där flera RMA-filer för en enskild produkt kan skapas via *Resterande API*. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 är installerat. Korrigerings-ID är ACSD-53790. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Flera RMA:er för en enskild produkt kan skapas via *Resterande API*.

<u>Steg som ska återskapas</u>:

1. Beställ.
1. Fakturera och skicka ordern.
1. Skapa RMA med REST-slutpunkten.
1. Skapa samma RMA med REST-slutpunkten.

<u>Förväntade resultat</u>:

Ett valideringsfel visas i stället för att en dubblett-RMA skapas.

<u>Faktiska resultat</u>:

Samma RMA skapas av REST-slutpunkten.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
