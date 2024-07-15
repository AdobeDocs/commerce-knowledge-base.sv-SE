---
title: Composer-plugin mot attacker med beroendekonfusion
description: I den här artikeln finns information om det insticksprogram som släpps för attacker med beroendekonfusion och rekommendationer om hur du undviker felet. Composer-plugin introducerades tillsammans med Adobe Commerce 2.4.3 för att skydda Adobe Commerce handlare från attacker med beroendekonfusion.
exl-id: 42543043-cf60-4431-80e9-866771c5c87b
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# Composer-plugin mot attacker med beroendekonfusion

I den här artikeln finns information om det insticksprogram som släpps för attacker med beroendekonfusion och rekommendationer om hur du undviker felet. Composer-plugin introducerades tillsammans med Adobe Commerce 2.4.3 för att skydda Adobe Commerce handlare från attacker med beroendekonfusion.

## Berörda produkter och versioner

* Adobe Commerce 2.4.3 och framtida versioner (alla distributionsmetoder)

## Problem

Ett möjligt fall av en aktiv beroendekonfusion upptäcks genom minst ett av de direkta eller indirekta beroenden som definieras i `composer.json` av dispositionsplugin-programmet `magento/composer-dependency-version-audit-plugin` under installationen/uppdateringen av dispositionen.

<u>Steg som ska återskapas</u>:

När du installerar/uppdaterar en disposition avbryts insticksprogrammet för disposition om det upptäcker en potentiell beroendekonfusion. I så fall misslyckas installationen/uppdateringen av disposition med ett felmeddelande som liknar:

*```Higher matching version x.x.x of package/name was found in public repository packagist.org than x.x.x in private.repo. Public package might've been taken over by a malicious entity; please investigate and update package requirement to match the version from the private repository.```*

## Orsak

Anfall av beroendekonfusion gör att du kan fjärrköra godtycklig kod på en server genom att trigga en beroendehanterare (till exempel PHP:s Composer) med att hämta ett skadligt paket från en offentlig källa i stället för det ursprungliga paketet från en privat databas.

En sådan attack kan till och med bli oidentifierad om en angripare kan upprätthålla originalpaketets funktionalitet.

Angriparna kan utnyttja säkerhetsluckan om ett paket bara är tillgängligt via privata databaser, men inte är registrerat i den offentliga. Angriparen överför sedan ett paket med samma namn till den offentliga databasen och ger det en senare version än den som är tillgänglig privat. Beroendehanteraren jämför sedan versioner av både privat och offentligt tillgängliga paket och väljer den högsta versionen från den offentliga databasen. Den skadliga kod som hämtas av beroendehanteraren körs sedan med samma behörighet som programmets kod.

## Lösning

### Recommendations till handlare

* Ta felmeddelandet som visas när plugin-programmet stoppar installationen/uppdateringen av kompositören på allvar och kontakta tilläggsutvecklaren om du känner igen det potentiellt komprometterade paketet.
* Du kan fortfarande installera Adobe Commerce med den säkra versionen av paketet från Marketplace eller någon annan betrodd privat databas.
* Ändra den nödvändiga paketversionen i din Composer.json till exakt den version som finns på Marketplace för att fortsätta med installationen/uppdateringen av dispositionen.

### Förväntningar från tilläggsutvecklare

* Det finns inget sätt att veta om ett plugin-program, om det kommer från en offentlig repo, har komprometterats eller inte. Plugin-programmet identifierar när en offentlig version av ett paket på packagist.org har en senare version än den som finns i ett privat svar som [repo.magento.com](https://repo.magento.com). Vi rekommenderar att utvecklare av tillägg undviker sådana situationer och inte publicerar nyare versioner offentligt än de som är tillgängliga via [repo.magento.com](https://repo.magento.com).
* Adobe Commerce inser att granskningsprocessen på Marketplace kan fördröja tillgängligheten till tillägg, men processen är till för att skydda handlarna och hjälpa utvecklare att hitta misstag de kan ha missat.
