---
title: 'Gewusst wie: Verwalten von Symbolen'
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.changing
- vc.editors.symbol.restrictions.name
- vc.editors.symbol.changing.value
- vc.editors.symbol.restrictions.value
- vc.editors.symbol.changing.header
- vc.editors.symbol.changing.unassigned
- vc.editors.symbol.shared.calculated
helpviewer_keywords:
- symbol names
- symbols [C++], names
- restrictions, symbol names
- numeric values
- symbols [C++], numeric values
- numeric values, changing symbols
- symbols [C++], value restrictions
- restrictions, symbol values
- resource files [C++], multiple
- Resource Includes dialog box [C++]
- symbol header files [C++], changing names
- symbols [C++], symbol header files
- Resource.h
- symbols [C++], unassigned
- Change Symbol dialog box [C++]
- unassigned symbols
- symbols [C++], deleting
- symbols [C++], read-only
- symbols [C++], shared
- symbols [C++], calculated
- read-only symbols
- symbol directives
- calculated symbols
- shared symbols
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
ms.openlocfilehash: 67a5c801c13038e7215473edecc2d41a8f7086e0
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505725"
---
# <a name="how-to-manage-symbols"></a>Gewusst wie: Verwalten von Symbolen

Wenn Sie eine neue Ressource oder ein neues Ressourcen Objekt erstellen, weist die Entwicklungsumgebung ihr einen standardmäßigen Symbolnamen zu, z `IDD_DIALOG1` . b.. Sie können den [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window) verwenden, um den Standard Symbolnamen zu ändern oder um den Namen eines beliebigen Symbols zu ändern, das bereits einer Ressource zugeordnet ist.

Bei Symbolen, die einer einzelnen Ressource zugeordnet sind, können Sie auch das **Eigenschaften** Fenster verwenden, um den Symbolwert zu ändern. Sie können das [Dialogfeld Ressourcen Symbole](./creating-new-symbols.md) verwenden, um den Wert von Symbolen zu ändern, die derzeit nicht einer Ressource zugewiesen sind.

Normalerweise werden alle Symbol Definitionen in gespeichert `Resource.h` . Jedoch müssen Sie den Namen dieser Includedatei möglicherweise ändern, sodass Sie z. B. mit mehr als eine Ressourcendatei im selben Verzeichnis arbeiten können.

> [!NOTE]
> Wenn das Projekt noch keine RC-Datei enthält, finden Sie weitere Informationen unter Gewusst [wie: Erstellen von Ressourcen](how-to-create-a-resource-script-file.md).

## <a name="symbol-name-restrictions"></a>Beschränkungen bei Symbolnamen

Die Einschränkungen für Symbolnamen lauten wie folgt:

- Alle [Symbole](symbols-resource-identifiers.md) müssen innerhalb des Gültigkeits Bereichs der Anwendung eindeutig sein, um widersprüchliche Symbol Definitionen in den Header Dateien zu verhindern.

- Zu den gültigen Zeichen für einen Symbolnamen zählen A–Z, a–z, 0–9 und Unterstriche ( – ).

- Symbol Namen dürfen nicht mit einer Zahl beginnen und sind auf 247 Zeichen beschränkt.

- Symbol Namen dürfen keine Leerzeichen enthalten.

- Bei Symbol Namen wird nicht nach Groß-/Kleinschreibung unterschieden, aber der Fall der ersten Symbol Definition wird beibehalten.

   Die die Symbole definierende Headerdatei wird durch den Ressourcencompiler/Editor und durch das bzw. die C++Programm(e) verwendet, um auf in einer Ressourcendatei definierte Ressourcen zu verweisen. Bei zwei Symbolnamen, die sich nur in der Groß-/Kleinschreibung unterscheiden, erkennt das C++-Programm zwei getrennte Symbole, während der Ressourcencompiler/Editor beide Namen als ein einzelnes Symbol erkennt.

> [!NOTE]
> Wenn Sie das unten beschriebene standardmäßige Symbol Namensschema (ID * _ [Schlüsselwort]) nicht befolgen und Ihr Symbol Name mit dem Schlüsselwort identisch ist, das dem Ressourcen Skript Compiler bekannt ist, führt der Versuch, die Ressourcen Skriptdatei zu erstellen, zu einer scheinbar zufälligen Fehler Generierung, die schwer zu diagnostizieren ist. Halten Sie sich an die standardmäßige Namensgebung, um dies zu verhindern.

Symbolnamen weisen beschreibende Präfixe auf, die die Art der Ressource oder des Objekts andeuten, die bzw. das sie repräsentieren. Diese beschreibenden Präfixe beginnen mit der Textkombinations-ID. Die MFC-Bibliothek (Microsoft Foundation Class) verwendet die in der folgenden Tabelle dargestellten Symbol Benennungs Konventionen:

