---
title: SDK-Benchmarking
description: Überprüfen Sie die Java SDK-Benchmarking-Ergebnisse für Adobe Experience Rollouts, einschließlich Messungen der Antwortzeit über eine unterschiedliche Anzahl von Feature Flags hinweg unter typischen Lastbedingungen.
source-git-commit: 8b8b5db1a28af3a3ac29aecf26482f70eb84c714
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 7%

---


# SDK-Benchmarking {#sdk-benchmarking}

Die Erlebnis-Rollouts von Java SDK werden einem Benchmarking unterzogen, um Integrationsteams eine zuverlässige Schätzung der Ressourcen und Reaktionszeiten zu liefern, die bei der Ausführung von SDK innerhalb ihrer Infrastruktur zu erwarten sind.

## Testumgebung {#test-environment}

Das Benchmarking wurde auf einer Spring Boot-Anwendung mit der folgenden festen Konfiguration durchgeführt:

* **CPU-Kerne:** 8
* **JVM-Arbeitsspeicher:** 4096 MB

## Testannahmen {#test-assumptions}

Die folgenden Bedingungen wurden über alle Benchmark-Durchgänge hinweg konstant gehalten:

* Feature Flags getestet: 8 bis 128
* Kontextvariablen pro Feature Flag: 2 (Typ `STRING`, Länge 36 Zeichen)
* Durchschnittliche Auslastung: 15.000 Anfragen pro Minute (RPM)
* Aktive Threads: 100

## Ergebnisse {#results}

Die nachstehende Tabelle zeigt die 99,99. Perzentil der Reaktionszeit für `getFeatures()`-Aufrufe, wenn die Anzahl der Feature Flags steigt:

| Anzahl der Feature Flags | Kontextvariablen pro Markierung | Reaktionszeit (ms, p99.99) |
|---|---|---|
| 8 | 2 | &lt; 0.5 |
| 16 | 2 | &lt; 0.5 |
| 32 | 2 | &lt; 0.5 |
| 64 | 2 | &lt; 1 |
| 128 | 2 | &lt; 1 |

## Interpretieren der Ergebnisse {#interpretation}

Die oben genannten Benchmarks stellen die Leistung unter den beschriebenen spezifischen Testbedingungen dar. Da SDK in der Infrastruktur Ihres Programms ausgeführt wird, variieren die tatsächlichen Antwortzeiten je nach den Faktoren, die für Ihre Umgebung spezifisch sind:

* Verfügbare CPU und Anzahl der Kerne
* JVM-Heap-Größe und Verhalten bei der automatischen Bereinigung
* Thread-Verfügbarkeit und Kontextwechsel
* Aktuelle Systemlast zum Zeitpunkt der Anfrage

Verwenden Sie diese Zahlen als Planungsgrundlage und nicht als garantierte Leistungsziele für Ihre Produktionsumgebung.

## Siehe auch {#see-also}

* [Java SDK-Integrationshandbuch](java/java-sdk-integration-guide.md)
* [Java SDK - Versionshinweise](java/java-sdk-release-notes.md)
* [SDKs](../integrate/sdks.md)
