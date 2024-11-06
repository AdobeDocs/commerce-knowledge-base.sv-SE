---
title: 'MDVA-41236: Det går inte att skapa nya eller redigera befintliga schemalagda uppdateringar för produkten'
description: MDVA-41236-korrigeringen åtgärdar ett problem där användare inte kan skapa nya eller redigera befintliga schemalagda uppdateringar för produkten om slutdatumet har tagits bort tidigare. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 är installerat. Korrigerings-ID är MDVA-41236. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 00d6c0af-f248-49f6-aaa2-3ae3c0294832
feature: Products, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# MDVA-41236: Det går inte att skapa nya eller redigera befintliga schemalagda uppdateringar för produkten

MDVA-41236-korrigeringen åtgärdar ett problem där användare inte kan skapa nya eller redigera befintliga schemalagda uppdateringar för produkten om slutdatumet har tagits bort tidigare. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 har installerats. Korrigerings-ID är MDVA-41236. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användare kan inte skapa nya scheman eller redigera befintliga för produkter om Slutdatum har tagits bort tidigare.

<u>Steg som ska återskapas</u>:

1. Skapa en produkt med statusvärdet *disable*.
1. Lägg till en schemalagd uppdatering för att aktivera den här produkten.
   * Lägg till framtida start- och slutdatum.
1. Redigera den schemalagda uppdateringen genom att ta bort **slutdatumet**.
1. Redigera schemat igen och försök lägga till ett **slutdatum**. Ett fel kommer att uppstå.
1. Uppdatera sidan och gå till **Redigera schemalagd uppdatering** igen.
1. Klicka på **Ta bort från uppdatering** > **Ta bort uppdateringen**.
1. Nu ska du inte se den schemalagda uppdateringen ovanför produktredigeringssidan.
1. Försök att skapa en ny schemalagd uppdatering som överlappar den tidigare tidslängden.

<u>Förväntade resultat</u>:

* Det finns inget fel i steg 4. Administratören kan uppdatera den schemalagda uppdateringen utan fel eftersom schemat ännu inte är aktivt.
* Administratörsanvändaren kan ta bort den tidigare uppdateringen och skapa en ny.

<u>Faktiska resultat</u>:

Användarna får följande felmeddelande:

*fel: Framtida uppdatering finns redan i det här tidsintervallet. Ange ett annat intervall och försök igen.*


## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
