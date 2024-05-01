---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.35'
description: Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av patcharna i [!DNL Quality Patches Tool] (QPT) v1.1.35.
feature: Tools and External Services
role: Admin
exl-id: 46228690-44ce-462f-b700-1aea6fa0eeab
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Översikt [!DNL Quality Patches Tool] (QPT) v1.1.35

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av patcharna i [!DNL Quality Patches Tool] (QPT) v1.1.35.

QPT v1.1.35 innehåller följande patchar:

1. **ACSD-51899**: Korrigerar problemet där standardleveransadressen i utcheckningssteget fylls i automatiskt med en tidigare vald hämtningsadress i butiken.
1. **ACSD-52041**: Åtgärdar problemet där felmeddelandet: *[FEL] [!DNL Page Builder] återgav i 5 sekunder utan att frigöra lås*. visas i [!DNL Chrome] webbläsare när innehåll som redigerats med sparas [!DNL Page Builder].
1. **ACSD-52095**: Åtgärdar problemet där `manage_stock` Värdet angavs felaktigt till 0 i CSV-filen efter produktexporten.
1. **ACSD-51358**: Korrigerar problemet där borttagning av en schemalagd uppdatering utan slutdatum leder till borttagning av andra schemalagda uppdateringar för samma entitet.
1. **ACSD-48070**: Korrigerar problemet där redigering av en schemalagd uppdatering utlöser ett undantag.
1. **ACSD-51890**: Åtgärdar problemet där [!UICONTROL Submit review] kan klickas flera gånger utan [!DNL Google] reCAPTCHA v3-validering.
1. **ACSD-51984**: Åtgärdar problemet där det inte är markerat *Använd standardvärde och icke-standardvärden för produktfält* sparas inte för den andra webbplatsen, butiken och butiksvyn.
1. **ACSD-52398**: Åtgärdar felet *Begärd kvantitet är inte tillgänglig* som inträffar när man försöker uppdatera kvantiteten för en paketerad produkt i kundvagnen på butiken.
1. **ACSD-52786**: Korrigerar problemet där ett villkor för katalogregel tillämpas på alla produkter med början från angiven SKU.
1. **ACSD-52921**: Korrigerar problemet där ett internt fel inträffar om kundvagnsinformation begärs från GraphQL när det finns en ej lagerförd konfigurerbar produkt i vagnen.
1. **ACSD-51683**: Korrigerar problemet där ett anpassningsbart alternativ inte kan läggas till i kundvagnen med GraphQL.
1. **ACSD-52133**: Korrigerar problemet där ett kundkonto inte kan sparas efter en uppgradering.
1. **ACSD-52202**: Korrigerar problemet där den säljbara kvantiteten standardlager ändras felaktigt till 0 när ett icke-standardlager ändras till 0 kvantitet vid orderleverans.
1. **ACSD-51265**: Åtgärdar problemet med `catalog_product_price` omindexering av prestanda när det finns för många paketerade produkter i systemet.
1. **ACSD-52831**: Korrigerar problemet där kunderna inte kan göra överlåtbara offertbeställningar när [!DNL Google reCAPTCHA v3 Invisible] är aktiverat.
1. **ACSD-51845**: Korrigerar problemet där efterföljande produkter med nivåpriser och olika attributuppsättningar inte kan uppdateras via asynkron REST API.
1. **ACSD-52815**: Korrigerar problemet där indata för kvantitetsfältet för en icke-standardkälla endast stöder upp till 6 siffror, till skillnad från 8 för ett standardlager.
1. **ACSD-51149**: Åtgärdar problemet där [!UICONTROL Scheduled ImportExport] med aktiverad [!UICONTROL Catalog Permissions] gör indexerare ogiltiga och cachelagrar sedan tömningar efter cron.
1. **ACSD-50815**: Korrigerar problemet där decimalkvantiteten för en enkel produkt inte kan användas för ett nytt produktalternativ.
1. **ACSD-52399**: Korrigerar problemet där det konfigurerbara produktalternativet med en säljbar kvantitet på 0 visar *I Stock* på produktsidan.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
