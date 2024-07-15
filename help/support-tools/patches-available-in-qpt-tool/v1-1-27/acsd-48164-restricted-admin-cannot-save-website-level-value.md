---
title: 'ACSD-48164: begränsad administratör kan inte spara webbplatsnivåvärde'
description: Använd korrigeringsfilen ACSD-48164 för att åtgärda Adobe Commerce-problemet där en begränsad administratör inte kan spara ett webbplatsnivåvärde.
exl-id: 6ec15163-ad30-4566-a46c-5756bfd9f8d4
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48164: Begränsad administratör kan inte spara webbplatsnivåvärde

Korrigeringen ACSD-48164 åtgärdar ett problem där en begränsad administratör inte kan spara ett värde på webbplatsnivå. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 har installerats. Korrigerings-ID är ACSD-48164. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Begränsad administratör kan inte spara ett värde på webbplatsnivå.

<u>Steg som ska återskapas</u>:

1. Skapa en ny webbplats-, butiks- och butiksvy i [!UICONTROL Admin] > **[!UICONTROL Store]** > **[!UICONTROL All Stores]**.
1. Skapa en ny administratörsroll i [!UICONTROL Admin] > **[!UICONTROL System]** > **[!UICONTROL User Roles]**.

   * Gå till **[!UICONTROL Role Resources]** > **[!UICONTROL Role Scopes]**, markera den nya webbplatsen och tilldela den här rollen till valfri administratörsanvändare.

1. Välj valfri produkt och tilldela bara den nya webbplatsen. Välj inte standardwebbplatsen.
1. Logga in som admin-användare tilldelad i steg två och redigera produkten under **[!UICONTROL All Store View]** genom att ändra alla webbplatsnivåattribut som *[!UICONTROL Status]*, *[!UICONTROL Tax Class]* och ange produkten som ny.
1. Spara produkten.

<u>Förväntade resultat</u>:

Administratörsanvändare som är associerad med rollomfånget för en webbplats kan spara produktattribut på webbplatsnivå med omfånget *[!UICONTROL All Store View]*.

<u>Faktiska resultat</u>:

Meddelandet om att produkten sparades visas, men produktattributvärdena ändras inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
