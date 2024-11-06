---
title: Kan inte komma åt den senaste Beta-versionen
description: I den här artikeln beskrivs lösningar på problem när du försöker använda de senaste Beta-versionerna av koden för Adobe Commerce. Beta-kod är endast tillgänglig för officiella Adobe-partners som har följt den process som beskrivs i [Adobe Commerce Beta Program](https://github.com/magento/magento2/wiki/Magento-Beta-Program).
exl-id: a53c854e-38a8-4c8c-8586-9d99c576c835
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Kan inte komma åt den senaste Beta-versionen

I den här artikeln beskrivs lösningar på problem när du försöker använda de senaste Beta-versionerna av koden för Adobe Commerce. Beta-kod är bara tillgänglig för officiella Adobe-partners som har följt den process som beskrivs i [Adobe Commerce Beta Program](https://github.com/magento/magento2/wiki/Magento-Beta-Program).

## Problem

I den här artikeln beskrivs följande problem med att komma åt koden för tidig åtkomst:

* Adobe Commerce Beta-versionen är inte tillgänglig för hämtning under **Mitt konto** > **Nedladdningar** på [magento.com](https://account.magento.com/customer/account/login).
* Det gick inte att hämta Adobe Commerce-versionen för tidig åtkomst från [magento.com](https://account.magento.com/customer/account/login) med Composer.

## Orsak

Detta är de vanligaste orsakerna till problem:

* Du letar efter koden för tidig åtkomst på fel plats.
* Du använder fel MageID.
* Utvecklaren behöver åtkomstnycklar från rätt MageID.
* Ditt konto ingår inte i Beta.

## Lösning

### Kodplats för tidig åtkomst

Under betaåtkomstperioder är versionspaket endast tillgängliga via Composer på [repo.magento.com](https://repo.magento.com/). Versionspaket är inte tillgängliga på GitHub- och Adobe Commerce-portaler under den här perioden, och vi kommer att publicera dem på dessa platser på GA-datumet. Klicka [här](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer) om du vill ha mer information om hur du använder Composer.

### MageID som du behöver använda

Du måste använda det primära MageID som är kopplat till ditt partnerkonto. Beta-programmet är inte länkat till någon kontakt med delad åtkomst. Tidig åtkomst kan bara göras via Composer eller [repo.magento.com](https://repo.magento.com/) via det MageID som är kopplat till din partnerlicens.

#### Hur får jag reda på om mitt MageID är det primära

Ta reda på om ditt MageID är primärt genom att göra följande:

1. Logga in på [magento.com](https://account.magento.com/customer/account/login) och gå till fliken **Min produkt och tjänster**. I underavsnittet Partners ska du kontrollera om du ser den aktiva partnerlicensinformationen:
   * Om du ser den aktiva partnerlicensinformationen är ditt MageID primärt. Partnerlicensen är aktiv om värdet END DATE är ett datum i framtiden.
   * Om du inte ser den aktiva partnerlicensinformationen har ditt MageID bara delad åtkomst. Om du vill ta reda på vem som är primär ID-hållare går du till **Delad med mig**-meddelandet som SHARENAME har angett där. Klicka på **Byt konto** och välj det värde du har angett i SHARENAME. På välkomstsidan ser du e-postadressen till den primära ID-innehavaren.
1. Kontakta din Partner Manager om du av någon anledning inte hittar den här informationen på [magento.com](https://account.magento.com/customer/account/login).
1. [Kontakta support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed) om inget av ovanstående fungerar.

#### Utvecklaren har inte rätt åtkomst till nycklar

Om du är primär MageID-ägare och behöver ge åtkomst till en utvecklare i ditt team följer du stegen nedan:

1. Låt den primära MageID-ägaren logga in på [account.magento.com](https://account.magento.com/customer/account/login).
1. Välj fliken **Marketplace** och klicka sedan på **Åtkomsttangenter**.
1. Välj **Skapa en ny åtkomstnyckel** och ge den ett namn.
1. Skicka nycklarna till utvecklaren.

### Inte en del av programmet för tidig åtkomst

Vårt Beta Access-program är bara tillgängligt för våra Solution- och Technical Partners så att de kan utvärdera vår förproduktionskod. För att kunna inkluderas i Beta Access-programmet måste din organisation ha ett aktivt partnerkonto för Adobe som är i god ordning och har signerat Beta-sekretessavtal [här](https://github.com/magento/magento2/wiki/Magento-Beta-Program). Om du anser att du uppfyller dessa kriterier och inte kan komma åt betakoden kontaktar du [commercebeta@adobe.com](mailto:commercebeta@adobe.com).
