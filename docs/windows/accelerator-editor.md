---
title: Zugriffstasten-Editor (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.accelerator.F1
- vc.editors.accelerator
helpviewer_keywords:
- accelerator tables [C++], editing
- tables [C++], accelerator key
- accelerator keys [C++]
- resource editors [C++], Accelerator editor
- keyboard shortcuts [C++], Accelerator editor
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
- VIRTKEY
- Key property
- ID property
- accelerator tables [C++], editing
- keyboard shortcuts [C++], editing in an accelerator table
- searching, in accelarator tables
- accelerator tables [C++], finding entries
- accelerator tables [C++], adding entries
- New Accelerator command
- accelerator tables [C++], deleting entries
- keyboard shortcuts [C++], deleting entry from accelerator table
- accelerator tables [C++], copying entries
- rc files [C++], moving an accelerator table entry
- .rc files [C++], moving accelerator table entries
- accelerator tables [C++], moving entries
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: 013c30b6-5d61-4f1c-acef-8bd15bed7060
ms.openlocfilehash: c98ff1fd44b73b3f204e9b952836c387f7f21146
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353089"
---
# <a name="accelerator-editor-c"></a>Zugriffstasten-Editor (C++)

Eine Zugriffstasten Tabelle ist eine Windows-C++-Ressource, die eine Liste mit Zugriffstasten, die als Tastenkombinationen bezeichnet wird, sowie die Befehls Bezeichner enthält, die Ihnen zugeordnet sind. Ein Programm kann über mehrere Zugriffstastentabellen verfügen.

Normalerweise werden Zugriffstasten als Tastenkombinationen für Programmbefehle verwendet, die auch in einem Menü oder auf einer Symbolleiste verfügbar sind. Allerdings können Sie die Zugriffstastentabelle auch verwenden, um Tastenkombinationen für Befehle zu definieren, denen kein Objekt auf der Benutzeroberfläche zugeordnet ist.

> [!TIP]
> Wenn Sie den Zugriffstasten- **Editor**verwenden, klicken Sie mit der rechten Maustaste, um ein Kontextmenü mit häufigen Befehlen anzuzeigen. Die verfügbaren Befehle hängen davon ab, auf was der Zeiger verweist.

Sie können die [Klassenansicht](/visualstudio/ide/viewing-the-structure-of-code) verwenden, um Zugriffstastenbefehle mit Code zu verknüpfen. Eine Liste der vordefinierten Zugriffstasten finden Sie unter Zugriffs [Tasten](predefined-accelerator-keys.md).

> [!NOTE]
> Windows lässt nicht zu, dass leere Zugriffstasten Tabellen erstellt werden. Wenn Sie eine Zugriffstastentabelle ohne Einträge erstellen, wird diese beim Speichern automatisch gelöscht.

## <a name="accelerator-properties"></a>Zugriffstasten Eigenschaften

Sie können Zugriffstasten Eigenschaften jederzeit in der [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window) festlegen. Sie können auch den Zugriffstasten- **Editor** verwenden, um die Eigenschaften der Zugriffstaste in der Zugriffstasten Tabelle zu ändern. Änderungen, die über das **Eigenschaften** Fenster oder den Zugriffstasten- **Editor** vorgenommen wurden, haben dasselbe Ergebnis. Änderungen werden sofort in der Zugriffstasten Tabelle widergespiegelt.

Die **ID** -Eigenschaft verweist auf jeden Zugriffstasten Tabelleneintrag im Programmcode. Dieser Eintrag ist der Befehls Wert, den das Programm empfängt, wenn ein Benutzer die Zugriffstaste oder eine Tastenkombination drückt. Um eine Zugriffstaste mit einem Menü Element identisch zu machen, machen Sie die **ID** identisch, solange die **ID** der Zugriffstasten Tabelle mit der **ID** für die Menü Ressource übereinstimmt.

Jede Zugriffstasten- **ID** hat drei Eigenschaften: **Modifizierer**, **Key**und **Type** .

Die **Modifier** -Eigenschaft legt Tastenkombinationen für die Zugriffstaste fest.

> [!NOTE]
> Im Fenster **Eigenschaften** wird die **modifizierereigenschaft** als drei separate **boolesche** Eigenschaften angezeigt, die alle unabhängig voneinander gesteuert werden können: **alt**, **STRG**und **UMSCHALT**.

Im folgenden sind die rechtlichen Einträge für die **modifizierereigenschaft** in der Zugriffstasten Tabelle aufgeführt:

   |Wert|BESCHREIBUNG|
   |-----------|-----------------|
   |**None**|Der Benutzer drückt nur den **Schlüssel** Wert.<br/><br/>Dieser Wert wird am effektivsten mit den ASCII/ANSI-Werten 001 bis 026 verwendet, der als ^ A bis ^ Z (**STRG + A** bis **STRG + Z**) interpretiert wird.|
   |**Alt**|Der Benutzer muss vor dem **Schlüssel** Wert **alt** drücken.|
   |**Ctrl**|Der Benutzer muss vor dem **Schlüssel** Wert **STRG** drücken, der mit dem ASCII-Typ nicht gültig ist.|
   |**Shift**|Der Benutzer muss vor dem Schlüsselwert **UMSCHALT** **Taste** drücken.|
   |**STRG + ALT**|Der Benutzer muss vor dem **Schlüssel** Wert **STRG** und **alt** drücken, und der ASCII-Typ ist ungültig.|
   |**STRG + UMSCHALT**|Der Benutzer muss **STRG** und **UMSCHALT** vor dem **Schlüssel** Wert drücken, nicht gültig mit dem ASCII-Typ.|
   |**Alt + Umschalttaste**|Der Benutzer muss **alt** und **UMSCHALT** vor dem **Schlüssel** Wert drücken, der mit dem ASCII-Typ nicht gültig ist.|
   |**Strg + Alt + Umschalttaste**|Der Benutzer muss **STRG**, **alt**und **UMSCHALT** vor dem **Schlüssel** Wert drücken, der mit dem ASCII-Typ nicht gültig ist.|

Die **Key** -Eigenschaft legt den eigentlichen Schlüssel fest, der als Zugriffstaste verwendet werden soll.

Im folgenden sind die rechtlichen Einträge für die Key-Eigenschaft in der Zugriffs **Tasten** Tabelle aufgeführt:

   |Wert|BESCHREIBUNG|
   |-----------|-----------------|
   |Eine ganze Zahl zwischen 0 und 255 im Dezimal Format.|Der-Wert bestimmt wie folgt, ob der-Wert als ASCII oder ANSI behandelt wird:<br/><br/>   -Einstellige Zahlen werden immer als der entsprechende Schlüssel interpretiert, nicht als ASCII-oder ANSI-Werte.<br/>   -Werte von 1 bis 26 werden bei vorangestellten Nullen als ^ A bis ^ Z interpretiert, was den ASCII-Wert der Buchstaben des Alphabets darstellt, wenn mit der **STRG** -Taste gedrückt wird.<br/>   -Die Werte aus 27-32 werden immer als dreistellige Dezimalwerte von 027 bis 032 interpretiert.<br/>   -Werte zwischen 033 und 255, ob mit 0 (null) oder nicht, werden als ANSI-Werte interpretiert.|
   |Ein einzelnes Tastatur Zeichen.|Großbuchstabe A-Z oder die Zahlen 0-9 können entweder ASCII-oder Virtual Key-Werte sein. Jedes andere Zeichen ist nur ASCII.|
   |Ein einzelnes Tastatur Zeichen im Bereich von a-Z (nur in Großbuchstaben), dem ein Caretzeichen (^) vorangestellt ist, z. b. ^ C.|Diese Option gibt den ASCII-Wert des Schlüssels ein, wenn er mit der **STRG** -Taste gedrückt wird.|
   |Jeder gültige virtuelle Schlüssel Bezeichner.|Das Dropdown- **Schlüssel** Feld in der Zugriffstasten Tabelle enthält eine Liste mit standardmäßigen virtuellen Schlüssel bezeichnerbezeichner.|

> [!NOTE]
> Wenn Sie einen ASCII-Wert eingeben, sind die Eigenschaften Optionen für **Modifizierer** eingeschränkt. Der einzige für die Verwendung verfügbare Steuerungs Schlüssel ist die **alt** -Taste.

> [!TIP]
> Eine Tastenkombination zum Definieren einer Zugriffstaste besteht darin, mit der rechten Maustaste auf einen Eintrag oder mehrere Einträge in der Zugriffstasten Tabelle zu klicken. Klicken Sie anschließend auf weiter **typisierte Taste** , und drücken Sie die Tastenkombination oder die Tastenkombination auf der Tastatur.
>
> Der **nächste Schlüssel** Befehl, der eingegeben wird, ist auch über das Menü **Bearbeiten** verfügbar.

Die **Type** -Eigenschaft bestimmt, ob die Tastenkombination, die der Zugriffstasten- **ID** zugeordnet ist, als ASCII/ANSI-Schlüsselwert oder Virtual Key (VIRTKEY)-Kombination interpretiert wird.

- Wenn es sich bei der **Type** -Eigenschaft um **ASCII**handelt, kann die **modifizierereigenschaft** nur `None` oder sein `Alt` , oder Sie kann über eine Zugriffstaste verfügen, die die **STRG** -Taste verwendet, wie durch vorangestellt vor dem Schlüssel mit einem angegeben `^` .

- Wenn die **Type** -Eigenschaft **VIRTKEY**ist, ist eine beliebige Kombination von **Modifiziererwerten** und **Schlüssel** Werten gültig.

> [!NOTE]
> Wenn Sie einen Wert in die Zugriffstasten Tabelle eingeben und den Wert als ASCII/ANSI behandeln möchten, wählen Sie den **Typ** für den Eintrag in der Tabelle aus, und wählen Sie in der Dropdown Liste **ASCII** aus. Wenn Sie jedoch den Befehl " **Next Key typisiert** " im Menü " **Bearbeiten** " verwenden, um den **Schlüssel**anzugeben, müssen Sie die **Type** -Eigenschaft von **VIRTKEY** in **ASCII** ändern, *bevor* Sie den **Schlüssel** Code eingeben.

## <a name="accelerator-tables"></a>Zugriffstasten Tabellen

In einem C++-Projekt können Sie eine Zugriffstasten Tabelle direkt mit direkter Bearbeitung im Zugriffstasten- **Editor**bearbeiten.

Die folgenden Verfahren beziehen sich auf die Verwendung von Standard Eigenschafts Seiten. die direkte Bearbeitung und die Eigenschaften Seiten Methode haben jedoch das gleiche Ergebnis. Änderungen, die mithilfe von Eigenschaften Seiten oder der direkten Bearbeitung vorgenommen wurden, werden sofort in der Zugriffstasten Tabelle widergespiegelt.

### <a name="to-edit-in-an-accelerator-table"></a>So führen Sie die Bearbeitung in einer Zugriffstastentabelle durch

1. Öffnen Sie die Zugriffstasten Tabelle, indem Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)auf das zugehörige Symbol doppelklicken.

