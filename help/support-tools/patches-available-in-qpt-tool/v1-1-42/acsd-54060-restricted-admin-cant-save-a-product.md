---
title: 'ACSD-54060: Begränsad administratör kan inte spara produkten om den är underordnad en annan produkt'
description: Använd patchen ACSD-54060 för att åtgärda Adobe Commerce-problemet där en begränsad administratör inte kan spara en produkt om den är underordnad en annan produkt som tilldelats ett annat omfång.
feature: Admin Workspace, Roles/Permissions, Products
role: Admin, Developer
exl-id: 28fa3c99-f2b6-4c6d-955a-bd6638a1b077
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-54060: Begränsad administratör kan inte spara produkten om den är underordnad en annan produkt

Korrigeringen ACSD-54060 åtgärdar ett problem där en begränsad administratör inte kan spara en produkt om den är underordnad en annan produkt som tilldelats ett annat omfång. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 har installerats. Korrigerings-ID är ACSD-54060. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En begränsad administratör kan inte spara en produkt om den är underordnad en annan produkt som har tilldelats ett annat omfång.

<u>Steg som ska återskapas</u>:

1. Skapa ytterligare en webbplats.
1. Skapa en enkel produkt och tilldela den till båda webbplatserna.
1. Skapa en konfigurerbar produkt med den enkla produkten som enda variant och tilldela endast den konfigurerbara produkten till standardwebbplatsen.
1. Skapa en begränsad administratörsanvändare med endast åtkomst till den andra webbplatsen.
1. Logga in som begränsad administratörsanvändare.
1. Försök att ändra det enkla produktnamnet i det andra webbplatsomfånget.

<u>Förväntade resultat</u>:

Den begränsade administratören kan ändra produktnamnet.

<u>Faktiska resultat</u>:

Ett fel inträffar: *Fler behörigheter krävs för att visa det här objektet*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
