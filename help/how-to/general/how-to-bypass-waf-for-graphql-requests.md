---
title: Åsidosätta WAF för GraphQL-förfrågningar
description: I den här artikeln beskrivs hur du åsidosätter WAF för GraphQL-begäranden.
feature: GraphQL
exl-id: 3a0f2c22-f976-4596-b6a9-4634be1ea4c3
source-git-commit: 2bec86818336a9ef4d8316e257a0ca4256cdd93c
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Åsidosätta WAF för GraphQL-förfrågningar

I den här artikeln beskrivs hur du åsidosätter WAF för GraphQL-begäranden när [!DNL Fastly]-WAF blockerar dina GraphQL-begäranden.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur (alla versioner)

## Orsak

På grund av GraphQL-begärandenas inneboende natur kan det finnas många upprepade tecken som kan utlösa en falsk positiv blockering av förfrågningar från [!DNL Fastly]-SWF:en.

## Lösning

1. Åsidosätt WAF för dessa förfrågningar genom att lägga till ett anpassat fragment via modulen [!DNL Fastly] Magento:

   typ: recv
prioritet: 15
innehåll:

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. Klicka på **[!UICONTROL Upload VCL to Fastly]**.

## Relaterad läsning

* [Brandvägg för webbaserade program (WAF)](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) i guiden för Commerce om molninfrastruktur.
* [Komma igång med anpassad VCL](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) i guiden för molninfrastruktur i Commerce.
