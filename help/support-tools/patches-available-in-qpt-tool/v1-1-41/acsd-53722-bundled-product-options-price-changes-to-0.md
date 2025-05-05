---
title: 'ACSD-53722: Prisändringar för programpaket till $0'
description: Använd patchen ACSD-53722 för att åtgärda Adobe Commerce-problemet där priset för de paketerade produktalternativen ändras till $0 när schemalagda uppdateringar för olika omfång aktiveras.
feature: Products
role: Admin, Developer
exl-id: da4c25ac-78bc-4d4e-a55e-826924a099e9
source-git-commit: e587b70a270bca624fb60a1b0940c05221da3aef
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-53722: Prisändringar för programpaket till $0

Korrigeringen ACSD-53722 åtgärdar ett problem där priset för de paketerade produktalternativen ändras till $0 när schemalagda uppdateringar för olika omfång aktiveras. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 har installerats. Korrigerings-ID är ACSD-53722. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Priset för paketerade produktalternativ ändras till $0 när schemalagda uppdateringar för olika omfång aktiveras.

<u>Steg som ska återskapas</u>:

1. Skapa två webbplatser, A och B.
1. Ange konfigurationen under **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]** = **[!UICONTROL Website]**.
1. Skapa en paketprodukt med ett fast pris på webbplatserna A och B:

   * Paketerat produktpris = Fast = *0*

1. Lägg till en enkel produkt som ett nedrullningsbart alternativ för paketet. Ange följande priser:

   * Den enkla produktens pris för alla butiksvyer i paket = *120*
   * Enkel produkts webbplats Ett pris inuti paket = *130*
   * Den enkla produktens webbplats B-pris inuti paket = *140*

1. Schemalägg en uppdatering för att inaktivera den paketerade produkten på webbplats A.

<u>Förväntade resultat</u>:

Den schemalagda uppdateringen för webbplats A påverkar inte priset för webbplats B.

<u>Faktiska resultat</u>:

Efter den schemalagda uppdateringen ändras priset på produktalternativet för paket på webbplats B till **$0**.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
