---
title: 'Hanterade varningar på Adobe Commerce: Redis Memory Warning'
description: 'I den här artikeln finns felsökningsanvisningar för när du får en Redis-varning för Adobe Commerce i New Relic. Du måste vidta omedelbara åtgärder för att lösa problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt:'
exl-id: b7867a42-3817-4cb4-93cf-d69acee33a41
feature: Categories, Marketing Tools, Observability, Services, Support, Tools and External Services, Variables
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Hanterade varningar på Adobe Commerce: Redis Memory Warning

I den här artikeln finns felsökningsanvisningar för när du får en Redis-varning för Adobe Commerce i New Relic. Du måste vidta omedelbara åtgärder för att lösa problemet. Varningen ser ut ungefär så här, beroende på vilken meddelandekanal du valt:

![new_relic_redis_memory_warning.png](assets/new_relic_redis_memory_warning.png)

## Berörda produkter och versioner

Alla versioner av Adobe Commerce på Cloud Infrastructure Pro-planarkitekturen.

## Problem

Du får en avisering i New Relic om du har registrerat upp till [Hanterade aviseringar för Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) och ett eller flera av aviseringströskelvärdena har överskridits. Dessa varningar har utvecklats av Adobe för att ge handlarna en standarduppsättning med hjälp av insikter från support och konstruktion.

**<u>Gör!</u>**

* Vi rekommenderar att du avbryter alla schemalagda distributioner tills den här aviseringen har rensats.
* Om din webbplats inte svarar eller inte svarar alls ska du omedelbart försätta platsen i underhållsläge. Anvisningar finns i [Installationshandboken > Aktivera eller inaktivera underhållsläge](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#enable-or-disable-maintenance-mode-1) i installationshandboken.
* Se till att du lägger till din IP-adress i listan över undantagna IP-adresser för att vara säker på att du fortfarande kan komma åt din webbplats för felsökning. Anvisningar finns i [Underhåll listan över undantagna IP-adresser](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#maintain-the-list-of-exempt-ip-addresses) i vår installationshandbok.

**<u>Gör inte!</u>**

* lansera fler marknadsföringskampanjer som kan ge er webbplats fler sidvisningar.
* Kör indexerare eller ytterligare kroner som kan orsaka ytterligare belastning på processorn eller disken.
* Utför alla större administrativa uppgifter (dvs. större åtgärder i Commerce Admin, t.ex. import/export av data, tömning av media, sparande av kategorier med ett stort antal tilldelade produkter och massuppdateringar).
* Rensa cachen.

## Lösning

Följ de här stegen för att identifiera och felsöka orsaken.

1. Kontrollera om Redis Used Memory ökar eller minskar genom att gå till sidan [one.newrelic.com](https://login.newrelic.com/login) > **Infrastructure** > **Tredjepartstjänster** och välj Redis-instrumentpanelen. Om det är stabilt eller ökar [skickar du en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) så att klustret storleksändras, eller ökar `maxmemory`-gränsen till nästa nivå.
1. Om du inte kan identifiera orsaken till den ökade Redis-minnesförbrukningen kan du granska aktuella trender för att identifiera problem med nyligen använda koddistributioner eller konfigurationsändringar (till exempel nya kundgrupper och stora ändringar i katalogen). Vi rekommenderar att du granskar de senaste sju dagarnas aktivitet för att se eventuella samband i koddistributioner eller ändringar.
1. Kontrollera om det finns tillägg från tredje part som inte fungerar som de ska:
   * Försök att hitta ett samband med nyligen installerade tillägg från tredje part och när problemet uppstod.
   * Granska tillägg som kan påverka cacheminnet i Adobe Commerce och få cacheminnet att växa snabbt. Exempel: anpassade layoutblock, åsidosätta cachefunktioner och lagra stora mängder data i cache.
1. Om det inte finns några tecken på att tillägg är felaktiga [Installera de senaste korrigeringarna för att åtgärda Redis-problem för Adobe Commerce i molninfrastrukturen](/help/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues.md). Om ovanstående steg inte hjälper dig att identifiera eller felsöka problemkällan bör du överväga att aktivera L2-cache för att minska nätverkstrafiken mellan appen och Redis. Allmän information om vad som är L2-cache finns i [L2-cachning i Adobe Commerce-programmet](/docs/commerce-operations/configuration-guide/cache/level-two-cache.html) i vår konfigurationshandbok. Så här aktiverar du L2-cache för molninfrastruktur:
   * Uppgradera ECE-verktygen om de är under version 2002.1.2.
   * Konfigurera L2-cache genom att använda [Använd REDIS\_BACKEND-variabeln](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) och uppdatera `.magento.env.yaml`-filen:

   ```yaml
   stage:
      deploy:
          REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