1. Wählen Sie einen Eintrag in der Tabelle aus, und wählen Sie aus, um die direkte Bearbeitung zu aktivieren.

1. Wählen Sie aus dem Dropdown-Kombinations Feld aus, oder geben Sie ein, um Änderungen vorzunehmen:

   - Wählen Sie für **ID**aus der Liste oder dem zu bearbeitenden Typ aus.

   - Wählen Sie für **Modifizierer**aus der Liste aus.

   - Wählen Sie für **Schlüssel**aus der Liste oder dem zu bearbeitenden Typ aus.

   - Wählen Sie unter **Typ**die Option **ASCII** oder **VIRTKEY** aus der Liste aus.

### <a name="to-find-an-entry-in-an-open-accelerator-table"></a>So suchen Sie einen Eintrag in einer geöffneten Zugriffstastentabelle

1. Öffnen Sie die Zugriffstasten Tabelle, indem Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)auf das zugehörige Symbol doppelklicken.

1. Wählen Sie eine Spalten Kopfzeile aus, um den Inhalt der Spalte alphabetisch zu sortieren. Wählen Sie beispielsweise **ID** aus, um alle IDs in der Zugriffstasten Tabelle alphabetisch anzuzeigen.

   Sie können die Liste dann durchsuchen und den gewünschten Eintrag finden.

