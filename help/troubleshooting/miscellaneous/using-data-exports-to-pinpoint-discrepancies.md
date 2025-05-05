---
title: Identifiera avvikelser med hjälp av dataexport
description: Den här artikeln innehåller lösningar för felsökning av avvikelser i data från Magento BI. Dataexport är ett användbart verktyg för att jämföra dina Magento BI-data med dina källdata för att identifiera datameddelanden i dina rapporter, särskilt om [checklista för diagnostik av diskrepanser](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy) inte hjälper dig att identifiera problemet. I den här artikeln får du ett exempel på hur datameddelanden kan identifieras med hjälp av dataexport.
exl-id: b42d585c-ad8c-4685-9ad4-a13686566f18
feature: Commerce Intelligence, Data Import/Export
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '1300'
ht-degree: 0%

---

# Identifiera avvikelser med hjälp av dataexport

Den här artikeln innehåller lösningar för felsökning av avvikelser i data från Magento BI. Dataexport är ett användbart verktyg för att jämföra dina Magento BI-data med dina källdata för att identifiera datamatchningsskillnader i dina rapporter, särskilt om checklistan för [diagnostik av datameddelanden](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy) inte hjälper dig att identifiera problemet. I den här artikeln får du ett exempel på hur datameddelanden kan identifieras med hjälp av dataexport.

Ta den här analysen, till exempel:

![](assets/Exports_Discrepancies_1.png)

Det är en misstänkt dipp i november 2014. 500 780,94 dollar i intäkter? Det låter inte rätt. Du har bekräftat att det visas fler intäkter för november 2014 i källdatabasen och du har dubbelkontrollerat att det **intäktsmått** som används i den här rapporten är korrekt definierat. Det verkar som att data i datalagret i Magento BI är ofullständiga, vilket kan bekräftas med dataexport.

## Exportera data {#export}

Börja med att klicka på kugghjulet i diagrammets övre högra hörn och sedan på alternativet för Raw-export i listrutan. Då kan du exportera diagrammets data i obearbetad form.

![](assets/Export_Discrepancies_5.gif)

På menyn **Raw-dataexport** kan du markera den tabell som ska exporteras tillsammans med de kolumner som ska ingå i exporten. Du kan också använda filter på resultatuppsättningen.

I vårt exempel använder det **intäktsmått** som används i den här rapporten fältet **order\_total** som definieras i tabellen **`orders`**, med hjälp av **date** som tidsstämpel. I vår export vill vi inkludera alla **order\_id**-värden för november 2014 och deras **order\_total** . Inga filter används för **intäktsmåttet**, men vi lägger till ett filter i exporten för att begränsa resultatet till bara november 2014.

Så här ser Raw Data Export-menyn ut:

![](assets/Exports_Discrepancies_2.png)

Klicka på Exportera data för att påbörja exporten. Ett fönster med information om exporten, inklusive status, visas. Det tar några minuter innan exporten påbörjas, vilket gör att det nu är lämpligt att utföra ett liknande extrakt av källdata för november 2014, inklusive **date, order\_id** och **order\_total** . Vi öppnar den här filen i Excel och låter den vara kvar eftersom vi snart kommer tillbaka till den.

När knappen Hämta visas i fönstret för Raw Data-export klickar du på den för att hämta zip-filen som innehåller CSV-filen.

![](assets/Export_Discrepancies_6.png)

I det här skedet måste vi samla alla data i ett enda blad för att hitta problemet. Vi importerar CSV-filen (exporten från Magento BI) till ett annat Excel-blad som innehåller våra källdata.

## Fästa problemet {#pinpoint}

Nu när alla data finns på ett och samma ställe kan vi leta efter orsaken till diskrepansen. Genom att jämföra antalet rader i varje blad kan vi identifiera problemet. Låt oss titta närmare på varje situation.

### Båda tabellerna innehåller samma antal rader

Om båda systemen har samma radantal och måttet **Intäkter** inte matchar källdata, måste **order\_total** vara avstängd någonstans. Det är möjligt att fältet **order\_total** har uppdaterats i källdatabasen och att Magento BI inte kan hämta dessa ändringar.

