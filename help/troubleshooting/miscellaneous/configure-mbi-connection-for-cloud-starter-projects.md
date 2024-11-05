---
title: Konfigurera Adobe Commerce Intelligence-anslutning för befintliga Cloud Starter-projekt
description: Den här artikeln innehåller en lösning för när du vill konfigurera Adobe Commerce Intelligence-anslutningen för ett befintligt Cloud Starter-projekt.
feature: Commerce Intelligence
role: Developer
exl-id: 56f6ad64-729d-4e3a-93a9-da1b91bc5c1d
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 0%

---

# Konfigurera Adobe Commerce Intelligence-anslutning för befintliga Cloud Starter-projekt

>[!NOTE]
>
>Adobe Commerce Intelligence kallades tidigare Magento Business Intelligence (MBI).

Den här artikeln innehåller en lösning för när du vill konfigurera Adobe Commerce Intelligence-anslutningen för ett befintligt Cloud Starter-projekt.

## Berörda produkter och versioner

Adobe Commerce on cloud starter (alla versioner)

## Problem

Du vill konfigurera Commerce Intelligence-anslutningen för ett befintligt Cloud Starter-projekt.

>[!NOTE]
>
>Adobe har inte längre stöd för nya Creative Cloud Starter-prenumerationer, men om du har ett befintligt Starter-projekt måste du följa stegen nedan för att konfigurera anslutningen.

## Lösning

Om du vill aktivera Commerce Intelligence för Cloud Starter-projekt skapar du ett Commerce Intelligence-konto, skapar en SSH-nyckel och ansluter till din Adobe Commerce-databas.

Följ de här stegen:

