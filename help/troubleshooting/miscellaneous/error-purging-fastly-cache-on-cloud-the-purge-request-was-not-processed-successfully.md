---
title: Fel vid rensning av snabbcache i molnet (rensningsbegäran bearbetades inte korrekt)
description: 'I den här artikeln finns en korrigering för när du använder ett snabbtömningsalternativ och du får felmeddelandet: *Begäran om tömning har inte bearbetats korrekt*. Fast är en CDN och cachningstjänst som ingår i Adobe Commerce om molninfrastrukturplaner och implementeringar. Om du försöker använda alternativet Rensa snabbt, och det inte fungerar, kan du ha felaktiga Fastly-autentiseringsuppgifter i miljön eller så kan ett fel ha uppstått."'
exl-id: 568b1f4c-2ccb-4740-a6e4-d227a55fcfe6
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Fel vid rensning av snabbcache i molnet (rensningsbegäran bearbetades inte korrekt)

Den här artikeln innehåller en korrigering för när du använder ett snabbtömningsalternativ och du får felmeddelandet: *Begäran om tömning kunde inte bearbetas*. Fast är en CDN och cachningstjänst som ingår i Adobe Commerce om molninfrastrukturplaner och implementeringar. Om du försöker använda ett alternativ för att ta bort snabbt, och det inte fungerar, kan du ha felaktiga autentiseringsuppgifter för snabbt i din miljö eller så har du råkat ut för ett problem.

Den här informationen hjälper dig att verifiera och testa snabbmeddelandehuvuden för dina aktiva webbplats- och ursprungsservrar.

## Berörda versioner

* Adobe Commerce om molninfrastruktur 2.1.X och senare
* Snabbt 1.2.27 och senare

## Problem

Cachelagring fungerar, men när du försöker tömma får du ett fel eller så fungerar den inte. Felet innehåller:&quot;Begäran om rensning kunde inte bearbetas.&quot;

## Orsak

Du kan ha angett felaktiga autentiseringsuppgifter i miljön eller behöver överföra VCL-fragment.

## Lös

### Kontrollera autentiseringsuppgifter snabbt

Kontrollera om du har rätt snabb service-ID och API-token i din miljö. Om du har inloggningsuppgifter för mellanlagring i Produktion kanske rensningarna inte bearbetas eller bearbetas felaktigt.

1. Logga in som administratör hos din lokala Commerce-administratör.
1. Klicka på **Lagrar** > Inställningar > **Konfiguration** > **Avancerat** > **System** och expandera **Helsidescache**.    ![magento_full_page_cache_2.4.1.png](assets/magento_full_page_cache_2.4.1.png)
1. Expandera Snabb konfiguration och verifiera snabb service-ID och API-token för din miljö.
1. Om du ändrar värdena klickar du på Testa autentiseringsuppgifter.

### Kontrollera VCL-fragment

Om autentiseringsuppgifterna är korrekta kan du ha problem med dina VCL:er. Om du vill visa och granska dina VCL-listor per tjänst anger du följande API-anrop i en terminal:

```
curl -X GET -s https://api.fastly.com/service/<Service ID>/version/<Editable Version #>/snippet -H "Fastly-Key:FASTLY_API_TOKEN"
```

Granska listan över VCL:er. Om du har problem med standard-VCL:er från Fastly kan du överföra igen eller verifiera innehållet enligt [Snabbt standard-VCL:er](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets). Mer information om hur du redigerar anpassade VCL-listor finns i [Anpassade snabbVCL-fragment](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) i Commerce on Cloud Infrastructure Guide.

## Mer information

I vår utvecklardokumentation:

* [Om snabbt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [Konfigurera snabbt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)
* [Anpassade VCL-kodfragment snabbt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)
