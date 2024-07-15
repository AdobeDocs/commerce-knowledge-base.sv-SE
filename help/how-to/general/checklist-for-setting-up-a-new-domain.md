---
title: Checklista för att konfigurera en ny  [!DNL domain]
description: Det här är en checklista över hur du konfigurerar en ny  [!DNL domain]  i Adobe Commerce för molninfrastruktur.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 625ed2c7ab79f7bca9a979903e97c44c875e607c
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Checklista för att konfigurera en ny [!DNL domain]

Det här är en checklista över hur du konfigurerar en ny [!DNL domain] i Adobe Commerce för molninfrastruktur. Det gäller oavsett om du försöker lägga till en ny domän eller ersätta den aktuella domänen med en ny.

## Berörda produkter och versioner

Adobe Commerce i molninfrastruktur, [alla versioner som stöds](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Konfigurera en ny domän

### Steg 1 - Är detta för [!DNL Integration, Staging] eller [!DNL Production environment]?

* **[!DNL Integration]**: [!DNL Custom domains] stöds inte. Du måste använda den här metoden i stället: [Konfigurera flera webbplatser eller butiker: Konfigurera lokal installation](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) i användarhandboken.
* **[!DNL Staging]**: Gå till **Steg 2**.
* **[!DNL Production]**: Gå till **Steg 3**.

### Steg 2 - [!DNL Staging environment]: är du på [!DNL Pro] eller [!DNL Starter]?

* **[!DNL Pro]**: **Skicka en begäran** om att lägga till domänen i [!DNL Fastly, Nginx] och konfigurera [!DNL SSL certificate] (samt [!DNL Sendgrid domain] om det behövs). När konfigurationen är klar [uppdaterar  [!DNL DNS] konfigurationen med  [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>Du kan lägga till den nya [!DNL domain] till [!DNL Fastly] själv genom att uppdatera konfigurationen i [!DNL Admin] i **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** som i [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) i användarhandboken.
>
>Om du inte kan lägga till domänen kan det bero på något av följande:
>
>1. Du migrerar domänen till molnmiljön, som har konfigurerats i din egen [!DNL Fastly]-tjänst. I det här fallet ska du skicka en begäran och begära delegering av domänen.
>1. Du migrerar domänen från Starter till Pro. Om så är fallet, lämna in en begäran om ytterligare hjälp.

* **[!DNL Starter]**: [!DNL Custom domains] stöds inte i mellanlagringsmiljön.

### Steg 3 - [!DNL Production environment]: Är du på [!DNL Pro] eller [!DNL Starter]?

* **[!DNL Pro]**: **Skicka en begäran** om att lägga till domänen i [!DNL Fastly, Nginx] och konfigurera [!DNL SSL certificate] (som [!DNL Sendgrid domain] om det behövs). Fortsätt till **Steg 4** när konfigurationen är klar.

>[!NOTE]
>
>Du kan lägga till den nya [!DNL domain] till [!DNL Fastly] själv genom att uppdatera konfigurationen i [!DNL Admin] i **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) i användarhandboken.
>
>
>Om du inte kan lägga till domänen kan det bero på något av följande:
>
>1. Du migrerar domänen från lokala platser till molnmiljön, som har konfigurerats i din egen [!DNL Fastly]-tjänst. I det här fallet ska du skicka en begäran och begära delegering av domänen.
>1. Du migrerar domänen från Starter till Pro. Om så är fallet, lämna in en begäran om ytterligare hjälp.

* **[!DNL Starter]**: Lägg till [!DNL domain] i ditt projekt på fliken **[!DNL Domains]** och **skicka sedan en begäran** som tillhandahåller **[!DNL ACME Challenge Key]** för [!DNL SSL certificate].

### Steg 4 - Är [!DNL domain] live?

* **JA**: [Uppdatera  [!DNL DNS] konfigurationen med [!UICONTROL production] inställningar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings).
* **NO**: [Uppdatera  [!DNL DNS] konfigurationen med [!UICONTROL development] inställningar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

## Relaterad läsning

* [Konfigurera flera webbplatser eller butiker: Lägg till ny [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) i användarhandboken.
