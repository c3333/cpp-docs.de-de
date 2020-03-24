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
ms.openlocfilehash: fd9f8b444d263818aca1b16260f70730d5350e7c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169109"
---
# <a name="using-c-or-c-symbols-in-__asm-blocks"></a>Verwenden von C- oder C++-Symbolen in __asm-Blöcken

**Microsoft-spezifisch**

Ein `__asm`-Block kann auf jedes C- C++ oder-Symbol im Bereich verweisen, in dem der-Block angezeigt wird. (C- C++ und-Symbole sind Variablennamen, Funktionsnamen und Bezeichnungen, d. h. Namen, die keine symbolischen Konstanten oder `enum` Elemente sind. Member-Funktionen C++ können nicht aufgerufen werden.)

Es gelten einige Einschränkungen für die Verwendung von C und C++ Symbolen:

- Jede Assembly-sprach Anweisung kann nur ein C-oder C++ -Symbol enthalten. Mehrere Symbole können in derselben **Assemblyanweisung**nur mit **Längen**-, Typ-und **Größen** Ausdrücken angezeigt werden.

- Funktionen, auf die in einem `__asm`-Block verwiesen wird, müssen zuvor im Programm als (prototypisiert) deklariert werden. Andernfalls kann der Compiler nicht zwischen Funktionsnamen und Bezeichnungen im `__asm`-Block unterscheiden.

- Ein `__asm`-Block kann keine C- C++ oder-Symbole mit derselben Schreibweise wie in MASM reservierten Wörtern (unabhängig von der Groß-/Kleinschreibung) verwenden. Zu den in MASM reservierten Wörtern zählen Anweisungs Namen wie **Push** -und Registernamen wie z. b. si.

- Struktur-und Union-Tags werden in `__asm` Blöcken nicht erkannt.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Verwenden von C oder C++ in __asm-Blöcken](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
