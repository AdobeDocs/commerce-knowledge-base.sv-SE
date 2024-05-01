---
title: Inkludera en teammedlem i supportmeddelanden
description: I den här artikeln beskrivs hur du inkluderar en teammedlem i supportmeddelanden.
feature: Cloud, Support, Admin Workspace
role: Admin, Developer
exl-id: 63ea3f60-a509-447c-ac3d-bb2133141c80
source-git-commit: 1c568d75534bbfe322d9f980b40c5dd64fc5b7a2
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Inkludera en teammedlem i supportmeddelanden

I den här artikeln beskrivs hur du inkluderar en teammedlem som automatiskt får supportuppdateringar via e-postmeddelanden.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen, alla [versionerna](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Orsak

* Teammedlemmen har inte lagts till i [!DNL cloud project] med nödvändiga privilegier.
* Teammedlemmen har inget supportkonto.

## Lösning

1. Gå till **[!DNL Cloud Project URL]** (Exempel: `https://us-3.magento.cloud/projects/xxxxxx/edit`).
1. Verifiera om teammedlemmen har lagts till i projektet och är en [!DNL Super User].

Om de inte kräver [!DNL cloud project] behörighet, skicka [Supportförfrågan hos Adobe Commerce Support Center](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) till CC automatiskt: de finns på alla biljetter och tillhandahåller även **[!DNL MAGE ID]** (om tillgängligt).

Om de inte har lagts till i projektet måste du lägga till dem som en [!DNL Super User] och bidrag [!DNL Shared Access]:

* [Hantera användaråtkomst](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) i vår användarhandbok.
* [Det går inte att lägga till användare i Adobe Commerce molnprojekt](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html) i Commerce Knowledge Base.
* [Användarhandbok för Adobe Commerce Help Center: Delad åtkomst](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#shared-access) i Commerce Knowledge Base.

Om de har lagts till i [!DNL cloud project], men har inte [!DNL Super User role], uppdatera deras [!DNL role] i enlighet med [Hantera användaråtkomst](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).

## Relaterad läsning

[Före detta teammedlemmar får Adobe Commerce molnmeddelanden via e-post](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html)
