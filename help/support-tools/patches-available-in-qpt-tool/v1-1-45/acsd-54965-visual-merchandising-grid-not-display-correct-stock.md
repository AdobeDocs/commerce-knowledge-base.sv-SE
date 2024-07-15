---
title: 'ACSD-54965: [!UICONTROL Visual Merchandising]-rutnätet visar inte rätt resurs'
description: Använd ACSD-54965-korrigeringen för att åtgärda Adobe Commerce-problemet där rutnätet [!UICONTROL Visual Merchandising] inte visar rätt lager när en produkt tilldelas till ett anpassat lager.
feature: Merchandising, Categories
role: Admin, Developer
exl-id: 13d98f55-ca2c-4064-b66f-ab2cdeb37382
source-git-commit: 4f05117aa42dec1f56e4986ffd22d1a68bf5cea2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-54965: Rutnätet [!UICONTROL Visual Merchandising] visar inte rätt resurs

Korrigeringen ACSD-54965 åtgärdar ett problem där rutnätet [!UICONTROL Visual Merchandising] inte visar rätt lager när en produkt tilldelas till ett anpassat lager. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 har installerats. Korrigerings-ID är ACSD-54965. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Rutnätet [!UICONTROL Visual Merchandising] visar inte rätt lager när en produkt tilldelas en anpassad Stock.

<u>Steg som ska återskapas</u>:

1. Skapa en ny källa.
1. Skapa en ny aktie.
1. Skapa två produkter:
   * En produkt som endast innehåller det anpassade lagret.
   * En produkt med endast standardlagret.
1. Lägg till de här produkterna i en kategori.
1. Gå till stödrastret [!UICONTROL visual Merchandising] (*[!UICONTROL Products in Category]*).

<u>Faktiska resultat</u>:

I *[!UICONTROL All Store Views]*-omfånget visas ingen kvantitet för produkten med anpassad aktie. Det är bara när omfånget *[!UICONTROL Default Store View]* har valts, som det anpassade lagret visar produktkvantiteten.

<u>Förväntade resultat</u>:

Rutnätet visar all stockinformation om omfattningen är *[!UICONTROL All Store Views]*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
