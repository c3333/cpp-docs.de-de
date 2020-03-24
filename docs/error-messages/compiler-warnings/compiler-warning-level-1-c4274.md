---
title: Compilerwarnung (Stufe 1) C4274
ms.date: 11/04/2016
f1_keywords:
- C4274
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
ms.openlocfilehash: 5f2350f275f883e7bf18aa1621d08b34132e8dfb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175845"
---
# <a name="compiler-warning-level-1-c4274"></a>Compilerwarnung (Stufe 1) C4274

\#Ident wird ignoriert. Weitere Informationen finden Sie in der Dokumentation zu #Pragma Kommentar (exestr, ' String ')

Die `#ident`-Direktive, die eine benutzerdefinierte Zeichenfolge in das Objekt oder die ausführbare Datei einfügt, ist veraltet. Folglich ignoriert der Compiler die-Direktive.

> [!CAUTION]
>  Warnung C4274 Sie können die Anweisung [#pragma comment (exestr, ' String ')](../../preprocessor/comment-c-cpp.md) verwenden. Dieser Ratgeber ist jedoch veraltet und wird in einer zukünftigen Version des Compilers überarbeitet. Wenn Sie die `#pragma`-Direktive verwenden, ignoriert das Linker-Tool (Link. exe) den von der-Direktive erzeugten Kommentar Daten Satz und gibt Warning [Linkertoolwarnung LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)aus. Anstelle der `#ident`-Direktive empfiehlt es sich, dass Sie in Ihrer Anwendung eine Ressourcen Zeichenfolge für die Dateiversion verwenden.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Entfernen Sie die `#ident "`*Zeichenfolge*`"` Direktive.

## <a name="see-also"></a>Weitere Informationen

[comment (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[Linkertoolwarnung LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[Arbeiten mit Ressourcendateien](../../windows/working-with-resource-files.md)
