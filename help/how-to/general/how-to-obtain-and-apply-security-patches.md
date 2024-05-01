---
title: Hur man skaffar och tillämpar [!UICONTROL security patch]
description: I den här artikeln finns instruktioner om hur du hämtar och använder en [!UICONTROL security patch] som har släppts, men instruktioner är inte tillgängliga.
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: b15a1d008b6cc2bdce797768e6ee7029a747e6da
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Hur man skaffar och tillämpar en [!UICONTROL security patch]

I den här artikeln finns instruktioner om hur du hämtar och använder en [!UICONTROL security patch] som har släppts, men instruktioner är inte tillgängliga.

## Berörda produkter och versioner

Adobe Commerce On-Premise och Cloud - alla versioner

## Orsak

Mest [!UICONTROL Security Patches] släpps utan någon fysisk fil eller snabbkorrigering.

## Lösning


### Fall I:

Om en fysisk korrigeringsfil/snabbkorrigering anges i versionsinformationen:

* Ladda ned filen från nedladdningsdelen av [https://account.magento.com](https://account.magento.com/downloads/view/). (Delade åtkomstanvändare måste först tilldelas hämtningsbehörighet av kontoägaren/licenshavaren)

**Caveats:**

Om du har en äldre version av Adobe Commerce och har köpt Extended Support (Utökad support) måste din version vara något av följande för att du ska kunna tillämpa Security Patches (Säkerhetsuppdateringar):

* 2.4.2-p2
* 2.4.3-p3

Om du inte har Extended Support (Utökad support) kan du begära Support för att dela korrigeringsfilerna med dig, men de kan inte lösa eventuella problem eller fel som du kan stöta på när du tillämpar dem.

### Fall II:

Om en fysisk korrigeringsfil/snabbkorrigering inte omnämns i versionsinformationen:

* **Moln:**

1. Några [!UICONTROL Security Patches] kan ingå/släppas i den senaste versionen av Cloud Tools Suite (ECE-verktyg) under Cloud Patches for Commerce - kontrollera [Versionsinformation](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite)och om en säkerhetskorrigering nämns i den versionen uppgraderar du paketet till den versionen.
1. Om versionsinformationen inte innehåller någon säkerhetskorrigering kan du fortsätta läsa.

* **Moln eller lokal:**

* Om det inte finns någon fysisk korrigeringsfil/snabbkorrigering tillgänglig [uppgradera Adobe Commerce-versionen till Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X till den senaste patchversionen 2.4.X-pY.
* Om det inte finns någon fysisk korrigeringsfil/snabbkorrigering tillgänglig [uppgradera Adobe Commerce-versionen On-Premise](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X till den senaste patchversionen 2.4.X-pY.

## Relaterad läsning

* Se [Versionsinformation om Commerce Cloud Tools Suite](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) i *Infrastrukturhandbok för Adobe Commerce on Cloud*.
* Se [Uppgradera Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) i *Infrastrukturhandbok för Adobe Commerce on Cloud*.
