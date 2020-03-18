---
description: Du kan använda den här informationen för att spåra djupa och fördröjda länkar i dina mobilappar med hjälp av Adobe Mobile Android SDK.
keywords: android;library;mobile;sdk
seo-description: Du kan använda den här informationen för att spåra djupa och fördröjda länkar i dina mobilappar med hjälp av Adobe Mobile Android SDK.
seo-title: Spåra djupa länkar i Adobes mobiltjänster
solution: Marketing Cloud,Analytics
title: Spåra djupa länkar
topic: Developer and implementation
uuid: ebb1c08c-a246-40b3-9ac6-4606a14b4c5a
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Spåra djuplänkar {#tracking-deep-links}

Du kan använda den här informationen för att spåra djupa och fördröjda länkar i dina mobilappar med hjälp av Adobe Mobile Android SDK.

## Spåra djuplänkar

1. Lägg till SDK i ditt projekt och implementera livscykelvärden.

   Mer information finns i *Lägga till SDK- och konfigurationsfilen i IntelliJ IDEA- eller Eclipse-projektet* i [Core Implementation och Lifecycle](/help/android/getting-started/dev-qs.md).

1. Registrera programmet som ska hantera URL:er.

   Mer information finns i [URL-adresser](https://developer.android.com/training/basics/intents/filters.html).
1. Överför aktivitet med djuplänksmetod till Adobe SDK med hjälp av `collectLifecycleData`.

   Här är ett exempel på en djup länk för spår:

   ```java
   public class ParseDeepLinkActivity extends Activity { 
       @Override 
       protected void onCreate(Bundle savedInstanceState) { 
           super.onCreate(savedInstanceState); 
   
           Config.collectLifecycleData(this); 
           ... 
       } 
   }
   ```

Adobe Mobile] SDK kan tolka nyckel- och värdepar med data som är tillagda i en Deep- eller Universal Link så länge länken innehåller en nyckel med `a.deeplink.id` -etiketten och ett motsvarande icke-null- och användargenererat värde. Alla nyckel- och värdepar med data som läggs till länken tolkas, bifogas till en livscykelträff och skickas till Adobe Analytics] så länge länken innehåller `a.deeplink.id` nyckel och värde.

Dessutom kan du lägga till en eller flera av följande reserverade nycklar (med användargenererade värden) till djuret eller Universallänken:

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Dessa nycklar är förmappade variabler för rapportering i Adobe Analytics. Mer information om mappnings- och bearbetningsregler finns i [Bearbeta regler och Kontextdata](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

## Spåra fördröjda djuplänkar (för användning med marknadsföringslänkar)

Med en fördröjd djup länk öppnar Adobe SDK en ny metod med den djupa länken som intent data. Den här processen hanteras som en extern djuplänk med koden ovan.

## Allmän information om länkar {#section_1815396353614DA8A63D8D92112217E7}

### Konstanter

```java
/* 
 * Used for message deep link tracking
 * Key for deep link URL. 
 */
public static final String ADB_MESSAGE_DEEPLINK_KEY = "adb_deeplink";
```
