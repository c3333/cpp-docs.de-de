---
title: /EXPORT (Funktion exportieren)
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLinkerTool.ExportFunctions
- /export
helpviewer_keywords:
- /EXPORT linker option
- EXPORT linker option
- -EXPORT linker option
ms.assetid: 0920fb44-a472-4091-a8e6-73051f494ca0
ms.openlocfilehash: a55b2a4ce72de644fe426894ab389f62bd29b204
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232689"
---
# <a name="export-exports-a-function"></a>/EXPORT (Funktion exportieren)

Exportiert eine Funktion anhand des Namens oder der Ordnungszahl bzw. der Daten aus dem Programm.

## <a name="syntax"></a>Syntax

> **/Export:**<em>entryname</em>[**, \@ **<em>Ordnungszahl</em>[**, NONAME**]] [**, Data**]

## <a name="remarks"></a>Bemerkungen

Die Option **/Export** gibt eine Funktion oder ein Datenelement an, das aus dem Programm exportiert werden soll, damit andere Programme die Funktion oder die Daten verwenden können. Exporte werden in der Regel in einer DLL definiert.

*Entryname* ist der Name der Funktion oder des Datenelements, wie er vom aufrufenden Programm verwendet werden soll. *Ordnungszahl* gibt einen Index in der Tabelle "Exports" im Bereich von 1 bis 65.535 an. Wenn Sie keine *Ordinalzahl*angeben, wird eine Verknüpfung zugewiesen. Das **Noname** -Schlüsselwort exportiert die Funktion nur als Ordinalzahl ohne *entryname*.

Das **Data** -Schlüsselwort gibt an, dass das exportierte Element ein Datenelement ist. Das Datenelement im Client Programm muss mit **Extern __declspec (dllimport)** deklariert werden.

Es gibt vier Methoden zum Exportieren einer Definition, die in der empfohlenen Reihenfolge der Verwendung aufgeführt ist:

1. [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) im Quellcode

1. Eine [Exports](exports.md) -Anweisung in einer DEF-Datei

1. Eine /EXPORT-Spezifikation in einem LINK-Befehl

1. Eine [comment](../../preprocessor/comment-c-cpp.md) -Anweisung im Quellcode der Form `#pragma comment(linker, "/export: definition ")` .

Alle diese Methoden können im selben Programm verwendet werden. Wenn Link ein Programm erstellt, das Exporte enthält, wird auch eine Import Bibliothek erstellt, es sei denn, im Build wird eine EXP-Datei verwendet.

Link verwendet ergänzte Formen von bezeichlern. Der Compiler schmückt einen Bezeichner, wenn er die OBJ-Datei erstellt. Wenn *entryname* für den Linker in seiner nicht ergänzten Form angegeben wird (wie er im Quellcode angezeigt wird), versucht Link, den Namen zu erfüllen. Wenn eine eindeutige Entsprechung nicht gefunden werden kann, gibt Link eine Fehlermeldung aus. Verwenden Sie das [DUMPBIN](dumpbin-reference.md) -Tool, um die ergänzte [namens](decorated-names.md) Form eines Bezeichners zu erhalten, wenn Sie ihn für den Linker angeben müssen.

> [!NOTE]
> Geben Sie nicht die ergänzte Form von C-bezeichlen an, die als deklariert wurden **`__cdecl`** **`__stdcall`** .

Wenn Sie einen nicht ergänzten Funktionsnamen exportieren müssen und abhängig von der Buildkonfiguration unterschiedliche Exporte aufweisen (z. b. in 32-Bit-oder 64-Bit-Builds), können Sie verschiedene DEF-Dateien für jede Konfiguration verwenden. (Bedingte Präprozessordirektiven sind in DEF-Dateien nicht zulässig.) Als Alternative können Sie eine- `#pragma comment` Direktive vor einer Funktionsdeklaration verwenden, wie hier gezeigt, wobei `PlainFuncName` der nicht ergänzte Name und `_PlainFuncName@4` der ergänzte Name der Funktion ist:

```cpp
#pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
BOOL CALLBACK PlainFuncName( Things * lpParams)
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften**Seite für die  >  **Linker**  >  **Linkerbefehlszeile** der Configuration Properties

1. Geben Sie die Option im Feld **zusätzliche Optionen** ein.

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Siehe auch

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)
