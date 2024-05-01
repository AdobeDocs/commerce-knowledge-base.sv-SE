---
title: 'MDVA-30594: Flera adresschassfel'
description: MDVA-30594-korrigeringen löser problemet där kunden inte ser orderframgångssida efter att ha lagt en order med flera adresser. När du kontrollerar beställningarna på Commerce Admin visas två beställningar med samma produkter i stället för rätt produkter. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat. Problemet har åtgärdats i Adobe Commerce 2.4.2.
exl-id: 7560cc39-ff0d-4313-979e-5cd588554c1d
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# MDVA-30594: flera adresschasseringsfel

MDVA-30594-korrigeringen löser problemet där kunden inte ser orderframgångssida efter att ha lagt en order med flera adresser. När du kontrollerar beställningarna på Commerce Admin visas två beställningar med samma produkter i stället för rätt produkter. Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 är installerat. Problemet har åtgärdats i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce i molninfrastruktur 2.3.3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Beställningar på flera adresser slutförs inte med ordersidan och två beställningar med samma produkter visas istället för de korrekta.

<u>Förutsättningar</u>:

Skapa två webbplatser med butiker och butiksvyer.

<u>Steg som ska återskapas</u>:

1. Ange **Katalogprisomfång** för webbplatskatalog (**Lager** > **Inställningar** > **Konfiguration** > **Katalog** > **Katalog** > **Pris** > **Omfång**).
1. Konfigurera **Fasta produktskatter** (**Lager** > **Konfiguration** > **Försäljning** > **Moms** > **Fasta produktskatter**):

   * **Aktivera FPT** = *Ja*
   * **Visa priser i produktlistan** = *exklusive FPT*
   * **Visa priser på produktvisningssidan** = *exklusive FPT*
   * **Visa priser i försäljningsmoduler** = *exklusive FPT* (Inklusive **FPT** beskrivning och slutpris).
   * **Visa priser i e-post** = *exklusive FPT* (Inklusive **FPT** beskrivning och slutpris).
   * **Tillämpa skatt på FPT** = *Ja*
   * **Inkludera FPT i delsumma** = *Nej*

1. Skapa en **FPT-attribut** och tilldela den till standardattributuppsättningen. (Se [Konfigurera FPT: Skapa ett FPT-attribut](https://docs.magento.com/user-guide/tax/fixed-product-tax-configuration.html#step-2-create-an-fpt-attribute) i vår användarhandbok).

1. Skapa fyra enkla produkter och ange **FPT** **attributvärde** (Exempel: ange **FPT**   **attributvärde** = *Australien*).

1. Skapa två paketerade produkter med följande konfiguration:

   * Definiera **FPT**.
   * Ange **Dynamiskt pris** = *Nej*.
   * Ange **Pris** = *100*.
   * Paketalternativ levererades tillsammans, alla markerade som standard med **Pristyp** = *Fast*.
   * Lägg till två av de enkla produkter som skapats i steg fyra.

1. Skapa ett användarkonto i förgrunden. Uppdatera adressen med den australiska adressen (ange landet till Australien eller det land som användes i **FPT** konfiguration).

1. Lägg de två paketerade produkterna i kundvagnen.

1. Gå till kundvagnssidan och kontrollera att **FPT** visas korrekt.

1. Klicka **Checka ut med flera adresser**.

1. Lägg till en andra adress.

1. Tilldela varje produkt till en annan adress.

1. Fortsätt med utcheckningsprocessen upp till **Montera beställning**.

1. Klicka på **Montera beställning** -knappen.

<u>Förväntade resultat</u>:

Ordern med flera adresser har placerats ut.

<u>Faktiska resultat</u>:

Ett meddelande som &quot;*Ett fel har inträffat.* visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
