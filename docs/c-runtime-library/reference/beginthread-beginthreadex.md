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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 5060c4b34005c1cc066e002d20ca70cbfea0fbef
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684819"
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
Startadresse einer Routine, die die Ausführung eines neuen Threads beginnt. Bei **_beginthread**ist die Aufruf Konvention entweder [__cdecl](../../cpp/cdecl.md) (bei nativem Code) oder [__clrcall](../../cpp/clrcall.md) (für verwalteten Code). bei **_beginthreadex**ist es entweder [__stdcall](../../cpp/stdcall.md) (bei nativem Code) oder [__clrcall](../../cpp/clrcall.md) (für verwalteten Code).

*stack_size*<br/>
Stapelgröße für einen neuen Thread oder 0.

*Arglist*<br/>
Argument Liste, die an einen neuen Thread übermittelt werden soll, oder **null**.

*Security*<br/>
Zeiger auf eine [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) -Struktur, die bestimmt, ob das zurückgegebene Handle von untergeordneten Prozessen geerbt werden kann. Wenn *Security* die Sicherheit **null**ist, kann das Handle nicht geerbt werden. Muss für Windows 95-Anwendungen **null** sein.

*initflag*<br/>
Flags, die den anfänglichen Zustand eines neuen Threads steuern. Legen Sie *initflag* auf 0 fest, um sofort auszuführen, oder auf **CREATE_SUSPENDED** , um den Thread in einem angehaltenen Zustand zu erstellen. Verwenden Sie [ResumeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-resumethread) , um den Thread auszuführen. Legen Sie *initflag* auf **STACK_SIZE_PARAM_IS_A_RESERVATION** Flag fest, um *STACK_SIZE* als anfängliche Reservierungs Größe des Stapels in Byte zu verwenden. Wenn dieses Flag nicht angegeben ist, gibt *STACK_SIZE* die Commitgröße an.

*thrdaddr*<br/>
Zeigt auf eine 32-Bit-Variable, die den Threadbezeichner empfängt. Wenn er **null**ist, wird er nicht verwendet.

## <a name="return-value"></a>Rückgabewert

Bei Erfolg gibt jede dieser Funktionen ein Handle für den neu erstellten Thread zurück. Wenn der neu erstellte Thread allerdings zu schnell beendet wird, gibt **_beginthread** möglicherweise kein gültiges Handle zurück. (Weitere Informationen finden Sie im Abschnitt "Hinweise".) Bei einem Fehler gibt **_beginthread** den Wert-1L zurück, und **errno** wird auf **eagain** festgelegt, wenn zu viele Threads vorhanden sind, auf **EINVAL** , wenn das Argument ungültig oder die Stapelgröße falsch ist, oder auf **EACCES** , wenn nicht genügend Ressourcen (z. b. Arbeitsspeicher) vorhanden sind. Bei einem Fehler gibt **_beginthreadex** 0 zurück, und **errno** und **_doserrno** werden festgelegt.

Wenn *start_address* **null**ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, legen diese Funktionen **errno** auf **EINVAL** fest und geben-1 zurück.

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Weitere Informationen zu **uintptr_t**finden Sie unter [Standard Typen](../../c-runtime-library/standard-types.md).

## <a name="remarks"></a>Bemerkungen

