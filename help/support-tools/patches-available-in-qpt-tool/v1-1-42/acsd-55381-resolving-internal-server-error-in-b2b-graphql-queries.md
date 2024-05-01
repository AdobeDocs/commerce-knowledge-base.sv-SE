---
title: 'ACSD-55381: Åtgärdar fel vid begäran om konfigurerbara produktalternativguider från B2B-rekvisitionslistan'
description: Använd patchen ACSD-55381 för att åtgärda Adobe Commerce-problemet när ett internt serverfel inträffar under GraphQL-frågor för fälten "configurable_product_option_uid" och "configurable_product_option_value_uid" från en B2B-rekvisitionslista.
feature: GraphQL, B2B, Products
role: Admin, Developer
exl-id: 4e7edb8d-8be8-45c9-b9ba-ff329656312e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-55381: Åtgärdar fel vid begäran om konfigurerbara produktalternativguider från B2B-rekvisitionslistan

Korrigeringen ACSD-55381 åtgärdar ett problem där ett internt serverfel inträffar under GraphQL-frågor för `configurable_product_option_uid` och `configurable_product_option_value_uid` fält från en B2B-rekvisitionslista. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 är installerat. Korrigerings-ID är ACSD-55381. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett internt serverfel inträffar vid frågor `configurable_product_option_uid` och `configurable_product_option_value_uid` fält från en B2B-rekvisitionslista via GraphQL.

<u>Förutsättningar</u>:

1. Adobe Commerce B2B-moduler är installerade och aktiverade.
1. Rekvisitionslistan är aktiverad i konfigurationen.

<u>Steg som ska återskapas</u>:

1. Logga in som kund i butiken.
1. Lägg till en konfigurerbar produkt i en rekvisitionslista.
1. Försök att hämta värden för `configurable_product_option_uid` och `configurable_product_option_value_uid` fält med `getRequisitionList` i ett GraphQL-anrop.

```
query getRequisitionList {
  customer {
    requisition_lists(filter: { uids: { eq: "MQo=" } }) {
      items {
        items(pageSize: 1, currentPage: 1) {
          items {
            ... on ConfigurableRequisitionListItem {
              configurable_options {
                value_id
                id
                configurable_product_option_uid
                configurable_product_option_value_uid
              }
            }
          }
        }
      }
    }
  }
}
```

<u>Förväntade resultat</u>:

```
{
    "data": {
        "customer": {
            "requisition_lists": {
                "items": [
                    {
                        "items": {
                            "items": [
                                {
                                    "configurable_options": [
                                        {
                                            "value_id": 175,
                                            "id": 186,
                                            "configurable_product_option_uid": "MTg2",
                                            "configurable_product_option_value_uid": "MTc1"
                                        },
                                        {
                                            "value_id": 58,
                                            "id": 93,
                                            "configurable_product_option_uid": "OTM=",
                                            "configurable_product_option_value_uid": "NTg="
                                        }
                                    ]
                                }
                            ]
                        }
                    }
                ]
            }
        }
    }
}
```

<u>Faktiska resultat</u>:

Ett fel inträffar.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
