---
title: Checklista för att konfigurera en ny  [!DNL domain]
description: Det här är en checklista över hur du konfigurerar en ny  [!DNL domain]  i Adobe Commerce för molninfrastruktur.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 79195c457bae31f97c2d47e53e2ff84534697d13
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---

# Checklista för att konfigurera en ny [!DNL domain]

Den här checklistan förklarar hur du konfigurerar en ny [!DNL domain] i Adobe Commerce för molninfrastruktur. Det gäller oavsett om du lägger till en ny domän eller ersätter den aktuella domänen. Det gäller också efter hämtning av en ny mellanlagringsmiljö (se steg 4).

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
>För PRO-arkitektur måste en supportförfrågan skickas till Adobe Commerce om du lägger till en ny domän. Även om vissa kunder kan konfigurera Fast manuellt via Admin Console gäller detta endast i vissa fall, t.ex. när domänen inte är kopplad till någon annan tjänst eller ett annat projekt. Nginx-konfiguration krävs dock alltid och det här steget måste hanteras av Adobe. På grund av detta rekommenderar vi att du skickar in en supportanmälan och låter Adobe hantera hela domänkonfigurationsprocessen.


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

### Steg 5 - Har domänomdirigeringar konfigurerats i `magento-vars.php`?

När domänen har konfigurerats måste du [ändra variablerna](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure-store/multiple-sites#modify-variables) i filen `magento-vars.php` för att dirigera domänen till rätt webbplats-/butiks-URL.

### Steg 6 - Är [!DNL domain]-konfigurationen verifierad?

Om du har lagt till nya butiker, butiksgrupper och webbplatser i **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]** för de nya domänerna, kontrollerar du om följande avsnitt visas i `app/etc/config.php`-filen, till exempel:

```php
'scopes' => [
    'websites' => [
        'admin' => [
            'website_id' => '0',
            'code' => 'admin',
            'name' => 'Admin',
            'sort_order' => '0',
            'default_group_id' => '0',
            'is_default' => '0',
        ],
        'base' => [
            'website_id' => '1',
            'code' => 'base',
            'name' => 'Main Website',
            'sort_order' => '0',
            'default_group_id' => '1',
            'is_default' => '1',
        ],
        'site2' => [
            'website_id' => '2',
            'code' => 'site2',
            'name' => 'Second Website',
            'sort_order' => '0',
            'default_group_id' => '2',
            'is_default' => '0',
        ],
    ],
    'groups' => [
        0 => [
            'group_id' => '0',
            'website_id' => '0',
            'name' => 'Default',
            'root_category_id' => '0',
            'default_store_id' => '0',
            'code' => 'default',
        ],
        1 => [
            'group_id' => '1',
            'website_id' => '1',
            'name' => 'Main Website Store',
            'root_category_id' => '2',
            'default_store_id' => '1',
            'code' => 'main_website_store',
        ],
        2 => [
            'group_id' => '2',
            'website_id' => '2',
            'name' => 'Second Website Store',
            'root_category_id' => '2',
            'default_store_id' => '2',
            'code' => 'site2store',
        ],
    ],
    'stores' => [
        'admin' => [
            'store_id' => '0',
            'code' => 'admin',
            'website_id' => '0',
            'group_id' => '0',
            'name' => 'Admin',
            'sort_order' => '0',
            'is_active' => '1',
        ],
        'default' => [
            'store_id' => '1',
            'code' => 'default',
            'website_id' => '1',
            'group_id' => '1',
            'name' => 'Default Store View',
            'sort_order' => '0',
            'is_active' => '1',
        ],
        'site2sv' => [
            'store_id' => '2',
            'code' => 'site2sv',
            'website_id' => '2',
            'group_id' => '2',
            'name' => 'Second Website Store view',
            'sort_order' => '0',
            'is_active' => '1',
        ],
    ],
]
```

Det innebär att du har konfigurerat [SCD för Build](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/deploy/static-content#setting-the-scd-on-build) genom att köra kommandot `config:dump` i paketet `ece-tools` tidigare.

Om du upptäcker att den nya butiken/webbplatsen som du har skapat inte visas i filen `app/etc/config.php` måste du köra kommandot igen för att synkronisera filen `config.php` med ändringarna i databasen, sedan implementera filen `config.php` och sedan distribuera den igen. Detta gör det lättare att distribuera statiskt innehåll för den nya butiken/webbplatsen/webbplatserna till rätt filsökvägar.

## Relaterad läsning

* [Konfigurera flera webbplatser eller butiker: Lägg till ny [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) i användarhandboken.
* [Webbplatsen är inte tillgänglig på grund av ursprungsinsvepning](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26856)
