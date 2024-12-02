---
title: 'ACSD-45049: Kundens attributinställning ''Är obligatorisk'' fungerar inte enligt webbplatsomfånget i Admin'
description: Använd korrigeringsfilen ACSD-45049 för att åtgärda Adobe Commerce-problemet där attributet [!UICONTROL Is required] för kund inte har åsidosatts korrekt enligt webbplatsomfånget i Admin.
feature: Attributes, Customers
role: Admin, Developer
exl-id: e6ed7076-9d39-4b01-9e20-50ce296032c0
source-git-commit: 06f751e43ef825c0eb29cb9b42eb41f07c308625
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-45049: Kundens attributinställning *[!UICONTROL Is required]* fungerar inte enligt webbplatsomfånget i Admin

Korrigeringen för ACSD-45049 åtgärdar ett problem där attributinställningen *[!UICONTROL Is required]* för kunden inte fungerar som den ska enligt webbplatsomfånget i Admin. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.50 är installerad. Korrigerings-ID är ACSD-45049. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.4-p7 och 2.4.5 - 2.4.5-p9

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kundens *[!UICONTROL Is required]*-attributinställning fungerar inte korrekt enligt webbplatsomfånget i Admin.

<u>Steg som ska återskapas</u>:

1. Skapa två webbplatser.
1. Öppna **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer attribute]**.
1. Skapa ett nytt attribut, ange **[!UICONTROL Is value required]** = *Nej*.
1. Växla till standardwebbplatsen och ändra **[!UICONTROL Is value required]** = *Ja*. Den andra webbplatsen har standardvärdet.
1. Skapa en ny kund från Admin för den webbplats som inte är standard.

<u>Förväntade resultat</u>:

Attributet krävs inte för den icke-förvalda webbplatsen.

<u>Faktiska resultat</u>:

* Attributet krävs för den icke-förvalda webbplatsen när en kund skapas i Admin.
* Attributet krävs inte för den icke-förvalda webbplatsen när en kund registreras i butiken.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
