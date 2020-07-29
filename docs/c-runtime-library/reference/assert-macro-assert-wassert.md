---
title: assert-Makro, _assert, _wassert
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
ms.openlocfilehash: 173974cfd9d3f9b3fc054bb71ad70b757f8ef819
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232624"
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

*Stimmen*<br/>
Die Zeilennummer in der Quelldatei mit dem Assertionsfehler.

## <a name="remarks"></a>Bemerkungen

Das **Assert** -Makro wird normalerweise verwendet, um Logikfehler während der Programmentwicklung zu identifizieren. Verwenden Sie es, um die Programmausführung zu beenden, wenn unerwartete Bedingungen auftreten, indem Sie das *Ausdrucks* Argument so implementieren, dass es **`false`** nur dann in ausgewertet wird, wenn das Programm Assertionsüberprüfungen können zur Kompilierzeit durch Definieren des Makros **NDEBUG**deaktiviert werden. Sie können das **Assert** -Makro deaktivieren, ohne die Quelldateien zu ändern, indem Sie die Befehlszeilenoption **/DNDEBUG** verwenden. Sie können das **Assert** -Makro im Quellcode deaktivieren, indem Sie eine- `#define NDEBUG` Direktive verwenden, bevor \<assert.h> enthalten ist.

Das **Assert** -Makro gibt eine Diagnose Meldung aus, wenn *Expression* zu **`false`** (0) ausgewertet wird, und ruft [Abbruch](abort.md) auf, um die Programmausführung zu beenden. Es wird keine Aktion ausgeführt, wenn *Expression* **`true`** (ungleich null) ist. Die Diagnosemeldung enthält den Ausdruck, für den der Fehler aufgetreten ist, den Namen der Quelldatei und die Nummer der Zeile, in der der Assertionsfehler aufgetreten ist.

Die Diagnosemeldung wird in Breitzeichen ausgegeben. Daher funktioniert sie auch dann erwartungsgemäß, wenn sich Unicode-Zeichen im Ausdruck befinden.

Das Ziel der Diagnosemeldung hängt vom Typ der Anwendung ab, die die Routine aufgerufen hat. Konsolen Anwendungen empfangen die Nachricht immer über **stderr**. In einer Windows-basierten Anwendung ruft **Assert** die [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) -Funktion von Windows auf, um ein Meldungs Feld zu erstellen, in dem die Meldung zusammen mit einer **OK** -Schaltfläche angezeigt wird. Wenn der Benutzer auf **OK**klickt, wird das Programm sofort beendet.

Wenn die Anwendung mit einer Debugversion der Laufzeitbibliotheken verknüpft ist, erstellt **Assert** ein Meldungs Feld mit drei Schaltflächen: **Abbrechen**, **wiederholen**und **ignorieren**. Wenn der Benutzer auf **Abbrechen**klickt, wird das Programm sofort beendet. Wenn der Benutzer auf **Wiederholen**klickt, wird der Debugger aufgerufen und der Benutzer kann das Programm debuggen, wenn Just-In-Time (JIT)-Debuggen aktiviert ist. Wenn der Benutzer auf **ignorieren**klickt, wird **Assert** mit der normalen Ausführung fortgesetzt: Erstellen des Meldungs Felds mit der Schaltfläche " **OK** ". Wenn ein Fehlerzustand vorliegt, kann das Klicken auf **Ignorieren** zu undefiniertem Verhalten führen.

Weitere Informationen zum CRT-Debugging finden Sie unter [CRT-Debugverfahren](/visualstudio/debugger/crt-debugging-techniques).

Die Funktionen **_ASSERT** und **_wassert** sind interne CRT-Funktionen. Sie helfen dabei, den für die Unterstützung von Assertion in Ihren Objektdateien erforderlichen Code zu minimieren. Wir empfehlen nicht, diese Funktionen direkt aufzurufen.

Das **Assert** -Makro ist sowohl in der Release-als auch der Debugversion der C-Laufzeitbibliotheken aktiviert, wenn **NDEBUG** nicht definiert ist. Wenn **NDEBUG** definiert ist, ist das Makro verfügbar, wertet aber nicht sein Argument aus und hat keine Auswirkungen. Wenn es aktiviert ist, ruft das **Assert** -Makro **_wassert** für seine Implementierung auf. Andere Assertionsmakros, [_ASSERT](assert-asserte-assert-expr-macros.md), [_ASSERTE](assert-asserte-assert-expr-macros.md) und [_ASSERT_EXPR](assert-asserte-assert-expr-macros.md), sind ebenfalls verfügbar, sie werten die ihnen übergebenen Ausdrücke jedoch nur aus, wenn das [_DEBUG](../../c-runtime-library/debug.md)-Makro definiert wurde und sie sich in Code befinden, der mit der Debugversion der C-Laufzeitbibliotheken gelinkt wurde.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**Assert**, **_wassert**|\<assert.h>|

Die Signatur der **_ASSERT** -Funktion ist nicht in einer Header Datei verfügbar. Die Signatur der **_wassert** -Funktion ist nur verfügbar, wenn das **NDEBUG** -Makro nicht definiert ist.

## <a name="example"></a>Beispiel

In diesem Programm verwendet die **analyze_string** -Funktion das **Assert** -Makro, um verschiedene Bedingungen im Zusammenhang mit String und length zu testen. Wenn bei einer der Bedingungen ein Fehler auftritt, gibt das Programm eine Meldung aus, die auf die Ursache des Fehlers hinweist.

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

Je nach Version von Betriebssystem und Laufzeitbibliothek, wird möglicherweise nach dem Assertionsfehler ein Meldungsfeld angezeigt, das etwas in dieser Art enthält:

```Output
A problem caused the program to stop working correctly. Windows will close the program and notify you if a solution is available.
```

Wenn ein Debugger installiert ist, wählen Sie die Schaltfläche **Debug** aus, um den Debugger zu starten, oder **Programm schließen** zum Beenden.

## <a name="see-also"></a>Siehe auch

[Fehlerbehandlung](../../c-runtime-library/error-handling-crt.md)<br/>
[Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[raise](raise.md)<br/>
[signal](signal.md)<br/>
[_ASSERT, _ASSERTE _ASSERT_EXPR Makros](assert-asserte-assert-expr-macros.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
