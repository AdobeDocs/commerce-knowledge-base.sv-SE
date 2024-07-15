---
title: Kravjobbsfel i Advanced Reporting Adobe Commerce
description: I den här artikeln finns korrigeringsfiler för problem med avancerade rapporteringsjobben i Adobe Commerce, vilket kan orsaka ett 404-fel för kunder som försöker få åtkomst till avancerade rapporter.
exl-id: c11a5faf-a243-411a-af0f-585a401e6e39
feature: Cache
role: Developer
source-git-commit: 6287e708c830680e04dd068b64cf63ca13ecdedb
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Kravjobbsfel i Advanced Reporting Adobe Commerce

I den här artikeln finns korrigeringsfiler för problem med avancerade rapporteringsjobben i Adobe Commerce, vilket kan orsaka ett 404-fel för kunder som försöker få åtkomst till avancerade rapporter.

## Berörda produkter och versioner

Adobe Commerce (alla installationsalternativ) 2.3.x

## Problem

En kund får ett 404-fel när de försöker få åtkomst till avancerad rapportering och det finns fel i loggarna som är kopplade till `analytics_collect_data job`.

## Kompatibla Magento-versioner:

Patcharna är kompatibla (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:

* [MDVA-19391\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip): Adobe Commerce (alla distributionsalternativ) 2.3.1-2.3.4-p2
* [MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip): Adobe Commerce (alla distributionsalternativ) 2.3.0
* [MDVA-15136\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip): Adobe Commerce (alla distributionsalternativ) 2.3.0

## **Lösning**

Åtgärda problemet genom att använda den relevanta korrigeringen som är bifogad den här artikeln. Klicka på följande länkar om du vill hämta den:

* Hämta [MDVA-19391\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip)
* Hämta [MDVA-15136\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip)
* Hämta [MDVA-18980\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)

Så här kontrollerar du vilken patch som ska användas:

<ol><li>Granska loggarna med följande kommando:<code>grep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz</code>
</li><li>Beroende på vilket fel du ser kan du välja en korrigering med hjälp av informationen i följande tabell.<table style="width: 826px;">
<tbody>
<tr>
<td class="wysiwyg-text-align-center">
<p>Fel</p>
</td>
<td class="wysiwyg-text-align-center">Lappa</td>
</tr>
<tr>
<td>
<pre>report.CRITICAL: Fel vid körning av cron-jobb {"exception":"[object] (RuntimeException(code:
  0): Fel vid körning av ett cron-jobb på /srv/public_html/vendor/magento/module-cron/Observer/ProcessCronQueueObserver.php:327,
  TypeError(code: 0): substr_count() förväntar att parameter 1 ska vara sträng, null angiven
  på /srv/public_html/vendor/magento/module-page-builder-analytics/Model/ContentTypeUsageReportProvider.php:106)"}
  []</pre>ELLER<pre>report.ERROR: Cron Job analytics_collect_data har ett fel: substr_count() förväntar
  parameter 1 ska vara sträng, null har angetts. Statistik: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384}
  [] []</pre>
<p> </p>
</td>
<td>Använd <a href="assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch">MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip</a>, rensa cachen och vänta 24 timmar på att jobbet ska köras igen och försök igen.</td>
</tr>
<tr>
<td>
<p><em>Det gick inte att öppna filen /tmp/analytics/tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/./tmp/ ../tmp/../tmp/../tmp/../tmp/../</em></p>
</td>
<td>Använd <a href="assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch">MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip</a>, rensa cachen och vänta 24 timmar på att jobbet ska köras igen och försök igen.</td>
</tr>
<tr>
<td><em>Ogiltig chiffrering</em></td>
<td>Använd <a href="assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch">MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip</a>, rensa cachen och vänta 24 timmar på att jobbet ska köras igen och försök igen.</td>
</tr>
</tbody>
</table>
</li></ol>

## Så här sätter du på plåstret

Zippa upp filen och följ instruktionerna i [Använda en kompositkorrigering från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## Relaterad läsning

[Det går inte att ta bort filen. Varning!unlink: Det finns inget sådant fil- eller katalogfel från administratören](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md)
