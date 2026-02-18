---
title: Ändra administratörs-URL på Adobe Commerce i molninfrastruktur
description: Som standard är URL:en för [Commerce Admin](https://experienceleague.adobe.com/sv/docs/commerce-admin/start/admin/admin) inställd på *&lt;domain_name&gt;/admin*. I den här artikeln visas hur du ändrar URL-adressen.
exl-id: 6236370c-e0a2-45a6-a38f-12e219c540af
feature: Admin Workspace, Cloud
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Ändra administratörs-URL på Adobe Commerce i molninfrastruktur

Som standard är URL:en för [Commerce Admin](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html?lang=sv-SE) inställd på *&lt;domän\_namn>/admin*. I den här artikeln visas hur du ändrar URL-adressen.

## Metod 1: Ändra med Admin

Läs stegen: [Använda en anpassad administratörs-URL > Ändra från Admin](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html?lang=sv-SE#use-a-custom-admin-url) i vår användarhandbok.

## Metod 2: Lägg till miljövariabel ADMIN\_URL

### Integreringsmiljö

Lägg till en ny variabel med [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=sv-SE):

**Namn:** ADMIN\_URL **Värde:** ny Admin-URL

* Mer information finns i [Lägg till miljövariabler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=sv-SE#configure-environment) i utvecklardokumentationen.
* Se även [miljövariabler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=sv-SE) i utvecklardokumentationen.

### När mellanlagring och produktion inte är tillgängliga i molnkonsolen

[Skicka en supportanmälan](https://experienceleague.adobe.com/sv/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) som begär att få lägga till ADMIN\_URL-variabeln för din mellanlagrings- eller produktionsmiljö.

Om du kan nå Förproduktion och Förproduktion från molnkonsolen lägger du till miljövariabeln enligt beskrivningen i avsnittet *Integreringsmiljö* ovan.

### Lägga till variabler med Cloud CLI

Du kan lägga till variabeln ADMIN\_URL med följande Cloud CLI-kommando (för huvudversionen):

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

Mer detaljerade anvisningar finns i [Ändra Admin-URL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=sv-SE#change-the-admin-url) i avsnittet om adminvariabler i Commerce om Cloud-infrastrukturguiden.

Tänk på att om du använder molnbaserad CLI för att ändra variabeln ADMIN\_URL utlöses en omdistribution av miljön. Variabler är ärvbara som standard. Om du vill förhindra arv använder du kommandoalternativen för CLI i molnet för att ange att du inte vill att variabelvärdet ska ärvas av underordnade miljöer. Se avsnittet [Synlighet](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html?lang=sv-SE#visibility) i Variabelnivåer i Commerce i molninfrastrukturguiden.
