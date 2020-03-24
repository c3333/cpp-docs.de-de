---
title: Zeichen folgen-C++Editor ()
ms.date: 02/14/2019
f1_keywords:
- vc.editors.string.F1
- vc.editors.string
helpviewer_keywords:
- String editor
- string tables
- string tables [C++], String editor
- string editing
- string editing, string tables
- resource editors [C++], String editor
- strings [C++], editing
- strings [C++], searching
- strings [C++]
- strings [C++], adding to string tables
- string tables [C++], deleting strings
- strings [C++], deleting in string tables
- string tables [C++], adding strings
- strings [C++], moving between files
- resource script files [C++], moving strings
- string editing, moving strings between resources
- String editor [C++], moving strings between files
- resource identifiers, string properties
- string tables [C++], changing strings
- strings [C++], properties
- String editor [C++], changing properties of multiple strings
- string tables [C++], changing caption of multiple strings
- special characters, adding to strings
- ASCII characters, adding to strings
- strings [C++], formatting
- strings [C++], special characters
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
ms.openlocfilehash: 1f9b21893bd361d02b3446360b24a97f4d1d1365
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214408"
---
# <a name="string-editor-c"></a>Zeichen folgen-C++Editor ()

Eine Zeichenfolgentabelle in einer Windows-Ressource, die eine Liste mit IDs, Werten und Beschriftungen für alle Zeichenfolgen Ihrer Anwendung enthält. Beispielsweise befinden sich die Statusleistenmeldungen in der Zeichenfolgentabelle.

Beim Entwickeln einer Anwendung können Sie mehrere Zeichenfolgentabellen verwenden – eine für jede Sprache oder Bedingung. Ein ausführbares Moduls weist jedoch nur eine Zeichenfolgentabelle auf. Eine ausgeführte Anwendung kann auf verschiedene Zeichenfolgentabellen verweisen, wenn Sie die Tabellen in verschiedenen DLLs platzieren.

Mithilfe von Zeichenfolgentabellen können Sie Ihre Anwendung bequem in verschiedene Sprachen lokalisieren. Wenn sich alle Zeichenfolgen in einer Zeichenfolgentabelle befinden, können Sie die Anwendung lokalisieren, indem Sie die Zeichenfolgen (und andere Ressourcen) übersetzen, ohne den Quellcode zu ändern. Diese Situation ist besser erwünscht als das manuelle suchen und ersetzen verschiedener Zeichen folgen in Quelldateien.

> [!NOTE]
> Windows lässt die Erstellung leerer Zeichen folgen Tabellen nicht zu. Wenn Sie eine Zeichenfolgentabelle ohne Einträge erstellen, wird sie beim Speichern der Ressourcendatei automatisch gelöscht.

## <a name="how-to"></a>Vorgehensweise

Der **Zeichen** folgen-Editor ermöglicht Ihnen Folgendes:

### <a name="to-find-a-string-resource-in-the-string-table"></a>So suchen Sie eine Zeichen folgen Ressource in der Zeichen folgen Tabelle

1. Öffnen Sie die Zeichen folgen Tabelle, indem Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)auf das zugehörige Symbol doppelklicken.

1. Wechseln Sie zum Menü **Bearbeiten** > **Suchen und ersetzen** , und klicken Sie auf **Suchen**.

1. Wählen Sie im Feld **Suchen** nach eine vorherige Such Zeichenfolge aus der Dropdown Liste aus, oder geben Sie den Beschriftungs Text oder den Ressourcen Bezeichner der Zeichenfolge ein, die Sie suchen möchten.

1. Wählen Sie **eine der Suchoptionen aus** , und klicken Sie auf **weiter suchen**.

> [!TIP]
> Um [reguläre Ausdrücke](/visualstudio/ide/using-regular-expressions-in-visual-studio) beim Durchsuchen von Dateien zu verwenden, verwenden Sie den Befehl **in Dateien suchen** im Menü **Bearbeiten** .
>
> Geben Sie einen regulären Ausdruck ein, um eine Entsprechung für ein Muster festzustellen, oder klicken Sie auf die Schaltfläche rechts neben dem Feld **Suchen** nach, um eine Liste regulärer Such Ausdrücke anzuzeigen Wenn Sie einen Ausdruck aus dieser Liste auswählen, wird dieser als Suchtext **im Feld Suchen** nach ersetzt.
>
> Wenn Sie reguläre Ausdrücke verwenden, stellen Sie sicher, dass das Kontrollkästchen **use: reguläre Ausdrücke** aktiviert ist.

### <a name="to-add-or-delete-a-string-resource"></a>So können Sie eine Zeichen folgen Ressource hinzufügen oder löschen

Mithilfe des Zeichen folgen- **Editors**können Sie schnell Einträge in die Zeichen folgen Tabelle einfügen oder löschen. Neue Zeichen folgen werden am Ende der Tabelle platziert und erhalten den nächsten verfügbaren Bezeichner. Sie können die Eigenschaften " **ID**", " **Wert**" oder " **Caption** " im [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window) nach Bedarf bearbeiten.

Der **Zeichen** folgen-Editor stellt sicher, dass Sie keine ID verwenden, die bereits verwendet wird. Wenn Sie eine bereits verwendete ID auswählen, werden Sie vom Zeichen folgen- **Editor** benachrichtigt, und anschließend wird eine generische eindeutige ID zugewiesen, z. b. `IDS_STRING58113`.

#### <a name="to-add-a-string-table-entry"></a>So fügen Sie einen Eintrag der Zeichen folgen Tabelle hinzu

1. Öffnen Sie die Zeichen folgen Tabelle, indem Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)auf das zugehörige Symbol doppelklicken.

1. Klicken Sie mit der rechten Maustaste in die Zeichen folgen Tabelle, und wählen Sie **neue Zeichenfolge**

