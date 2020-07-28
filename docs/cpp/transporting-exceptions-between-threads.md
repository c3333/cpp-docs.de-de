---
title: Transportieren von Ausnahmen zwischen Threads
ms.date: 05/07/2019
helpviewer_keywords:
- std::current_exception
- transporting exceptions between threads
- std::copy_exception
- exception_ptr
- std::exception_ptr
- std::rethrow_exception
- current_exception
- transport exceptions between threads
- copy_exception
- rethrow_exception
- move exceptions between threads
ms.assetid: 5c95d57b-acf5-491f-8122-57c5df0edd98
ms.openlocfilehash: 1b3e6ffa0e98d54b047e18e4c023a8f5173470b1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87186099"
---
# <a name="transporting-exceptions-between-threads"></a>Transportieren von Ausnahmen zwischen Threads

Der Microsoft C++-Compiler (MSVC) unterstützt das *transportieren einer Ausnahme* von einem Thread zu einem anderen. Durch das Transportieren von Ausnahmen können Sie eine Ausnahme in einem Thread abfangen und anschließend die Ausnahme scheinbar in einem anderen Thread auslösen lassen. Sie können diese Funktion beispielsweise verwenden, um eine Multithreadanwendung zu schreiben, in der der primäre Thread alle Ausnahmen behandelt, die von seinen sekundären Threads ausgelöst werden. Das Transportieren von Ausnahmen ist insbesondere für Entwickler hilfreich, die parallele Programmierbibliotheken und -systeme erstellen. Zum Implementieren von Transport Ausnahmen stellt MSVC den [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) -Typ und die Funktionen [current_exception](../standard-library/exception-functions.md#current_exception), [rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)und [make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr) bereit.

## <a name="syntax"></a>Syntax

```cpp
namespace std
{
   typedef unspecified exception_ptr;
   exception_ptr current_exception();
   void rethrow_exception(exception_ptr p);
   template<class E>
       exception_ptr make_exception_ptr(E e) noexcept;
}
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*nicht angegeben*|Eine nicht angegebene interne Klasse, die verwendet wird, um den Typ `exception_ptr` zu implementieren.|
|*cker*|Ein `exception_ptr`-Objekt, das auf eine Ausnahme verweist.|
|*Fresser*|Eine Klasse, die eine Ausnahme darstellt.|
|*e*|Eine Instanz der `E`-Parameterklasse.|

## <a name="return-value"></a>Rückgabewert

Die `current_exception`-Funktion gibt ein `exception_ptr`-Objekt zurück, das auf die Ausnahme verweist, die gerade ausgeführt wird. Wenn keine Ausnahme ausgeführt wird, gibt die Funktion ein `exception_ptr`-Objekt zurück, das keiner Ausnahme zugeordnet ist.

Die- `make_exception_ptr` Funktion gibt ein- `exception_ptr` Objekt zurück, das auf die durch den *e* -Parameter angegebene Ausnahme verweist.

## <a name="remarks"></a>Bemerkungen

### <a name="scenario"></a>Szenario

Angenommen, Sie möchten eine Anwendung erstellen, die skaliert werden kann, um einen variablen Arbeitsaufwand zu verarbeiten. Um dieses Ziel zu erreichen, entwerfen Sie eine Multithreadanwendung, in der ein primärer Ausgangsthread so viele sekundäre Threads erstellt, wie zum Ausführen des Auftrags benötigt werden. Die sekundären Threads helfen dem primären Thread, Ressourcen zu verwalten, einen Lastausgleich vorzunehmen und den Durchsatz zu verbessern. Durch Verteilen der Arbeit zeigt die Multithreadanwendung eine bessere Leistung als eine Singlethreadanwendung.

Wenn jedoch ein sekundärer Thread eine Ausnahme auslöst, sollte diese vom primären Thread behandelt werden. Dies liegt daran, dass die Anwendung Ausnahmen auf konsistente, einheitliche Art und Weise behandeln sollte, unabhängig von der Anzahl von sekundären Threads.

### <a name="solution"></a>Lösung

Um das vorherige Szenario zu behandeln, unterstützt der C++-Standard das Transportieren einer Ausnahme zwischen Threads. Wenn ein sekundärer Thread eine Ausnahme auslöst, wird diese Ausnahme zur *aktuellen Ausnahme*. Analog zur realen Welt wird die aktuelle *Ausnahme als aktiv bezeichnet.* Die aktuelle Ausnahme ist aktiv, sobald sie ausgelöst wird, bis der Ausnahmehandler, der sie abfängt, zurückgegeben wird.

Der sekundäre Thread kann die aktuelle Ausnahme in einem **`catch`** -Block abfangen und dann die- `current_exception` Funktion zum Speichern der Ausnahme in einem-Objekt aufzurufen `exception_ptr` . Das `exception_ptr`-Objekt muss für den sekundären Thread und den primären Thread verfügbar sein. Beispielsweise kann das `exception_ptr`-Objekt eine globale Variable sein, deren Zugriff durch einen Mutex gesteuert wird. Der Begriff *Transport a Exception* bedeutet, dass eine Ausnahme in einem Thread in ein Formular konvertiert werden kann, auf das von einem anderen Thread zugegriffen werden kann.

Anschließend ruft der primäre Thread die `rethrow_exception`-Funktion auf, die die Ausnahme extrahiert und anschließend aus dem `exception_ptr`-Objekt auslöst. Wenn die Ausnahme ausgelöst wird, wird sie zur aktuellen Ausnahme im primären Thread. Das heißt, die Ausnahme stammt scheinbar aus dem primären Thread.

Schließlich kann der primäre Thread die aktuelle Ausnahme in einem **`catch`** -Block abfangen und dann verarbeiten oder an einen Ausnahmehandler auf höherer Ebene auslösen. Oder der primäre Thread kann die Ausnahme ignorieren und das Beenden des Vorgangs erlauben.

Die meisten Anwendungen müssen keine Ausnahmen zwischen Threads transportieren. Allerdings ist diese Funktion auf einem parallelen Computersystem nützlich, da das System die Arbeit auf sekundäre Threads, Prozessoren oder Kerne aufteilen kann. In einer parallelen Computerumgebung kann ein einzelner, dedizierter Thread alle Ausnahmen von den sekundären Threads behandeln und ein konsistentes Ausnahmebehandlungsmodell für jede Anwendung bieten.

Weitere Informationen zum Antrag des Ausschusses für C++-Standards finden Sie im Internet. Suchen Sie nach der Dokumentnummer N2179 und Sprachenunterstützung für das Transportieren von Ausnahmen zwischen Threads.

### <a name="exception-handling-models-and-compiler-options"></a>Ausnahme Behandlungsmodelle und Compileroptionen

Das Ausnahmebehandlungsmodell Ihrer Anwendung bestimmt, ob eine Ausnahme abgefangen und transportiert werden kann. Visual C++ unterstützt drei Modelle, die C++-Ausnahmen, SEH-Ausnahmen (Structured Exception Handling, Strukturierte Ausnahmebehandlung) und Common Language Runtime (CLR)-Ausnahmen behandeln können. Verwenden Sie die Compileroptionen [/eh](../build/reference/eh-exception-handling-model.md) und [/CLR](../build/reference/clr-common-language-runtime-compilation.md) , um das Modell für die Ausnahmebehandlung Ihrer Anwendung anzugeben.

Nur die folgende Kombination von Compileroptionen und Programmieranweisungen kann eine Ausnahme transportieren. Andere Kombinationen können entweder keine Ausnahmen abfangen oder Ausnahmen zwar abfangen, jedoch nicht transportieren.

- Die **/EHa** -Compileroption und die- **`catch`** Anweisung können Seh-und C++-Ausnahmen transportieren.

- Die **/EHa**-, **/EHS**-und **/EHsc** -Compileroptionen und die- **`catch`** Anweisung können C++-Ausnahmen transportieren.

- Die **/CLR** -Compileroption und die- **`catch`** Anweisung können C++-Ausnahmen transportieren. Die **/CLR** -Compileroption impliziert die Angabe der **/EHa** -Option. Beachten Sie, dass der Compiler das Transportieren von verwalteten Ausnahmen nicht unterstützt. Dies liegt daran, dass verwaltete Ausnahmen, die von der [System. Exception-Klasse](../standard-library/exception-class.md)abgeleitet werden, bereits Objekte sind, die Sie mithilfe der Funktionen der Common Language-Laufzeit zwischen Threads verschieben können.

   > [!IMPORTANT]
   > Es wird empfohlen, die **/EHsc** -Compileroption anzugeben und nur C++-Ausnahmen abzufangen. Wenn Sie die **/EHa** -oder **/CLR** -Compileroption und eine **`catch`** -Anweisung mit einer Ellipse *-Ausnahme Deklaration* () verwenden, machen Sie sich selbst eine Sicherheitsbedrohung ausgesetzt `catch(...)` . Wahrscheinlich möchten Sie die- **`catch`** Anweisung verwenden, um einige spezifische Ausnahmen zu erfassen. Allerdings fängt die `catch(...)`-Anweisung alle C++- und SEH-Ausnahmen ab, einschließlich der unerwarteten Ausnahmen mit schwerwiegenden Ausnahmefehlern. Wenn Sie eine unerwartete Ausnahme nicht korrekt behandeln oder ignorieren, kann Malware-Code diese Möglichkeit nutzen, die Sicherheit Ihres Programms zu beeinträchtigen.

## <a name="usage"></a>Verbrauch

In den folgenden Abschnitten wird beschrieben, wie Ausnahmen mithilfe des `exception_ptr` -Typs und der `current_exception` Funktionen, und transportiert werden `rethrow_exception` `make_exception_ptr` .

## <a name="exception_ptr-type"></a>exception_ptr-Typ

Verwenden Sie ein `exception_ptr`-Objekt, um auf die aktuelle Ausnahme oder eine Instanz einer vom Benutzer angegebenen Ausnahme zu verweisen. In der Microsoft-Implementierung wird eine Ausnahme von einer [EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record)-Struktur dargestellt. Jedes `exception_ptr`-Objekt enthält ein Ausnahmeverweisfeld, das auf eine Kopie der `EXCEPTION_RECORD`-Struktur zeigt, die die Ausnahme darstellt.

Wenn Sie eine `exception_ptr`-Variable deklarieren, wird die Variable keiner Ausnahme zugeordnet. Das heißt, das Ausnahmeverweisfeld ist NULL. Ein solches `exception_ptr`-Objekt wird als *null exception_ptr* bezeichnet.

Verwenden Sie die Funktion `current_exception` oder `make_exception_ptr`, um eine Ausnahme einem `exception_ptr`-Objekt zuzuweisen. Wenn Sie einer `exception_ptr`-Variable eine Ausnahme zuweisen, zeigt das Ausnahmeverweisfeld der Variable auf eine Kopie der Ausnahme. Ist nicht genügend Arbeitsspeicher zum Kopieren der Ausnahme vorhanden, zeigt das Ausnahmeverweisfeld auf eine Kopie einer [std::bad_alloc](../standard-library/bad-alloc-class.md)-Ausnahme. Wenn die `current_exception` - `make_exception_ptr` Funktion oder die-Funktion die Ausnahme aus einem anderen Grund nicht kopieren kann, ruft die Funktion die Funktion [Beenden](../c-runtime-library/reference/terminate-crt.md) auf, um den aktuellen Prozess zu beenden.

Trotz seines Namens ist ein `exception_ptr`-Objekt nicht selbst ein Zeiger. Sie befolgt keine Zeiger Semantik und kann nicht mit den Operatoren "Pointer Member Access ()" oder "Dereferenzierungsoperator ()" verwendet werden `->` `*` . Das `exception_ptr`-Objekt weist keine öffentlichen Datenmember oder Memberfunktionen auf.

### <a name="comparisons"></a>Vergleiche

Sie können den Gleichheitsoperator (`==`) und den Ungleichheitsoperator (`!=`) verwenden, um zwei `exception_ptr`-Objekte zu vergleichen. Die Operatoren vergleichen nicht den Binärwert (Bitmuster) der `EXCEPTION_RECORD`-Strukturen, die die Ausnahmen darstellen. Stattdessen vergleichen die Operatoren die Adressen im Ausnahmeverweisfeld der `exception_ptr`-Objekte. Folglich sind ein NULL-`exception_ptr` und der NULL-Wert gleichwertig.

## <a name="current_exception-function"></a>current_exception-Funktion

Ruft die- `current_exception` Funktion in einem- **`catch`** Block auf. Wenn eine Ausnahme aktiv ist und der- **`catch`** Block die Ausnahme abfangen kann, `current_exception` gibt die-Funktion ein- `exception_ptr` Objekt zurück, das auf die Ausnahme verweist. Andernfalls gibt die Funktion ein NULL-`exception_ptr`-Objekt zurück.

### <a name="details"></a>Details

Die- `current_exception` Funktion erfasst die Ausnahme, die aktiv ist, unabhängig davon, ob die **`catch`** -Anweisung eine [Exception-Declaration-](../cpp/try-throw-and-catch-statements-cpp.md) Anweisung angibt.

Der Dekonstruktor für die aktuelle Ausnahme wird am Ende des Blocks aufgerufen, **`catch`** Wenn die Ausnahme nicht erneut ausgelöst wird. Auch wenn Sie die `current_exception`-Funktion im Destruktor aufrufen, gibt die Funktion ein `exception_ptr`-Objekt zurück, das auf die aktuelle Ausnahme verweist.

Aufeinander folgende Aufrufe der `current_exception`-Funktion geben `exception_ptr`-Objekte zurück, die sich auf unterschiedliche Kopien der aktuellen Ausnahme beziehen. Folglich sind die Objekte bei einem Vergleich ungleich, da sie auf unterschiedliche Kopien verweisen, auch wenn die Kopien den gleichen Binärwert aufweisen.

### <a name="seh-exceptions"></a>SEH-Ausnahmen

Wenn Sie die **/EHa** -Compileroption verwenden, können Sie eine SEH-Ausnahme in einem C++-Block abfangen **`catch`** . Die `current_exception`-Funktion gibt ein `exception_ptr`-Objekt zurück, das auf die SEH-Ausnahme verweist. Und die- `rethrow_exception` Funktion löst die SEH-Ausnahme aus, wenn Sie Sie mit dem über transportierten `exception_ptr` Objekt als Argument aufruft.

Die- `current_exception` Funktion gibt einen NULL-Wert zurück `exception_ptr` , wenn Sie ihn in einem SEH-Beendigungs **`__finally`** Handler, einem **`__except`** Ausnahmehandler oder dem **`__except`** Filter Ausdruck aufruft.

Eine transportierte Ausnahme unterstützt keine geschachtelte Ausnahmen. Eine geschachtelte Ausnahme tritt auf, wenn eine andere Ausnahme ausgelöst wird, während eine Ausnahme behandelt wird. Wenn Sie eine geschachtelte Ausnahme abfangen, zeigt der `EXCEPTION_RECORD.ExceptionRecord`-Datenmember auf eine Kette von `EXCEPTION_RECORD`-Strukturen, die die zugeordneten Ausnahmen beschreiben. Die `current_exception`-Funktion unterstützt keine geschachtelte Ausnahmen, da sie ein `exception_ptr`-Objekt zurückgibt, dessen `ExceptionRecord`-Datenmember auf Null gesetzt ist.

Wenn Sie eine SEH-Ausnahme abfangen, müssen Sie den Speicher verwalten, auf den von einem Zeiger im `EXCEPTION_RECORD.ExceptionInformation`-Datenmemberarray verwiesen wird. Sie müssen sicherstellen, dass der Arbeitsspeicher während der Lebensdauer des entsprechenden `exception_ptr`-Objekts gültig ist und dass der Arbeitsspeicher freigegeben wird, wenn das `exception_ptr`-Objekt gelöscht wird.

Sie können Funktionen des Konvertierungsprogramms für strukturierte Ausnahmen zusammen mit der Funktion für den Ausnahmetransport verwenden. Wenn eine SEH-Ausnahme in eine C++-Ausnahme übersetzt wird, gibt die `current_exception`-Funktion einen `exception_ptr` zurück, der auf die übersetzte Ausnahme anstelle der ursprünglichen SEH-Ausnahme verweist. Die `rethrow_exception`-Funktion löst daraufhin die übersetzte Ausnahme, nicht die ursprüngliche Ausnahme, aus. Weitere Informationen zu den Funktionen von SE Translator finden Sie unter [_set_se_translator](../c-runtime-library/reference/set-se-translator.md).

## <a name="rethrow_exception-function"></a>rethrow_exception-Funktion

Nachdem Sie eine abgefangene Ausnahme in einem `exception_ptr`-Objekt gespeichert haben, kann der primäre Thread das Objekt verarbeiten. Rufen Sie in Ihrem primären Thread die `rethrow_exception`-Funktion zusammen mit dem `exception_ptr`-Objekt als Argument auf. Die `rethrow_exception`-Funktion extrahiert die Ausnahme vom `exception_ptr`-Objekt und löst die Ausnahme anschließend im Kontext des primären Threads aus. Wenn der *p* -Parameter der `rethrow_exception` Funktion NULL ist `exception_ptr` , löst die Funktion [Std:: Bad_exception](../standard-library/bad-exception-class.md)aus.

Die extrahierte Ausnahme ist jetzt die aktuelle Ausnahme im primären Thread, und Sie können sie behandeln wie jede andere Ausnahme. Wenn Sie die Ausnahme abfangen, können Sie Sie sofort behandeln oder eine-Anweisung verwenden, **`throw`** um Sie an einen Ausnahmehandler auf höherer Ebene zu senden. Unternehmen Sie anderenfalls nichts, und lassen Sie den standardmäßigen Systemausnahmehandler den Prozess beenden.

## <a name="make_exception_ptr-function"></a>make_exception_ptr-Funktion

Die `make_exception_ptr`-Funktion akzeptiert eine Instanz einer Klasse als Argument und gibt dann einen `exception_ptr` zurück, der auf die Instanz verweist. Normalerweise geben Sie ein [exception class](../standard-library/exception-class.md)-Objekt als Argument für die `make_exception_ptr`-Funktion an, obwohl jedes Klassenobjekt als Argument zulässig ist.

Das Aufrufen der- `make_exception_ptr` Funktion entspricht dem Auslösen einer C++-Ausnahme, dem Abfangen in einem **`catch`** -Block und dem anschließenden Aufrufen der- `current_exception` Funktion, um ein Objekt zurückzugeben, `exception_ptr` das auf die Ausnahme verweist. Die Microsoft-Implementierung der `make_exception_ptr`-Funktion ist effizienter als das Auslösen und anschließende Abfangen einer Ausnahme.

Eine Anwendung erfordert in der Regel nicht die `make_exception_ptr` -Funktion, und es wird von ihrer Verwendung abgeraten.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird eine Standard-C++-Ausnahme und eine benutzerdefinierte C++-Ausnahme von einem Thread zu einem anderen transportiert.

```cpp
// transport_exception.cpp
// compile with: /EHsc /MD
#include <windows.h>
#include <stdio.h>
#include <exception>
#include <stdexcept>

using namespace std;

// Define thread-specific information.
#define THREADCOUNT 2
exception_ptr aException[THREADCOUNT];
int           aArg[THREADCOUNT];

DWORD WINAPI ThrowExceptions( LPVOID );

// Specify a user-defined, custom exception.
// As a best practice, derive your exception
// directly or indirectly from std::exception.
class myException : public std::exception {
};
int main()
{
    HANDLE aThread[THREADCOUNT];
    DWORD ThreadID;

    // Create secondary threads.
    for( int i=0; i < THREADCOUNT; i++ )
    {
        aArg[i] = i;
        aThread[i] = CreateThread(
            NULL,       // Default security attributes.
            0,          // Default stack size.
            (LPTHREAD_START_ROUTINE) ThrowExceptions,
            (LPVOID) &aArg[i], // Thread function argument.
            0,          // Default creation flags.
            &ThreadID); // Receives thread identifier.
        if( aThread[i] == NULL )
        {
            printf("CreateThread error: %d\n", GetLastError());
            return -1;
        }
    }

    // Wait for all threads to terminate.
    WaitForMultipleObjects(THREADCOUNT, aThread, TRUE, INFINITE);
    // Close thread handles.
    for( int i=0; i < THREADCOUNT; i++ ) {
        CloseHandle(aThread[i]);
    }

    // Rethrow and catch the transported exceptions.
    for ( int i = 0; i < THREADCOUNT; i++ ) {
        try {
            if (aException[i] == NULL) {
                printf("exception_ptr %d: No exception was transported.\n", i);
            }
            else {
                rethrow_exception( aException[i] );
            }
        }
        catch( const invalid_argument & ) {
            printf("exception_ptr %d: Caught an invalid_argument exception.\n", i);
        }
        catch( const myException & ) {
            printf("exception_ptr %d: Caught a  myException exception.\n", i);
        }
    }
}
// Each thread throws an exception depending on its thread
// function argument, and then ends.
DWORD WINAPI ThrowExceptions( LPVOID lpParam )
{
    int x = *((int*)lpParam);
    if (x == 0) {
        try {
            // Standard C++ exception.
            // This example explicitly throws invalid_argument exception.
            // In practice, your application performs an operation that
            // implicitly throws an exception.
            throw invalid_argument("A C++ exception.");
        }
        catch ( const invalid_argument & ) {
            aException[x] = current_exception();
        }
    }
    else {
        // User-defined exception.
        aException[x] = make_exception_ptr( myException() );
    }
    return TRUE;
}
```

```Output
exception_ptr 0: Caught an invalid_argument exception.
exception_ptr 1: Caught a  myException exception.
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<exception>

## <a name="see-also"></a>Weitere Informationen

[Behandlung von Ausnahmen](../cpp/exception-handling-in-visual-cpp.md)<br/>
[/EH (Ausnahme Behandlungsmodell)](../build/reference/eh-exception-handling-model.md)<br/>
[/clr (Common Language Runtime-Kompilierung)](../build/reference/clr-common-language-runtime-compilation.md)
