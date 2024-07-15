---
title: Det går inte att logga in på Adobe Commerce support eller molnkonto
description: Den här artikeln innehåller en lösning när du har svårt att logga in på Adobe Commerce support eller ditt molnprojekt.
exl-id: 676b32d2-8197-4c60-a1b1-3c51b01dd3a3
feature: Cloud, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Det går inte att logga in på Adobe Commerce support eller molnkonto

Den här artikeln innehåller en lösning när du har svårt att logga in på Adobe Commerce support eller ditt molnprojekt.

## Berörda produkter och versioner

Adobe Commerce (alla distributionsmetoder) alla [versioner som stöds](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problem

När du går till [https://account.magento.com/customer/account/login/](https://account.magento.com/customer/account/login/) eller [https://accounts.magento.cloud/user](https://accounts.magento.cloud/user) kanske du märker att det nu finns ett enhetligt inloggningsformulär och att du inte längre kan ange dina inloggningsuppgifter som du har gjort tidigare.

<u>Steg som ska återskapas</u>:

Försök att logga in på ditt Commerce-konto.

![adobe-login-one](assets/adobe-login-one.png)

<u>Förväntat resultat</u>:

Inloggningen har slutförts.

<u>Faktiskt resultat</u>:

Du omdirigeras till en sida om du vill logga in med ett Adobe-konto och autentiseringsuppgifterna fungerar inte.

![adobe-login-two](assets/adobe-login-two.png)


## Orsak

Som en del av vår process med att integrera Adobe Commerce med andra Adobe-lösningar måste alla användare skapa en inloggning för Adobe - om de inte redan har en - med samma e-postadress som är kopplad till deras MageID.

## Lösning

Du kan logga in på kontot med:

- Ett befintligt företagskonto/personkonto för Adobe.
- Om du inte har något Adobe-konto skapar du ett med samma e-postadress.

Anvisningar finns i [Commerce Identity Manager](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-identity-manager.html) i Adobe Experience League.

## Relaterad läsning

- [Länka Magento.com och konton.magento.cloud-kontoinloggningar](/help/faq/general/linking-magento-com-and-accounts-magento-cloud-account-logins.md)
