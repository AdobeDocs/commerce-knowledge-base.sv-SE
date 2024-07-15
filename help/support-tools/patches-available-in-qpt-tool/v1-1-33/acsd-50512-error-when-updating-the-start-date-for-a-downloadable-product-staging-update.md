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

Korrigeringen ACSD-50512 åtgärdar ett problem där felet *Den hämtningsbara länken inte är relaterad till produkten. Verifiera länken och försök igen*, inträffar när startdatumet för en hämtningsbar mellanlagringsuppdatering för produkten uppdateras. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.33 har installerats. Korrigerings-ID är ACSD-51502. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Felet *Den hämtningsbara länken är inte relaterad till produkten. Verifiera länken och försök igen*, inträffar när startdatumet för en hämtningsbar mellanlagringsuppdatering för produkten uppdateras.

<u>Steg som ska återskapas</u>:

1. Skapa en nedladdningsbar produkt med *nedladdningsbara länkar* och *exempellänkar*.
1. Skapa en schemalagd uppdatering för samma produkt och spara produkten.
1. Redigera den förkonfigurerade schemalagda uppdateringen (från steg 2) och ändra startdatumet.
1. Spara den schemalagda uppdateringen.

<u>Förväntade resultat</u>:

Ändringarna i den schemalagda uppdateringen har sparats.

<u>Faktiska resultat</u>:

Du får felmeddelandet: *Den hämtningsbara länken är inte relaterad till produkten. Verifiera länken och försök igen*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
