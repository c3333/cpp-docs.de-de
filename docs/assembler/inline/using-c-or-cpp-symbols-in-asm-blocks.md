---
title: Verwenden von C- oder C++-Symbolen in __asm-Blöcken
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], syntax
- symbols, in __asm blocks
- Visual C, symbols in __asm blocks
- __asm keyword [C++], C/C++ elements in
- Visual C++, in __asm blocks
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
ms.openlocfilehash: ecdd3b6b6916a5c9585678838d8e494a58e0508c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191195"
---
# <a name="using-c-or-c-symbols-in-__asm-blocks"></a>Verwenden von C- oder C++-Symbolen in __asm-Blöcken

**Microsoft-spezifisch**

Ein- **`__asm`** Block kann auf jedes C-oder C++-Symbol im Bereich verweisen, in dem der-Block angezeigt wird. (C-und C++-Symbole sind Variablennamen, Funktionsnamen und Bezeichnungen, d. h. Namen, bei denen es sich nicht um symbolische Konstanten oder Member handelt **`enum`** . C++-Member-Funktionen können nicht aufgerufen werden.)

Es gelten einige Einschränkungen für die Verwendung von C-und C++-Symbolen:

- Jede Assembly-sprach Anweisung kann nur ein C-oder C++-Symbol enthalten. Mehrere Symbole können in derselben **Assemblyanweisung**nur mit **Längen**-, Typ-und **Größen** Ausdrücken angezeigt werden.

- Funktionen, auf die in einem- **`__asm`** Block verwiesen wird, müssen zuvor im Programm als (prototypisiert) deklariert werden. Andernfalls kann der Compiler nicht zwischen Funktionsnamen und Bezeichnungen im-Block unterscheiden **`__asm`** .

- Ein- **`__asm`** Block kann keine C-oder C++-Symbole mit derselben Schreibweise wie in MASM reservierten Wörtern (unabhängig von der Groß-/Kleinschreibung) verwenden. Zu den in MASM reservierten Wörtern zählen Anweisungs Namen wie **Push** -und Registernamen wie z. b. si.

- Struktur-und Union-Tags werden in-Blöcken nicht erkannt **`__asm`** .

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Verwenden von C oder C++ in __asm Blöcken](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
