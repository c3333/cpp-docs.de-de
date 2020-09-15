---
title: '/experimental: Module (Modulunterstützung aktivieren)'
description: 'Verwenden Sie die/Experimental: Module-Compileroption, um experimentelle Compilerunterstützung für Module zu aktivieren.'
ms.date: 09/03/2019
f1_keywords:
- module
- /experimental:module
helpviewer_keywords:
- module
- /experimental:module
- Enable module support
ms.openlocfilehash: 0eea5127f651eaff30c197271ae6da38ac1356be
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075724"
---
# <a name="experimentalmodule-enable-module-support"></a>/experimental: Module (Modulunterstützung aktivieren)

Aktiviert die experimentelle Compilerunterstützung für Module gemäß dem Standard Entwurf c++ 20.

## <a name="syntax"></a>Syntax

> **/experimental: Modul**[ **-** ]

## <a name="remarks"></a>Bemerkungen

Sie können die Unterstützung für experimentelle Module mithilfe der **/experimental: Module** -Compileroption zusammen mit der [/Std: c + + Latest](std-specify-language-standard-version.md) -Option aktivieren. Sie können **/experimental: Module** verwenden, um die Modulunterstützung explizit zu deaktivieren.

Diese Option ist ab Visual Studio 2015 Update 1 verfügbar. Ab Visual Studio 2019 Version 16,2 sind Draft C++ 20 Standard Module im Microsoft C++-Compiler nicht vollständig implementiert. Sie können die Module-Funktion verwenden, um einzelne Partitions Module zu erstellen und die von Microsoft bereitgestellten Standard Bibliotheks Module zu importieren. Ein Modul und der Code, in dem es verwendet wird, müssen mit denselben Compileroptionen kompiliert werden.

Weitere Informationen zu Modulen und deren Verwendung und Erstellung finden Sie unter [Übersicht über Module in C++](../../cpp/modules-cpp.md).

Im folgenden finden Sie ein Beispiel für die Compilerbefehlszeilenoptionen, die zum Erstellen eines Export Moduls aus der Quelldatei *ModuleName. IXX*verwendet werden:

```cmd
cl /EHsc /MD /experimental:module /module:export /module:name ModuleName /module:wrapper C:\Output\path\ModuleName.h /module:output C:\Output\path\ModuleName.ifc -c ModuleName.ixx
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Legen Sie die Dropdown- **Konfiguration** auf **alle Konfigurationen**fest.

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Sprache** aus.

1. Ändern Sie die Eigenschaft **C++-Module aktivieren (experimentell)** , und wählen Sie dann **OK**aus.

## <a name="see-also"></a>Weitere Informationen

[`/headerUnit` (Header Einheit "IFC" verwenden)](headerunit.md)\
[`/module:exportHeader` (Header Einheiten erstellen)](module-exportheader.md)\
[`/module:reference` (Benanntes Modul "IFC" verwenden)](module-reference.md)\
[`/translateInclude` (Konvertieren von include-Direktiven in Import Direktiven)](translateinclude.md)\
[/Zc (Übereinstimmung)](zc-conformance.md)
