---
title: "ACSD-50512: Fel vid uppdatering av startdatum för en hämtningsbar mellanlagringsuppdatering för produkt"
description: Använd korrigeringsfilen ACSD-51892 för att åtgärda prestandaproblemet i Adobe Commerce där felet *Den hämtningsbara länken inte är relaterad till produkten.Kontrollera länken och försök igen*, som inträffar när du uppdaterar startdatumet för en hämtningsbar mellanlagringsuppdatering.
feature: Products, Staging
role: Admin
exl-id: 873357ef-49c3-48f8-a98e-41c48cb9ba8b
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# ACSD-50512: Fel vid uppdatering av startdatum för hämtningsbar mellanlagringsuppdatering

Korrigeringen ACSD-50512 åtgärdar ett problem där felet *Den nedladdningsbara länken är inte relaterad till produkten. Kontrollera länken och försök igen* inträffar när du uppdaterar startdatumet för en hämtningsbar mellanlagringsuppdatering för produkten. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.33 är installerat. Korrigerings-ID är ACSD-51502. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Felet *Den nedladdningsbara länken är inte relaterad till produkten. Kontrollera länken och försök igen* inträffar när du uppdaterar startdatumet för en hämtningsbar mellanlagringsuppdatering för produkten.

<u>Steg som ska återskapas</u>:

1. Skapa en nedladdningsbar produkt med *nedladdningsbara länkar* och *exempellänkar*.
1. Skapa en schemalagd uppdatering för samma produkt och spara produkten.
1. Redigera den förkonfigurerade schemalagda uppdateringen (från steg 2) och ändra startdatumet.
1. Spara den schemalagda uppdateringen.

<u>Förväntade resultat</u>:

Ändringarna i den schemalagda uppdateringen har sparats.

<u>Faktiska resultat</u>:

Du får felmeddelandet: *Den nedladdningsbara länken är inte relaterad till produkten. Verifiera länken och försök igen*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
