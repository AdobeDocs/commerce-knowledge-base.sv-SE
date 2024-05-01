---
title: '''ACSD-52606: Felmeddelande visas när användaren klickar på "Notify Order is Ready for Pickup"'
description: Åtgärda Adobe Commerce-problemet med korrigeringen ACSD-52606 där ett felmeddelande visas när användaren klickar på **[!UICONTROL Notify Order is Ready for Pickup]**.
feature: Orders, User Account
role: Admin, Developer
exl-id: c3e69eb1-90bf-46cf-9b53-110e40e0c3c1
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-52606: Felmeddelande som visas när användaren klickar på Meddela beställning är klar för hämtning

Korrigeringen ACSD-52606 åtgärdar ett problem där ett felmeddelande visas *Din beställning är inte klar för hämtning* visas när användaren klickar **[!UICONTROL Notify Order is Ready for Pickup]**. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.37 är installerat. Korrigerings-ID är ACSD-52606. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett felmeddelande *Din beställning är inte klar för hämtning* visas på skärmen när användaren klickar **[!UICONTROL Notify Order is Ready for Pickup]**.

<u>Förutsättningar</u>:

Lagermoduler är installerade.

<u>Steg som ska återskapas</u>:

1. Installera en ny instans.
1. Skapa en ny källa och aktie.
1. Tilldela den nya källan till standardwebbplatsen.
1. Aktivera hämtningsplats för den nya källan.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** och aktivera **[!UICONTROL In-Store Delivery]**.
1. Skapa en *I Stock* enkel produkt med *ANTAL=0* för alla lager och *[!UICONTROL Manage Stock = No]* och tilldela den till båda källorna.
1. Skapa en beställning från frontend med den produkt som skapades i föregående steg genom att välja *[!UICONTROL In-Store Pickup]* som leveransmetod.
1. Gå till Admin **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice that order]**.
1. Klicka på **[!UICONTROL Notify order is ready for pickup]**.

<u>Förväntade resultat</u>:

Du meddelas utan fel.

<u>Faktiska resultat</u>:

Du får följande felmeddelande: *Din beställning är inte klar för hämtning*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
