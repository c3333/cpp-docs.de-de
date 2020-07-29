---
title: /GR (Laufzeit-Typeninformation aktivieren)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo
- VC.Project.VCCLCompilerTool.RuntimeTypeInfo
helpviewer_keywords:
- -Gr compiler option [C++]
- Gr compiler option [C++]
- RTTI compiler option
- /Gr compiler option [C++]
- enable run-time type information compiler option [C++]
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
ms.openlocfilehash: 974a2b38c793b21abc9f17f5b7ca5c9f5e3305f5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215230"
---
# <a name="gr-enable-run-time-type-information"></a>/GR (Laufzeit-Typeninformation aktivieren)

Fügt Code hinzu, um Objekttypen zur Laufzeit zu überprüfen.

## <a name="syntax"></a>Syntax

```
/GR[-]
```

## <a name="remarks"></a>Bemerkungen

Wenn **/gr** auf ON festgelegt ist, definiert der Compiler das `_CPPRTTI` Präprozessormakro. Standardmäßig ist **/gr** auf ON eingestellt. **/Gr-** deaktiviert Lauf Zeittyp Informationen.

Verwenden Sie **/gr** , wenn der Compiler einen Objekttyp im Code nicht statisch auflösen kann. Normalerweise benötigen Sie die Option **/gr** , wenn Ihr Code [dynamic_cast Operator](../../cpp/dynamic-cast-operator.md) oder [typeid](../../cpp/typeid-operator.md)verwendet. **/Gr** vergrößert jedoch die Größe der rdata-Abschnitte des Bilds. Wenn Ihr Code nicht oder verwendet **`dynamic_cast`** **`typeid`** , kann **/gr-** ein kleineres Bild liefern.

Weitere Informationen zur Lauf Zeittyp Überprüfung finden Sie unter [Lauf Zeittyp Informationen](../../cpp/run-time-type-information.md) in der *C++-Sprachreferenz*.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **C/C++** .

1. Klicken Sie auf die Eigenschaften Seite **Sprache** .

1. Ändern Sie die Eigenschaft " **Lauf Zeittyp Info aktivieren** ".

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)
