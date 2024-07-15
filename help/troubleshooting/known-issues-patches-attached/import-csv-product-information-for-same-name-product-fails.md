---
title: Det gick inte att importera CSV-produktinformation för samma namnprodukt
description: I den här artikeln finns en patch för det kända Adobe Commerce 2.2.3-problemet som rör fel vid import av en ".csv"-fil med produktinformation om det finns produkter med samma namn.
exl-id: 420b0283-455a-4bd5-ba51-18f341ddacd5
feature: Data Import/Export, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Det gick inte att importera CSV-produktinformation för samma namnprodukt

I den här artikeln finns en korrigering för det kända Adobe Commerce 2.2.3-problemet som rör fel vid import av en `.csv`-fil med produktinformation om det finns produkter med samma namn.

## Problem

När en `.csv`-fil med produktinformation importeras och det finns produkter med samma namn visas följande fel i steget Kontrollera data: *`URL Key XYZ was already generated for an item with the SKU %sku%"`*. Problemet orsakas av att produkternas URL-adresser skrivs om under importen, även när det inte finns någon kolumn för produkternas URL-adresser i den importerade `.csv`-filen.

<u>Steg som ska återskapas</u>:

1. Skapa två konfigurerbara produkter med samma namn i Commerce Admin.
1. Skapa en `.csv`-fil för att importera data för dessa produkter, som till exempel har följande kolumner: `sku` | `product_type` | `name` | `product_websites` | `store_view_code`
1. Gå till **System** > **Dataöverföring** > **Importera** och markera filen `.csv`.
1. Klicka på **Kontrollera data**.

<u>Förväntat resultat</u>:

Inga problem hittades. Du kan importera filen `.csv`.

<u>Faktiskt resultat</u>:

Följande felmeddelande visas: *&quot;XYZ för URL-nyckel har redan genererats för ett objekt med SKU %sku%&quot;*, det går inte att importera filen.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Hämta MDVA-12899\_EE\_2.2.3\_COMPOSER\_v2.patch](assets/MDVA-12899_EE_2.2.3_COMPOSER_v2.patch.zip)

### Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce lokal 2.2.3

Korrigeringen är även kompatibel (men löser kanske inte problemet) med följande utgåvor och versioner av Adobe Commerce:

* Adobe Commerce om molninfrastruktur från 2.2.0 till 2.2.7 och 2.3.0
* Adobe Commerce lokalt från 2.2.0 till 2.2.2, från 2.2.4 till 2.2.7 och 2.3.0

## Så här sätter du på plåstret

Mer information finns i [Använda en dispositionsruta från Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

## Användbara länkar

[Använd anpassade korrigeringsfiler för Adobe Commerce i molninfrastrukturen](https://devdocs.magento.com/guides/v2.3/cloud/project/project-patch.html)

## Bifogade filer
