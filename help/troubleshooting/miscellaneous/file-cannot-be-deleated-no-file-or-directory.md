---
title: 'Det går inte att ta bort filen. Varning! Bryt länk: Det finns inget sådant fil- eller katalogfel från  [!DNL Admin]'
description: Den här artikeln innehåller en lösning på problemet där ett fel uppstod *Det går inte att ta bort filen. Varning!avlänka Det finns inget sådant fil- eller katalogfel* från  [!DNL Admin] när du utför en [!DNL Javascript/CSS] tömning.
feature: Admin Workspace, Observability
role: Developer
exl-id: db265e3c-a809-4404-839a-273001e81d22
source-git-commit: fd5fd6e1bc04db56497a2e0c2a96bc1b06d4f7a1
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# *Det går inte att ta bort filen. Varning!unlink: Det finns inget sådant fil- eller katalogfel* från [!DNL Admin]

Den här artikeln innehåller en lösning på problemet där ett fel *Det går inte att ta bort filen. Varning!unlink: Det finns inget sådant fil- eller katalogfel* från [!DNL Commerce Admin] när du tömmer [!DNL JavaScript/CSS].

## Berörda produkter och versioner

* Adobe Commerce 2.4.0 - 2.4.6, alla distributionsmetoder

## Problem

Ett fel inträffar när du gör en [!DNL JS/CSS]-tömning:

*Det går inte att ta bort filen &quot;/app/pub/static/_cache/merged/.nfsa42d0e64799fd100000001b&quot;. Varning!unlink(/app/pub/static/_cache/merged/.nfsa42d0e64799fd1000000001b): Ingen sådan fil eller katalog*

Eller: Felet ovan visas i [!DNL Admin] och/eller ett liknande fel i [!DNL New Relic] eller i distributionsloggarna.

Eller: Du har inte åtkomst till Advanced Reporting och kron-jobbet analytics_collect_data misslyckas med det här felet:

*Det går inte att ta bort filen &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a000850c0&quot;. Varning!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a000850c0): Ingen sådan fil eller katalog*

<u>Steg att återskapa:</u>

Metod 1:

1. Logga in på [!DNL Admin].
1. Gå till **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Klicka på **[!UICONTROL Flush][!DNL JavaScript/CSS][!UICONTROL Cache]**.

Metod 2:

1. Logga in på [!DNL Admin].
1. Gå till **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**.
1. Gör ändringar i [!UICONTROL Base URL] eller [!UICONTROL Base URL (Secure)].
1. Klicka på **[!UICONTROL Save Config]**.

## Lösning

Om du använder Adobe Commerce i molninfrastrukturen och har [!DNL magento/magento-cloud-patches] 1.0.22 installerat som innehåller korrigeringsfilen behöver du inte installera ACSD-50165 separat.

Adobe Commerce i molninfrastruktur: Uppgradera molnkorrigeringar för Commerce till 1.0.22 (**eller senare**) som innehåller den här korrigeringen: [Molnkorrigeringar för Commerce](/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html).

Lokal Adobe Commerce: Använd ACSD-50165 med [kvalitetskorrigeringsverktyg > Användning](/docs/commerce-operations/tools/quality-patches-tool/usage.html). ACSD-50165-korrigeringen levereras med [!DNL QPT] [v1.1.30.](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html#v1-1-30)

## Relaterad läsning

* [[!DNL Quality Patches Tool] > Versionsinformation](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) i Commerce-handboken.
* [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i Commerce Tools Guide.