### <a name="to-add-an-entry-to-an-accelerator-table"></a>So fügen Sie einer Zugriffstastentabelle einen Eintrag hinzu

1. Öffnen Sie die Zugriffstasten Tabelle, indem Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)auf das zugehörige Symbol doppelklicken.

1. Klicken Sie mit der rechten Maustaste in die Zugriffstasten Tabelle, und wählen Sie **neue**Zugriffstaste, oder klicken Sie auf den leeren Zeileneintrag unten in der Tabelle.

1. Wählen Sie in der Dropdown Liste im Feld **ID** eine **ID** aus, oder geben Sie im Feld **ID** eine neue *ID* ein.

1. Geben Sie den *Schlüssel* ein, den Sie als Zugriffstaste verwenden möchten, oder klicken Sie mit der rechten Maustaste, und wählen Sie **weiter Schlüssel typisiert** aus **Edit**, um eine Tastenkombination festzulegen  >  **Next Key Typed**.

1. Ändern Sie ggf. den **Modifizierer** und den **Typ**, und drücken **Sie die Eingabe**Taste.

> [!NOTE]
> Stellen Sie sicher, dass alle von Ihnen definierten Zugriffstasten eindeutig sind. Sie können der gleichen ID mehrere Tastenkombinationen zuweisen, ohne dass eine Beeinträchtigung beeinträchtigt wird, z. b. Wenn **STRG** + **P** und **F8** ID_PRINT zugewiesen werden können. Eine Tastenkombination, die mehr als einer ID zugewiesen ist, funktioniert jedoch nicht gut, z. b. ist **STRG** + **Z** sowohl ID_SPELL_CHECK als auch ID_THESAURUS zugewiesen.

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>So löschen Sie einen Eintrag aus einer Zugriffstastentabelle

