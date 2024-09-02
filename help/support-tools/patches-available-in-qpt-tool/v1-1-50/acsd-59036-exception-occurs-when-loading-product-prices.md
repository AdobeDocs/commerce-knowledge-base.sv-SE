---
title: 'ACSD-59036: Ett undantag inträffar när produktpriser läses in med både nedre och övre gränser inställda på $0'
description: Använd patchen ACSD-59036 för att åtgärda Adobe Commerce-problemet där ett undantag inträffar när du läser in produktpriser med både nedre och övre gränser inställda på *$0*.
feature: Categories, Products, Storefront, Search
role: Admin, Developer
source-git-commit: d711fb8ff8876a4a514daade6d7df4d7cf7e3593
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---


# ACSD-59036: Ett undantag inträffar när produktpriser läses in med både nedre och övre gränser inställda på *$0*

Korrigeringen ACSD-59036 åtgärdar ett problem där ett undantag inträffar när produktpriser läses in med både nedre och övre gränser inställda på *$0*. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 har installerats. Korrigerings-ID är ACSD-59036. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.7

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett undantag inträffar när produktpriser läses in med både nedre och övre gränser inställda på *$0*.

Problemet inträffar eftersom algoritmen inte tar hänsyn till NULL-värden när frågan läses in med prisintervall. För att åtgärda detta kan vi kontrollera om både det nedre och det övre intervallet är NULL, och om det är det, tilldela värdet *0* för båda gränserna. Detta bör förhindra att fel uppstår.

<u>Steg som ska återskapas</u>:

1. Skapa *13* enkla produkter.
1. Tilldela alla *13*-produkter till en kategori.
1. Ange priset för en produkt till *$1322.94*.
1. Ange priset för alla andra produkter till *$0*.
1. Konfigurera [!DNL OpenSearch] som en sökmotor.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]** och ställ in antalet **[!UICONTROL PLP]** till *16*.
1. Ange **[!UICONTROL Price Navigation Step Calculation]** som *Automatisk (utjämna produktantal)*.
1. Kör fullständig omindexering.
1. Öppna sidan *[!UICONTROL Category]*.

<u>Förväntade resultat</u>:

På sidan *[!UICONTROL Category]* visas alla produkter.

<u>Faktiska resultat</u>:

Ett fel inträffar:

```JSON
report.CRITICAL: OpenSearch\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]"}],"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [filter]","caused_by":{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]","caused_by":{"type":"illegal_argument_exception","reason":"field name is null or empty"}}},"status":400} in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Connections/Connection.php:664
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
