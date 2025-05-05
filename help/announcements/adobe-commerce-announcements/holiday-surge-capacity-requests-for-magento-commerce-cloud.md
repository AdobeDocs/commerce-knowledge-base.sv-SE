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

Vi rekommenderar att alla Adobe Commerce-handlare i vår molninfrastruktur [använder den här uppsättningen rekommendationer för hur man beräknar säsongstrafik](https://business.adobe.com/blog/how-to/the-5-ps-of-peak-season-performance-a-guide-to-preparing-your-infrastructure-for-high-traffic) för högsäsong varje år.

När du är klar med den rekommenderade beräkningen kan du fortsätta med nästa steg för att få information om hur du begär överkapacitet om ditt team har identifierat datum där du tror att du kommer att behöva ytterligare kapacitet.

**Visa historiken för dina storlekar**

Du kan visa historiken för begärda storlekar genom att begära information från din **CSM (Customer Success Manager)**.
Följande information finns för varje begäran om storleksändring:

* **Storlek på startdatum**: datum för begäran om uppstorleksändring.
* **Slutdatum för storleksändring**: det datum då klustret återgick till den tidigare storleken.
* **vCPU-storlek**: storleken på klustret efter storleken.
* **Dagar för användning**: under hur många dagar som klustret förblev uppskalat.
* **Period vCPU**: vCPU-storleken har ändrats med antalet dagar som den användes. (till exempel är vCPU-storleken 192 x 25 dagar lika med 4 800).

**Begär överkapacitet**

Adobe Commerce handlare i vår molninfrastruktur som förutser ett behov av extra kapacitet under semestersäsongen bör [skicka en supportanmälan för överkapacitet](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize.html?lang=sv-SE) via vårt [Help Center](/help/overview.md), vilket anger datum och förväntade kapacitetsbehov i biljetten. Observera att ökad kapacitet kräver att du använder den licensierade överlagringskapaciteten.

**Vi rekommenderar att du skickar dessa biljetter minst 48 arbetstimmar innan du behöver kapaciteten. Vi rekommenderar dessutom att du gör en begäran om måndag mellan fredag och måndag i svartvitt så långt som möjligt, eftersom kapaciteten under perioden är begränsad.**


**Mer hjälp?**

Behöver du mer vägledning om hur man förbereder sig för högtrafik? Adobe Commerce handlare i vår molninfrastruktur kan kontakta sitt kontoteam på Adobe för att få hjälp, strategi och planeringstips för att förbereda sig för en lyckad högsäsong. Vi rekommenderar också att du tittar på [Magento-bloggen](https://magento.com/blog) för strategitips året om.

## Resurser för att granska din kapacitet

I vår kunskapsbas:

* [Beräkning av processorallokering för Adobe Commerce i molnet](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html?lang=sv-SE)
* [Kontrollera om det krävs en uppgradering för värdinstanser för Adobe Commerce i molnet](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html?lang=sv-SE)
* [Kontrollera värddatorns processorkonfiguration för Adobe Commerce i molnet](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html?lang=sv-SE)
* [Identifiera och mät avbrott för Adobe Commerce i molnet](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html?lang=sv-SE)
