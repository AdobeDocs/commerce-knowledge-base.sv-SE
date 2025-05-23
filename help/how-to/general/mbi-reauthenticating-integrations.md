---
title: 'MBI: Återautentiserar integreringar'
description: Den här artikeln innehåller lösningar för att återauktorisera en integrering för att ge Magento Business Intelligence (MBI) de behörigheter som krävs för att hämta data från en tredjepartstjänst. Återauktorisering krävs när dessa behörigheter återkallas.
exl-id: c608d6f9-64a5-44f8-9d7b-9a85a2668775
feature: Commerce Intelligence, Integration
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# MBI: Återautentiserar integreringar

Den här artikeln innehåller lösningar för att återauktorisera en integrering för att ge Magento Business Intelligence (MBI) de behörigheter som krävs för att hämta data från en tredjepartstjänst. Återauktorisering krävs när dessa behörigheter återkallas.

## Integreringar mellan databaser och SaaS

En lista över integreringar mellan databaser och SaaS finns i [Ansluta externa data med hjälp av en integrering](https://experienceleague.adobe.com/sv/docs/commerce-business-intelligence/mbi/analyze/saas/integrations) i utvecklardokumentationen. (Använd innehållsförteckningen till vänster för navigering när du öppnar sidan.)

## Har du anslutningsproblem?

Om du godkänner en integrering får MBI de behörigheter som krävs för att hämta data från en tredjepartstjänst. Återauktorisering krävs när dessa behörigheter återkallas.

Detta kan bero på flera orsaker:

* ett problem med tjänsten från tredje part
* utgångsdatum för autentiseringstoken
* en ändring har gjorts i ditt administratörskonto
* eller en intern utgåva i MBI

Status för alla integreringar finns på integreringssidan ( **Hantera data > Integreringar** ):

![Integrations_page.png](assets/Integrations_page.png)

Om du vill återautentisera måste du kanske ange dina kontouppgifter igen. I vissa fall kanske du måste generera nya API-nycklar för problemintegreringen. Klicka på namnet på den problemintegration som du vill starta omauktoriseringsprocessen.

[Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om problemet kvarstår.
