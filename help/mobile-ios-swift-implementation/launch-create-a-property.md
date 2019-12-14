---
title: Eine Starteigenschaft für mobile Apps erstellen
description: Erfahren Sie, wie Sie sich bei der Startschnittstelle anmelden und eine mobile Launch-Eigenschaft erstellen. Diese Lektion ist Teil des Tutorials "Implementieren der Experience Cloud in Mobile iOS Swift Applications".
seo-description: null
seo-title: Eine Starteigenschaft für mobile Apps erstellen
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 7166d2933cc99bcbbd4713fba8f87fb0826b711e

---


# Eigenschaft "Launch"erstellen

Adobe Experience Platform Launch ist die nächste Generation von Funktionen für mobiles SDK und Website-Tag-Management. Mit Launch erhalten Kunden eine einfache Möglichkeit, alle Analyse-, Marketing- und Werbelösungen zu implementieren und zu verwalten, die erforderlich sind, um relevante Kundenerlebnisse zu optimieren. Für den Start ist keine zusätzliche Gebühr erforderlich. Es steht jedem Adobe Experience Cloud-Kunden zur Verfügung.

In dieser Lektion erstellen Sie eine Launch-Eigenschaft für mobile Apps.

## Voraussetzungen 

Um die nächsten Lektionen abzuschließen, müssen Sie über die Berechtigung zum Entwickeln, Genehmigen, Veröffentlichen, Verwalten von Erweiterungen und Verwalten von Umgebungen in Launch verfügen. Wenn Sie diese Schritte nicht ausführen können, da die Benutzeroberflächenoptionen nicht verfügbar sind, wenden Sie sich an Ihren Experience Cloud-Administrator, um Zugriff anzufordern. For more information on Launch permissions, see [the documentation](https://docs.adobe.com/content/help/en/launch/using/reference/admin/user-permissions.html).

## Lernziele

Dies können Sie am Ende dieser Lektion:

* Anmelden bei der Benutzeroberfläche "Starten"
* Neue mobile Launch-Eigenschaft erstellen
* Konfigurieren der mobilen Launch-Eigenschaft

## Öffnen von Launch

**So starten Sie**

1. Bei der [Adobe Experience Cloud anmelden](https://experiencecloud.adobe.com)

1. Klicken Sie auf das Symbol ![für den Lösungsschalter](images/mobile-launch-solutionSwitcher.png) , um den Lösungsschalter zu öffnen

1. Select **[!UICONTROL Launch]** from the menu

   ![Öffnen Sie den Umschalter der Lösung mit dem Symbol und klicken Sie auf Aktivierung](images/mobile-launch-solutionSwitcherActivation.png)

1. Klicken Sie unter **[!UICONTROL Adobe Experience Cloud Launch]** auf die Schaltfläche **[!UICONTROL Gehe zu Start]**

   ![Klicken Sie auf die Schaltfläche Start](images/mobile-launch-goToLaunch.png)

You should now see the `Properties` screen (if no properties have ever been created in the account, this screen might be empty):

![Eigenschaftenbildschirm](images/mobile-launch-propertiesScreen.png)

Wenn Sie häufig Launch verwenden, können Sie auch die folgende URL mit einem Lesezeichen versehen und sich direkt bei [https://launch.adobe.com anmelden.](https://launch.adobe.com)

## Erstellen einer Eigenschaft

Eine Eigenschaft ist im Grunde ein Container, den Sie beim Bereitstellen von Tags für Ihre App mit Erweiterungen, Regeln, Datenelementen und Bibliotheken füllen. Eine einzelne mobile Eigenschaft kann auf mehreren App-Plattformen verwendet werden (z. B. iOS und Android), sofern die Apps ähnliche Funktionen aufweisen und dieselben Lösungen implementiert werden müssen.  Weitere Informationen zum Erstellen von Eigenschaften finden Sie unter ["Einrichten einer mobilen Eigenschaft"](https://aep-sdks.gitbook.io/docs/getting-started/create-a-mobile-property) in der Produktdokumentation.

**So erstellen Sie eine Eigenschaft**

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Neue Eigenschaft]** :

   ![Klicken Sie auf Neue Eigenschaft](images/mobile-launch-addNewProperty.png)

1. Benennen Sie Ihre Eigenschaft (z. B. `Mobile Tutorial`)
1. Klicken Sie als Plattform auf **[!UICONTROL Mobil]**
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Speichern]**

   ![Neue Eigenschaft erstellen](images/mobile-launch-newProperty.png)

Ihre neue Eigenschaft sollte auf der Seite Eigenschaften angezeigt werden. Note that if you check the box next to the property name, options to **[!UICONTROL Configure]** or **[!UICONTROL Delete]** the property appear above the property list. Klicken Sie auf den Namen Ihrer Eigenschaft (z.B. `Mobile Tutorial`), um den `Overview` Bildschirm zu öffnen.
![Klicken Sie auf den Namen der Eigenschaft, um sie zu öffnen](images/mobile-launch-openProperty.png)

[Nächste "Erweiterungen hinzufügen"&gt;](launch-add-extensions.md)
