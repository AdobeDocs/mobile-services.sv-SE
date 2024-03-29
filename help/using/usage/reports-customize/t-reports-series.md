---
description: Den här informationen hjälper er att anpassa de inbyggda rapporterna genom att lägga till ytterligare serier (mätvärden) eller appar i olika rapportsviter för att jämföra data.
keywords: mobil
solution: Experience Cloud Services,Analytics
title: Lägg till serier (mått) i rapporter
topic-fix: Reports,Metrics
uuid: 84fdfb1f-70e6-4c02-9b3b-526e9c924f74
exl-id: 1b1356c6-7f62-4b88-996a-09ed33b19c9d
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 2%

---

# Lägg till serier (mätvärden) i rapporter{#add-series-metrics-to-reports}

{#eol}

Den här informationen hjälper er att anpassa de inbyggda rapporterna genom att lägga till ytterligare serier (mätvärden) eller appar i olika rapportsviter för att jämföra data.

>[!IMPORTANT]
>
>Mätvärden för mobilappar finns också i marketing reports and analytics, ad hoc-analyser, data warehouse och andra analysrapporteringsgränssnitt. Om det inte finns någon nedbrytning- eller rapporttyp i Adobe Mobile kan den genereras med ett annat rapporteringsgränssnitt.

I det här exemplet anpassar vi **[!UICONTROL Users & Sessions]** -rapport, men instruktionerna kan gälla för alla rapporter.

1. Öppna appen och klicka på **[!UICONTROL Usage]** > **[!UICONTROL Users & Sessions]**.

   ![Stegresultat](assets/customize1.png)

   Den här rapporten ger en fullständig övertidsöversikt över våra appanvändare. Vi vill dock lägga till en serie för att rapportera programkrascher.

1. Klicka på **[!UICONTROL Customize]**.

   ![Stegresultat](assets/customize2.png)

1. Bläddra nedåt och klicka **[!UICONTROL Add Series]**.

   Seriens namn fylls i med samma namn som den sista serien i listan. I föregående bild är den senaste serien **[!UICONTROL App Store Downloads]**, så en ny serie läggs till och får även namnet **[!UICONTROL App Store Downloads]**.

1. Gör något av följande:

   * Om du vill lägga till en ny serie (metrisk) klickar du på namnet på den serie du just skapade och väljer ett nytt livscykelmått i listrutan.

      ![Stegresultat](assets/add_series.png)

   * Om du vill lägga till en ny app i en annan rapportserie så att du kan jämföra data mellan appar klickar du på appnamnet i den nyligen skapade serien och väljer önskad app.

      ![](assets/add_series_app.png)

1. (Villkorligt) Lägg till filter i den nya serien.

   Mer information finns i [Lägg till filter i rapporter](/help/using/usage/reports-customize/t-reports-customize.md).
1. Klicka **[!UICONTROL Update]** och **[!UICONTROL Run]**.
