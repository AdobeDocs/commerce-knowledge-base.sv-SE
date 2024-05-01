---
title: Ändra administratörs-URL på Adobe Commerce i molninfrastruktur
description: Som standard är URL:en för [Commerce Admin](https://docs.magento.com/m2/ee/user_guide/stores/admin.html) inställd på *&lt;domain\_name&gt;/admin*. I den här artikeln visas hur du ändrar URL-adressen.
exl-id: 6236370c-e0a2-45a6-a38f-12e219c540af
feature: Admin Workspace, Cloud
source-git-commit: 04dba4e2adeaaa7649b817444024bf96e7830ad3
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Ändra administratörs-URL på Adobe Commerce i molninfrastruktur

Som standard är [Commerce Admin](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html) URL är inställd på *&lt;domain _name=&quot;&quot;>/admin*. I den här artikeln visas hur du ändrar URL-adressen.

## Metod 1: Ändra med Admin

Läs stegen: [Använda en anpassad administratörs-URL > Ändra från administratör](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url) i vår användarhandbok.

## Metod 2: Lägg till miljövariabel ADMIN\_URL

### Integreringsmiljö

Från [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html)lägger du till en ny variabel med:

**Namn:** ADMIN\_URL **Värde:** ny Admin-URL

* Detaljerade anvisningar finns i [lägg till miljövariabler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-environment) i vår dokumentation för utvecklare.
* Se även [miljövariabler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html) i vår dokumentation för utvecklare.

### När mellanlagring och produktion inte är tillgängliga i molnkonsolen

[Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) begär att få lägga till variabeln ADMIN\_URL för mellanlagrings- eller produktionsmiljön.

Om du kan nå Förproduktion och Förproduktion från molnkonsolen lägger du till miljövariabeln enligt beskrivningen i *Integreringsmiljö* ovan.

### Lägga till variabler med Cloud CLI

Du kan lägga till variabeln ADMIN\_URL med följande Cloud CLI-kommando (för huvudversionen):

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

Detaljerade instruktioner finns i [Ändra Admin-URL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=en#change-the-admin-url) i avsnittet Administratörsvariabler i Commerce om Cloud Infrastructure Guide.

Tänk på att om du använder molnbaserad CLI för att ändra variabeln ADMIN\_URL utlöses en omdistribution av miljön. Variabler är ärvbara som standard. Om du vill förhindra arv använder du kommandoalternativen för CLI i molnet för att ange att du inte vill att variabelvärdet ska ärvas av underordnade miljöer. Se [Synlighet](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) i Variabelnivåer i Commerce om Cloud Infrastructure Guide.
