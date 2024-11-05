---
title: Fel efter inloggning på Commerce Admin
description: Den här artikeln innehåller en lösning på problemet där du får ett felmeddelande om att den begärda URL:en inte hittades på den här servern.
exl-id: f52b383b-87f2-4216-9bf4-e765db31ca6b
feature: Admin Workspace
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---

# Fel efter inloggning på Commerce Admin

Den här artikeln innehåller en lösning på problemet där du får ett felmeddelande om att den begärda URL:en inte hittades på den här servern.

## Information

Den begärda URL:en /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ hittades inte på den här servern.

Observera att det inte finns något snedstreck mellan `magento2` och `index.php` i URL:en.

## Lösning

Bas-URL:en är inte korrekt. Bas-URL måste:

* Börja med `http://` eller `https://`
* Sluta med ett snedstreck ( `/` )
* Matcha skiftläget för posten `web/unsecure/base_url` i databastabellen `core_config_data`

Kör installationen igen med ett giltigt värde.

## Relaterad läsning

[Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
