---
title: 'ACSD-51528: Olika beteenden för formatering med orm_case'
description: Använd korrigeringsfilen ACSD-51528 för att åtgärda Adobe Commerce-problemet där det finns olika beteenden för formatering med orm_case.
exl-id: dd878321-8032-41f3-8dcd-acb0cc023b44
feature: Variables
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-51528: Olika beteenden för formatering med orm_case

Korrigeringen ACSD-51528 korrigerar olika beteenden för formatering med orm_case. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.32 är installerat. Korrigerings-ID är ACSD-51528. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Olika beteenden för formatering av orm_case.

<u>Steg som ska återskapas</u>:

1. Testa `\Magento\Framework\Api\DataObjectHelper::populateWithArray` med en mängd olika egenskapsnamn.
1. Egenskaperna med namn som *NewPName* bör omvandlas till *new_p_name* i stället omvandlas de till *new_pname*.
1. När du använder *getNewPName* funktionen i objektet, *null* returneras eftersom *Abstrakt modell* kommer att omvandla anropet till *new_p_name* gör båda funktionerna inkompatibla med varandra.

<u>Förväntade resultat</u>

The **[!UICONTROL populateWithArray]** funktionen ska omforma objektegenskaperna till snake_case korrekt, så att den blir kompatibel med **[!DNL AbstractModel's]** `Getters` och `Setters`.

<u>Faktiska resultat</u>

När du använder **[!UICONTROL populateWithArray]** om en objektegenskap som innehåller två eller flera versala bokstäver i en rad i namnet gör att ormen_case-omformningen blir felaktig i den slutliga datarrayen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
