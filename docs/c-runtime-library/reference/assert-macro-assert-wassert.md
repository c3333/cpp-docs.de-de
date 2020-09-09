---
title: assert-Makro, _assert, _wassert
description: Die Auswirkungen der Assert-Makros und-Funktionen in der C-Laufzeit.
ms.date: 11/04/2016
api_name:
- assert
- _assert
- _wassert
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- assert
- _assert
- _wassert
- assert/_wassert
helpviewer_keywords:
- aborting programs
- assert function
- assert macro
ms.assetid: a9ca031a-648b-47a6-bdf1-65fc7399dd40
ms.openlocfilehash: 071424f2201ceda43438fe1056801811fe444a01
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609074"
---
# <a name="assert-macro-_assert-_wassert"></a>assert-Makro, _assert, _wassert

Wertet einen Ausdruck aus und gibt, wenn das Ergebnis ist **`false`** , eine Diagnose Meldung aus und bricht das Programm ab.

## <a name="syntax"></a>Syntax

```C
assert(
   expression
);
void _assert(
   char const* message,
   char const* filename,
   unsigned line
);
void _wassert(
   wchar_t const* message,
   wchar_t const* filename,
   unsigned line
);
```

### <a name="parameters"></a>Parameter

*expression*<br/>
Ein skalarer Ausdruck (einschließlich Zeiger Ausdrücken), der zu ungleich NULL ( **`true`** ) oder 0 () ausgewertet wird **`false`** .

*Nachricht*<br/>
Die anzuzeigende Meldung.

*filename*<br/>
Der Name der Quelldatei, in der der Assertionsfehler aufgetreten ist.

*line*<br/>
Die Zeilennummer in der Quelldatei mit dem Assertionsfehler.

## <a name="remarks"></a>Hinweise

Das `assert` -Makro wird normalerweise verwendet, um Logikfehler während der Programmentwicklung zu erkennen. Verwenden Sie es, um die Programmausführung zu beenden, wenn unerwartete Bedingungen auftreten, indem Sie das *Ausdrucks* Argument so implementieren, dass es **`false`** nur dann in ausgewertet wird, wenn das Programm Assertionsüberprüfungen können zur Kompilierzeit durch Definieren des Makros **NDEBUG**deaktiviert werden. Mithilfe der Befehlszeilenoption `assert` können Sie das **assert** -Makro deaktivieren, ohne Ihre Quelldateien zu verändern. Sie können das- `assert` Makro im Quellcode mit einer- `#define NDEBUG` Direktive ausschalten, bevor \<assert.h> enthalten ist.

Das- `assert` Makro gibt eine Diagnose Meldung aus, wenn der *Ausdruck* zu **`false`** (0) ausgewertet wird und Aufrufe [`abort`](abort.md) zum Beenden der Programmausführung Es wird keine Aktion ausgeführt, wenn *Expression* **`true`** (ungleich null) ist. Die Diagnosemeldung enthält den Ausdruck, für den der Fehler aufgetreten ist, den Namen der Quelldatei und die Nummer der Zeile, in der der Assertionsfehler aufgetreten ist.

Die Diagnose Meldung wird in breit Zeichen gedruckt `wchar_t` . Daher funktioniert sie erwartungsgemäß, auch wenn Unicode-Zeichen im Ausdruck vorhanden sind.

Das Ziel der Diagnosemeldung hängt vom Typ der Anwendung ab, die die Routine aufgerufen hat. Konsolen Anwendungen empfangen die Nachricht über **stderr**. In einer Windows-basierten Anwendung `assert` Ruft die [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) -Funktion von Windows auf, um ein Meldungs Feld zu erstellen, in dem die Meldung mit drei Schaltflächen angezeigt wird: **Abbrechen**, **wiederholen**und **ignorieren**. Wenn der Benutzer auf **Abbrechen**klickt, wird das Programm sofort beendet. Wenn der Benutzer auf **Wiederholen**klickt, wird der Debugger aufgerufen und der Benutzer kann das Programm debuggen, wenn Just-In-Time (JIT)-Debuggen aktiviert ist. Wenn der Benutzer auf **ignorieren**klickt, wird das Programm mit normaler Ausführung fortgesetzt. Wenn Sie auf " **ignorieren** " klicken, wenn ein Fehlerzustand vorhanden ist, kann dies zu einem nicht definierten Verhalten führen, da die Vorbedingungen des

Um das Standardausgabe Verhalten unabhängig vom APP-Typ zu überschreiben, [`_set_error_mode`](set-error-mode.md) müssen Sie aufrufen, um zwischen dem Verhalten Output-to-stderr und Display-Dialogfeld auszuwählen.

Nachdem `assert` die zugehörige Meldung angezeigt hat, ruft Sie auf [`abort`](abort.md) . Daraufhin wird ein Dialogfeld mit den Schaltflächen  **Abbrechen**, **wiederholen**und **ignorieren** angezeigt. [`abort`](abort.md) beendet das Programm, sodass die Programmausführung nach dem-Befehl durch die Schaltfläche **wiederholen** und **ignorieren** nicht fortgesetzt wird `assert` . Wenn `assert` ein Dialogfeld angezeigt wird, wird das [`abort`](abort.md) Dialogfeld nicht angezeigt. Das [`abort`](abort.md) Dialogfeld wird nur angezeigt, wenn die `assert` Ausgabe an stderr sendet.

