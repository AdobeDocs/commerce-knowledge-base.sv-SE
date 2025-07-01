---
title: 'cURL-fel 60: SSL-certifikatet har upphört att gälla'
description: 'I den här artikeln visas hur du kontrollerar när en gren senast distribuerades efter att ha fått ett cURL-fel 60: SSL-certifikatet har upphört att gälla i huvud- eller integreringsgrenarna på Adobe Commerce i molninfrastrukturen.'
exl-id: 74f1db7e-ee2b-4e27-8fcc-fe462a9e72c3
feature: Configuration
role: Developer
source-git-commit: dcaae51408534b82181b268f60905b123e240900
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# cURL-fel 60: SSL-certifikatet har upphört att gälla

I den här artikeln visas hur du kontrollerar när en gren senast distribuerades efter att en `cURL error 60`: [!DNL SSL certificate] har gått ut i grenarna [!DNL Master] eller [!DNL Integration] på Adobe Commerce i molninfrastruktur.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur, [alla versioner som stöds](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Orsak

[!DNL SSL certificates] i de grenarna är bara giltiga i 30 dagar och grenen har kanske inte distribuerats om på över 30 dagar.

Felet ser ut ungefär så här:

```cURL
cURL error 60: SSL certificate problem: certificate has expired
```

>[!NOTE]
>
>Dessa certifikat har inte signerats av välkända externa certifikatutfärdare (CA) som [!DNL Let's Encrypt] eller [!DNL DigiCert]. De hanteras av Adobe-plattformen i testnings- och utvecklingssyfte och är inte betrodda som standard i webbläsare eller webbläsare om du inte uttryckligen litar på rotcertifikatutfärdaren.

## Lösning

Kontrollera när grenen senast distribuerades. Om gränsvärdet är över 30 dagar ska du distribuera grenen igen.

Två metoder för att kontrollera när den senaste distributionen utfördes:

* [Metod 1: Använd [!DNL magento-cloud] CLI](#meth2).
* [Metod 2: Öppna  [!DNL Project URL]](#meth3).

Om distributionen har slutförts förnyas [!DNL SSL certificate] automatiskt.

Om distributionen misslyckas och du behöver hjälp med att lösa den, [skickar du en supportanmälan](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=sv-SE#submit-ticket).

### Metod 1: Använd [!DNL magento-cloud] CLI {#meth2}

Kör det här kommandot: `magento-cloud activity:list --type=environment.push`

### Metod 2: Öppna [!DNL Project URL] {#meth3}

Gå till, till exempel: `https://demo.magento.cloud/#/projects/<project>/environments/<environment>`, och kontrollera när den senaste distributionen utfördes.

## Relaterad läsning

I vår utvecklardokumentation:

* [Cloud Manager API: SSLCertificates](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/SSLCertificates)
* [Konfigurera snabbt: Etablera SSL-/TLS-certifikat](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates)

I vår kunskapsbas:

* [Information om förfallodatum för anpassat SSL-certifikat](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/custom-ssl-certificate-expiration-information.html?lang=sv-SE)
* [SSL-certifikat (TLS) för Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/ssl-tls-certificates-for-magento-commerce-cloud-faq.html?lang=sv-SE)
