---
title: 'Hanterade varningar på Adobe Commerce: Redis-minneskritisk varning'
description: I den här artikeln finns felsökningsanvisningar för när du får en Redis-varning om minneskritisk status för Adobe Commerce i New Relic. Du måste vidta omedelbara åtgärder för att lösa problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.
exl-id: 28e1d879-d7ca-4439-8e81-52a1fbf3ecb0
feature: Cache, Categories, Observability, Services, Support, Tools and External Services, Variables
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 0%

---

# Hanterade varningar på Adobe Commerce: Redis-minneskritisk varning

I den här artikeln finns felsökningsanvisningar för när du får en Redis-varning om minneskritisk status för Adobe Commerce i New Relic. Du måste vidta omedelbara åtgärder för att lösa problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt.

![new_relic_redis_memory_critical.png](assets/new_relic_redis_memory_critical.png)

## Berörda produkter och versioner

Alla versioner av Adobe Commerce om molninfrastruktur Pro planarkitektur

## Problem

Du får en avisering i New Relic om du har registrerat upp till [Hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) och ett eller flera av aviseringströskelvärdena har överskridits. Dessa varningar har utvecklats av Adobe för att ge handlarna en standarduppsättning med hjälp av insikter från support och konstruktion.

**<u>Gör!</u>**

* Avbryt all schemalagd distribution tills den här aviseringen har rensats.
* Placera platsen i underhållsläge omedelbart om platsen inte svarar eller inte svarar alls. Anvisningar om hur du gör detta finns i [Installationshandbok > Aktivera eller inaktivera underhållsläge](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#enable-or-disable-maintenance-mode-1) i installationshandboken. Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Anvisningar finns i [Underhåll listan över undantagna IP-adresser](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#maintain-the-list-of-exempt-ip-addresses) i vår installationshandbok.

**<u>Gör inte!</u>**

* lansera fler marknadsföringskampanjer som kan ge er webbplats fler sidvisningar.
* Kör indexerare eller ytterligare kroner som kan orsaka ytterligare belastning på processorn eller disken.
* Utför alla större administrativa uppgifter (dvs. större åtgärder i Commerce Admin, t.ex. import/export av data, tömning av media, sparande av kategorier med ett stort antal tilldelade produkter och massuppdateringar).
* Rensa cachen.

## Lösning

Följ de här stegen för att identifiera och felsöka orsaken.

**Eftersom det här är en viktig varning rekommenderar vi att du slutför steg 1 innan du försöker felsöka problemet (steg 2 och framåt).**

1. Kontrollera om Adobe Commerce supportanmälan finns. Anvisningar finns i [Spåra dina supportärenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) i vår kunskapsbas för support. Supporten kan redan ha fått en New Relic-tröskelvarning, skapat en biljett och börjat arbeta med problemet. Om det inte finns någon biljett skapar du en. Biljetten ska ha följande information:

   * Kontaktorsak: välj&quot;New Relic CRITICAL-varning mottagen&quot;.
   * Beskrivning av aviseringen.
   * [New Relic-incidentlänk](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents/). Detta ingår i dina [hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).

1. Om det inte finns någon supportanmälan kontrollerar du om Redis Used Memory ökar eller minskar genom att gå till sidan [one.newrelic.com](https://login.newrelic.com) > **Infrastructure** > **Third party services** (Tjänster från tredje part) och välja kontrollpanelen i Redis. Om det är stabilt eller ökar [skickar du en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) så att klustret storleksändras, eller ökar `maxmemory`-gränsen till nästa nivå.
1. Om du inte kan identifiera orsaken till den ökade Redis-minnesförbrukningen kan du granska aktuella trender för att identifiera problem med nyligen använda koddistributioner eller konfigurationsändringar (till exempel nya kundgrupper och stora ändringar i katalogen). Vi rekommenderar att du granskar de senaste sju dagarnas aktivitet för att se eventuella samband i koddistributioner eller ändringar.
1. Kontrollera om det finns tillägg från tredje part som inte fungerar som de ska:

   * Försök att hitta ett samband med nyligen installerade tillägg från tredje part och när problemet uppstod.
   * Granska tillägg som kan påverka cacheminnet i Adobe Commerce och få cacheminnet att växa snabbt. Exempel: anpassade layoutblock, åsidosätta cachefunktioner och lagra stora mängder data i cache.

1. Om det inte finns några tecken på att tillägg är felaktiga [Installera de senaste korrigeringarna för att åtgärda Redis-problem för Adobe Commerce i molninfrastrukturen](/help/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues.md).
1. Om ovanstående steg inte hjälper dig att identifiera eller felsöka problemkällan bör du överväga att aktivera L2-cache för att minska nätverkstrafiken mellan appen och Redis. Allmän information om vad som är L2-cache finns i [L2-cachning i Adobe Commerce-programmet](/docs/commerce-operations/configuration-guide/cache/level-two-cache.html) i utvecklardokumentationen. Så här aktiverar du L2-cache för molninfrastruktur:

   * Uppgradera ECE-verktygen om de är under version 2002.1.2.
   * Konfigurera L2-cache genom att använda [Använd REDIS\_BACKEND-variabeln](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) och uppdatera `.magento.env.yaml`-filen:

   ```yaml
   stage:
       deploy:
           REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
