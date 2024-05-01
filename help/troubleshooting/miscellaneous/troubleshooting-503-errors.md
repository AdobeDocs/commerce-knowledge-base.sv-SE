---
title: Felsökning av 503-fel orsakad av att standardinställningarna för lack måste ändras
description: Den här artikeln innehåller lösningar för felsökning av 503-fel som orsakas av att vissa standardvärden för Varnish Cache inte är tillräckligt för din butik.
exl-id: 3f001cc9-b19a-4dee-bff0-fc8ba89e2646
feature: Cache, Categories
role: Admin
source-git-commit: 9c5e993b69a98865a1142110625252da848eae04
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Felsökning av 503-fel orsakad av att standardinställningarna för lack måste ändras

Den här artikeln innehåller lösningar för felsökning av 503-fel som orsakas av att vissa standardvärden för Varnish Cache inte är tillräckligt för din butik.

## Problem

Om längden på de cachetaggar som används av Adobe Commerce överstiger varnishs standardvärde på 8 192 byte, kan du se HTTP 503-fel (Backend Fetch Failed) i webbläsaren. Felen kan se ut ungefär så här: *&quot;Fel 503 Backend-hämtning misslyckades. Backend-hämtning misslyckades&quot;*

## Lösning

Lös problemet genom att öka standardvärdet för `http_resp_hdr_len` -parametern i Varnish-konfigurationsfilen. The `http_resp_hdr_len` parameter anger maximal rubriklängd *inom* den totala standardsvarsstorleken på 32768 byte.

>[!NOTE]
>
>Om `http_resp_hdr_len` värdet överstiger 32 kB måste du också öka standardsvarsstorleken med `http_resp_size` parameter.

1. Som användare med `root` behörighet, öppna din VDanish-konfigurationsfil i en textredigerare:
   * CentOS 6: `/etc/sysconfig/varnish`
   * CentOS 7: `/etc/varnish/varnish.params`
   * Debian: `/etc/default/varnish`
   * Ubuntu: `/etc/default/varnish`
1. Sök efter `http_resp_hdr_len` parameter.
1. Om parametern inte finns lägger du till den efter `thread_pool_max` .
1. Ange `http_resp_hdr_len` till ett värde som motsvarar antalet produkter i din största kategori multiplicerat med 21. (Varje produkttagg består av cirka 21 tecken.)    Om du till exempel anger värdet till 65 536 byte bör det fungera om den största kategorin har 3 000 produkter.    Till exempel:    ```conf    -p http_resp_hdr_len=65536 \    ```
1. Ange `http_resp_size` till ett värde som passar den ökade svarshuvudets längd.    Om du t.ex. använder summan av den ökade huvudlängden och standardsvarsstorleken är det en bra startpunkt (t.ex. 65536 + 32768 = 98304): `-p http_resp_size=98304`. Ett utdrag följer:

   ```
   # DAEMON_OPTS is used by the init script.
   DAEMON_OPTS="-a ${VARNISH_LISTEN_ADDRESS}:${VARNISH_LISTEN_PORT} \
       -f ${VARNISH_VCL_CONF} \
       -T ${VARNISH_ADMIN_LISTEN_ADDRESS}:${VARNISH_ADMIN_LISTEN_PORT} \
       -p thread_pool_min=${VARNISH_MIN_THREADS} \
       -p thread_pool_max=${VARNISH_MAX_THREADS} \
       -p http_resp_hdr_len=65536 \
       -p http_resp_size=98304 \
       -p workspace_backend=98304 \
       -S ${VARNISH_SECRET_FILE} \
       -s ${VARNISH_STORAGE}" \
   ```

## Timeout för hälsokontroll {#health-check-timeouts}

Om du inaktiverar cacheminnet när lack är konfigurerat som cachningsprogram och Adobe Commerce är i utvecklarläge kan det bli omöjligt att logga in på Admin.

Detta kan inträffa eftersom standardhälsokontrollen har en `timeout` värde på 2 sekunder. Det kan ta mer än 2 sekunder för hälsokontrollen att samla in och sammanfoga information vid varje hälsokontrollsbegäran. Om detta inträffar i 6 av 10 hälsokontroller anses Adobe Commerce-servern vara felfri. Slutgiltigt innehåll visas när servern inte är felfri.

Eftersom Admin används via Varnish kan du inte logga in på Admin för att aktivera cachelagring (om inte Adobe Commerce blir felfritt igen). Du kan emellertid använda följande kommando för att aktivera cache:

```bash
$ bin/magento cache:enable
```

Mer information om hur du använder kommandoraden finns i [Kom igång med kommandoradskonfiguration](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands.html).
