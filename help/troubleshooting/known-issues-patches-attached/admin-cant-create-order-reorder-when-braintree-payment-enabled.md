---
title: Administratören kan inte skapa en order eller beställa om när Braintree-betalning är aktiverat
description: Den här artikeln innehåller en patch för Adobe Commerce 2.4.5-utgåvan där en Admin-användare inte kan skapa order eller beställningar för kunder när betalningsmetoden Braintree är aktiverad.
exl-id: 8840aecb-21d9-4965-8c09-395e2d263aaa
feature: Admin Workspace, Native Luma Frontend Development, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Administratören kan inte skapa en order eller beställa om när Braintree-betalning är aktiverat

Den här artikeln innehåller en patch för Adobe Commerce 2.4.5-utgåvan där en Admin-användare inte kan skapa order eller beställningar för kunder när betalningsmetoden Braintree är aktiverad.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur 2.4.5
* Adobe Commerce lokal 2.4.5
* Magento Open Source 2.4.5

## Problem

<u>Steg som ska återskapas</u>:

1. Integreringen av Braintree används (**Lagrar** > **Konfigurationer** > **Försäljning** > **Betalningsmetod** > **Braintree**).
1. Gör en beställning med Luma Storefront.
1. Gå till Admin UI > **Sales**.
1. Försök antingen att skapa en ny order för en kund eller gå till en tidigare placerad order och klicka på **Ändra ordning**.

<u>Förväntat resultat</u>:

Administratörsanvändare kan skapa order och ombeställningar för kunder när betalningsmetoden Braintree är aktiverad.

<u>Faktiskt resultat</u>:

Administratörsanvändare kan inte skapa beställningar eller ombeställningar för kunder när betalningsmetoden Braintree är aktiverad och returnerar följande fel:

```bash
report.CRITICAL: Error: Call to a member function getMethodInstance() on null in /app/vendor/paypal/module-braintree-core/Block/Form.php:174
```

## Orsak

Felaktiga klassberoenden (`vendor/paypal/module-braintree-core/Block/Form.php`)

## Lösning

Använd den patch som finns i den här artikeln.

## Lappa

Korrigeringen är kopplad till den här artikeln. Klicka på följande länk om du vill hämta den:

[BUNDLE-3137-composer.patch.zip](assets/BUNDLE-3137-composer.patch.zip)

>[!NOTE]
>
>Dessutom för Adobe Commerce på återförsäljare av molninfrastruktur: Adobe har tagit med korrigeringen i Cloud Patches for Commerce version 1.0.18. Se [Cloud Patches for Commerce release notes](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches) i utvecklardokumentationen för att hitta instruktioner om hur du använder det senaste paketet.

### Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce i molninfrastruktur 2.4.5
* Adobe Commerce lokal 2.4.5
* Magento Open Source 2.4.5

>[!NOTE]
>
>Korrigeringen är inte kompatibel med andra versioner och utgåvor av Adobe Commerce och Magento Open Source.

## Så här sätter du på plåstret

Mer information finns i [Använda en dispositionsruta från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.
