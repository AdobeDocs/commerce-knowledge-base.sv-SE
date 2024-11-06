---
title: 'MDVA-33606: Användarna får felmeddelanden när CMS-sidor som tilldelats hierarkin sparas'
description: MDVA-33606-korrigeringen åtgärdar ett problem där användaren får felet *Unikt villkorsfel påträffades* när en CMS-sida som tilldelats hierarkiträdet sparas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 är installerat. Korrigerings-ID är MDVA-33606. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
exl-id: cdefece5-6d13-4003-87e9-810c665e940c
feature: CMS
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# MDVA-33606: Användarna får felmeddelanden när CMS-sidor sparas som tilldelats hierarkin

MDVA-33606-korrigeringen löser problemet där användaren får felet *Unik överträdelse av begränsningen* när en CMS-sida som tilldelats hierarkiträdet sparas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 har installerats. Korrigerings-ID är MDVA-33606. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1-2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När användare försöker spara en CMS-sida som tilldelats hierarkiträdet visas följande felmeddelande: *Unik överträdelse hittades*.

<u>Steg som ska återskapas</u>:

1. Skapa en ny CMS-sida. Ange omfånget till Alla butiksvyer. Det här är din CMS-sida 1.
1. Skapa en ny butiksvy. Det här är din butiksvy 2.
1. Gå till **Innehåll** > **Hierarki** > Lägg till CMS Page 1 i hierarkiträdet.
1. Ändra omfattningen till butiksvy 2.
   * Avmarkera Använd hierarkin för den överordnade noden.
   * Lägg till CMS Page 1 i det här omfånget och spara det.
1. Ändra nu omfånget till standardbutiksvyn.
   * Avmarkera Använd hierarkin för den överordnade noden.
   * Lägg till CMS Page 1 i det här omfånget och spara det.
1. Gå till **Innehåll** > **Sidor** > **Lägg till ny sida**.
   * Ge sidan namnet Sida 2.
   * I avsnittet Sida i webbplatser tilldelar du till Alla butiksvyer och båda butiksvyerna (standardbutiksvy och butiksvy 2) och klickar på **Spara sida**.
1. Öppna fliken Hierarki på CMS redigeringssida.
   * Tilldela sidan 2 till Store View 2-noden, Default-noden och All Websites-noden.

<u>Förväntade resultat</u>:

Du kan tilldela CMS-sidan till alla tre noderna utan fel.

<u>Faktiska resultat</u>:

Du får följande fel: *Unik överträdelse hittades*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
