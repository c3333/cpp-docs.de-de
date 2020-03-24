---
title: Signatur ändern
ms.date: 11/16/2016
ms.assetid: 8daaa060-7305-4035-99d2-8b460b4f4454
ms.openlocfilehash: 1599a7900e33db61994ea75581f9d87b1aee83f9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171904"
---
# <a name="change-signature"></a>Signatur ändern

**Zweck:** Ändern der Parameter einer Funktion.

**Wann:** Wenn Sie die Parameter einer Funktion neu anordnen, hinzufügen, entfernen oder ändern möchten, die derzeit an vielen Stellen verwendet wird.

**Grund:** Sie können diese Parameter eigenhändig manuell ändern und dann alle Aufrufe dieser Funktion suchen und nacheinander ändern, was jedoch zu Fehlern führen kann.  Bei diesem Refactoringtool wird der Task automatisch ausgeführt.

**Anwendung:**

1. Platzieren Sie Ihren Text oder Mauszeiger auf dem Namen der zu ändernden Methode oder auf einer deren Verwendungen:

   ![Markierter Code](images/changesignature_highlight.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+R** und dann **STRG+O**.  (Beachten Sie, dass Ihre Tastenkombination je nach dem gewählten Profil möglicherweise abweicht.)
     * Drücken Sie **STRG+.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen, und klicken Sie im Kontextmenü auf **Signatur ändern**.
   * **Maus**
     * Wählen Sie **Bearbeiten > Umgestalten > Parameter neu anordnen** aus.
     * Klicken Sie mit der rechten Maustaste auf den Code, und klicken Sie auf das Menü **Schnellaktionen und Refactorings**, klicken Sie dann im Kontextmenü auf **Signatur ändern**.

1. Mit den Schaltflächen auf der rechten Seite im angezeigten Dialogfeld **Signatur ändern** können Sie die Methodensignatur ändern:

   ![Dialogfeld „Signatur ändern“](images/changesignature_dialog.png)

   | Taste | BESCHREIBUNG
   | ------ | ---
   | **Nach oben/unten**    | Den ausgewählten Parameter in der Liste nach oben oder nach unten verschieben
   | **Add (Hinzufügen)**        | Einen neuen Parameter zur Liste hinzufügen
   | **Remove**     | Den ausgewählten Parameter aus der Liste entfernen
   | **Modify**     | Ändern Sie den Typ und Namen des ausgewählten Parameters, und geben Sie an, ob er optional ist und was sein eingefügter Wert wäre
   | **Zurücksetzen**     | Den ursprünglichen Zustand des ausgewählten Parameters wiederherstellen
   | **Alle zurücksetzen** | Den ursprünglichen Zustand aller Parameter wiederherstellen

   > [!TIP]
   > Verwenden Sie das Kontrollkästchen **Vorschau der Verweisänderungen überspringen, wenn alle Verweise bestätigt sind**, um die Änderungen sofort anzuwenden, ohne dass erst das Vorschaufenster angezeigt wird.

   Beim Hinzufügen oder Ändern eines Parameters wird das Fenster **Parameter hinzufügen** oder das Fenster **Parameter bearbeiten** angezeigt.

   ![Parameter hinzufügen/ändern](images/changesignature_addmodify.png)

   Hier stehen Ihnen folgende Optionen zur Verfügung:

   | Eintrag | BESCHREIBUNG
   | ----- | ---
   | **Typ**               | Der Typ des Parameters (int, double, float usw.)
   | **Name**               | Der Name des Parameters
   | **Optionaler Parameter** | Legt fest, dass der Parameter optional angegeben wird
   | **Eingefügter Wert**     | Der Wert, der in alle Aufrufe der Funktion eingefügt wird, für die der Parameter nicht angegeben wird (nur für **Hinzufügen** gültig)
   | **Standardwert**      | Der Wert, den die Funktion verwendet, wenn der Aufrufer keinen angibt (nur für **optionale Parameter** gültig)

1. Verwenden Sie die Dropdownliste **Suchbereich**, um auszuwählen, ob Änderungen auf das Projekt oder auf die gesamte Projektmappe angewendet werden.

1. Wenn Sie fertig sind, klicken Sie auf die Schaltfläche **OK**, um die Änderungen zu übernehmen.  Stellen Sie sicher, dass die von Ihnen angeforderten Änderungen ordnungsgemäß durchgeführt werden.  Verwenden Sie die Kontrollkästchen in der oberen Hälfte des Fensters, um das Umbenennen von Elementen zu aktivieren oder zu deaktivieren.

   ![Vorschau der Änderung einer Signatur](images/changesignature_preview.png)

1. Klicken Sie auf die Schaltfläche **Anwenden**, wenn Sie fertig sind, um die Funktion in Ihrem Quellcode zu ändern.

   ![Ergebnis der Aktion zum Ändern einer Signatur](images/changesignature_result.png)
