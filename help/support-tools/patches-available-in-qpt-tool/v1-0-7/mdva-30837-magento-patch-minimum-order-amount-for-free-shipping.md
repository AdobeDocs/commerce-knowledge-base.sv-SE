---
title: "MDVA-30837: minimiorderbelopp för fri frakt"
description: MDVA-30837-patchen lägger till konfigurationsalternativ för beräkning av fri frakt så att användaren kan konfigurera minimiorderbeloppet för fri frakt baserat på delsumman (eller totalsumman). Detta möjliggör lokala anpassningar av skatte- och leveransmetoder. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: 64716d08-4ce0-40d5-aeb7-242e2aa85bb0
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---

# MDVA-30837: minimiorderbelopp för fri frakt

MDVA-30837-patchen lägger till konfigurationsalternativ för beräkning av fri frakt så att användaren kan konfigurera minimiorderbeloppet för fri frakt baserat på delsumman (eller totalsumman). Detta möjliggör lokala anpassningar av skatte- och leveransmetoder. Den här korrigeringen är tillgänglig när [QPT-verktyget ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat. Observera att problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce om molninfrastruktur 2.3.4-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce om molninfrastruktur 2.3.1 - 2.3.4-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Korrigeringen MDVA-30837 lägger till konfigurationsinställningen för att konfigurera inställningen **Minsta orderbelopp** för fri frakt baserat på delsumma (eller totalsumma):

* **Inkludera moms i belopp**: *Ja/Nej* i konfigurationen av metoden för fri frakt.
   * När **Inkludera skatt till belopp** är inställt på *Ja* beräknas minimiorderbeloppet som Delsumma + Moms - Rabatt.
   * När **Inkludera moms till belopp** är inställt på *Nej* beräknas minimiorderbeloppet som Delsumma - rabatt.

<u>Steg som ska återskapas</u>:

1. Gå till **Store** > Inställningar > **Konfiguration** > **Försäljning** > **Moms** och ange följande:

   * Skatteberäkning baserad på *leveransadress*
   * Aktivera gränsöverskridande handel: *Nej*
   * Visa produktpriser i katalog: *exklusive moms*
   * Visa leveranspriser: *exklusive moms*
   * Visningspriser: *exklusive moms*
   * Visa delsumma: *exklusive moms*
   * Visa leveransbelopp: *exklusive moms*
   * Visa presentfigursättningspriser: *exklusive moms*
   * Visa utskrivna kortpriser: *exklusive moms*
   * Inkludera skatt i ordersumma: *Ja*
   * Visa fullständig momssammanfattning: *Ja*

1. Gå till **Försäljning** > **Leveransinställningar** > **Fri frakt** och ange **Minsta orderbelopp** = *30*.
1. Gå till **Marknadsföring** > Kampanjer > **Kundprisregler** och skapa en ny prisregel (mer information finns i [Skapa en kundprisregel](https://docs.magento.com/user-guide/marketing/price-rules-cart-create.html) i vår användarhandbok).

   * Kupongkod = *Specifik kupong*.
   * Villkor: Delsumman är lika med eller större än $25.
   * Åtgärder: Fri frakt = *För leveranser med matchande artiklar*.

1. Skapa en produkt till priset av 23,10 USD.
1. Lägg till CA-skatt i standardmomsregeln.
1. Lägg produkten i kundvagnen.
1. Få en offert - efter moms tillkommer totalsumman = $25.01 och fri frakt.
1. Använd kupongkoden - den är inte giltig eftersom delsumman (exklusive moms) är $23.10.

<u>Förväntade resultat</u>:

Det finns en ytterligare konfigurationsinställning - Inkludera moms till belopp: *Ja*/*Nej* i konfigurationen av metoden för kostnadsfri leverans:

* När Inkludera moms till belopp är inställt på *Ja* beräknas minimiorderbeloppet som Delsumma + Moms - Rabatt.
* När Inkludera moms till belopp är inställt på *Nej* beräknas minimiorderbeloppet som Delsumma - rabatt.

<u>Faktiska resultat</u>:

Regelvillkoret Fri frakt kan endast baseras på delsumman, medan metoden fri frakt endast kan baseras på totalsumman.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://devdocs.magento.com/cloud/project/project-patch.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår utvecklardokumentation.
