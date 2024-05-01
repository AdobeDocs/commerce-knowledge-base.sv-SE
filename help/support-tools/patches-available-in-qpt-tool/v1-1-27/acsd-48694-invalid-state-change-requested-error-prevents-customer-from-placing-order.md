---
title: 'ACSD-48694: Felaktig begärd tillståndsändring förhindrar kunden från att beställa'
description: Använd patchen ACSD-48694 för att åtgärda Adobe Commerce-problemet där felet *Ogiltig tillståndsändring har begärts* förhindrar att en kund beställer.
exl-id: edf79424-6c4f-4cfd-ab7e-19f95b9bc685
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-48694: *Ogiltig tillståndsändring begärdes* fel förhindrar att kunden lägger en order

Korrigeringen ACSD-48694 åtgärdar ett problem där felet *Ogiltig tillståndsändring begärdes* förhindrar att en kund lägger en order. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 är installerat. Korrigerings-ID är ACSD-48694. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.37-p4, 2.4.1 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Felet *Ogiltig tillståndsändring begärdes* förhindrar att en kund lägger en order.

<u>Steg som ska återskapas</u>:

1. Lägg till en fördröjning under `/estimate-shipping-methods` begäran genom att inkludera `sleep()` på `app/code/Magento/Quote/Model/GuestCart/GuestShippingMethodManagement.php::estimateByExtendedAddress()` funktionen, så att `/estimate-shipping-methods` begäran slutförs efter `/shipping-information` när du går från leveranssteg till betalningssteg vid utcheckning.
1. Konfigurera sessionen som ska användas [!DNL Redis] med *disable_locking: 1* inställning.
1. Öppna **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** och aktivera *[!UICONTROL Persistent Shopping Cart]*.
1. Logga in som kund och lägg till en produkt i kundvagnen.
1. Låt kundsessionen förfalla. Beständig kaka och vagnen finns kvar.
1. Gå till kassan, lägg till leveransadressen och navigera till betalningsavsnittet.
1. Gå tillbaka till startsidan eller någon annan sida och logga in med kundkontot.
1. Låt sessionen förfalla igen.
1. Gå direkt till kassan och gå till betalningssteget.
1. Försök att lägga ordern.

<u>Förväntade resultat</u>:

* Det finns inget fel.
* Ordern har placerats och en *Tack* visas.

<u>Faktiska resultat</u>:

Felet *Ogiltig tillståndsändring begärdes* visas, men ordningen placeras.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
