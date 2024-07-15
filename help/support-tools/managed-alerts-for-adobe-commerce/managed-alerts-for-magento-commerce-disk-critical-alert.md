---
title: 'Hanterade varningar för Adobe Commerce: diskkritisk varning'
description: I den här artikeln beskrivs felsökningsåtgärder när du får en viktig diskvarning för Adobe Commerce i New Relic. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.
exl-id: 03e5694b-7689-4fbf-8781-636fa46ca0d3
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: c829b4383fa808df29aab03229c59f06ef8a38bc
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---

# Hanterade varningar för Adobe Commerce: Diskkritisk varning

I den här artikeln beskrivs felsökningsåtgärder när du får en viktig diskvarning för Adobe Commerce i New Relic. Det krävs omedelbara åtgärder för att åtgärda problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.

![Diskkritisk varning](assets/disk-critical-magento-managed.png){width="500"}

## Berörda produkter och versioner

Adobe Commerce molninfrastruktur i Pro-planarkitekturen

## Problem

Du får en avisering i New Relic om du har registrerat upp till [Hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) och ett eller flera av aviseringströskelvärdena har överskridits. Dessa varningar utvecklades av Adobe för att ge kunderna en standarduppsättning med hjälp av insikter från support och konstruktion.

<u> **Gör!** </u>

* Avbryt all schemalagd distribution tills den här aviseringen har rensats.
* Placera platsen i underhållsläge omedelbart om platsen inte svarar eller inte svarar alls. Anvisningar finns i [Installationshandbok > Aktivera eller inaktivera underhållsläge](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) . Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Anvisningar finns i [Underhåll listan över undantagna IP-adresser](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt).

**Gör inte!**

* lansera fler marknadsföringskampanjer som kan ge er webbplats fler sidvisningar.
* Kör indexerare eller ytterligare kroner som kan orsaka ytterligare belastning på processorn eller disken.
* Utför några större administrativa uppgifter (t.ex. Commerce Admin, import/export av data).
* Rensa cachen.

Din webbplats kanske inte svarar (om du inte redan drabbas av ett avbrott i din webbplats) om du utför någon av åtgärderna&quot;Gör inte&quot; innan du har undersökt och löst orsaken till varningen.

## Lösning

Följ de här stegen för att identifiera och felsöka orsaken.

>[!WARNING]
>
>Eftersom det här är en viktig varning rekommenderar vi att du slutför **steg 1** innan du försöker felsöka problemet (steg 2 och framåt).

1. Kontrollera om Adobe Commerce supportanmälan finns. Anvisningar finns i [Spåra dina supportärenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) i vår kunskapsbas för support. Supporten kan ha tagit emot en New Relic-tröskelvarning, skapat en biljett och börjat arbeta med problemet. Om det inte finns någon biljett skapar du en. Biljetten ska ha följande information:
   * Kontaktorsak: välj&quot;New Relic CRITICAL-varning mottagen&quot;.
   * Beskrivning av aviseringen.
   * [Länk till New Relic Incident](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Detta ingår i dina [hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Granska skivorna i New Relic för användning i toppklass. Anvisningar om hur du gör detta finns på fliken Lagring på sidan New Relic [Värdar för infrastrukturövervakning:](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage)
   * Om diskanvändningen ökar långsamt i New Relic kan du prova följande alternativ:
   * Optimera diskutrymmet genom att justera utrymmesallokeringen. Anvisningar finns i [Hantera diskutrymme](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) i utvecklardokumentationen. Du kan också behöva begära mer diskutrymme (kontakta kontoteamet på Adobe).
   * Frigör diskutrymme för MySQL. Mer information finns i [MySQL-diskutrymmet är lågt](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) i vår supportkunskapsbas.
   * Om diskanvändningen snabbt ökar i New Relic kan det tyda på att det finns ett problem som har fått en fil att öka mycket snabbt i en katalog. Gör följande kontroller:
1. Kontrollera det totala diskutrymmet för att identifiera problemet genom att köra följande kommando i CLI/Terminal: `df -h`
1. När du har identifierat en katalog med oväntat stor och ökande diskanvändning måste du kontrollera det berörda filsystemet. I följande exempel visas hur du kontrollerar filkatalogen `pub/media/`. Det här är den katalog som Commerce använder för att lagra loggar och stora mediefiler. Du bör dock köra det här kommandot för alla kataloger som visar oväntad diskanvändning: `du -sch ~/pub/media/*`

Om utdata från terminalen visar en fil i någon av dessa kataloger som snabbt ökar diskanvändningen och du vet att filens innehåll inte behövs, bör du ta bort filen. Om du inte är säker på att du kan utföra den här åtgärden [skickar du en Adobe Commerce-supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
