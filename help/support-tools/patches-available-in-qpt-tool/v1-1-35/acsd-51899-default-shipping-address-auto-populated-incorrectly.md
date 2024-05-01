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

Korrigeringen ACSD-51899 åtgärdar ett problem där standardleveransadressen fylls i automatiskt med fel adress. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 är installerat. Korrigerings-ID är ACSD-51899. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Standardleveransadressen fylls i automatiskt med fel adress

<u>Steg som ska återskapas</u>:

1. Aktivera **Plocka i butik** under leveranssätt.
1. Skapa *stock* och *källa*.
1. Skapa produkt och tilldela produkten till källan.
1. Lägg en produkt i kundvagnen.
1. Klicka på **Gå till kassan** från minikundvagn.
1. Ange testets e-postadress och välj **Plocka i butik**.
1. Klicka på **Välj butik** och välj en lagringsplats att välja från.
1. Klicka på **nästa** -knappen.
1. Navigera till **Hemsida** genom att klicka på butikslogotypen.
1. Öppna **Mini cart**.
1. Klicka på den nedre hyperlänken med namnet **Visa och redigera kundvagn**.
1. Klicka **Gå till kassan**.
1. Klicka på leveransknappen på leveranssidan.

<u>Förväntade resultat</u>

Fältet för leveransadress är tomt förutom *Land, region och postnummer*.

<u>Faktiska resultat</u>

Standardleveransadressen är automatiskt ifylld med *Upphämtning i butik* efter att sidan har uppdaterats.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
