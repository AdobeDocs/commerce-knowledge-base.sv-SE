---
title: 'B2B-2674: Lägger till cachelagring i GraphQL-frågan customAttributeMetadata'
description: Använd korrigeringen B2B-2674 för att lägga till cachelagring i GraphQL-frågan customAttributeMetadata.
feature: Attributes, B2B, Cache, GraphQL
role: Admin
exl-id: a4efb268-f811-41f2-a788-a8cfc3016f61
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# B2B-2674: Lägger till cachelagring i GraphQL-frågan `customAttributeMetadata`

B2B-2674-korrigeringen lägger till cachelagringsfunktioner i GraphQL-frågorna för `customAttributeMetadata`. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 har installerats. Korrigerings-ID är B2B-2674. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7-beta1.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

`customAttributeMetadata` GraphQL-frågan är inte cachelagrad.

<u>Förutsättningar</u>:

* Servern pekar på [!DNL Varnish] som proxar till Adobe Commerce serverdel.
* Konfigurationsinställningen `system/full_page_cache/caching_application` är inställd på **&#x200B; ([!DNL Varnish]), eller gå till Adobe Commerce Admin > &#x200B;** [!UICONTROL Stores] **&#x200B; > &#x200B;** [!UICONTROL System] **&#x200B; > &#x200B;** [!UICONTROL Full Page Cache] **&#x200B; > &#x200B;** [!UICONTROL Caching Application]** > och ställ in den på [!DNL Varnish].

När korrigeringen har installerats utför du följande steg för att se till att det nu finns möjlighet till cachelagring:

1. Skicka `GET`-begäran till den GraphQL-fråga som anges ovan med hjälp av eventuella godtyckliga fält.
1. Skicka om begäran utan att göra några ändringar. Du kommer att märka att den går mycket snabbare. Observera att begäran inte skickas till serverdelen, men hanteras fullständigt av [!DNL Varnish] som en cacheträff.
1. Om ytterligare korrektur krävs kommenterar du bort det `X-Magento-Debug`-huvud som finns i [VCL](https://github.com/magento/magento2/blob/2.4-develop/app/code/Magento/PageCache/etc/varnish6.vcl#L239), startar sedan om [!DNL Varnish] och kör stegen ovan igen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
