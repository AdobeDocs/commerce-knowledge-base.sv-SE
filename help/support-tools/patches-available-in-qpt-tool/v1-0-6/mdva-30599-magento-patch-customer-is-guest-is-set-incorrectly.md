---
title: 'MDVA-30599: customer_is_gäst är felaktigt inställd'
description: MDVA-30599-korrigeringen åtgärdar ett problem där gästcitat som skapats med API felaktigt markeras som citattecken för inloggade kunder. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 är installerat. Problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: e16bb926-241b-451e-89a5-33000f73c5b7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-30599: customer_is_gäst är felaktigt inställd

MDVA-30599-korrigeringen åtgärdar ett problem där gästcitat som skapats med API felaktigt markeras som citattecken för inloggade kunder. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 är installerat. Problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce om molninfrastruktur 2.3.5-p2

**Kompatibel med Adobe Commerce:**

Adobe Commerce (alla distributionsmetoder) 2.3.4 - 2.4.0

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Gästcitattecken som skapats med API markeras felaktigt som citattecken för inloggade kunder.

<u>Steg som ska återskapas</u>:

1. Lägg en produkt i kundvagnen som gästanvändare i Adobe Commerce Store.
1. I din Adobe Commerce DB hittar du motsvarande `quote_id_mask`.
1. Skicka en API-begäran till `quoteGuestCartRepositoryV1` Cart Repository-gränssnitt för gästvagnar. Det kan göras via Swagger- eller cURL-begäran.

```curl
curl -X GET "http://web2-73.sparta.corp.magento.com/dev/support/ee24dev/rest/all/V1/guest-carts/ToOwPtSBxkorkCLq6ztwupPd99y8zhky" -H "accept: application/json"
```

<u>Förväntade resultat</u>:

Som svar får du `"customer_is_guest": true`

<u>Faktiska resultat</u>:

Som svar får du `"customer_is_guest": false`

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Ytterligare steg krävs efter installationen av korrigeringsfilen

Korrigeringen gäller för alla nya gästvagnar. Om du behöver korrigera befintliga gästvagnar anger du `quote.customer_is_guest = 1` för de register där `quote.customer_id` är NULL. Du kan köra en fråga som ser ut ungefär så här:

```sql
UPDATE quote SET customer_is_guest = 1 WHERE customer_id IS NULL;
```

>[!WARNING]
>
>Vi rekommenderar att du testar frågan i mellanlagrings-/integreringsmiljön innan du kör den i Production. Vi rekommenderar även att du har en säkerhetskopia nyligen före eventuella ändringar med DB.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
