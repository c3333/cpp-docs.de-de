---
title: /volatile (Interpretation des volatile-Schlüsselworts)
ms.date: 11/04/2016
f1_keywords:
- /volatile:iso
- /volatile:ms
- /volatile
helpviewer_keywords:
- /volatile compiler option
- /volatile compiler option [C++]
- -volatile compiler option
- volatile compiler option [C++]
- volatile compiler option
- -volatile compiler option [C++]
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
ms.openlocfilehash: 7c2c1cd477b424f56e66bd9246e7bde76ad06120
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223784"
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile (Interpretation des volatile-Schlüsselworts)

Gibt an, wie das [volatile](../../cpp/volatile-cpp.md) -Schlüsselwort interpretiert werden soll.

## <a name="syntax"></a>Syntax

> **/volatile:**{**ISO** | **MS**}

## <a name="arguments"></a>Argumente

**/volatile: ISO**<br/>
Wählt strikte **`volatile`** Semantik gemäß der ISO-Standard-C++-Sprache aus. Semantiken zum Abrufen bzw. Freigeben sind bei flüchtigen Zugriffen nicht garantiert. Wenn der Compiler auf Arm ausgerichtet ist, ist dies die Standardinterpretation von **`volatile`** .

**/volatile: ms**<br/>
Wählt die erweiterte **`volatile`** Semantik von Microsoft aus, die über die ISO-Standard-C++-Sprache hinaus Speicher Bestell Garantien hinzufügt. Semantiken zum Abrufen bzw. Freigeben sind bei flüchtigen Zugriffen garantiert. Allerdings zwingt diese Option den Compiler auch zum Generieren von Hardwarearbeitsspeicherbarrieren, die möglicherweise beträchtlichen Mehraufwand für ARM und andere schwache Speicheranordnungsarchitekturen bedeuten. Wenn der Compiler auf eine Plattform mit Ausnahme von Arm ausgerichtet ist, ist dies die Standardinterpretation von **`volatile`** .

## <a name="remarks"></a>Bemerkungen

Es wird dringend empfohlen, **/volatile: ISO** zusammen mit expliziten Synchronisierungs primitiven und systeminternen Compilerfunktionen zu verwenden, wenn Sie mit Arbeitsspeicher arbeiten, der über mehrere Threads gemeinsam genutzt wird. Weitere Informationen finden Sie unter [volatile](../../cpp/volatile-cpp.md).

Wenn Sie vorhandenen Code portieren oder diese Option in der Mitte eines Projekts ändern, kann es hilfreich sein, die Warnung [C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md) zu aktivieren, um Code Speicherorte zu identifizieren, die von den Unterschieden in der Semantik betroffen sind.

Es gibt keine `#pragma`-Entsprechung, zum Steuern dieser Option.

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>So legen Sie die /volatile-Compileroption in Visual Studio fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** für das Projekt. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Fügen Sie im Feld **zusätzliche Optionen** **/volatile: ISO** oder **/volatile: ms** hinzu, und wählen Sie dann **OK** oder **anwenden** aus, um die Änderungen zu speichern.

## <a name="see-also"></a>Siehe auch

[volatile](../../cpp/volatile-cpp.md)<br/>
[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)
