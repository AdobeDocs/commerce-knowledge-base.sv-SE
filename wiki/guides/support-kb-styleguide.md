---
source-git-commit: c992521cae8c847adc0cc23d2323300e0ba69cdc
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---
# Stöd för KB-formatguide

Följ dessa rekommendationer för format och formatering när du bidrar till Adobe Commerce Help Center.

## Titlar

* Titlarna är i versalstil.
* Plural för titlar; singular för procedurrubriker. Exempel: Titel - skriva böcker. Header - Skriv en bok.
* Håll rubrikerna korta, med viktiga ord i början. Av SEO-skäl rekommenderar vi att titlarna inte är längre än 70 tecken (det finns ett undantag när en titelreducering förhindrar att den verkliga innebörden kommuniceras). 

## Sidhuvuden

* Sidhuvudet på den översta nivån är H2. (H1 är som standard artikelrubrik, även om titeln inte är synligt formaterad med H1).
* Använd oändliga verb för uppgiftsrubriker. Exempel:&quot;Hur man identifierar trafikhändelser&quot;.
* Använd det enskilda formuläret för uppgiftsrubriker. Exempel: &quot;Modulstruktur&quot;.
* Undvik dubbla rubriker (det ska finnas minst en mening mellan rubrikerna).
* Inledande versal för alla rubriker.
* Aktivitetsrubriker är obligatoriska (&quot;Skapa x&quot;, inte&quot;Skapa x&quot; eller&quot;Skapa x&quot;).

## Listor

* Steg i en uppgift: max 9

* Punktlistor gör skanningen enkel.

   * Använd punktlistor för metoder, metoder, alternativ och steg som inte följer på varandra.
   * Håll texten i punktlistor kort, helst inte mer än två meningar.
   * Minimera antalet punkter. Sju eller färre är idealiskt.
   * Undvik att placera ett tips eller en anteckning mellan punktlistor.
   * Använd parallell grammatikstruktur i listor, men bryt den här regeln om den leder till för mycket verb eller stelt språk.
   * Inled det första ordet för varje objekt i en punktlista med versal, även om det är ett fragment.

* Skapa parallella listor. Till exempel ska varje objekt vara ett substantiv eller en fras som börjar med ett verb.

## Anteckningar och tips

Behåll anteckningar och tips endast i ett stycke. Behovet av mer än ett stycke signalerar behovet av att strukturera om innehållet och inkludera det i artikelns brödtext.

## Versaler

Använd inte versaler när du är osäker. Använd inledande versal i mening i rubriker. Använd inledande versal i ord och det första ordet efter kolon.

## Gränssnittselement

* Allt som användaren klickar på placeras i **fet**. Exempel:&quot;Klicka på **Fortsätt**.&quot; Alternativvärden och felmeddelanden formateras med _kursiv_.
* Undvik, där det är möjligt, att nämna UI-elementtypen i instruktionerna. (Klicka på **Nästa**. vs Klicka på knappen **Nästa**.)
* Använd&quot;Välj&quot; och&quot;>&quot; i kommandosekvenser. (Välj **Redigera** > **Inställningar**. vs Klicka på Redigera | Inställningar.)
* Preposition: &quot;in&quot; för dialogruta, fönster, är a, panel, view, wizard, list, folder, node.
* Förposition: &quot;på&quot; för skärm, sida, verktygsfält, menyrad, flik, ruta, menyflik.
* Förposition: Klicka (klicka på **Nästa** eller klicka på **Nästa**).

## Filnamn

Filnamn och mappar formateras som kod. Exempel: Systemkatalogen `/var/log` innehåller loggar för alla miljöer.


## Nummer

Ovanför alla gäller enhetlighetsregler när man närmar sig problemet med utskrivna siffror kontra siffror.

Skriv ut en siffra, som&quot;fem&quot; eller&quot;nio&quot;, när siffran är under 10 (nummer ett till nio).

Skriv ett tal som ett tal, till exempel &quot;42&quot; eller &quot;11&quot; när:

* Talet är över 9 (tal tio och högre).
* Du anger numret:
   * Inom en kodrad eller ett kodfragment.
   * Inom en filsökväg eller ett katalognamn.
   * När du kommunicerar med ett intervall, som&quot;mellan 5 och 25&quot; eller&quot;granskar nummer 8 till 21&quot;.
   * Numren har mätts eller beräknats som &quot;62 pica&quot; eller &quot;830 MHz&quot;.

Använd en blandning av siffror och siffror när du lägger märke till en mängd numrerade saker, som&quot;en samling med femton provversioner av 1 000&quot;.

Skriv båda talen med ord eller båda, om du har två siffror i en mening, en under 10 (som 4) och en över 10 (som 14). Du kan till exempel behålla siffror här:&quot;14 minuter för varje 4 liter vätska&quot;.


## Särskilda fall av formulering

