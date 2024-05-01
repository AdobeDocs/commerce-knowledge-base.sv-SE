---
title: 'ACSD-56858: Rollbehörighetsdiskrepans i B2B-företagsadministratör'
description: Använd patchen ACSD-56858 för att åtgärda Adobe Commerce-problemet där rollbehörigheter visas felaktigt för en företagsadministratör med begränsat tillstånd i B2B-miljön.
feature: Companies, B2B, Roles/Permissions
role: Admin, Developer
exl-id: d446f815-78bf-42ec-bc2b-a5934b15b416
source-git-commit: 4bf5deb1115705560acc8410441219943329c1a4
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-56858: Skillnad i rollbehörigheter i B2B-företagsadministratör

Korrigeringen ACSD-56858 åtgärdar ett problem där rollbehörigheter felaktigt visas för en företagsadministratör med begränsat tillstånd i B2B-miljön. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.47 är installerat. Korrigerings-ID är ACSD-56858. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Rollbehörigheterna för en begränsad företagsadministratör i B2B-miljön visas felaktigt.

<u>Steg som ska återskapas</u>:

1. Börja med att konfigurera ett företag och lägga till en företagsadministratör och företagsanvändare.
1. Logga in som företagsadministratör i butiken och skapa olika roller för olika användare.
1. Tilldela de här rollerna efter behov, till exempel för att begränsa åtkomsten för vissa uppgifter samtidigt som du ger fullständig åtkomst för andra.
1. Tilldela de här rollerna fullständig åtkomst till en annan användare än företagsadministratören.
1. Logga in på en icke-företagsanvändare, t.ex. en company_manager.
1. Navigera till **[!UICONTROL Roles and permission]** och redigera rollen.
1. Observera att behörigheterna som visas inte matchar behörigheterna som anges i företagets databas för det roll-ID:t.

<u>Förväntade resultat</u>:

Roller och behörigheter visas korrekt för den icke-företagsinterna administratörsanvändaren.

<u>Faktiska resultat</u>:

Rollerna visas inte korrekt för den icke-företagsinterna administratörsanvändaren enligt databasposterna i behörighetstabellen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
