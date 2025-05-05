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

Korrigeringen ACSD-51907 åtgärdar prestandaproblemet där den begränsade administratörsanvändaren inte kan skapa en kreditnota med en offlineåterbetalning. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.33 har installerats. Korrigerings-ID är ACSD-51907. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Begränsad administratörsanvändare kan inte skapa en kreditnota med offlineåterbetalning.

<u>Steg som ska återskapas</u>:

1. Skapa en **kund** på standardwebbplatsen.
1. Skapa **ny webbplats** med relaterad *butiksvy* och *butiksvy*.
1. Ange standardwebbplatsen för den nya webbplatsen, rensa cacheminnen.
1. Ändra kundkonfiguration: **Admin** > **Store** > **Konfiguration** > **Kunder** > **Kundkonfiguration** > **Dela kundkonton = Global**.
1. Skapa en ny administratörsanvändarroll med rollomfånget inställt på den nya skapade webbplatsen *(endast åtkomst till säljdata)* i **Admin** > **System** > **Behörigheter**.
1. Skapa ett nytt administratörskonto med den här rollen.
1. Skapa ny order med onlinebetalningsmetod *(t.ex. Auth.net eller PayPal)*.
1. Logga in som en begränsad administratörsanvändare.
1. Gå till **Försäljning** > **Beställningar** > **ordervy**.
1. Skapa en faktura.
1. Navigera till fliken Fakturor.
1. Klicka på **Faktura**.
1. Klicka på **[!UICONTROL Credit Memo]**.
1. Markera kryssrutan **[!UICONTROL Refund to Store Credit]** och ställ in textfältet intill värdet **.
1. Klicka på knappen **[!UICONTROL Refund Offline]**.

<u>Förväntade resultat</u>:

Kreditnotan skapas och *$1* återbetalas till butikskrediten.

<u>Faktiska resultat</u>:

Felmeddelandet *Fler behörigheter krävs för att visa objektet* visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
