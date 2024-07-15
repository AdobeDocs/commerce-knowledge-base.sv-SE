---
title: '''ACSD-51899: Standardleveransadressen har fyllts i felaktigt"'
description: Använd patchen ACSD-51899 för att åtgärda Adobe Commerce-problemet där standardleveransadressen fylls i automatiskt med fel adress.
feature: Checkout
role: Admin
exl-id: 67100fcd-e98f-4740-8f1f-fcc820f4c75d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-51899: Standardleveransadressen fylldes i felaktigt

Korrigeringen ACSD-51899 åtgärdar ett problem där standardleveransadressen fylls i automatiskt med fel adress. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 har installerats. Korrigerings-ID är ACSD-51899. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Standardleveransadressen fylls i automatiskt med fel adress

<u>Steg som ska återskapas</u>:

1. Aktivera **In Store Pickup** under leveransmetod.
1. Skapa *stock* och *source*.
1. Skapa produkt och tilldela produkten till källan.
1. Lägg en produkt i kundvagnen.
1. Klicka på **Fortsätt till kassan** från mini-cart.
1. Ange testets e-postadress och välj **Välj i butik**.
1. Klicka på knappen **Välj butik** och välj en lagringsplats att välja från.
1. Klicka på knappen **nästa**.
1. Navigera till **hemsidan** genom att klicka på butikslogotypen.
1. Öppna **Mini cart**.
1. Klicka på den nedre hyperlänken **Visa och redigera kundvagn**.
1. Klicka på **Fortsätt till kassan**.
1. Klicka på leveransknappen på leveranssidan.

<u>Förväntade resultat</u>

Leveransadressfältet är tomt förutom för *Land, region och postnummer*.

<u>Faktiska resultat</u>

Standardleveransadressen fylls i automatiskt med *hämtningsadressen i butiken* när sidan har uppdaterats.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
