---
title: Zielgruppenregel mit Client-IP-Kontextvariable
description: Erfahren Sie, wie Sie die Client-IP-Kontextvariable in Zielgruppenregeln in Adobe Experience Rollouts verwenden, einschließlich Unterstützung für IP-Adressen, CIDR-Blöcke und Netzwerkbereiche.
source-git-commit: 3f3f7145b3c58dc721cbeb850e9e8571e3255bb1
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 1%

---


# Zielgruppenregel mit Client-IP-Kontextvariable {#clientip-rule}

Mit der Kontextvariablen `clientip` können Sie Benutzende basierend auf ihrer Client-IP-Adresse als Ziel auswählen. Dies ist nützlich, um Funktionen einzuschränken oder zu aktivieren, die auf dem Netzwerk basieren, von dem aus Benutzer auf Ihre Anwendung zugreifen - z. B. die Einschränkung des frühzeitigen Zugriffs auf Benutzer in einem Unternehmensnetzwerk.

## Unterstützte Eingabetypen {#input-types}

Die `clientip` Kontextvariable unterstützt drei Arten von Eingabewerten:

| Eingabetyp | Beschreibung | Unterstützte Operatoren |
|---|---|---|
| **IP-Adresse** | Eine einzelne IPv4- oder IPv6-Adresse | Ist, ist nicht gleich, In |
| **CIDR-Block** | Ein Bereich von IP-Adressen in CIDR-Notation (z. B. `192.168.1.0/24`) | Ist, in, ist nicht gleich |
| **Netzwerkbereich** | Ein vordefinierter benannter Netzwerkbereich, der von der Plattform verwaltet wird | Ist Teil von |

## Hinzufügen einer Client-IP-Regel {#adding-rule}

1. Öffnen Sie die Feature Flag, Feature Group oder Cross-Team Feature Group in der Konsole.
2. Navigieren Sie zur Registerkarte **Zielgruppe** .
3. Fügen Sie **&quot;**&quot; eine Bedingung mithilfe der Variablen **clientip** hinzu.
4. Wählen Sie den Operator aus und geben Sie den Wert ein (IP-Adresse, CIDR-Block oder einen vordefinierten Netzwerkbereich).

## Siehe auch {#see-also}

* [Verwenden des Kontexts in Zielgruppenregeln](using-context-in-audience-rules.md)
* [Zielgruppe in Feature Flags und Feature Groups](audience-in-feature-flags-and-feature-groups.md)
* [Komplexe Zielgruppenregeln](complex-rules.md)
