---
title: _beginthread, _beginthreadex
ms.date: 4/2/2020
api_name:
- _beginthread
- _beginthreadex
- _o__beginthread
- _o__beginthreadex
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- beginthread
- _beginthread
- beginthreadex
- _beginthreadex
helpviewer_keywords:
- _beginthread function
- threading [C++], creating threads
- beginthreadex function
- _beginthreadex function
- beginthread function
ms.assetid: 0df64740-a978-4358-a88f-fb0702720091
ms.openlocfilehash: 2d2851a7e76a43501145b1e55e8028b72c2a8afb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348676"
---
# <a name="_beginthread-_beginthreadex"></a>_beginthread, _beginthreadex

Erstellt einen Thread.

## <a name="syntax"></a>Syntax

```cpp
uintptr_t _beginthread( // NATIVE CODE
   void( __cdecl *start_address )( void * ),
   unsigned stack_size,
   void *arglist
);
uintptr_t _beginthread( // MANAGED CODE
   void( __clrcall *start_address )( void * ),
   unsigned stack_size,
   void *arglist
);
uintptr_t _beginthreadex( // NATIVE CODE
   void *security,
   unsigned stack_size,
   unsigned ( __stdcall *start_address )( void * ),
   void *arglist,
   unsigned initflag,
   unsigned *thrdaddr
);
uintptr_t _beginthreadex( // MANAGED CODE
   void *security,
   unsigned stack_size,
   unsigned ( __clrcall *start_address )( void * ),
   void *arglist,
   unsigned initflag,
   unsigned *thrdaddr
);
```

### <a name="parameters"></a>Parameter

*start_address*<br/>
Startadresse einer Routine, die die Ausführung eines neuen Threads beginnt. Bei **_beginthread**ist die Aufrufkonvention entweder [__cdecl](../../cpp/cdecl.md) (für systemeigenen Code) oder [__clrcall](../../cpp/clrcall.md) (für verwalteten Code); für **_beginthreadex**ist es entweder [__stdcall](../../cpp/stdcall.md) (für systemeigenen Code) oder [__clrcall](../../cpp/clrcall.md) (für verwalteten Code).

*Stack_size*<br/>
Stapelgröße für einen neuen Thread oder 0.

*Arglist*<br/>
Argumentliste, die an einen neuen Thread oder **NULL**übergeben werden soll.

*Security*<br/>
Zeiger auf eine [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) -Struktur, die bestimmt, ob das zurückgegebene Handle von untergeordneten Prozessen geerbt werden kann. Wenn *Sicherheit* **NULL**ist, kann das Handle nicht vererbt werden. Muss **NULL** für Windows 95-Anwendungen sein.

*initflag*<br/>
Flags, die den anfänglichen Zustand eines neuen Threads steuern. Setzen Sie *initflag* auf 0, um sofort ausgeführt zu werden, oder **CREATE_SUSPENDED,** um den Thread in einem angehaltenen Zustand zu erstellen. Verwenden Sie [ResumeThread,](/windows/win32/api/processthreadsapi/nf-processthreadsapi-resumethread) um den Thread auszuführen. Legen Sie *initflag* auf **STACK_SIZE_PARAM_IS_A_RESERVATION-Flag** fest, um *stack_size* als anfängliche Reservegröße des Stapels in Bytes zu verwenden. Wenn dieses Flag nicht angegeben ist, *gibt stack_size* die Commitgröße an.

*thrdaddr*<br/>
Zeigt auf eine 32-Bit-Variable, die den Threadbezeichner empfängt. Wenn es **NULL**ist, wird es nicht verwendet.

## <a name="return-value"></a>Rückgabewert

Wenn diese Funktionen erfolgreich sind, gibt sie ein Handle an den neu erstellten Thread zurück. Wenn der neu erstellte Thread jedoch zu schnell beendet wird, **gibt _beginthread** möglicherweise kein gültiges Handle zurück. (Siehe die Diskussion im Abschnitt "Bemerkungen".) Bei einem Fehler **gibt _beginthread** -1L zurück, und **errno** wird auf **EAGAIN** gesetzt, wenn zu viele Threads vorhanden sind, auf **EINVAL,** wenn das Argument ungültig ist oder die Stapelgröße falsch ist, oder auf **EACCES,** wenn nicht genügend Ressourcen vorhanden sind (z. B. Arbeitsspeicher). Bei einem Fehler **gibt _beginthreadex** 0 zurück, und **errno** und **_doserrno** werden festgelegt.

