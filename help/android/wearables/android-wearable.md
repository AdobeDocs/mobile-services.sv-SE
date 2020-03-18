---
description: Från och med Android SDK version 4.5 har ett nytt Android-tillägg lagts till som gör att du kan samla in data från Android-appen.
seo-description: Från och med Android SDK version 4.5 har ett nytt Android-tillägg lagts till som gör att du kan samla in data från Android-appen.
seo-title: Android Wearables - komma igång
solution: Marketing Cloud,Analytics
title: Android Wearables - komma igång
topic: Developer and implementation
uuid: bfe5d41e-b17c-4634-80ac-7a38671ecb81
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Android Wearables: komma igång{#android-wearables-getting-started}

Från och med Android SDK version 4.5 har ett nytt Android-tillägg lagts till som gör att du kan samla in data från Android-appen.

## Konfigurera SDK för en handdator (Android Studio) {#section_262237484EC44C58953891B105F0D000}

Mer information om hur du importerar SDK till ditt projekt finns i [Core Implementation och Lifecycle](/help/android/getting-started/dev-qs.md).

1. Lägg till `ADBMobileConfig.json` filen i projektmappen.
1. Lägg till `adobeMobileLibrary-*.jar` filen i mappen libs eller se till att projektet refererar till filen.

   >[!TIP]
   >
   >Du kan behöva synkronisera övertoningsprojektet när du har lagt till `.jar` filen.

1. I `onCreate` metoden tillåter du SDK-åtkomst till programkontexten genom att använda `Config.setContext`:

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext()); 
   }
   ```

1. Lägg till följande kod i `AndroidManifest.xml` filen:

   ```java
       <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" /> 
       <uses-permission android:name="android.permission.INTERNET" /> 
       <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
   
   <application> 
   ....... 
   <meta-data android:name="com.google.android.gms.version" 
               android:value="@integer/google_play_services_version" /> 
   </application>
   ```

1. Se till att ditt projekt innehåller Googles bibliotek för speltjänster.
1. Implementera `WearableListenerService` eller lägg till motsvarande kod i din `WearableListenerService`:

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onMessageReceived(MessageEvent messageEvent) { 
           super.onMessageReceived(messageEvent); 
       } 
   
       private GoogleApiClient mGoogleApiClient; 
   
       @Override 
       public void onCreate() { 
           super.onCreate(); 
           mGoogleApiClient = new GoogleApiClient.Builder(this) 
                   .addApi(Wearable.API) 
                   .build(); 
           mGoogleApiClient.connect(); 
       } 
       @Override 
       public void onDestroy() { 
           super.onDestroy(); 
           mGoogleApiClient.disconnect(); 
       } 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerHandheld.onDataChanged(dataEvents, mGoogleApiClient, this); 
       } 
   }
   ```

1. Lägg till `WearListenerService` i `AndroidManifest.xml` filen:

   ```java
   If you are using Google Play Services  < 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                   <action android:name="com.google.android.gms.wearable.BIND_LISTENER" /> 
               </intent-filter> 
       </service> 
   </application> 
   If you are using Google Play Services >= 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                     <action android:name="com.google.android.gms.wearable.DATA_CHANGED" /> 
                    <data android:scheme="wear" android:host="*" android:pathPrefix="/abdmobile" /> 
               </intent-filter> 
       </service> 
   </application> 
   
   Please find more information from google's blog https://android-developers.googleblog.com/2016/04/deprecation-of-bindlistener.html. 
   Permalink Edit
   ```

## Konfigurera SDK för en ändringsbar app (Android Studio) {#section_2268EC03E20B4A228A28BDCFEA2E9AE4}

1. Gör något av följande:

   * Lägg till samma `ADBMobileConfig.json` fil i resursmappen för ditt bärbara projekt.
   * Ändra övertoningskonfigurationen så att den används `ADBMobileConfig.json` i resursmappen i den handhållna appen:

      ```java
      android { 
      
          sourceSets { 
              main { 
                  assets.srcDirs = ['src/main/assets','../mobile/src/main/assets'] 
              } 
         } 
      }
      ```

1. Lägg till `adobeMobileLibrary-*.jar` filen i mappen libs eller se till att projektet refererar till den.

   Du kan behöva synkronisera övertoningsprojektet när du har lagt till filen jar.

1. I `onCreate` metoden tillåter du SDK-åtkomst till programkontexten med `Config.setContext`:

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main);      
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext(), Config.ApplicationType.APPLICATION_TYPE_WEARABLE); 
   }
   ```

1. Lägg till följande kod i `AndroidManifest.xml`:

   ```java
   <application> 
   ....... 
   <meta-data android:name="com.google.android.gms.version" 
               android:value="@integer/google_play_services_version" /> 
   </application>
   ```

1. Se till att ditt projekt innehåller Googles bibliotek för speltjänster.
1. Implementera `WearableListenerService` eller lägg till motsvarande kod i din `WearableListenerService`:

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerWearable.onDataChanged(dataEvents); 
       } 
   
   }
   ```

1. Lägg till `WearListenerService` i `AndroidManifest.xml` filen:

   ```java
   If you are using Google Play Services  < 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                   <action android:name="com.google.android.gms.wearable.BIND_LISTENER" /> 
               </intent-filter> 
       </service> 
   </application> 
   If you are using Google Play Services >= 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                     <action android:name="com.google.android.gms.wearable.DATA_CHANGED" /> 
                    <data android:scheme="wear" android:host="*" android:pathPrefix="/abdmobile" /> 
               </intent-filter> 
       </service> 
   </application> 
   Please find more information from google's blog https://android-developers.googleblog.com/2016/04/deprecation-of-bindlistener.html. 
   Permalink Edit
   ```