Die **_beginthread** -Funktion erstellt einen Thread, der die Ausführung einer Routine bei *start_address*beginnt. Die Routine bei *start_address* muss die **`__cdecl`** -Aufruf Konvention (für systemeigenen Code) oder **__clrcall** (für verwalteten Code) verwenden und sollte keinen Rückgabewert haben. Wenn der Thread aus dieser Routine zurückgegeben wird, wird er automatisch beendet. Weitere Informationen zu Threads finden Sie unter [Multithreadingunterstützung für älteren Code (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

**_beginthreadex** ähnelt [der Win32-](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) API-API-API enger als **_beginthread** . **_beginthreadex** unterscheidet sich wie folgt von **_beginthread** :

- **_beginthreadex** hat drei zusätzliche Parameter: *initflag*, *Security*und **threadaddr**. Der neue Thread kann in einem angehaltenen Zustand mit angegebener Sicherheit erstellt werden, und der Zugriff darauf ist mithilfe von " *thrdaddr*" möglich. Dies ist der Thread Bezeichner.

- Die an **_beginthreadex** übergebenen- *start_address* Routine muss die- **`__stdcall`** Aufruf Konvention (für systemeigenen Code) oder **__clrcall** (für verwalteten Code) verwenden und einen Thread Beendigungs Code zurückgeben.

- **_beginthreadex** gibt bei einem Fehler 0 (null) anstelle von-1L zurück.

- Ein Thread, der mit **_beginthreadex** erstellt wird, wird durch einen- [aufruf_endthreadex](endthread-endthreadex.md)beendet.

Die **_beginthreadex** -Funktion ermöglicht Ihnen mehr Kontrolle darüber, wie der Thread erstellt wird, als **_beginthread** . Die **_endthreadex** -Funktion ist auch flexibler. Beispielsweise können Sie mit **_beginthreadex**Sicherheitsinformationen verwenden, den Anfangszustand des Threads festlegen (wird ausgeführt oder angehalten) und den Thread Bezeichner des neu erstellten Threads erhalten. Sie können auch das Thread Handle verwenden, das von **_beginthreadex** mit den Synchronisierungs-APIs zurückgegeben wird, was Sie mit **_beginthread**nicht tun können.

Es ist sicherer, **_beginthreadex** als **_beginthread**zu verwenden. Wenn der Thread, der von **_beginthread** generiert wird, schnell beendet wird, ist das Handle, das an den Aufrufer von **_beginthread** zurückgegeben wurde, möglicherweise ungültig oder verweist auf einen anderen Thread. Allerdings muss das Handle, das von **_beginthreadex** zurückgegeben wird, vom Aufrufer von **_beginthreadex**geschlossen werden, sodass sichergestellt ist, dass es ein gültiges Handle ist, wenn **_beginthreadex** keinen Fehler zurückgegeben hat.

Sie können [_endthread](endthread-endthreadex.md) oder explizit **_endthreadex** zum Beenden eines Threads abrufen. **_endthread** oder **_endthreadex** wird jedoch automatisch aufgerufen, wenn der Thread aus der Routine zurückgegeben wird, die als Parameter übergeben wird. Wenn Sie einen Thread mit einem **_endthread** -oder **_endthreadex** -Rückruf beenden, wird sichergestellt, dass die für den Thread zugeordneten Ressourcen ordnungsgemäß wieder hergestellt werden.

**_endthread** schließt das Thread Handle automatisch, während **_endthreadex** nicht. Wenn Sie **_beginthread** und **_endthread**verwenden, schließen Sie das Thread handle daher nicht explizit, indem Sie die Win32- [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) -API aufrufen. Dieses Verhalten unterscheidet sich von dem der [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) -Win32-API.

> [!NOTE]
> Rufen Sie für eine mit "LIBCMT. lib" verknüpfte ausführbare Datei die **ExitThread** -Win32-API nicht auf, sodass Sie nicht verhindern, dass das Laufzeitsystem zugeordnete Ressourcen freigibt. **_endthread** und **_endthreadex** zugeordnete Thread Ressourcen freizugeben und dann **ExitThread**aufzurufen.

Das Betriebssystem verarbeitet die Zuordnung des Stapels, wenn entweder **_beginthread** oder **_beginthreadex** aufgerufen wird. Sie müssen die Adresse des Thread Stapels nicht an eine dieser Funktionen übergeben. Außerdem kann das *STACK_SIZE* -Argument gleich 0 sein. in diesem Fall verwendet das Betriebssystem denselben Wert wie der Stapel, der für den Haupt Thread angegeben wird.

*Arglist* ist ein Parameter, der an den neu erstellten Thread übergeben werden soll. In der Regel ist das die Adresse eines Datenelements, z. B. einer Zeichenfolge. *Arglist* kann **null** sein, wenn es nicht erforderlich ist, aber **_beginthread** und **_beginthreadex** muss ein Wert angegeben werden, der an den neuen Thread übergeben werden kann. Alle Threads werden beendet, wenn ein Thread [Abbruch](abort.md), **Exit**, **_exit**oder **ExitProcess**aufruft.

Das Gebiets Schema des neuen Threads wird initialisiert, indem die prozessspezifischen globalen aktuellen Gebiets Schema Informationen verwendet werden. Wenn das Thread spezifische Gebiets Schema durch einen Aufruf von [_configthreadlocale](configthreadlocale.md) (entweder global oder nur für neue Threads) aktiviert wird, kann der Thread sein Gebiets Schema unabhängig von anderen Threads ändern, indem **setlocale** oder **_wsetlocale**aufgerufen wird. Threads, bei denen das Thread spezifische Gebiets Schema Flag nicht festgelegt ist, können sich auf die Gebiets Schema Informationen in allen anderen Threads auswirken, für die außerdem nicht das Thread spezifische Gebiets Schema festgelegt ist, sowie alle neu erstellten Threads. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Für **/CLR** -Code verfügen **_beginthread** und **_beginthreadex** jeweils über zwei über Ladungen. Der andere übernimmt einen systemeigenen Aufruf Konvention-Funktionszeiger, der andere einen **__clrcall** Funktionszeiger. Die erste Überladung ist nicht anwendungsdomänensicher und wird es niemals sein. Wenn Sie **/CLR** -Code schreiben, müssen Sie sicherstellen, dass der neue Thread die richtige Anwendungsdomäne eingibt, bevor er auf verwaltete Ressourcen zugreift. Hierzu können Sie beispielsweise die [call_in_domain-Funktion](../../dotnet/call-in-appdomain-function.md) verwenden. Die zweite Überladung ist Anwendungs Domänen sicher. der neu erstellte Thread endet immer in der Anwendungsdomäne des Aufrufers von **_beginthread** oder **_beginthreadex**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_beginthread**|\<process.h>|
|**_beginthreadex**|\<process.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Nur Multithread-Versionen von [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md) .

Um **_beginthread** oder **_beginthreadex**verwenden zu können, muss die Anwendung mit einer der C-Laufzeitbibliotheken von Multithread verknüpft werden.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel werden **_beginthread** und **_endthread**verwendet.

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

Der folgende Beispielcode veranschaulicht, wie Sie das Thread Handle verwenden können, das von **_beginthreadex** mit der Synchronisierungs-API [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject)zurückgegeben wird. Der Hauptthread wartet auf das Beenden des zweiten Threads, bevor er fortsetzt. Wenn der zweite Thread **_endthreadex**aufruft, bewirkt dies, dass das Thread Objekt in den signalisierten Zustand wechselt. Damit kann der primäre Thread fortgesetzt werden. Dies kann nicht mit **_beginthread** und **_endthread**erfolgen, da **_endthread** **CloseHandle**aufruft, das das Thread Objekt zerstört, bevor es auf den signalisierten Zustand festgelegt werden kann.

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

## <a name="see-also"></a>Weitere Informationen

- [Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)
- [_endthread, _endthreadex](endthread-endthreadex.md)
- [abort](abort.md)
- [exit, _Exit, _exit](exit-exit-exit.md)
- [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)
