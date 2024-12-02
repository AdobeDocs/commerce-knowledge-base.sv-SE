---
title: Fel vid rensning av cache i Commerce Admin
description: 'I den här artikeln beskrivs hur du identifierar orsaken till ett felmeddelande som inträffar när cacheminnet rensas i Commerce Admin. När du försöker rensa cacheminnet via administratören får du följande meddelande:'
exl-id: aa414e04-bc6d-46bd-b98f-0446b97bda14
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Fel vid rensning av cache i Commerce Admin

I den här artikeln beskrivs hur du identifierar orsaken till ett felmeddelande som inträffar när cacheminnet rensas i Commerce Admin. När du försöker rensa cacheminnet via administratören får du följande meddelande:
Det går inte att ta bort filen */app/project-id/pub/media/catalog/product/cache/directory/filename. Varning!unlink(/app/projekt-id/pub/media/catalog/product/cache/directory/filename): Ingen sådan fil eller katalog*

## Berörda produkter och versioner

Adobe Commerce (alla distributionsmetoder) 2.3.0-2.3.7, 2.4.0-2.4.2-p1

## Problem

När du försöker rensa cacheminnet via administratören får du ett felmeddelande.

<u>Steg att återskapa:</u>

1. Gå till **System** > **Verktyg** > **Cachehantering** i Admin.
1. Välj något av alternativen för rensad cachelagring.

<u>Förväntat resultat:</u>

Adobe Commerce-cachen rensades utan fel.

<u>Faktiskt resultat:</u>

Felet&quot;filen kan inte tas bort&quot; visas.

## Orsak

Felet beror på en fördröjning mellan den tidpunkt då cacherengöringen initierades och den tidpunkt då den rapporterades som slutförd.

## Lösning

1. Bekräfta att filerna som anges i felet inte finns på servern (kontrollera att rensningen av cachen lyckades):

```bash
ls -la pub/media/catalog/product/cache/directory/filename
```

Om följande utdata visas:

```bash
ls: cannot access 'pub/media/catalog/product/cache/directory/filename/': No such file or directory
```

ett försök gjordes att rensa filerna när åtgärden redan hade slutförts. Det här är inte något fel. Det är ett problem med samtidighet för meddelanden som förväntas inträffa ibland. Det finns inget problem att felsöka.
Om utdata visar att filerna fortfarande finns i cachen måste du [skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Relaterad läsning

* [Cachehantering](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) i utvecklardokumentationen.
