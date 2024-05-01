---
title: 'ACSD-54026: Felaktigt felmeddelande för updateCompanyRole GraphQL-begäran'
description: Använd ACSD-54026-korrigeringen för att åtgärda Adobe Commerce-problemet där det finns ett felaktigt felmeddelande för en updateCompanyRole GraphQL-begäran för en obehörig användare.
feature: Roles/Permissions
role: Admin, Developer
exl-id: c18a8815-975a-499d-a372-8635d89aa673
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-54026: Fel felmeddelande för `updateCompanyRole` GraphQL-begäran

Korrigeringen ACSD-54026 åtgärdar ett fel där ett felaktigt felmeddelande för ett `updateCompanyRole` GraphQL begär en obehörig användare. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.39 är installerat. Korrigerings-ID är ACSD-54026. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Hämta ett felaktigt felmeddelande för ett `updateCompanyRole` GraphQL begär en obehörig användare.

<u>Steg som ska återskapas</u>:

1. Aktivera B2B-företaget i konfigurationen.
1. Skapa ett företag.
1. Skicka ett `updateCompanyRole` GraphQL-begäran utan att skicka en innehavartoken eller med en ogiltig innehavartoken.
1. Observera felmeddelandet i GraphQL svar.

<u>Förväntade resultat</u>:

Du får följande felmeddelande: *Den aktuella kunden är inte auktoriserad.*

<u>Faktiska resultat</u>:

Du får följande felmeddelande: *Kunden är inte en företagsanvändare.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
