---
title: Fler produkter togs bort än initierades under massborttagning i Admin
description: Den här artikeln innehåller en patch för den kända Adobe-С om molninfrastruktur 2.2.3 som handlar om att inte ta bort markerade poster när en massborttagning utförs i ett rutnät i Commerce Admin.
exl-id: 0bfdc84e-0292-4702-a20e-bdbe67c111a2
feature: Admin Workspace, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Fler produkter togs bort än initierades under massborttagning i Admin

Den här artikeln innehåller en patch för den kända Adobe-С om molninfrastruktur 2.2.3 som handlar om att inte ta bort markerade poster när en massborttagning utförs i ett rutnät i Commerce Admin.

## Problem

Om du markerar kund- eller klientposter som ska tas bort i Admin, filtrerar rutnätet och sedan väljer åtgärden **Ta bort** tas alla poster bort.

<u>Steg som ska återskapas</u>:

1. Navigera till **Katalog** > **Produkter** i Admin.
1. Välj en eller flera produkter.
1. Välj Ta bort i listrutan Åtgärder.

<u>Förväntade resultat</u>:

Endast valda produkter tas bort.

<u>Faktiska resultat</u>:

Vissa andra produkter tas också bort.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk:

[Hämta MDVA-10600\_EE\_2.2.3\_v1.comser.patch](assets/MDVA-10600_EE_2.2.3_v1.composer.patch.zip)

### Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce om molninfrastruktur 2.2.3

Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce lokal 2.1.8-2.1.14, 2.2.0-2.2.2 och 2.2.4-2.2.5
* Adobe Commerce om molninfrastruktur 2.2.4-2.2.5

## Så här sätter du på plåstret

Mer information finns i [Använda en dispositionsruta från Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).
