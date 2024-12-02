---
title: 'ACSD-48807: Produktrecensioner som inte filtrerats av butiksgranskningar'
description: Använd patchen ACSD-48807 för att åtgärda Adobe Commerce-problemet där produktrecensioner inte filtreras genom butiksgranskning via GraphQL.
exl-id: 754ef455-ff06-4832-9eb6-ad8cccec8799
feature: Admin Workspace, Products
role: Admin
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-48807: Produktrecensioner som inte filtrerats av butiksgranskningar

Korrigeringsfilen ACSD-48807 åtgärdar ett problem där produktrecensioner inte filtreras genom butiksgranskning via GraphQL. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 har installerats. Korrigerings-ID är ACSD-48807. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktrecensioner filtreras inte genom butiksgranskning via GraphQL.

<u>Steg som ska återskapas</u>:

1. Skapa ytterligare en butiksgranskning.
1. Skapa ett kundkonto och logga in.
1. Skapa en granskning för en produkt i standardbutiken.
1. Gå över till en annan affisch och skapa en ny recension av en produkt.
1. Godkänn båda granskningarna i Adobe Commerce Admin.
1. Skicka kundens GraphQL-fråga om du vill hämta produktrecensioner och ange den butiksgranskning som skapats i steg ett i sidhuvudet.
1. Observera svaret.

<u>Förväntade resultat</u>:

Endast produktrecensionen för den angivna butiksgranskningen returneras i svaret.

<u>Faktiska resultat</u>:

Båda granskningarna returneras som svar.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
