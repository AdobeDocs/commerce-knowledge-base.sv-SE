---
title: Förfrågningar om överkapacitet på heldag för Adobe Commerce i vår molninfrastruktur
description: Under högsädessäsongen (ungefär mellan mitten november och mitten av januari) rekommenderar Adobe att alla Adobe Commerce handlare som är värdar i vår molninfrastruktur förbereder sig för ökad trafik.
exl-id: 9d6910bf-30bc-4117-bf7f-a0316f9506b5
feature: Cloud, Paas
role: Admin
source-git-commit: 357e0acb1c849079ff0fe9f53fe386f60475c7f9
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# Förfrågningar om överkapacitet på heldag för Adobe Commerce i vår molninfrastruktur

Under högsädessäsongen (ungefär mellan mitten november och mitten av januari) rekommenderar Adobe att alla Adobe Commerce handlare som är värdar i vår molninfrastruktur förbereder sig för ökad trafik.

**Planerings- och utvärderingstrafik**

Vi rekommenderar alla Adobe Commerce-handlare i vår molninfrastruktur [använda den här uppsättningen rekommendationer för hur man beräknar trafik för högsäsong](https://business.adobe.com/blog/how-to/the-5-ps-of-peak-season-performance-a-guide-to-preparing-your-infrastructure-for-high-traffic) för högsädessäsong varje år.

När du är klar med den rekommenderade beräkningen kan du fortsätta med nästa steg för att få information om hur du begär överkapacitet om ditt team har identifierat datum där du tror att du kommer att behöva ytterligare kapacitet.

**Visa historiken för dina uppgraderingar**

Du kan visa historiken för begärda storlekar genom att begära information från **CSM (kundframgångsansvarig)**.
Följande information finns för varje begäran om storleksändring:

* **Storlek på startdatum**: datum för begäran om uppgradering.
* **Slutdatum för storlek**: datum när klustret återgick till den tidigare storleken.
* **vCPU-storlek**: storleken på klustret efter uppstorleken.
* **Dagar, användning**: om du vill se hur många dagar klustret förblev större.
* **Period vCPU**: ändrad vCPU-storlek med antalet dagar som användes. (till exempel är vCPU-storleken 192 x 25 dagar lika med 4 800).

**Begär överkapacitet**

Adobe Commerce handlare i vår molninfrastruktur som förutser ett behov av extra kapacitet under semestersäsongen bör [skicka en supportanmälan för överkapacitet](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize.html) via vår [Help Center](/help/overview.md), som anger datum och förväntade kapacitetsbehov inom biljetten. Observera att ökad kapacitet kräver att du använder den licensierade överlagringskapaciteten.

**Vi rekommenderar att man skickar in dessa biljetter minst 48 arbetstimmar innan man behöver kapacitet och dessutom rekommenderar att man så långt som möjligt lägger begäran om Black Friday/Cyber Monday-perioden, eftersom kapaciteten under denna period är begränsad.**


**Mer hjälp?**

Behöver du mer vägledning om hur man förbereder sig för högtrafik? Adobe Commerce handlare i vår molninfrastruktur kan kontakta sitt kontoteam på Adobe för att få hjälp, strategi och planeringstips för att förbereda sig för en lyckad högsäsong. Vi rekommenderar även att du checkar ut [Magento blogg](https://magento.com/blog) för strategitips året om.

## Resurser för att granska din kapacitet

I vår kunskapsbas:

* [Beräkning av processorallokering för Adobe Commerce i molnet](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
* [Kontrollera om det krävs en uppstorlek för värdinstanserna för Adobe Commerce i molnet](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
* [Kontrollera värddatorns CPU-konfiguration för Adobe Commerce i molnet](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* [Identifiera och mät avbrott för Adobe Commerce i molnet](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html)
