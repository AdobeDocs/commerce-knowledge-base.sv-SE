---
title: '[!UICONTROL salesRule] etiketterar problem vid uppgradering från version &lt; 2.4.5'
description: Använd en patch för att hantera **[!UICONTROL salesRule]**-problemen vid uppgradering från Adobe Commerce-versionerna &lt; 2.4.5.
exl-id: e1bd6d44-576e-4d91-bab5-32c41e3b8300
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# **[!UICONTROL salesRule]** etiketterar problem vid uppgradering från versioner &lt; 2.4.5

Etikettmellanlagringsfunktionen **[!UICONTROL salesRule]** introducerades i Adobe Commerce [ 2.4.5](/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html). Ändringen kan medföra problem när du uppgraderar från Adobe Commerce &lt; 2.4.5 till valfri version >= 2.4.5. Efter uppgraderingen kan det finnas en risk för att **[!UICONTROL salesRule]** etiketter inte matchar. För att åtgärda problemet bör en patch installeras direkt efter uppgraderingen till en nyare Adobe Commerce-version.

## Berörda produkter och versioner

Adobe Commerce i molninfrastruktur &lt; 2.4.5

## Lappa

Använd följande bifogade patch:

[ACSD-50625_2.4.5-P1.patch.zip](assets/ACSD-50625_2.4.5-p1.patch.zip)

## Så här sätter du på plåstret

1. Följ stegen i [Utför en uppgradering](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html?lang=sv-SE) i Commerce-guiden.
1. Använd den bifogade korrigeringen före **[!UICONTROL Update metadata]**-fasen.
(Du kan också tillämpa korrigeringen när du har slutfört **[!UICONTROL Update metadata]**-fasen, men sedan måste du köra `bin/magento setup:upgrade` igen).
1. Fortsätt med resten av stegen i [Utför en uppgradering](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html?lang=sv-SE).
