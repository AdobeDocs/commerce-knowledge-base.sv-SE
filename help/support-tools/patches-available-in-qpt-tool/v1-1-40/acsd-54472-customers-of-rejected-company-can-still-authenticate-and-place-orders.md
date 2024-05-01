---
title: "ACSD-54472: Kunder i ett avvisat företag kan fortfarande autentisera"
description: Använd patchen ACSD-54472 för att åtgärda Adobe Commerce-problemet där kunderna i ett avvisat företag fortfarande kan autentisera och kunder i ett blockerat och avvisat företag fortfarande kan göra beställningar.
feature: B2B
role: Admin, Developer
exl-id: 76fc4553-02b1-4563-91a9-0cda99fa4c7d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-54472: Kunder i ett avvisat företag kan fortfarande autentisera

Korrigeringen ACSD-54472 åtgärdar ett problem där kunder i ett avvisat företag fortfarande kan autentisera och kunder i ett blockerat och avvisat företag fortfarande kan göra beställningar. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 är installerat. Korrigerings-ID är ACSD-54472. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kunderna i ett avvisat företag kan fortfarande autentisera, och kunder i ett blockerat och avvisat företag kan fortfarande göra beställningar.

<u>Steg som ska återskapas</u>:

1. Skapa ett företag.
1. Lägg produkter i kundvagnen via [!DNL GraphQL].
1. Ändra företagsstatus till *Blockerad*.
1. Skicka en [!DNL GraphQL] begära att få lägga ordern och skapa en överlåtbar offert.
1. Ändra företagsstatus till *Avvisad*.
1. Skicka en [!DNL GraphQL] begäran om att erhålla företagets token för användarauktorisering.
1. Ange kundstatus till *Inaktiv*.
1. Skicka en [!DNL GraphQL] begäran om att erhålla företagets token för användarauktorisering.

<u>Förväntade resultat</u>:

* Beställning och överlåtbar offert läggs inte in av användaren av *Blockerad* företag.
* Autentiseringstoken har inte inhämtats för användaren av *Avvisad* företag.
* Auktoriseringstoken har inte hämtats för *Inaktiv* kund.

<u>Faktiska resultat</u>:

* Beställning och överlåtbar offert görs av användaren av *Blockerad* företag.
* Auktoriseringstoken hämtas för användaren av *Avvisad* företag.
* Auktoriseringstoken hämtas för *Inaktiv* kund.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
