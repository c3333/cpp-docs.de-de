---
title: Compiler-Grenzen
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: 9e61cae1638c87f03b6fa775552408961bde6859
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189576"
---
# <a name="compiler-limits"></a>Compiler-Grenzen

Der C++-Standard empfiehlt Grenzen für verschiedene Sprachkonstrukte. Im folgenden finden Sie eine Liste der Fälle, in C++ denen der Microsoft-Compiler die empfohlenen Grenzwerte nicht implementiert. Die erste Zahl ist das Limit, das im ISO C++ 11-Standard (INCITS/ISO/IEC 14882-2011 [2012], Anhang B) und die zweite Zahl das vom Microsoft C++ -Compiler implementierte Limit ist:

- Schachtelungs Ebenen von Verbund Anweisungen, Iterations Steuerungsstrukturen und Auswahl Steuerungsstrukturen C++ -Standard: 256, C++ Microsoft-Compiler: hängt von der Kombination der geschachtelten-Anweisungen ab, aber in der Regel zwischen 100 und 110.

- Parameter in einer Makro Definition: C++ Standard: 256, Microsoft C++ -Compiler: 127.

- Argumente in einem Makro Aufruf: C++ Standard: 256, Microsoft C++ Compiler 127.

- Zeichen in einem literalzeichenfolgenliteraloder einem Wide String-Literalformat (nach der Verkettung)- C++ Standard: 65536, Microsoft C++ Compiler: 65535 Einzel Byte Zeichen, einschließlich des NULL-Abschluss Zeichens und 32767 Doppelbyte Zeichen, einschließlich des NULL-Terminator.

- Ebenen der Klassen-, Struktur-oder Union-Definitionen in einer einzelnen `struct-declaration-list`- C++ Standard: 256, Microsoft C++ -Compiler: 16.

- Member- C++ Initialisierer in einer Konstruktordefinition: Standard: 6144, C++ Microsoft-Compiler: mindestens 6144.

- Bereichs Qualifizierungen eines Bezeichners C++ : Standard: 256, C++ Microsoft-Compiler: 127.

- In der Tabelle **extern** genannte C++ Spezifikationen: Standard: 1024 C++ , Microsoft-Compiler: 9 (die implizite **externe** Spezifikation wird nicht im globalen Gültigkeitsbereich gezählt), oder 10, wenn Sie die implizite **externe** Spezifikation im globalen Gültigkeitsbereich zählen.

- Vorlagen Argumente in einer Vorlagen Deklaration C++ : Standard: 1024, C++ Microsoft-Compiler: 2046.

## <a name="see-also"></a>Weitere Informationen

[Nicht dem Standard entsprechendes Verhalten](../cpp/nonstandard-behavior.md)
