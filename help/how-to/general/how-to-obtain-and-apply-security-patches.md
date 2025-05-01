---
title: Så här hämtar och använder du [!UICONTROL security patch]
description: Den här artikeln innehåller anvisningar om hur du hämtar och använder en [!UICONTROL security patch] som har släppts, men det finns inga instruktioner.
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: 3c7234b52e5e4465d95c95345e1c070c28600dfb
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# Så här hämtar och använder du en [!UICONTROL security patch]

>[!NOTE]
>Om du har en lokal installation och inte använder versionskontrollsystem som [!DNL CVS] eller [!DNL GitHub] för att hantera koden, kan din webbvärd kanske hjälpa dig med att tillämpa korrigeringen. Kontakta dem gärna om du behöver hjälp.

Den här artikeln innehåller anvisningar om hur du hämtar och använder en [!UICONTROL security patch] som har släppts, men det finns inga instruktioner.

## Berörda produkter och versioner

Adobe Commerce On-Premise och Cloud - alla versioner


## Orsak

De flesta [!UICONTROL Security Patches] släpps utan någon isolerad korrigering eller snabbkorrigering och måste uppgraderas till [!UICONTROL Security Patch]-versionen.

## Lösning


### Fall I:

* Om en isolerad korrigeringsfil/snabbkorrigering anges i [Versionsinformation](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-tools-suite) hämtar du filen från hämtningsavsnittet på [https://account.magento.com](https://account.magento.com/downloads/view/). Användare med delad åtkomst måste först få hämtningsbehörighet av kontoägaren/licenshavaren.

**Caveats:**

Om du har en äldre version av Adobe Commerce (2.4.4) har du automatiskt fått utökad support. Din version måste vara en av följande versioner som inte stöds för att du ska kunna tillämpa de senaste tillgängliga säkerhetsuppdateringarna:

2.4.4 - 2.4.4-p11

Versioner som inte stöds (2.3.x, 2.4.0 - 2.4.3) har inte rätt till support och du måste först uppgradera till en version som stöds för att kunna utnyttja de senaste säkerhetskorrigeringarna.

Om du inte har Extended Support (Utökad support) kan du begära Support för att dela korrigeringsfilerna med dig, men de kan inte lösa eventuella problem eller fel som du kan stöta på när du tillämpar dem.

### Fall II:

Isolerade korrigeringsfiler tillhandahålls endast i undantagsfall och är inte den rekommenderade formen för implementering av säkerhetskorrigeringar.

Om en isolerad korrigeringsfil/snabbkorrigering inte omnämns i versionsinformationen:

* **Cloud:**

1. Vissa [!UICONTROL Security Patches] kan ingå/släppas i den senaste versionen av Cloud Tools Suite (ECE-verktyg) under Cloud Patches for Commerce - kontrollera [Versionsinformation](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) och om en säkerhetskorrigering nämns i den versionen uppgraderar du paketet till den versionen.
1. Om versionsinformationen inte innehåller någon säkerhetskorrigering kan du fortsätta läsa.

* **Cloud eller lokal:**

* Om det inte finns någon isolerad korrigeringsfil/snabbkorrigering kan du [uppgradera Adobe Commerce-versionen i molnet](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X till den senaste korrigeringsversionen, 2.4.X-pY.
* Om det inte finns någon isolerad korrigeringsfil/snabbkorrigering kan du [uppgradera Adobe Commerce-versionen On-Premise](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X till den senaste korrigeringsversionen, 2.4.X-pY.

## Relaterad läsning

* Se [Versionsinformation om Commerce Cloud Tools Suite](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) i *Adobe Commerce on Cloud Infrastructure Guide*.
* Se [Uppgradera Adobe Commerce-versionen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) i *Adobe Commerce on Cloud Infrastructure Guide*.
