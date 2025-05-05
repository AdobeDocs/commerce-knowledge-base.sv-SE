---
title: Sökmotorn för MySQL-kataloger kommer att tas bort i Adobe Commerce 2.4.0
description: Adobe Commerce lokalt, Adobe Commerce i molninfrastruktur och Magento Open Source 2.4.0 kommer att släppas under de närmaste månaderna. För Adobe Commerce lokalt och Magento Open Source är version 2.4.0 Elasticsearch 6.x eller 7.x en obligatorisk komponent och MySQL-sökmotorn tas bort. I Adobe Commerce i molninfrastruktur krävs redan Elasticsearch.
exl-id: 717be515-3cbf-42e9-9b72-caf11b8c3771
feature: Catalog Management, Search, Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# Sökmotorn för MySQL-kataloger kommer att tas bort i Adobe Commerce 2.4.0

Adobe Commerce lokalt, Adobe Commerce i molninfrastruktur och Magento Open Source 2.4.0 kommer att släppas under de närmaste månaderna. För Adobe Commerce lokalt och Magento Open Source är version 2.4.0 Elasticsearch 6.x eller 7.x en obligatorisk komponent och MySQL-sökmotorn tas bort. I Adobe Commerce i molninfrastruktur krävs redan Elasticsearch.

>[!WARNING]
>
>Om du inte installerar/konfigurerar Elasticsearch 6/7 innan du försöker uppgradera kan det orsaka allvarliga problem med Adobe Commerce. Observera att uppgraderingar av tjänster på Adobe Commerce i molninfrastruktur inte kan skjutas upp till produktionsmiljön utan att vårt infrastrukturteam får ett meddelande om detta inom 48 timmar. Detta är nödvändigt eftersom vi måste se till att det finns en infrastruktursupporttekniker tillgänglig som kan uppdatera din konfiguration inom en önskad tidsram med minimala driftavbrott i din produktionsmiljö. Så 48 timmar före när dina ändringar behöver vara i produktion [skickar du en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) med information om den nödvändiga uppgraderingen och den tidpunkt då du vill att uppgraderingen ska starta.

Orsaken till att MySQL-sökmotorn har tagits bort är att Elasticsearch har överlägsna sökfunktioner och optimerade kataloginställningar.

## Berörda produkter och versioner:

* Adobe Commerce lokalt v2.4.0
* Magento Open Source v2.4.0

## Uppgraderar:

<table style="height: 164px; width: 632.2px;">
<tbody>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;"><strong>Sökmotor</strong></td>
<td class="wysiwyg-text-align-center" style="width: 478.2px;"><strong>Åtgärd</strong></td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">MySQL</td>
<td style="width: 478.2px;">Du måste installera Elasticsearch. Se <a href="https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/search/overview-search">Installera och konfigurera Elasticsearch</a> i utvecklardokumentationen.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch (utan version angiven)</td>
<td style="width: 478.2px;">Du använder Elasticsearch 2 och måste uppdatera till Elasticsearch 7 (rekommenderas) eller 6. Mer information finns i <a href="https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/search/overview-search#es-upgrade6">Uppgradera Elasticsearch</a> och <a href="https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/search/configure-search-engine">Konfigurera Commerce att använda Elasticsearch</a> i utvecklardokumentationen.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">ELASTICSEARCH 5</td>
<td style="width: 478.2px;">Elasticsearch 5 har nått sitt <a href="https://www.elastic.co/support/eol">sista användningsdatum</a> och har tagits bort i Adobe Commerce 2.4.0. Uppdatera till Elasticsearch 7 (rekommenderas) eller 6.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch 6 eller 7</td>
<td style="width: 478.2px;">Du behöver inte utföra några ytterligare steg innan du uppgraderar till Adobe Commerce 2.4.0.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Tredjepartstillägg</td>
<td style="width: 478.2px;">Du behöver inte installera Elasticsearch. Adobe Commerce rekommenderar att du kontaktar din sökmotorleverantör för att avgöra om tillägget är helt kompatibelt med Adobe Commerce 2.4.0.</td>
</tr>
</tbody>
</table>

## Installation:

När Adobe Commerce lokal och Magento Open Source 2.4.0 släpps är Elasticsearch en nödvändig komponent, så du måste ha en Elasticsearch-värdkonfiguration och konfigurerad innan du installerar version 2.4.0. Se [Installera och konfigurera Elasticsearch](https://experienceleague.adobe.com/sv/docs/commerce-operations/configuration-guide/search/overview-search) i utvecklardokumentationen.

Som standard används Elasticsearch 7 som sökmotor i Adobe Commerce-sökningen och försök att ansluta till en server på localhost:9200. Elasticsearch 6.x stöds också. Om konfigurationen inte matchar standardinställningarna kan du konfigurera de här inställningarna med argument som skickas till `setup:install`, på ungefär samma sätt som databasanslutningen konfigureras.

Exempel: `setup:install --elasticsearch-host=es.mystore.com`

Under installationen kontrolleras anslutningen till Elasticsearch och installationen misslyckas om Adobe Commerce inte kan ansluta till en Elasticsearch-värd. Om detta inträffar kontrollerar du att Elasticsearch är igång och att du har angett rätt anslutningsparametrar.
