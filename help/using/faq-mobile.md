---
description: Vanliga frågor och svar om Adobes mobiltjänster och en allmän beskrivning av funktioner.
keywords: mobile
seo-description: Vanliga frågor och svar om Adobes mobiltjänster och en allmän beskrivning av funktioner.
seo-title: Vanliga frågor
solution: Marketing Cloud,Analytics
title: Vanliga frågor
topic: Metrics
uuid: 62a9241c-2ada-483a-a594-b023916cb0b6
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Vanliga frågor {#frequently-asked-questions}

Följande tabell innehåller en lista med vanliga frågor och svar om Adobes mobiltjänster:

## Adobe Mobile SDK {#section_9C2181F7B39A4BEB8EE6BCEFCF14C72F}

### Gör du ofta uppdateringar med SDK:n?

Ja, vi gör ständigt uppdateringar för att du ska få tillgång till avancerade, standardiserade och säkra SDK:er. Vi släpper vanligtvis en ny version varje månad. Dessa SDK-uppdateringar är ersättningar vid programbortfall (för version 4x) som underlättar implementeringen. Mer information om våra uppdateringar finns i [versionsinformationen](https://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html).

### Vilken SDK-version ska jag använda?

Våra nuvarande SDK:er finns i version 4.11. Mer information finns i [versionsinformationen](https://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html).

### Var kan jag ladda ned SDK:erna?

SDK:erna för enskilda mobilplattformar kan laddas ned genom att gå till [Hantera appinställningar](/help/using/c-manage-app-settings/c-manage-app-settings.md) .

### Hur konfigurerar jag SDK:erna?

När du har skapat en ny programrapportsserie går du till Hantera appinställningar och konfigurerar alla nödvändiga alternativ på programinformationssidan. När du har sparat konfigurationen hämtar du de SDK:er som krävs från nederkanten av sidan Hantera appinställningar. SDK kommer att levereras förkonfigurerat med de alternativ som du har sparat och finns i filen i SDK- `ADBMobileConfig.json` paketet. Om du ändrar några SDK-inställningar på sidan Hantera programinställningar kontrollerar du att du hämtar SDK-filerna igen eller uppdaterar din `ADBMobileConfig.json` fil med de ändringar som krävs.

### Har Adobe Mobile SDK stöd för IPv6 för iOS?

Adobes SDK för mobiler använder iOS- och Android-standardnätverksstackarna. För iOS använder SDK NSURLSession (iOS version 7+) och NSURLConnection (iOS version 7 och senare) som är helt kompatibla med IPv6. Utvecklare som har skapat eller använt sin egen nätverksstack kanske vill granska om det finns andra orsaker till att minska risken. Här är ytterligare information från Apple:

*Om du skriver en klientapp med nätverks-API:er på hög nivå, som NSURLSession och CFNetwork, och du ansluter efter namn, behöver du inte ändra något för att appen ska fungera med IPv6-adresser.* Mer information finns i [Stöd för IPv6 DNS64/NAT64-nätverk](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html#__/apple_ref/doc/uid/TP40010220-CH213-SW1).


## Adobe Analytics {#section_78EC9D83791F477AAED678720CEBA9F6}

### Vad är Lifecycle Metrics?

Livscykelstatistik är körklara mått som samlas in automatiskt när SDK implementeras första gången i din app. Mer information finns i [Lifecycle Metrics (Android)](/help/android/metrics.md) and [Lifecycle Metrics (iOS)](/help/ios/metrics.md).

### Hur felsöker jag bearbetningsregler?

Mer information finns i Tips och tricks för [bearbetningsregler](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules-tips.html).

### Kan jag skicka analysdata till flera rapportsviter?

Ja. SDK:erna gör det möjligt att skicka data till flera rapportsviter i Adobe Analytics. Om du vill samla in data i flera rapportsviter med hjälp av en bildbegäran anger du ID:n för flera rapportsviter i **[!UICONTROL rsids]** fältet under **[!UICONTROL analytics]** avsnittet i `ADBMobileConfig.json` filen, avgränsade med kommatecken och utan blanksteg. Mer information finns i [ADBMomobile JSON Config](/help/ios/configuration/json-config/json-config.md).

### Hur skiljer sig mobilbesöken från lanseringar?

SDK:n mäter när en användare öppnar appen för första gången eller återgår till appen efter att ha varit utanför appen längre tid än det angivna timeoutvärdet. Den vanliga tidsgränsen är 5 minuter (300 sekunder) i **[!UICONTROL lifecycleTimeout]** fältet, som finns i `ADBMobileConfig.json` filen. Ett besök är en beräkning på serversidan som görs av Adobe Analytics och som baseras på den första och den sista dataträffen som skickas av SDK utan att tidsgränsen för besöket överskrids. Sessionstimeout anges vanligtvis till 30 minuter för en rapportsvit. Även om besök kommer från traditionell webbanalys ger de här träffarna fortfarande värdefulla insikter om hur användarna kommer in i och avslutar er app.

## Meddelanden {#section_5EFDD2B2EBA543C09902FF979C89F2EC}

### Finns det några storleksbegränsningar eller andra begränsningar för push-meddelanden?

Push-meddelanden får innehålla högst 140 tecken. Det finns inga gränser för hur många meddelanden som kan skickas eller schemaläggas eller hur ofta meddelanden skickas.

### Stöder du anpassade nyttolaster för push-meddelanden?

Ja, vi tillhandahåller en anpassad push-nyttolast som kan kodas i JSON. Android- och iOS-nyttolaster är begränsade till 4 kB respektive 2 kB. Dessa nyttolaster skickas till appen via ett push-meddelande eller ett lokalt meddelande. Mer information finns i [Upplevelse: Push-meddelande](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### Finns det storleksbegränsningar för meddelanden i appen?

Publicerade och aktiva meddelanden i appen som skapats i Adobe Mobile Services lagras på en server med en storleksbegränsning på 15 MB per programrapporteringsserie. Begränsningen gäller för meddelandeinnehåll och -resurser hos Adobe, men det finns inga begränsningar för vilka resurser meddelandet i appen kan referera till på andra värdar eller i appen.

### Kan jag använda min egen HTML-kod för meddelanden i appen?

Ja, vi stöder anpassad HTML för dina meddelanden i appen. Mer information finns i [Upplevelse: Meddelande](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md)i appen.

### Vilka utlösare kan jag använda för att skicka push-meddelanden eller meddelanden i appen?

Marknadsförarna kan välja alla Analytics-data eller -händelser som skickas som en utlösare för att visa meddelanden i appen. Meddelanden i appen använder utlösare som inträffar lokalt på enheten. Om flera utlösare väljs måste alla utlösare inträffa i samma träff för att meddelandet ska kunna visas. Mer information finns i [Upplevelse: Meddelande](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md)i appen.

Push-meddelanden skickas med befintliga Adobe Analytics-segment eller anpassade segment som kan skapas utifrån tidigare insamlade analysdata. Mer information finns i [Upplevelse: Push-meddelande](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### Varför får jag ett fel med namnet på länken i appen, push eller Marketing Link som jag skrev in?

Du kan inte använda samma namn på meddelanden i appen, push-meddelanden eller markeringslänk i flera appar som använder samma överordnade rapportserie eller VRS. Lös problemet genom att ange ett annat namn för meddelandet i appen, push-meddelandet eller Marketing Link.

## Plats {#section_01208FE3B7764E0DADDCB9AD9E1FCD87}

### Finns det någon gräns för hur många intressepunkter jag kan ha?

Det finns ingen specifik begränsning, men för idealiska prestanda och på grund av minnesbegränsningar på användarens enhet rekommenderar vi att du skapar eller överför högst 5 000 POI.

## Förvärv {#section_B37F1129CD5843E890D0E54179455357}

### Kan jag attribuera kampanjer till aktiviteter i appen?

Ja. Adobe Mobile Services kan hjälpa er att bygga marknadsföringstricks som hjälper er att marknadsföra och driva trafik till era appar och koppla kundvärvningskampanjer till analyser och konverteringar i appen. Mer information finns i [Anskaffning](/help/using/acquisition-main/acquisition-main.md).

### Hur skapar jag länkar för att skaffa och spåra nya appanvändare?

Du kan skapa marknadsföringslänkar som dirigerar användare att hämta program från Apple App Store och Google Play. Med dessa länkar kan du attribuera dina lyckade händelser till hämtningarna. Mer information finns i [Marketing Links Builder](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).