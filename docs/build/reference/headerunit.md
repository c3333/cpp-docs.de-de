---
title: /headerUnit (Header Einheit "IFC" verwenden)
description: Verwenden Sie die/headerUnit-Compileroption, um eine vorhandene, in der aktuellen Kompilierung zu importierende IFC-Header Einheit anzugeben.
ms.date: 09/13/2020
f1_keywords:
- /headerUnit
helpviewer_keywords:
- /headerUnit
- Use header unit IFC
ms.openlocfilehash: 2734df728b188dcfbbe5f475cfc67715a070975d
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079144"
---
# <a name="headerunit-use-header-unit-ifc"></a>`/headerUnit` (Header Einheit "IFC" verwenden)

Weist den Compiler an, `#include` Direktiven für einen importierbar-Header Namen in eine-Direktive zu übersetzen `import header-name;` , anstatt die Text Aufnahme zu verwenden.

## <a name="syntax"></a>Syntax

> **`/headerUnit`** *`header-filename`*=*`ifc-filename`*

### <a name="arguments"></a>Argumente

*`header-filename`*\
Der Name einer Datei, in die der Compiler eine auflöst `header-name` . Während `import header-name ;` der compilerauflösung `header-name` in eine Datei auf dem Datenträger aufgelöst wird. Verwenden *`header-filename`* Sie, um die Datei anzugeben. Nach dem Abgleich öffnet der Compiler den entsprechenden "IFC" mit dem Namen "" *`ifc-filename`* für Import.

*`ifc-filename`*\
Der Name einer Datei, die die Informationen zu " *IFC Data*" und "vorgefertigte Module" enthält. Um mehr als eine Header Einheit zu importieren, fügen Sie eine separate **`/headerUnit`** Option für jede Datei ein.

## <a name="remarks"></a>Bemerkungen

Die- **`/headerUnit`** Compileroption erfordert, dass Sie Unterstützung für experimentelle Module mithilfe der- [`/experimental:module`](experimental-module.md) Compileroption und der Option [/Std: c + + Latest](std-specify-language-standard-version.md) aktivieren. Diese Option ist ab Visual Studio 2019 Version 16,8 verfügbar.

Der Compiler kann nicht mehreren IFC-Dateien eine einzelne zuordnen *`header-name`* . Die Zuordnung mehrerer *`header-name`* Argumente zu einem einzelnen "IFC" ist zwar möglich, wird jedoch nicht empfohlen. Der Inhalt des IFC wird so importiert, als wäre er nur der von angegebene Header *`header-name`* .

### <a name="examples"></a>Beispiele

Bei einem Projekt, das auf zwei Header Dateien und deren Header Einheiten verweist, die in dieser Tabelle aufgeführt sind:

| Headerdatei | IFC-Datei |
|--|--|
| *`C:\utils\util.h`* | *`C:\util.h.ifc`* |
| *`C:\app\app.h`* | *`C:\app.h.ifc`* |

Die Compileroptionen, mit denen auf die Header Einheiten für diese bestimmten Header Dateien verwiesen werden kann, können wie im folgenden Beispiel aussehen:

```CMD
cl ... /experimental:module /translateInclude /headerUnit C:\utils\util.h=C:\util.h.ifc /headerUnit C:\app\app.h=C:\app.h.ifc
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Legen Sie die Dropdown- **Konfiguration** auf **alle Konfigurationen**fest.

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Ändern Sie die Eigenschaft **zusätzliche Optionen** , um die *`/headerUnit`* Optionen und Argumente hinzuzufügen. Wählen Sie dann **OK** oder **anwenden** aus, um die Änderungen zu speichern.

## <a name="see-also"></a>Weitere Informationen

[`/experimental:module` (Modulunterstützung aktivieren)](experimental-module.md)\
[`/module:exportHeader` (Header Einheiten erstellen)](module-exportheader.md)\
[`/module:reference` (Benanntes Modul "IFC" verwenden)](module-reference.md)\
[`/translateInclude` (Konvertieren von include-Direktiven in Import Direktiven)](translateinclude.md)\
