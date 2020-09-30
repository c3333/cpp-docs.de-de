---
title: /sourceDependencies (Abhängigkeiten auf Quellebene melden)
description: Referenzhandbuch zur/sourceDependencies-Compileroption in Microsoft C++.
ms.date: 07/29/2020
f1_keywords:
- /sourceDependencies
helpviewer_keywords:
- /sourceDependencies compiler option
- /sourceDependencies
ms.openlocfilehash: 0c1866812435c777f6f1fd7ed7f9db788a8cf031
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502845"
---
# <a name="sourcedependencies-report-source-level-dependencies"></a>`/sourceDependencies` (Berichts Abhängigkeiten auf Quell Ebene)

Weist den Compiler an, eine JSON-Datei zu generieren, die die während der Kompilierung genutzten Abhängigkeiten auf Quell Ebene detailliert beschreibt.

Die JSON-Datei enthält eine Liste der Quell Abhängigkeiten, die Folgendes umfassen:

- Header Dateien (sowohl transitiv als auch direkt enthaltene Header).
- Der verwendete PCH (wenn **`/Yu`** angegeben ist).
- Importierte Module und importierte Header Einheiten (sowohl transitiv als auch direkt importierte Module/Header Einheiten).

## <a name="syntax"></a>Syntax

> **`/sourceDependencies`***Dateiname*\
> **`/sourceDependencies`***Verzeichnis*

## <a name="arguments"></a>Argumente

*Einfügen*\
Der Compiler schreibt die Ausgabe der Quell Abhängigkeit in den angegebenen Dateinamen, der möglicherweise einen relativen oder absoluten Pfad enthält.

*befinden*\
Wenn das Argument ein Verzeichnis ist, generiert der Compiler Quell Abhängigkeits Dateien im angegebenen Verzeichnis. Der Name der Ausgabedatei basiert auf dem vollständigen Namen der Eingabedatei mit der angefügten *`.json`* Erweiterung. Wenn z. b. die für den Compiler bereitgestellte Datei ist *`main.cpp`* , ist der generierte Ausgabe Dateiname *`main.cpp.json`* .

## <a name="remarks"></a>Bemerkungen

Die- **`/sourceDependencies`** Compileroption ist ab Visual Studio 2019 Version 16,7 verfügbar. Er ist standardmäßig nicht aktiviert.

Wenn Sie die- **`/MP`** Compileroption angeben, empfiehlt es sich, **`/sourceDependencies`** mit einem Verzeichnis Argument zu verwenden. Wenn Sie ein einzelnes filename-Argument angeben, versuchen zwei Instanzen des Compilers möglicherweise, die Ausgabedatei gleichzeitig zu öffnen und einen Fehler zu verursachen. Weitere Informationen zu **`/MP`** finden Sie unter [ `/MP` (erstellen mit mehreren Prozessen)](mp-build-with-multiple-processes.md).

Wenn ein nicht schwerwiegender Compilerfehler auftritt, werden die Abhängigkeitsinformationen weiterhin in die Ausgabedatei geschrieben.

Alle Dateipfade werden in der Ausgabe als absolute Pfade angezeigt.

### <a name="examples"></a>Beispiele

Im folgenden Beispielcode:

```cpp
// main.cpp
#include "header.h"
import m;
import "other.h";

int main() { }
```

Sie können **`/sourceDependencies`** zusammen mit den restlichen Compileroptionen verwenden:

> `cl ... /sourceDependencies output.json ... main.cpp`

dabei `...` steht für Ihre anderen Compileroptionen. Diese Befehlszeile erzeugt eine JSON-Datei *`output.json`* mit Inhalt, die etwa wie folgt aussieht:

```JSON
{
    "Version": "1.0",
    "Data": {
        "Source": "C:\\...\\main.cpp",
        "PCH": "C:\\...\\pch.pch",
        "Includes": [
            "C:\\...\\header.h"
        ],
        "Modules": [
            "C:\\...\\m.ifc",
            "C:\\...\\other.h.ifc"
        ]
    }
}
```

Wir haben verwendet `...` , um die gemeldeten Pfade abzukürzen. der Bericht enthält die absoluten Pfade. Welche Pfade gemeldet werden, hängt davon ab, wo der Compiler die Abhängigkeiten findet. Wenn die Ergebnisse nicht erwartet werden, können Sie die Einstellungen für den Includepfad Ihres Projekts überprüfen.

### <a name="to-set-the-sourcedependencies-compiler-option-in-visual-studio"></a>So legen Sie die/sourceDependencies-Compileroption in Visual Studio fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** für das Projekt. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Fügen Sie im Feld **zusätzliche Optionen** hinzu, *`/sourceDependencies: <filename>`* und wählen Sie dann **OK** oder **anwenden** aus, um die Änderungen zu speichern.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Diese Option hat keine programmgesteuerte Entsprechung.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)<br/>
