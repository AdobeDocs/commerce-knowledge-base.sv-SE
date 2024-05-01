---
title: Det går inte att komma åt den senaste förhandsversionen av Adobe Commerce
description: I den här artikeln beskrivs lösningar på problem när du försöker använda den senaste förhandsversionen av Adobe Commerce.
exl-id: cbf54a15-b307-4bfc-90b7-cff98aeb4fce
feature: Roles/Permissions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# Det går inte att komma åt den senaste förhandsversionen av Adobe Commerce

I den här artikeln beskrivs lösningar på problem när du försöker använda den senaste förhandsversionen av Adobe Commerce.

>[!NOTE]
>
>Om du har problem med betaåtkomsten kan du läsa [Det går inte att komma åt den senaste betaversionen](/help/how-to/general/cannot-access-the-latest-beta-version.md) artikel.

## Problem

I den här artikeln beskrivs följande problem med att komma åt koden för förhandsversionen:

* Du kan inte hitta koden för förhandsversionen.
* Det gick inte att hämta den tidiga Adobe Commerce-versionen från [magento.com](https://account.magento.com/customer/account/login) med Composer.

## Orsak

Detta är de vanligaste orsakerna till problem:

* Du letar efter koden för tidig åtkomst på fel plats.
* Du använder fel MageID när du öppnar koden via Composer.
* Ditt konto ingår inte i förhandsversionen.

## Lösning

### Kodplats för tidig åtkomst

Under förhandsversionen finns versionspaket på två platser:

1. Via Composer on [magento.com](https://repo.magento.com/) med det primära MageID:t för kontot. Mer information om hur du använder Composer finns i [Installera Adobe Commerce med Composer](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html) i vår dokumentation för utvecklare.
1. **Mitt konto** > **Nedladdningar** på [account.magento.com](https://account.magento.com/customer/account/login).

>[!NOTE]
>
>Versionspaket är inte tillgängliga på GitHub förrän GA-datumet.

### MageID som du behöver använda

Du måste använda det primära MageID som är kopplat till ditt Adobe Commerce- eller partnerkonto. Förhandsversionen är inte länkad till någon kontakt som har delad åtkomst. Tidig åtkomst är bara tillgänglig via Composer eller [repo.magento.com](https://repo.magento.com/) av det MageID som är kopplat till din Adobe Commerce-licens eller partnerlicens.

#### Hur får jag reda på om mitt MageID är det primära?

**För handlare**

Ta reda på om ditt MageID är primärt genom att göra följande:

1. Logga in [magento.com](https://account.magento.com/customer/account/login) och går till **Mina produkter och tjänster** -fliken. Kontrollera om du ser licensinformationen för Adobe Commerce här:
   * Om du ser licensinformationen för Adobe Commerce är ditt MageID primärt.
   * Om du inte ser licensinformationen för Adobe Commerce har ditt MageID bara delad åtkomst. Om du vill ta reda på vem som har det primära ID:t går du till **Delas med mig** Lägg märke till det SHARENAME som anges där. Klicka **Byt konto** och välj det värde du har noterat i SHARENAME. På välkomstsidan ser du e-postadressen till den primära ID-innehavaren.
1. Om du av någon anledning inte hittar den här informationen på [magento.com](https://account.magento.com/customer/account/login)kontakta kontoteamet på Adobe.
1. Om inget av ovanstående fungerar, [kontakta supporten](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

**För partners**

Ta reda på om ditt MageID är primärt genom att göra följande:

1. Logga in [magento.com](https://account.magento.com/customer/account/login) och går till **Mina produkter och tjänster** -fliken. I underavsnittet Partners ska du kontrollera om du ser den aktiva partnerlicensinformationen:
   * Om du ser den aktiva partnerlicensinformationen är ditt MageID primärt. Partnerlicensen är aktiv om värdet END DATE är ett datum i framtiden.
   * Om du inte ser den aktiva partnerlicensinformationen har ditt MageID bara delad åtkomst. Om du vill ta reda på vem som har det primära ID:t går du till **Delas med mig** Lägg märke till det SHARENAME som anges där. Klicka **Byt konto** och välj det värde du har noterat i SHARENAME. På välkomstsidan ser du e-postadressen till den primära ID-innehavaren.
1. Om du av någon anledning inte hittar den här informationen på [magento.com](https://account.magento.com/customer/account/login)kontaktar du din Partner Manager.
1. Om inget av ovanstående fungerar, [с kontaktsupport](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Inte en del av programmet för förhandsversioner

För att kunna inkluderas i programmet för åtkomst före lansering måste din organisation ha ett aktivt Adobe Commerce- eller partnerkonto som är i gott skick. Om du tror att du uppfyller dessa kriterier och inte kan komma åt koden för förhandsversionen, vänligen [kontakta supporten](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) med ditt MageID.
