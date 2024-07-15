---
title: Slut på minne under installation eller uppgradering
description: I den här artikeln behandlas lösningar för fel när minnet tar slut vid installation/uppgradering av Adobe Commerce lokala produkter och produkter från Magento Open Source.
exl-id: c0ed8228-9357-4a3b-a102-1119386ea52a
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Slut på minne under installation eller uppgradering

I den här artikeln behandlas lösningar för fel när minnet tar slut vid installation/uppgradering av Adobe Commerce lokala produkter och produkter från Magento Open Source.

## Berörda produkter och versioner

* Adobe Commerce lokal 2.3.x
* Magento Open Source lokal 2.3.x

## Problem

När du installerar eller uppdaterar Adobe Commerce- eller Magento Open Source-program eller -komponenter som tillägg, teman eller språkpaket med hjälp av Web Setup Wizard visas ett fel som liknar det som visas nedan:

```bash
Could not complete update {"components":[
{"name":"magento/module-bundle-sample-data","version":"100.1.0"}
]} successfully: proc_open(): fork failed - Cannot allocate memory
```

Felet

```bash
proc_open(): fork failed - Cannot allocate memory
```

kan även visas på kommandoraden.

## Lösning {#solution}

Vi rekommenderar att du [tilldelar 2 GB minne till PHP](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) i vår utvecklardokumentation för att vara säker på att installationen eller uppgraderingen lyckas.

Om du redan har gjort det skapar du en växlingsfil på datorn. En Linux-dator använder *växlingsutrymme* om den behöver mer minnesresurser och RAM-minnet är fullt. Växlingsutrymmet används för inaktiva sidor i minnet.

Följande är endast förslag, andra alternativ kan vara tillgängliga. Kontakta en nätverksadministratör eller en annan kunskapsbar resurs innan du fortsätter. Du måste köra kommandona för att skapa en utbytesfil som en användare med `root`-behörighet.

### Växla fil på Ubuntu {#swap-file-on-ubuntu}

Använd kommandot `fallocate` enligt följande referenser:

* [Så här lägger du till växel i Ubuntu 14.04 (Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)
* [Så här lägger du till växlingsutrymme i Ubuntu 16.04 (Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04)
* [SwapFAQ (help.ubuntu.com)](https://help.ubuntu.com/community/SwapFaq)

### Växla fil på CentOS {#swap-file-on-centos}

Använd kommandot `mkswap` enligt följande referenser:

* [Så här lägger du till växel i CentOS 6 (digitalt hav)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-6)
* [Så här lägger du till växel i CentOS 7 (digitalt hav)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-7)
* [Växlingsutrymme (kundportalen RedHat)](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ch-swapspace.html)
