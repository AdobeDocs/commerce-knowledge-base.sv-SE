---
title: Ont om diskutrymme
description: I den här artikeln ges förslag på lösningar för situationen när utrymmet tar slut i en viss miljö i Adobe Commerce för molninfrastruktur.
exl-id: 1b2c25d3-ca1b-4409-8d6b-378aa0952f94
feature: Storage, Observability
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Ont om diskutrymme

I den här artikeln ges förslag på lösningar för situationen när utrymmet tar slut i en viss miljö i Adobe Commerce för molninfrastruktur.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen, alla [versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Diskutrymmet på disken med skrivbara kataloger är snart slut. Ett symtom kan vara [fast distribution](/help/troubleshooting/deployment/deployment-stuck-with-unable-to-upload-the-application-to-the-remote-cluster-error.md).

Kör följande kommando för att kontrollera diskanvändningen:

```bash
df -h var/
```

## Orsak

Katalogen `var` är oftast den som kan ta mycket utrymme och enkelt kan rensas.

Adobe Commerce lagrar alla loggfiler i katalogen `var`. Nya loggfiler skapas och gamla arkiveras dagligen. Men om antalet genererade fel fortsätter att öka tar loggfilerna mer och mer utrymme.

Anpassade import-/exportfiler lagras också i katalogen `var` och tar plats om antalet ökar.

## Lösning

Lösningsalternativ:

* Kontrollera om du har stora loggfiler och ta reda på varför de är stora, åtgärda problemet med att generera stora mängder loggutdata.
* Rensa katalogen `var`.
* Konfigurera ett cron-jobb för att spåra storleken på katalogen `var` och rensa den.
* Allokera mer diskutrymme om du inte har använt något. (Se avsnittet nedan för mer information om hur du kontrollerar din utrymmesgräns.)
   * I Starter-planen, alla miljöer och Pro-planintegreringsmiljöer kan du allokera diskutrymme om du inte har använt något, vilket beskrivs i [Hantera diskutrymme: Allokera diskutrymme](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#application-disk-space).
   * För Pro-planmiljöer för mellanlagrings- och produktionsmiljöer kontaktar du support för att tilldela mer diskutrymme om du har oanvänt något.
* Om du har nått din utrymmesgräns och fortfarande har problem med lite utrymme kan du överväga att köpa mer diskutrymme. Kontakta Adobe Account Team för mer information.

### Kontrollera diskutrymmesgräns

Så här ser du hur mycket utrymme du har för varje Adobe Commerce i molninfrastrukturmiljö:

1. Logga in på [molnkonsolen](https://console.adobecommerce.com).
1. Välj det relevanta projektet på kontrollpanelen **[!UICONTROL All projects]**. I det vänstra hörnet ser du tillgängligt diskutrymme.

   ![project_space.png](/help/troubleshooting/miscellaneous/assets/project_space.png)