1. Öffnen Sie die Zugriffstasten Tabelle, indem Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)auf das zugehörige Symbol doppelklicken.

1. Wählen Sie den Eintrag aus, den Sie löschen möchten, oder halten Sie die **STRG** -oder **UMSCHALT** Taste gedrückt, während Sie mehrere Einträge auswählen.

1. Klicken Sie mit der rechten Maustaste, und wählen Sie **Löschen**aus, oder wechseln Sie zum Menü Menü **Bearbeiten**  >  **Delete**

> [!TIP]
> Sie können auch die ENTF-Taste **zum Löschen drücken** .

### <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>So verschieben oder kopieren Sie einen Eintrag in einer Zugriffstastentabelle in eine andere Ressourcenskriptdatei

1. Öffnen Sie die Zugriffstasten Tabellen in beiden Ressourcen Skriptdateien, und wählen Sie den Eintrag aus, den Sie verschieben möchten.

1. Wählen Sie im Menü **Bearbeiten** die Option **Kopieren** oder **Ausschneiden**aus.

1. Wählen Sie einen Eintrag in der Ziel Ressourcen-Skriptdatei aus, und wählen Sie im Menü **Bearbeiten** die Option **Einfügen**aus.

> [!NOTE]
> Zum Kopieren und Einfügen können Sie auch Tastenkombinationen verwenden.

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>So ändern Sie die Eigenschaften mehrerer Zugriffstasten

1. Öffnen Sie die Zugriffstasten Tabelle, indem Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)auf das zugehörige Symbol doppelklicken.

1. Wählen Sie die Tastenkombinationen aus, die Sie ändern möchten, indem Sie die **STRG** -Taste gedrückt halten, während Sie diese auswählen.

1. Wechseln Sie zum [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window) , und geben Sie die Werte ein, die von allen ausgewählten Accelerators gemeinsam genutzt werden sollen.

> [!NOTE]
> Jeder Modifiziererwert wird im **Eigenschaften** Fenster als boolesche Eigenschaft angezeigt. Wenn Sie einen Modifiziererwert im **Eigenschaften** Fenster ändern, behandelt die Zugriffstasten Tabelle den neuen Modifizierer als Ergänzung zu allen zuvor gefundenen Modifizierern. Wenn Sie daher einen Modifiziererwert festlegen, müssen Sie alle festlegen, um sicherzustellen, dass jede Zugriffstaste die gleichen **Modifizierereinstellungen** gemeinsam nutzt.

## <a name="requirements"></a>Requirements (Anforderungen)

Win32

## <a name="see-also"></a>Weitere Informationen

[Ressourcen-Editoren](resource-editors.md)<br/>
[Zugriffstasten](predefined-accelerator-keys.md)<br/>
