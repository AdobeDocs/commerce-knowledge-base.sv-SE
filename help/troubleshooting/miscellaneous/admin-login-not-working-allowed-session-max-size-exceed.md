---
title: '[!UICONTROL Admin]-inloggningen fungerar inte - den tillåtna maxstorleken för sessionen har överskridits'
description: Lös problemet när du försöker logga in på panelen [!UICONTROL Admin] och formuläret uppdateras, och du kan inte logga in.
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: fe4a48581bdfe24da5082b69fb26a8032bd77334
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# [!UICONTROL Admin]-inloggningen fungerar inte - den tillåtna maxstorleken för sessionen har överskridits

I den här artikeln finns en fix som du kan använda när du försöker logga in på panelen [!UICONTROL Admin], men formuläret uppdateras bara och du kan inte logga in, eller så utför du några åtgärder på panelen [!UICONTROL Admin] och loggas ut automatiskt.
Detta orsakas av att [!UICONTROL Admin] [!UICONTROL Session Size] har överskridits.

## Berörda versioner

* Adobe Commerce lokalt, [alla versioner som stöds](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce i molninfrastruktur, [alla versioner som stöds](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problem

Du upplever något av följande symtom på [!UICONTROL Admin]:

1. Det går inte att logga in på [!UICONTROL Admin] eftersom formuläret läses in igen.
1. Du loggas ut automatiskt när du försöker utföra en åtgärd.

## Orsak

Högsta tillåtna sessionsstorlek har överskridits.

## Lösning

Kontrollera om det finns fel i filen `var/log/support_report.log`:

*[2023-07-13T04:26:09.792060+00:00] rapport.VARNING! Sessionsstorleken 260572 överskrider den tillåtna sessionsstorleken på 256000. [] []
[2023-07-13T04:26:17.056714+00:00] report.VARNING! Sessionsstorleken 260570 överskrider den tillåtna sessionsstorleken på 256000. [][]*

Om du ser dessa fel är lösningen:

<u>Adobe Commerce lokalt</u>:
1. Öka värdet **[!UICONTROL Max Session Size in Admin]** från serverdelskonfigurationen. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Security]** > **[!UICONTROL Max Session Size in Admin]** om du vill göra det.
1. Ange värdet till *500000* eller högre. Beroende på den befintliga maxstorleken som rapporteras i felet kan du också ange värdet till *0*, vilket tar bort sessionsstorleksgränsen.

<u>Adobe Commerce i molninfrastruktur</u>:

(Den här inställningen är bara tillgänglig i [!UICONTROL Admin] när distributions-/åtgärdsläget är *standard* eller *utvecklare*. I molnmiljön är dock endast Production-distributionsläget tillåtet.)

Om du vill öka det här värdet kör du det här kommandot i terminalen (SSH):

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

Du kan ange högre än *50000* beroende på den befintliga maxstorleken som rapporteras i felet och du kan också ange värdet till *0* för att ta bort sessionsstorleksgränsen.

## Relaterad läsning

* [Sessionsstorlek](https://experienceleague.adobe.com/sv/docs/commerce-admin/systems/security/security-session-management#admin-sessions) i handboken för administratörssystem
* [Åtgärdsläge](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/cli/set-mode) i konfigurationshandboken
* [Säkra anslutningar](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/secure-connections) i Commerce on Cloud Infrastructure Guide
