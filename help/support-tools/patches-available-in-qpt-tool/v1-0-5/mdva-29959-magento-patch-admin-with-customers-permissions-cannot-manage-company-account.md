---
title: 'MDVA-29959-korrigering: Administratör med behörighet "Kunder" kan inte hantera företagskonto'
description: MDVA-29959-korrigeringsfilen som finns i [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) version 1.0.5 åtgärdar ett problem där en begränsad admin-användare med alla behörigheter för"Customer" ACL inte kan hantera företag (lägga till eller ta bort ett företag). Observera att problemet har åtgärdats i B2B för Adobe Commerce 2.3.4.
exl-id: ee246380-d37e-4c24-8435-97ae80088227
feature: Admin Workspace, B2B, Companies, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# MDVA-29959-korrigering: Administratör med behörighet &quot;Kunder&quot; kan inte hantera företagskonto

MDVA-29959-korrigeringsfilen som finns i [QPT-verktyget](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md), version 1.0.5, åtgärdar ett problem där en begränsad admin-användare med alla behörigheter för &quot;Customer&quot; ACL inte kan hantera företag (lägga till eller ta bort ett företag). Observera att problemet har åtgärdats i B2B för Adobe Commerce 2.3.4.

## Berörda produkter och versioner

B2B för Adobe Commerce om molninfrastruktur 2.3.0-2.3.3-p1.

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändare med alla behörigheter för kundåtkomstkontrollistan kan inte hantera företag (lägga till eller ta bort ett företag).

<u>Steg som ska återskapas</u>

1. Skapa en ny administratörsroll i Commerce Admin och tilldela en användare till den rollen.
1. Tilldela endast kundresurser till rollen.
1. Logga in som en användare med den här rollen.
1. Försök att ta bort ett företagskonto.

<u>Förväntat resultat:</u>

Företagskontot har tagits bort.

<u>Faktiskt resultat:</u>

Du kan inte ta bort företagskontot. Du får *Tyvärr måste du ha behörighet att visa det här innehållet.* felmeddelande.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
