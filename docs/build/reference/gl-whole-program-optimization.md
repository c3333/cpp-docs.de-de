---
title: /GL (Optimierung des ganzen Programms)
ms.date: 11/04/2016
f1_keywords:
- /gl
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
ms.openlocfilehash: 875865a32dcb80cb8a6d8fa53646260f3d9413a5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439654"
---
# <a name="gl-whole-program-optimization"></a>/GL (Optimierung des ganzen Programms)

Aktiviert die Optimierung des gesamten Programms.

## <a name="syntax"></a>Syntax

```
/GL[-]
```

## <a name="remarks"></a>Bemerkungen

Die Optimierung des gesamten Programms ermöglicht es dem Compiler, Optimierungen mit Informationen zu allen Modulen im Programm auszuführen. Ohne die Optimierung des gesamten Programms werden Optimierungen pro Modul (Kompilierungen) durchgeführt.

Die Optimierung des gesamten Programms ist standardmäßig deaktiviert und muss explizit aktiviert werden. Es ist jedoch auch möglich, ihn mit **/GL-** explizit zu deaktivieren.

Mit Informationen zu allen Modulen kann der Compiler folgende Aktionen ausführen:

- Optimieren Sie die Verwendung von Registern über Funktionsgrenzen hinweg.

- Erzielen Sie eine bessere Aufgabe beim Nachverfolgen von Änderungen an globalen Daten, wodurch die Anzahl der Lade-und Speichervorgänge reduziert wird.

- Führen Sie eine bessere Aufgabe der Nachverfolgung der möglichen Elemente aus, die durch eine Zeiger Dereferenzierung geändert werden, und reduzieren Sie die Anzahl der Lade-und Speichervorgänge.

- Inline eine Funktion in einem Modul, auch wenn die Funktion in einem anderen Modul definiert ist.

. obj-Dateien, die mit **/GL** erstellt werden, sind für diese Linker-Hilfsprogramme nicht als [EDITBIN](editbin-reference.md) und [DUMPBIN](dumpbin-reference.md)verfügbar.

Wenn Sie das Programm mit **/GL** und [/c](c-compile-without-linking.md)kompilieren, sollten Sie die Option/LTCG Linker verwenden, um die Ausgabedatei zu erstellen.

[/Zi](z7-zi-zi-debug-information-format.md) kann nicht mit **/GL** verwendet werden.

Das Format von Dateien, die in der aktuellen Version mit **/GL** erstellt werden, ist möglicherweise nicht in C++nachfolgenden Versionen von Visual lesbar. Sie sollten eine LIB-Datei, die aus OBJ-Dateien besteht, die mit **/GL** erstellt wurden, nicht liefern, es sei denn, Sie sind bereit, Kopien der lib- C++ Datei für alle Versionen von Visual zu senden, die von den Benutzern in Zukunft erwartet werden.

. obj-Dateien, die mit **/GL** -und vorkompilierten Header Dateien erstellt werden, sollten nicht zum Erstellen einer LIB-Datei verwendet werden, es sei denn, die LIB-Datei wird auf demselben Computer verknüpft, der die **/GL** . obj-Datei erstellt hat. Informationen aus der vorkompilierten Header Datei der obj-Datei werden zur Verknüpfungs Zeit benötigt.

Weitere Informationen zu den in verfügbaren Optimierungen und den Einschränkungen der Optimierung des gesamten Programms finden Sie unter [/LTCG](ltcg-link-time-code-generation.md).  **/GL** macht außerdem eine Profil gesteuerte Optimierung verfügbar. Siehe/LTCG.  Wenn Sie für Profil gesteuerte Optimierungen kompilieren und die Funktions Reihenfolge ihrer Profil gesteuerten Optimierungen wünschen, müssen Sie mit [/Gy](gy-enable-function-level-linking.md) oder einer Compileroption kompilieren, die/Gy. impliziert.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Weitere Informationen zum Angeben von **/GL** in der Entwicklungsumgebung finden Sie unter [/LTCG (Link-Time Code Generation)](ltcg-link-time-code-generation.md) .

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

1. Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)
