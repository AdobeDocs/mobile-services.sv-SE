---
description: I följande tabell beskrivs de olika appidentifierarna som används av Android SDK och Adobe Mobile-tjänsterna.
seo-description: I följande tabell beskrivs de olika appidentifierarna som används av Android SDK och Adobe Mobile-tjänsterna.
seo-title: Program-ID
solution: Marketing Cloud,Analytics
title: Program-ID
topic: Developer and implementation
uuid: 3ac99489-6269-439e-a814-24102ef220b1
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Program-ID{#app-ids}

I följande tabell beskrivs de olika appidentifierarna som används av Android SDK och Adobe Mobile-tjänsterna.

| ID | Beskrivning |
|--- |--- |
| ID skickat med livscykelvärden | Detta är en kombination av appnamnet och paketversionen som skickas till appbutiken. Det här värdet används för Versionsrapporten i Adobe Mobile Services, och du kan filtrera med det här värdet för att segmentera efter en specifik version av din app. |
| App Store-ID | Detta ID tilldelas till din app av appbutiken och tillhandahålls i Adobe Mobile Services när du skapar värvningslänkar. |
| AppID i ADBMomobile JSON-konfiguration | Detta är ett unikt ID som tilldelas programinstansen av Adobe Mobile Services för alla associerade metadata i systemet. Detta ID används för att skapa unika URL:er för anskaffningsspårning eller spårningslänk. Detta ID läggs automatiskt till i JSON-konfigurationsfilen för ADBMomobile när den här filen hämtas från användargränssnittet och finns i Hantera appinställningar under värvningsinställningarna för din app. |