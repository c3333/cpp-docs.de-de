---
title: /await (Coroutineunterstützung aktivieren)
ms.date: 08/15/2017
f1_keywords:
- /await
- -await
helpviewer_keywords:
- /await enable coroutine support [C++]
- -await enable coroutine support [C++]
- await enable coroutine support [C++]
ms.assetid: 302c8e69-09b6-4c58-bcdd-0a6a8713a8df
ms.openlocfilehash: 526216ba2ae259b53bcf77691ebd09a6152b83f0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223927"
---
# <a name="await-enable-coroutine-support"></a>/await (Coroutineunterstützung aktivieren)

Verwenden Sie die **/await** -Compileroption, um Compilerunterstützung für coroutines zu aktivieren.

## <a name="syntax"></a>Syntax

> /await

## <a name="remarks"></a>Bemerkungen

Die **/await** -Compileroption aktiviert die Compilerunterstützung für C++-Coroutinen und die Schlüsselwörter, **`co_await`** **`co_yield`** und **`co_return`** . Diese Option ist standardmäßig deaktiviert. Weitere Informationen zur Unterstützung von Coroutinen in Visual Studio finden Sie im [Visual Studio-Teamblog](https://devblogs.microsoft.com/cppblog/category/coroutine/). Weitere Informationen zum Coroutinen-Standardvorschlag finden Sie unter [N4628 Working Draft, Technical Specification for C++ Extensions for Coroutinen](https://wg21.link/n4628).

Die **/await** -Option ist ab Visual Studio 2015 verfügbar.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaften Seiten** des Projekts.

1. Erweitern Sie unter **Konfigurations Eigenschaften**den Ordner **C/C++** , und wählen Sie die Eigenschaften Seite **Befehlszeile** aus.

1. Geben Sie die **/await** -Compileroption im Feld **zusätzliche Optionen** ein. Wählen Sie **OK** oder **anwenden** aus, um die Änderungen zu speichern.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)
