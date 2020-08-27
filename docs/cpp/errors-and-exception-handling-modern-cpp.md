---
title: Modern C++ bewährte Methoden für Ausnahmen und Fehlerbehandlung
description: Die Art und Weise, wie modern C++ außergewöhnliche Programmierungs Stile über Fehlercodes
ms.date: 08/24/2020
ms.topic: conceptual
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
ms.openlocfilehash: b402c93ea5af3cc7dab418b6dea58446ae300c67
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898365"
---
# <a name="modern-c-best-practices-for-exceptions-and-error-handling"></a>Modern C++ bewährte Methoden für Ausnahmen und Fehlerbehandlung

In modernem C++ ist in den meisten Szenarien die Verwendung von Ausnahmen die bevorzugte Methode zum Mitteilen und Behandeln von logischen Fehlern und Laufzeitfehler. Dies trifft vor allem dann zu, wenn der Stapel mehrere Funktionsaufrufe zwischen der Funktion enthält, die den Fehler erkennt, und der Funktion mit dem Kontext, der den Fehler behandelt. Ausnahmen stellen eine formale, gut definierte Methode für den Code bereit, der Fehler erkennt, um die Informationen an die Aufrufliste (call stack) zu übergeben.

## <a name="use-exceptions-for-exceptional-code"></a>Ausnahmen für Ausnahme Code verwenden

Programmfehler werden häufig in zwei Kategorien unterteilt: logische Fehler, die durch Programmierfehler verursacht werden, z. b. der Fehler "Index außerhalb des gültigen Bereichs". Und Laufzeitfehler, die über die Kontrolle des Programmierers hinausgehen, z. b. der Fehler "Netzwerkdienst nicht verfügbar". In der C-Programmierung sowie in COM erfolgt die Benachrichtigung über Fehler entweder durch Rückgabe eines Werts, der einen Fehlercode oder einen Statuscode für eine bestimmte Funktion darstellt, oder durch Festlegung einer globalen Variablen, die der Aufrufer nach jedem Funktionsaufruf abrufen kann, um festzustellen, ob Fehler gemeldet wurden. Beispielsweise verwendet die COM-Programmierung den HRESULT-Rückgabewert, um Fehler an den Aufrufer zu übermitteln. Und die Win32-API verfügt über die- `GetLastError` Funktion, um den letzten Fehler abzurufen, der von der-aufrufsstapel gemeldet wurde. In beiden Fällen liegt es beim Aufrufer, den Code zu erkennen und darauf entsprechend zu reagieren. Wenn der Aufrufer den Fehlercode nicht explizit behandelt, stürzt das Programm möglicherweise ohne Warnung ab. Möglicherweise wird Sie weiterhin mit ungültigen Daten ausgeführt, und es werden falsche Ergebnisse erzeugt.

Ausnahmen werden in modernem C++ aus folgenden Gründen verwendet:

- Eine Ausnahme erzwingt, dass der aufrufende Code eine Fehlerbedingung erkennt und behandelt. Nicht behandelte Ausnahmen beenden die Programmausführung.

- Einer Ausnahme springt zu der Position in der Aufrufliste, an welcher der Fehler behandelt werden kann. Zwischenfunktionen können die Ausnahme weitergeben. Sie müssen sich nicht mit anderen Ebenen koordinieren.

- Der Ausnahme Stapel-Entwicklungsmechanismus zerstört alle Objekte im Gültigkeitsbereich nach dem Auslösen einer Ausnahme gemäß den klar definierten Regeln.

- Eine Ausnahme ermöglicht die saubere Trennung zwischen dem Code, der den Fehler erkennt, und dem Code, der den Fehler behandelt.

Das folgende vereinfachende Beispiel zeigt die notwendige Syntax zum Auslösen und Abfangen von Ausnahmen in C++.

```cpp
#include <stdexcept>
#include <limits>
#include <iostream>

using namespace std;

void MyFunc(int c)
{
    if (c > numeric_limits< char> ::max())
        throw invalid_argument("MyFunc argument too large.");
    //...
}

int main()
{
    try
    {
        MyFunc(256); //cause an exception to throw
    }

    catch (invalid_argument& e)
    {
        cerr << e.what() << endl;
        return -1;
    }
    //...
    return 0;
}
```

