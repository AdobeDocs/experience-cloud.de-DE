---
title: Analytics
description: Erfahren Sie, wie Sie das integrierte Analyse-Dashboard in Adobe Experience Rollouts aktivieren und verwenden, um die Leistung von Feature Flag-Kennzeichnungen zu verfolgen und die Auswirkungen des Rollouts zu messen.
hide: true
exl-id: edddca99-f263-461b-a16f-b46ee7c15f6c
source-git-commit: 12032cbed45e694a3f25f16afe80308b3eb82924
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 1%

---

# Analytics {#analytics}

Erlebnis-Rollouts bietet integrierte Analysen für Feature Flags, Feature Groups, Team-übergreifende Feature Groups und Releases. Verwenden Sie das Analytics-Dashboard, um zu verstehen, wie viele Benutzende an Ihrem Rollout teilnehmen und wie die Varianten- und Kontrollgruppen verglichen werden.

## Analytics aktivieren {#enable}

Analytics muss auf zwei Ebenen aktiviert werden:

1. **Anwendungsebene** - Wenden Sie sich an den Experience Rollouts-Support, um Analysen für Ihre Anwendung zu aktivieren.
2. **Feature Flag-Ebene** - Sobald Analytics für Ihr Programm aktiviert ist, aktivieren Sie das Kontrollkästchen **Analytics aktivieren** auf der Registerkarte **Grundlegende Details** jedes Feature Flag, das Sie verfolgen möchten.

>[!NOTE]
>
>Analytics kann standardmäßig für bis zu 20 Feature Flags pro Anwendung aktiviert werden. Wenden Sie sich an den Support, wenn Sie dieses Limit erhöhen müssen.

## Analytics-Dashboard anzeigen {#dashboard}

Sobald Analytics aktiviert ist, werden alle Feature Flags, Feature Groups und Releases für Ihre Anwendung mit dem Tracking von Daten gestartet. Greifen Sie auf das Dashboard zu **indem Sie &quot;**&quot; für das Feature Flag, die Feature Group oder Release auswählen, das Sie analysieren möchten.

Das Dashboard zeigt Folgendes an:

* **Teilnehmer** - Gesamtzahl der Benutzer, die sich für die Funktion qualifiziert haben (Variante + Kontrollgruppe kombiniert)
* **Kontrollgruppe** - Anzahl der der Kontrollgruppe zugewiesenen Benutzer (Benutzer, die das Standarderlebnis erhalten haben)
* **Diagramm auf Tagesebene** - Tägliche Liniendiagramme, die die Registrierung in der Varianten- und Kontrollgruppe im Zeitverlauf anzeigen; Markierungen geben an, wann die Feature Flag-Konfiguration aktualisiert wurde
* **Analyse auf Variantenebene** — Kumulative Anzahl der Benutzer, die in der Kontrollgruppe und in jeder Variante registriert sind

Wählen Sie für Funktionsgruppen und Versionen die Dropdown-Liste **Ergebnisse** aus, um ein Programm auszuwählen und Analysen für dieses Programm anzuzeigen. Analytics ist nur für Programme verfügbar, für die es aktiviert ist.

## Siehe auch {#see-also}

* [Erstellen des ersten Feature Flags](create-your-first-feature-flag.md)
* [A/B-Tests mit Feature Flags](a-b-testing.md)
* [Erstellen einer Funktionsgruppe](create-a-feature-group.md)

<!-- -->
