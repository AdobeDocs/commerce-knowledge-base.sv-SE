---
title: UPS-API:er har tagits bort
description: UPS-API:er är tillfälligt föråldrade eftersom Adobe Commerce-integreringen med UPS inte stöder säkerhetsmodellen OAuth 2.0. Vi räknar dock med att stödja denna modell i slutet av detta år. Detta påverkar inte nuvarande handlare med genererade API-nycklar eftersom UPS stöder autentisering via API:er fram till 3 juni 2024. Handlare utan genererade nycklar kan inte använda vår integrering, men de kan använda en befintlig integrering från marknadsplatsen.
exl-id: 57cae8df-8f8f-42c6-805b-8d34e3be151d
feature: REST, Identity Management
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# UPS-API:er har tagits bort

UPS-API:er (United Postal Service) är tillfälligt föråldrade eftersom Adobe Commerce-integreringen med UPS för närvarande inte stöder säkerhetsmodellen OAuth 2.0. Vi räknar dock med att kunna ge stöd för denna modell i slutet av 2023. Detta påverkar inte nuvarande handlare med genererade API:er eftersom UPS kommer att stödja autentisering via API:er fram till 3 juni 2024. Handlare utan genererade nycklar kan inte använda vår integrering, men de kan använda en befintlig integrering från marknadsplatsen.

Mer information finns i developer.ups.com: [Guide för migrering av nyckel för utvecklarportal](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914).
