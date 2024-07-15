---
title: Adobe Commerce Support Knowledge Base börjar ta emot bidrag
description: Från och med den 15 juni kan Adobe Commerce Support Knowledge Base-teamet börja acceptera direktredigeringar och nya artikelbidrag från externa Adobe Commerce-användare via [magento/knowledge-base](https://github.com/magento/knowledge-base) GitHub repo!
exl-id: b5198de0-d6b5-4107-8b74-a12606583596
feature: Support
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# Adobe Commerce Support Knowledge Base börjar ta emot bidrag

Från och med den 15 juni kan Adobe Commerce Support Knowledge Base-teamet börja acceptera direktredigeringar och nya artikelbidrag från externa Adobe Commerce-användare via GitHub-repo:n [magento/knowledge-base](https://github.com/magento/knowledge-base)!

Har du märkt ett stavfel i någon av våra artiklar eller ofullständiga felsökningssteg?
Nu kan du åtgärda det själv och få poäng!

## Contribute

Vi välkomnar alla typer av bidrag, från smärre typkorrigeringar till fullständiga felsökningsartiklar. Genom att bidra till den här rapporten får du belöningspoäng, ungefär som när du bidrar till Adobe Commerce-koden och vår dokumentation för utvecklare. Mer information finns i [belöningspoäng för bidrag](https://github.com/magento/knowledge-base/blob/main/docs/contribution-points.md).

### Allmänt bidragsflöde

1. Glöm den här rapporten.
1. Redigera på föråldrad repo.
1. Skicka en Pull Request (PR) till den här rapporten.
1. Testerna körs:
   * Adobe CLA - Kontrollera att Adobe Open Source Contributor License Agreement är signerat.
   * Markdown Linting test - kontrollera att markeringssyntaxen är korrekt.
   * Valideringstest av filstruktur - kontrollera att implementeringen är klar enligt den [obligatoriska filstrukturen](https://github.com/magento/knowledge-base/blob/main/.github/CONTRIBUTING.md#file_structure).
1. Flöde för PR-godkännanden:
   1. KB-skribenterna (Support Knowledge Base) granskar PR inom flera dagars tidsram och lägger till etiketter.
   1. KB-skrivaren kan godkänna/neka/begära ändringar.
   1. Om KB:s skribent godkänner det läggs etiketter till som motsvarar den nivå på input som lämnats i PR och den interna ämnesexperten (SME) granskar PR.
   1. SMF kan godkänna/neka/begära ändringar.
1. När alla korrigeringar har gjorts (om en sådan har begärts), och både KB-författaren och SMF godkänner PR, importerar KB-författaren innehåll till den interna rapporten och sammanfogar det internt.
1. Repo [magento/knowledge-base](https://github.com/magento/knowledge-base) synkroniseras med den interna på 20 minuter.
1. När rapporterna har synkroniserats stängs din PR och du får [bidragspunkter](#contribution-points).

Mer information om bidragsflöde finns i [Contributor&#39;s Guide](https://github.com/magento/knowledge-base/blob/main/.github/CONTRIBUTING.md).
Mer information om mallar, formatguider och formateringsriktlinjer finns i [Dokumentation](https://github.com/magento/knowledge-base/tree/main/docs).

### Hitta KB-artikelfilen för support på Github

I KB (Support Knowledge Base) ordnas artiklarna i sektioner som kapslas under kategorier.

Artikeln [Så här prenumererar du på statusuppdateringar för Adobe Magento](/help/how-to/general/how-to-subscribe-to-adobe-magento-status-updates.md) hör till avsnittet Allmänt i kategorin Använda.

Du kan se avsnittet och kategorinamnet i sökvägen för textstycken på artikelsidan. Se bilden nedan:

![kategorivägbeskrivningar och avsnittsvägbeskrivningar](assets/breadcrumbs.png)

Artikelfiler ordnas på samma sätt i [magento/knowledge-base](https://github.com/magento/knowledge-base) -repo.
Allt innehåll lagras i mappen `src`, med mappar för kategorier och kapslade mappar för avsnitt. Filnamnen sammanfaller antingen med artikelrubriker eller är liknande.

Du kan också använda sökningen i rapporten med hjälp av text från KB-artikeln Support som söksträng. När sökningen returnerar filer som innehåller den här strängen måste du välja den fil som tillhör rätt avsnitt och kategori.

### Bidrag

Repo [magento/knowledge-base](https://github.com/magento/knowledge-base) är integrerad med Magento Community Engineering för bidragspunkter och support.

Se dokumentet [Contribute Points](https://github.com/magento/knowledge-base/blob/main/docs/contribution-points.md) för att se hur poäng belönas.
