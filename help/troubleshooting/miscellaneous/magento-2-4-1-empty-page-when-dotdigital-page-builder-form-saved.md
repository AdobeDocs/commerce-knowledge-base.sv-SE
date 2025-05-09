---
title: "Adobe Commerce 2.4.1: tom sida när ett digitalt Page Builder-formulär sparas"
description: I den här artikeln beskrivs en lösning på ett känt fel i Adobe Commerce 2.4.1 som kan användas för att visa en tom webbsida efter att ha sparat ett digitalt Page Builder-formulär på Admin Panel i webbläsaren Safari.
exl-id: 682eac73-1ad2-4093-acfb-6a8da4c05cf5
feature: Page Builder
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Adobe Commerce 2.4.1: tom sida när ett digitalt Page Builder-formulär har sparats

I den här artikeln beskrivs en lösning på ett känt fel i Adobe Commerce 2.4.1 som kan användas för att visa en tom webbsida efter att ha sparat ett digitalt Page Builder-formulär på Admin Panel i webbläsaren Safari.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.4.1
* Adobe Commerce i molninfrastruktur 2.4.1

## Problem

<u>Steg som ska återskapas</u>

1. Gå till **Admin Panel** > **Content** > **Pages** och välj **Edit** of any page.
1. Gå till **Innehåll** och klicka på knappen **Redigera med Page Builder** .
1. Dra blocket **dotdigital form** och välj **Redigera**.
1. Välj något av testformulären, välj sedan **Inbäddat** läge och spara formuläret.
1. Spara sidändringen.

<u>Förväntat resultat:</u>

Webbsidan bör sparas.

<u>Faktiskt resultat:</u>

Webbsidan är tom. När du har läst in webbsidan igen tillämpas ändringarna.

## Tillfällig lösning

Lösningen är att använda en annan webbläsare än Safari. Problemet kommer att åtgärdas i nästa version, Adobe Commerce 2.4.2, under första kvartalet 2021.

## Relaterad läsning

* [Vad är Page Builder?](https://developer.adobe.com/commerce/frontend-core/page-builder/) i vår utvecklardokumentation.
* [Utskriftsformat för Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/setup.html?lang=sv-SE) i utvecklardokumentationen.
* [Page Builder](https://experienceleague.adobe.com/sv/docs/commerce-admin/page-builder/introduction) i vår användarhandbok.
* [Page Builder - Elements](https://experienceleague.adobe.com/sv/docs/commerce-admin/page-builder/workspace#elements) i vår användarhandbok.
