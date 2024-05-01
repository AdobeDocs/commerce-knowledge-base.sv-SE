---
title: '''[!DNL Advanced Reporting] 404-fel i Adobe Commerce'
description: Den här artikeln innehåller en patch för Adobe Commerce-utgåvan när en handlare får ett 404-fel när de försöker få åtkomst till [[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html). När den här korrigeringen har installerats kan användarna komma åt den [!DNL Advanced Reporting].
exl-id: bac61704-44fe-4bd2-b342-af90219231ef
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# [!DNL Advanced Reporting] 404-fel i Adobe Commerce

Den här artikeln innehåller en patch för Adobe Commerce-utgåvan när en handlare får ett 404-fel när de försöker få åtkomst till [[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html). När den här korrigeringen har installerats kan användarna komma åt den [!DNL Advanced Reporting].

Kontrollera om den här korrigeringen kan lösa problemet genom att först granska loggarna med följande kommando:

`zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz`

Om du ser `Not valid cipher` fel, använd den bifogade korrigeringen.

## Berörda produkter och versioner

Adobe Commerce 2.2.6

## Problem

En handlare får ett 404-fel när de försöker få åtkomst [!DNL Advanced Reporting].

## Lösning

Åtgärda problemet genom att tillämpa den patch som är bifogad den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk: [Ladda ned MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)

## Så här sätter du på plåstret

Se [Använda en kompositkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) för instruktioner.

## Bifogade filer
