---
title: Uppdatering av livscykelpolicy för Adobe Commerce Support-biljetter
description: I den här artikeln finns information om uppdatering av Adobe Commerce supportbiljettens livscykelpolicy.
exl-id: c3fbcb4a-107f-48b3-afed-b9a0c5d0425c
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 1%

---

# Uppdatering av livscykelpolicy för Adobe Commerce Support-biljetter

I den här artikeln finns information om uppdatering av Adobe Commerce supportbiljettens livscykelpolicy.

Följande tabell visar de uppdaterade scenarierna. Du hittar information om varje scenario i avsnittet nedan.

<table>
 <tbody>
 <tr>
 <td class="wysiwyg-text-align-center"> </td>
 <td class="wysiwyg-text-align-center"><strong>Biljettstatus</strong></td>
 <td class="wysiwyg-text-align-center"><strong>Dagar till "Löst"</strong></td>
 <td class="wysiwyg-text-align-center"><strong>Dagar till"Stängd"</strong></td>
 <td class="wysiwyg-text-align-center"><strong>Tidsinställning</strong></td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>Teknikern tillhandahåller en lösning</strong></td>
 <td class="wysiwyg-text-align-center">"Väntar på ditt svar"</td>
 <td class="wysiwyg-text-align-center">3</td>
 <td class="wysiwyg-text-align-center">6</td>
 <td class="wysiwyg-text-align-center">Dagar 3 och 6</td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>Väntar på information från kund</strong></td>
 <td class="wysiwyg-text-align-center">"Väntar på ditt svar"</td>
 <td class="wysiwyg-text-align-center">Ej tillämpligt</td>
 <td class="wysiwyg-text-align-center">6</td>
 <td class="wysiwyg-text-align-center">Dagar 1, 3 och 6</td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>Kunden anger till"Löst" eller begär att teknikern ska ange till"Löst"</strong></td>
 <td class="wysiwyg-text-align-center">"Löst"</td>
 <td class="wysiwyg-text-align-center">Omedelbar</td>
 <td class="wysiwyg-text-align-center">1</td>
 <td class="wysiwyg-text-align-center">Dag 1</td>
 </tr>
 </tbody>
 </table>

## Detaljerade scenarier

### När en tekniker tillhandahåller en lösning

1. När kunden fått en lösning anger teknikern biljettstatus till&quot;Väntar på svar&quot;.
1. Om kunden inte svarar inom 3 dagar efter att statusen ändrats till&quot;Väntar på ditt svar&quot; flyttas biljetten till&quot;Löst&quot; och kunden meddelas.
1. Om kunden inte svarar inom 6 dagar efter att statusen ändrats till&quot;Väntar på ditt svar&quot; stängs biljetten och kunden meddelas.

### När ytterligare information krävs från en kund

1. Om det krävs en uppdatering från kunden sätter teknikern biljetten till&quot;Väntar på ditt svar&quot;.
1. Meddelanden skickas till kunden dag 1 och dag 3 som begär uppföljning av kunden.
1. Om kunden inte svarar inom 6 dagar efter att statusen ändrats till&quot;Väntar på ditt svar&quot; stängs biljetten och kunden meddelas.

### Biljetten är inställd på&quot;Löst&quot; av en kund

När en biljett är inställd på&quot;Löst&quot; av en kund stängs den om en dag och kunden meddelas.

### Kunden instruerar supporten att stänga biljetten

När en kund ber Adobe Commerce Support att stänga biljetten stängs den om en dag och kunden meddelas.

## Relaterad läsning

* [Skicka en supportanmälan](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)
* [Länken Skicka en biljett visas inte på startsidan för Adobe Commerce Help Center](/help/help-center-guide/help-center/magento-help-center-user-guide.md#no-submit-link)
* [Formulär för att skicka biljetter: handlaren visas inte i den nedrullningsbara listan Organisation](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed)
