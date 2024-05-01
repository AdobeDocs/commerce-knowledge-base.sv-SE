---
title: Identifiera avvikelser med hjälp av dataexport
description: Den här artikeln innehåller lösningar för felsökning av avvikelser i data från Magento BI. Dataexport är ett användbart verktyg för att jämföra dina Magento BI-data med dina källdata för att identifiera datameddelanden i dina rapporter, särskilt om [checklista för diagnostik av diskrepanser](/help/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.md) inte hjälper dig att identifiera problemet. I den här artikeln får du ett exempel på hur datameddelanden kan identifieras med hjälp av dataexport.
exl-id: b42d585c-ad8c-4685-9ad4-a13686566f18
feature: Commerce Intelligence, Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '1291'
ht-degree: 0%

---

# Identifiera avvikelser med hjälp av dataexport

Den här artikeln innehåller lösningar för felsökning av avvikelser i data från Magento BI. Dataexport är ett användbart verktyg för att jämföra dina Magento BI-data med dina källdata för att identifiera datameddelanden i dina rapporter, särskilt om [checklista för diagnostisk diskrepans](/help/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.md) hjälpte dig inte att hitta problemet. I den här artikeln får du ett exempel på hur datameddelanden kan identifieras med hjälp av dataexport.

Ta den här analysen, till exempel:

![](assets/Exports_Discrepancies_1.png)

Det är en misstänkt dipp i november 2014. 500 780,94 dollar i intäkter? Det låter inte rätt. Du har bekräftat att det visas fler intäkter för november 2014 i källdatabasen och du har dubbelkontrollerat att **Intäkter** Det mätvärde som används i den här rapporten är korrekt definierat. Det verkar som att data i datalagret i Magento BI är ofullständiga, vilket kan bekräftas med dataexport.

## Exportera data {#export}

Börja med att klicka på kugghjulet i diagrammets övre högra hörn och sedan på alternativet för Raw-export i listrutan. Då kan du exportera diagrammets data i obearbetad form.

![](assets/Export_Discrepancies_5.gif)

På menyn Exportera Raw-data kan du markera den tabell som ska exporteras tillsammans med de kolumner som ska ingå i exporten. Du kan också använda filter på resultatuppsättningen.

I vårt exempel **Intäkter** det mätvärde som används i den här rapporten använder **order\_total** fält definierat på **order** tabell, använda **datum** som tidsstämpel. Vi vill inkludera alla **order\_id** värden för november 2014 och deras **order\_total** . The **Intäkter** Inga filter används för måttet, men vi lägger till ett filter i exporten för att begränsa resultatet till bara november 2014.

Så här ser Raw Data Export-menyn ut:

![](assets/Exports_Discrepancies_2.png)

Klicka på Exportera data för att påbörja exporten. Ett fönster med information om exporten, inklusive status, visas. Det tar några minuter innan exporten är klar, vilket gör att det nu är lämpligt att utföra ett liknande extrakt av källdata för november 2014, inklusive **date, order\_id** och **order\_total** . Vi öppnar den här filen i Excel och låter den vara kvar eftersom vi snart kommer tillbaka till den.

När knappen Hämta visas i fönstret för Raw Data-export klickar du på den för att hämta zip-filen som innehåller CSV-filen.

![](assets/Export_Discrepancies_6.png)

I det här skedet måste vi samla alla data i ett enda blad för att hitta problemet. Vi importerar CSV-filen (exporten från Magento BI) till ett annat Excel-blad som innehåller våra källdata.

## Fästa problemet {#pinpoint}

Nu när alla data finns på ett och samma ställe kan vi leta efter orsaken till diskrepansen. Genom att jämföra antalet rader i varje blad kan vi identifiera problemet. Låt oss titta närmare på varje situation.

### Båda tabellerna innehåller samma antal rader

Om båda systemen har samma radantal och **Intäkter** mätvärdet matchar inte källdata, så **order\_total** Måste vara borta någonstans. Det är möjligt att **order\_total** fältet har uppdaterats i källdatabasen och Magento BI kan inte hämta dessa ändringar.

Bekräfta detta genom att titta på om **order\_total** kolumnen kontrolleras om. Gå till Data Warehouse Manager och klicka på ordertabellen. Du kommer att se [kontrollera frekvens](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html) som anges i avsnittet &#39;Ändrar?&#39; kolumn. The **order\_total** ska ställas in så att omkontrollen görs så ofta som den förväntas ändras. Om så inte är fallet, ska du ställa in den till önskad frekvens för omkontroll.

