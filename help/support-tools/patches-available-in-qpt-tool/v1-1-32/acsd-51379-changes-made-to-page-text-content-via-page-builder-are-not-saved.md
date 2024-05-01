---
title: "ACSD-51379: Ändrar sidans textinnehåll via [!DNL Page Builder] har inte sparats"
description: Använd korrigeringsfilen ACSD-51379 för att åtgärda Adobe Commerce-problemet där ändringar av en sidas textinnehåll görs via [!DNL Page Builder] sparas inte.
exl-id: e274ca03-b675-4ded-9820-1d60978685d0
feature: Page Builder, Page Content
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-51379: Ändringar av sidans textinnehåll via [!DNL Page Builder] har inte sparats

Korrigeringen ACSD-51379 åtgärdar ett problem där ändringar som gjorts i en sidas textinnehåll via [!DNL Page Builder] sparas inte. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 är installerat. Korrigerings-ID är ACSD-51379. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

De ändringar som gjorts i en sidas textinnehåll via [!DNL Page Builder] sparas inte.

<u>Steg som ska återskapas</u>:

1. Logga in på Admin.
1. Gå till **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**.
1. Skapa en testsida med en rad och ett textelement på **[!UICONTROL Content]** -fliken.
1. Spara sidan och gå tillbaka till **[!UICONTROL Content]** -fliken.
1. Redigera texten genom att markera den och ändra den.

   **Obs!** Problemet kan bara reproduceras om texten är markerad och ändrad utan att redigeraren aktiveras.

1. Klicka på **[!UICONTROL Save and Close]** på testsidan.
1. Öppna testsidan igen och kontrollera **[!UICONTROL Content]** -fliken.

<u>Förväntade resultat</u>:

Den nya texten har sparats för ursprungliga och duplicerade textelement.

<u>Faktiska resultat</u>:

Textelementet har duplicerats, men den nya texten sparas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
