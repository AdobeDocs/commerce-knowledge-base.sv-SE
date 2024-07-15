---
title: Före detta teammedlemmar får Adobe Commerce molnmeddelanden via e-post
description: Den här artikeln innehåller en lösning på e-postmeddelanden om molninfrastrukturmeddelanden som skickas till tidigare teammedlemmar.
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
source-git-commit: 0017d43e221ef3023630f714c34aa65b368e214f
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# Före detta teammedlemmar får Adobe Commerce molnmeddelanden via e-post

Den här artikeln innehåller en lösning för att ta bort användare från mottagarens lista med e-postmeddelanden som är:
* Tidigare teammedlemmar som inte längre är kopplade till ditt projekt.
* Aktuella teammedlemmar som inte ska ta emot meddelanden.

## Problem

Ett meddelande om ett inspelningsfel eller ett viktigt problem med molnprojektet/molnmiljön har skickats till ditt team. Detta inkluderar medlemmar som kanske inte längre är kopplade till ditt projekt, t.ex. externa utvecklare/agentutvecklare eller systemintegratörer. Du vill att de här användarna ska sluta ta emot meddelanden.

## Lösning

Det finns två sätt att stoppa meddelandena genom att ta bort användare från projektet:

* Metod 1: Använder molnet [!DNL Project URL]. Mer information finns i [Hantera användaråtkomst](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) i guiden för molninfrastruktur för Commerce.
* Metod 2: Använder magento-cloud [!DNL CLI]. Mer information finns i [Hantera användare med  [!DNL CLI]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-with-the-cli) i guiden för molninfrastruktur i Commerce.

Om detta redan har gjorts och e-postmeddelandena fortfarande omfattar dessa användare, skickar du en supportanmälan och begär att de tas bort från inställningen *[!UICONTROL Always CC]* för kontot.

## Relaterad läsning

* [Visa en användares projektroll](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#view-a-user’s-project-role) i guiden för Commerce om molninfrastruktur.
* [Så här inkluderar du en teammedlem i supportmeddelanden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html) i Commerce KB.
