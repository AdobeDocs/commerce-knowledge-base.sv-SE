---
title: Det går inte att komma åt rätt Adobe Commerce-konto/projekt eller så saknas projektet på ditt konto
description: Den här artikeln innehåller en korrigering av problemet när du inte har tillgång till rätt Adobe Commerce-molnprojekt när ägarskap eller e-postadresser har ändrats.
exl-id: 165b9a18-6e84-4f0f-b377-a07152d55c9e
hide: true
hidefromtoc: true
feature: Cloud, Paas
role: Developer
source-git-commit: 423a392eb32df69c38b84081ac2ed17ae1efdc7b
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# Det går inte att komma åt rätt molnkonto/molnprojekt eller så saknas projektet från ditt konto

Den här artikeln innehåller en korrigering för följande problem efter att kontoägarskapet eller de associerade e-postadresserna har ändrats:

1. Du har inte åtkomst till Adobe Commerce-projekt i molnet.
1. Inga Adobe Commerce-projekt i molnet visas under ditt konto på [accounts.magento.cloud/user](https://accounts.magento.cloud/user).
1. Du ser information om ett annat konto (dvs. föregående kontoägare) på [accounts.magento.cloud/user](https://accounts.magento.cloud/user).

## Problem

Du har inte åtkomst till rätt Adobe Commerce-projekt i molnet när ägarskap eller e-postadresser har ändrats.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur, [alla versioner som stöds](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Orsak

Det här problemet inträffar vanligtvis när den tidigare projektägarens enkel inloggning (SSO) fortfarande är integrerad med Adobe.com efter:

1. Ägarskapet för molnprojektet har överförts till dig (användaren) och du ser det ursprungliga projektägarens konto. Klicka här för [lösningen](#solution-for-cause-one-and-two).

   ELLER

1. Du (användaren) har flyttat till ett annat företag, följt av en ändring av e-postadressen och de projekt du har åtkomst till. Du ser de projekt som du har beviljats åtkomst till i din tidigare roll/företag. Klicka här för [lösningen](#solution-for-cause-one-and-two).

   ELLER

1. Du har ändrat din e-postadress på https://account.adobe.com till en annan e-postadress som för närvarande inte är kopplad till ett molnprojekt. Klicka här för [lösningen](#solution-for-cause-three).

## Lösning för orsak ett och två {#solution-for-cause-one-and-two}

Lösningen för när problemet orsakas av ett och två är att koppla från integreringen med enkel inloggning med Adobe.com. Följ stegen nedan för att koppla från:

1. Från https://accounts.magento.cloud/user expanderar du avsnittet **[!UICONTROL Single Sign-On]**. Klicka på **[!UICONTROL Disconnect from Adobe.com]** för att koppla från.

   ![single-sign-on-adobe-connect](assets/sso-adobe-disconnect.png)

1. Klicka på **[!UICONTROL Disconnect]**.

   ![adobe-disconnect](assets/adobe-disconnect.png)

1. Logga ut.
1. Klicka på knappen **[!UICONTROL Adobe.com]**.

   ![Magento.com](assets/adobe-welcome-login.png)

1. Nu bör du kunna se rätt konto och komma åt rätt molnprojekt.

## Lösning för orsak tre {#solution-for-cause-three}

Om problemet har orsakats av tre orsaker ber du en befintlig superanvändare i projektet att lägga till din nya e-postadress i projektet. Mer information finns i [Hantera användaråtkomst](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).
