---
title: 404 Fel i butiksleverans när uppdatering av katalogiffegler har utförts
description: I den här artikeln finns en korrigeringsfil och de steg som krävs för att åtgärda det kända Adobe Commerce 2.2.1-problemet som rör att få ett 404-fel på alla butikssidor, efter att en uppdatering av katalogprisregeln har skapats och starttiden redigerades senare. För att åtgärda problemet måste du installera korrigeringen.
exl-id: 7ea148a5-56cb-479a-8b2f-fae8b3bd4b22
feature: Cache, Catalog Management, Marketing Tools, Orders, Price Rules
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# 404 Fel i butiksleverans när uppdatering av katalogiffegler har utförts

I den här artikeln finns en korrigeringsfil och de steg som krävs för att åtgärda det kända Adobe Commerce 2.2.1-problemet som rör att få ett 404-fel på alla butikssidor, efter att en uppdatering av katalogprisregeln har skapats och starttiden redigerades senare. För att åtgärda problemet måste du installera korrigeringen.

## Problem

Det går inte att komma åt butikssidor, vilket returnerar 404-fel. Problemet uppstår när den aktiva katalogens prisregeluppdatering förfaller, under förutsättning att startdatumet för den här uppdateringen redigerades efter det att den första uppdateringen skapades.

<u>Steg som ska återskapas</u>:

1. I Commerce Admin skapar du en ny katalogprisregel under **Marknadsföring** > **Kampanjer** > **Katalogprisregel**.
1. Klicka på **Redigera** i rutnätet **Katalogens prisregel** och schemalägg en ny uppdatering och ange **Status** till *Aktiv.*
1. Navigera till **Innehåll** > **Förproduktion av innehåll** > **Kontrollpanel.**
1. Markera den nyligen skapade uppdateringen och ändra dess starttid.
1. Spara ändringarna.

<u>Förväntat resultat</u> :

När uppdateringens startdatum börjar gälla tillämpas katalogprisregeln.

<u>Faktiskt resultat</u> :

När uppdateringens startdatum börjar gälla blir alla kataloger och produkter i butiken otillgängliga och returnerar felet 404.

## Lösning

Om du vill återställa katalogsidor och kunna använda uppdateringsfunktionen för katalogprisregler fullt ut måste du installera korrigeringsfilen, ta bort regeln både manuellt och i administratören och åtgärda de ogiltiga länkarna i databasen. Du måste också återskapa katalogprisregeln.

Här följer en detaljerad beskrivning av de steg som krävs:

1. [Använd korrigeringen](#patch).
1. I Commerce Admin tar du bort katalogprisregeln för problemet (där starttiden uppdaterades). Det gör du genom att öppna regelsidan under **Marknadsföring** > **Kampanjer** > **Katalogprisregel** och klicka på **Ta bort regel**.
1. Om du öppnar databasen manuellt tas den relaterade posten bort från tabellen `catalogrule`.
1. Åtgärda ogiltiga länkar i databasen. Mer information finns i det [relaterade stycket](#fix_links).
1. Gå till **Kampanjer** > **Katalogprisregel** i Commerce Admin under **Markering** och skapa den nya regeln med den konfiguration som krävs.
1. Rensa webbläsarcachen under **System** > **Cachehantering**.
1. Kontrollera att cron-jobben är korrekt konfigurerade och kan köras.

## Lappa {#patch}

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Hämta MDVA-7392\_EE\_2.2.1\_COMPOSER\_v2.patch](assets/MDVA-7392_EE_2.2.1_COMPOSER_v2.patch.zip)

## Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce 2.2.1

Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce om molninfrastruktur 2.2.0 - 2.2.4
* Adobe Commerce lokal 2.2.0 och 2.2.2 - 2.2.4

## Så här sätter du på plåstret

Mer information finns i [Använda en dispositionsruta från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

## Åtgärda ogiltiga länkar till mellanlagring i DB {#fix_links}

>[!WARNING]
>
>Vi rekommenderar starkt att du skapar en säkerhetskopia av databasen före eventuella databasändringar. Vi rekommenderar också att du testar frågor om utvecklingsmiljön först.

Följ de här stegen för att korrigera raderna med ogiltiga länkar till tabellen `staging_update`.

1. Kontrollera om de ogiltiga länkarna till tabellen `staging_update` finns i tabellen `flag`. Det här är poster där `flag_code=staging`.
1. Identifiera den ogiltiga versionen från tabellen `flag` med följande fråga:

   ```sql
   SELECT flag_data FROM flag WHERE flag_code = 'staging';
   ```

1. I tabellen `staging_update` väljer du den befintliga versionen som är mindre än den aktuella (ogiltiga) versionen och hämtar versionsvärdet som är två siffror tillbaka. Du kan använda den, inte den föregående versionen, för att undvika situationen när den tidigare versionen är den högsta versionen i tabellen `staging_update` som kan användas och vi fortfarande måste tillämpa den igen.

   ```sql
   SELECT id FROM staging_update WHERE id < %current_id% ORDER BY id DESC LIMIT 1, 1
   ```

   Versionen du får som svar är din giltiga version `id`.

1. För rader med ogiltiga länkar i tabellen `flag` anger du `flag_data`-värdena till data som ska innehålla ett giltigt versions-ID. Detta hjälper till att spara prestanda vid omindexering och gör att du kan undvika omindexering av alla enheter.

   ```sql
   UPDATE flag SET flag_data=REPLACE(flag_data, '%invalid_id%', '%new_valid_id%') WHERE flag_code='staging';
   ```

<u>Exempel:</u>

```sql
SELECT flag_data FROM flag WHERE flag_code = 'staging'; <code class="language-bash">Response < 2.2 version</code>
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| a:1:{s:15:"current_version";s:10:"1490005140";} |
```

```bash
+-------------------------------------------------+
```

```bash
Response from 2.2 version
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| {"current_version":"1490005140"} |
```

```bash
+-------------------------------------------------+
```

```sql
SELECT id FROM staging_update WHERE id < 1490005140 <code class="language-sql">ORDER BY id DESC LIMIT 1, 1</code>;
```

```bash
Response:
```

```bash
1490005138
```

```sql
UPDATE flag SET flag_data=REPLACE(flag_data, '1490005140', '1490005138') WHERE flag_code='staging';
```

## Bifogade filer
