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

Korrigeringen ACSD-48164 åtgärdar ett problem där en begränsad administratör inte kan spara ett värde på webbplatsnivå. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 är installerat. Korrigerings-ID är ACSD-48164. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Begränsad administratör kan inte spara ett värde på webbplatsnivå.

<u>Steg som ska återskapas</u>:

1. Skapa en ny webbplats, lagra och lagra vy i [!UICONTROL Admin] > **[!UICONTROL Store]** > **[!UICONTROL All Stores]**.
1. Skapa en ny administratörsroll i [!UICONTROL Admin] > **[!UICONTROL System]** > **[!UICONTROL User Roles]**.

   * Gå till **[!UICONTROL Role Resources]** > **[!UICONTROL Role Scopes]** väljer du den nya webbplatsen och tilldelar rollen till valfri administratörsanvändare.

1. Välj valfri produkt och tilldela bara den nya webbplatsen. Välj inte standardwebbplatsen.
1. Logga in som admin-användare tilldelad i steg 2 och redigera produkten under **[!UICONTROL All Store View]** genom att ändra attribut på webbplatsnivå som *[!UICONTROL Status]*, *[!UICONTROL Tax Class]* och ange produkten som ny.
1. Spara produkten.

<u>Förväntade resultat</u>:

Administratörsanvändare som är kopplad till rollomfånget för en webbplats kan spara produktattribut på webbplatsnivå med *[!UICONTROL All Store View]* omfång.

<u>Faktiska resultat</u>:

Meddelandet om att produkten sparades visas, men produktattributvärdena ändras inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
