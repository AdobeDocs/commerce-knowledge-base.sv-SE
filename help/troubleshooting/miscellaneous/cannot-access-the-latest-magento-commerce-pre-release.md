---
title: Det går inte att komma åt den senaste förhandsversionen av Adobe Commerce
description: I den här artikeln beskrivs lösningar på problem när du försöker använda den senaste förhandsversionen av Adobe Commerce.
exl-id: cbf54a15-b307-4bfc-90b7-cff98aeb4fce
feature: Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# Det går inte att komma åt den senaste förhandsversionen av Adobe Commerce

I den här artikeln beskrivs lösningar på problem när du försöker använda den senaste förhandsversionen av Adobe Commerce.

>[!NOTE]
>
>Om du har problem med Beta åtkomst kan du läsa artikeln [Det går inte att komma åt den senaste versionen av Beta](/help/how-to/general/cannot-access-the-latest-beta-version.md).

## Problem

I den här artikeln beskrivs följande problem med att komma åt koden för förhandsversionen:

* Du kan inte hitta koden för förhandsversionen.
* Det gick inte att hämta Adobe Commerce-versionen för tidig åtkomst från [magento.com](https://account.magento.com/customer/account/login) med Composer.

## Orsak

Detta är de vanligaste orsakerna till problem:

* Du letar efter koden för tidig åtkomst på fel plats.
* Du använder fel MageID när du öppnar koden via Composer.
* Ditt konto ingår inte i förhandsversionen.

## Lösning

### Kodplats för tidig åtkomst

Under förhandsversionen finns versionspaket på två platser:

1. Via Composer på [magento.com](https://repo.magento.com/) med hjälp av det primära MageID:t för kontot. Mer information om hur du använder Composer finns i [Installera Adobe Commerce med Composer](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/composer) i utvecklardokumentationen.
1. **Mitt konto** > **Nedladdningar** på [account.magento.com](https://account.magento.com/customer/account/login).

>[!NOTE]
>
>Versionspaket är inte tillgängliga på GitHub förrän GA-datumet.

### MageID som du behöver använda

Du måste använda det primära MageID som är kopplat till ditt Adobe Commerce- eller partnerkonto. Förhandsversionen är inte länkad till någon kontakt som har delad åtkomst. Tidig åtkomst kan bara göras via Composer eller [repo.magento.com](https://repo.magento.com/) via det MageID som är kopplat till din Adobe Commerce-licens eller partnerlicens.

#### Hur får jag reda på om mitt MageID är det primära?

**För handlare**

Ta reda på om ditt MageID är primärt genom att göra följande:

1. Logga in på [magento.com](https://account.magento.com/customer/account/login) och gå till fliken **Min produkt och tjänster**. Kontrollera om du ser licensinformationen för Adobe Commerce här:
   * Om du ser licensinformationen för Adobe Commerce är ditt MageID primärt.
   * Om du inte ser licensinformationen för Adobe Commerce har ditt MageID bara delad åtkomst. Om du vill ta reda på vem som är primär ID-hållare går du till **Delad med mig**-meddelandet som SHARENAME har angett där. Klicka på **Byt konto** och välj det värde du har angett i SHARENAME. På välkomstsidan ser du e-postadressen till den primära ID-innehavaren.
1. Om du av någon anledning inte kan hitta den här informationen på [magento.com](https://account.magento.com/customer/account/login) kontaktar du ditt Adobe-kontoteam.
1. [Kontakta support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om inget av ovanstående fungerar.

**För partner**

Ta reda på om ditt MageID är primärt genom att göra följande:

1. Logga in på [magento.com](https://account.magento.com/customer/account/login) och gå till fliken **Min produkt och tjänster**. I underavsnittet Partners ska du kontrollera om du ser den aktiva partnerlicensinformationen:
   * Om du ser den aktiva partnerlicensinformationen är ditt MageID primärt. Partnerlicensen är aktiv om värdet END DATE är ett datum i framtiden.
   * Om du inte ser den aktiva partnerlicensinformationen har ditt MageID bara delad åtkomst. Om du vill ta reda på vem som är primär ID-hållare går du till **Delad med mig**-meddelandet som SHARENAME har angett där. Klicka på **Byt konto** och välj det värde du har angett i SHARENAME. På välkomstsidan ser du e-postadressen till den primära ID-innehavaren.
1. Kontakta din Partner Manager om du av någon anledning inte hittar den här informationen på [magento.com](https://account.magento.com/customer/account/login).
1. [с Kontakta support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om inget av ovanstående fungerar.

### Inte en del av programmet för förhandsversioner

För att kunna inkluderas i programmet för åtkomst före lansering måste din organisation ha ett aktivt Adobe Commerce- eller partnerkonto som är i gott skick. Om du tror att du uppfyller det här villkoret och inte kan komma åt koden för förhandsversionen [kontaktar du support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) med ditt MageID.
