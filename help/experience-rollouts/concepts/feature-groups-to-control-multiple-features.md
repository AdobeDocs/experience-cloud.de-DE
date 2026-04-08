---
title: Funktionsgruppen zur Steuerung mehrerer Funktionen
description: Erfahren Sie, wie Sie mit Funktionsgruppen in Experience Rollouts verwandte Feature Flags programmübergreifend als eine Einheit bündeln und verwalten können.
exl-id: dfeb7eff-34f1-4cb5-9c3e-a40d1eda3016
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# Funktionsgruppen zur Steuerung mehrerer Funktionen {#feature-groups}

Eine [Feature Flag](what-is-a-feature-flag.md) steuert ein einzelnes Feature. Wenn Sie mehrere zugehörige Feature Flags zusammen verwalten müssen - und sicherstellen, dass diese dieselbe Zielgruppe erreichen -, verwenden Sie eine **Feature Group**.

## Funktionen einer Funktionsgruppe {#what-it-does}

Eine Funktionsgruppe bündelt mehrere Funktions-Flags und ermöglicht es Ihnen, eine einzige Zielgruppenregel auf alle gleichzeitig anzuwenden. Dies ist nützlich, wenn eine einzelne benutzerseitige Funktion mehrere Anwendungen oder Dienste umfasst.

Nehmen wir zum Beispiel eine Funktion für die Zusammenarbeit, die Änderungen an einer Desktop-Anwendung, einer Mobile App und einem Backend-Service umfasst. Durch die Erstellung einer Funktionsgruppe mit Flags aus allen drei Anwendungen können Sie die Funktion für 1 % der Benutzer öffnen und sicherstellen, dass diese Benutzer ein konsistentes Erlebnis auf allen drei Oberflächen gleichzeitig sehen.

## Programmübergreifende Gruppierung {#cross-application}

Funktionsgruppen unterstützen programmübergreifendes Feature Management. Verwandte Flags über mehrere Anwendungen hinweg können gruppiert werden.

