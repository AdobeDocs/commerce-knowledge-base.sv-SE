---
title: '''[!UICONTROL Recommendations] [!DNL JS] fel efter uppgradering till Adobe Commerce version 2.4.5'
description: I den här artikeln finns en fix för när det efter uppgraderingen till Adobe Commerce (alla distributionsmetoder) finns [!DNL JS] fel i konsolen relaterade till produkten [!UICONTROL Recommendations] moduler.
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# [!UICONTROL Recommendations] [!DNL JS] fel efter uppgradering till Adobe Commerce version 2.4.5

I den här artikeln finns en fix för när det efter uppgraderingen till Adobe Commerce (alla distributionsmetoder) finns [!DNL JS] fel i konsolen relaterade till produkten [!UICONTROL Recommendations] moduler/enheter.

Det finns för närvarande inga planer på att åtgärda detta problem i framtida versioner.

## Berörda versioner och produkter

* Adobe Commerce (alla distributionsmetoder) vid uppgradering till version 2.4.5

## Problem

Problemet orsakas av att webbplatsen storefront fortfarande refererar till en borttagen produkt [!UICONTROL Recommendations] moduler/enheter (block och/eller widgetar) på startsidan [!DNL CMS].

<u>Steg som ska återskapas</u>:

1. Uppgradera till Adobe Commerce 2.4.5.
1. Gå till butikens webbsida.
1. Högerklicka med musen och välj **Inspect** för att öppna webbinspektören i webbläsaren.
1. Klicka på **[!UICONTROL Console]** -fliken.
1. Granska [!DNL JS] fel.

<u>Förväntade resultat</u>:

Lyckad uppgradering utan [!DNL JS] fel.

<u>Faktiska resultat</u>:

Flera olika typer av [!DNL JS] fel visas i webbläsarkonsolen.

## Tillfällig lösning

Du kan komma runt problemet genom att granska alla [!UICONTROL Recommendations] enheter som du har använt på sidan och tagit bort borttagna enheter.
