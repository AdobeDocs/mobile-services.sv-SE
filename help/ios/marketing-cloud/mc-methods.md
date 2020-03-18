---
description: Här är Adobe Experience Platform Identity Service-metoderna som tillhandahålls av iOS-biblioteket.
seo-description: Här är Adobe Experience Platform Identity Service-metoderna som tillhandahålls av iOS-biblioteket.
seo-title: Adobe Experience Platform Identity Service-metoder
solution: Marketing Cloud,Analytics
title: Adobe Experience Platform Identity Service-metoder
topic: Developer and implementation
uuid: cdd307bc-8b7d-47a8-b77e-00902b9e2968
translation-type: tm+mt
source-git-commit: cbbb85b4d117fcaa502a1e01423f1f5d3b2ecc2b

---


# Adobe Experience Platform Identity Service-metoder {#experience-cloud-id-service-methods}

Här är Adobe Experience Platform Identity Service-metoderna som tillhandahålls av iOS-biblioteket.

SDK har för närvarande stöd för flera Adobe Experience Cloud-lösningar, inklusive Analytics, Target, Audience Manager och Experience Cloud Visitor ID-tjänsten.

Metoderna prefixeras enligt lösningen och Experience Cloud ID-metoderna prefixas `visitor`. Mer information finns i [Aktivera Experience Cloud-ID](/help/ios/marketing-cloud/mcvid.md).

* **`+`(null-able NSURL`*`)visitorAppendToURL:(null-able NSURL`*`)url;**

   Lägger till Adobe-besöksdata i en URL-sträng som ska användas med Adobe JavaScript-biblioteket. Om du vill använda den här metoden måste du ha Mobile SDK version 4.12 eller senare. Mer information finns i [Bifoga hjälpfunktion](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-appendvisitorid.html)för besökar-ID.

   >[!IMPORTANT]
   >
   >Den här metoden kan orsaka ett blockerande nätverksanrop. Anropa inte detta på tidskänsliga trådar.

   * Indata: `URL<NSURL>`En obligatorisk URL-sträng som besökarinformationen ska läggas till i.
   * `URL<NSURL>`
En sträng med besökarinformationen tillagd.

   * Här är kodexemplet för den här metoden:

      ```objective-c
       NSURL *url = [NSURL URLWithString:@"https://www.example.com"];  
       NSURL *decoratedURL = [ADBMobile visitorAppendToURL: url];  
       [[UIApplication sharedApplication] openURL: decoratedURL];  
      ```

* **visitorMarketingCloudID**

   Hämtar Experience Cloud-ID:t från ID-tjänsten.

   * Här är syntaxen för den här metoden:

      ```objective-c
      + (NSString  *)  visitorMarketingCloudID;
      ```

   * Här är kodexemplet för den här metoden:

      ```objective-c
      NSString *mcid = [ADBMobile visitorMarketingCloudID]; 
      ```

      >[!IMPORTANT]
      >
      >Den här metoden kan orsaka ett blockerande nätverksanrop och bör **inte** anropas från en gränssnittstråd.

* **visitorSyncIdentifiers:**

   Med Experience Cloud-ID kan ni ange ytterligare kund-ID:n som kan kopplas till varje besökare. Besökar-API:t godkänner flera kund-ID:n för samma besökare, med en kundtypsidentifierare som avgränsar omfattningen av olika kund-ID:n. Den här metoden motsvarar den `setCustomerIDs` i JavaScript-biblioteket.

   * Här är syntaxen för den här metoden:

      ```objective-c
      +  (void)  visitorSyncIdentifiers:(NSDictionary  *)identifiers;
      ```

   * Här är kodexemplet för den här metoden:

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"idType":@"idValue"}];
      ```

* **visitorSyncIdentifiers:authenticationState:**

   Synkroniserar angivna identifierare till ID-tjänsten. Ange `authState` ett av följande värden:

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * Här är syntaxen för den här metoden:

      ```objective-c
      +  (void) visitorSyncIdentifiers:(nullable NSDictionary  *)identifiers  authenticationState:(ADBMobileVisitorAuthenticationState)authState; 
      ```

   * Här är kodexemplet för den här metoden:

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"myIdType":@"valueForUser"}  authenticationState:ADBMobileVisitorAuthenticationStateAuthenticated]; 
      ```

* **visitorSyncIdentifierWithType:identifier:authenticationState:**

   Synkroniserar angiven identifierartyp och angivet värde med ID-tjänsten. Ange `authState` ett av följande värden:

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * Här är syntaxen för den här metoden:

      ```objective-c
      + (void) visitorSyncIdentifierWithType:(nullable NSString *)identifierType  
      identifier:(nullable NSString *)identifier authenticationState:
      (ADBMobileVisitorAuthenticationState)authState; 
      ```

   * Här är syntaxen för den här metoden:

      ```objective-c
      [ADBMobile visitorSyncIdentifierWithType:@"myIdType" identifier:@"valueForUser"  
      authenticationState:ADBMobileVisitorAuthenticationStateLoggedOut]; 
      ```

* **visitorGetIDs**

   Hämtar en array med skrivskyddade `ADBVisitorID` objekt.

   * Här är syntaxen för den här metoden:

      ```objective-c
      +  (nullable NSArray *) visitorGetIDs;
      ```

   * Här är kodexemplet för den här metoden:

      ```objective-c
      NSArray *myVisitorIDs = [ADBMobile visitorGetIDs];
      ```

* **visitorgetUrlVariablesAsync**

   Den här metoden, som introducerades i version 4.16.0, returnerar en sträng med URL-variabler för Visitor ID-tjänsten. Mer information om hur den här metoden används finns i [Adobe Experience Platform Identity Service-metoder](/help/ios/reference/hybrid-app.md).

   * Här är syntaxen för den här metoden:

      ```objectivec
      + (void) visitorGetUrlVariablesAsync:(nullable void (^)(NSString* __nullable urlVariables))callback;
      ```

   * Här är kodexemplet för den här metoden:

      ```objectivec
      NSString *urlString = @"https://www.mydomain.com/index.php"; 
      [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
        NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
        // use urlStringWithVisitorData 
      }];
      ```

## Gränssnittet ADBVisitorID {#section_2FF74454D25C4ADABAC5E43CBFAAEC26}

**Offentliga metoder:**

```objective-c
- (nullable NSString *) idType; 
- (nullable NSString *) identifier; 
- (ADBMobileVisitorAuthenticationState) authenticationState; 
```

## ADBMomobileVisitorAuthenticationState enum {#section_A55A3F336DDF4F838900632087F51430}

```objective-c
ADBMobileVisitorAuthenticationStateUnknown, 
ADBMobileVisitorAuthenticationStateAuthenticated, 
ADBMobileVisitorAuthenticationStateLoggedOut
```