Ausnahmen in C++ ähneln denen in Sprachen wie c# und Java. **`try`** Wenn eine Ausnahme im-Block *ausgelöst wird* , wird Sie vom *caught* ersten zugeordneten-Block abgefangen, **`catch`** dessen Typ mit dem der Ausnahme übereinstimmt. Das heißt, die Ausführung springt von der- **`throw`** Anweisung in die- **`catch`** Anweisung. Ist kein verwendbarer catch-Block vorhanden, wird `std::terminate` aufgerufen und das Programm beendet. In C++ kann jeder Typ ausgelöst werden. Es wird jedoch empfohlen, einen Typ auslösen, der direkt oder indirekt von `std::exception` abgeleitet ist. Im vorherigen Beispiel wird der Ausnahmetyp, [`invalid_argument`](../standard-library/invalid-argument-class.md) , in der-Standardbibliothek in der [`<stdexcept>`](../standard-library/stdexcept.md) Header Datei definiert. C++ stellt keinen Block bereit oder erfordert einen- **`finally`** Block, um sicherzustellen, dass alle Ressourcen freigegeben werden, wenn eine Ausnahme ausgelöst wird. Die RAII-Technik (Resource Acquisition Is Initialization, Ressourcenbelegung ist Initialisierung), die intelligente Zeiger verwendet, bietet die erforderliche Funktionalität zur Ressourcenbereinigung. Weitere Informationen finden Sie unter Gewusst [wie: Entwerfen für die Ausnahme Sicherheit](how-to-design-for-exception-safety.md). Weitere Informationen zum C++ Stack-Entwicklungsmechanismus finden Sie unter [Ausnahmen und Stapel Auflösung](exceptions-and-stack-unwinding-in-cpp.md).

## <a name="basic-guidelines"></a>Grundlegende Richtlinien

Stabile Fehlerbehandlung ist in jeder Programmiersprache schwierig. Obwohl Ausnahmen etliche Funktionen bereitstellen, die gute Fehlerbehandlung unterstützen, können sie Ihnen nicht die gesamte Arbeit abnehmen. Um die Vorteile des Ausnahmemechanismus auszuschöpfen, sollten Sie Ausnahmen bei der Entwicklung Ihres Codes einplanen.

