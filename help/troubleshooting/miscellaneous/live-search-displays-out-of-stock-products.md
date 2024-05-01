---
title: '[!DNL Live Search] visar ej lagerförda produkter oavsett inställningarna för lagerstatus i admin'
description: Den här artikeln innehåller information om det kända problemet där PLP (Product Listing Page) visar *Vi kan inte hitta produkter som matchar felet* medan sökleverantören returnerar några objekt.
exl-id: 2a351b83-407c-444a-a761-4932b5b88843
feature: Admin Workspace, Categories, Orders, Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# [!DNL Live Search] visar ej lagerförda produkter oavsett inställningarna för lagerstatus i administratören

>[!IMPORTANT]
>
>Problemet har åtgärdats i [[!DNL Live Search] [2.0.4]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html). För att installera den senaste versionen, se [Uppdaterar [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#update) i användarhandboken.

I den här artikeln finns information om kända fel där produktlistningssidan (PLP) visar *Det går inte att hitta produkter som matchar markeringen* fel när sökleverantören returnerar vissa objekt.

## Berörda produkter och versioner

Adobe Commerce (alla distributionsmetoder) 2.4.x

## Problem

[!DNL Live Search] visar sökresultat oavsett inställningarna för Stock-status i Adobe Commerce Admin. Även när **[!UICONTROL Display Out-of-Stock Products]** är inställd på *Nej* visas produkterna. Resultatet blir ett PLP-fel *Det går inte att hitta produkter som matchar markeringen*.

<u>Steg som ska återskapas</u>:

1. Skapa en kategori och lägg till produkter. (Exempel: Kategori = _Jeans_, Produkt1 = _Blå jeans_, Produkt2 = _Black Jeans_)
1. Gör alla produkter i kategorin utanför lagret.
1. Ange **[!UICONTROL Display Out-of-Stock Products]** till *Nej*.
1. I butiken anger du *Jeans* i sökfältet.
1. Klicka **[!UICONTROL View All]** i popup-fönstret.

<u>Förväntat resultat</u>:

Du ser *Det går inte att hitta produkter som matchar markeringen* på PLP och inga produkter visas i sökfönstret.

<u>Faktiskt resultat</u>:

Du ser *Det går inte att hitta produkter som matchar markeringen* på PLP, och båda produkterna visas i sökfönstret.

## Lösning

Det finns för närvarande ingen lösning på det här problemet. Våra [!DNL Live Search] kommer snart att tillhandahålla en inställning för att konfigurera [!DNL Live Search] för att visa produkterna korrekt.

## Relaterad läsning

[Installera [!DNL Live Search]](https://docs.magento.com/user-guide/live-search/install.html) i vår användarhandbok.
