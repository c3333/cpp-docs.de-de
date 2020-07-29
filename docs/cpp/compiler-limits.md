---
title: Compiler-Grenzen
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: e0e2381d88c727466b06a97c72826d2d5e15a87b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233768"
---
# <a name="compiler-limits"></a>Compiler-Grenzen

Der C++-Standard empfiehlt Grenzen für verschiedene Sprachkonstrukte. Im folgenden finden Sie eine Liste der Fälle, in denen der Microsoft C++-Compiler die empfohlenen Grenzwerte nicht implementiert. Die erste Zahl ist das Limit, das im ISO C++ 11-Standard (INCITS/ISO/IEC 14882-2011 [2012], Anhang B) festgelegt ist, und die zweite Zahl ist das vom Microsoft C++-Compiler implementierte Limit:

- Schachtelungs Ebenen von Verbund Anweisungen, Iterations Steuerungsstrukturen und Auswahl Steuerungsstrukturen C++ Standard: 256, Microsoft C++ Compiler: hängt von der Kombination der geschachtelten-Anweisungen ab, aber in der Regel zwischen 100 und 110.

- Parameter in einer Makro Definition C++ Standard: 256, Microsoft C++ Compiler: 127.

- Argumente in einem Makro Aufruf C++ Standard: 256, Microsoft C++ Compiler 127.

- Zeichen in einem literalzeichenfolgenliteraloder einem Wide String-Literalzeichen (nach der Verkettung)-C++ Standard: 65536, Microsoft C++ Compiler: 65535 Einzel Byte Zeichen, einschließlich des NULL-Terminator und 32767 Doppelbyte Zeichen, einschließlich des NULL-Terminator.

- Ebenen der Klassen-, Struktur-oder Union-Definitionen in einem Single `struct-declaration-list` -C++-Standard: 256, Microsoft C++ Compiler: 16.

- Member-Initialisierer in einer Konstruktordefinition C++ Standard: 6144, Microsoft C++ Compiler: mindestens 6144.

- Bereichs Qualifizierungen eines Bezeichners C++ Standard: 256, Microsoft C++ Compiler: 127.

- **`extern`** Eingefügte Spezifikationen C++ Standard: 1024, Microsoft C++ Compiler: 9 (die implizite **`extern`** Spezifikation wird nicht im globalen Gültigkeitsbereich gezählt, oder 10, wenn Sie die implizite **`extern`** Spezifikation im globalen Gültigkeitsbereich zählen.)

- Vorlagen Argumente in einer Vorlagen Deklaration C++ Standard: 1024, Microsoft C++ Compiler: 2046.

## <a name="see-also"></a>Siehe auch

[Nicht dem Standard entsprechende Verhalten](../cpp/nonstandard-behavior.md)