1. Wählen Sie **im Zeichen**folgen-Editor in der Dropdown Liste **ID** eine **ID** aus, oder geben Sie direkt direkt eine *ID* ein.

1. Bearbeiten Sie ggf. den **Wert**.

1. Geben Sie einen Eintrag für die **Beschriftung**ein.

   > [!NOTE]
   > NULL-Zeichen folgen sind in Windows-Zeichen folgen Tabellen nicht zulässig. Wenn Sie einen Eintrag in der Zeichen folgen Tabelle erstellen, bei der es sich um eine NULL-Zeichenfolge handelt, erhalten Sie eine Meldung, in der Sie aufgefordert werden, **eine Zeichenfolge für diesen Tabelleneintrag einzugeben**.

#### <a name="to-delete-a-string-table-entry"></a>So löschen Sie einen Eintrag für eine Zeichen folgen Tabelle

Wählen Sie den Eintrag aus, den Sie löschen möchten, und führen Sie einen der folgenden Schritte aus:

- Wechseln Sie zum Menü **Bearbeiten** > **Löschen**.

- Klicken Sie mit der rechten Maustaste auf die zu löschende Zeichenfolge, **und wählen**

- Drücken Sie **die** ENTF-Taste.

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>So verschieben Sie eine Zeichenfolge aus einer Ressourcen Skriptdatei in eine andere

1. [Öffnen Sie die Zeichen folgen Tabellen in beiden RC-Dateien](../windows/how-to-create-a-resource-script-file.md).

1. Klicken Sie mit der rechten Maustaste auf die Zeichenfolge, und wählen Sie **Ausschneiden**

1. Platzieren Sie den Cursor im Fenster Ziel-Zeichen folgen- **Editor** .

1. Klicken Sie in der *RC* -Datei, in die Sie die Zeichenfolge verschieben möchten, mit der rechten Maustaste, und wählen Sie **Einfügen**aus.

> [!NOTE]
> Wenn die **ID** oder der **Wert** der verschostellenden Zeichenfolge mit einer vorhandenen **ID** oder einem **Wert** in der Zieldatei in Konflikt steht, ändert sich entweder die **ID** oder der **Wert der verschostellenden** Zeichenfolge.

### <a name="to-change-the-properties-of-a-string-resource"></a>So ändern Sie die Eigenschaften einer Zeichen folgen Ressource

Sie können die direkte Bearbeitung verwenden, um die Eigenschaften " **ID**", " **Wert**" und " **Beschriftung** " zu ändern.

> [!NOTE]
>  Sie können auch die Eigenschaften einer Zeichenfolge in der [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window)bearbeiten.

#### <a name="to-change-a-string-or-its-identifier"></a>So ändern Sie eine Zeichenfolge oder Ihren Bezeichner

1. Öffnen Sie die Zeichen folgen Tabelle, indem Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)auf das zugehörige Symbol doppelklicken.

1. Wählen Sie die Zeichenfolge aus, die Sie bearbeiten möchten, und doppelklicken Sie auf die Spalte **ID**, **Wert**oder **Beschriftung** , dann können Sie folgende Aktionen ausführen:

   - Wählen Sie in der Dropdown Liste **ID** eine **ID** aus, oder geben Sie direkt direkt eine *ID* ein.

   - Geben Sie eine andere Zahl in die Spalte **Wert** ein.

   - Geben Sie in der Spalte **Beschriftung** bearbeitbare Änderungen ein.

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>So ändern Sie die Caption-Eigenschaft mehrerer Zeichen folgen Ressourcen

1. Öffnen Sie die Zeichen folgen Tabelle, indem Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)auf das zugehörige Symbol doppelklicken.

1. Wählen Sie die Zeichen folgen aus, die Sie ändern möchten, indem Sie die **STRG** -Taste gedrückt halten, während Sie diese auswählen.

1. Geben Sie im [Eigenschaften Fenster](/visualstudio/ide/reference/properties-window)einen neuen Wert für die Eigenschaft ein, die Sie ändern möchten.

1. Drücken Sie die **EINGABETASTE**.

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>So fügen Sie einer Zeichen folgen Ressource Formatierungen oder Sonderzeichen hinzu

1. Öffnen Sie die Zeichen folgen Tabelle, indem Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)auf das zugehörige Symbol doppelklicken.

1. Wählen Sie die Zeichenfolge aus, die Sie ändern möchten.

1. Fügen Sie im [Fenster Eigenschaften](/visualstudio/ide/reference/properties-window)eine der unten aufgeführten Standard-Escapesequenzen dem Text im Feld **Beschriftung** hinzu, und drücken **Sie die Eingabe**Taste.

   |Um dies zu erreichen...|Eingeben...|
   |-----------------|---------------|
   | Neue Zeile | \\n |
   | Wagenrücklauf | \\r |
   | Registerkarte | \\t |
   | Umgekehrter Schrägstrich (\\) | \\\\ |
   | ASCII-Zeichen | \\ddd (Oktale Notation) |
   | Warnung (Glocken) | \\a |

   > [!NOTE]
   > Der **Zeichen** folgen-Editor unterstützt nicht den vollständigen Satz mit Escapezeichen. Sie können nur die oben aufgeführten verwenden.

## <a name="requirements"></a>Requirements (Anforderungen)

Win32

## <a name="see-also"></a>Weitere Informationen

[Ressourcen-Editoren](../windows/resource-editors.md) [
Zeichen](/windows/win32/menurc/strings) folgen<br/>
[Informationen über Zeichenfolgen](/windows/win32/menurc/about-strings)<br/>
[Anpassen von Fensterlayouts](/visualstudio/ide/customizing-window-layouts-in-visual-studio)