1. Skapa ett Adobe Commerce Intelligence-konto:

   * Gå till [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
   * Navigera till **[!UICONTROL My Account]** > **[!UICONTROL My MBI Instances]**.
   * Klicka på **[!UICONTROL Create Instance]**. Om du inte ser den här knappen kontaktar du din Customer Success Manager eller kundens tekniska rådgivare.
   * Välj din Creative Cloud Starter-prenumeration. Om du bara har en Cloud Starter-prenumeration väljs den automatiskt.
   * Klicka på **[!UICONTROL Continue]**.
   * Ange dina uppgifter för att skapa ditt konto.

   ![Skapa MBI-konto](/help/troubleshooting/miscellaneous/assets/create_mbi_account.png)

   * Gå till din inkorg och verifiera e-postadressen.

   ![Verifiera e-postadress](/help/troubleshooting/miscellaneous/assets/verify_email_address_mbi.png)

   * Skapa ett lösenord.

   ![Skapa ett lösenord](/help/troubleshooting/miscellaneous/assets/create_password_mbi.png)

   * När du har skapat ditt konto kan du lägga till användare i ditt nya konto. Nu kan tekniska administratörer läggas till för att utföra följande steg.

   ![Lägg till användare](/help/troubleshooting/miscellaneous/assets/add_users_mbi.png)

1. Ange information om din butik för att ange dina inställningar.

   ![Lägg till butiksinformation](/help/troubleshooting/miscellaneous/assets/add_store_info_mbi.png)

   Det finns viss information som du måste samla in innan du kan ansluta databasen för det tredje steget i startflödet. Du fyller i sidan *[!UICONTROL Connect your database]* i steg 9.

1. Skapa en dedikerad Commerce Intelligence-användare.

   * Skapa en ny användare på [account.adobe.com](https://account.adobe.com/).
   * Gå till [https://accounts.magento.com/customer/account/](https://accounts.magento.com/customer/account/) för att skapa ditt Adobe Commerce-konto.
   * Varför en ny användare? Adobe Commerce Intelligence behöver en användare som läggs till i projektet för att kontinuerligt hämta nya data som ska överföras till kontots Commerce Intelligence datalager. Den här användaren fungerar som den anslutningen. Om du lägger till den här användaren i projektet kommer du till steg 4.
   * Orsaken till att du har en dedikerad Commerce Intelligence-användare är att den tillagda användaren inte oavsiktligt inaktiveras eller tas bort och att Commerce Intelligence-anslutningen avbryts.

1. Lägg till den nyskapade användaren i projektets primära miljö som *Contributor*.

   ![Lägg till användare som Contributor](/help/troubleshooting/miscellaneous/assets/contributor_user_mbi.png)

1. Hämta dina Commerce Intelligence SSH-nycklar.

   * Gå till sidan **[!UICONTROL Connect your database]** i Commerce Intelligence inställningsgränssnitt och bläddra nedåt till **[!UICONTROL Encryption settings]**.
   * Välj **[!UICONTROL SSH Tunnel]** för fältet **[!UICONTROL Encryption Type]**.
   * I listrutan kan du kopiera och klistra in den angivna offentliga nyckeln för Magento BI Essentials.

   ![Krypteringsinställningar](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

1. Lägg till din nya offentliga nyckel för Magento BI Essentials till den Commerce Intelligence-användare som skapades i steg 5.

   * Gå till [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login). Logga in med din kontoinloggningsinformation för den nya Commerce Intelligence-användare som har skapats. Gå sedan till fliken **[!UICONTROL Account Settings]**.
   * Bläddra nedåt på sidan och expandera listrutan för SSH-tangenter. Klicka sedan på **[!UICONTROL Add a public key]**.

   ![Lägg till en offentlig nyckel](/help/troubleshooting/miscellaneous/assets/add_public_key_mbi.png)

   * Lägg till den offentliga nyckeln för SSH från ovan för Magento MBI Essentials.

   ![Lägg till offentlig SSH-nyckel](/help/troubleshooting/miscellaneous/assets/add_ssh_key_mbi.png)

1. Ange autentiseringsuppgifter för Business Intelligence Essentials [!DNL MySQL].

   * Uppdatera din `.magento/services.yaml`.

   ```
   mysql:
    type: mysql:10.0
    disk: 2048
    configuration:
        schemas:
            - main
        endpoints:
            mysql:
                default_schema: main
                privileges:
                    main: admin
            mbi:
                default_schema: main
                privileges:
                    main: ro
   ```

   * Uppdatera din `.magento.app.yaml`.

   ```
   relationships:
            database: "mysql:mysql"
            mbi: "mysql:mbi"
            redis: "redis:redis"
   ```

1. Hämta information om hur du ansluter databasen till Commerce Intelligence.

   Kör `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 --decode | json_pp` om du vill ha information om hur du ansluter databasen.

   Du bör få information som liknar utdata nedan:

   ```
   "mbi" : [
              {
                 "scheme" : "mysql",
                 "rel" : "mbi",
                 "cluster" : "vfbfui4vmfez6-master-7rqtwti",
                 "query" : {
                    "is_master" : true
                 },
                 "ip" : "169.254.169.143",
                 "path" : "main",
                 "host" : "mbi.internal",
                 "hostname" : "3m7xizydbomhnulyglx2ku4wpq.mysql.service._.magentosite.cloud",
                 "username" : "mbi",
                 "service" : "mysql",
                 "port" : 3306,
                 "password" : "[password]"
              }
           ],
   ```

1. Anslut Adobe Commerce-databasen.

   ![Anslut din Adobe Commerce-databas](/help/troubleshooting/miscellaneous/assets/connect_magento_database_mbi.png)

   *Indata*:

   * Integrationsnamn: [Välj ett namn för integreringen.]
   * Värd: `mbi.internal`
   * Port: 3306
   * Användarnamn: mbi
   * Lösenord: [indatalösenord angavs i utdata från steg 8.]
   * Databasnamn: huvud
   * Tabellprefix: [lämna tomt om det inte finns några tabellprefix]

1. Ange [!UICONTROL Timezone Settings].

   ![Tidszonsinställningar](/help/troubleshooting/miscellaneous/assets/timezone_settings_mbi.png)

   *Indata*

   * Databas: Tidszon: UTC
   * Önskad tidszon: [Välj den tidszon som du vill att dina data ska visas i.]

1. Hämta information om dina krypteringsinställningar.

   * Projektgränssnittet tillhandahåller en SSH-åtkomststräng. Strängen kan användas för att samla in den information som behövs för fjärradressen och användarnamnet när du konfigurerar **[!UICONTROL Encryption settings]**. Välj **[!UICONTROL SSH]** om du vill visa ditt användarnamn och din fjärradress. Textsträngen före *@* är ditt användarnamn och textsträngen efter *@* är din fjärradress.

   ![Åtkomst till webbplatshuvud](/help/troubleshooting/miscellaneous/assets/access_site_mbi.png)

1. Indatainformation för din [!UICONTROL Encryption Settings].

   ![Krypteringsinställningar](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

   *Indata*

   * Krypteringstyp: SSH-tunnel
   * Fjärradress: ssh.us-3.magento.cloud
   * Användarnamn: vfbfui4vmfez6-master-7rqtwti—mymagento
   * Port: 22

1. Klicka på **[!UICONTROL Save Integration]**.
1. Du har nu anslutit till ditt Commerce Intelligence Essentials-konto.
1. Om du är kund hos Adobe Commerce Intelligence Pro kontaktar du din Customer Success Manager eller kundens tekniska rådgivare för att samordna nästa steg.

## Relaterad läsning

[Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook
