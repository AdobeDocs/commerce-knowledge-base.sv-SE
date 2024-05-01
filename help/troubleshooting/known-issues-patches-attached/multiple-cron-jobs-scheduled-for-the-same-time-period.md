---
title: Flera kronijobb har schemalagts för samma tidsperiod
description: I den här artikeln finns en patch för ett känt Adobe Commerce 2.2.2-problem som rör att ha flera kronijobb schemalagda att köras samtidigt efter att tidsvariablerna för vissa åtgärder redigerades i Commerce Admin.
exl-id: a3c1fe77-ed4c-43b5-8d6f-e5c549096c73
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---

# Flera kronijobb har schemalagts för samma tidsperiod

I den här artikeln finns en patch för ett känt Adobe Commerce 2.2.2-problem som rör att ha flera kronijobb schemalagda att köras samtidigt efter att tidsvariablerna för vissa åtgärder redigerades i Commerce Admin.

## Problem

När cron är konfigurerat att köras varje minut och du redigerar tidsvariabler för tre schemalagda aktiviteter i Admin `cron_schedule` databastabell visar grupper med flera aktiviteter som schemalagts att köras samtidigt.

<u>Steg som ska återskapas</u>:

1. I Commerce Admin går du till **Lager** > Inställningar > **Konfiguration** > **AVANCERAD** > **System** > **Kron (schemalagda aktiviteter)** > **Konfigurationsalternativ för kron för grupp: standard.**
1. Konfigurera följande alternativ:
   * **Händelserensning var**: rensa **Använd system** och ange *1440*.
   * **Livstid för lyckad historik**: rensa **Använd system** och ange *1440*.
   * **Livstid för felhistorik**: rensa **Använd system** och ange *1440*.

1. Klicka **Spara konfiguration**.
1. Kör `crontab -e` -kommando.
1. Sätt kron att springa varje minut.
1. Öppna tre terminalflikar/fönster.
1. Gå till Adobe Commerce `root/base/project` i varje terminalfönster.
1. Kör följande kommando i varje flik/fönster:

   ```bash
   bin/magento cache:flush && bin/magento cron:run && bin/magento cache:flush && bin/magento cron:run
   ```

1. Gå till MySQL och kör följande fråga:

   ```sql
   SELECT job_code, scheduled_at, count as count FROM cron_schedule GROUP BY job_code, scheduled_at HAVING count > 1 ORDER BY scheduled_at;
   ```

1. Se grupper med aktiviteter som schemaläggs att köras samtidigt.

<u>Förväntat resultat</u>: Ett cron `job_code` bör planeras för en viss tidsperiod.

<u>Faktiskt resultat</u>: Det finns flera kroniska jobb schemalagda för samma tidsperiod.

## Lösning

För Adobe Commerce på återförsäljare av molninfrastruktur [uppdatera ECE-verktygen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) kommer att lösa problemet.

Adobe Commerce lokala handlare bör använda en av de bifogade patcharna för att lösa problemet.

## Patchar

Patcherna är kopplade till den här artikeln. Om du vill hämta filen bläddrar du nedåt till slutet av artikeln och klickar på filnamnet, eller klickar på någon av följande länkar:

* [Hämta MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip)
* [Hämta MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip)
* [Hämta MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* [Hämta MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip)
* [Hämta MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip)
* [Hämta MDVA-11304\_EE\_2.2.2\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip)
* [Hämta MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip)

### Kompatibla Adobe Commerce-versioner

Patcharna skapades för en viss version och beskrivs i patchfilens namn. Exempel: MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch skapades för Adobe Commerce 2.2.4 och är den bästa korrigeringsfilen som kan användas för den här versionen.

Patcharna är också kompatibla med följande versioner:

* För Adobe Commerce lokalt 2.1.0-2.1.4: [Hämta MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip) Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:
   * Adobe Commerce om molninfrastruktur 2.1.0-2.1.4
* För Adobe Commerce lokalt 2.1.5-2.1.12: [Hämta MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip) Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:
   * Adobe Commerce om molninfrastruktur 2.1.5-2.1.12
* För Adobe Commerce om molninfrastruktur 2.1.13: [Hämta MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* För Adobe Commerce lokal 2.1.14-2.1.17: [Hämta MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip) Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:
   * Adobe Commerce lokal 2.1.18
   * Adobe Commerce om molninfrastruktur 2.1.14-2.1.18
* För Adobe Commerce lokalt 2.2.0-2.2.1: [Hämta MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip) Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:
   * Adobe Commerce om molninfrastruktur 2.2.0-2.2.1
* För Adobe Commerce lokalt 2.2.0-2.2.3: [Hämta MDVA-11304\_EE\_2.2.2\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip) Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:
   * Adobe Commerce om molninfrastruktur 2.2.0-2.2.3
* För Adobe Commerce lokalt 2.2.4: [Hämta MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip) Patchen är även kompatibel (men löser kanske inte problemet) med följande versioner och utgåvor av Adobe Commerce:
   * Adobe Commerce i molninfrastruktur 2.2.4

## Så här sätter du på plåstret

Se [Använda en kompositkorrigering från Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) i vår kunskapsbas för support, för instruktioner.

## Bifogade filer
