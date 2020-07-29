---
title: /Zc:trigraphs (Trigraphen-Ersetzung)
description: Eine Microsoft C++-Compileroption, die die Konformität für die Unterstützung von drei Diagrammen steuert.
ms.date: 07/25/2020
f1_keywords:
- /Zc:trigraphs
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
ms.openlocfilehash: e24f3d2f0064c3acc04b4c3774f47f6e442d5ddd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211852"
---
# <a name="zctrigraphs-trigraphs-substitution"></a>`/Zc:trigraphs`(Trigraphen-Ersetzung)

Wenn **`/Zc:trigraphs`** angegeben wird, ersetzt der Compiler mithilfe eines entsprechenden Interpunktions Zeichens eine Escapezeichenfolge.

## <a name="syntax"></a>Syntax

> **`/Zc:trigraphs`**[**`-`**]

## <a name="remarks"></a>Bemerkungen

Ein " *tagraph* " besteht aus zwei aufeinander folgenden Fragezeichen ( **`??`** ), gefolgt von einem eindeutigen dritten Zeichen. Der C-Sprachstandard unterstützt für Quelldateien, die einen Zeichensatz verwenden, der keine praktischen grafischen Darstellungen für einige Interpunktions Zeichen enthält. Wenn z. b. die drei-und Ausgabeoptionen aktiviert sind, ersetzt der Compiler das- **`??=`** Zeichen mit dem- **`#`** Zeichen. Bis c++ 14 werden die drei-und-drei-und-drei unterstützt. Der Standard C++ 17 entfernt die drei-und ausgabegramme aus der Sprache C++. In C++-Code ermöglicht die- **`/Zc:trigraphs`** Compileroption die Ersetzung von trigraphsequenzen durch das entsprechende Interpunktions Zeichen. **`/Zc:trigraphs-`** deaktiviert die trigraphersetzung.

Die **`/Zc:trigraphs`** Option ist standardmäßig deaktiviert, und die Option ist nicht betroffen, wenn die [`/permissive-`](permissive-standards-conformance.md) Option angegeben wird.

Eine Liste der C/C++-testgraphen und ein Beispiel, das die Verwendung von drei Diagrammen veranschaulicht, finden Sie unter " [drei](../../c-language/trigraphs.md)Diagramme".

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Ändern Sie die Eigenschaft **zusätzliche Optionen** so, dass oder einschließt, **`/Zc:trigraphs`** **`/Zc:trigraphs-`** und wählen Sie dann **OK**aus.

## <a name="see-also"></a>Weitere Informationen

[`/Zc`Konformitäts](zc-conformance.md)<br/>
[Trigraphen](../../c-language/trigraphs.md)
