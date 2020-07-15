---
title: /Qpar-report (Auto-Parallelizer-Berichtsebene)
ms.date: 11/04/2016
ms.assetid: 562673b9-02da-4bf8-bb64-70bc25ef4651
ms.openlocfilehash: ea3e430dec61d35b8540792773b5519e64cedaef
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373787"
---
# <a name="qpar-report-auto-parallelizer-reporting-level"></a>/Qpar-report (Auto-Parallelizer-Berichtsebene)

Aktiviert die Berichterstattungs Funktion des [automatischen parallelisierers](../../parallel/auto-parallelization-and-auto-vectorization.md) des Compilers und gibt die Ebene der Informationsmeldungen für die Ausgabe während der Kompilierung an.

## <a name="syntax"></a>Syntax

```
/Qpar-report:{1}{2}
```

## <a name="remarks"></a>Hinweise

**/QPAR-Report: 1**<br/>
Gibt eine Informationsmeldung für Schleifen an, die parallel ausgeführt werden.

**/QPAR-Report: 2**<br/>
Gibt eine Informationsmeldung für Schleifen an, die parallel ausgeführt werden und auch für Schleifen, die nicht, zusammen mit einen Ursachencode parallel ausgeführt werden.

Nachrichten werden an Stdout gesendet. Wenn keine Informationsmeldungen angezeigt werden, enthält der Code keine Schleifen oder die Berichterstellungsebene wurde nicht festgelegt, um Bericht-Schleifen, die nicht parallel ausgeführt werden, zu melden. Weitere Informationen zu Ursachen Codes und Meldungen finden Sie unter [vektorizer-und parallelizer-Meldungen](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

### <a name="to-set-the-qpar-report-compiler-option-in-visual-studio"></a>So legen Sie die /Qpar-report-Compileroption in Visual Studio fest

1. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für das Projekt, und wählen Sie **Eigenschaften**aus.

1. Wählen Sie im Dialogfeld **Eigenschaften Seiten** unter **C/C++** die Option **Befehlszeile**aus.

1. Geben Sie im Feld **zusätzliche Optionen** `/Qpar-report:1` oder ein `/Qpar-report:2` .

### <a name="to-set-the-qpar-report-compiler-option-programmatically"></a>So legen Sie die Compileroption "/Qpar-report" programmgesteuert fest

- Verwenden Sie hierzu das Codebeispiel unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Weitere Informationen

[/Q-Optionen (Vorgänge auf niedriger Ebene)](q-options-low-level-operations.md)<br/>
[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)<br/>
[Vektorisierung in nativem Code in Visual Studio](https://docs.microsoft.com/archive/blogs/nativeconcurrency/auto-vectorizer-in-visual-studio-2012-overview)
