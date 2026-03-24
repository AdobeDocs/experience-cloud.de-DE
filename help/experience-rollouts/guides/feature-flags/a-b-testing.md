---
title: A/B-Tests mit Feature Flags
description: Erfahren Sie, wie Sie A/B-Tests mit Funktionsgruppen in Adobe Experience Rollouts ausführen, indem Sie mehrere Varianten für eine Reihe von Funktions-Flags konfigurieren.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 1%

---


# A/B-Tests mit Feature Flags {#a-b-testing}

A/B-Tests in Erlebnis-Rollouts werden mit **Funktionsgruppen** durchgeführt. Durch die Konfiguration von mehr als einer Variante in einer Funktionsgruppe können Sie verschiedene Versionen einer Funktion für verschiedene Untergruppen Ihrer Zielgruppe bereitstellen und die Ergebnisse vergleichen.

## Voraussetzungen {#prerequisites}

* Sie haben Zugriff auf die Konsole — siehe [Bei Konsole anmelden](../console/log-in-to-the-console.md)
* Sie gehören einem Team an und Ihr Programm wird integriert
* Sie haben die Rolle **Entwickler** oder **Produktversionsinhaber** (siehe [Benutzerrollen](../teams/user-roles.md)
* Sie haben die zu testenden Feature Flags erstellt (siehe [Erstellen des ersten Feature Flags](create-your-first-feature-flag.md)

## Schritt 1: KE-Gruppe mit mehreren Varianten erstellen {#create}

1. Navigieren Sie zu **Funktionstests > Funktionsgruppen** und wählen Sie **Neue Funktionsgruppe** aus.
2. Geben **in &quot;** Details“ einen Titel, einen Schlüssel und eine Beschreibung an.
3. Legen Sie einen **Rollout in Prozent** fest, um festzulegen, wie viel Ihrer Audience am Test teilnimmt.
4. Legen Sie **Varianten** auf einen Wert größer als 1 fest (z. B. zwei Varianten für einen klassischen A/B-Test).
5. Unter [Festlegen einer Funktionsgruppe für das schrittweise Rollout](set-feature-group-gradual-rollout.md) erfahren Sie, wie der Belichtungsprozentsatz auf die verschiedenen Varianten verteilt ist.

## Schritt 2: Festlegen der Audience {#audience}

Fügen Sie auf der Registerkarte **Audience** Audience-Kriterien hinzu und wählen Sie die einzuschließenden Programme aus. Funktionsgruppen können mehrere Anwendungen innerhalb desselben Teams umfassen.

>[!NOTE]
>
>Um externe Benutzer in einem A/B-Test anzusprechen, müssen Sie über die Rolle **Produktversionsinhaber** verfügen. Die Entwicklerrolle ist Sandbox-fähig und auf private Tests beschränkt.

## Schritt 3: Funktionen pro Variante hinzufügen {#features}

Auf der Registerkarte **Funktionen** verfügt jede Variante über eine eigene Registerkarte. Fügen Sie jeder Variante die entsprechenden Funktions-Flags hinzu, um die verschiedenen Erlebnisse zu definieren, die Sie vergleichen möchten.

>[!IMPORTANT]
>
>Ein Feature Flag kann jeweils nur über eine Methode bereitgestellt werden - Feature Flag, Feature Group oder Release. Wenn Sie einer Funktionsgruppe ein Flag hinzufügen, werden alle Zielgruppen- oder prozentualen Rollout-Sets direkt im Flag entfernt.

## Schritt 4: Speichern und aktivieren {#save}

Speichern Sie die Funktionsgruppeneinstellungen. Wenn Sie bereit sind, den Test zu starten, setzen Sie die Funktionsgruppe auf den aktiven Status.

## Siehe auch {#see-also}

* [Erstellen einer Funktionsgruppe](create-a-feature-group.md)
* [Festlegen einer Funktionsgruppe für das schrittweise Rollout](set-feature-group-gradual-rollout.md)
* [Analytics](analytics.md)