Als Folge des obigen Verhaltens wird ein Dialogfeld nach einem- `assert` Rückruf im Debugmodus immer angezeigt. Das Verhalten der einzelnen Schaltflächen wird in der folgenden Tabelle aufgezeichnet.

|Fehler Modus|Ausgabe an stderr (Konsole/_OUT_TO_STDERR)|Anzeige (Dialog Feld) (Windows/_OUT_TO_MSGBOX)|
|----------|----------------|------------------|
|Abbruch|Sofort mit Exitcode 3 beenden|Sofort mit Exitcode 3 beenden|
|Erneut versuchen|In Debugger unterbrechen während `abort`|In Debugger unterbrechen während `assert`|
|Ignorieren|Beendigung beenden über `abort`|Programm fortsetzen, als hätte der Assert nicht ausgelöst (kann zu nicht definiertem Verhalten führen, da Vorbedingungen des aufrufenden Codes nicht erfüllt wurden)|

Weitere Informationen zum CRT-Debugging finden Sie unter [CRT-Debugverfahren](/visualstudio/debugger/crt-debugging-techniques).

Die Funktionen `_assert` und `_wassert` sind interne CRT-Funktionen. Sie helfen dabei, den für die Unterstützung von Assertion in Ihren Objektdateien erforderlichen Code zu minimieren. Es wird nicht empfohlen, diese Funktionen direkt aufzurufen.

Das- `assert` Makro ist sowohl in der Release-als auch in der Debugversion der C-Laufzeitbibliotheken aktiviert, wenn **NDEBUG** nicht definiert ist. Wenn **NDEBUG** definiert ist, ist das Makro verfügbar, wertet aber nicht sein Argument aus und hat keine Auswirkungen. Wenn es aktiviert ist, `assert` Ruft das Makro die `_wassert` Implementierung auf. Andere Assertionsmakros, [_ASSERT](assert-asserte-assert-expr-macros.md), [_ASSERTE](assert-asserte-assert-expr-macros.md) und [_ASSERT_EXPR](assert-asserte-assert-expr-macros.md), sind ebenfalls verfügbar, sie werten die ihnen übergebenen Ausdrücke jedoch nur aus, wenn das [_DEBUG](../../c-runtime-library/debug.md)-Makro definiert wurde und sie sich in Code befinden, der mit der Debugversion der C-Laufzeitbibliotheken gelinkt wurde.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|`assert`, `_wassert`|\<assert.h>|

Die Signatur der `_assert` Funktion ist nicht in einer Header Datei verfügbar. Die Signatur der `_wassert` Funktion ist nur verfügbar, wenn das **NDEBUG** -Makro nicht definiert ist.

## <a name="example"></a>Beispiel

In diesem Programm verwendet die **analyze_string** -Funktion das- `assert` Makro, um verschiedene Bedingungen im Zusammenhang mit String und length zu testen. Wenn bei einer der Bedingungen ein Fehler auftritt, gibt das Programm eine Meldung aus, die auf die Ursache des Fehlers hinweist.

```C
// crt_assert.c
// compile by using: cl /W4 crt_assert.c
#include <stdio.h>
#include <assert.h>
#include <string.h>

void analyze_string( char *string );   // Prototype

int main( void )
{
   char  test1[] = "abc", *test2 = NULL, test3[] = "";

   printf ( "Analyzing string '%s'\n", test1 ); fflush( stdout );
   analyze_string( test1 );
   printf ( "Analyzing string '%s'\n", test2 ); fflush( stdout );
   analyze_string( test2 );
   printf ( "Analyzing string '%s'\n", test3 ); fflush( stdout );
   analyze_string( test3 );
}

// Tests a string to see if it is NULL,
// empty, or longer than 0 characters.
void analyze_string( char * string )
{
   assert( string != NULL );        // Cannot be NULL
   assert( *string != '\0' );       // Cannot be empty
   assert( strlen( string ) > 2 );  // Length must exceed 2
}
```

Das Programm erzeugt diese Ausgabe:

```Output
Analyzing string 'abc'
Analyzing string '(null)'
Assertion failed: string != NULL, file crt_assert.c, line 25
```

Abhängig von der Version des Betriebssystems und der Lauf Zeit Bibliothek wird ggf. ein Meldungs Feld angezeigt, das etwa wie folgt aussieht:

```Output
A problem caused the program to stop working correctly. Windows will close the program and notify you if a solution is available.
```

Wenn ein Debugger installiert ist, wählen Sie die Schaltfläche **Debug** aus, um den Debugger zu starten, oder **Programm schließen** zum Beenden.

## <a name="see-also"></a>Weitere Informationen

[Fehlerbehandlung](../../c-runtime-library/error-handling-crt.md)<br/>
[Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[Abbruch](abort.md)<br/>
[züchten](raise.md)<br/>
[signal](signal.md)<br/>
[_ASSERT, _ASSERTE _ASSERT_EXPR Makros](assert-asserte-assert-expr-macros.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
