---
title: Det går inte att lägga till användare i Adobe Commerce molnprojekt
description: Den här artikeln innehåller en lösning för när du inte kan lägga till en användare i ett Adobe Commerce-molnprojekt.
exl-id: 59940916-bf92-4e89-a6f9-bca87c54125c
feature: Cloud, Paas
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Det går inte att lägga till användare i Adobe Commerce molnprojekt

Den här artikeln innehåller en lösning för när du försöker lägga till en användare i ett molnprojekt, men den misslyckas med ett fel: *Användare XXX finns inte*.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur, [alla versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Den här artikeln innehåller en lösning för när du inte kan lägga till en användare i ett Adobe Commerce-molnprojekt.

## Orsak

Detta är det förväntade beteendet. Användarens konto bör först skapas på https://accounts.magento.cloud och länkas till Adobe SSO för att kunna läggas till som användare i projektet.

## Lösning

1. Be användaren logga in på sitt konto på https://accounts.magento.cloud (de måste ha registrerat sig för ett konto på adobe.com under den e-postadressen). Att skapa/ha ett konto på https://account.adobe.com innebär inte automatiskt att användaren skulle ha ett konto på https://accounts.magento.cloud)
Obs! Om användaren har ett konto på account.magento.com eller accounts.magento.cloud före augusti 2022, har han/hon kanske inget konto med/på adobe.com såvida han/hon inte har skapat det i augusti 2022 eller senare. Om användaren har ett Adobe-konto och inte kan logga in skickar du ett e-postmeddelande till [Grp-Magento-HelpCenterLoginIssues@adobe.com](mailto:Grp-Magento-HelpCenterLoginIssues@adobe.com) med information.
1. Användaren ska sedan gå till https://accounts.magento.cloud.
1. När de har gjort det bör du kunna lägga till användaren i projektet. Anvisningar om hur du gör detta finns i [Lägga till användare och hantera åtkomst](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-users-and-manage-access) i vår guide för Commerce om molninfrastruktur.

## Relaterad läsning:

* [Hantera användaråtkomst](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) i vår Commerce on Cloud Infrastructure Guide.
* [Det går inte att logga in på Adobe Commerce support eller molnkontot](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html)
