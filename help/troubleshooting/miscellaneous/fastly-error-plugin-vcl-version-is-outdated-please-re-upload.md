---
title: '"Snabbt fel: Plugin VCL-versionen är inaktuell. Please reUpload'''
description: Den här artikeln innehåller en lösning för när du ser meddelandet "*Plugin VCL version is outdated! Ladda upp igen.*" i Snabbkonfiguration i Commerce Admin eftersom den senaste snabbmodulen inte har installerats.
exl-id: d7870e9e-ba6b-49c2-a80c-26fb464cbae3
feature: Best Practices, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Snabbt fel: Plugin VCL-versionen är inaktuell. Ladda upp igen

Den här artikeln innehåller en lösning för när meddelandet *Plugin VCL-versionen är inaktuell! Ladda upp igen.* i Snabbkonfiguration i Commerce Admin eftersom den senaste snabbmodulen inte har installerats.

## Berörda produkter och versioner

Adobe Commerce on cloud infrastructure 2.2.x., 2.3.x<br>
Snabbt: Det här felet kan påverka alla versioner av modulen Snabbt, förutom den senaste. Information om den senaste versionen finns i [Snabbsläppningsinformation](https://github.com/fastly/fastly-magento2/releases) på GitHub.

## Problem

1. Logga in på Commerce Admin-panelen.
1. Navigera till **Lager** > **Konfiguration** > **Avancerat** > **System** > **Helsidescache**   **Cachelagra snabbt.**
1. I avsnittet **Automatisk överföring och aktivering av tjänster** kommer det att finnas en VCL-version för plugin-programmet *som är inaktuell. Ladda upp igen.*-meddelande.
1. Du försöker överföra VCL-kodfragment genom att klicka på knappen &quot;Överför VCL till Snabbt&quot;, men du ser fortfarande varningen *Plugin VCL version är inaktuell! Ladda upp igen.*&quot;

## Orsak

Tillägget Snabbt uppdaterades (tillsammans med en paketerad VCL-konfiguration och mallar), men den uppdaterade VCL-konfigurationen har inte överförts till tjänsten Snabbt. När du uppdaterar Adobe Commerce-modulen `Fastly_Cdn` måste du överföra en uppdaterad VCL-konfiguration till Snabbt igen.

## Lösning

1. Kontrollera att du har de senaste ECE-verktygen installerade och i den [aktuella versionen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html) i utvecklardokumentationen. ECE-Tools har en version av snabbpaketet i sina beroenden.

   Detta är kanske inte den senaste versionen av Fastly-pluginen, men det är sannolikt en senare version än den som du har installerat och det är bäst att ha den senaste ECE-verktygen installerad.

1. Om du inte har tillgång till den aktuella versionen av ECE-verktygen följer du de här stegen för att [uppgradera](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) i vår utvecklardokumentation.
1. När du har uppgraderat ECE-Tools bör du kontrollera om du nu har en aktuell version av [Fastly plugin](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets) installerad.
1. Om Fastly-plugin-programmet inte är den aktuella versionen följer du de här stegen för att [uppgradera plugin-programmet till den senaste versionen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upgrade-the-fastly-module) i utvecklardokumentationen.

## Relaterad läsning

* Mer information om hur du konfigurerar och konfigurerar snabbt finns i [Konfigurera snabbtjänster](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html) i utvecklardokumentationen.
* Allmän information om Fastly finns på [fastly.com](https://www.fastly.com/).
