---
title: 'Hanterade varningar för Adobe Commerce: diskvarning'
description: I den här artikeln beskrivs felsökningssteg när du får en varning för Adobe Commerce i New Relic. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.
exl-id: 07b34db1-11ec-4cf2-ae47-cfc067f91383
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# Hanterade varningar för Adobe Commerce: diskvarning

I den här artikeln beskrivs felsökningssteg när du får en varning för Adobe Commerce i New Relic. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.

![diskvarning](assets/disk-warning-magento-managed.png){width="500"}

## Berörda produkter och versioner

* Adobe Commerce om molninfrastruktur, Pro-planarkitektur.

## Problem

Du får en avisering i New Relic om du har registrerat upp till [Hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) och ett eller flera av aviseringströskelvärdena har överskridits. Dessa varningar utvecklades av Adobe för att ge kunderna en standarduppsättning med hjälp av insikter från support och konstruktion.

<u> **Gör!** </u>

* Avbryt all schemalagd distribution tills den här aviseringen har rensats.
* Placera platsen i underhållsläge omedelbart om platsen inte svarar eller inte svarar alls. Anvisningar om hur du gör detta finns i [Installationshandbok > Aktivera eller inaktivera underhållsläge](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) i utvecklardokumentationen. Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Anvisningar finns i [Underhåll listan över undantagna IP-adresser](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) i utvecklardokumentationen.

<u> **Gör inte!** </u>

* lansera fler marknadsföringskampanjer som kan ge er plats fler sidvisningar.
* Kör indexerare eller ytterligare kroner som kan orsaka ytterligare belastning på processorn eller disken.
* Utför några större administrativa uppgifter (t.ex. Commerce Admin, import/export av data).
* Rensa cachen. Din webbplats kanske inte svarar (om du inte redan drabbas av ett avbrott i din webbplats) om du utför någon av åtgärderna&quot;Gör inte&quot; innan du har undersökt och löst orsaken till varningen.

## Lösning

Följ de här stegen för att identifiera och felsöka orsaken:

1. Granska skivorna i New Relic för användning i toppklass. Anvisningar om hur du gör detta finns på fliken Lagring på New Relic [värdsida för infrastrukturövervakning](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/):
   * Om diskanvändningen ökar långsamt i New Relic kan du prova följande alternativ:
   * Optimera diskutrymmet genom att justera utrymmesallokeringen. Anvisningar finns i [Hantera diskutrymme](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) i utvecklardokumentationen. Du kan också behöva begära mer diskutrymme (kontakta kontoteamet på Adobe).
   * Frigör diskutrymme för MySQL. Gå till [MySQL-diskutrymmet är lågt](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) för steg.
   * Om diskanvändningen snabbt ökar i New Relic kan det tyda på att det finns ett problem som har fått en fil att öka mycket snabbt i en katalog. Gör följande kontroller:
1. Kontrollera det totala diskutrymmet för att identifiera problemet genom att köra följande kommando i CLI/Terminal: `df -h`
1. När du har identifierat en katalog med oväntat stor och ökande diskanvändning måste du kontrollera det berörda filsystemet. I följande exempel visas hur du kontrollerar filkatalogen `pub/media/`. Det här är den katalog som Adobe Commerce använder för att lagra loggar och stora mediefiler. Du bör dock köra det här kommandot för alla kataloger som visar oväntad diskanvändning: `du -sch ~/pub/media/*`.

Om utdata från terminalen visar en fil i någon av dessa kataloger som snabbt ökar diskanvändningen och du vet att filens innehåll inte behövs, bör du ta bort filen. Om du inte är säker på att du kan utföra den här åtgärden [skickar du en Adobe Commerce-supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
