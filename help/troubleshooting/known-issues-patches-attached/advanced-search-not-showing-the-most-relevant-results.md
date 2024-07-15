---
title: Avancerad sökning som inte visar de mest relevanta resultaten
description: I den här artikeln finns en patch för det kända Adobe Commerce-problemet, där den avancerade sökningen inte visar de mest relevanta resultaten först.
exl-id: 88f0782d-ba7d-4f19-9761-7894d978d334
feature: Search
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Avancerad sökning som inte visar de mest relevanta resultaten

I den här artikeln finns en patch för det kända Adobe Commerce-problemet, där den avancerade sökningen inte visar de mest relevanta resultaten först.

## Berörda versioner {#Advancedsearchnotshowingmostrelevantresults-Affectedversions}

* Adobe Commerce (alla installationsalternativ) 2.x.x
* Magento Open Source 2.x.x

## Problem {#Advancedsearchnotshowingmostrelevantresults-Description}

Den avancerade sökfunktionen returnerar inte de mest relevanta resultaten först, som snabbsökningen gör. Problemet beror inte på den valda sökmotortypen.

<u>Steg att återskapa:</u>

1. Gå till snabbsökningen i butiken och sök efter &quot;Anpassa fodral&quot;.
1. Observera att&quot;Riktat fodral med två toningar&quot; är det första resultatet.
1. Gå till avancerad sökning och sök efter &quot;Anpassa fodral&quot; i namnfältet.

<u>Förväntat resultat:</u>

&quot;Invändigt fodral med två färgtoner&quot; är det första resultatet när avancerad sökning används, som det mest relevanta resultatet.

<u>Faktiskt resultat:</u>

&quot;Orion Two-Tone Fsigned Jacket&quot; är inte det första resultatet, även om det är det mest relevanta.

## Lösning {#Advancedsearchnotshowingmostrelevantresults-Solution}

Du löser problemet genom att tillämpa den patch som är bifogad den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Ladda ned MDVA-7256\_EE\_2.1.7\_v1.comser.patch](assets/MDVA-7256_EE_2.1.7_v1.composer.patch.zip)

Korrigeringen lägger till implementeringen för sortering efter relevans för avancerade sökresultat som standardsorteringsfält.

Korrigeringen är kompatibel med alla berörda versioner och utgåvor.

## Så här sätter du på plåstret

Instruktioner finns i [Använda en dispositionsruta från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

## Bifogade filer
