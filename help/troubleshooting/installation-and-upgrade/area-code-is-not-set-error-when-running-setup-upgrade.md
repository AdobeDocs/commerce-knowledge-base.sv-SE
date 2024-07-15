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

# Felet &#39;Riktnummer har inte angetts&#39; när `setup:upgrade` körs

I den här artikeln finns en patch för det kända Adobe Commerce-felet i molninfrastruktur 2.2.3 som rör hämtning av felet *&quot;Riktkoden är inte inställd&quot;* när följande kommando körs:

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

får du följande felmeddelande: *&quot;Module &#39;Magento\_AdvancedSalesRule&#39;: Installing data...Area code not set: Area code must be set before starting a session&quot;* and the command execution is broken. Problemet visas eftersom områdeskonfigurationen begärs innan den ställs in. Korrigeringen gör det möjligt att fånga upp felet och inte avbryta uppgraderingsprocessen.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Hämta MDVA-10439\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-10439_EE_2.2.3_COMPOSER_v1.patch.zip)

## Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce om molninfrastruktur 2.2.3

Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.2.0 - 2.2.3

## Så här sätter du på plåstret

Instruktioner finns i [Använda en dispositionsruta från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support.

## Bifogade filer
