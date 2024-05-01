---
title: 'ACSD-56515: Administratör med behörighet på webbplatsnivå kan inte redigera [!UICONTROL Dynamic Block]'
description: Använd korrigeringsfilen ACSD-56515 för att åtgärda Adobe Commerce-problemet där administratören med behörighet på webbplatsnivå inte kan lägga till eller redigera [!UICONTROL Dynamic Block].
feature: Roles/Permissions, Admin Workspace
role: Admin, Developer
exl-id: 5aa6b11e-b467-4076-ad36-162966cbf6df
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-56515: Administratör med behörighet på webbplatsnivå kan inte redigera [!UICONTROL Dynamic Block]

Korrigeringen ACSD-56515 åtgärdar ett problem där administratören med behörighet på webbplatsnivå inte kan lägga till eller redigera [!UICONTROL Dynamic Block]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 är installerat. Korrigerings-ID är ACSD-56515. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p4

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratören med behörighet på webbplatsnivå kan inte lägga till eller redigera [!UICONTROL Dynamic Block].

<u>Steg som ska återskapas</u>:

1. Skapa en sekundär webbplats med butiker och butiksmaterial.
1. Gå till **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]** och skapa en användarroll som är begränsad till den sekundära webbplatsomfånget med alla tillgängliga resurser.
1. Skapa en administratörsanvändare med rollen som skapas ovan.
1. Logga in med den begränsade administratörsanvändaren och skapa en [!UICONTROL Dynamic Block].

<u>Förväntade resultat</u>:

Administratörsanvändare med begränsningar för webbplatsen kan skapa en [!UICONTROL Dynamic Block].

<u>Faktiska resultat</u>:

Du får följande fel: *Fler behörigheter krävs för att visa det här objektet*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