- Verwenden Sie Assertionen, um Fehler zu verhindern, die nie auftreten sollten. Verwenden Sie Ausnahmen, um Fehler abzufangen, die beispielsweise bei der Eingabevalidierung oder in Parametern von öffentlichen Funktionen auftreten können. Weitere Informationen finden Sie im Abschnitt [Ausnahmen](#exceptions_versus_assertions) und Assertionen.

- Verwenden Sie Ausnahmen, wenn der Code, der den Fehler behandelt, von dem Code getrennt ist, der den Fehler von einem oder mehreren dazwischen liegenden Funktionsaufrufen erkennt. Legen Sie fest, ob Fehlercodes anstelle von Leistungs kritischen Schleifen verwendet werden sollen, wenn Code, der den Fehler behandelt, eng mit dem Code verknüpft ist, der ihn erkennt.

- Für jede Funktion, die eine Ausnahme auslösen oder verteilen kann, sollten Sie eine der drei Ausnahmegarantien bereitstellen: die starke Garantie, die grundlegende Garantie oder die Nothrow (Noexcept)-Garantie. Weitere Informationen finden Sie unter Gewusst [wie: Entwerfen für die Ausnahme Sicherheit](how-to-design-for-exception-safety.md).

- Lösen Sie Ausnahmen per Wert aus, fangen Sie Ausnahmen per Referenz ab. Fangen Sie nicht ab, was Sie nicht behandeln können.

- Verwenden Sie keine Ausnahmespezifikationen; sie sind seit C++11 veraltet. Weitere Informationen finden Sie unter [Ausnahme Spezifikationen und- `noexcept` ](#exception_specifications_and_noexcept) Abschnitt.

- Verwenden Sie wenn möglich Ausnahmetypen der Standardbibliothek. Leiten Sie benutzerdefinierte Ausnahme Typen aus der [ `exception` Klassen](../standard-library/exception-class.md) Hierarchie ab.

- Lassen Sie Ausnahmen nicht von Destruktoren oder Funktionen zur Speicherfreigabe auslösen.

## <a name="exceptions-and-performance"></a>Ausnahmen und Leistungsfähigkeit

Der Ausnahme Mechanismus wirkt sich nur minimal auf die Leistung aus, wenn keine Ausnahme ausgelöst wird. Wenn eine Ausnahme ausgelöst wird, sind die Kosten für Stapeldurchlauf und -Entladung ungefähr mit den Kosten eines Funktionsaufrufs vergleichbar. Zusätzliche Datenstrukturen sind erforderlich, um die-Rückruf Liste nach dem Eintreten eines-Blocks zu verfolgen **`try`** , und zusätzliche Anweisungen sind erforderlich, um den Stapel zu entladen, wenn eine Ausnahme ausgelöst wird. In den meisten Szenarien sind die Kosten für Leistung und Speicherbedarf jedoch nicht signifikant. Die negative Auswirkung von Ausnahmen auf die Leistung ist wahrscheinlich nur für Speicher eingeschränkte Systeme von Bedeutung. Oder in Leistungs kritischen Schleifen, bei denen ein Fehler wahrscheinlich regelmäßig auftritt und eine enge Kopplung zwischen dem Code und dem Code vorliegt, der ihn meldet. In jedem Fall ist es unmöglich, die Effektivkosten von Ausnahmen ohne Codeprofilierung und Messungen zu ermitteln. Auch in den seltenen Fällen, in denen die Kosten signifikant sind, sollten Sie abwägen, ob diese Kosten nicht die Vorteile rechtfertigen (wie korrekter Code, leichtere Verwaltbarkeit und andere), die von einer gut entworfenen Ausnahmerichtlinie sichergestellt werden.

## <a name="exceptions-versus-assertions"></a><a name="exceptions_versus_assertions"></a> Ausnahmen und Assertionen

Ausnahmen und Assertionen sind zwei verschiedene Mechanismen zum Erkennen von Laufzeitfehlern in einem Programm. Verwenden `assert` Sie-Anweisungen, um während der Entwicklung auf Bedingungen zu testen, die nie true sein sollten, wenn der gesamte Code korrekt ist. Es gibt keinen Punkt bei der Behandlung eines solchen Fehlers mithilfe einer Ausnahme, da der Fehler darauf hinweist, dass etwas im Code korrigiert werden muss. Sie stellt keine Bedingung dar, die das Programm zur Laufzeit wiederherstellen muss. Eine beendet die `assert` Ausführung bei der-Anweisung, sodass Sie den Programmzustand im Debugger überprüfen können. Eine Ausnahme setzt die Ausführung des ersten passenden catch-Handlers fort. Verwenden Sie Ausnahmen, um Fehlerbedingungen zu überprüfen, die zur Laufzeit auftreten können (beispielsweise "Datei nicht gefunden" oder "Nicht genügend Arbeitsspeicher"), auch wenn der Code korrekt ist. Ausnahmen können diese Bedingungen behandeln, auch wenn die Wiederherstellung nur eine Nachricht an ein Protokoll ausgibt und das Programm beendet. Überprüfen Sie immer Argumente für öffentliche Funktionen mithilfe von Ausnahmen. Auch wenn die Funktion fehlerfrei ist, haben Sie möglicherweise keine vollständige Kontrolle über die Argumente, die ein Benutzer übergibt.

## <a name="c-exceptions-versus-windows-seh-exceptions"></a>C++-Ausnahmen und Windows SEH-Ausnahmen

Sowohl C-Programme als auch C++-Programme können den Mechanismus der strukturierten Ausnahmebehandlung (Structured Exception Handling, SEH) im Windows-Betriebssystem verwenden. Die Konzepte in SEH ähneln denen in C++-Ausnahmen, mit dem Unterschied, dass SEH die- **`__try`** , **`__except`** -und- **`__finally`** Konstrukte anstelle von **`try`** und verwendet **`catch`** . Im Microsoft C++-Compiler (MSVC) werden C++-Ausnahmen für Seh implementiert. Wenn Sie jedoch C++-Code schreiben, verwenden Sie die Syntax für C++-Ausnahmen.

Weitere Informationen zu seh finden Sie unter [strukturierte Ausnahmebehandlung (C/C++)](structured-exception-handling-c-cpp.md).

## <a name="exception-specifications-and-noexcept"></a><a name="exception_specifications_and_noexcept"></a> Ausnahme Spezifikationen und `noexcept`

Ausnahmespezifikationen wurden in C++ als Möglichkeit eingeführt, um die Ausnahmen festzulegen, die eine Funktion auslösen kann. Ausnahmespezifikationen haben sich in der Praxis jedoch als problematisch herausgestellt und wurden im Normenentwurf C++11 als veraltet gekennzeichnet. Es wird empfohlen, keine **`throw`** Ausnahme Spezifikationen mit Ausnahme von zu verwenden `throw()` , was darauf hinweist, dass die Funktion keine Ausnahmen zulässt. Wenn Sie Ausnahme Spezifikationen der veralteten Form verwenden müssen `throw( type-name )` , ist die MSVC-Unterstützung eingeschränkt. Weitere Informationen finden Sie unter [Ausnahme Spezifikationen (Throw)](exception-specifications-throw-cpp.md). Der **`noexcept`** Spezifizierer wird in c++ 11 als bevorzugte Alternative zu eingeführt `throw()` .

## <a name="see-also"></a>Weitere Informationen

[Gewusst wie: Schnittstelle zwischen Ausnahme-und nicht-Ausnahme Code](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)<br/>
[C++-Sprachreferenz](../cpp/cpp-language-reference.md)<br/>
[C++-Standard Bibliothek](../standard-library/cpp-standard-library-reference.md)
