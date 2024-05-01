---
title: "MDVA-42806: Nytt e-postmeddelande om företagsregistrering skickas varje gång ett befintligt företag uppdateras"
description: MDVA-42806-korrigeringen löser problemet där ett nytt e-postmeddelande om företagsregistrering skickas varje gång ett befintligt företag uppdateras via REST API. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 är installerat. Korrigerings-ID är MDVA-42806. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 957b89f7-cd4d-4c94-8d1d-c30442aafa6a
feature: REST, B2B, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# MDVA-42806: Nytt e-postmeddelande om företagsregistrering skickas varje gång ett befintligt företag uppdateras

MDVA-42806-korrigeringen löser problemet där ett nytt e-postmeddelande om företagsregistrering skickas varje gång ett befintligt företag uppdateras via REST API. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 är installerat. Korrigerings-ID är MDVA-42806. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett nytt e-postmeddelande om företagsregistrering skickas varje gång ett befintligt företag uppdateras via REST API.

<u>Förutsättningar</u>:

B2B-moduler är installerade.

<u>Steg som ska återskapas</u>:

1. Skapa ett företag.
1. Använd `/V1&#x200B;/company&#x200B;/<company_id>` slutpunkt. Information om hur du uppdaterar det skapade företaget finns i [uppdatera företaget](https://devdocs.magento.com/guides/v2.4/b2b/company-object.html#update-the-company) i vår dokumentation för utvecklare. Nedan visas ett exempel på nyttolast:

```php
{
    "company": {
        "id": 2,
        "status": 1,
        "company_name": "Company",
        "company_email": "company@example.test",
        "street": [
            "Test"
        ],
        "city": "Test",
        "country_id": "US",
        "region_id": "1",
        "postcode": "12345",
        "telephone": "8009994301",
        "customer_group_id": 2,
        "sales_representative_id": 1,
        "super_user_id": 2
    }
}
```

<u>Förväntade resultat</u>:

Inget e-postmeddelande skickas med meddelandet&quot;Ny registreringsbegäran&quot; eftersom API:t uppdaterar ett befintligt företag.

<u>Faktiska resultat</u>:

Ett e-postmeddelande med texten&quot;Ny registreringsbegäran&quot; skickas varje gång API-begäran skickas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
