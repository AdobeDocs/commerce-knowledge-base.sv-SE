---
title: "ACSD-51845: Det går inte att uppdatera efterföljande produkter med nivåpriser och olika attributuppsättningar via en synkroniserad bulk [!DNL API]"
description: Använd korrigeringsfilen ACSD-51845 för att åtgärda Adobe Commerce-problemet där du inte kan uppdatera efterföljande produkter med nivåpriser och olika attributuppsättningar via asynkron bulk [!DNL REST API].
feature: REST, Products
role: Admin
exl-id: c3fff9f2-30ad-4bcb-945e-e9e0c69630b3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51845: Det går inte att uppdatera efterföljande produkter med nivåpriser och olika attributuppsättningar via en synkroniserad bulk [!DNL API]

Korrigeringen ACSD-51845 åtgärdar ett problem där du inte kan uppdatera efterföljande produkter med nivåpriser och olika attributuppsättningar via asynkron bulk [!DNL REST API]. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 är installerat. Korrigerings-ID är ACSD-51845. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Uppdateringen misslyckas för efterföljande produkter med nivåpriser och olika attributuppsättningar via asynkron bulk [!DNL REST API].

<u>Steg som ska återskapas</u>:

1. Konfigurera [!DNL RabbitMQ].
1. Skapa två attribut.
1. Skapa två **Enkla produkter**, tilldelar varje produkt en egen attributuppsättning.
1. Lägg till en **Kundgruppspris** för varje produkt.
1. Uppdatera båda produkterna i samma grupp [!DNL API] uppdatera.
1. Se till att `bin/magento queue:consumers:start async.operations.all` kommandot körs.
1. Kontrollera massan [!DNL API] status.

<u>Förväntade resultat</u>:

Tjänsten har körts.

<u>Faktiska resultat</u>:

Systemet returnerar felmeddelandet: *Det gick inte att spara produkten. Försök igen.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
