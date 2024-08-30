---
title: 'ACSD-59378: Store-level [!DNL URL] skriver om felaktigt uppdaterat under import'
description: Använd korrigeringsfilen ACSD-59378 för att åtgärda Adobe Commerce-problemet där  [!DNL URL] återskrivningar på butiksnivå inte uppdateras korrekt under importen.
feature: Data Import/Export
role: Admin, Developer
source-git-commit: 3f400c3e325c3f377a5e12170b08615ebeadbcd1
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---


# ACSD-59378: Lagringsnivå [!DNL URL] skriver om felaktigt uppdaterat under import

ACSD-59378-korrigeringen åtgärdar ett problem där [!DNL URL]-omskrivningar på butiksnivå felaktigt uppdateras under importen. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 har installerats. Korrigerings-ID är ACSD-59378. Observera att detta problem har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.5-p5

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.5x (alla versioner av 2.4.5)

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!DNL URL]-omskrivningar på Store-nivå uppdateras felaktigt under importen.

<u>Steg som ska återskapas</u>:

1. Skapa en produkt med `url_key = key_default` i scopet **Alla butiksvyer**.
1. Ange `url_key = key_store` i omfattningen **Standardbutiksvy**.
1. Exportera produkten.
1. Importera en [!DNL CSV]-fil för den här produkten med följande data:
   * Kolumnen `store_view_code` är inställd på *empty* så att den gäller för omfattningen **All Store Views** .
   * `url_key` är inställd på standardnyckeln *`key_default`*.

<u>Förväntade resultat</u>:

[!DNL URL] omskrivningar genereras bara om för butiksvyer där det inte finns någon åsidosatt `url_key` (där standardvärdet `url_key` gäller).

<u>Faktiska resultat</u>:

`key_store` [!DNL URL] omskrivningar tas bort, men [!DNL URL] omskrivningen på nivån **Standardbutiksvy** för produkten är fortfarande inställd på *`key_store`*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
