---
title: Was ist ein Feature Flag?
description: Erfahren Sie, was Feature Flags sind und wie Sie damit Anwendungsfunktionen zur Laufzeit aktivieren oder deaktivieren können, ohne dass eine erneute Bereitstellung erforderlich ist.
exl-id: c4ed4ab5-0d73-4697-b05c-476d6e4010ce
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---

# Was ist ein Feature Flag? {#what-is-a-feature-flag}

Ein Feature Flag ist ein Mechanismus, mit dem Sie Features Ihrer Anwendung zur Laufzeit aktivieren oder deaktivieren können, ohne Code erneut bereitzustellen.

Feature Flags entkoppeln **Code-Bereitstellung** von **Funktionsverfügbarkeit**. Sie können neuen Code an die Produktion senden, wobei die Funktion hinter einer Markierung verborgen ist, und ihn dann aktivieren, wenn Sie bereit sind - für alle Benutzer oder für eine Zieluntergruppe.

Diese Trennung verringert das Risiko erheblich. Entwickler können kontinuierlich und mit minimaler Unterbrechung erstellen und versenden, während Produkt-Teams die volle Kontrolle darüber behalten, wann und für wen eine Funktion sichtbar wird.

>[!NOTE]
>
>Bei Erlebnis-Rollouts ist eine Feature Flag die atomischste Einheit der Feature Control. Sie kann allein verwendet werden, um ein einzelnes Feature anzusprechen, oder in Kombination mit anderen Flags in einer [Feature Group](feature-groups-to-control-multiple-features.md).