### ![](assets/Export_Discrepancies_4.gif)

Om kontrollfrekvensen redan är korrekt är något annat fel. Se [Kontakta supportavdelningen](#support) i slutet av den här artikeln för nästa steg.

## Källdatabasen har FLER rader än Magento BI {#morerows}

Om källdatabasen har fler rader än Magento BI och mellanrummet är större än det antal order som du kan förvänta dig att komma in under en uppdateringscykel, kan det bero på ett anslutningsproblem. Det innebär att Magento BI inte kan hämta in nya data från källdatabasen, vilket kan hända av flera orsaker.

Gå till sidan Anslutningar och titta på statusen för datakällan som innehåller ordertabellen:

1. **Om statusen är Återautentisera** används inte rätt autentiseringsuppgifter för anslutningen. Klicka på anslutningen, ange korrekta autentiseringsuppgifter och försök igen.
1. **Om statusen är Misslyckad** kan anslutningen vara felaktig på serversidan. Felaktiga anslutningar uppstår oftast på grund av ett felaktigt värdnamn eller på grund av att målservern inte accepterar anslutningar på den angivna porten. Klicka på anslutningen och dubbelkontrollera stavningen av värdnamnet och att rätt port har angetts. På serversidan måste du se till att porten kan acceptera anslutningar och att din brandvägg har IP-adressen för Magento BI (54.88.76.97/32) som tillåts. **Om anslutningen fortsätter att misslyckas** , se [Kontakta supportavdelningen](#support) i slutet av den här artikeln för nästa steg.
1. **Om statusen är Slutförd** så är inte anslutningen problemet och RJ-supporten måste involveras. Se [Kontakta supportavdelningen](#support) i slutet av den här artikeln för nästa steg.

## Källdatabasen har FÄRRE rader än Magento BI {#lessrows}

Om källdatabasen har färre rader än Magento BI kan det hända att rader tas bort från källdatabasen och Magento BI inte kan hämta dessa borttagningar. ** [Tar bort data](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html) kan leda till avvikelser, längre uppdateringstider och ett antal logistiska problem**, så vi rekommenderar att du aldrig tar bort data om det inte är nödvändigt.

Om du däremot tar bort rader från tabellen bör du titta på hur ofta kontrollen ska göras om primärnyckeln. Om du upprepar primärnyckeln kontrolleras om tabellen innehåller borttagna rader.

I Data Warehouse Manager markeras primärnyckelkolumner med en nyckelsymbol. I vårt exempel är primärnyckeln **order\_id** kolumn:

![](assets/Export_Discrepancies_3.png)

Om primärnyckeln redan är inställd på ommarkering eller om rader aldrig tas bort från den här tabellen behöver du stöd för RJ för att hitta problemet. Gå till följande avsnitt för nästa steg.

## Kontakta support {#support}

Om du inte kan hitta källan till problemet måste du göra en slinga i RJ-stödet. Gör följande innan du skickar in en biljett:

* **Om källdatabasen och Magento BI har samma antal rader** och frekvenserna för omkontroll är korrekt inställda, utför en VLOOKUP i kalkylbladet **om du vill ta reda på vilka order\_id-värden som har ett annat order\_total-värde mellan Magento BI och din källdatabas.** Inkludera dessa värden när du skickar in din biljett.
* **Om källdatabasen har FLER rader än Magento BI** och anslutningen visas som Slutförd eller fortsätter att misslyckas, måste vi veta namnet på anslutningen och felmeddelandet som du ser, om det finns något.
* **Om källdatabasen har FÄRRE rader än Magento BI,** raderna tas inte bort från tabellen, och omkontrollsfrekvenser ställs in korrekt, utför en VLOOKUP i kalkylbladet **för att hitta i vilken ordning\_id-värden finns i Magento BI** men inte i källdatabasen. Inkludera dessa värden när du skickar in din biljett.

## Relaterad

* [Checklista för diagnostisk diskrepans](/help/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.md)
* [Skicka en avvikelseanmälan](https://support.magento.com/hc/en-us/articles/360016506472-Submitting-a-data-discrepancy-ticket)
