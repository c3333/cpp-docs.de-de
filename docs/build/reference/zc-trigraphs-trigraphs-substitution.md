---
title: /Zc:trigraphs (Trigraphen-Ersetzung)
ms.date: 03/06/2018
f1_keywords:
- /Zc:trigraphs
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
ms.openlocfilehash: 0e4c98e09551d39e3ff7978767b21f1d2c5bb318
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438652"
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:trigraphs (Trigraphen-Ersetzung)

Wenn **/Zc: tagraphen** angegeben wird, ersetzt der Compiler eine Zeichenfolge mit einem Zeichen, indem ein entsprechendes Interpunktions Zeichen verwendet wird.

## <a name="syntax"></a>Syntax

> **/Zc:** nur wenige Diagramme [ **-** ]

## <a name="remarks"></a>Bemerkungen

Ein " *Digraph* " besteht aus zwei aufeinander folgenden Fragezeichen ("??"), gefolgt von einem eindeutigen dritten Zeichen. Der C-Sprachstandard unterstützt für Quelldateien, die einen Zeichensatz verwenden, der keine praktischen grafischen Darstellungen für einige Interpunktions Zeichen enthält. Wenn z. b. die drei-und Ausgabeoptionen aktiviert sind, ersetzt der Compiler "?? = "mit dem Zeichen" # ". Bis c++ 14 werden die drei-und-drei-und-drei unterstützt. Der c++ 17-Standard entfernt die drei- C++ und ausgabegramme. Im C++ Code ermöglicht die **/Zc: trigraphs** -Compileroption die Ersetzung von trigraphsequenzen durch das entsprechende Interpunktions Zeichen. **/Zc: trigraphs:** deaktiviert die trigraphersetzung.

Die Option **/Zc:** -Option ist standardmäßig deaktiviert, und die Option ist nicht betroffen, wenn die [/permissive-](permissive-standards-conformance.md) -Option angegeben wird.

Eine Liste von C/-C++ drei Diagrammen und ein Beispiel, das die Verwendung von drei Diagrammen veranschaulicht, finden Sie unter " [testgraphs](../../c-language/trigraphs.md)".

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf der Eigenschaftenseite auf **Konfigurationseigenschaften** > **C/C++**  > **Befehlszeile**.

1. Ändern Sie die Eigenschaft **zusätzliche Optionen** so, dass Sie **/Zc:** -unter **-oder/Zc:-drei Diagramme** einschließt, und wählen Sie dann **OK**aus.

## <a name="see-also"></a>Weitere Informationen

[/Zc (Übereinstimmung)](zc-conformance.md)<br/>
[Trigraphen](../../c-language/trigraphs.md)<br/>
