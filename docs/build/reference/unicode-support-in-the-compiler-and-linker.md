---
title: Unicode-Unterstützung im Compiler und Linker
ms.date: 12/15/2017
f1_keywords:
- VC.Project.VCLinkerTool.UseUnicodeResponseFiles
- VC.Project.VCLibrarianTool.UseUnicodeResponseFiles
- VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles
- VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles
helpviewer_keywords:
- Unicode, Visual C++
ms.openlocfilehash: 420b01263320cf86df3f99da4523cc2b8bb4d4b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168836"
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>Unicode-Unterstützung im Compiler und Linker

Die meisten C++ Visual Build-Tools unterstützen Unicode-Eingaben und-Ausgaben.

## <a name="filenames"></a>Dateinamen

In der Befehlszeile oder in Compilerdirektiven (z. b. `#include`) angegebene Dateinamen können Unicode-Zeichen enthalten.

## <a name="source-code-files"></a>Quellcodedateien

Unicode-Zeichen werden in Bezeichnerzeichen, Makros, Zeichen folgen-und Zeichen Literalen und in Kommentaren unterstützt.  Universelle Zeichennamen werden ebenfalls unterstützt.

Unicode kann in den folgenden Codierungen in eine Quellcodedatei eingegeben werden:

- UTF-16-Little-Endian mit oder ohne Bytereihenfolgemarkierung (BOM)

- UTF-16-Big-Endian mit oder ohne BOM

- UTF-8 with BOM

## <a name="output"></a>Output

Während der Kompilierung gibt der Compiler Diagnoseinformationen an die Konsole in UTF-16 aus.  Welche Zeichen auf Ihrer Konsole angezeigt werden können, ist von den Eigenschaften des Konsolenfensters abhängig.  Die in eine Datei umgeleitete Compilerausgabe entspricht der aktuellen ANSI-Konsolencodepage.

## <a name="linker-response-files-and-def-files"></a>Antwortdateien für den Linker und DEF-Dateien

Antwort Dateien und DEF-Dateien können entweder UTF-16 mit einer BOM oder ANSI sein.

## <a name="asm-and-cod-dumps"></a>ASM- und COD-Dumps

ASM- und COD-Dumps müssen standardmäßig in ANSI sein, damit die Kompatibilität mit MASM gewährleistet ist. Verwenden Sie [/FAU](fa-fa-listing-file.md) , um UTF-8 auszugeben. Beachten Sie Folgendes: Wenn Sie **/FAS**angeben, wird die zusammen geprägte Quelle einfach direkt gedruckt und kann als gegartet angezeigt werden, beispielsweise wenn der Quellcode UTF-8 ist und Sie **/FAsu**nicht angegeben haben.

## <a name="see-also"></a>Weitere Informationen

[Verwenden des MSVC-Toolsets über die Befehlszeile](../building-on-the-command-line.md)
