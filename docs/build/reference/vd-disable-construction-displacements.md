---
title: /vd (Konstruktionsverschiebungen deaktivieren)
ms.date: 11/04/2016
f1_keywords:
- /vd
helpviewer_keywords:
- -vd0 compiler option [C++]
- vd1 compiler option [C++]
- /vdn (Disable Construction Displacement) compiler option
- constructor displacements
- vtordisp fields
- /vd0 compiler option [C++]
- -vd1 compiler option [C++]
- /vd1 compiler option [C++]
- displacements compiler option
- vd0 compiler option [C++]
- Disable Construction Displacements compiler option
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
ms.openlocfilehash: df8891cc71dd5a4cfd417969578c0c1b46ae3be3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223810"
---
# <a name="vd-disable-construction-displacements"></a>/vd (Konstruktionsverschiebungen deaktivieren)

## <a name="syntax"></a>Syntax

```
/vdn
```

## <a name="arguments"></a>Argumente

**0**<br/>
Unterdrückt den vtordisp-Konstruktor/destrukturverschiebungs-Member. Wählen Sie diese Option nur aus, wenn Sie sicher sind, dass alle Klassenkonstruktoren und debugtoren virtuelle Funktionen virtuell aufruft.

**1**<br/>
Ermöglicht die Erstellung von ausgeblendeten Vtordisp-Konstruktoren/destrukturverschiebungs Elementen. Diese Auswahl ist die Standardeinstellung.

**2**<br/>
Ermöglicht es Ihnen, [dynamic_cast Operator](../../cpp/dynamic-cast-operator.md) für ein Objekt zu verwenden, das erstellt wird. Beispielsweise ein dynamic_cast von einer virtuellen Basisklasse zu einer abgeleiteten Klasse.

**"/vd2"** fügt ein vtordisp-Feld hinzu, wenn Sie über eine virtuelle Basis mit virtuellen Funktionen verfügen. **/VD1-** sollte ausreichend sein. Der häufigste Fall, bei dem **"/vd2"** erforderlich ist, ist, wenn die einzige virtuelle Funktion in der virtuellen Basis ein Dekonstruktor ist.

## <a name="remarks"></a>Bemerkungen

Diese Optionen gelten nur für C++-Code, der virtuelle Basen verwendet.

Visual C++ implementiert die C++-Erstellungs Unterstützung in Situationen, in denen die virtuelle Vererbung verwendet wird. Konstruktions Verschiebungen lösen das Problem, das erstellt wird, wenn eine virtuelle Funktion, die in einer virtuellen Basis deklariert und in einer abgeleiteten Klasse überschrieben wurde, von einem Konstruktor aufgerufen wird, wenn eine weitere abgeleitete Klasse erstellt wird.

Das Problem besteht darin, dass an die virtuelle Funktion aufgrund **`this`** von Abweichungen zwischen den Verschiebungen der virtuellen Basen einer Klasse und den Verschiebungen zu den abgeleiteten Klassen möglicherweise ein falscher Zeiger weitergeleitet wird. Die Lösung bietet für jede virtuelle Basis einer Klasse eine einzelne bauverschiebungs Anpassung, die als vtordisp-Feld bezeichnet wird.

Standardmäßig werden vtordisp-Felder immer dann eingeführt, wenn der Code benutzerdefinierte Konstruktoren und decoditoren definiert und auch virtuelle Funktionen virtueller Basen überschreibt.

Diese Optionen wirken sich auf die gesamten Quelldateien aus. Verwenden Sie [vtordisp](../../preprocessor/vtordisp.md) , um vtordisp-Felder auf Klassenbasis zu unterdrücken und erneut zu aktivieren.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **C/C++** .

1. Klicken Sie auf die Eigenschaftenseite **Befehlszeile** .

1. Geben Sie die Compileroption im Feld **Zusätzliche Optionen** ein.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)
