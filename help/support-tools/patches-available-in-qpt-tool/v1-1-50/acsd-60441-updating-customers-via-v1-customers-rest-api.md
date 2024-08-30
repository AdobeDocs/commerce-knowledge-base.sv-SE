---
title: 'ACSD-60441: Uppdatering av kunder via V1/customers [!DNL REST] API-slutpunkt orsakar ett fel'
description: Använd korrigeringsfilen ACSD-60441 för att åtgärda Adobe Commerce-problemet där det uppstår ett fel när du uppdaterar kunder via V1/customers [!DNL REST] API när du använder en integreringsåtkomsttoken som genererats från backend.
feature: REST, Customers
role: Admin, Developer
source-git-commit: ea62d2387ab0c04fe44291df431f42d78a0d2f2a
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# ACSD-60441: Uppdatering av kunder via `V1/customers` [!DNL REST] API-slutpunkt ger ett fel

Korrigeringen ACSD-60441 åtgärdar ett problem där en uppdatering av kunder via `V1/customers` [!DNL REST] API när integreringsåtkomsttoken som genererats från serverdelen används orsakar ett fel. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 har installerats. Korrigerings-ID är ACSD-60441. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p8

**Kompatibel med Adobe Commerce-versioner**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p9, 2.4.5-p8, 2.4.6-p6, 2.4.7-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Uppdatering av kunder via API-slutpunkten `V1/customers` [!DNL REST] när integreringsåtkomsttoken som genererats från serverdelen används genererar ett fel.

<u>Steg som ska återskapas</u>:

1. Skapa en integrering från administratören.
1. Skicka en [!DNL POST]-begäran till `rest/default/V1/customers/<customer_id>` med integreringstoken.

   ```json
   {
     "customer": {
       "email": "roni_cost@example.com",
       "firstname": "Veronica",
       "lastname": "Costello"
     }
   }
   ```

<u>Förväntade resultat</u>:

Kunddata uppdateras.

<u>Faktiska resultat</u>:

Du får följande fel:

    &quot;json
    {
    &quot;message&quot;: &quot;En kund med samma e-postadress finns redan på en associerad webbplats.&quot;,
    &quot;trace&quot;: ...
    }
    &quot;

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
