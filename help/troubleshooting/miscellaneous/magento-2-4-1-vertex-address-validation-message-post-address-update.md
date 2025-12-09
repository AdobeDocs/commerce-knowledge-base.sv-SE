---
title: Adobe Commerce 2.4.1 Vertex Address validation message post address update
description: I den här artikeln beskrivs ett känt Adobe Commerce 2.4.1-problem där vertex-adressvalidering inte fungerar under betalningssteget när en annan leveransadress än faktureringsadressen används. Problemet är schemalagt att åtgärdas i Adobe Commerce 2.4.2.
exl-id: c2abeb96-e837-4d16-92dd-82fea5661dd9
feature: Shipping/Delivery
role: Developer
source-git-commit: ce377064efabaf09d3856da7c6c5c742a9fdcc2f
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 Vertex Address validation message post address update

I den här artikeln beskrivs ett känt Adobe Commerce 2.4.1-problem där vertex-adressvalidering inte fungerar under betalningssteget när en annan leveransadress än faktureringsadressen används. Problemet är schemalagt att åtgärdas i Adobe Commerce 2.4.2.

## Berörda produkter och versioner

* Adobe Commerce lokalt 2.4.1 med Vertex-integrering aktiverad
* Adobe Commerce i molninfrastruktur 2.4.1 med Vertex-integrering aktiverad

## Problem


<u>Steg att återskapa:</u>

1. Skapa ett konto och logga in.
1. Lägg till ett objekt i kundvagnen genom att klicka på **Lägg till i kundvagnen**. Klicka på kundvagnsikonen och sedan på **Fortsätt till kassan**.
1. Ange en giltig adress i fältet **Leveransadress**.
1. Markera ett av alternativen under **Leveransmetoder**. Klicka sedan på **Nästa**.
1. Om adressverifieringen föreslår en annan adressinformation klickar du på **Uppdatera adress** och sedan på **Nästa**.
1. Avmarkera kryssrutan **Min fakturerings- och leveransadress är densamma**.

<u>Första scenariot:</u>

Följ [över sex steg](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) och sedan:

1. Ange en ny giltig faktureringsadress.
1. Klicka på knappen **Uppdatera**. Meddelandet/förslaget visas enligt följande: *Adressen är inte giltig.* Detta följer med ett adressförslag som: *Postnummer: XXXXX-XXXX Street : XXX City Street XXX*
1. Klicka på knappen **Uppdatera** (klicka inte på knappen **Uppdatera adress** i vertex-adressförslaget).
1. Klicka på knappen **Redigera** för den uppdaterade faktureringsadressen.
1. Välj adressen i listrutan Adress.
1. Klicka på knappen **Uppdatera**.

<u>Förväntat resultat:</u>

Det gamla meddelandet/förslaget för validering har tagits bort.

<u>Faktiskt resultat:</u>

Verifieringsmeddelandet/förslaget *&quot;Vi hittade ingen giltig adress Postnummer: XXXXX-XXXX Street : XXX City Street XXX&quot;* message is **NOT** removed. Samma problem uppstår om du anger en ogiltig adress i formuläret.

<u>Andra scenariot:</u>

Följ [över sex steg](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) och sedan:

1. Ange en giltig adress i adressformuläret.
1. Klicka på knappen **Uppdatera**. Meddelandet/förslaget visas enligt följande: *Adressen är inte giltig.* Detta följer med ett adressförslag som: *Postnummer: XXXXX-XXXX Street : XXX City Street XXX*.
1. Klicka på knappen **Uppdatera** (klicka inte på knappen **Uppdatera adress** för vertex-adressförslag).
1. Kontrollera att ***Min fakturerings- och leveransadress är samma***-listruta.

<u>Förväntat resultat:</u>

Det gamla meddelandet/förslaget för validering har tagits bort.

<u>Faktiskt resultat:</u>

Verifieringsmeddelandet/förslaget *&quot;Vi hittade ingen giltig adress Postnummer: XXXXX-XXXX Street XXX City Street XXX&quot;* meddelande är **INTE** borttaget. Samma problem uppstår om du anger en ogiltig adress i formuläret.

## Relaterad läsning i vår kunskapsbas:

[Problem med Adobe Commerce 2.3.6, 2.4.0-p1 och 2.4.1: det går inte att logga in på dotdigital när kontot är aktiverat](/help/troubleshooting/miscellaneous/magento-2-3-6-2-4-0-p1-2-4-1-known-issue-dotdigital-login.md)
