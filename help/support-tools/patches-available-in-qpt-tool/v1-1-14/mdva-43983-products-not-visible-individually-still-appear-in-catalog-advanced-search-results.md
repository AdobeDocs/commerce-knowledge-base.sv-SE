---
title: 'MDVA-43983: Produkter som angetts som "Inte synliga enskilt" visas i sökresultaten'
description: MDVA-43983-korrigeringen åtgärdar ett problem där produkter som är inställda på"Inte synlig enskilt" fortfarande visas i katalogavancerade sökresultat. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 är installerat. Korrigerings-ID är MDVA-43983. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 2599fb6c-5b27-461b-9740-f586ae7df9f5
feature: Catalog Management, Products, Search
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-43983: Produkter som angetts som &quot;Inte synliga enskilt&quot; visas i sökresultaten

MDVA-43983-korrigeringen åtgärdar ett problem där produkter som är inställda på&quot;Inte synlig enskilt&quot; fortfarande visas i katalogavancerade sökresultat. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 är installerat. Korrigerings-ID är MDVA-43983. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produkterna som är inställda på&quot;Inte synlig enskilt&quot; visas fortfarande i katalogavancerade sökresultat.

<u>Steg som ska återskapas</u>:

1. Skapa ett attribut med **katalogindatatypen för butiksägare** som **listruta** eller **visuell färgruta** (till exempel Färg).
1. Ange **Använd i sökning** som **Ja** och **Synligt i avancerad sökning** som **Ja**.
1. Lägg till några attributalternativ.
1. Skapa produkter med **Synlighet** som **Inte synlig enskilt**.
1. Tilldela alternativ för färgattribut.
1. Gå till sidan **Avancerad katalogsökning** i butiken.
1. Välj bara alternativet Färgattribut i fältet Färgattribut och lämna resten av fälten tomma eller som de är.
1. Skicka ett avancerat sökformulär.
1. Observera sökresultaten.

<u>Förväntade resultat</u>:

Produkter som är inställda på&quot;Inte synlig enskilt&quot; visas inte i katalogens avancerade sökresultat.

<u>Faktiska resultat</u>:

Produkter som är inställda på&quot;Inte synlig enskilt&quot; visas i katalogens avancerade sökresultat.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i vår utvecklardokumentation.
