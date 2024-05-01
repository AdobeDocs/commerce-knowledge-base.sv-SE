---
title: Ont om diskutrymme
description: I den här artikeln ges förslag på lösningar för situationen när utrymmet tar slut i en viss miljö i Adobe Commerce för molninfrastruktur.
exl-id: 1b2c25d3-ca1b-4409-8d6b-378aa0952f94
feature: Storage, Observability
role: Developer
source-git-commit: 9ee4145d5516a37fab1c092d539000627f242a93
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Ont om diskutrymme

I den här artikeln ges förslag på lösningar för situationen när utrymmet tar slut i en viss miljö i Adobe Commerce för molninfrastruktur.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastrukturen, alla [versionerna](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Diskutrymmet på disken med skrivbara kataloger är snart slut. Ett symtom kan vara [fast driftsättning](/help/troubleshooting/deployment/deployment-stuck-with-unable-to-upload-the-application-to-the-remote-cluster-error.md).

Kör följande kommando för att kontrollera diskanvändningen:

```bash
df -h var/
```

## Orsak

The `var` är oftast den som kan ta mycket utrymme och enkelt kan rengöras.

Adobe Commerce lagrar alla loggfiler i `var` katalog. Nya loggfiler skapas och gamla arkiveras dagligen. Men om antalet genererade fel fortsätter att öka tar loggfilerna mer och mer utrymme.

Anpassade import-/exportfiler lagras också i `var` och tar plats om antalet ökar.

## Lösning

Lösningsalternativ:

* Kontrollera om du har stora loggfiler och ta reda på varför de är stora, åtgärda problemet med att generera stora mängder loggutdata.
* Städa `var` katalog.
* Ställ in ett cron-jobb för att spåra storleken på `var` och rensa den.
* Allokera mer diskutrymme om du inte har använt något. (Se avsnittet nedan för mer information om hur du kontrollerar din utrymmesgräns.)
   * För Starter-planen, alla miljöer och Pro-planintegreringsmiljöer kan du allokera diskutrymmet om du inte använder något, vilket beskrivs i [Hantera diskutrymme: Allokera diskutrymme](https://devdocs.magento.com/guides/v2.3/cloud/project/manage-disk-space.html#application-disk-space).
   * För Pro-planmiljöer för mellanlagrings- och produktionsmiljöer kontaktar du support för att tilldela mer diskutrymme om du har oanvänt något.
* Om du har nått din utrymmesgräns och fortfarande har problem med lite utrymme kan du överväga att köpa mer diskutrymme. Kontakta Adobe Account Team för mer information.

### Kontrollera diskutrymmesgräns

Så här ser du hur mycket utrymme du har för varje Adobe Commerce i molninfrastrukturmiljö:

1. Logga in på [Cloud Console](https://console.adobecommerce.com).
1. På **[!UICONTROL All projects]** väljer du relevant projekt. I det vänstra hörnet ser du tillgängligt diskutrymme.

   ![project_space.png](/help/troubleshooting/miscellaneous/assets/project_space.png)
