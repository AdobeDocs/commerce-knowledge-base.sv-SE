---
title: 'ACSD-47497: ACL saknas för Store / Configuration / Services [!UICONTROL OAuth]'
description: Använd korrigeringsfilen ACSD-47497 för att åtgärda Adobe Commerce-problemet när behörigheter anges för en viss roll och du inte kan definiera åtkomst till konfigurationsavsnittet.
exl-id: c13fd541-1379-4893-9190-9da1422b2b99
feature: Configuration, Identity Management, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-47497: ACL saknas för Store / Configuration / Services [!UICONTROL OAuth]

Programfixen ACSD-47497 löser problemet där **[!UICONTROL Services]** -fliken visas inte i **[!UICONTROL Configuration]** i Adobe Commerce Admin. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 är installerat. Korrigerings-ID är ACSD-47497. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**
* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce:**
* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När behörigheter har angetts för en viss roll kan du inte definiera åtkomst till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**.

<u>Steg som ska återskapas</u>:

1. Logga in på Adobe Commerce Admin. Gå till **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**.
1. Välj **[!UICONTROL Role Resources]** i rollen Administratörer och ange **[!UICONTROL Resource Access]** under **[!UICONTROL Roles Resources]** till _Egen_ markerar du alla kryssrutorna. Välj **[!UICONTROL Save Role]**.
1. Välj **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]**. The **[!UICONTROL OAuth]** konfigurationsavsnittet är inte tillgängligt.

<u>Förväntade resultat</u>:

I **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]** visas konfigurationsavsnittet.

<u>Faktiska resultat</u>:

I **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**, saknas konfigurationsavsnittet.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
