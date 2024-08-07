---
title: 'MDVA-29954: fel adress skickade e-post för registrering av nyanställda användare'
description: Korrigeringen MDVA-29954 löser problemet där"New Company Registration Request" och"You'have been linked to a company" skickas från fel e-postadress. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: 9b3d1b93-3fe6-40a0-a68a-3e3d789c6d66
feature: B2B, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-29954: fel adress skickade e-post för registrering av nyanställda

Korrigeringen MDVA-29954 löser problemet där&quot;New Company Registration Request&quot; och&quot;You&#39;have been linked to a company&quot; skickas från fel e-postadress. Den här korrigeringen är tillgänglig när [QPT-verktyget ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.3.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.3.5-p2, 2.4.0 och 2.4.1.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Förutsättningar</u>:

Installera Adobe Commerce med B2B, med **B2B-funktioner** och **Företag** aktiverade.

<u>Steg som ska återskapas</u>:

1. Klicka på listrutan **Skapa konto** i butiken och välj **Skapa nytt företagskonto**.
1. Fyll i de obligatoriska fälten och registrera kontot.
1. Aktivera **Företag** från serverdelen (**Kund** > **Företag**).
1. Kontrollera e-postadressen som du använde för registreringen.
1. Ange **företagets administratörslösenord** genom att följa instruktionerna i e-postmeddelandet.
1. Logga in på frontend med **företagets administratörslösenord**.
1. Skapa en ny **företagsanvändare** i **Mitt konto** > **Företagsanvändare** > **Lägg till ny användare**.
1. Gå till **Store** > **Configurations** > **General-Store Email Addresses** > **General Contact** och kontrollera **Sender Email**.
1. Gå till e-postmeddelandet som du använde för att registrera den **nya användaren** i steg 7.

<u>Förväntade resultat</u>:

E-postmeddelandet&quot;Du har länkats till ett företag&quot; skickas från en e-postadress med samma värde som för **avsändarens e-postadress** i steg 8.

<u>Faktiska resultat</u>:

E-postmeddelandet&quot;Du har länkats till ett företag&quot; skickas från e-postmeddelandet **Företagsadministratör**.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
