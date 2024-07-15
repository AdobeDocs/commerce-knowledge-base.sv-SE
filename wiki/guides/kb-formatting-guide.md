---
source-git-commit: c587986edc925c49bf95ab935888b59f265371af
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---
# KB-formateringshandbok

## Författare i kod

Vanligtvis använder vi [Adobe Experience League Markdown Syntax Style Guide](https://experienceleague.adobe.com/docs/authoring-guide-exl/using/markdown/syntax-style-guide.html?lang=en), men det finns vissa skillnader och undantag. I vissa fall krävs även vissa HTML-taggar.

Nedan följer exempel på den Markdown-formatering som oftast används i vårt svar.

## Grundläggande formatering

Om du vill formatera text med fet stil omger du den med två asterisker:

`This will be **bold** text`

Använd en asterisk om du vill formatera text som kursiv:

`This text will be *italics*`

Om du vill formatera text som understruken använder du taggen `<ins>`:

`<ins>This text will be underlined</ins>`

Använd taggen `<br>` HTML om du vill lägga till en radbrytning.


## Sidhuvuden

Använd följande formatering för sidhuvuden från H2 till H5. H1 används aldrig eftersom artikeltiteln anses vara H1.

`## Header 2 `

`### Header 3 `

`#### Header 4`

`##### Header 5`

## Textbunden kod och block

Använd en enda bakterie för att omsluta det kodelement som du vill markera:

Detta är \`infogad kod\` i ett textstycke.

### Kodblock

Om du vill infoga ett kodblock omsluter du kodblocket med tre bakgrunder och anger språket när du har öppnat trippelbakgrunder:

\`\`\` sql

VÄLJ TABLE_NAME SOM `Table`,
ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FRÅN information_schema.TABELLER
WHERE TABLE_SCHEMA = &quot;%project_id%&quot;
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;

\`\`\`

Detta återges som:

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "%project_id%"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Enligt våra lintingregler måste du alltid ange ett språk för kodblocket.

En lista över språk som stöds finns på https://github.com/github/linguist/blob/master/lib/linguist/languages.yml.

Om markeringen inte fungerar för ett visst språk i markeringar (d.v.s. språket inte stöds) ska du använda följande HTML:

```html
<pre><code class="language-%language-code%"
your code here
</pre></code>
```

Där ``%language-code%`` är de koder som definieras av [språk som stöds av Prism.js ](https://prismjs.com/#supported-languages).

## Listor

Avgränsa alltid listor från resten av innehållet med tomma rader. Listor ska föregås och följas av en tom rad.

Använd följande formatering för sorterade listor:

```markdown
1. First numbered list item.
1. Second numbered list item.
...
1. Last numbered list item.
```

Om du vill skapa en punktlista som inte är numrerad börjar du en rad med *, eller + eller -. Men välj en metod och använd den konsekvent genom hela artikeln.

Exempel:

```markdown
* Unordered list item.
* Unordered list item.
---
* Last unordered list item.
```

Om du vill lägga till innehåll mellan listobjekt lägger du till fyra blanksteg i början av raden:

```markdown
* List item.
* List item.
    Here's some content between list items.
* Here we continue the list
```

Du kan även bädda in listor på det här sättet.

## Länkar

Externa länkar är enkla:

```markdown
[Adobe](https://www.adobe.com)
```

### Länkar till bilagor

Alla typer av bilagor ska vara i formaten .png, .jpg och .jpeg. Av säkerhetsskäl godkänner vi endast bilagor som är i ett av de tre formaten.

Om du vill infoga en bild placerar du bilden i undermappen *assets* i samma avsnittsmapp som artikeln och använder följande syntax för att infoga bilden i artikeln:

```markdown
![alt text](assets/image.png)
```

Om du vill anpassa bildstorleken måste du göra det med följande HTML-tagg:

```html
<img src = "assets/image.png" alt = "your alt text" width="custom width, ex: 250px">
```

```markdown
[asset_title](assets/%file_name%).
```

### Länkar till ett visst avsnitt i artikeln

Om du behöver referera till ett avsnitt i artikeln behöver du inte skapa en separat ankarpunkt. De genereras automatiskt vid publicering för alla H2-H6-rubriker. Fästpunkterna genereras från rubriken genom att alla ord skrivs med gemener och &quot;-&quot; används för att separera ord.

Exempel:

```markdown
## This is header
```

Det här är en länk till det här huvudet:

```markdown
[this is link to the anchor in the same article](#this-is-header)
```

Om du behöver referera till ett annat element än huvudet använder du HTML för att definiera elementet som ska läggas till med attributet [id](https://www.w3schools.com/html/html_id.asp). Du kan sedan använda Markdown eller HTML för att referera till detta ID.

### Relativa länkar och länkar till andra artiklar

Använd inte relativa länkar för att referera till våra supportartiklar i kunskapsbasen. Länkarna fungerar inte när artikeln publiceras i [Adobe Commerce Help Center](https://support.magento.com/hc/en-us).
Använd fullständiga hyperlänkar från [Adobe Commerce Help Center](https://support.magento.com/hc/en-us).


## Tabeller

Använd [HTML-formatering för tabeller](https://www.w3schools.com/html/html_tables.asp).


## Varningar och informationsblock

Godkänd anteckningsblock:

```
>![success]
>
>This is a success note
```

Varningsblock:

```
>![warning]
>
>This is a warning
```

Informationsanteckningsblock:

```
>![info]
>
>This is a block with additional info
```
