---
title: Söker efter DDoS-attack från CLI
description: I den här artikeln behandlas frågan om hur man försöker söka efter DoS-attacker (Distributed Denial of Service) från serverns CLI (Command Line Interface).
exl-id: dfdef289-cf51-42d7-b3fb-d4d2d3760951
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 0%

---

# Söker efter DDoS-attack från CLI

I den här artikeln behandlas frågan om hur man försöker söka efter DoS-attacker (Distributed Denial of Service) från serverns CLI (Command Line Interface).

## Berörda produkter och versioner

* Adobe Commerce, alla versioner
* Magento Open Source, alla versioner

## Problem

Webbplatsen är långsam och du har inte tillgång till några andra analysverktyg, förutom CLI, för att kontrollera om det finns en potentiell DDoS-attack. Symtomen på en DoS-attack kan variera mycket beroende på nätverkskonfigurationen, vilken programvara som används osv.

Vi rekommenderar dock att du använder analysprogram som är särskilt utformade för att identifiera DDoS-attacker.

## Orsak

Det finns flera möjliga orsaker till en långsam webbplats, bland annat en server med långsam prestanda, hög processoranvändning eller felkonfigurering av skript, kod eller billig maskinvara. Ibland kan det bero på en DDoS-attack. Två av de grundläggande verktygen du måste använda för att söka efter DDoS-attacker är dina Adobe Commerce-loggar och din CLI.

Det är viktigt att komma ihåg att det skulle vara mycket användbart att använda program som är särskilt utformade för att identifiera DDoS-attacker i din utredning.

## Lösningssteg

1. Kontrollera om det finns något annat än en DDoS-attack i Adobe Commerce loggar. Mer information finns i följande artiklar i utvecklardokumentationen:
   * [Adobe Commerce och Magento Open Source loggar platser](https://devdocs.magento.com/guides/v2.3/config-guide/cli/logging.html)
   * [Adobe Commerce på platser för molninfrastrukturloggar](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html)
1. Börja använda CLI för att kontrollera alla dina nuvarande internetanslutningar med `netstat` kommando: `netstat -na`. Detta visar alla aktiva etablerade anslutningar till servern. Här kan du kanske lägga märke till att för många anslutningar kommer från samma IP-adress.
1. Använd det här kommandot om du vill begränsa dina etablerade anslutningsresultat ytterligare till endast de som ansluter på port 80 (webbplatsens http-port), så att du kan sortera och identifiera för många anslutningar från en IP-adress eller grupp med IP-adresser: `netstat -an | grep :80 | sort`. Du kan upprepa samma kommando för https på port 443: `netstat -an | grep :443 | sort`. Ett annat alternativ är att utöka det ursprungliga kommandot till både port 80 och 443: `netstat -an | egrep ":80|:443" | sort`.
1. För att se om många är aktiva `SYNC_REC` används på servern med kommandot:     `netstat -n -p|grep SYN_REC | wc -l`     Detta är vanligtvis mindre än 5, men det kan vara mycket högre för en DDoS-attack, men för vissa servrar kan ett högre antal vara ett normalt tillstånd.
1. Visa alla IP-adresser som skickar `SYNC_REC` -status, använd kommandot: `netstat -n -p | grep SYN_REC | sort -u`.
1. Om du vill visa fler unika IP-adresser som skickar `SYNC_REC` -status, använd kommandot: `netstat -n -p | grep SYN_REC | awk ‘{print $5}’ | awk -F: ‘{print $1}’`.
1. Du kan också använda `netstat` för att räkna och beräkna antalet anslutningar som varje IP-adress gör till servern: `netstat -ntu | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. Om du vill visa antalet UDP- eller TCP-protokollanslutningar som är anslutna till servern använder du kommandot: `netstat -anp |grep ‘tcp|udp’ | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. Om du vill kontrollera etablerade anslutningar i stället för bara alla anslutningar och visa antalet anslutningar för varje IP-adress använder du kommandot: `netstat -ntu | grep ESTAB | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -nr`.
1. Om du vill visa antalet anslutningar som anges av IP-adressen till port 80 använder du kommandot: `netstat -plan|grep :80|awk {‘print $5’}|cut -d: -f 1|sort|uniq -c|sort -nk 1`.

Se till att du har någon som kan analysera de data du hittar för att avgöra om du faktiskt har en DDoS-attack. Använda `netstat` kommandon från serverns CLI i de här stegen ovan hjälper dig att analysera om du drabbas av en DDoS-attack, men med programanalysprodukter som är särskilt utformade för att identifiera DDoS-attacker, tillsammans med korrekt analys, är de bästa verktygen för att identifiera DDoS-hot.

Om du råkar ut för ett DDoS-angrepp beror de åtgärder du kan vidta på nätverkskonfigurationen och hur DDoS-attacken inträffar, men du bör kontakta din Internet-leverantör, skaffa en ny IP-adress till servern och/eller kontakta IT-personal som är skicklig på att hantera DDoS-problem för att analysera och ge råd om din specifika situation.

## Relaterade läsningar i vår dokumentation för utvecklare:

* [DDoS-skydd](https://devdocs.magento.com/guides/v2.3/cloud/cdn/cloud-fastly.html#ddos-protection)
* [Använda CLI-kommandon](https://devdocs.magento.com/guides/v2.3/config-guide/deployment/pipeline/example/cli.html)
* [Cloud CLI för Commerce](https://devdocs.magento.com/guides/v2.3/cloud/reference/cli-ref-topic.html)
