---
title: Erstellen einer Funktionsgruppe
description: Erfahren Sie, wie Sie in Adobe Experience Rollouts eine Funktionsgruppe erstellen, um mehrere Funktions-Flags in allen Anwendungen Ihres Teams als Einheit zu verwalten.
exl-id: 58148df1-84ee-4a78-a4b4-71f74cd8ce0a
source-git-commit: 454b5c719a5f8be82d1ed835da58bfca6316def2
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Erstellen einer Funktionsgruppe {#create-feature-group}

## Voraussetzungen {#prerequisites}

Bevor Sie eine Funktionsgruppe erstellen, führen Sie Folgendes aus:

* Sie haben Zugriff auf die Konsole „Experience Rollouts“ — siehe [Bei Konsole anmelden](../console/log-in-to-the-console.md)
* Ihr Programm wurde integriert - siehe [Onboarding Ihres Programms](../applications/onboard-your-application.md)
* Sie haben die Rolle **Entwickler** oder **Produktversionsinhaber**.
* Sie haben die Feature Flags erstellt, die Sie der Gruppe hinzufügen möchten - siehe [Erstellen des ersten Feature Flags](create-your-first-feature-flag.md)

Eine Einführung in Funktionsgruppen finden Sie unter &quot;[ zur Steuerung mehrerer Funktionen](../../concepts/feature-groups-to-control-multiple-features.md).

## Schritt 1: Funktionsgruppe erstellen {#create}

Öffnen Sie die Konsole und starten Sie eine neue Funktionsgruppe:

1. Melden Sie sich bei der Konsole „Experience Rollouts“ an und navigieren Sie zu **Funktionstests > Funktionsgruppen**.
2. Wählen Sie **Neue Funktionsgruppe** aus.

## Schritt 2: Grundlegende Details {#basic-details}

Konfigurieren Sie die allgemeinen Einstellungen für die Funktionsgruppe:

1. Geben Sie einen Titel, einen Schlüssel, eine Beschreibung und optional ein Tag an.
2. Legen Sie für **Funktionsgruppe einen** Rollout) fest.
3. Wenn Sie einen A/B-Test durchführen möchten, wählen Sie mehr als eine Variante aus. Andernfalls belassen Sie es bei einer Variante. Siehe [A/B-Tests mit Feature Flags](a-b-testing.md) für weitere Informationen.

## Schritt 3: Zielgruppe {#audience}

Definieren Sie, wer die Funktionen in dieser Gruppe erhalten soll:

1. Fügen Sie auf der Registerkarte **Audience** Audience-Kriterien hinzu, um zu definieren, welche Benutzer die Funktion erhalten.
2. Fügen **unter** eine oder mehrere Anwendungen aus Ihrem Team hinzu. Funktionsgruppen können mehrere Anwendungen umfassen, solange sie alle zum selben Team gehören.

>[!NOTE]
>
>Die **Entwickler**-Rolle ist Sandbox. Fügen Sie Ihre eigene Benutzer-ID unter **Zielgruppe > Profil > Benutzer-ID)**, um einen privaten Test durchzuführen. Um externe Benutzer anzusprechen, benötigen Sie die Rolle **Produktversionsinhaber** .

## Schritt 4: Funktionen {#features}

Weisen Sie die Feature Flags zu, die von dieser Gruppe gesteuert werden:

1. Auf der Registerkarte **Funktionen** wird für jede ausgewählte Anwendung ein Feld angezeigt.
2. Hinzufügen von Feature Flags für jede Anwendung.
3. Wenn Sie mehrere Varianten ausgewählt haben (für A/B-Tests), werden für jede Variante Registerkarten angezeigt. Fügen Sie jedem die entsprechenden Feature Flags hinzu.

>[!IMPORTANT]
>
>Ein Feature Flag kann nur über eine Methode bereitgestellt werden - entweder direkt als Feature Flag, über eine Feature Group oder über eine Release. Wenn Sie einer Funktionsgruppe ein Feature Flag hinzufügen, werden alle Zielgruppen- oder prozentualen Rollout-Sets für das Flag entfernt. Feature Flags, die bereits einer anderen Version oder Funktionsgruppe zugewiesen sind, werden nicht in der Liste angezeigt.

## Schritt 5: Zeitplan (optional) {#schedule}

Sie können festlegen, dass die Funktionsgruppe zu einem späteren Zeitpunkt aktiviert wird. Weitere Informationen [ Sie unter ](schedule.md).

## Siehe auch {#see-also}

* [Festlegen einer Funktionsgruppe für das schrittweise Rollout](set-feature-group-gradual-rollout.md)
* [A/B-Tests mit Feature Flags](a-b-testing.md)
* [Funktionsgruppen zur Steuerung mehrerer Funktionen](../../concepts/feature-groups-to-control-multiple-features.md)
