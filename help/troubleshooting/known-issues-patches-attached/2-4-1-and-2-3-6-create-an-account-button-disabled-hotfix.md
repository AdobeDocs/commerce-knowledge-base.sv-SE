---
title: Adobe Commerce 2.4.1 och 2.3.6 skapar en snabbkorrigering för inaktiverad kontoknapp
description: Den här artikeln innehåller en snabbkorrigering för problemet när du har svårt att skapa ett nytt konto efter att ha angett ett felaktigt värde för ett fält i formuläret. Om du t.ex. anger en e-postadress i fel format, lämnar fälten för förnamn eller efternamn tomma eller inte anger något värde som uppfyller lösenordskraven. En permanent fix kommer att ingå i Q1-versionerna (2.4.2, 2.4.1-p1 och 2.3.6-p1).
exl-id: e6e65ede-8156-4e2b-b369-b18395bb3dbf
feature: Customer Service
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 och 2.3.6 skapar en snabbkorrigering för inaktiverad kontoknapp

Den här artikeln innehåller en snabbkorrigering för problemet när du har svårt att skapa ett nytt konto efter att ha angett ett felaktigt värde för ett fält i formuläret. Om du t.ex. anger en e-postadress i fel format, lämnar fälten för förnamn eller efternamn tomma eller inte anger något värde som uppfyller lösenordskraven. En permanent fix kommer att ingå i Q1-versionerna (2.4.2, 2.4.1-p1 och 2.3.6-p1).

## Problem

Knappen **Skapa ett konto** på sidan **Skapa nytt konto** är inaktiverad om en kund har angett ogiltiga data. Detta förhindrar att kunderna försöker återskapa ett konto efter att ha gjort ett fel.

<u>Steg som ska återskapas</u>:

1. Gå till **Skapa nytt kundkonto**.
1. Fyll i formulärfälten. I fältet **Lösenord** anger du indatavärden som inte uppfyller lösenordskraven. Exempel:
   * Lösenorden i fälten **Lösenord** och **Bekräfta lösenord** matchar inte.
   * Lösenorden i fälten **Lösenord** och **Bekräfta lösenord** är inte tillräckligt långa.
1. Klicka på knappen **Skapa ett konto**.

<u>Förväntade resultat</u>:

* Knappen **Skapa ett konto** ska förbli aktiv/aktiverad.
* Användaren bör kunna skapa ett nytt konto.

<u>Faktiska resultat</u>:

* Knappen **Skapa ett konto** är inaktiverad även om alla obligatoriska fält har fyllts i med giltiga/korrekta data.
* Kunden kan inte skapa ett nytt konto.

## Lappa

Korrigeringen är kopplad till den här artikeln. Om du vill hämta den bläddrar du nedåt till slutet av artikeln och klickar på filnamnet eller klickar på följande länk: [Download MC-38509-comser.patch](assets/MC-38509-composer.patch.zip)

## Kompatibla Adobe Commerce-versioner:

Korrigeringen skapades för:

* Adobe Commerce om molninfrastruktur 2.3.6 och 2.4.1.
* Adobe Commerce lokalt 2.3.6 och 2.4.1.

Korrigeringen är inte kompatibel med andra Adobe Commerce-versioner och -utgåvor.

## Så här använder du patchen

Mer information finns i [Använda en dispositionsruta från Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## Relaterad läsning

* [GitHub Adobe Commerce > Skickar ogiltigt formulär för att skapa konto, men skicka-knappen är inaktiverad](https://github.com/magento/magento2/issues/30513)
* [Adobe Commerce Användarhandbok > Komma igång > Skapa ett konto](https://experienceleague.adobe.com/en/docs/commerce-admin/start/commerce-account/commerce-account-create)
