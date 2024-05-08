---
title: Åsidosätta WAF för GraphQL-förfrågningar
description: I den här artikeln beskrivs hur du åsidosätter WAF för GraphQL-begäranden.
feature: GraphQL
source-git-commit: c35d4ba82fbe1657756e160a73fd575c736b4e1c
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Åsidosätta WAF för GraphQL-förfrågningar

I den här artikeln beskrivs hur du åsidosätter WAF för GraphQL-begäranden när [!DNL Fastly] WAF blockerar dina GraphQL-förfrågningar.

## Berörda produkter och versioner

Adobe Commerce om molninfrastruktur (alla versioner)

## Orsak

På grund av inbyggt i GraphQL-begäranden kan det finnas många upprepade tecken som kan utlösa en falsk positiv blockering av förfrågningar från [!DNL Fastly] WAF.

## Lösning

1. Åsidosätt WAF för dessa förfrågningar genom att lägga till ett anpassat fragment via [!DNL Fastly] Modulen Magento:

   typ: recv-prioritet: 15 innehåll:

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. Klicka på **[!UICONTROL Upload VCL to Fastly]**.

## Relaterad läsning

* [Brandvägg för webbaserade program (WAF)](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) i Commerce om Cloud Infrastructure Guide.
* [Komma igång med anpassad VCL](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) i Commerce om Cloud Infrastructure Guide.

