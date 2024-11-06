---
title: 'ACSD-48058: produktprisindexet fungerar inte om den paketerade produkten inte tilldelats någon webbplats'
description: Använd patchen ACSD-48058 för att åtgärda problemet med Adobe Commerce där produktprisomindexeringen inte fungerar om den paketerade produkten inte har tilldelats någon webbplats.
exl-id: 691371f1-7f10-4be6-80e4-821e7cf664a6
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-48058: produktprisindex fungerar inte om paketprodukten inte är tilldelad någon webbplats

Korrigeringen ACSD-48058 åtgärdar ett problem där produktprisindexet inte fungerar om den paketerade produkten inte är tilldelad någon webbplats. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 har installerats. Korrigerings-ID är ACSD-48058. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Omindexering av produktpris fungerar inte om den paketerade produkten inte har tilldelats någon webbplats.

<u>Steg som ska återskapas</u>:

1. Gå till Adobe Commerce Admin > **[!UICONTROL Catalog]** > **[!UICONTROL Products]** och skapa en ny paketerad produkt eller redigera en befintlig paketerad produkt.
   * Klicka på fliken **[!UICONTROL Product in Websites]** och avmarkera alla kryssrutor (webbplatser)
   * Spara produkten
1. Utför omindexering.

<u>Förväntade resultat</u>:

Indexeringen har slutförts.

<u>Faktiska resultat</u>:

Följande fel inträffar när produktprisindexet körs:

```bash
Undefined array key <bundel product id > in vendor/magento/module-bundle/Model/ResourceModel/Indexer/Price/DisabledProductOptionPriceModifier.php on line 117
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
