---
title: Adobe Commerce 2.4.7-p4 [!DNL HIPAA] 1.2.0-kompatibilitetspaket Hotfix
description: I den här artikeln finns en snabbkorrigering för att lägga till kompatibilitet för det nya [!DNL HIPAA] paketet 1.2.0 med Adobe Commerce i molninfrastrukturen 2.4.7-p4
feature: Install, Upgrade, Security, Compliance
role: Developer
source-git-commit: 705c43d2328d47fb5f00ae582a2a623ca9f94f70
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Adobe Commerce 2.4.7-p4 [!DNL HIPAA] 1.2.0-kompatibilitetspaket Hotfix

I den här artikeln finns en snabbkorrigering för att lägga till kompatibilitet för det nya **[!DNL HIPAA]-paketet 1.2.0** med Adobe Commerce i molninfrastrukturen 2.4.7-p4.

Problemet kommer att åtgärdas i version 2.4.7-p5.

## Berörda versioner och produkter

Adobe Commerce om molninfrastruktur 2.4.7-p4 och tidigare

## Förutsättningar

* Adobe har etablerat ditt Adobe Commerce-konto för att komma åt tillägget **[!DNL HIPAA Ready]**. Se [[!DNL HIPAA] beredskap för Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview) för mer information i vår **Adobe Commerce: Starthandbok**.
* Åtkomst till [repo.magento.com](https://repo.magento.com) för att installera tillägget. Om du vill ha nyckelgenerering och de nödvändiga rättigheterna kan du läsa [Hämta dina autentiseringsnycklar](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) i **Adobe Commerce: Installationshandbok**.

## Problem

[!DNL HIPAA]-paketet 1.1.0 är inte kompatibelt med versionsraden för Adobe Commerce 2.4.7x.

## Lösning

Genom den här snabbkorrigeringen kan handlare som kör Adobe Commerce i molninfrastruktur 2.4.7-p4 använda paketet [!DNL HIPAA] 1.2.0.

>[!NOTE]
>
>**[!DNL HIPAA]1.2.0 är endast kompatibelt med Adobe Commerce 2.4.7-p5. Om du vill lägga till kompatibilitet med [!DNL HIPAA] 1.2.0 i Adobe Commerce 2.4.7-p4 installerar du den angivna korrigeringen.<br><u>Om du inte använder Adobe Commerce 2.4.7-p4 måste du först uppgradera till Adobe Commerce 2.4.7-p4 för att kunna använda korrigeringen</u>.**

För att åtgärda problemet med Adobe Commerce i molninfrastrukturen 2.4.7-p4 bör du installera korrigeringsfilen:

[ac-13382--patch-for-hipaa-2-4-7-p4-composer-patch.zip](assets/ac-13382--patch-for-hipaa-2-4-7-p4-composer-patch.zip)

## Så här sätter du på plåstret

Zippa upp filen och se [Använda en kompositkorrigering från Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) i vår kunskapsbas för support för instruktioner.

## Endast för Adobe Commerce på molnhandlare - Hur du ser om korrigeringen har tillämpats

Eftersom det inte är enkelt att kontrollera om problemet har åtgärdats, kanske du vill kontrollera om korrigeringen har installerats korrekt.

>[!NOTE]
>
><u>Du kan göra detta genom att följa de här stegen och använda filen `VULN-27015-2.4.7_COMPOSER.patch` **som ett exempel**</u>:

1. [Installera verktyget för kvalitetskorrigeringar](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Kör kommandot:<br>
   ![cve-2024-34102-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Du bör se utdata som liknar detta, **<u>där exemplet som används här, VULN-27015</u>**, returnerar statusen *Används*:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->