|Category|Präfix|Verwendung|
|--------------|------------|---------|
|Ressourcen|IDR_, IDD_, IDC_, IDI_, IDB_|Zugriffstaste oder Menü (und zugeordnete oder benutzerdefinierte Ressourcen), Dialogfeld, Cursor, Symbol, Bitmap|
|Menüelemente|ID_|Menüelement|
|Befehle|ID_|Get-Help|
|Steuerelemente und untergeordnete Fenster|IDC_|Control|
|Zeichenfolgen|IDS_|Zeichenfolge in der Zeichenfolgentabelle|
|MFC|AFX_|Reserviert für vordefinierte MFC-Symbole|

### <a name="to-change-a-symbol-name-id"></a>So ändern Sie einen Symbolnamen (ID)

1. Wählen Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)die Ressource aus.

1. Geben Sie im **Eigenschaften** Fenster einen neuen Symbolnamen ein, oder wählen Sie aus der Liste der vorhandenen Symbole im Feld **ID** aus.

   Wenn Sie einen neuen Symbolnamen eingeben, wird ihm automatisch ein Wert zugewiesen.

> [!NOTE]
> Sie können das [Dialogfeld Ressourcen Symbole](./creating-new-symbols.md) verwenden, um die Namen von Symbolen zu ändern, die derzeit nicht einer Ressource zugewiesen sind.

## <a name="symbol-value-restrictions"></a>Beschränkungen bei Symbolwerten

Bei einem Symbolwert kann es sich um eine beliebige Ganzzahl handeln, die für `#define` Präprozessordirektiven normal ausgedrückt wird Hier sind einige Beispiele für Symbolwerte:

```
18
4001
0x0012
-3456
```

Symbol Werte für Ressourcen wie Acceleratoren, Bitmaps, Cursor, Dialogfelder, Symbole, Menüs, Zeichen folgen Tabellen und Versionsinformationen müssen Dezimalzahlen im Bereich zwischen 0 und 32.767 sein, aber nicht hexadezimal. Symbolwerte für Ressourcenbestandteile wie Dialogfeldsteuerelemente oder einzelne Zeichenfolgen in der Zeichenfolgentabelle können von 0 bis 65.534 oder von -32.768 bis 32.767 reichen. Weitere Informationen zu Zahlenbereichen finden Sie unter [TN023: MFC-Standard Ressourcen](../mfc/tn023-standard-mfc-resources.md).

Ressourcen Symbole sind 16-Bit-Zahlen. Sie können Sie als "signiert" oder "unsigniert" eingeben. Sie werden jedoch intern als ganze Zahlen ohne Vorzeichen verwendet, sodass negative Zahlen in den entsprechenden positiven Wert umgewandelt werden.

Einige Einschränkungen von Symbol Werten sind:

- Die Visual Studio-Entwicklungsumgebung und MFC verwenden einige Zahlenbereiche für besondere Zwecke. Alle Zahlen mit dem wichtigsten Bitset (-32.768 bis -1 oder 32.768 bis 65.534 in Abhängigkeit des Zeichens) sind für MFC reserviert.

- Ein Symbolwert kann nicht mit anderen Symbol Zeichenfolgen definiert werden. Beispielsweise wird die folgende Symbol Definition nicht unterstützt:

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- Präprozessormakros können nicht mit Argumenten als Wert Definitionen verwendet werden. Das folgende Beispiel ist kein gültiger Ausdruck, unabhängig davon `ID` , was zum Zeitpunkt der Kompilierung ausgewertet wird:

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

- Ihre Anwendung verfügt möglicherweise über eine vorhandene Datei, die mit Ausdrücken definierte Symbole enthält.

### <a name="to-change-a-symbol-value"></a>So ändern Sie einen Symbolwert

1. Wählen Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)die Ressource aus.

1. Geben Sie im Fenster **Eigenschaften** den Symbolnamen, gefolgt von einem Gleichheitszeichen und einer ganzen Zahl in das Feld **ID** ein, z. b.:

    ```
    IDC_EDITNAME=5100
    ```

   Der neue Wert wird in der Symbolheaderdatei gespeichert, wenn Sie das nächste Mal das Projekt speichern. Nur der Symbol Name bleibt im Feld ID sichtbar, und das Gleichheitszeichen und der Wert werden nach der Validierung nicht angezeigt.

## <a name="change-or-delete-symbols"></a>Symbole ändern oder löschen

Im [Dialogfeld Ressourcen Symbole](./creating-new-symbols.md)können Sie vorhandene Symbole bearbeiten oder löschen, die nicht bereits einer Ressource oder einem Objekt zugewiesen sind.

### <a name="to-change-an-unassigned-symbol"></a>So ändern Sie ein nicht zugewiesenes Symbol

1. Wählen Sie im Feld **Name** das Symbol nicht zugewiesen aus, und wählen Sie dann **ändern**aus.

1. Bearbeiten Sie den Namen oder Wert des Symbols in den Feldern, die im Dialogfeld **Symbol ändern** angezeigt werden.

