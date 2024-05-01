---
title: Lösa UTF-8-fel för CSV-filöverföringar
description: I den här artikeln finns en fix som du kan använda när felmeddelandet"CSV-filer måste använda UTF-8-kodning" visas. Det här felmeddelandet innebär att filen som du försöker överföra innehåller ogiltiga tecken, eller otillåtna tecken. UTF-8-kodning tillåter [de flesta tecken](https://www.fileformat.info/info/charset/UTF-8/list.htm), men vissa är inte kompatibla med Magento BI.
exl-id: 88d8e0b8-152e-4a6d-bc44-3b285e0eb0c3
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Lösa UTF-8-fel för CSV-filöverföringar

I den här artikeln finns en fix som du kan använda när felmeddelandet&quot;CSV-filer måste använda UTF-8-kodning&quot; visas. Det här felmeddelandet innebär att filen som du försöker överföra innehåller ogiltiga tecken, eller otillåtna tecken. UTF-8-kodning tillåter [de flesta tecken](https://www.fileformat.info/info/charset/UTF-8/list.htm), vissa är inte kompatibla med Magento BI.

För att åtgärda problemet måste du ändra filens kodning. Om du sparar om filen med rätt kodning löses vanligtvis problemet, men du kan förlora viss information (till exempel kan ogiltiga tecken tas bort) när du gör detta.

Vi rekommenderar att du [Publicera text](https://www.sublimetext.com/2) för att spara och koda filen.

1. Öppna filen i Microsoft Excel, Google Docs, Apple Numbers eller i valfritt program.
1. Klicka på &#x200B; &#x200B; **Fil** > **Spara som** &#x200B; &#x200B; och välj &#x200B; &#x200B; **Kommaavgränsade värden (.csv)** format för att spara filen.
1. Öppna CSV-filen i Publicera text.
1. Navigera till &#x200B; &#x200B; i Publicera text **Fil** > **Spara med kodning** > **UTF-8\* &#x200B;** . Detta sparar CSV-filen med UTF-8-kodning.    ![csv_file_UTF-8_sublime_3.2.2_magento_BI.png](assets/csv_file_UTF-8_sublime_3.2.2_magento_BI.png)
1. [Överför data](https://docs.magento.com/mbi/data-analyst/importing-data/connecting-data/using-file-uploader.html) (i vår användarhandbok) till en ny tabell i Magento BI.