Kontrollera detta genom att kontrollera om kolumnen **order\_total** ommarkeras eller inte. Gå till tabellhanteraren och klicka på Datan Warehouse **`orders`**. Du ser [kontrollfrekvensen](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html?lang=sv-SE) som anges i avsnittet &#39;Ändringar?&#39; kolumn. Fältet **order\_total** ska ställas in så att det kontrolleras igen så ofta som det förväntas ändras. Om så inte är fallet ska du ställa in den till önskad frekvens för omkontroll.

### ![](assets/Export_Discrepancies_4.gif)

Om kontrollfrekvensen redan är korrekt är något annat fel. Gå till avsnittet [Kontakta support](#support) i slutet av den här artikeln för nästa steg.

## Källdatabasen har FLER rader än Magento BI {#morerows}

Om källdatabasen har fler rader än Magento BI och mellanrummet är större än det antal order som du kan förvänta dig att komma in under en uppdateringscykel, kan det bero på ett anslutningsproblem. Det innebär att Magento BI inte kan hämta in nya data från källdatabasen, vilket kan hända av flera orsaker.

Gå till sidan Anslutningar och ta en titt på statusen för datakällan som innehåller tabellen `order`:

1. **Om statusen är Återautentiserad** använder anslutningen inte rätt autentiseringsuppgifter. Klicka på anslutningen, ange korrekta autentiseringsuppgifter och försök igen.
1. **Om statusen är Misslyckad** kanske anslutningen inte är korrekt konfigurerad på serversidan. Felaktiga anslutningar uppstår oftast på grund av ett felaktigt värdnamn eller på grund av att målservern inte accepterar anslutningar på den angivna porten. Klicka på anslutningen och dubbelkontrollera stavningen av värdnamnet och att rätt port har angetts. På serversidan måste du se till att porten kan acceptera anslutningar och att din brandvägg har IP-adressen för Magento BI (54.88.76.97/32) som tillåts. **Om anslutningen fortsätter att misslyckas** kan du gå till avsnittet [Kontakta support](#support) i slutet av den här artikeln för nästa steg.
1. **Om statusen är Slutförd** är anslutningen inte problemet och RJ-stödet måste involveras. Gå till avsnittet [Kontakta support](#support) i slutet av den här artikeln för nästa steg.

## Källdatabasen har FÄRRE rader än Magento BI {#lessrows}

Om källdatabasen har färre rader än Magento BI kan det hända att rader tas bort från källdatabasen och Magento BI inte kan hämta dessa borttagningar. **&#x200B; [Om du tar bort data](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html?lang=sv-SE) kan det leda till avvikelser, längre uppdateringstider och en rad logistiska problem**. Därför rekommenderar vi att du aldrig tar bort data om det inte är nödvändigt.

Om du däremot tar bort rader från tabellen bör du titta på hur ofta kontrollen ska göras om primärnyckeln. Om du upprepar primärnyckeln kontrolleras om tabellen innehåller borttagna rader.

I Data Warehouse Manager markeras primärnyckelkolumner med en nyckelsymbol. I vårt exempel är primärnyckeln kolumnen **order\_id**:

![](assets/Export_Discrepancies_3.png)

Om primärnyckeln redan är inställd på ommarkering eller om rader aldrig tas bort från den här tabellen behöver du stöd för RJ för att hitta problemet. Gå till följande avsnitt för nästa steg.

## Kontakta support {#support}

Om du inte kan hitta källan till problemet måste du göra en slinga i RJ-stödet. Gör följande innan du skickar in en biljett:

* **Om källdatabasen och Magento BI har samma antal rader** och omkontrollfrekvenser är korrekt inställda, ska du utföra en VLOOKUP i ditt kalkylblad **för att hitta vilka order\_id-värden som har ett annat order\_total-värde mellan Magento BI och din källdatabas.** Inkludera dessa värden när du skickar in din biljett.
* **Om källdatabasen har fler rader än Magento BI** och anslutningen visas som Slutförd eller fortsätter att misslyckas, måste vi veta namnet på anslutningen och felmeddelandet om det finns något.
* **Om din källdatabas har FÄRRE rader än Magento BI, tas** rader inte bort från tabellen och omkontrollsfrekvenser är korrekt angivna, utför en VLOOKUP i ditt kalkylblad **för att hitta vilka order\_id-värden som finns i Magento BI** men inte i din källdatabas. Inkludera dessa värden när du skickar in din biljett.

## Relaterad läsning

* [Checklista för diagnostisk datameddelandekontroll](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy)
* [Adobe Commerce Intelligence tjänstprinciper](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies)
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook

