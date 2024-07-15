---
title: Ändra administratörslösenord för Adobe Commerce i molninfrastruktur
description: '![login_panel_s.png](assets/login_panel_s.png)'
exl-id: 1b6e867e-d314-4e7b-be95-d699e6749896
feature: Admin Workspace, Cloud
source-git-commit: 7dc84525aef4d59346bb9bc980a7ed9b7f6612cf
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---

# Ändra administratörslösenord för Adobe Commerce i molninfrastruktur

## Metod 1: Har glömt lösenordet (återställs via e-post)

![login_panel_s.png](assets/login_panel_s.png)

Läs stegen i avsnittet [Återställ ditt lösenord i Admin Sign In](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin-signin.html#admin-sign-in) i användarhandboken.

Nedan finns viktig användningsinformation.

### Aktivera utgående e-post

Innan du använder formuläret **Har du glömt ditt lösenord** måste du [aktivera utgående e-post](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/outgoing-emails.html) med [molnkonsolen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).

### Kontrollera skräppostmappen

Om du inte kan hitta meddelandet med länken Återställ lösenord kontrollerar du mappen *Skräppost*. Namnet på e-postmeddelandet är *Bekräftelse av återställning av lösenord för administratörens användarnamn*.

## Metod 2: Lägg till en ny administratörsanvändare

Om du inte kan återställa lösenordet för den befintliga användaren kan du skapa en ny Admin-användare och ange ett lösenord för den här användaren. Gör så här:

1. Använd [SSH för att logga in i fjärrmiljön](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Kör följande kommando: `bin/magento admin:user:create   --admin-user=%user_name% --admin-password=%your_password% --admin-email=%your_email% --admin-firstname=%admin_user_first_name% --admin-lastname=%admin_user_last_name%`
