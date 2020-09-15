---
title: '/Module: exporteader (Header Einheiten erstellen)'
description: 'Verwenden Sie die/Module: exporteader-Compileroption, um Modul Header Einheiten für die angegebenen Header Namen-oder Includedateien zu erstellen.'
ms.date: 09/13/2020
f1_keywords:
- /module:exportHeader
helpviewer_keywords:
- /module:exportHeader
- Create header units
ms.openlocfilehash: f0c0ce1c593df742af77aa36189df1e89de75b6b
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079140"
---
# <a name="moduleexportheader-create-header-units"></a>`/module:exportHeader` (Header Einheiten erstellen)

Weist den Compiler an, die von den Eingabe Argumenten angegebenen Header Einheiten zu erstellen. Der Compiler generiert eine Ausgabe in "IFC ()"- *`.ifc`* Dateien.

## <a name="syntax"></a>Syntax

> **`/module:exportHeader`** *`header-name`* \[...]\
> **`/module:exportHeader`** *`filename`* \[...]

### <a name="arguments"></a>Argumente

*`header-name`*\
Die zu exportier Header Datei. Das- *`header-name`* Argument muss dieselbe Form wie ein Argument für eine- `#include` Direktive annehmen.

*`filename`*\
Der relative oder absolute Pfad zur Header Datei, aus der eine Header Einheit erstellt werden soll.

## <a name="remarks"></a>Bemerkungen

Die- **`/module:exportHeader`** Compileroption erfordert, dass Sie Unterstützung für experimentelle Module mithilfe der- [`/experimental:module`](experimental-module.md) Compileroption und der Option [/Std: c + + Latest](std-specify-language-standard-version.md) aktivieren. Diese Option ist ab Visual Studio 2019 Version 16,8 verfügbar.

Eine **`/module:exportHeader`** Compileroption kann beliebig viele Header Namen Argumente angeben, die der Build erfordert. Sie müssen diese nicht separat angeben.

Standardmäßig erstellt der Compiler keine Objektdatei, wenn eine Header Einheit kompiliert wird. Geben Sie die-Compileroption an, um eine Objektdatei zu entwickeln **`/Fo`** . Weitere Informationen finden Sie unter [ `/Fo` (Objekt Dateiname)](fo-object-file-name.md).

Der Compiler löst einen *`header-name`* basierend auf der Reihenfolge der Verzeichnis Suchvorgänge, einschließlich der von Ihnen angegebenen, auf. Weitere Informationen finden Sie unter [ `/I` (weitere Includeverzeichnisse)](i-additional-include-directories.md).

Das Argument *`header-name`* muss auf die gleiche Weise wie in der Quelle angegeben werden. Das-Argument ist sensibel für das Zitieren von Regeln und für `<` -und- `>` Operatoren in der Befehlszeile. Der Befehl zum ordnungsgemäßen Escapezeichen zum Erstellen einer Header Einheit, wie z. b. `<vector>` die Verwendung der VS2019-Eingabeaufforderung, sieht

```cmd
cl ... /experimental:module /module:exportHeader "<vector>"
```

Das Entwickeln eines lokalen Projekt Headers wie könnte z. b. `"utils/util.h"` wie folgt aussehen:

```cmd
cl ... /experimental:module /module:exportHeader """util/util.h"""
```

Die Anführungs Regeln in anderen Befehlszeilen Prozessoren unterscheiden sich möglicherweise.

Wenn Sie die *`header-name`* Form von verwenden **`/module:exportHeader`** , ist es möglicherweise hilfreich, die ergänzende Option zu verwenden **`/module:showResolvedHeader`** . Die- **`/module:showResolvedHeader`** Option gibt einen absoluten Pfad zu der Datei aus *`header-name`* , in die das Argument aufgelöst wird.

**`/module:exportHeader`** kann mehrere Eingaben gleichzeitig auch unter verarbeiten **`/MP`** . Wir empfehlen Ihnen **`/module:output <directory>`** die Verwendung von, um für jede Kompilierung eine separate IFC-Datei zu erstellen.

### <a name="examples"></a>Beispiele

Die angegebenen Header `"C:\util\util.h"` und `"C:\app\app.h"` können *`header-name`* mithilfe des folgenden Befehls als Argumente exportiert werden:

```cmd
cl /IC:\ /experimental:module /module:exportHeader """util/util.h""" """app/app.h""" /FoC:\obj
```

Sie können Sie *`filename`* mithilfe des folgenden Befehls als Argumente exportieren:

```cmd
cl /IC:\ /experimental:module /module:exportHeader C:\util\util.h C:\app\app.h /FoC:\obj
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Legen Sie die Dropdown- **Konfiguration** auf **alle Konfigurationen**fest.

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Ändern Sie die Eigenschaft **zusätzliche Optionen** , um die *`/module:exportHeader`* Option und alle Argumente hinzuzufügen. Wählen Sie dann **OK** oder **anwenden** aus, um die Änderungen zu speichern.

## <a name="see-also"></a>Weitere Informationen

[`/experimental:module` (Modulunterstützung aktivieren)](experimental-module.md)\
[`/headerUnit` (Header Einheit "IFC" verwenden)](headerunit.md)\
[`/module:reference` (Benanntes Modul "IFC" verwenden)](module-reference.md)\
[`/translateInclude` (Konvertieren von include-Direktiven in Import Direktiven)](translateinclude.md)
