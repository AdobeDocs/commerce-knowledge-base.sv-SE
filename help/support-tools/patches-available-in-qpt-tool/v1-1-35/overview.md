---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.35'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.35.
feature: Tools and External Services
role: Admin
exl-id: 46228690-44ce-462f-b700-1aea6fa0eeab
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.35

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som är tillgängliga i [!DNL Quality Patches Tool] (QPT) v1.1.35.

QPT v1.1.35 innehåller följande patchar:

1. **ACSD-51899**: Korrigerar problemet där standardleveransadressen i utcheckningssteget fylls i automatiskt med en tidigare vald hämtningsadress i butiken.
1. **ACSD-52041**: Korrigerar problemet där felmeddelandet: *[ERROR] [!DNL Page Builder] återgav i 5 sekunder utan att frigöra lås*. visas i webbläsaren [!DNL Chrome] när innehåll som har redigerats med [!DNL Page Builder] sparas.
1. **ACSD-52095**: Korrigerar problemet där värdet `manage_stock` felaktigt hade angetts till 0 i CSV-filen efter produktexporten.
1. **ACSD-51358**: Korrigerar problemet där borttagning av en schemalagd uppdatering utan slutdatum leder till att andra schemalagda uppdateringar för samma entitet tas bort.
1. **ACSD-48070**: Korrigerar problemet där redigering av en schemalagd uppdatering utlöser ett undantag.
1. **ACSD-51890**: Korrigerar problemet där knappen [!UICONTROL Submit review] kan klickas flera gånger utan [!DNL Google] reCAPTCHA v3-validering.
1. **ACSD-51984**: Korrigerar problemet där *Använd standardvärden och icke-standardvärden för produktfält* inte sparas för den andra webbplatsen, butiken och butiksvyn.
1. **ACSD-52398**: Korrigerar felet *Begärd kvantitet är inte tillgänglig* som inträffar när en paketerad produkt i kundvagnen på butiken uppdateras.
1. **ACSD-52786**: Korrigerar problemet där ett villkor för katalogregel används för alla produkter med början från angiven SKU.
1. **ACSD-52921**: Korrigerar problemet där ett internt fel inträffar om kundvagnsinformation begärs från GraphQL när det finns en produkt som inte finns i lager i kundvagnen.
1. **ACSD-51683**: Korrigerar problemet där ett anpassningsbart alternativ inte kan läggas till i vagnen med GraphQL.
1. **ACSD-52133**: Korrigerar problemet där ett kundkonto inte kan sparas efter en uppgradering.
1. **ACSD-52202**: Korrigerar problemet där den säljbara kvantiteten standardlager ändras felaktigt till 0 när ett icke-standardlager ändras till 0 kvantitet vid orderleverans.
1. **ACSD-51265**: Korrigerar problemet med `catalog_product_price` omindexeringsprestanda när det finns för många paketerade produkter i systemet.
1. **ACSD-52831**: Korrigerar problemet där kunder inte kan göra överlåtbara offertorder när [!DNL Google reCAPTCHA v3 Invisible] är aktiverat.
1. **ACSD-51845**: Korrigerar problemet där efterföljande produkter med nivåpriser och olika attributuppsättningar inte kan uppdateras via asynkron REST API för bulk.
1. **ACSD-52815**: Korrigerar problemet där indata för kvantitetsfältet för en icke-standardkälla endast stöder upp till 6 siffror, till skillnad från 8 för en standardresurs.
1. **ACSD-51149**: Korrigerar problemet där [!UICONTROL Scheduled ImportExport] med aktiverad [!UICONTROL Catalog Permissions] gör indexerare ogiltiga och sedan cachelagrar tömningar med cron.
1. **ACSD-50815**: Korrigerar problemet där decimalkvantiteten för en enkel produkt inte kan användas för ett nytt produktalternativ.
1. **ACSD-52399**: Korrigerar problemet där det konfigurerbara produktalternativet med försäljningsvärdet 0 visar *I Stock* på produktsidan.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
