---
title: '/Module: Reference (benanntes Modul verwenden)'
description: 'Verwenden Sie die/Module: reference-Compileroption, um Modul Header Einheiten für die angegebenen Header Namen-oder Includedateien zu erstellen.'
ms.date: 09/13/2020
f1_keywords:
- /module:reference
helpviewer_keywords:
- /module:reference
- Use named module IFC
ms.openlocfilehash: 5f40f6b700c38f3238cc7a621313621085fbc289
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079142"
---
# <a name="modulereference-use-named-module-ifc"></a>`/module:reference` (Benanntes Modul "IFC" verwenden)

Weist den Compiler an, eine vorhandene "IFC ( *`.ifc`* )" für die aktuelle Kompilierung zu verwenden.

## <a name="syntax"></a>Syntax

> **`/module:reference`** *`module-name=filename`*\
> **`/module:reference`** *`filename`*

### <a name="arguments"></a>Argumente

*`filename`*\
Der Name einer Datei, die die Informationen zu " *IFC Data*" und "vorgefertigte Module" enthält. Um mehr als ein Modul zu importieren, fügen Sie eine separate **`/module:reference`** Option für jede Datei ein.

*`module-name`*\
Ein gültiger Name eines exportierten primären Modulschnittstellen-Einheits namens oder eines vollständigen Modul Partitions namens.

## <a name="remarks"></a>Bemerkungen

Die- **`/module:reference`** Compileroption erfordert, dass Sie Unterstützung für experimentelle Module mithilfe der- [`/experimental:module`](experimental-module.md) Compileroption und der Option [/Std: c + + Latest](std-specify-language-standard-version.md) aktivieren. Diese Option ist ab Visual Studio 2019 Version 16,8 verfügbar.

Wenn das **`/module:reference`** Argument ein *`filename`* ohne ist *`module-name`* , wird die Datei zur Laufzeit geöffnet, um zu überprüfen, ob das *`filename`* Argument einen bestimmten Import Namen hat. Dies kann zu einer langsameren Laufzeitleistung in Szenarios mit vielen **`/module:reference`** Argumenten führen.

Der *`module-name`* muss ein gültiger Name der primären Modulschnittstellen Einheit oder ein vollständiger Modul Partitions Name sein. Beispiele für primäre Modulschnittstellen Namen:

- `M`
- `M.N.O`
- `MyModule`
- `my_module`

Beispiele für vollständige Modul Partitionsnamen:

- `M:P`
- `M.N.O:P.Q`
- `MyModule:Algorithms`
- `my_module:algorithms`

Wenn ein Modul Verweis mit einem erstellt wird *`module-name`* , werden andere Module in der Befehlszeile nicht durchsucht, wenn der Compiler auf einen Import dieses Namens trifft. Angenommen, Sie haben die folgende Befehlszeile:

```cmd
cl ... /experimental:module /module:reference m.ifc /module:reference m=n.ifc
```

Im obigen Fall wird, wenn der Compiler sieht `import m;` , *`m.ifc`* nicht durchsucht.

### <a name="examples"></a>Beispiele

In der folgenden Tabelle sind drei Module angegeben:

| Modul | IFC-Datei |
|--|--|
| *`M`* | *`m.ifc`* |
| *`M:Part1`* | *`m-part1.ifc`* |
| *`Core.Networking`* | *`Networking.ifc`* |

Die Verweis Optionen mit einem- *`filename`* Argument könnten wie folgt aussehen:

```cmd
cl ... /experimental:module /module:reference m.ifc /module:reference m-part.ifc /module:reference Networking.ifc
```

Die Verweis Optionen mit *`module-name=filename`* können wie folgt aussehen:

```cmd
cl ... /experimental:module /module:reference m=m.ifc /module:reference M:Part1=m-part.ifc /module:reference Core.Networking=Networking.ifc
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Legen Sie die Dropdown- **Konfiguration** auf **alle Konfigurationen**fest.

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Ändern Sie die Eigenschaft **zusätzliche Optionen** , um die Option und die zugehörigen Argumente hinzuzufügen *`/module:reference`* . Wählen Sie dann **OK** oder **anwenden** aus, um die Änderungen zu speichern.

## <a name="see-also"></a>Weitere Informationen

[`/experimental:module` (Modulunterstützung aktivieren)](experimental-module.md)\
[`/headerUnit` (Header Einheit "IFC" verwenden)](headerunit.md)\
[`/module:exportHeader` (Header Einheiten erstellen)](module-exportheader.md)\
[`/translateInclude` (Konvertieren von include-Direktiven in Import Direktiven)](translateinclude.md)
