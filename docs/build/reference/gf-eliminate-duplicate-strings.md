---
title: /GF (Doppelte Zeichenfolgen beseitigen)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.StringPooling
- VC.Project.VCCLWCECompilerTool.StringPooling
- /gf
helpviewer_keywords:
- duplicate strings
- Eliminate Duplicate Strings compiler option [C++]
- pooling strings compiler option [C++]
- -GF compiler option [C++]
- /GF compiler option [C++]
- GF compiler option [C++]
- strings [C++], pooling
ms.assetid: bb7b5d1c-8e1f-453b-9298-8fcebf37d16c
ms.openlocfilehash: e0d23004c7b710f51065db52410fbb15b7cca040
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320496"
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF (Doppelte Zeichenfolgen beseitigen)

Ermöglicht es dem Compiler, während der Ausführung eine einzelne Kopie identischer Zeichenfolgen im Programmabbild und im Arbeitsspeicher zu erstellen. Dies ist eine Optimierung namens *String-Pooling,* die kleinere Programme erstellen kann.

## <a name="syntax"></a>Syntax

```
/GF
```

## <a name="remarks"></a>Bemerkungen

Wenn Sie **/GF**verwenden, tauscht das Betriebssystem den Zeichenfolgenteil des Arbeitsspeichers nicht aus und kann die Zeichenfolgen aus der Bilddatei zurücklesen.

**/GF** bündelt Zeichenfolgen als schreibgeschützt. Wenn Sie versuchen, Zeichenfolgen unter **/GF**zu ändern, tritt ein Anwendungsfehler auf.

Durch das Stringpooling können mehrere Zeiger auf mehrere Puffer als mehrere Zeiger auf einen einzelnen Puffer verwendet werden. Im folgenden Code `s` `t` und werden mit derselben Zeichenfolge initialisiert. Durch das Stringpooling werden sie auf denselben Speicher verweisen:

```
char *s = "This is a character buffer";
char *t = "This is a character buffer";
```

> [!NOTE]
> Die Option [/ZI,](z7-zi-zi-debug-information-format.md) die für Bearbeiten und Fortfahren verwendet wird, legt automatisch die Option **/GF** fest.

> [!NOTE]
> Die Compileroption **/GF** erstellt einen adressierbaren Abschnitt für jede eindeutige Zeichenfolge. Und standardmäßig kann eine Objektdatei bis zu 65.536 adressierbare Abschnitte enthalten. Wenn Ihr Programm mehr als 65.536 Zeichenfolgen enthält, verwenden Sie die Compileroption [/bigobj,](bigobj-increase-number-of-sections-in-dot-obj-file.md) um weitere Abschnitte zu erstellen.

**/GF** ist wirksam, wenn [/O1](o1-o2-minimize-size-maximize-speed.md) oder [/O2](o1-o2-minimize-size-maximize-speed.md) verwendet wird.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **C/C++** .

1. Klicken Sie auf die Eigenschaftenseite **Codegenerierung.**

1. Ändern Sie die **Eigenschaft String Pooling aktivieren.**

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>.

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)
