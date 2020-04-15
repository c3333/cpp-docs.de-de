---
title: Formatieren von Zeichenfolgen und Ein-/Ausgaben (Modern C++)
description: Optionen für formatierte Zeichenfolgen-E/A, die in modernem C++ verfügbar sind.
ms.date: 05/30/2019
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: a3fc93b0baf414759eb50c787c4057fb85dcb370
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375776"
---
# <a name="string-and-io-formatting-modern-c"></a>Formatieren von Zeichenfolgen und Ein-/Ausgaben (Modern C++)

[ \<C++->-Klassen,](../standard-library/iostream.md) -Funktionen und -Operatoren unterstützen formatierte Zeichenfolgen-E/A. Der folgende Code zeigt beispielsweise, `cout` wie Sie festlegen, dass eine ganze Zahl so formatiert wird, dass sie in hexadezimal ausgegeben wird. Zuerst speichert es den aktuellen Status, um ihn anschließend `cout`zurückzusetzen, da er, sobald der Formatstatus an übergeben wurde, so bleibt, bis er geändert wird. Sie gilt nicht nur für die eine Codezeile.

```cpp
#include <iostream>
#include <iomanip>

using namespace std;

int main()
{
    ios state(nullptr);

    cout << "The answer in decimal is: " << 42 << endl;

    state.copyfmt(cout); // save current formatting
    cout << "In hex: 0x" // now load up a bunch of formatting modifiers
        << hex
        << uppercase
        << setw(8)
        << setfill('0')
        << 42            // the actual value we wanted to print out
        << endl;
    cout.copyfmt(state); // restore previous formatting
}
```

Dieser Ansatz ist typsicher und erweiterbar, aber er ist auch komplex und ausführlich.

## <a name="alternative-format-options"></a>Alternative Formatoptionen

Alternativ können Sie die `Boost.Format` Boost C++-Bibliotheken verwenden, auch wenn es nicht standardmäßig ist. Sie können jede Boost-Bibliothek von der [Boost-Website](https://www.boost.org/) herunterladen.

Einige Vorteile `Boost.Format` von sind:

- Sicher: Typsicher und löst eine Ausnahme für Fehler aus, z. B. die Angabe von zu wenigen oder zu vielen Elementen.

- Erweiterbar: Funktioniert für jeden Typ, der gestreamt werden kann

- Praktisch: Standard POSIX und ähnliche Formatzeichenfolgen.

Obwohl `Boost.Format` c++ [ \<iostream>-Einrichtungen](../standard-library/iostream-programming.md) basiert, die sicher und erweiterbar sind, sind sie nicht leistungsoptimiert. Wenn Sie eine Leistungsoptimierung benötigen, sollten Sie C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) und [sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), die schnell und einfach zu bedienen sind, in Betracht ziehen. Sie sind jedoch nicht erweiterbar oder sicher vor Sicherheitslücken. (Sichere Versionen sind vorhanden, doch verursachen diese geringfügige Leistungseinbußen. Weitere Informationen finden Sie in [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) und [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)).

Im folgenden Code werden einige der Boost-Formatierungsfunktionen verdeutlicht.

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>Siehe auch

[Willkommen zurück bei C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++-Sprachreferenz](../cpp/cpp-language-reference.md)<br/>
[C++-Standardbibliothek](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream>](../standard-library/iostream.md)<br/>
[\<Grenzwerte>](../standard-library/limits.md)<br/>
[\<iomanip>](../standard-library/iomanip.md)
