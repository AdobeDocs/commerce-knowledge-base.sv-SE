---
title: '[!UICONTROL Recommendations] [!DNL JS] fel efter uppgradering till Adobe Commerce version 2.4.5'
description: I den här artikeln finns en korrigering för när det efter uppgraderingen till Adobe Commerce (alla distributionsmetoder) finns  [!DNL JS] fel i konsolen som rör produktmodulerna [!UICONTROL Recommendations].
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# [!UICONTROL Recommendations] [!DNL JS] fel efter uppgradering till Adobe Commerce version 2.4.5

I den här artikeln finns en korrigering för när det efter uppgraderingen till Adobe Commerce (alla distributionsmetoder) finns [!DNL JS] fel i konsolen för produktmodulerna/enheterna i [!UICONTROL Recommendations].

Det finns för närvarande inga planer på att åtgärda detta problem i framtida versioner.

## Berörda versioner och produkter

* Adobe Commerce (alla distributionsmetoder) vid uppgradering till version 2.4.5

## Problem

Problemet orsakas av att butikens webbsida fortfarande refererar till några borttagna produktmoduler/enheter (block och/eller widgetar) på dess hemsida [!DNL CMS].[!UICONTROL Recommendations]

<u>Steg som ska återskapas</u>:

1. Uppgradera till Adobe Commerce 2.4.5.
1. Gå till butikens webbsida.
1. Högerklicka med musen och välj **Inspect** för att öppna webbkontrollen i webbläsaren.
1. Klicka på fliken **[!UICONTROL Console]**.
1. Granska [!DNL JS]-felen.

<u>Förväntade resultat</u>:

Uppgraderingen slutfördes utan [!DNL JS] fel.

<u>Faktiska resultat</u>:

Flera olika typer av [!DNL JS]-fel visas i webbläsarkonsolen.

## Tillfällig lösning

Som en tillfällig lösning kan du granska alla [!UICONTROL Recommendations] enheter som du har använt på sidan och ta bort borttagna enheter.
