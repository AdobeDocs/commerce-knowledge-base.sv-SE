---
title: "'Riktnummer har inte angetts'-fel vid installation:uppgradering"
description: I den här artikeln finns en patch för det kända problemet med Adobe Commerce i molninfrastruktur 2.2.3 som rör felet *Områdeskoden är inte inställd* när du kör kommandot setup:upgrade.
exl-id: ace92331-6022-49fa-a776-d06d841b3b32
feature: Install, Upgrade
role: Developer
source-git-commit: 4617b915a62093e00da428a753d913a39d30f3a0
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Felet &#39;Riktkod har inte angetts&#39; vid körning `setup:upgrade`

Den här artikeln innehåller en patch för det kända problemet med Adobe Commerce i molninfrastruktur 2.2.3 som gäller hämtning av *&quot;Riktnummer har inte angetts&quot;* fel vid körning av följande kommando:

```bash
setup:upgrade
```

>[!NOTE]
>
>Problemet har åtgärdats i Adobe Commerce 2.2.4.

## Problem

När du kör

```bash
bin/magento setup:upgrade
```

får du följande felmeddelande: *&quot;Modul &#39;Magento\_AdvancedSalesRule&#39;: Installerar data...Riktkoden har inte angetts: Riktkoden måste anges innan en session startas&quot;* och kommandokörningen avbryts. Problemet visas eftersom områdeskonfigurationen begärs innan den ställs in. Korrigeringen gör det möjligt att fånga upp felet och inte avbryta uppgraderingsprocessen.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Hämta MDVA-10439\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-10439_EE_2.2.3_COMPOSER_v1.patch.zip)

## Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce om molninfrastruktur 2.2.3

Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.2.0 - 2.2.3

## Så här sätter du på plåstret

Instruktioner finns i [Använda en kompositkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

## Bifogade filer
