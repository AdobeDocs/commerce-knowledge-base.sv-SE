---
title: Felsöka fel i verktyg för uppgraderingskompatibilitet
description: I den här artikeln beskrivs fel som kan uppstå när du använder verktyget för kompatibilitetsuppgradering och lösningar för att åtgärda felen så att du kan köra verktyget.
exl-id: 1cce1146-942e-46cb-a395-8da9e472cd39
feature: Customer Service, Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Felsöka fel i verktyg för uppgraderingskompatibilitet

I den här artikeln beskrivs fel som kan uppstå när du använder verktyget för kompatibilitetsuppgradering och lösningar för att åtgärda felen så att du kan köra verktyget.

## Berörda produkter och versioner

* [Kompatibilitetsverktyget för uppgradering](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html) är kompatibelt med Adobe Commerce-versioner från och med 2.3.0.

## Segmenteringsfel

<u>Orsak</u>:

När två moduler har samma namn visas ett segmenteringsfel i verktyget Kompatibilitet för uppgradering.

<u>Lösning</u>:

För att undvika det här felet bör du ange sökvägen till modulen som ett argument:

```bash
bin/uct upgrade:check --current-version=2.4.4 path/to/the/module
```

>[!WARNING]
>
> Kompatibilitetsverktyget för uppgradering kanske inte kan analysera kodbasen om den innehåller cirkulärt beroende mellan metoder.

## Tomma utdata

<u>Steg som ska återskapas</u>:

1. Om du har kört det här kommandot:

   ```bash
   bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
   ```

1. Den enda utdata är `Upgrade compatibility tool`:

   ```terminal
   bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
   Upgrade compatibility tool
   ```

<u>Orsak</u>:

Den troliga orsaken är en minnesbegränsning för PHP.

Det finns två möjliga lösningar för att undvika denna minnesbegränsning för PHP.

<u>Lösning 1</u>:

Åsidosätt minnesbegränsningen genom att ange `memory_limit` till `-1`:

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

>[!NOTE]
>
> `M2_VERSION` är den Adobe Commerce-målversion som du vill jämföra med din Adobe Commerce-instans.

<u>Lösning 2</u>:

Om du lägger till alternativet `-m` kan verktyget Kompatibilitet för uppgradering analysera varje enskild modul för att undvika att stöta på två moduler med samma namn i din Adobe Commerce-instans.

Med det här kommandoalternativet kan du även analysera en mapp som innehåller flera moduler med verktyget Kompatibilitet för uppgradering:

```bash
bin/uct upgrade:check /<dir>/<instance-name> -m /vendor/<vendor-name>/
```

Mer information om gränssnittsalternativ för kommandorad finns på sidan [Kör verktyget i ett kommandoradsgränssnitt](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/run.html) .
