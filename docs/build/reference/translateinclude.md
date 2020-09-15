---
title: /translateInclude (Include-Direktiven in Import Direktiven übersetzen)
description: 'Verwenden Sie die/translateInclude-Compileroption, um #include Direktiven für einen importierbaren Header Namen in eine Import Header-Name-Direktive zu übersetzen.'
ms.date: 09/13/2020
f1_keywords:
- /translateInclude
helpviewer_keywords:
- /translateInclude
- Translate include directives into import directives
ms.openlocfilehash: 0050f2cb117e48d69cf97a587ef128b9b45790af
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079139"
---
# <a name="translateinclude-translate-include-directives-into-import-directives"></a>`/translateInclude` (Konvertieren von include-Direktiven in Import Direktiven)

Weist den Compiler an, `#include` Direktiven für einen importierbar-Header Namen in eine-Direktive zu übersetzen `import header-name;` , anstatt die Text Aufnahme zu verwenden.

## <a name="syntax"></a>Syntax

> **`/translateInclude`**

## <a name="remarks"></a>Bemerkungen

Die- **`/translateInclude`** Compileroption erfordert, dass Sie Unterstützung für experimentelle Module mithilfe der- [`/experimental:module`](experimental-module.md) Compileroption und der Option [/Std: c + + Latest](std-specify-language-standard-version.md) aktivieren. Diese Option ist ab Visual Studio 2019 Version 16,8 verfügbar.

Mit der- **`/translateInclude`** Option wird die folgende Transformation durchführt, wobei das Beispiel `<vector>` eine importierbare Header Einheit ist:

```cpp
#include <vector>
```

Der Compiler ersetzt diese Direktive durch:

```cpp
import <vector> ;
```

In MSVC wird eine importierbar-Header Einheit durch einen **`/headerUnit`** Verweis benannt. Weitere Informationen finden Sie unter [ `/headerUnit` (Header Einheit "IFC" verwenden)](headerunit.md).

### <a name="examples"></a>Beispiele

Bei einem Projekt, das auf zwei Header Dateien und deren Header Einheiten verweist, die in dieser Tabelle aufgeführt sind:

| Headerdatei | IFC-Datei |
|--|--|
| *`C:\utils\util.h`* | *`C:\util.h.ifc`* |
| *`C:\app\app.h`* | *`C:\app.h.ifc`* |

Und eine Quell *`.cpp`* Datei mit den Headern,

```cpp
#include "utils/util.h"
#include "app/app.h"

int main() { }
```

Die- **`/translateInclude`** Option ermöglicht es dem Compiler, die Header Einheiten zu importieren, anstatt die Header erneut zu kompilieren. Im folgenden finden Sie eine Beispiel Befehlszeile, die die include-Direktiven für *`util.h`* und *`app.h`* in Importe der Header Einheiten übersetzt:

```CMD
cl /IC:\ /experimental:module /translateInclude /headerUnit C:\utils\util.h=C:\util.h.ifc /headerUnit C:\app\app.h=C:\app.h.ifc
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Legen Sie die Dropdown- **Konfiguration** auf **alle Konfigurationen**fest.

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Ändern Sie die Eigenschaft **zusätzliche Optionen** , um die Option hinzuzufügen *`/translateInclude`* . Wählen Sie dann **OK** oder **anwenden** aus, um die Änderungen zu speichern.

## <a name="see-also"></a>Weitere Informationen

[`/experimental:module` (Modulunterstützung aktivieren)](experimental-module.md)\
[ `/headerUnit` (Header Einheit "IFC" verwenden)](headerunit.md). \
[`/module:exportHeader` (Header Einheiten erstellen)](module-exportheader.md)\
[`/module:reference` (Benanntes Modul "IFC" verwenden)](module-reference.md)
