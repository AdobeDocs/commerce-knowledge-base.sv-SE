---
title: 'ACSD-51471: Administratörsanvändaren kan inte spara schemalagd uppdatering för paketerad produkt'
description: Använd patchen ACSD-51471 för att åtgärda Adobe Commerce-problemet där en administratörsanvändare inte kan spara en schemalagd uppdatering för en paketerad produkt som använder en enkel produkt med en schemalagd uppdatering.
exl-id: 7d80aef0-8505-4491-bde3-5b1a30b840f6
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# ACSD-51471: Administratörsanvändaren kan inte spara schemalagd uppdatering för paketerad produkt

Korrigeringen ACSD-51471 åtgärdar ett problem där en administratörsanvändare inte kan spara en schemalagd uppdatering för en paketerad produkt som använder en enkel produkt med en schemalagd uppdatering. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 har installerats. Korrigerings-ID är ACSD-51471. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändare kan inte spara en schemalagd uppdatering för en paketerad produkt som använder en enkel produkt som själv har en schemalagd uppdatering.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt.
1. Lägg till en schemalagd uppdatering för den enkla produkten med endast *Startdatum* och *Slutdatum*.
1. När uppdateringen har installerats ändrar du SKU för produkten.
1. Skapa en paketerad produkt och lägg till den enkla produkten som skapats i steg 1 som en underordnad produkt.
1. Skapa en schemalagd uppdatering för den paketerade produkten för att aktivera den paketerade produkten. Ange både *Startdatum* och *Slutdatum* för den schemalagda uppdateringen.
1. Spara den schemalagda uppdateringen.

<u>Förväntade resultat</u>:

Den schemalagda uppdateringen har sparats.

<u>Faktiska resultat</u>:

Följande fel inträffar när den schemalagda uppdateringen sparas: *Produkten som begärdes finns inte. Verifiera produkten och försök igen.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
