---
title: Globale Unterdrückungsliste
description: Informationen zur globalen Unterdrückungsliste
hide: true
exl-id: 40aef987-52a3-470b-88ca-c716a116bdfc
source-git-commit: b66e2525694c771ebb7ac5190b7259ef5658d81a
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 100%

---

# Globale Unterdrückungsliste {#global-suppression-list}

Eine Unterdrückungsliste besteht aus E-Mail-Adressen, die Kundinnen und Kunden von ihren Sendungen ausschließen möchten, da das Senden an diese Kontakte ihren Ruf als Versender und ihre Versandraten beeinträchtigen könnte. Derzeit führt Adobe eine aktualisierte Liste bekannter schlechter E-Mail-Adressen, die sich nachweislich negativ auf die Interaktion und die Reputation des Versenders auswirken, und stellt sicher, dass E-Mails an diese Adressen nicht zugestellt werden. Diese Liste wird in einer globalen Unterdrückungsliste verwaltet, die für alle Adobe-Kunden gleich ist. Die Adressen und Domain-Namen in der globalen Unterdrückungsliste sind verborgen. In den Versandberichten wird nur die Anzahl der ausgeschlossen Empfänger angegeben.

Es ist nun möglich, die globale Unterdrückungsliste über eine intern verfügbare Schnittstelle zu verwalten. Diese Liste wird nur von Fachleuten für Zustellbarkeit verwaltet. Die globale Unterdrückungsliste kann E-Mail- oder Domain-Adressen enthalten.

## Zugriff auf die globale Unterdrückungsliste

Um auf die detaillierte Liste der ausgeschlossenen E-Mail-Adressen und Domains zuzugreifen, navigieren Sie zu **[!UICONTROL Globale Unterdrückungsliste]**.

>[!CAUTION]
>
>Die Berechtigungen zum Anzeigen, Exportieren und Verwalten der globalen Unterdrückungsliste hängen vom Verteiler ab, dem Sie zugewiesen sind. Weitere Informationen

Es werden zwei Registerkarten angezeigt: **[!UICONTROL E-Mail]** und **[!UICONTROL Domain]**.

Es stehen Filter zur Verfügung, mit denen Sie die Liste durchsuchen können.

## Hinzufügen von Adressen und Domains

Derzeit gibt es zwei Möglichkeiten, der globalen Unterdrückungsliste Adressen hinzuzufügen:

* Vom Team für Zustellbarkeit kuratierte Liste.
* Liste, die vom Drittdienstleister Blackbox bereitgestellt wird.

Sie können E-Mail-Adressen oder Domains [einzeln](#add-one-address-or-domain) oder [im Bulk-Modus](#upload-csv-file) über einen CSV-Datei-Upload hinzufügen.

Klicken Sie dazu auf den Button **[!UICONTROL E-Mail oder Domain hinzufügen]** und folgen Sie dann einer der folgenden Methoden.

### Eine einzelne Adresse oder Domain hinzufügen {#add-one-address-or-domain}

1. Wählen Sie die Option **[!UICONTROL Einzeln]** aus.

1. Wählen Sie den Adresstyp aus: **[!UICONTROL E-Mail-Adresse]** oder **[!UICONTROL Domain-Adresse]**.

1. Geben Sie die E-Mail-Adresse oder Domain ein, die Sie vom Versand ausschließen möchten.

   >[!NOTE]
   >
   >Vergewissern Sie sich, dass Sie eine gültige E-Mail-Adresse (z. B. abc@firma.com) oder Domain (z. B. abc.firma.com) eingeben.

1. Geben Sie bei Bedarf einen Grund an.

   >[!NOTE]
   >
   >Alle druckbaren ASCII-Zeichen zwischen 32 und 126 sind in diesem Feld zulässig. Die vollständige Liste finden Sie zum Beispiel auf [dieser Seite](https://en.wikipedia.org/wiki/Wikipedia:ASCII#ASCII_printable_characters){target="_blank"}.

1. Klicken Sie zur Bestätigung auf **[!UICONTROL Senden]**.

### CSV-Datei hochladen {#upload-csv-file}

1. Wählen Sie die Option **[!UICONTROL CSV hochladen]** aus.

1. Laden Sie die zu verwendende CSV-Vorlage herunter, die die folgenden Spalten und das folgende Format enthält:

   ```
   TYPE,VALUE,COMMENT
   EMAIL,abc@somedomain.com,Comment
   DOMAIN,somedomain.com,Comment
   ```

   >[!CAUTION]
   >
   >Ändern Sie nicht die Namen der Spalten in der CSV-Vorlage.
   >
   >Die Dateigröße darf 1 MB nicht überschreiten.

1. Füllen Sie die CSV-Vorlage mit den E-Mail-Adressen und/oder Domains aus, die Sie der Unterdrückungsliste hinzufügen möchten.

   >[!NOTE]
   >
   >Alle ASCII-Zeichen zwischen 32 und 126 sind in der Spalte **Kommentar** zulässig. Die vollständige Liste finden Sie zum Beispiel auf [dieser Seite](https://en.wikipedia.org/wiki/Wikipedia:ASCII#ASCII_printable_characters){target="_blank"}.

1. Ziehen Sie danach die CSV-Datei per Drag-and-Drop in den entsprechenden Bereich und klicken Sie auf **[!UICONTROL Senden]**.

>[!NOTE]
>
>Vergewissern Sie sich nach dem Hochladen, dass der Upload erfolgreich war, indem Sie seinen Status in der Benutzeroberfläche überprüfen. [Weitere Informationen dazu](#recent-uploads)

### Status der letzten Uploads überprüfen {#recent-uploads}

Klicken Sie die Schaltfläche **[!UICONTROL Letzte Uploads]**, um den Status der zuletzt hochgeladenen CSV-Dateien zu überprüfen.

Mögliche Status sind:

* **[!UICONTROL Ausstehend]**: Der Datei-Upload wird ausgeführt.
* **[!UICONTROL Fehler]**: Der Datei-Upload-Vorgang ist aufgrund eines technischen Problems oder eines Dateiformatfehlers fehlgeschlagen.
* **[!UICONTROL Fertig]**: Der Datei-Upload-Vorgang wurde erfolgreich abgeschlossen.

Wenn beim Hochladen einige Adressen nicht das richtige Format aufweisen, werden sie nicht der globalen Unterdrückungsliste hinzugefügt.

Wenn der Upload abgeschlossen ist, wird er in diesem Fall mit einem Bericht verknüpft. Sie können ihn herunterladen, um die aufgetretenen Fehler zu überprüfen.

## Entfernen von Adressen

Um eine Adresse aus der globalen Unterdrückungsliste zu entfernen, verwenden Sie die Schaltfläche **[!UICONTROL Löschen]**.

>[!CAUTION]
>
>Adressen oder Domains, die automatisch vom Drittdienstleister Blackbox hinzugefügt werden, können von der Beraterin oder dem Berater nicht über die Schnittstelle entfernt werden. Dies ist nur über ein Backend-Ticket möglich.
