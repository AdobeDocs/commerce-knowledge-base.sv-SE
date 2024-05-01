---
title: 'ACSD-54983: Företagets användar-UID med GraphQL är inte tillgängligt med inaktiv användare'
description: Använd patchen ACSD-54983 för att åtgärda Adobe Commerce-problemet där det inte går att hämta företagets användar-UID med GraphQL-begäran när användarstatusen är inaktiv.
feature: GraphQL
role: Admin, Developer
exl-id: 57e7b9ca-3421-4b50-86b4-abdf1b3d79d1
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-54983: Företagets användar-UID med GraphQL är inte tillgängligt med inaktiv användare

Korrigeringen ACSD-54983 åtgärdar ett problem där det inte går att hämta företagets användar-UID med GraphQL-begäran när användarstatusen är inaktiv. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 är installerat. Korrigerings-ID är ACSD-54983. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det går inte att hämta företagets användar-UID med GraphQL-begäran när användarstatusen är inaktiv.

<u>Steg som ska återskapas</u>:

1. Skapa ett företag med en administratörsanvändare. Exempel: company@test.com.
1. Skapa en ny kund.
1. Tilldela den nya kunden till ett företag.
1. Få en **[!UICONTROL company admin token]**.
1. Använda **[!UICONTROL company admin token]**, hämta företagsstrukturen. Se [Returnera företagsstrukturen](https://developer.adobe.com/commerce/webapi/graphql/schema/b2b/company/queries/company/#return-the-company-structure) i vår dokumentation för utvecklare.
1. Svaret innehåller bara *AKTIV* kunder med sina ID:n.
1. Uppdatera företagsanvändaren till *INAKTIV*.
1. Hämta företagsstrukturen igen.

<u>Förväntade resultat</u>:

Det går att hämta företagets användar-UID när statusen är inaktiv.

<u>Faktiska resultat</u>:

De inaktiva kunderna finns inte med i listan. Det går inte att hämta företagets användar-UID när statusen är inaktiv.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
