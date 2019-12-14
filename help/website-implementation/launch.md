---
title: Eigenschaft "Launch"erstellen
description: Erfahren Sie, wie Sie sich bei der Startschnittstelle anmelden und eine Launch-Eigenschaft erstellen. Diese Lektion ist Teil des Tutorials zum Implementieren der Experience Cloud in Websites mit Start.
seo-description: null
seo-title: Eigenschaft "Launch"erstellen
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 7166d2933cc99bcbbd4713fba8f87fb0826b711e

---


# Eigenschaft "Launch"erstellen

In dieser Lektion erstellen Sie Ihre erste Launch-Eigenschaft.

Eine Eigenschaft ist im Wesentlichen ein Container, den Sie bei der Bereitstellung von Tags auf Ihrer Site mit Erweiterungen, Regeln, Datenelementen und Bibliotheken füllen.

## Voraussetzungen 

Um die nächsten Lektionen abzuschließen, müssen Sie über die Berechtigung zum Entwickeln, Genehmigen, Veröffentlichen, Verwalten von Erweiterungen und Verwalten von Umgebungen in Launch verfügen. Wenn Sie diese Schritte nicht ausführen können, da die Benutzeroberflächenoptionen nicht verfügbar sind, wenden Sie sich an Ihren Experience Cloud-Administrator, um Zugriff anzufordern. For more information on Launch permissions, see [the documentation](https://docs.adobe.com/content/help/en/launch/using/reference/admin/user-permissions.html).

## Lernziele

Dies können Sie am Ende dieser Lektion:

* Anmelden bei der Benutzeroberfläche "Starten"
* Neue Launch-Eigenschaft erstellen
* Konfigurieren einer Launch-Eigenschaft

## Öffnen von Launch

**So starten Sie**

1. Bei der [Adobe Experience Cloud anmelden](https://experiencecloud.adobe.com)

1. Klicken Sie auf das Symbol ![für den Lösungsschalter](images/launch-solutionSwitcher.png) , um den Lösungsschalter zu öffnen

1. Wählen Sie **[!UICONTROL Start]** aus dem Menü ![Öffnen Sie den Lösungsschalter mit dem Symbol und klicken Sie auf Aktivierung](images/launch-solutionSwitcherActivation.png)

1. Klicken Sie unter **[!UICONTROL Adobe Experience Cloud Launch]** auf die Schaltfläche **[!UICONTROL Gehe zu Start]**

   ![Klicken Sie auf die Schaltfläche Start](images/launch-goToLaunch.png)

You should now see the `Properties` screen (if no properties have ever been created in the account, this screen might be empty):

![Eigenschaftenbildschirm](images/launch-propertiesScreen.png)

Wenn Sie häufig Launch verwenden, können Sie auch die folgende URL mit einem Lesezeichen versehen und sich direkt bei [https://launch.adobe.com anmelden.](https://launch.adobe.com)

## Erstellen einer Eigenschaft

Eine Eigenschaft ist im Wesentlichen ein Container, den Sie bei der Bereitstellung von Tags auf Ihrer Site mit Erweiterungen, Regeln, Datenelementen und Bibliotheken füllen. Es kann sich bei einer Eigenschaft um eine beliebige Gruppierung einer oder mehrerer Domänen bzw. Subdomänen handeln. Sie können diese Assets auf ähnliche Weise verwalten und verfolgen. Angenommen, Sie haben mehrere Websites, die auf einer Vorlage basieren, und Sie möchten auf all diesen Websites dieselben Assets verfolgen. Sie können eine Eigenschaft auf mehrere Domänen anwenden. Weitere Informationen zum Erstellen von Eigenschaften finden Sie unter ["Unternehmen und Eigenschaften"](https://docs.adobe.com/content/help/en/launch/using/reference/admin/companies-and-properties.html) in der Produktdokumentation.

**So erstellen Sie eine Eigenschaft**

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Neue Eigenschaft]** :

   ![Klicken Sie auf Neue Eigenschaft](images/launch-addNewProperty.png)

1. Benennen Sie Ihre Eigenschaft (z. B. `Launch Tutorial` oder `Daniel's Launch Tutorial`)
1. Als Domäne geben Sie ein, `enablementadobe.com` da dies die Domäne ist, in der die Luma-Demo-Site gehostet wird. Obwohl das Feld "Domäne"erforderlich ist, funktioniert die Eigenschaft "Start"in jeder Domäne, in der es implementiert ist. Der Hauptzweck dieses Felds ist das Vorausfüllen von Menüoptionen im Rule Builder.
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Speichern]**

   ![Neue Eigenschaft erstellen](images/launch-newProperty.png)

Ihre neue Eigenschaft sollte auf der Seite Eigenschaften angezeigt werden. Note that if you check the box next to the property name, options to **[!UICONTROL Configure]** or **[!UICONTROL Delete]** the property appear above the property list. Klicken Sie auf den Namen Ihrer Eigenschaft (z.B. `Launch Tutorial`), um den `Overview` Bildschirm zu öffnen.
![Klicken Sie auf den Namen der Eigenschaft, um sie zu öffnen](images/launch-openProperty.png)

[Weiter "Einbettungscode starten"&gt;](launch-add-embed.md)