> [!NOTE]
> Wenn Sie ein Symbol ändern möchten, das einer Ressource oder einem Objekt zugewiesen ist, müssen Sie den Ressourcen-Editor oder das **Eigenschaften** Fenster verwenden.

### <a name="to-delete-an-unassigned-unused-symbol"></a>So löschen Sie ein nicht zugewiesenes (nicht verwendetes) Symbol

Wählen Sie im Dialogfeld **Ressourcen Symbole** das Symbol aus, das Sie löschen möchten, und wählen Sie **Löschen**aus.

> [!NOTE]
> Stellen Sie vor dem Löschen eines nicht verwendeten Symbols in einer Ressourcen Datei sicher, dass es nicht an anderer Stelle im Programm oder in Ressourcen Dateien, die zur Kompilierzeit enthalten sind, verwendet wird.

## <a name="include-symbols"></a>Symbole einschließen

Wenn die Entwicklungsumgebung erstmals eine durch eine andere Anwendung erstellte Ressourcendatei liest, markiert sie alle einbezogenen Headerdateien als schreibgeschützt. Sie können das [Dialogfeld Ressourcenincludes](./how-to-include-resources-at-compile-time.md) verwenden, um zusätzliche schreibgeschützte Symbol Header Dateien hinzuzufügen.

Ein Grund, weshalb Sie möglicherweise schreibgeschützte Symboldefinitionen verwenden möchten, ist der Plan, Symboldateien unter verschiedenen Projekten freizugeben.

Sie können zudem einbezogene Symboldateien verwenden, wenn Sie über vorhandene Ressourcen mit Symboldefinitionen verfügen, die anstelle von einfachen Ganzzahlen Ausdrücke zum Definieren des Symbolwerts verwenden. Beispiel:

```cpp
#define   IDC_CONTROL1 2100
#define   IDC_CONTROL2 (IDC_CONTROL1+1)
```

Die Umgebung interpretiert diese berechneten Symbole ordnungsgemäß, sofern Folgendes gegeben ist:

- Die berechneten Symbole sind in einer schreibgeschützten Symboldatei platziert.

- Ihre Ressourcendatei enthält Ressourcen, zu denen diese berechneten Symbole bereits zugewiesen sind.

- Es wird ein numerischer Ausdruck erwartet.

> [!NOTE]
> Wenn eine Zeichenfolge oder ein numerischer Ausdruck erwartet wird, wird der Ausdruck nicht ausgewertet.

### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>So beziehen Sie freigegebene (schreibgeschützte) Symbole in Ihrer Ressourcendatei ein

1. Klicken Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)mit der rechten Maustaste auf die *RC* -Datei, und wählen Sie [Ressource enthält](./how-to-include-resources-at-compile-time.md).

1. Verwenden Sie im Feld **Direktiven** für schreibgeschützte Symbole die `#include` Compilerdirektive, um die Datei anzugeben, in der die schreibgeschützten Symbole beibehalten werden sollen.

   Die Datei wird nicht aufgerufen `Resource.h` , da dies der Dateiname ist, der normalerweise von der Hauptsymbol Header Datei verwendet wird.

   > [!NOTE]
   > Was Sie in das Feld **Direktiven** für schreibgeschützte Symbole eingeben, ist in der Ressourcen Datei genau wie beim eingeben enthalten. Stellen Sie sicher, dass die Eingabe weder Schreib- noch Syntaxfehler aufweist.

   Verwenden Sie das Feld **Direktiven** für schreibgeschützte Symbole, um nur Dateien mit Symbol Definitionen einzubeziehen. Fügen Sie keine Ressourcen Definitionen ein, sonst werden doppelte Ressourcen Definitionen erstellt, wenn die Datei gespeichert wird.

1. Platzieren Sie die Symbole in der von Ihnen angegebenen Datei.

   Die Symbole in Dateien, die auf diese Weise eingeschlossen werden, werden jedes Mal ausgewertet, wenn Sie die Ressourcen Datei öffnen, aber Sie werden nicht auf dem Datenträger ersetzt, wenn Sie die Datei speichern.

1. Klicken Sie auf **OK**.

### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>So ändern Sie den Namen den Symbolheaderdatei für die Ressource

1. Klicken Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)mit der rechten Maustaste auf die *RC* -Datei, und wählen Sie [Ressource enthält](./how-to-include-resources-at-compile-time.md).

1. Geben Sie im Feld **Symbol Header Datei** den neuen Namen für die Includedatei ein.

## <a name="requirements"></a>Requirements (Anforderungen)

Win32

## <a name="see-also"></a>Weitere Informationen

[Ressourcen Bezeichner (Symbole)](symbols-resource-identifiers.md)<br/>
[Gewusst wie: Erstellen von Symbolen](creating-new-symbols.md)<br/>
[Vordefinierte Symbol-IDs](predefined-symbol-ids.md)<br/>
