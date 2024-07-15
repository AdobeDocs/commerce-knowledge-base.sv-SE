---
title: När du använder en korrigeringsfil tar det längre tid att lägga på webbplatsen
description: Den här artikeln handlar om ett problem där en korrigering som du just tillämpade tar ner din webbplats. Du kan lösa problemet genom att ta bort patchen.
exl-id: dc765bcd-0761-4efd-a345-46a908d61272
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# När du använder en korrigeringsfil tar det längre tid att lägga på webbplatsen

Den här artikeln handlar om ett problem där en korrigering som du just tillämpade tar ner din webbplats. Du kan lösa problemet genom att ta bort patchen.

## Berörda produkter och versioner

* Adobe Commerce (alla distributionsmetoder), alla versioner som stöds
* Magento Open Source, alla versioner

## Problem

När du har tillämpat en korrigering kommer platsen att krascha.

## Orsak

Det här problemet kan uppstå på grund av en versionsinkompatibilitet mellan den korrigering du just tillämpade på webbplatsen, dina anpassningar, andra korrigeringar som du använt tidigare eller något annat fel.

## Lösning

Ta bort plåstret. Metoden för borttagning av korrigeringsfiler skiljer sig åt för Adobe Commerce i molninfrastrukturen jämfört med för Adobe Commerce lokalt och Magento Open Source.

### Magento Open Source, alla 1.X-versioner

För Magento Open Source 1.X-versioner

* Kör följande SSH-kommando: `h SUPEE_patch --revert `

### Adobe Commerce lokalt, Magento Open Source, alla 2.x-versioner

För Adobe Commerce lokalt och Magento Open Source 2.x

1. Kör följande SSH-kommando:

   ```
   patch -p1 -R %patch_name%.composer.patch
   ```

   (Om ovanstående kommando inte fungerar kan du försöka med att använda `-p2` i stället för `-p1`.)

1. Uppdatera cacheminnet i administratören under **System** > **Cachehantering** för att ändringarna ska återspeglas.

### Adobe Commerce om molninfrastruktur, alla versioner

För Adobe Commerce om molninfrastruktur gäller alla versioner,

1. Ta bort `%patch_name%.composer.patch` fil(er) från katalogen `m2-hotfixes`.
1. Verkställ och skicka dina kodändringar:

   ```
   git commit -m "Remove %patch_name%.composer.patch patch" && git push origin
   ```

## Relaterad läsning

* [Använda en kompositörkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.
