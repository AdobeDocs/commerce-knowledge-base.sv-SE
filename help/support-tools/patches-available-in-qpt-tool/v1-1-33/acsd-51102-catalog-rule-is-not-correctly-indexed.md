---
title: 'ACSD-51102: Katalogregel som används för ett stort antal produkter har inte indexerats korrekt'
description: Använd patchen ACSD-51102 för att åtgärda Adobe Commerce-problemet där en katalogregel som tillämpas på ett stort antal produkter inte indexeras korrekt när regeln aktiveras av en schemalagd uppdatering.
feature: Catalog Management, Products
role: Admin
exl-id: 5c1c5f9c-9cce-4b11-8058-0e12a4bf93fd
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# ACSD-51102: Katalogregel som används för ett stort antal produkter har inte indexerats korrekt

Korrigeringen ACSD-51102 åtgärdar ett problem där en katalogregel som tillämpas på ett stort antal produkter inte indexeras korrekt när regeln aktiveras av en schemalagd uppdatering. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 är installerat. Korrigerings-ID är ACSD-51102. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En katalogregel som tillämpas på ett stort antal produkter indexeras inte korrekt när regeln aktiveras av en schemalagd uppdatering.

Förutsättningar:

* Kronjobbet är klart och körs varje minut.

<u>Steg som ska återskapas</u>:

1. Skapa en stor katalog med tusentals produkter för att få körtiden för *katalogregel* indexerare på mer än 120 sekunder när katalogregler aktiveras.
2. Skapa två katalogregler med *Aktiv* status inställd på *Nej*.  Till exempel: *Test 1* och *Test 2*. Varje regel ska påverka alla produkter i katalogen och göra så att indexeraren körs i mer än 120 sekunder.
3. Kontrollera att indexerarens status är *Klar*.
4. Skapa schemalagda uppdateringar för att aktivera dessa två regler. *Test 2* schemat börjar kort efter *Test 1*. Exempel: med en minuts skillnad.
5. Kontrollera produktpriserna i Store.

<u>Förväntade resultat</u>

Rabatter från båda reglerna tillämpas.

<u>Faktiska resultat</u>

Endast rabatten för den första regeln tillämpas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) i [!DNL Quality Patches Tool] guide.
