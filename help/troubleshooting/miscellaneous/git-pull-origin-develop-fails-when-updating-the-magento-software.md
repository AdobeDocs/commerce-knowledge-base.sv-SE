---
title: Git pull origin-utveckling misslyckas vid uppdatering av Adobe Commerce
description: I den här artikeln finns en fix som anger när du inte kan uppdatera Adobe Commerce när du kör "git pull origin develop develop".
exl-id: b133253e-c160-4f15-a9b0-8591e93a1e9b
feature: Upgrade
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Git pull origin-utveckling misslyckas vid uppdatering av Adobe Commerce

I den här artikeln finns en fix som anger när du inte kan uppdatera Adobe Commerce-program när du kör `git pull origin develop`.

## Information

Ett av stegen i uppdateringen av Adobe Commerce är att uppdatera din lokala lagringsplats genom att köra:

```bash
$ git pull origin develop
```

Följande fel kan visas:

```terminal
error: Your local changes to the following files would be overwritten by merge:
<list of files>
```

Om du vill ta reda på vilka filer som kan skrivas över läser du antingen meddelandet eller anger:

```bash
git status
```

I nästa avsnitt diskuteras föreslagna lösningar.

### Föreslagna lösningar

Din lösning beror på om du avsiktligt har ändrat filer i Adobe Commerce filsystem eller inte. Mer information finns i ett av följande avsnitt.

#### Du har avsiktligt ändrat filer

Lös konflikterna manuellt på det vanliga sättet. Om du är osäker på vad du ska göra kan du kontakta [Hjälp om GitHub](https://help.github.com/).

#### Du har inte avsiktligt ändrat några filer

Gör något av följande:

* Om du är säker på att du inte har ändrat några filer och du inte har något emot att ta bort eller skriva över ändringarna i filsystemet i Adobe Commerce anger du:

  </p>
    <pre><code class="language-bash">$ git reset --hard HEAD && git pull origin develop</code></pre>

  Därefter fortsätter du där du slutade med Adobe Commerce-uppdateringen.

* Det är möjligt att en GitHub-konfigurationsinställning kan förhindra dessa fel i framtiden. Som standard lagrar GitHub innehåll med operativsystemets standardradslutstecken. Om du använder Linux, men en annan medarbetare har implementerat en ändring med Windows, konverterar GitHub Windows-radsluten till Linux när du klonar eller drar. Detta ger intryck av att filerna ändras när de faktiskt inte har ändrats.

  Om du vill konfigurera GitHub så att radslut ignoreras anger du följande kommando i Git-klienten:

  </p>
    <pre><code class="language-bash">$ git config --system core.autocrlf false</code></pre>

  Om du använder Windows anger du:

  </p>
    <pre><code class="language-bash">$ git config --system core.eol LF</code></pre>

  >[!NOTE]
  >
  >Adobe rekommenderar eller stöder inte några särskilda GitHub-konfigurationsinställningar. Föregående är endast förslag. Mer information finns i [Hjälp om GitHub](https://help.github.com/).

  Fortsätt där du slutade med Adobe Commerce-uppdateringen.
