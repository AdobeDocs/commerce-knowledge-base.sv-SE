---
title: 'ACSD-52613: Cachen och index uppdateras utan uppdateringar'
description: Använd patchen ACSD-52613 för att åtgärda Adobe Commerce-problemet där cache och index uppdateras när inga uppdateringar görs av Inventory_source-objekt senast  [!DNL REST API].
feature: REST
role: Admin
exl-id: 78f23fee-a48e-4ee2-bc75-e98e3dd1ac44
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-52613: Cache och index uppdateras även utan uppdateringar

Korrigeringen ACSD-52613 åtgärdar ett problem där Adobe Commerce-problemet där cache och index uppdateras när [!DNL REST API] inte gör några uppdateringar av `Inventory_source` objekt. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.37 har installerats. Korrigerings-ID är ACSD-52613. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.7

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Cachen och index uppdateras när inga uppdateringar görs av `Inventory_source` objekt av [!DNL REST API].

<u>Förutsättningar</u>:

Installerade lagermoduler

<u>Steg som ska återskapas</u>:

1. Låt utvecklarläget ha `debug.log`.
1. Förbered importfilen med 100 produkter - import.csv:

   ```
   sku    name    product_type    attribute_set_code    price
   test_sku_1    test_sku_1    simple    Default    10
   test_sku_2    test_sku_2    simple    Default    10
   ...
   test_sku_100    test_sku_100    simple    Default    10
   ```

1. Importera produkter från `import.csv`
1. Skapa ett nytt lager och en ny källa med namnen **test_stock** och **test_source**.
1. Tilldela nytt arkiv till webbplatsen och tilldela Stock källan.
1. Skapa en ny integrering med åtkomst till alla, aktivera den och kopiera och klistra in åtkomsttoken.
1. Gå till **Lagrar** > **Konfiguration** > **Tjänster** > **OAuth** > **Konsumentinställningar** och aktivera **Tillåt att OAuth Access-token används som fristående Bearer-token**.
1. Töm cacheminnet.
1. Ange indexerare som **Uppdaterad av schema**
1. Kör API-begäran

   `POST ../rest/V1/inventory/source-items`

   som använder den här texten

   ```
   {
    "sourceItems": [
        {
            "sku": "test_sku_1",
            "source_code": "test_source",
            "quantity": 24,
            "status": 1
        },
        {
            "sku": "test_sku_2",
            "source_code": "test_source",
            "quantity": 50,
            "status": 1
        },
        {
            "sku": "test_sku_3",
            "source_code": "test_source",
            "quantity": 50,
            "status": 1
        },
        {
            "sku": "test_sku_4",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_5",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_6",
            "source_code": "test_source",
            "quantity": 19,
            "status": 1
        },
        {
            "sku": "test_sku_7",
            "source_code": "test_source",
            "quantity": 50,
            "status": 1
        },
        {
            "sku": "test_sku_8",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_9",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_10",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_11",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_12",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_13",
            "source_code": "test_source",
            "quantity": 50,
            "status": 1
        },
        {
            "sku": "test_sku_14",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_15",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_16",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_17",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_18",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_19",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_20",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_21",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_22",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_23",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_24",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_25",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_26",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_27",
            "source_code": "test_source",
            "quantity": 13,
            "status": 1
        },
        {
            "sku": "test_sku_28",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_29",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_30",
            "source_code": "test_source",
            "quantity": 1,
            "status": 1
        },
        {
            "sku": "test_sku_31",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_32",
            "source_code": "test_source",
            "quantity": 1,
            "status": 1
        },
        {
            "sku": "test_sku_33",
            "source_code": "test_source",
            "quantity": 49,
            "status": 1
        },
        {
            "sku": "test_sku_34",
            "source_code": "test_source",
            "quantity": 12,
            "status": 1
        },
        {
            "sku": "test_sku_35",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_36",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_37",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_38",
            "source_code": "test_source",
            "quantity": 10,
            "status": 1
        },
        {
            "sku": "test_sku_39",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_40",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_41",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_42",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_43",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_44",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_45",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_46",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_47",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_48",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_49",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_50",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_51",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_52",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_53",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_54",
            "source_code": "test_source",
            "quantity": 1,
            "status": 1
        },
        {
            "sku": "test_sku_55",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_56",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_57",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_58",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_59",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_60",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_61",
            "source_code": "test_source",
            "quantity": 16,
            "status": 1
        },
        {
            "sku": "test_sku_62",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_63",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_64",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_65",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_66",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_67",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_68",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_69",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_70",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_71",
            "source_code": "test_source",
            "quantity": 16,
            "status": 1
        },
        {
            "sku": "test_sku_72",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_73",
            "source_code": "test_source",
            "quantity": 3,
            "status": 1
        },
        {
            "sku": "test_sku_74",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_75",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_76",
            "source_code": "test_source",
            "quantity": 50,
            "status": 1
        },
        {
            "sku": "test_sku_77",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_78",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_79",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_80",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_81",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_82",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_83",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_84",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_85",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_86",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_87",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_88",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_89",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_90",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_91",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_92",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_93",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_94",
            "source_code": "test_source",
            "quantity": 3,
            "status": 1
        },
        {
            "sku": "test_sku_95",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_96",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_97",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_98",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_99",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_100",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        }
    ]
   }
   ```

1. Ta bort alla loggar från `var/log`
1. Kör [!DNL REST API]-begäran igen.
1. Kontrollera `var/log/debug.log`.

<u>Förväntade resultat</u>:

Cachen bör inte rensas och indexen bör inte köras efter den andra körningen eftersom inget har ändrats.

<u>Faktiska resultat</u>:

`var/log/debug.log` innehåller den post som är relaterad till rensningen av cachen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