<table class="relative-table" style="width: 100.0%;"><colgroup><col style="width: 12.003596%;"> <col style="width: 16.444849%;"> <col style="width: 71.55351%;"></colgroup>

<tbody>

<tr>

<th>Felaktig</th>

<th>Korrigera</th>

<th> Orsak
</th>

</tr>

<tr>

<td>Logga in på kontosidan för Magento.com </td>

<td>Logga in på ditt Adobe Commerce-konto</td>

<td colspan="1">
</td>

</tr>

<tr>

<td>Tillägg från tredje part (moduler)</td>

<td>tillägg från tredje part (moduler)</td>

<td colspan="1">
</td>

</tr>

<tr>

<td>SQL-kodfragment</td>

<td>Programsatser är versaler (SELECT vs select)</td>

<td colspan="1">Bättre läsbarhet</td>

</tr>

<tr>

<td colspan="1">

Referenser till andra resurser.

Exempel: Se xyz i vår utvecklardokumentation


</td>

<td colspan="1">Se xyz i vår utvecklardokumentation</td>

<td colspan="1">

Tillgänglighetskrav: Alla länkar beskriver länkens mål.


</td>

</tr>

<tr>

<td colspan="1">

Adobe Commerce v2.4.0

Adobe Commerce 2.4.0

Adobe Commerce version 2.4.0

</td>

<td colspan="1">Adobe Commerce 2.4.0 (ingen version)</td>

<td colspan="1"></td>

</tr>

<tr>

<td colspan="1">

2.4.x

2.4.X

</td>

<td colspan="1">

2.4.0

2.4.x

</td>

<td colspan="1">

Ingen orsak till versaler.

</td>

</tr>

<tr>

<td colspan="1">

Felmeddelande: _._

Felmeddelande: __Något gick fel.__

</td>

<td colspan="1"> Felmeddelande: <i>Något gick fel.</i> </td>

<td colspan="1">
</td>

</tr>

</tbody>

</table>

## Tillgänglighet

* Alla element som inte är text eller grafiska har textmotsvarigheter eller Alt-text. Exempel: ![example_image](/url "alt_text_for_this_image").

* Alla länkar beskriver länkens mål. Exempel: [link](/uri "destination_of_the_link").


<!--
## Accessible tables

Use tables for information that is best presented along two axes (rows and columns). Do not use tables when a list or definition list serves the purpose. If using tables, follow these recommendations:

*   Headers for rows and columns; row headers easier for screen readers.

*   Simple linear construction.

*   Content within cells consistently structured.  -->


## Abusivt språk

* Undvik stötande språk. 
* Undvik rasistiska eller &quot;kan kännas som rasistiska&quot; språk.
* Undvik språk med starka negativa konnoteringar eller stark känslomässig färgning, som &quot;döda&quot;, &quot;avsluta&quot;.


## Länkar 

De flesta länkar visas i länklistor i artikeln. Undvik onödiga textbundna länkar.

Det bästa sättet är att isolera textbundna länkar i en länklista med en konfigurerbar titel.

En specialiserad länklista, som kallas en lista med även visningar, visas endast i slutet av en artikel.    Använd länklistor strategiskt, bara nödvändigt. Som tumregel får det inte finnas fler än sex länkar i en länklista.

### Länkar till externa webbplatser

Använd vanliga URL:er i stället för goURL:er för att länka till sidor utanför [Adobe.com](http://Adobe.com).


## Kommatecken

I allmänhet följer du rekommendationerna i Chicago Manual of Style för interpunktion med öppen stil, där interpunktion bara behövs för att förhindra felläsning. Du kan t.ex. utelämna kommatecken före en kombination i en sammansatt mening om det finns liten risk för felläsning eller ingen risk för detta. Använd kommatecken där det behövs för klargörandet.

* Använd alltid det seriella kommatecknet (ett komma före _och_ eller _eller_ i en lista med tre eller fler objekt): x, y och z

* Placera ett kommatecken före en kombination som introducerar en oberoende sats:&quot;Ange en plats och ange ett namn för fillistan.&quot;

* Avgränsa inte plattformsskillnader med kommatecken: &quot;.. Ctrl (Windows) eller Kommando (Mac OS)&quot;

* Använd alltid ett kommatecken efter en inledande fras eller sats:&quot;Importera Illustrator-filen i Photoshop.&quot;

## Versioner

* Vi använder&quot;version&quot; för alla versioner (större/mindre/korrigeringar). Exempel:&quot;Versioner som stöds: Adobe Commerce 2.3.x&quot;

* Vi använder gemener&quot;x&quot; när vi skriver om alla korrigeringsutgåvor inom en mindre release och alla små med större version. Exempel: Adobe Commerce 2.x.x.

## Varumärke

* Magento Commerce är nu Adobe Commerce. Mer information om hur du använder det aktuella varumärkesspråket finns i [omprofileringsvillkoren](https://github.com/magento/knowledge-base/wiki)-wiki.
