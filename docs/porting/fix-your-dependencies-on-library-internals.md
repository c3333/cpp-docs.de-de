---
title: Beheben der Abhängigkeiten von C++ Bibliotheks internen Elementen
ms.date: 05/24/2017
helpviewer_keywords:
- library internals in an upgraded Visual Studio C++ project
- _Hash_seq in an upgraded Visual Studio C++ project
ms.assetid: 493e0452-6ecb-4edc-ae20-b6fce2d7d3c5
ms.openlocfilehash: b101234c582d8730b1a8fb62e8182df68554b18c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214993"
---
# <a name="fix-your-dependencies-on-c-library-internals"></a>Beheben der Abhängigkeiten von C++ Bibliotheks internen Elementen

Microsoft hat den Quellcode für die Standardbibliothek, die Mehrheit der C-Laufzeitbibliothek und andere Microsoft-Bibliotheken in vielen Versionen von Visual Studio veröffentlicht. Die Absicht dahinter ist, dass Sie Unterstützung beim Verstehen des Bibliotheksverhaltens und beim Debuggen Ihres Codes erhalten. Ein Nebeneffekt der Veröffentlichung des Bibliotheksquellcodes ist, dass einige interne Werte, Datenstrukturen und Funktionen verfügbar gemacht werden, obwohl sie nicht Teil der Bibliotheksschnittstelle sind. In der Regel haben sie Namen, die mit zwei Unterstrichen oder einem Unterstrich gefolgt von einem Großbuchstaben beginnen; Namen, die der C++-Standard Implementierungen vorbehält. Bei diesen Werten, Strukturen und Funktionen handelt es sich um Implementierungsdetails, die sich ändern können, da sich die Bibliotheken im Laufe der Zeit weiterentwickeln. Daher wird dringend empfohlen, keine Abhängigkeiten von diesen zu erstellen. Wenn Sie dies tun, riskieren Sie nicht portierbaren Code und Probleme beim Versuch, Ihren Code zu neuen Versionen der Bibliotheken zu migrieren.

In den meisten Fällen erwähnen die Dokumente „Neuigkeiten“ oder „Wichtige Änderungen“ jedes Releases von Visual Studio keine Änderungen an bibliotheksinternen Elementen. Schließlich sollten sich diese Implementierungsdetails nicht auf Sie auswirken. Jedoch ist manchmal die Versuchung zu groß, Code zu verwenden, den Sie in der Bibliothek sehen. Dieses Thema behandelt Abhängigkeiten von CRT oder standardbibliotheksinternen Elementen, auf die Sie sich möglicherweise verlassen haben, und beschreibt, wie Sie Ihren Code aktualisieren können, um diese Abhängigkeiten zu entfernen, damit Sie ihn portierbarer machen oder zu neuen Versionen der Bibliothek migrieren können.

## <a name="_hash_seq"></a>_Hash_seq

Die interne Hash-Funktion `std::_Hash_seq(const unsigned char *, size_t)`, die zum Implementieren von `std::hash` auf einigen Zeichenfolgentypen verwendet wird, war in aktuellen Versionen der Standardbibliothek sichtbar. Diese Funktion implementierte einen [FNV-1a-Hash]( https://en.wikipedia.org/wiki/Fowler%E2%80%93Noll%E2%80%93Vo_hash_function) auf einer Zeichenfolge.

Um diese Abhängigkeit zu entfernen, haben Sie eine Reihe von Optionen.

- Wenn Ihre Absicht darin besteht, eine `const char *`-Sequenz mithilfe des gleichen Hashcode-Mechanismus wie `basic_string` in einen ungeordneten Container einzufügen, können Sie dafür die `std::hash`-Vorlagenüberladung verwenden, die `std::string_view` verwendet, wodurch dieser Hashcode auf portierbare Weise zurückgegeben wird. Der Zeichenfolgen-Bibliothekscode beruht möglicherweise auf der Verwendung eines FNV-1a-Hashs in der Zukunft. Dies ist daher die beste Weise, eine Abhängigkeit von einem bestimmten Hashalgorithmus zu vermeiden.

- Wenn Ihre Absicht darin besteht, einen FNV-1a-Hash über beliebigen Speicher zu generieren, finden Sie diesen Code auf GitHub im [VCSamples]( https://github.com/Microsoft/vcsamples)-Repository in einer eigenständigen Headerdatei, [fnv1a.hpp](https://github.com/Microsoft/VCSamples/tree/master/VC2015Samples/_Hash_seq), unter einer [MIT-Lizenz](https://github.com/Microsoft/VCSamples/blob/master/license.txt). Der Einfachheit halber haben wir auch hier eine Kopie eingefügt. Sie können diesen Code in eine Headerdatei kopieren, den Header zu betroffenem Code hinzufügen und dann `_Hash_seq` suchen und durch `fnv1a_hash_bytes` ersetzen. Dies führt zu dem gleichen Verhalten wie bei der internen Implementierung in `_Hash_seq`.

```cpp
/*
VCSamples
Copyright (c) Microsoft Corporation
All rights reserved.
MIT License
Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED *AS IS*, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
*/
#include <stddef.h>

inline size_t fnv1a_hash_bytes(const unsigned char * first, size_t count) {
#if defined(_WIN64)
    static_assert(sizeof(size_t) == 8, "This code is for 64-bit size_t.");
    const size_t fnv_offset_basis = 14695981039346656037ULL;
    const size_t fnv_prime = 1099511628211ULL;
#else /* defined(_WIN64) */
    static_assert(sizeof(size_t) == 4, "This code is for 32-bit size_t.");
    const size_t fnv_offset_basis = 2166136261U;
    const size_t fnv_prime = 16777619U;
#endif /* defined(_WIN64) */

    size_t result = fnv_offset_basis;
    for (size_t next = 0; next < count; ++next)
    {
        // fold in another byte
        result ^= (size_t)first[next];
        result *= fnv_prime;
    }
    return (result);
}
```

## <a name="see-also"></a>Weitere Informationen

[Aktualisieren von Projekten aus früheren Versionen von VisualC++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Überblick über potenzielle Aktualisierungsprobleme (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Aktualisieren Ihres Codes auf die Universal CRT](upgrade-your-code-to-the-universal-crt.md)
