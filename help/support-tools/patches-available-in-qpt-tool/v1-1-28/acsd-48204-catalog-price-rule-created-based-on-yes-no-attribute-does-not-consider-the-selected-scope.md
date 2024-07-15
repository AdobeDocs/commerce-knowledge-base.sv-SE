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

# ACSD-48204: Katalogprisregeln som skapats baserat på attributet *Yes/No* tar inte hänsyn till det valda omfånget

Korrigeringen ACSD-48204 åtgärdar ett problem där den katalogprisregel som skapas baserat på attributet *Yes/No* inte tar hänsyn till det valda omfånget. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 har installerats. Korrigerings-ID är ACSD-48204. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Katalogprisregeln som skapas baserat på attributet *Yes/No* tar inte hänsyn till det valda omfånget.

<u>Steg som ska återskapas</u>:

1. Skapa två webbplatser (standard och W2).
1. Skapa ett produktattribut av typen *Yes/No*.
   * Ange [!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. Skapa en konfigurerbar produkt baserad på valfritt attribut med två varianter (V1 och V2).
   * Lägg till attributet *Yes/No* i den konfigurerbara variantattributuppsättningen
   * För en av varianterna (V1) anger du värdet till *[!UICONTROL Yes]* på den icke-standardwebbplatsen (W2)
1. Skapa en katalogregel:
   * Tillämpas på båda webbplatserna
   * Villkor: attributvärdet *Yes/No* är *[!UICONTROL Yes]*
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

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
