---
title: "ACSD-51907: Begränsad administratörsanvändare kan inte skapa kreditnota för offlineåterbetalning"
description: Använd patchen ACSD-51907 för att åtgärda Adobe Commerce-problemet där den begränsade administratörsanvändaren inte kan skapa en kreditnota med en återbetalning offline.
exl-id: 564e8524-f2dc-453c-be78-a920fbd47d71
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-51907: Begränsad administratörsanvändare kan inte skapa kreditnota för offlineåterbetalning

Korrigeringen ACSD-51907 åtgärdar prestandaproblemet där den begränsade administratörsanvändaren inte kan skapa en kreditnota med en offlineåterbetalning. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.33 är installerat. Korrigerings-ID är ACSD-51907. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen skapas för Adobe Commerce-versionen:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya [!DNL Quality Patches Tool] releaser. Om du vill kontrollera om patchen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches` till den senaste versionen och kontrollera om [[!DNL Quality Patches Tool]: Sök efter korrigeringssida](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Begränsad administratörsanvändare kan inte skapa en kreditnota med offlineåterbetalning.

<u>Steg som ska återskapas</u>:

1. Skapa en **kund** på standardwebbplatsen.
1. Skapa **ny webbplats** med relaterade *store* och *butiksvy*.
1. Ange standardwebbplatsen för den nya webbplatsen, rensa cacheminnen.
1. Ändra kundkonfiguration: **Administratör** > **Butik** > **Konfiguration** > **Kunder** > **Kundkonfiguration** > **Dela kundkonton = Global**.
1. Skapa en ny administratörsanvändarroll med rollomfånget inställt på en ny skapad webbplats *(tillgång endast till säljdata)* in **Administratör** > **System** > **Behörigheter**.
1. Skapa ett nytt administratörskonto med den här rollen.
1. Skapa ny order med onlinebetalningsmetod *(t.ex. Auth.net eller PayPal)*.
1. Logga in som en begränsad administratörsanvändare.
1. Gå till **Försäljning** > **Beställningar** > **ordervysida**.
1. Skapa en faktura.
1. Navigera till fliken Fakturor.
1. Klicka på **Faktura**.
1. Klicka på **[!UICONTROL Credit Memo]**.
1. Kontrollera **[!UICONTROL Refund to Store Credit]** kryssrutan, ange textfältet intill *1* värde.
1. Klicka på **[!UICONTROL Refund Offline]** -knappen.

<u>Förväntade resultat</u>:

Kreditnotan skapas och *$1* återbetalas till butikskrediten.

<u>Faktiska resultat</u>:

Felmeddelandet *Fler behörigheter krävs för att visa det här objektet* visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt hos Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i [!DNL Quality Patches Tool] guide.
* Adobe Commerce om molninfrastruktur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool], se:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av högklassiga patchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en patch för din Adobe Commerce-utgåva med [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra patchar som finns i QPT finns i [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool] guide.
