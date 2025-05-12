---
title: Inkludera en teammedlem i supportmeddelanden
description: I den här artikeln beskrivs hur du inkluderar en teammedlem i supportmeddelanden.
feature: Cloud, Support, Admin Workspace
role: Admin, Developer
exl-id: 63ea3f60-a509-447c-ac3d-bb2133141c80
source-git-commit: 6a4c1115aa92663ce12ce848dc583538e155509b
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Inkludera en teammedlem i supportmeddelanden

I den här artikeln beskrivs hur du inkluderar en teammedlem som automatiskt får supportuppdateringar via e-postmeddelanden.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen, alla [versioner som stöds](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Orsak

* Teammedlemmen har inte lagts till i [!DNL cloud project] med nödvändiga privilegier.
* Teammedlemmen har inget supportkonto.

## Lösning

1. Gå till **[!DNL Cloud Project URL]** (Exempel: `https://us-3.magento.cloud/projects/xxxxxx/edit`).
1. Kontrollera om teammedlemmen har lagts till i projektet och är en [!DNL Super User].

Om de inte har lagts till i projektet måste du lägga till dem som en [!DNL Super User] och bevilja [!DNL Shared Access]:

* [Hantera användaråtkomst](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=sv-SE) i vår användarhandbok.
* [Det går inte att lägga till användare i Adobe Commerce molnprojekt](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html?lang=sv-SE) i Commerce kunskapsbas.
* [Användarhandbok för Adobe Commerce Help Center: Delad åtkomst](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=sv-SE#shared-access) i Commerce Knowledge Base.

Om de har lagts till i [!DNL cloud project], men inte har [!DNL Super User role], uppdaterar du deras [!DNL role] i [Hantera användaråtkomst](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=sv-SE).

Om du vill att en teammedlem ska kunna bevaka alla ärenden som har öppnats för din organisation skickar du en [supportanmälan](https://experienceleague.adobe.com/home?lang=sv-SE&amp;support-tab=home#support).

## Relaterad läsning

[Före detta teammedlemmar får e-postmeddelanden om molnmeddelanden från Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html?lang=sv-SE)
