---
title: URL för Adobe Commerce Admin - adress visas
description: I den här artikeln finns en patch för säkerhetsproblemet i Adobe Commerce där URL-adressen till Admin-panelen kan visas. Att veta var URL:en finns kan göra det enklare att automatisera attacker.
exl-id: fe147ad5-6019-46c1-b48c-6b957b6e1582
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# URL för Adobe Commerce Admin - adress visas

I den här artikeln finns en patch för säkerhetsproblemet i Adobe Commerce där URL-adressen till Admin-panelen kan visas. Att veta var URL:en finns kan göra det enklare att automatisera attacker.

## Berörda produkter och versioner

* Adobe Commerce i molninfrastruktur 2.X.X
* Adobe Commerce lokal 2.X.X
* Magento Open Source 2.x.x

## Problem

Ett problem har upptäckts i Magento Open Source och Adobe Commerce som kan användas för att visa URL-adressen för Admin-panelen. Även om det för närvarande inte finns någon anledning att tro att detta problem skulle leda till en direkt kompromiss, kan det vara enklare att automatisera attacker om du vet var URL:en finns.

## Lösning

Åtgärda problemet genom att tillämpa den patch som är bifogad den här artikeln. Klicka på följande länk om du vill hämta den:

* Ladda ned [PRODSECB UG-2432\_EE\_2.1.17\_Composer.patch](assets/PRODSECBUG-2432_EE_2.1.17_composer.patch.zip) - för version 2.1.13-2.1.17, Adobe Commerce, Magento Open Source
* Ladda ned [PRODSECB UG-2432\_EE\_2.2.8\_Composer.patch](assets/PRODSECBUG-2432_EE_2.2.8_composer.patch.zip) - för versionerna 2.2.0-2.2.8, alla utgåvor
* Ladda ned [PRODSECB UG-2432\_EE\_2.3.1\_Composer.patch](assets/PRODSECBUG-2432_EE_2.3.1_composer.patch.zip) - för versionerna 2.3.0-2.3.1, alla utgåvor

Om du inte ser någon patch för din produkt/version ska du uppgradera till den senaste säkerhetsreleasen och sedan använda patchen.

Adobe rekommenderar starkt att du sätter på plåstret så snart som möjligt, även om du inte har fått några symtom på en attack.

## Så här sätter du på plåstret

Mer information finns i [Använda en dispositionsruta från Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## Andra säkerhetsrekommendationer

Adobe rekommenderar också starkt att handlare använder verktyg för att säkra sin administrationspanel, inklusive tvåfaktorsautentisering, VPN, IP-Tillåtelselistning med mera. Mer information finns i följande bloggar och dokumentation:

* [5 Omedelbara åtgärder mot attacker från Protect mot akutstyrda attacker](https://magento.com/security/best-practices/5-immediate-actions-protect-against-brute-force-attacks)
* [Protect Ditt installationslösenord för Magento Garanterar en ny uppdatering](https://magento.com/security/best-practices/protect-your-magento-installation-password-guessing-new-update)
* [Bästa praxis för säkerhet](https://magento.com/security/best-practices/security-best-practices)
* Lägger till och konfigurerar tvåfaktorsautentisering i Adobe Commerce för [2.4.x](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication)
