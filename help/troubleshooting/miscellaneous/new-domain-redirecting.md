---
title: Den nya domänen dirigeras om till standarddomänen
description: Den här artikeln innehåller en korrigering av problemet där den nya domänen omdirigeras till standarddomänen i den befintliga eller andra miljön.
exl-id: 88e9eb3f-9b82-4ca3-aa80-e49f360b3eb9
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Den nya domänen dirigeras om till standarddomänen

Den här artikeln innehåller en korrigering av problemet där den nya domänen omdirigeras till standarddomänen i den befintliga eller andra miljön.

## Berörda produkter och versioner

* Adobe Commerce on cloud pro infrastructure (all versions)

## Problem

Den nya domänen dirigeras om till standarddomänen i den aktuella miljön eller till standarddomänen i en annan miljö.

## Orsak

Det inträffar när variablerna inte uppdateras efter att en ny domän har lagts till eller när fel [!DNL Fastly]-tjänst har konfigurerats i miljön.

## Lösning

1. Om domänen omdirigeras inom samma miljö kontrollerar du att du har konfigurerat [Variabler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=sv-SE#modify-variables).
1. Om domänen omdirigeras till en annan miljö kontrollerar du om du har konfigurerat rätt [!DNL Fastly]-tjänst genom att köra följande kommando: `bin/magento fastly:conf:get -s`

>[!NOTE]
>
>Du kan hitta API-autentiseringsuppgifterna för [!DNL Fastly] genom att logga in i varje miljö (mellanlagring/produktion) och kontrollera filen `/mnt/shared/fastly_tokens.txt`. Mer information finns i [Konfigurera [!DNL Fastly] tjänster](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=sv-SE) i Commerce on Cloud Infrastructure Guide.

Om båda konfigurationerna ovan är korrekta skickar du in en supportanmälan.

## Relaterad läsning

* [Checklista för att konfigurera en ny domän](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain.html?lang=sv-SE) i vår kunskapsbas för support.