Wenn *start_address* **NULL**ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, setzen diese Funktionen **errno** auf **EINVAL** und geben -1 zurück.

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Weitere Informationen **zu uintptr_t**finden Sie unter [Standardtypen](../../c-runtime-library/standard-types.md).

## <a name="remarks"></a>Bemerkungen

Die **_beginthread-Funktion** erstellt einen Thread, der mit der Ausführung einer Routine bei *start_address*beginnt. Die Routine bei *start_address* muss die **aufrufende** Konvention __cdecl (für systemeigenen Code) oder **__clrcall** (für verwalteten Code) verwenden und sollte keinen Rückgabewert aufweisen. Wenn der Thread aus dieser Routine zurückgegeben wird, wird er automatisch beendet. Weitere Informationen zu Threads finden Sie unter [Multithreadingunterstützung für älteren Code (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

**_beginthreadex** ähnelt der Win32 [CreateThread-API](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) stärker als **_beginthread.** **_beginthreadex** unterscheidet sich von **_beginthread** wie folgt:

- **_beginthreadex** hat drei zusätzliche Parameter: *initflag*, *Security*und **threadaddr**. Der neue Thread kann in einem angehaltenen Zustand mit einer angegebenen Sicherheit erstellt werden und kann mithilfe von *thrdaddr*, dem Threadbezeichner, aufgerufen werden.

- Die Routine bei *start_address,* **die** an _beginthreadex übergeben wird, muss die **Aufrufkonvention __stdcall** (für systemeigenen Code) oder **__clrcall** (für verwalteten Code) verwenden und einen Thread-Exit-Code zurückgeben.

- **_beginthreadex** gibt bei einem Fehler 0 zurück, anstatt -1L.

- Ein Thread, der mithilfe von **_beginthreadex** erstellt wird, wird durch einen Aufruf [von _endthreadex](endthread-endthreadex.md)beendet.

Die **_beginthreadex-Funktion** gibt Ihnen mehr Kontrolle darüber, wie der Thread erstellt wird, als **_beginthread.** Auch **die _endthreadex** Funktion ist flexibler. Mit **_beginthreadex**können Sie beispielsweise Sicherheitsinformationen verwenden, den Anfangszustand des Threads festlegen (ausgeführt oder angehalten) und den Threadbezeichner des neu erstellten Threads abrufen. Sie können auch das Threadhandle verwenden, das von **_beginthreadex** mit den Synchronisierungs-APIs zurückgegeben wird, was Sie mit **_beginthread**nicht tun können.

Es ist sicherer, **_beginthreadex** als **_beginthread**zu verwenden. Wenn der Thread, der von **_beginthread** generiert wird, schnell beendet wird, ist das Handle, das an den Aufrufer von **_beginthread** zurückgegeben wird, möglicherweise ungültig oder auf einen anderen Thread. Das Handle, das von **_beginthreadex** zurückgegeben wird, muss jedoch vom Aufrufer **von _beginthreadex**geschlossen werden, sodass es garantiert ein gültiges Handle ist, wenn **_beginthreadex** keinen Fehler zurückgegeben hat.

Sie können [_endthread](endthread-endthreadex.md) aufrufen oder **_endthreadex** explizit aufrufen, um einen Thread zu beenden. **_endthread** oder **_endthreadex** wird jedoch automatisch aufgerufen, wenn der Thread von der Routine zurückkehrt, die als Parameter übergeben wird. Das Beenden eines Threads mit einem Aufruf an **_endthread** oder **_endthreadex** trägt dazu bei, die korrekte Wiederherstellung von Ressourcen sicherzustellen, die dem Thread zugewiesen sind.

**_endthread** schließt das Gewindehandle automatisch, **_endthreadex** jedoch nicht. Wenn Sie **_beginthread** und **_endthread**verwenden, schließen Sie das Threadhandle daher nicht explizit, indem Sie die Win32 [CloseHandle-API](/windows/win32/api/handleapi/nf-handleapi-closehandle) aufrufen. Dieses Verhalten unterscheidet sich von dem der [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) -Win32-API.

> [!NOTE]
> Rufen Sie für eine ausführbare Datei, die mit Libcmt.lib verknüpft ist, die Win32 **ExitThread-API** nicht auf, damit Sie das Laufzeitsystem nicht daran hindern, zugewiesene Ressourcen zurückzufordern. **_endthread** und **_endthreadex** zugeordnete Threadressourcen zurückfordern und dann **ExitThread**aufrufen.

Das Betriebssystem übernimmt die Zuordnung des Stacks, wenn **_beginthread** oder **_beginthreadex** aufgerufen wird. Sie müssen die Adresse des Threadstapels nicht an eine dieser Funktionen übergeben. Darüber hinaus kann das *argument stack_size* 0 sein, in diesem Fall verwendet das Betriebssystem denselben Wert wie der Stapel, der für den Hauptthread angegeben ist.

*arglist* ist ein Parameter, der an den neu erstellten Thread übergeben werden soll. In der Regel ist das die Adresse eines Datenelements, z. B. einer Zeichenfolge. *arglist* kann **NULL** sein, wenn es nicht benötigt wird, aber **_beginthread** und **_beginthreadex** muss ein Wert gegeben werden, um an den neuen Thread übergeben zu werden. Alle Threads werden beendet, wenn Threads [abort](abort.md), **exit**, **_exit**oder **ExitProcess**aufrufen.

Das Gebietsschema des neuen Threads wird mithilfe der globalen aktuellen Gebietsschemainformationen pro Prozess initialisiert. Wenn ein Gebietsschema pro Thread durch einen Aufruf von [_configthreadlocale](configthreadlocale.md) aktiviert wird (entweder global oder nur für neue Threads), kann der Thread sein Gebietsschema unabhängig von anderen Threads ändern, indem **setlocale** oder **_wsetlocale**aufgerufen wird. Threads, die nicht über das Flag für ein Threadgebietsschema verfügen, können sich auf die Gebietsschemainformationen in allen anderen Threads auswirken, für die auch nicht das Flag pro Thread festgelegt ist, sowie auf alle neu erstellten Threads. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Für **/clr-Code** **haben _beginthread** und **_beginthreadex** jeweils zwei Überladungen. Der eine nimmt einen systemeigenen Aufrufkonventionsfunktionszeiger, der andere einen **__clrcall** Funktionszeiger. Die erste Überladung ist nicht anwendungsdomänensicher und wird es niemals sein. Wenn Sie **/clr-Code** schreiben, müssen Sie sicherstellen, dass der neue Thread in die richtige Anwendungsdomäne eindringt, bevor er auf verwaltete Ressourcen zugreift. Hierzu können Sie beispielsweise die [call_in_domain-Funktion](../../dotnet/call-in-appdomain-function.md) verwenden. Die zweite Überladung ist anwendungsdomänensicher; Der neu erstellte Thread landet immer in der Anwendungsdomäne des Aufrufers von **_beginthread** oder **_beginthreadex**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_beginthread**|\<process.h>|
|**_beginthreadex**|\<process.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Nur Multithread-Versionen von [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md) .

Um **_beginthread** oder **_beginthreadex**verwenden zu können, muss die Anwendung eine Verknüpfung mit einer der Multithread-C-Laufzeitbibliotheken herstellen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden **_beginthread** und **_endthread verwendet.**

```C
// crt_BEGTHRD.C
// compile with: /MT /D "_X86_" /c
// processor: x86
#include <windows.h>
#include <process.h>    /* _beginthread, _endthread */
#include <stddef.h>
#include <stdlib.h>
#include <conio.h>

void Bounce( void * );
void CheckKey( void * );

// GetRandom returns a random integer between min and max.
#define GetRandom( min, max ) ((rand() % (int)(((max) + 1) - (min))) + (min))
// GetGlyph returns a printable ASCII character value
#define GetGlyph( val ) ((char)((val + 32) % 93 + 33))

BOOL repeat = TRUE;                 // Global repeat flag
HANDLE hStdOut;                     // Handle for console window
CONSOLE_SCREEN_BUFFER_INFO csbi;    // Console information structure

int main()
{
    int param = 0;
    int * pparam = &param;

    // Get display screen's text row and column information.
    hStdOut = GetStdHandle( STD_OUTPUT_HANDLE );
    GetConsoleScreenBufferInfo( hStdOut, &csbi );

    // Launch CheckKey thread to check for terminating keystroke.
    _beginthread( CheckKey, 0, NULL );

    // Loop until CheckKey terminates program or 1000 threads created.
    while( repeat && param < 1000 )
    {
        // launch another character thread.
        _beginthread( Bounce, 0, (void *) pparam );

        // increment the thread parameter
        param++;

        // Wait one second between loops.
        Sleep( 1000L );
    }
}

// CheckKey - Thread to wait for a keystroke, then clear repeat flag.
void CheckKey( void * ignored )
{
    _getch();
    repeat = 0;    // _endthread implied
}

// Bounce - Thread to create and control a colored letter that moves
// around on the screen.
//
// Params: parg - the value to create the character from
void Bounce( void * parg )
{
    char       blankcell = 0x20;
    CHAR_INFO  ci;
    COORD      oldcoord, cellsize, origin;
    DWORD      result;
    SMALL_RECT region;

    cellsize.X = cellsize.Y = 1;
    origin.X = origin.Y = 0;

    // Generate location, letter and color attribute from thread argument.
    srand( _threadid );
    oldcoord.X = region.Left = region.Right =
        GetRandom(csbi.srWindow.Left, csbi.srWindow.Right - 1);
    oldcoord.Y = region.Top = region.Bottom =
        GetRandom(csbi.srWindow.Top, csbi.srWindow.Bottom - 1);
    ci.Char.AsciiChar = GetGlyph(*((int *)parg));
    ci.Attributes = GetRandom(1, 15);

    while (repeat)
    {
        // Pause between loops.
        Sleep( 100L );

        // Blank out our old position on the screen, and draw new letter.
        WriteConsoleOutputCharacterA(hStdOut, &blankcell, 1, oldcoord, &result);
        WriteConsoleOutputA(hStdOut, &ci, cellsize, origin, &region);

        // Increment the coordinate for next placement of the block.
        oldcoord.X = region.Left;
        oldcoord.Y = region.Top;
        region.Left = region.Right += GetRandom(-1, 1);
        region.Top = region.Bottom += GetRandom(-1, 1);

        // Correct placement (and beep) if about to go off the screen.
        if (region.Left < csbi.srWindow.Left)
            region.Left = region.Right = csbi.srWindow.Left + 1;
        else if (region.Right >= csbi.srWindow.Right)
            region.Left = region.Right = csbi.srWindow.Right - 2;
        else if (region.Top < csbi.srWindow.Top)
            region.Top = region.Bottom = csbi.srWindow.Top + 1;
        else if (region.Bottom >= csbi.srWindow.Bottom)
            region.Top = region.Bottom = csbi.srWindow.Bottom - 2;

        // If not at a screen border, continue, otherwise beep.
        else
            continue;
        Beep((ci.Char.AsciiChar - 'A') * 100, 175);
    }
    // _endthread given to terminate
    _endthread();
}
```

Drücken Sie zum Beenden der Beispielanwendung eine beliebige Taste.

## <a name="example"></a>Beispiel

Der folgende Beispielcode veranschaulicht, wie Sie das Threadhandle verwenden können, das von **_beginthreadex** mit der Synchronisierungs-API [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject)zurückgegeben wird. Der Hauptthread wartet auf das Beenden des zweiten Threads, bevor er fortsetzt. Wenn der zweite Thread **_endthreadex**aufruft, bewirkt er, dass sein Threadobjekt in den signalisierten Zustand übergeht. Damit kann der primäre Thread fortgesetzt werden. Dies kann nicht mit **_beginthread** und **_endthread**erfolgen, da **_endthread** **CloseHandle**aufruft, das das Threadobjekt zerstört, bevor es auf den signalisierten Zustand gesetzt werden kann.

```cpp
// crt_begthrdex.cpp
// compile with: /MT
#include <windows.h>
#include <stdio.h>
#include <process.h>

unsigned Counter;
unsigned __stdcall SecondThreadFunc( void* pArguments )
{
    printf( "In second thread...\n" );

    while ( Counter < 1000000 )
        Counter++;

    _endthreadex( 0 );
    return 0;
}

int main()
{
    HANDLE hThread;
    unsigned threadID;

    printf( "Creating second thread...\n" );

    // Create the second thread.
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc, NULL, 0, &threadID );

    // Wait until second thread terminates. If you comment out the line
    // below, Counter will not be correct because the thread has not
    // terminated, and Counter most likely has not been incremented to
    // 1000000 yet.
    WaitForSingleObject( hThread, INFINITE );
    printf( "Counter should be 1000000; it is-> %d\n", Counter );
    // Destroy the thread object.
    CloseHandle( hThread );
}
```

```Output
Creating second thread...
In second thread...
Counter should be 1000000; it is-> 1000000
```

## <a name="see-also"></a>Siehe auch

- [Prozess- und Umweltkontrolle](../../c-runtime-library/process-and-environment-control.md)
- [_endthread, _endthreadex](endthread-endthreadex.md)
- [Abbrechen](abort.md)
- [exit, _Exit, _exit](exit-exit-exit.md)
- [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)
