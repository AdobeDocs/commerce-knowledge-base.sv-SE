---
title: Checklista för att konfigurera en ny [!DNL domain]
description: Det här är en checklista över hur du konfigurerar en ny [!DNL domain] i Adobe Commerce om molninfrastruktur.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: cc3dc1e3f9c8f98370ce5db125b402d4c1dfbd6f
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---

# Checklista för att konfigurera en ny [!DNL domain]

Det här är en checklista över hur du konfigurerar en ny [!DNL domain] i Adobe Commerce om molninfrastruktur. Det gäller oavsett om du försöker lägga till en ny domän eller ersätta den aktuella domänen med en ny.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur, [alla versioner som stöds](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Konfigurera en ny domän

### Steg 1 - Är detta för [!DNL Integration, Staging], eller [!DNL Production environment]?

* **[!DNL Integration]**: [!DNL Custom domains] stöds inte. Du måste använda den här metoden i stället: [Konfigurera flera webbplatser eller butiker: Konfigurera lokal installation](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) i vår användarhandbok.
* **[!DNL Staging]**: Gå till **Steg 2**.
* **[!DNL Production]**: Gå till **Steg 3**.

### Steg 2 - [!DNL Staging environment]: är du på [!DNL Pro] eller [!DNL Starter]?

* **[!DNL Pro]**: **Skicka en begäran** för att lägga till domänen i [!DNL Fastly, Nginx]och konfigurera [!DNL SSL certificate] (samt [!DNL Sendgrid domain], om det behövs). När detta har konfigurerats [uppdatera [!DNL DNS] konfiguration med [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>Du kan lägga till den nya [!DNL domain] till [!DNL Fastly] genom att uppdatera konfigurationen i [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** som i [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) i vår användarhandbok.

* **[!DNL Starter]**: [!DNL Custom domains] stöds inte.

### Steg 3 - [!DNL Production environment]: är du på [!DNL Pro] eller [!DNL Starter]?

* **[!DNL Pro]**: **Skicka en begäran** för att lägga till domänen i [!DNL Fastly, Nginx]och konfigurera [!DNL SSL certificate] (som [!DNL Sendgrid domain], om det behövs). När det har konfigurerats fortsätter du med att **Steg 4**.

>[!NOTE]
>
>Du kan lägga till den nya [!DNL domain] till [!DNL Fastly] genom att uppdatera konfigurationen i [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) i vår användarhandbok.

* **[!DNL Starter]**: Lägg till [!DNL domain] till ditt projekt i **[!DNL Domains]** tabbtangenten, sedan **skicka en förfrågan** att tillhandahålla **[!DNL ACME Challenge Key]** för [!DNL SSL certificate].

### Steg 4 - är [!DNL domain] live?

* **JA**: [Uppdatera [!DNL DNS] konfiguration med [!UICONTROL production] inställningar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings).
* **NEJ**: [Uppdatera [!DNL DNS] konfiguration med [!UICONTROL development] inställningar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

## Relaterad läsning

* [Konfigurera flera webbplatser eller butiker: Lägg till ny [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) i vår användarhandbok.
