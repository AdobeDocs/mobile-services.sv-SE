---
description: Följ de här stegen för att konfigurera en rapportserie för att samla in appdata för iOS.
seo-description: Följ de här stegen för att konfigurera en rapportserie för att samla in appdata för iOS.
seo-title: Innan du börjar
solution: Marketing Cloud,Analytics
title: Innan du börjar
topic: Developer and implementation
uuid: 04133f68-3618-41fd-8a13-aec5b6f04df6
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Innan du börjar {#before-you-start}

Följ de här stegen för att konfigurera en rapportserie för att samla in appdata för iOS.

## Rollspecifika uppgifter {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analysadministratörer och apputvecklare måste utföra följande uppgifter:

### Analysadministratörer

Så här konfigurerar du en rapportserie och samlar in data om mobilappar:

1. Fyll i ett av avsnitten i [Logga in på Adobe Mobile Services-gränssnittet](/help/ios/getting-started/getting-started.md).
1. Skapa ett Analytics-konto för varje apputvecklare.

Programutvecklare har nu tillgång till de rapportsviter du har skapat.

>[!IMPORTANT]
>
>Om du vill skapa en ny rapportsserie och hämta SDK:er måste du vara Analytics Administrator.

### Apputvecklare

1. Kontrollera att Analytics-administratören har slutfört stegen i avsnittet *Analysadministratörer* ovan.

1. Verifiera att Analytics-administratören har slutfört ett av avsnitten i *Logga in i Adobe Mobile Services-gränssnittet* nedan.
1. När rapportsviten har konfigurerats slutför du stegen i *Hämta SDK* nedan.

Mer information om roller och behörigheter finns i [Roller och behörigheter](/help/using/gs/c-mob-roles-and-permissions.md).

## Logga in på användargränssnittet för Adobe Mobile Services {#section_690A2EC4572E47869F183974E932A6A8}

Adobes mobiltjänster är det primära rapporteringsgränssnittet för mobilappsanalyser och målinriktning. När du har utfört de här stegen kan du hämta en konfigurationsfil som är förkonfigurerad med din datainsamlingsserver, rapportserie och många andra inställningar.

Du kan logga in på Adobes mobiltjänster på något av följande sätt:

* **Experience Cloud**

   Logga in på [Experience Cloud](https://marketing.adobe.com) med ditt Adobe ID.

   Den här metoden förutsätter att ditt företag har etablerats och att du har länkat ditt Analytics-konto. Mer information om etablering finns i [Hantera Experience Cloud-användare och -produkter](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html). Mer information om hur du länkar ditt konto finns i [Organisationer och kontolänkning](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/organizations.html).

   >[!TIP]
   >
   >Om du är osäker på om ditt företag har etablerats i Experience Cloud kan du använda ditt befintliga Adobe Analytics-konto.

* **Adobe Analytics**

   Klicka **[!UICONTROL Sign in with Analytics]** och ange företagsnamnet för Analytics, ditt användarnamn och ditt lösenord.

## Skapa en rapportsvit {#section_7BC602ED1ABA42C6AB722F506B5219F3}

Så här skapar du en rapportserie för att samla in appdata och definiera en app:

1. Klicka på **[!UICONTROL Create New App]**.

   Om knappen inte visas klickar du på **[!UICONTROL Manage Apps]** > **[!UICONTROL Add]**.

1. In the **[!UICONTROL Report Suite]** drop-down, select **[!UICONTROL New Report Suite]**.

1. Ange namnet på din app och välj ett unikt rapportsprogram-ID.

   Ett exempel på ett rapportsvit-ID är `mycomobileappdev`. Ni måste skapa separata rapportsviter och appar för utvecklings- och produktionsversionerna. När du är redo att konfigurera produktionsversionen upprepar du dessa steg.
1. Låt **[!UICONTROL Mobile App Template]** vara markerat.

   Med den här mallen kan tidsstämplar samla in offlinedata och aktivera mobillösningens variabler för att hämta livscykelvärden.

1. Markera **[!UICONTROL Timezone]**, **[!UICONTROL Currency]** och klicka på **[!UICONTROL Save]**.

## Ladda ned SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

Så här hämtar du mobil-SDK:

1. Logga in på Mobiltjänster och öppna appen på något av följande sätt:

   * Välj din app i **[!UICONTROL All Apps]** listrutan.
   * Leta reda på appen i den högra rutan och öppna den.

1. Klicka på **[!UICONTROL Manage App Settings]**.
1. Bläddra **[!UICONTROL App SDK Downloads]** till **[!UICONTROL App SDK Downloads]** avsnittet i avsnittet.

1. Hämta SDK och exempelappen för din plattform.

>[!TIP]
>
>En konfigurationsfil för din app inkluderas automatiskt i SDK-nedladdningen, så du behöver inte hämta filen separat. Om du redan har laddat ned SDK och vill få uppdaterade inställningar hämtar du konfigurationsfilen igen.
