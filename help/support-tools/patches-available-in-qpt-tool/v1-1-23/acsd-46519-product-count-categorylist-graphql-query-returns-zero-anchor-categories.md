---
title: '"ACSD-46519: [!UICONTROL product_count] in [!UICONTROL categoryList] [!DNL GraphQL] fråga returnerar 0 för ankarkategorier'
description: Använd korrigeringsfilen ACSD-46519 för att åtgärda Adobe Commerce-problemet där du använder [!UICONTROL categoryList] [!DNL GraphQL] metod för att hämta underordnade kategorier som visar [!UICONTROL product_count] som 0 för överordnade kategorier.
exl-id: b71be3e6-6235-4e96-848b-d61eda973d98
feature: Categories, GraphQL, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-46519: [!UICONTROL product_count] in [!UICONTROL categoryList] [!DNL GraphQL] fråga returnerar 0 för ankarkategorier

ACSD-46519- plåstret löser problemet där [!UICONTROL product_count] in [!UICONTROL categoryList] [!DNL GraphQL] frågan returnerar 0 för ankarkategorier. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 är installerat. Korrigerings-ID är ACSD-46519. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**
* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**
* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.5-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När [!UICONTROL categoryList] [!DNL GraphQL] -metoden används för att hämta underordnade kategorier som visar [!UICONTROL product_count] som 0 för överordnade kategorier.

<u>Steg som ska återskapas</u>:

1. Använd följande [!DNL GraphQL] förfrågan om att hämta kategorihierarkin med [!UICONTROL product_count]:

<pre><code>
{
  categoryList(filters: { ids: { eq: "2" } }) {
    id
    name
    product_count
    level
    children {
      name
      product_count
      level
      children {
        name
        product_count
        level
        children {
          name
          product_count
          level
          children {
            name
            product_count
            level
          }
        }
      }
    }
  }
}
</code></pre>

<u>Förväntade resultat</u>:

Om den överordnade kategorin är en förankrad kategori visas [!UICONTROL product_count] ska visa summan av antalet underordnade kategoriprodukter på alla nivåer.

<u>Faktiska resultat</u>:

Om den överordnade kategorin är en förankrad kategori visas produkterna som 0 för kategori 2 och nedåt.

<pre><code>
{
    "data": {
        "categoryList": [
            {
                "id": 2,
                "name": "Default Category",
                "product_count": 186,
                "level": 1,
                "children": [
                    {
                        "name": "What's New",
                        "product_count": 0,
                        "level": 2,
                        "children": []
                    },
                    {
                        "name": "Women",
                        "product_count": 0,
                        "level": 2,
                        "children": [
                            {
                                "name": "Tops",
                                "product_count": 0,
                                "level": 3,
                                "children": []
                            },
                            {
                                "name": "Bottoms",
                                "product_count": 0,
                                "level": 3,
                                "children": []
                            }
                        ]
                    },
                    ...
                ]
            }
        ]
    }
}
</code></pre>

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
