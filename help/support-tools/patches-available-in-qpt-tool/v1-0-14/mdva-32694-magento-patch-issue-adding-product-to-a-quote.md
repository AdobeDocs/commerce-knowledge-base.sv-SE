---
title: 'MDVA-32694 patch: issue adding adding product to a quote'
description: MDVA-32694-korrigeringen åtgärdar problemet med att det inte går att lägga till en giltig produkt i Admin till en överlåtbar offert som skapats på en icke-standardwebbplats.
exl-id: 964abbbd-c8b1-4645-a393-7283f52e94ff
feature: Products, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-32694-korrigering: problem med att lägga till produkten i en offert

MDVA-32694-korrigeringen åtgärdar problemet med att det inte går att lägga till en giltig produkt i Admin till en överlåtbar offert som skapats på en icke-standardwebbplats.

Den här korrigeringen är tillgänglig när [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 är installerat. Observera att problemet schemaläggs att åtgärdas i Adobe Commerce version 2.4.3.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

Adobe Commerce i molninfrastruktur 2.3.2 med B2B version 1.2

**Kompatibel med Adobe Commerce:**

Adobe Commerce on cloud infrastructure and Adobe Commerce on-local 2.3.0 - 2.3.5-p2, 2.4.0, 2.4.1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

<u>Förutsättningar</u>:

Installera en ny Adobe Commerce-instans med B2B.

<u>Steg som ska återskapas</u>:

1. Gå till **STORES > Configuration > GENERAL > B2B Features** och aktivera **Företag** och **B2B-citat**.
1. Skapa ytterligare två webbplatser med **butiker** och **storecensioner** (Sammanlagt ska du ha tre webbplatser: *bas*, *webbplats2*, *webbplats3*).
1. Skapa en enkel produkt och tilldela den endast till *webbplats3*.
1. Gå till **STORES > All Stores** och ange *webbplats3* as **standard**.
1. Gå till fronten och skapa ett nytt företag på *webbplats3*.
1. Lägg den tidigare skapade produkten i kundvagnen och skapa en ny överlåtbar offert.
1. Gå till **STORES > All Stores** och ange &quot;*bas*&quot; som **standard**.
1. Gå till **SALES > Quotes > Open created earlier** och försöker lägga till samma produkt.

<u>Förväntade resultat</u>:

Administratörsanvändaren kan lägga till samma produkt i offerten som förväntat.

<u>Faktiska resultat</u>:

Administratörsanvändaren kan inte lägga till samma produkt i offerten, och det här felmeddelandet visas:

```php
This product is assigned to another website.
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [Programuppdateringsguide > Tillämpa korrigeringar](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) i vår dokumentation för utvecklare.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) i vår dokumentation för utvecklare.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Quality Patches Tool released: a new tool to self-service quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för din Adobe Commerce-utgåva med verktyget för kvalitetskorrigeringar](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [Patchar tillgängliga i QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) i vår dokumentation för utvecklare.
