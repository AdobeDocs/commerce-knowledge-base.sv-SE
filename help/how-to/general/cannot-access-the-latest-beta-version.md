---
title: Det går inte att komma åt den senaste betaversionen
description: I den här artikeln beskrivs lösningar på problem när du försöker använda de senaste betaversionerna av kod för Adobe Commerce. Betakod är endast tillgänglig för officiella Adobe-partners som har följt processen som beskrivs i [Adobe Commerce Beta Program](https://github.com/magento/magento2/wiki/Magento-Beta-Program).
exl-id: a53c854e-38a8-4c8c-8586-9d99c576c835
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Det går inte att komma åt den senaste betaversionen

I den här artikeln beskrivs lösningar på problem när du försöker använda de senaste betaversionerna av kod för Adobe Commerce. Betakoden är endast tillgänglig för officiella Adobe-partners som har följt processen som beskrivs i [Adobe Commerce Beta Program](https://github.com/magento/magento2/wiki/Magento-Beta-Program).

## Problem

I den här artikeln beskrivs följande problem med att komma åt koden för tidig åtkomst:

* Adobe Commerce Beta-versionen är inte tillgänglig för nedladdning under **Mitt konto** > **Nedladdningar** på [magento.com](https://account.magento.com/customer/account/login).
* Det gick inte att hämta den tidiga Adobe Commerce-versionen från [magento.com](https://account.magento.com/customer/account/login) med Composer.

## Orsak

Detta är de vanligaste orsakerna till problem:

* Du letar efter koden för tidig åtkomst på fel plats.
* Du använder fel MageID.
* Utvecklaren behöver åtkomstnycklar från rätt MageID.
* Ditt konto ingår inte i betaprogrammet.

## Lösning

### Kodplats för tidig åtkomst

Under betaåtkomstperioder är versionspaket endast tillgängliga via Composer på [repo.magento.com](https://repo.magento.com/). Versionspaket är inte tillgängliga på GitHub- och Adobe Commerce-portaler under den här perioden, och vi kommer att publicera dem på dessa platser på GA-datumet. Mer information om Composer finns i [här](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html).

### MageID som du behöver använda

Du måste använda det primära MageID som är kopplat till ditt partnerkonto. Betaprogrammet är inte länkat till någon kontakt med delad åtkomst. Tidig åtkomst är bara tillgänglig via Composer eller [repo.magento.com](https://repo.magento.com/) av det MageID som är kopplat till din partnerlicens.

#### Hur får jag reda på om mitt MageID är det primära

Ta reda på om ditt MageID är primärt genom att göra följande:

1. Logga in [magento.com](https://account.magento.com/customer/account/login) och går till **Mina produkter och tjänster** -fliken. I underavsnittet Partners ska du kontrollera om du ser den aktiva partnerlicensinformationen:
   * Om du ser den aktiva partnerlicensinformationen är ditt MageID primärt. Partnerlicensen är aktiv om värdet END DATE är ett datum i framtiden.
   * Om du inte ser den aktiva partnerlicensinformationen har ditt MageID bara delad åtkomst. Om du vill ta reda på vem som har det primära ID:t går du till **Delas med mig** Lägg märke till det SHARENAME som anges där. Klicka **Byt konto** och välj det värde du har noterat i SHARENAME. På välkomstsidan ser du e-postadressen till den primära ID-innehavaren.
1. Om du av någon anledning inte hittar den här informationen på [magento.com](https://account.magento.com/customer/account/login)kontaktar du din Partner Manager.
1. Om inget av ovanstående fungerar, [kontakta supporten](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed).

#### Utvecklaren har inte rätt åtkomst till nycklar

Om du är primär MageID-ägare och behöver ge åtkomst till en utvecklare i ditt team följer du stegen nedan:

1. Låt den primära MageID-ägaren logga in på [account.magento.com](https://account.magento.com/customer/account/login).
1. Välj **Marketplace** och sedan klicka på **Åtkomsttangenter**.
1. Välj **Skapa en ny åtkomstnyckel** och ge den ett namn.
1. Skicka nycklarna till utvecklaren.

### Inte en del av programmet för tidig åtkomst

Vårt Beta Access-program är bara tillgängligt för våra Solution- och Technical Partners så att de kan utvärdera vår förproduktionskod. För att kunna inkluderas i betaåtkomstprogrammet måste din organisation ha ett aktivt partnerkonto hos Adobe som är i god position och har signerat betaversionen av sekretessavtal [här](https://github.com/magento/magento2/wiki/Magento-Beta-Program). Om du tror att du uppfyller dessa kriterier och inte kan komma åt betakoden kontaktar du [commercebeta@adobe.com](mailto:commercebeta@adobe.com).
