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

Korrigeringen ACSD-52606 åtgärdar ett fel där felmeddelandet *Din beställning är inte klar för hämtning* visas när användaren klickar på **[!UICONTROL Notify Order is Ready for Pickup]**. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.37 har installerats. Korrigerings-ID är ACSD-52606. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett felmeddelande *Din beställning är inte klar för hämtning* visas på skärmen när användaren klickar på **[!UICONTROL Notify Order is Ready for Pickup]**.

<u>Förutsättningar</u>:

Lagermoduler är installerade.

<u>Steg som ska återskapas</u>:

1. Installera en ny instans.
1. Skapa en ny källa och aktie.
1. Tilldela den nya källan till standardwebbplatsen.
1. Aktivera hämtningsplats för den nya källan.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** och aktivera **[!UICONTROL In-Store Delivery]**.
1. Skapa en *enkel produkt i Stock* med *QTY=0* för alla lager och *[!UICONTROL Manage Stock = No]* och tilldela den till båda källorna.
1. Skapa en order från frontend med produkten som skapades i föregående steg och välj *[!UICONTROL In-Store Pickup]* som leveransmetod.
1. Gå till **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice that order]** i Admin.
1. Klicka på **[!UICONTROL Notify order is ready for pickup]**.

<u>Förväntade resultat</u>:

Du meddelas utan fel.

<u>Faktiska resultat</u>:

Du får följande felmeddelande: *Din beställning är inte klar för hämtning*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
