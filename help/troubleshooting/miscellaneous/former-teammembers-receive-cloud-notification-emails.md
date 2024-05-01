---
title: Före detta teammedlemmar får Adobe Commerce molnmeddelanden via e-post
description: Den här artikeln innehåller en lösning på e-postmeddelanden om molninfrastrukturmeddelanden som skickas till tidigare teammedlemmar.
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
source-git-commit: 075f295c5b600fcca9fbecc5aad20b0640d900f9
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Före detta teammedlemmar får Adobe Commerce molnmeddelanden via e-post

Den här artikeln innehåller en lösning där gruppmedlemmar som inte längre är associerade med ditt projekt får meddelanden även fortsättningsvis.

## Problem

Ett meddelande om ett inspelningsfel eller ett viktigt problem med molnprojektet/molnmiljön har skickats till ditt team. Detta inkluderar medlemmar som kanske inte längre är kopplade till ditt projekt, t.ex. externa utvecklare/agentutvecklare eller systemintegratörer. Du vill att de här användarna ska sluta ta emot meddelanden.

## Lösning

Det finns två sätt att stoppa meddelandena genom att ta bort användare från projektet:

* Metod 1: Använda molnet [!DNL Project URL]. Se [Hantera användaråtkomst](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) i Commerce om molninfrastruktur för steg.
* Metod 2: Använda magento-cloud [!DNL CLI]. Se [Hantera användare med [!DNL CLI]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-with-the-cli) i Commerce om molninfrastruktur för steg.

Om detta redan har gjorts och ändå e-postmeddelandena fortsätter att inkludera dessa användare, skickar du en supportanmälan för att begära att de tas bort från *[!UICONTROL Always CC]* inställning för kontot.

## Relaterad läsning

* [Visa en användares projektroll](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#view-a-user’s-project-role) i Commerce om molninfrastruktur.
* [Inkludera en teammedlem i supportmeddelanden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html) i Commerce KB.
