---
title: '[!DNL Live Search] visar färdiga produkter oavsett inställningarna för Stock-status i admin'
description: Den här artikeln innehåller information om det kända problemet där PLP (Product Listing Page) visar *Vi kan inte hitta produkter som matchar felet* medan sökleverantören returnerar några objekt.
exl-id: 2a351b83-407c-444a-a761-4932b5b88843
feature: Admin Workspace, Categories, Orders, Products, Search
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# [!DNL Live Search] visar produkter som inte finns i lager oavsett inställningarna för Stock-status i administratören

>[!IMPORTANT]
>
>Problemet har åtgärdats i [[!DNL Live Search] [2.0.4]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html?lang=sv-SE). Information om hur du installerar den senaste versionen finns i [Uppdatera [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=sv-SE#update) i användarhandboken.

Den här artikeln innehåller information om det kända problemet där PLP (Product Listing Page) visar *Vi kan inte hitta produkter som matchar felet* när sökleverantören returnerar några objekt.

## Berörda produkter och versioner

Adobe Commerce (alla distributionsmetoder) 2.4.x

## Problem

[!DNL Live Search] visar sökresultat oavsett inställningarna för Stock-status i Adobe Commerce Admin. Även när **[!UICONTROL Display Out-of-Stock Products]** är inställd på *Nej* visas produkterna. PLP-felet *Det går inte att hitta produkter som matchar markeringen*.

<u>Steg som ska återskapas</u>:

1. Skapa en kategori och lägg till produkter. (Exempel: Kategori = _Jeans_, Produkt1 = _Blå jeans_, Produkt2 = _Svarta jeans_)
1. Gör alla produkter i kategorin utanför lagret.
1. Ange **[!UICONTROL Display Out-of-Stock Products]** till *Nej*.
1. Ange *Jeans* i sökfältet i butiken.
1. Klicka på **[!UICONTROL View All]** i popup-fönstret.

<u>Förväntat resultat</u>:

Du ser *Det går inte att hitta produkter som matchar markeringen* i PLP, och inga produkter visas i sökpopup-fönstret.

<u>Faktiskt resultat</u>:

Du ser *Det går inte att hitta produkter som matchar markeringen* i PLP, och båda produkterna visas i sökpopup-fönstret.

## Lösning

Det finns för närvarande ingen lösning på det här problemet. Vårt [!DNL Live Search]-team kommer snart att tillhandahålla en inställning för att konfigurera [!DNL Live Search] så att produkter visas korrekt.

## Relaterad läsning

[Installera [!DNL Live Search]](https://experienceleague.adobe.com/sv/docs/commerce-merchant-services/live-search/install) i användarhandboken.
