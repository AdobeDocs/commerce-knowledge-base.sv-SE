---
title: 'B2B: Företag kan inte komma åt profilsidor på butikssidan'
description: I den här artikeln finns en patch för det kända Adobe Commerce 2.2.4 B2B-problemet som gäller när registrerade företag får felmeddelanden på sina kontosidor i butiken.
exl-id: 5f0d81a2-e0a1-487b-8a4f-28b8cb704e32
feature: B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# B2B: Företag kan inte komma åt profilsidor på butiksfront

I den här artikeln finns en patch för det kända Adobe Commerce 2.2.4 B2B-problemet som gäller när registrerade företag får felmeddelanden på sina kontosidor i butiken.

## Problem

Kunder (företag) kan skapa ett företagskonto på webbplatsen, men få *&quot;Ingen sådan enhet med customerId = &quot;* och *&quot;Du har inget företagskonto än&quot;* felmeddelanden. De kan också få *&quot;500 internt serverfel&quot;* när du försöker komma åt sidan Företagsprofil.

## Lappa

Om du vill hämta arkivet med en patch klickar du på följande länk:

[Ladda ned MDVA-9013\_EE\_2.2.2\_Composer.patch](assets/MDVA-9013_EE_2.2.2_composer.patch.zip)

### Kompatibla Adobe Commerce-versioner

Korrigeringen skapades för:

* Adobe Commerce lokal 2.2.2

Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* Adobe Commerce i molninfrastruktur från 2.2.0 till 2.2.4
* Adobe Commerce lokalt, från 2.2.0 till 2.2.1 och från 2.2.3 till 2.2.4

## Så här sätter du på plåstret

Se [Använda en kompositkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) för instruktioner.
