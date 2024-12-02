---
title: 'ACSD-49392: Orderstatus ändras till stängd efter partiell återbetalning'
description: Använd patchen ACSD-49392 för att åtgärda Adobe Commerce-problemet där orderstatusen ändras till stängd efter en partiell återbetalning av en paketerad produkt.
exl-id: fca6f502-e224-4444-b0d0-f823853c9458
feature: Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-49392: Orderstatus ändras till stängd efter partiell återbetalning

Korrigeringen ACSD-49392 åtgärdar ett problem där orderstatusen ändras till stängd efter en partiell återbetalning för en paketerad produkt. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.31 har installerats. Korrigerings-ID är ACSD-49392. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.3.7-p4 och 2.4.1 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Beställningsstatusen ändras till stängd efter en partiell återbetalning för en paketerad produkt.

<u>Steg som ska återskapas</u>:

1. Logga in på Adobe Commerce och skapa en paketerad produkt eller använd den befintliga paketerade produkten.
1. Gör en beställning av den här paketerade produkten med en kvantitet som är större än 1.
1. Gå till admin och öppna den order som skapades i steg 2 från **[!UICONTROL Sales]** > **[!UICONTROL Order]** och skapa en faktura. Observera orderstatus. Den kommer att bearbetas.
1. Skapa en partiell kreditnota (återbetala inte för alla produkter i paketet).
1. Kontrollera orderstatus.

<u>Förväntade resultat</u>

När en partiell kreditnota har skapats för den paketerade produkten bearbetas orderstatusen.

<u>Faktiska resultat</u>

När du har skapat en partiell kreditnota för den paketerade produkten är orderstatusen slutförd.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
