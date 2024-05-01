---
title: '''[!UICONTROL salesRule] etiketter vid uppgradering från version &lt; 2.4.5'
description: Använd en patch för att hantera **[!UICONTROL salesRule]** problem vid uppgradering från Adobe Commerce version &lt; 2.4.5.
exl-id: e1bd6d44-576e-4d91-bab5-32c41e3b8300
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# **[!UICONTROL salesRule]** etikettproblem vid uppgradering från versioner &lt; 2.4.5

The **[!UICONTROL salesRule]** funktionen för etikettmellanlagring infördes i Adobe Commerce [2.4.5](/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html). Ändringen kan medföra problem när du uppgraderar från Adobe Commerce &lt; 2.4.5 till valfri version >= 2.4.5. Efter uppgraderingen finns det en möjlighet att **[!UICONTROL salesRule]** etiketter matchar inte. För att åtgärda problemet bör en patch installeras direkt efter uppgraderingen till en nyare Adobe Commerce-version.

## Berörda produkter och versioner

Adobe Commerce i molninfrastruktur &lt; 2.4.5

## Lappa

Använd följande bifogade patch:

[ACSD-50625_2.4.5-P1.patch.zip](assets/ACSD-50625_2.4.5-p1.patch.zip)

## Så här sätter du på plåstret

1. Följ stegen i [Uppgradera](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html) i Commerce Guide.
1. Använd det bifogade plåstret före **[!UICONTROL Update metadata]** fas.
(Du kan också applicera plåstret när du har slutfört **[!UICONTROL Update metadata]** men du måste köra `bin/magento setup:upgrade` än en gång).
1. Fortsätt med resten av stegen i [Uppgradera](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
