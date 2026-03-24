---
title: Was ist ein Feature Flag?
description: Erfahren Sie, was Feature Flags sind und wie Sie damit Anwendungsfunktionen zur Laufzeit aktivieren oder deaktivieren können, ohne dass eine erneute Bereitstellung erforderlich ist.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---


# Was ist ein Feature Flag? {#what-is-a-feature-flag}

Ein Feature Flag ist ein Mechanismus, mit dem Sie Features Ihrer Anwendung zur Laufzeit aktivieren oder deaktivieren können, ohne Code erneut bereitzustellen.

Feature Flags entkoppeln **Code-Bereitstellung** von **Funktionsverfügbarkeit**. Sie können neuen Code an die Produktion senden, wobei die Funktion hinter einer Markierung verborgen ist, und ihn dann aktivieren, wenn Sie bereit sind - für alle Benutzer oder für eine Zieluntergruppe.

Diese Trennung verringert das Risiko erheblich. Entwickler können kontinuierlich und mit minimaler Unterbrechung erstellen und versenden, während Produkt-Teams die volle Kontrolle darüber behalten, wann und für wen eine Funktion sichtbar wird.

>[!NOTE]
>
>Bei Erlebnis-Rollouts ist eine Feature Flag die atomischste Einheit der Feature Control. Sie kann allein verwendet werden, um eine einzelne Funktion anzusprechen, oder in Kombination mit anderen Flags in einer [Funktionsgruppe](feature-groups-to-control-multiple-features.md) oder [Version](release-management.md).
