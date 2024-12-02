---
title: 'Distributionen misslyckas med felet"Error building project: The build krok failed with status code 1"'
description: 'I den här artikeln beskrivs orsakerna till och lösningarna för Adobe Commerce när det gäller molninfrastruktursproblem, där installationsfasen misslyckas och felmeddelandet sammanfattas med: *"Fel när projekt byggs: Bygget misslyckades med statuskod 1"*.'
exl-id: add1cdac-dbcb-4c55-8bc2-c1f27e24aadb
feature: Build, Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 0%

---

# Distributionen misslyckas med felet&quot;Error building project: The build krok failed with status code 1&quot;

I den här artikeln beskrivs orsaker och lösningar till Adobe Commerce-problemet med molninfrastruktur, där distributionsprocessens byggfas misslyckas, och felmeddelandet sammanfattas med: *&quot;Fel när projekt byggs: Bygget misslyckades med statuskod 1&quot;*.

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur, alla versioner

## Problem

<u>Steg som ska återskapas</u>:

Utlös distributionen manuellt eller genom att utföra en sammanslagning, push eller synkronisering av din miljö.

<u>Förväntat resultat</u>:

Distributionen har slutförts.

<u>Faktiskt resultat</u>:

1. Byggfasen misslyckas och hela installationsprocessen fastnar.
1. I distributionsfelloggen avslutas felmeddelandet med: *&quot;Fel när projektet skapades: Bygge-kroken misslyckades med statuskod 1. Avbruten generering.*

## Orsak

Det finns många orsaker till varför det inte går att bygga upp miljön. Vanligtvis visas ett långt felmeddelande i distributionsloggen, där den första delen skulle vara mer specifik med avseende på orsaken och slutsatsen skulle vara *&quot;Fel när projektet byggdes: Byggkopplingen misslyckades med statuskod 1. Avbruten generering.*

Om du tittar närmare på den första problemspecifika delen kan du identifiera problemet. Här är de vanligaste och i nästa avsnitt finns lösningar:

* Det finns inget tillgängligt lagringsutrymme.
* Ogiltig ECE-verktygskonfiguration.
* Den korrigering du försöker tillämpa är inte kompatibel med din Adobe Commerce-version eller har konflikter med andra korrigeringsfiler som används eller dina anpassningar.
* Problem med anpassad modulkod förhindrar att det går att skapa.

## Lösning

* Kontrollera att det finns tillräckligt med lagringsutrymme. Mer information om hur du kontrollerar tillgängligt utrymme finns i artikeln [Kontrollera diskutrymme i molnmiljö med CLI](/help/how-to/general/check-disk-space-on-cloud-environment-using-cli.md) . Du kan överväga att rensa loggkatalogerna och/eller öka diskutrymmet.
* Kontrollera att ECE-verktygen är korrekt konfigurerade.
* Kontrollera om det är korrigeringen som orsakar problemet. Lös konflikten eller kontakta [Adobe Commerce Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Mer information finns nedan.
* Kontrollera om det är det anpassade tillägg som orsakar problemet. Lös konflikten eller kontakta tilläggsutvecklarna för lösningen.

I följande stycken finns mer information.

### Rengör loggar och/eller öka utrymmet

Kataloger som ska beaktas för rensning:

* `var/log`
* `var/report`
* `var/debug/`
* `var`

Mer information om hur du kan öka diskutrymmet om du använder Adobe Commerce för startplanens arkitektur för molninfrastruktur finns i [Öka diskutrymmet för integreringsmiljön i molnet](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md). Samma instruktioner kan användas för att öka utrymmet för Adobe Commerce i molninfrastrukturen Pro-planens integreringsmiljö. För Pro Production/Staging måste du registrera en biljett till [Adobe Commerce Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) och begära utökat diskutrymme. Men det övervakas av Platform. I vanliga fall behöver du inte hantera detta när Adobe Commerce övervakar parametrarna och meddelar dig och/eller vidtar åtgärder enligt avtalet.

### Kontrollera att ECE-verktygen är korrekt konfigurerade

1. Kontrollera att build-hooks har definierats korrekt i filen `magento.app.yaml`. Om du använder Adobe Commerce 2.2.X ska du definiera byggkrokar enligt följande:

   ```yaml
   # We run build hooks before your application has been packaged.
   build: |
       php ./vendor/bin/ece-tools build
   # We run deploy hook after your application has been deployed and started.
   deploy: |
       php ./vendor/bin/ece-tools deploy
   ```

   Använd artikeln [Uppgradera till ece-tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/install-package) som referens.

1. Kontrollera att ECE-verktygspaketet finns i filen `composer.lock` genom att köra följande kommando:    <pre><code class="language-bash">grep &#39;<code class="language-yaml">&quot;name&quot;: &quot;magento/ece-tools&quot;</code>&#39; disposition.lock</code></pre>    Om de anges ser svaret ut som i följande exempel:    ```bash    "name": "magento/ece-tools",    "version": "2002.0.20",    ```

Referens finns i artikeln [Uppgradera till delade verktyg](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/install-package).

### Orsakar korrigeringen problemet?

Om det är den tillämpade korrigeringen som förhindrar miljön från att skapas korrekt, kommer du att se något liknande i distributionsloggen:

```bash
%patch_name%.composer.patch
[2019-02-19 18:12:59] CRITICAL:
....
[2019-02-19 18:12:59] CRITICAL: Command git apply --check --reverse /app/m2-hotfixes/%patch_name%.composer.patch returned code 1
...
W:
W: Command git apply --check --reverse /app/m2-hotfixes/%patch_name%.composer.patch returned code 1
W:
W:
W: build
...
E: Error building project: The build hook failed with status code 1. Aborted build.
```

Dessa felmeddelanden innebär att den korrigering du försöker tillämpa antingen har skapats för en annan version av Adobe Commerce eller är i konflikt med dina anpassningar eller tidigare tillämpade korrigeringar. Försök att lösa konflikten eller kontakta [Adobe Commerce Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Är tillägget orsaken till problemet?

Om det är det anpassade tillägg som förhindrar att miljön kan byggas ut visas namnen på de anpassade modulerna i distributionsloggen tillsammans med den särskilda konflikt som den här modulen orsakat. Lös konflikten eller kontakta tilläggsutvecklarna för lösningen.

### Se till att ändringarna tillämpas

Verkställ och push-styr ändringarna. Detta utlöser distributionen automatiskt.
