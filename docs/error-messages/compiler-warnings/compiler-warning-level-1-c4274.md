---
title: Compilerwarnung (Stufe 1) C4274
ms.date: 11/04/2016
f1_keywords:
- C4274
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
ms.openlocfilehash: 5d005fccc5920aea61698a65edf9284d56366a1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377080"
---
# <a name="compiler-warning-level-1-c4274"></a>Compilerwarnung (Stufe 1) C4274

\#ident ignoriert; siehe Dokumentation für #pragma Kommentar(exestr, 'string')

Die `#ident` Direktive, die eine benutzerdefinierte Zeichenfolge in das Objekt oder die ausführbare Datei einfügt, ist veraltet. Folglich ignoriert der Compiler die Direktive.

> [!CAUTION]
> Warnung C4274 rät Ihnen, die [#pragma-Kommentar-Anweisung (exestr, 'string')](../../preprocessor/comment-c-cpp.md) zu verwenden. Dieser Ratschlag ist jedoch veraltet und wird in einer zukünftigen Version des Compilers überarbeitet. Wenn Sie `#pragma` die Direktive verwenden, ignoriert das Linker-Tool (LINK.exe) den von der Direktive erstellten Kommentardatensatz und gibt eine Warnung [an LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)aus. Anstelle der `#ident` Direktive wird empfohlen, eine Dateiversionsressourcenzeichenfolge in Ihrer Anwendung zu verwenden.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Entfernen `#ident "`Sie die *Zeichenfolgendirektive.* `"`

## <a name="see-also"></a>Siehe auch

[comment (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[Linker Tools Warnung LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[Arbeiten mit Ressourcendateien](../../windows/working-with-resource-files.md)
