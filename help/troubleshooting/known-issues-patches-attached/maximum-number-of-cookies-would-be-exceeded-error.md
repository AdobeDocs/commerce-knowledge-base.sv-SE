---
title: Det högsta antalet cookies som tillåts i Adobe Commerce skulle överskridas
description: Lär dig hur du löser Adobe Commerce-problemet där ett fel inträffar som anger att det högsta antalet cookies skulle överskridas.
feature: Deploy, Support, Upgrade, Tools and External Services
role: Admin, Developer
source-git-commit: 44e167c801bbcd313f74c9fc51f9cde9473ef96f
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# *Maximalt antal cookies skulle överskridas*-fel i Adobe Commerce

Den här artikeln innehåller korrigeringsfiler som löser felet med att *det högsta antalet cookies som kan överskridas* i Adobe Commerce.

## Berörda produkter och versioner

Adobe Commerce (alla distributionsmetoder) 2.4.4-2.4.7, med någon av följande korrigeringar:

* MDVA-12304-korrigering tillämpad med [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/release-notes)
* [APSB25-08 isolerad säkerhetsuppdatering](/help/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08.md)
* [Molnkorrigeringar för [!DNL Commerce] 1.1.4](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches)

## Problem

Problem med cookies i Adobe Commerce orsakar följande fel i felloggarna:

*rapport.VARNING! Det går inte att skicka cookien. Maximalt antal cookies skulle överskridas.*

### Orsak

Problemet inträffar eftersom det maximala antalet tillåtna cookies är *50*.

## Lösning

1. Ta bort MDVA-12304-korrigeringen om du tillämpade den med [!DNL Quality Patches Tool (QPT)].

   * Ta bort korrigeringen från `.magento.env.yaml` för Adobe Commerce på molninfrastrukturer.
   * För Adobe Commerce lokala installationer kör du följande kommando för att återställa korrigeringen:

     `vendor/bin/magento/quality-patches revert MDVA-12304`

1. Använd de bifogade patcharna enligt din Adobe Commerce-version:

   * För versionerna 2.4.4-p12, 2.4.5-p11, 2.4.6-p9 och 2.4.7-p4 använder du korrigeringsfilen [ACSD-64710](assets/acsd-64710_2.4.5-p11.patch.zip).

   * För versionerna 2.4.4-p13, 2.4.5-p12, 2.4.6-p10, 2.4.7-p5 och 2.4.8 använder du korrigeringsfilen [ACSD-65562](assets/acsd-65562_2.4.5-p12.patch.zip).

### Relaterad läsning

* [Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/apply) i Adobe Commerce uppgraderingsguide
* [Bästa tillvägagångssätt för att distribuera Adobe Commerce-korrigeringsfiler i stor skala](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale) i Adobe Commerce Implementeringsspelbok
* [Versionsinformation om Commerce Cloud Tools Suite](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-tools-suite) i Commerce on Cloud Guide.
