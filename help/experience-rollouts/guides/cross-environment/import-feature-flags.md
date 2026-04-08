---
title: Feature Flags importieren
description: Erfahren Sie, wie Sie in Adobe Experience Rollouts Feature Flags von einer Sandbox in eine andere importieren, um zu vermeiden, dass Flag-Konfigurationen manuell neu erstellt werden.
exl-id: 37c84d75-a565-4202-8c99-f630e05b6bb6
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 1%

---

# Feature Flags importieren {#import-feature-flags}

Mit Erlebnis-Rollouts können Sie Feature Flags aus einer Sandbox (z. B. Sandbox 1) in eine andere Sandbox (z. B. Sandbox 2) importieren. Dadurch wird vermieden, dass Flag-Konfigurationen manuell neu erstellt werden müssen, und das Risiko von Konfigurationsabweichungen zwischen Sandboxes wird reduziert.

## Schritt 1: Zur Ziel-Sandbox und -Anwendung wechseln {#step-1}

Melden Sie sich bei der Konsole für die Sandbox **Ziel** an, also die Sandbox, in die Sie Flags importieren **. Wählen Sie die Anwendung, in die Sie Flags importieren möchten, aus der Dropdown-Liste Anwendung auf der Seite Feature Flags .

>[!IMPORTANT]
>
>Ihre aktuelle Sandbox und das ausgewählte Programm müssen das **Ziel** sein - nicht die Quelle. Um beispielsweise ein Flag aus Sandbox 1 in Sandbox 2 zu importieren, melden Sie sich bei der Sandbox 2 -Konsole an und wählen Sie Ihre Sandbox 2 -Anwendung aus.

## Schritt 2: Importdialogfeld öffnen {#step-2}

Wählen Sie **Feature Flags importieren**. Ein Dialogfeld wird geöffnet, in dem die Quell-Sandbox und das Programm angezeigt werden, die basierend auf den verfügbaren Programmen vorausgefüllt sind. Bei Bedarf können Sie die Quell-Sandbox und die Anwendung über die Dropdown-Listen im Dialogfeld ändern.

## Schritt 3: Feature Flags zum Importieren auswählen {#step-3}

Wählen Sie aus der Liste der Feature Flags in der Quell-Sandbox die Flags aus, die Sie importieren möchten. Sie können ein, mehrere oder alle Flags gleichzeitig auswählen.

## Schritt 4: Status der zu importierenden Feature Flags auswählen {#step-4}

Verwenden Sie das Dropdown-Menü, um auszuwählen, wie die Feature Flags importiert werden sollen - entweder **Aktiviert**, **Deaktiviert** oder in ihrem **aktuellen Status**. Standardmäßig werden Feature Flags im Status **Deaktiviert** importiert.

## Wichtige Hinweise {#important-notes}

Beachten Sie beim Importieren von Feature Flags Folgendes:

* Wenn in der Ziel-Sandbox bereits ein Feature Flag mit demselben Schlüssel vorhanden ist, wird es nicht importiert.

## Siehe auch {#see-also}

* [Funktionen und Funktionsgruppen](../feature-flags/features-feature-groups-releases.md)
* [Erstellen des ersten Feature Flags](../feature-flags/create-your-first-feature-flag.md)
