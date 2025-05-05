---
title: 'ACSD-51379: Ändringar av sidans textinnehåll via [!DNL Page Builder] sparas inte'
description: Använd korrigeringsfilen ACSD-51379 för att åtgärda Adobe Commerce-problemet där ändringar som gjorts i en sidas textinnehåll via  [!DNL Page Builder] inte sparas.
exl-id: e274ca03-b675-4ded-9820-1d60978685d0
feature: Page Builder, Page Content
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-51379: Ändringar av sidans textinnehåll via [!DNL Page Builder] sparas inte

Korrigeringen ACSD-51379 åtgärdar ett problem där ändringar som gjorts i en sidas textinnehåll via [!DNL Page Builder] inte sparas. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 har installerats. Korrigerings-ID är ACSD-51379. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ändringarna som gjorts i en sidas textinnehåll via [!DNL Page Builder] sparas inte.

<u>Steg som ska återskapas</u>:

1. Logga in på Admin.
1. Gå till **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**.
1. Skapa en testsida med en rad och ett textelement på fliken **[!UICONTROL Content]**.
1. Spara sidan och gå tillbaka till fliken **[!UICONTROL Content]**.
1. Redigera texten genom att markera den och ändra den.

   **Obs!** Utgåvan kan bara reproduceras om texten markeras och ändras utan att redigeraren aktiveras.

1. Klicka på knappen **[!UICONTROL Save and Close]** på testsidan.
1. Öppna testsidan igen och kontrollera fliken **[!UICONTROL Content]**.

<u>Förväntade resultat</u>:

Den nya texten har sparats för ursprungliga och duplicerade textelement.

<u>Faktiska resultat</u>:

Textelementet har duplicerats, men den nya texten sparas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
