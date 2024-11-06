---
title: Radera filer säkert när det inte finns tillräckligt med utrymme på disken i Adobe Commerce i molninfrastrukturen
description: Den här artikeln innehåller en lösning för när diskutrymmet tar slut och du behöver ta bort filer på ett säkert sätt. Innan du överväger den här åtgärden bör du läsa [Hantera diskutrymme](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#no-space-left) i utvecklardokumentationen. Om stegen i den artikeln inte är lämpliga för dig eller inte löser problemet kan du läsa stegen i den här artikeln.
exl-id: 6b0a5c1a-8db4-49d7-a785-b4e0bbaea0df
feature: Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Radera filer säkert när det inte finns tillräckligt med utrymme på disken i Adobe Commerce i molninfrastrukturen

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur 2.4.2 - 2.4.7
* Detta gäller specifikt för dedikerade Pro-kluster. Start- och integreringsmiljöer är en nod och har inte katalogen `/data/exports`.

## Tecken på otillräckligt diskutrymme

Signeringar som tar slut på diskutrymme kan fastna i driftsättningen, få diskvarningar och få sämre prestanda.
Om du vill se hur mycket diskutrymme som används i filsystemet kör du följande kommando i CLI/Terminal:

`df -h`


## Hur man tar bort filer på ett säkert sätt för att öka diskutrymmet

Du kan ta bort filer från programmets monteringspunkter, från sökvägen `/app` eller till `/mnt/shared`. Det finns två olika sätt att få åtkomst till samma filer.

>[!WARNING]
>
>**Ändra eller ta aldrig bort innehållet i`/data/exports`**.
>
>`/data/exports` är det underliggande lagringsutrymmet bakom det delade filsystemet och hanteras av GlusterFS.
>
>Filsystemet där innehåller inte bara filinnehållet, utan metadata om filsystemets tillstånd som möjliggör synkronisering >mellan noderna i klustret. **Om du ändrar eller tar bort filer direkt i det här filsystemet skadas det delade >filsystemet, vilket kräver omfattande reparationer eller dataåterställning.**

Om du vill hitta de största filerna som kan vara lämpliga för rensning kör du följande kommando (i stora eller upptagna projekt kan det ta upp till en timme):

```bash
FS='/data/exports';NUMRESULTS=20;resize;clear; echo "Please find below the Largest Directories and Files:";date;df -h $FS; echo "Largest Directories:";nice -n 19 find /app/*/ -type d -ls 2>/dev/null| sort -rnk1| head -n $NUMRESULTS| awk '
{printf "%d MB %s\n", $1/1024,$2}
';echo "Largest Files:"; nice -n 19 find /app/*/ -type f -ls 2>/dev/null| sort -rnk7| head -n $NUMRESULTS|awk '
{printf "%d MB\t%s\n", ($7/1024)/1024,$NF}
'; echo "Please use the above information to clear any unwanted data from the server, it is important this is done as soon as possible to ensure your server stays functional.";
```

Kommandots utdata innehåller en lista med de största filerna och katalogerna med angiven storlek.

## Relaterad läsning

I vår kunskapsbas:

* [Öka diskutrymmet för integreringsmiljön i molnet](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md)
* [Ont om diskutrymme](/help/troubleshooting/miscellaneous/low-disk-space.md)

I vår utvecklardokumentation:

* [Hantera diskutrymme](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space)
