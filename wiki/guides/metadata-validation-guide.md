---
source-git-commit: 0cfb7dc0dce68bcb0933a5ae49b0cd5a8b5b5a39
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---
# Guiden för validering av metadata

För att säkerställa korrekt formatering av metadata i MD-filer har vi infört ett metadatavalideringstest. Det här dokumentet innehåller riktlinjer som hjälper medarbetarna att undvika några av de vanligaste metadatavalideringsfelen.

**Exempel på metadata:**

```markdown
---
title: This is a title
labels: article,labels,tags
---

Article content...
```

## Vanliga valideringsfel och hur du undviker/åtgärdar dem

Nedan följer några av de vanligaste scenarierna där metadatavalideringsfel inträffar.

### Kolon i metadata

Ett valideringsfel uppstår om titeln eller etiketterna eller båda har kolon.

**Exempel:**

```markdown
---
title: Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,article,labels,tags
---
```

För att undvika det här felet kapslar du in titeln eller etiketterna (eller båda om båda har kolon) i **enkla citattecken**.

**Exempel:**

```markdown
---
title: 'Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure'
labels: 'patch: 2041.1,article,labels,tags'
---
```

### Kolon- och apostrof-tecken eller apostrof i metadata

Den tidigare lösningen fungerar inte om det finns kolon, apostrofer eller enkla citattecken i titeln eller etiketterna.

**Exempel:**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,'article',labels,tags
---
```

Det här felet åtgärdas genom att titeln eller etiketterna (eller båda) kapslas in i **citattecken**.

**Exempel:**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure"
labels: "patch: 2041.1,'article',labels,tags"
---
```

### Kolon, dubbelt citattecken och enkelt citattecken eller apostrof i metadata

**Exempel:**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe "Commerce" on cloud infrastructure
labels: patch: 2041.1,'article',"labels",can't,tags
---
```

När det inträffar omsluter du titeln eller etiketterna (eller båda) med **dubbla citattecken** och använder ett **omvänt snedstreck** för att undvika alla dubbla citattecken i titeln och etiketterna.

**Exempel:**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe \"Commerce\" on cloud infrastructure"
labels: "patch: 2041.1,'article',\"labels\",can't,tags"
---
```

### Fält saknas i metadata

Ett valideringsfel uppstår om antingen titelfältet eller etikettfältet saknas i metadata.

**Exempel:**

```markdown
---
title: This is a title
---
```

ELLER

```markdown
---
labels: article,labels,tags
---
```

Undvik det här felet genom att ta med båda fälten i metadata.

Etikettfältet kan lämnas tomt och det ger inget felmeddelande, men titelfältet måste fyllas i.

**Exempel:**

```markdown
---
title: Unlike labels the title field must be filled
labels:
---
```
