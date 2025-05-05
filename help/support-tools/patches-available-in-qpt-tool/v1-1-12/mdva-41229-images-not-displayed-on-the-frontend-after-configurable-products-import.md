---
title: "MDVA-41229: Bilder som finns på serverdelen visas inte på klientsidan efter import av konfigurerbara produkter"
description: MDVA-41229-korrigeringen åtgärdar ett problem där bilder som finns på baksidan inte visas på förgrunden efter att konfigurerbara produkter har importerats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 är installerat. Korrigerings-ID är MDVA-41229. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
exl-id: 69d7374f-9f8b-4ec4-8a7f-135ee06135a3
feature: Data Import/Export, Configuration, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 2%

---

# MDVA-41229: Bilder som finns på serverdelen visas inte på klientsidan efter att konfigurerbara produkter har importerats

MDVA-41229-korrigeringen åtgärdar ett problem där bilder som finns på baksidan inte visas på förgrunden efter att konfigurerbara produkter har importerats. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 är installerat. Korrigerings-ID är MDVA-41229. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.3.2-p2 och 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Bilder som finns på baksidan visas inte på förgrunden efter att du har importerat konfigurerbara produkter.

<u>Steg som ska återskapas</u>:

1. Installera en ren Adobe Commerce.
1. Lägg till ett anpassat attribut genom att gå till **Lager** > **Attribut** > **Produkt** > **Lägg till nytt attribut** med inställningarna nedan:

   * Egenskaper:
      * Attributegenskaper:

         * Standardetikett: Ange storlek
         * Katalogindatatyp för butiksägare: Textruta
         * Värden som krävs: Nej
         * Uppdatera bild för produktförhandsgranskning: Ja

      * Hantera färgruta (värden för attributet):

        | Är standard | Administratörsruta | Admin - beskrivning | Standardvy för butiksvy | Beskrivning av standardbutiksvy |
        |---|---|---|---|---|
        | no | 4 | 4 | 4 | 4 |
        | no | 24 | 24 | 24 | 24 |
        | no | 30 | 30 | 30 | 30 |
        | no | 60 | 60 | 60 | 60 |
        | no | 68 | 68 | 68 | 68 |

      * Avancerade attributegenskaper:

         * Attributkod: set_size
         * Omfång: Global
         * Unikt värde: Nej
         * Indatavalidering för butiksägare: Ingen
         * Alternativ för Lägg till i kolumn: Nej
         * Använd i filteralternativ: Nej

   * Hantera etiketter:

      * Hantera titlar (storlek, färg osv.)

         * Standardbutiksvy: Ange storlek

   * Egenskaper för Storefront:

      * Använd i sökning: Ja
      * Sökbredd: 1
      * Synlig i avancerad sökning: Nej
      * Jämförelsebar på Storefront: Ja
      * Använd i navigering i lager: Filterbar (med resultat)
      * Använd i Sökresultat vid navigering i lager: Ja
      * Använd för kampanjregelvillkor: Nej
      * Synligt på katalogsidor i Storefront: Ja
      * Används i produktlistan: Ja
      * Används för sortering i produktlista: Nej

1. Lägg till det här attributet i standardattributuppsättningen i produktinformationsgruppen (**Lagrar** > **Attribut** > **Attributuppsättning**).
1. Ladda ned bilder i var-mappen i Adobe Commerce rotkatalog.
1. Gå till **System** > **Dataöverföring** > och importera filen med alternativen nedan:

   * Importinställningar:

      * Enhetstyp: Produkter

   * Importbeteende:

      * Importbeteende: Lägg till/uppdatera
      * Valideringsstrategi: Stoppa vid fel
      * Antal tillåtna fel: 1
      * Fältavgränsare: `;`
      * Flera värdeavgränsare: `,`
      * Attributvärdeskonstant: EMPTYVALUE
      * Fältbilaga: avmarkerad

   * Fil som ska importeras:

      * Välj den fil som ska importeras
      * Bildfilskatalog: lämna den tom

1. Gå till butiken på sidan `/product-set.html` och växla mellan olika uppsättningsstorlekar. För Ange storlek 24 finns inget galleri.

<u>Förväntade resultat</u>:

Galleriet för alla enkla produkter i en konfigurerbar produkt visas med alla relaterade bilder.

<u>Faktiska resultat</u>:

Det finns inget galleri för produkterna.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/usage) i vår utvecklardokumentation.
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i vår utvecklardokumentation.
