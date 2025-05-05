---
title: Ändra administratörs-URL på Adobe Commerce i molninfrastruktur
description: Som standard är URL:en för [Commerce Admin](https://experienceleague.adobe.com/en/docs/commerce-admin/start/admin/admin) inställd på *&lt;domain_name&gt;/admin*. I den här artikeln visas hur du ändrar URL-adressen.
exl-id: 6236370c-e0a2-45a6-a38f-12e219c540af
feature: Admin Workspace, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Ändra administratörs-URL på Adobe Commerce i molninfrastruktur

Som standard är URL:en för [Commerce Admin](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html) inställd på *&lt;domän\_namn>/admin*. I den här artikeln visas hur du ändrar URL-adressen.

## Metod 1: Ändra med Admin

Läs stegen: [Använda en anpassad administratörs-URL > Ändra från Admin](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url) i vår användarhandbok.

## Metod 2: Lägg till miljövariabel ADMIN\_URL

### Integreringsmiljö

Lägg till en ny variabel med [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html):

**Namn:** ADMIN\_URL **Värde:** ny Admin-URL

* Mer information finns i [Lägg till miljövariabler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-environment) i utvecklardokumentationen.
* Se även [miljövariabler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html) i utvecklardokumentationen.

### När mellanlagring och produktion inte är tillgängliga i molnkonsolen

[Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) som begär att få lägga till ADMIN\_URL-variabeln för din mellanlagrings- eller produktionsmiljö.

Om du kan nå Förproduktion och Förproduktion från molnkonsolen lägger du till miljövariabeln enligt beskrivningen i avsnittet *Integreringsmiljö* ovan.

### Lägga till variabler med Cloud CLI

Du kan lägga till variabeln ADMIN\_URL med följande Cloud CLI-kommando (för huvudversionen):

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

Mer detaljerade anvisningar finns i [Ändra Admin-URL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=en#change-the-admin-url) i avsnittet om adminvariabler i Commerce om Cloud-infrastrukturguiden.

Tänk på att om du använder molnbaserad CLI för att ändra variabeln ADMIN\_URL utlöses en omdistribution av miljön. Variabler är ärvbara som standard. Om du vill förhindra arv använder du kommandoalternativen för CLI i molnet för att ange att du inte vill att variabelvärdet ska ärvas av underordnade miljöer. Se avsnittet [Synlighet](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) i Variabelnivåer i Commerce i molninfrastrukturguiden.
