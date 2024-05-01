---
title: 'ACSD-48300: Det går inte att skapa retur om den konfigurerbara produkten tas bort'
description: Använd patchen ACSD-48300 för att åtgärda Adobe Commerce-problemet där retur inte kan skapas om den konfigurerbara produkten tas bort.
exl-id: 4abbc398-b341-4ff6-9483-9cf8f3dbbfbb
feature: Admin Workspace, Configuration, Orders, Products, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-48300: Det går inte att skapa retur om den konfigurerbara produkten tas bort

Korrigeringen ACSD-48300 åtgärdar ett problem där en retur inte kan skapas om den konfigurerbara produkten tas bort. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 är installerat. Korrigerings-ID är ACSD-48300. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Retur kan inte skapas om den konfigurerbara produkten tas bort.

<u>Steg som ska återskapas</u>:

1. Aktivera RMA i butiken vid **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]**.
1. Skapa en konfigurerbar produkt.
1. Skapa ett konto (och/eller logga in) i butiken.
1. Lägg en konfigurerbar produkt i kundvagnen som första artikel.
1. Lägg till vilken enkel produkt som helst efteråt.
1. Beställ.
1. Leverera ordern.
1. Ta nu endast bort den konfigurerbara produkten (ta inte bort dess underordnade produkter).
1. Gå till butiken **[!UICONTROL My Orders]** och visa ordningen.
1. Klicka på **[!UICONTROL Return]**.

<u>Förväntade resultat</u>:

Administratören kan returnera artiklar även om den konfigurerbara produkten tas bort.

<u>Faktiska resultat</u>:

Ett fel inträffar när artiklar returneras.

```
report.CRITICAL: Error: Call to a member function getShipmentType() on null in magento2ee/app/code/Magento/Rma/view/frontend/templates/return/create.phtml:52
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
