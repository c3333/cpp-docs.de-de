---
title: String-Editor (C++)
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
ms.openlocfilehash: b0fb077752cf1912e07175c68cdc8acfe758b0c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370240"
---
# <a name="string-editor-c"></a>String-Editor (C++)

Eine Zeichenfolgentabelle in einer Windows-Ressource, die eine Liste mit IDs, Werten und Beschriftungen für alle Zeichenfolgen Ihrer Anwendung enthält. Beispielsweise befinden sich die Statusleistenmeldungen in der Zeichenfolgentabelle.

Beim Entwickeln einer Anwendung können Sie mehrere Zeichenfolgentabellen verwenden – eine für jede Sprache oder Bedingung. Ein ausführbares Moduls weist jedoch nur eine Zeichenfolgentabelle auf. Eine ausgeführte Anwendung kann auf verschiedene Zeichenfolgentabellen verweisen, wenn Sie die Tabellen in verschiedenen DLLs platzieren.

Mithilfe von Zeichenfolgentabellen können Sie Ihre Anwendung bequem in verschiedene Sprachen lokalisieren. Wenn sich alle Zeichenfolgen in einer Zeichenfolgentabelle befinden, können Sie die Anwendung lokalisieren, indem Sie die Zeichenfolgen (und andere Ressourcen) übersetzen, ohne den Quellcode zu ändern. Diese Situation ist wünschenswerter als das manuelle Suchen und Ersetzen verschiedener Zeichenfolgen in Quelldateien.

> [!NOTE]
> Windows lässt die Erstellung leerer Zeichenfolgentabellen nicht zu. Wenn Sie eine Zeichenfolgentabelle ohne Einträge erstellen, wird sie beim Speichern der Ressourcendatei automatisch gelöscht.

## <a name="how-to"></a>Vorgehensweise

Der **String-Editor** ermöglicht Ihnen:

### <a name="to-find-a-string-resource-in-the-string-table"></a>So suchen Sie eine Zeichenfolgenressource in der Zeichenfolgentabelle

1. Öffnen Sie die Zeichenfolgentabelle, indem Sie auf ihr Symbol in [der Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)doppelklicken.

1. Gehen Sie zum Menü **Suchen** > **suchen und Ersetzen und** wählen Sie **Suchen**.

1. Wählen Sie im Feld **Suchen Was** eine vorherige Suchzeichenfolge aus der Dropdownliste aus, oder geben Sie den Beschriftungstext oder Ressourcenbezeichner der Zeichenfolge ein, die Sie suchen möchten.

1. Wählen Sie eine der **Suchoptionen** aus, und wählen Sie **Weiter suchen**aus.

> [!TIP]
> Um [reguläre Ausdrücke](/visualstudio/ide/using-regular-expressions-in-visual-studio) beim Suchen von Dateien zu verwenden, verwenden Sie den Befehl **Dateien suchen** im Menü **Bearbeiten.**
>
> Geben Sie einen regulären Ausdruck ein, der einem Muster entspricht, oder wählen Sie die Schaltfläche rechts neben dem Feld **Suchen was** aus, um eine Liste regulärer Suchausdrücke anzuzeigen. Wenn Sie einen Ausdruck aus dieser Liste auswählen, wird er als Suchtext im Feld **Suchen ersetzt.**
>
> Wenn Sie reguläre Ausdrücke verwenden, stellen Sie sicher, dass das Kontrollkästchen **Verwenden: Reguläre Ausdrücke** aktiviert ist.

### <a name="to-add-or-delete-a-string-resource"></a>So fügen Sie eine Zeichenfolgenressource hinzu oder löschen sie

Mit dem **String-Editor**können Sie schnell Einträge in die Zeichenfolgentabelle einfügen oder löschen. Neue Zeichenfolgen werden am Ende der Tabelle platziert und erhalten den nächsten verfügbaren Bezeichner. Sie können die **Eigenschaften ID**, **Wert**oder **Beschriftung** im [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window) nach Bedarf bearbeiten.

Der **Zeichenfolgen-Editor** stellt sicher, dass Sie keine ID verwenden, die bereits verwendet wird. Wenn Sie eine bereits in Gebrauch eggf. ID auswählen, benachrichtigen `IDS_STRING58113`Sie der **String-Editor** und weisen dann eine generische eindeutige ID zu, z. B. .

#### <a name="to-add-a-string-table-entry"></a>So fügen Sie einen Zeichenfolgentabelleneintrag hinzu

1. Öffnen Sie die Zeichenfolgentabelle, indem Sie auf ihr Symbol in [der Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)doppelklicken.

1. Klicken Sie mit der rechten Maustaste in die Zeichenfolgentabelle, und wählen Sie **Neue Zeichenfolge**aus.

1. Wählen Sie im **String-Editor**eine **ID** aus der Dropdown-Liste **ID** aus, oder geben Sie eine *ID* direkt ein.

1. Bearbeiten Sie ggf. den **Wert.**

