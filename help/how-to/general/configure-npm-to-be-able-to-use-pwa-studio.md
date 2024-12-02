---
title: Konfigurera NPM för att kunna använda PWA Studio
description: '[Progressive Web Apps (PWA) Studio](https://magento.github.io/pwa-studio/) är ett nytt projekt för Adobe Commerce i molninfrastruktur 2.3.x eller senare. För att kunna använda och installera PWA Studio måste du ställa in NPM-pakethanterarversionen på 5.x eller senare för att få stöd för Node.js 8.x. Detta görs i avsnittet "hooks:build" i konfigurationsfilen `.magento.app.yaml".'
exl-id: 3854fc94-e8ad-45d8-bf3e-73462364220d
source-git-commit: 37ac9cca1f876a48092467aa38f2f2f013c83dd9
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Konfigurera NPM för att kunna använda PWA Studio

[Progressiva webbprogram (PWA) Studio](https://magento.github.io/pwa-studio/) är ett nytt projekt som är tillgängligt för Adobe Commerce i molninfrastruktur 2.3.x eller senare. För att kunna använda och installera PWA Studio måste du ställa in NPM-pakethanterarversionen på 5.x eller senare för att få stöd för Node.js 8.x. Detta görs i avsnittet `hooks:build` i konfigurationsfilen `.magento.app.yaml`.

## Miljö och teknik

* Adobe Commerce i molninfrastruktur 2.3.X
* PWA för Adobe Commerce

## Ange NPM-version: steg

Om du vill ange den NPM-version som behövs anger du den i konfigurationsfilen `.magento.app.yaml`. Följ de här stegen:

1. Leta reda på konfigurationsfilen `.magento.app.yaml` i den lokala utvecklingsmiljön.
1. Öppna filen för redigering med den vanliga textredigeraren eller IDE.
1. Ange den version som krävs i avsnittet `hooks:build`. I följande exempel är konfigurationen inställd på att installera NPM v9.5.0, den högsta tillgängliga för tillfället (4 februari 2019):

   ```yaml
   hooks:
       build: |
           unset NPM_CONFIG_PREFIX
           curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
           export NVM_DIR="$HOME/.nvm"
           [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
           nvm install 9.5.0
   ```

   >[!NOTE]
   >
   >Om du vill köra Node.JS i ditt program och inte bara i ditt bygge lägger du till följande kommandon för att ändra din build-krok:
   > 
   ```
   > echo 'unset NPM_CONFIG_PREFIX' >> .environment
   > echo 'export NO_UPDATE_NOTIFIER=1' >> .environment
   > echo 'export NVM_DIR="$MAGENTO_CLOUD_DIR/.nvm"' >> .environment
   > echo '[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"' >> .environment
   > ```

1. Spara ändringarna i filen.
1. Git skickar den redigerade filen till din [integreringsmiljö](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md).

Ändringarna träder i kraft efter att du har överfört den uppdaterade YAML-filen till miljön.

## Relaterad dokumentation

* [Programkonfiguration: hookar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/hooks-property.html) i vår Adobe Commerce on Cloud Infrastructure Guide.
