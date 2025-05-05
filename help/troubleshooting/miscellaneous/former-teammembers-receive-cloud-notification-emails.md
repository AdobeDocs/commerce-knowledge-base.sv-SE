---
title: Före detta teammedlemmar får Adobe Commerce molnmeddelanden via e-post
description: Den här artikeln innehåller en lösning på e-postmeddelanden om molninfrastrukturmeddelanden som skickas till tidigare teammedlemmar.
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
source-git-commit: bd199fac6d8f33491b9fa0f508b2bb52d56b46a5
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# Före detta teammedlemmar får Adobe Commerce molnmeddelanden via e-post

Den här artikeln innehåller en lösning för att ta bort användare från mottagarens lista med e-postmeddelanden som är:

* Tidigare teammedlemmar som inte längre är kopplade till ditt projekt.
* Aktuella teammedlemmar som inte ska ta emot meddelanden.

## Problem

Ett meddelande om ett inspelningsfel eller ett viktigt problem med molnprojektet/molnmiljön har skickats till ditt team. Detta inkluderar medlemmar som kanske inte längre är kopplade till ditt projekt, t.ex. externa utvecklare/agentutvecklare eller systemintegratörer. Du vill att de här användarna ska sluta ta emot meddelanden.

## Lösning

>[!NOTE]
>
>Om du är en extern utvecklare/agentutvecklare eller systemintegratör och inte längre är kopplad till projektet, måste du kontakta projektägaren eller projektadministratören för att få hjälp.

Det finns två sätt att stoppa meddelandena genom att ta bort användare från projektet:

* Metod 1: Använder molnet [!DNL Project URL]. Mer information finns i [Hantera användaråtkomst](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=sv-SE) i guiden för molninfrastruktur för Commerce.
* Metod 2: Använder magento-cloud [!DNL CLI]. Mer information finns i [Hantera användare med  [!DNL CLI]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=sv-SE#manage-users-with-the-cli) i guiden för molninfrastruktur i Commerce.

Om detta redan har gjorts och e-postmeddelandena fortfarande omfattar dessa användare, skickar du en supportanmälan och begär att de tas bort från inställningen *[!UICONTROL Always CC]* för kontot.

## Relaterad läsning

* [Visa en användares projektroll](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=sv-SE#view-a-user&?lang=sv-SE#39;s-project-role) i guiden för Commerce om molninfrastruktur.
* [Så här inkluderar du en teammedlem i supportmeddelanden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html?lang=sv-SE) i Commerce KB.