1. Geben Sie einen Eintrag für die **Beschriftung**ein.

   > [!NOTE]
   > Nullzeichenfolgen sind in Windows-Zeichenfolgentabellen nicht zulässig. Wenn Sie einen Eintrag in der Zeichenfolgentabelle erstellen, der eine Nullzeichenfolge ist, erhalten Sie eine Meldung, in der Sie aufgefordert werden, **eine Zeichenfolge für diesen Tabelleneintrag einzugeben.**

#### <a name="to-delete-a-string-table-entry"></a>So löschen Sie einen Zeichenfolgentabelleneintrag

Wählen Sie den Eintrag aus, den Sie löschen möchten, und wählen Sie einen der folgenden Schritte aus:

- Gehen Sie zum Menü **Löschen** > **bearbeiten**.

- Klicken Sie mit der rechten Maustaste auf die zu löschende Zeichenfolge, und wählen Sie **Löschen**aus.

- Drücken Sie die **Löschtaste.**

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>So verschieben Sie eine Zeichenfolge von einer Ressourcenskriptdatei in eine andere

1. [Öffnen Sie die Zeichenfolgentabellen in beiden .rc-Dateien](../windows/how-to-create-a-resource-script-file.md).

1. Klicken Sie mit der rechten Maustaste auf die Zeichenfolge, um sie zu verschieben, und wählen Sie **Ausschneiden**aus.

1. Platzieren Sie den Cursor im **Ziel-String-Editor-Fenster.**

1. Klicken Sie in der *.rc-Datei,* in die Sie die Zeichenfolge verschieben möchten, mit der rechten Maustaste und wählen **Sie Einfügen**.

> [!NOTE]
> Wenn die **ID** oder der **Wert** der verschobenen Zeichenfolge mit einer vorhandenen **ID** oder einem **vorhandenen Wert** in der Zieldatei in Konflikt steht, ändert sich entweder diese **ID** oder der **Wert** der verschobenen Zeichenfolge.

### <a name="to-change-the-properties-of-a-string-resource"></a>So ändern Sie die Eigenschaften einer Zeichenfolgenressource

Sie können die Ortsbearbeitung verwenden, um die **Eigenschaften ID**, **Wert**und **Beschriftung** zu ändern.

> [!NOTE]
> Sie können auch die Eigenschaften einer Zeichenfolge im [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window)bearbeiten.

#### <a name="to-change-a-string-or-its-identifier"></a>So ändern Sie eine Zeichenfolge oder ihren Bezeichner

1. Öffnen Sie die Zeichenfolgentabelle, indem Sie auf ihr Symbol in [der Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)doppelklicken.

1. Wählen Sie die Zeichenfolge aus, die Sie bearbeiten möchten, und doppelklicken Sie auf die Spalte **ID**, **Wert**oder **Beschriftung,** und können Sie dann:

   - Wählen Sie eine **ID** aus der Dropdown-Liste **ID** aus, oder geben Sie eine *ID* direkt an Ort und Stelle ein.

   - Geben Sie eine andere Zahl in die Spalte **Wert** ein.

   - Geben Sie Bearbeitungen in der **Spalte Beschriftung** ein.

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>So ändern Sie die Beschriftungseigenschaft mehrerer Zeichenfolgenressourcen

1. Öffnen Sie die Zeichenfolgentabelle, indem Sie auf ihr Symbol in [der Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)doppelklicken.

1. Wählen Sie die Zeichenfolgen aus, die Sie ändern möchten, indem Sie die **Strg-Taste** gedrückt halten, während Sie jede Zeichenfolge auswählen.

1. Geben Sie im [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window)einen neuen Wert für die Eigenschaft ein, die Sie ändern möchten.

1. Drücken Sie die **EINGABETASTE**.

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>So fügen Sie einer Zeichenfolgenressource Formatierungen oder Sonderzeichen hinzu

1. Öffnen Sie die Zeichenfolgentabelle, indem Sie auf ihr Symbol in [der Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)doppelklicken.

1. Wählen Sie die Zeichenfolge aus, die Sie ändern möchten.

1. Fügen Sie im [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window)eine der unten aufgeführten Standardescapesequenzen zum Text im Feld **Beschriftung** hinzu, und drücken Sie die **Eingabetaste**.

   |Um dies zu bekommen...|Geben Sie diese ein...|
   |-----------------|---------------|
   | Neue Zeile | \\n |
   | Wagenrücklauf | \\R |
   | Registerkarte | \\t |
   | Umgekehrter Schrägstrich (\\) | \\\\ |
   | ASCII-Zeichen | \\ddd (oktale Notation) |
   | Warnung (Glocke) | \\a |

   > [!NOTE]
   > Der **Zeichenfolgen-Editor** unterstützt nicht den vollständigen Satz von escape-asCI-Zeichen mit Escapezeichen. Sie können nur die oben aufgeführten verwenden.

## <a name="requirements"></a>Anforderungen

Win32

## <a name="see-also"></a>Siehe auch

[Resource Editors](../windows/resource-editors.md)
[Strings](/windows/win32/menurc/strings)<br/>
[Informationen über Zeichenfolgen](/windows/win32/menurc/about-strings)<br/>
[Anpassen von Fensterlayouts](/visualstudio/ide/customizing-window-layouts-in-visual-studio)
