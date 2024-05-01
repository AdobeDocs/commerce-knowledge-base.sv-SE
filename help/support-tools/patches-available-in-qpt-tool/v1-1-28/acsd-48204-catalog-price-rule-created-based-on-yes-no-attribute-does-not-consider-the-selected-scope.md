---
title: "ACSD-48204: Katalogprisregeln som skapats baserat på attributet *Ja/Nej* tar inte hänsyn till valt omfång"
description: Använd patchen ACSD-48204 för att åtgärda Adobe Commerce-problemet där den katalogprisregel som skapas baserat på attributet *Ja/Nej* inte tar hänsyn till det valda omfånget.
exl-id: 9b0b4d62-c4c5-40d7-a279-52f59ee7ac42
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-48204: Katalogprisregel skapad utifrån *Ja/Nej* det valda omfånget hanteras inte av attributet

Korrigeringen för ACSD-48204 åtgärdar ett problem där katalogprisregeln som skapas baserat på *Ja/Nej* det valda omfånget tas inte med i attributet. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 är installerat. Korrigerings-ID är ACSD-48204. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Katalogprisregeln som skapas utifrån *Ja/Nej* det valda omfånget tas inte med i attributet.

<u>Steg som ska återskapas</u>:

1. Skapa två webbplatser (standard och W2).
1. Skapa ett produktattribut för *Ja/Nej* typ.
   * Ange [!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. Skapa en konfigurerbar produkt baserad på valfritt attribut med två varianter (V1 och V2).
   * Lägg till *Ja/Nej* attribut till den konfigurerbara variantattributuppsättningen
   * För en av variationerna (V1) anger du värdet till *[!UICONTROL Yes]* på den webbplats som inte är standard (W2)
1. Skapa en katalogregel:
   * Tillämpas på båda webbplatserna
   * Villkor: *Ja/Nej* attributvärdet är *[!UICONTROL Yes]*
   * Rabatt = 50 %
1. Öppna den konfigurerbara produkten på den icke-förvalda webbplatsen (W2).
1. Kontrollera att 50 % rabatt används för varianten V1.
1. Öppna V1-varianten i Adobe Commerce Admin.
   * Växla till standardwebbplatsen
   * Gör inga ändringar och spara produkten
1. Uppdatera den konfigurerbara produktbutikssidan.

<u>Förväntade resultat</u>:

V1-varianten har fortfarande 50 % rabatt eftersom inga ändringar gjordes.

<u>Faktiska resultat</u>:

Rabatten försvinner.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
