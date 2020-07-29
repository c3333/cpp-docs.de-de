---
title: _set_se_translator
ms.date: 02/21/2018
api_name:
- _set_se_translator
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_se_translator
- set_se_translator
helpviewer_keywords:
- set_se_translator function
- exception handling, changing
- _set_se_translator function
ms.assetid: 280842bc-d72a-468b-a565-2d3db893ae0f
ms.openlocfilehash: f1c9446f9c3f0d637ea53d54584258959677b339
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232416"
---
# <a name="_set_se_translator"></a>_set_se_translator

Legen Sie eine Rückruffunktion pro Thread fest, um Win32-Ausnahmen (C-strukturierte Ausnahmen) in C++ typisierte Ausnahmen zu übersetzen.

## <a name="syntax"></a>Syntax

```cpp
_se_translator_function _set_se_translator(
    _se_translator_function seTransFunction
);
```

### <a name="parameters"></a>Parameter

*"stransfunction"*<br/>
Zeiger auf eine strukturierte C-Ausnahmeübersetzerfunktion, die Sie schreiben.

## <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf die vorherige Übersetzer Funktion zurück, die von **_set_se_translator**registriert wurde, sodass die vorherige Funktion später wieder hergestellt werden kann. Wenn keine vorherige Funktion festgelegt wurde, kann der Rückgabewert verwendet werden, um das Standardverhalten wiederherzustellen. Dieser Wert kann sein **`nullptr`** .

## <a name="remarks"></a>Bemerkungen

Die **_set_se_translator** -Funktion bietet eine Möglichkeit, Win32-Ausnahmen (C-strukturierte Ausnahmen) als C++-typisierte Ausnahmen zu verarbeiten. Damit jede c-Ausnahme von einem C++-Handler behandelt werden **`catch`** kann, definieren Sie zunächst eine Wrapper Klasse der c-Ausnahme, die verwendet oder von abgeleitet werden kann, um einen bestimmten Klassentyp einer C-Ausnahme zuzuordnen. Um diese Klasse zu verwenden, installieren Sie eine benutzerdefinierte C-Ausnahmeübersetzungsfunktion, die bei jedem Auslösen einer C-Ausnahme vom internen Mechanismus für die Ausnahmebehandlung aufgerufen wird. Innerhalb der Übersetzer Funktion können Sie eine beliebige typisierte Ausnahme auslösen, die von einem passenden C++-Handler abgefangen werden kann **`catch`** .

Sie müssen [/EHa](../../build/reference/eh-exception-handling-model.md) verwenden, wenn Sie **_set_se_translator**verwenden.

Um eine benutzerdefinierte Übersetzungsfunktion anzugeben, wenden Sie **_set_se_translator** mit dem Namen der Übersetzungsfunktion als Argument an. Die Übersetzer Funktion, die Sie schreiben, wird einmal für jeden Funktionsaufruf auf dem Stapel mit- **`try`** Blöcken aufgerufen. Es gibt keine standardmäßige Übersetzerfunktion.

Ihre Übersetzerfunktion sollte lediglich eine C++-typisierte Ausnahme auslösen. Wenn sich die Funktion nicht auf die Auslösung beschränkt (z.B. in eine Protokolldatei schreibt), verhält sich Ihr Programm möglicherweise nicht wie erwartet, da die Anzahl von Aufrufen der Übersetzerfunktion plattformabhängig ist.

In einer Multithreadumgebung werden die Übersetzerfunktionen für jeden Thread separat verwaltet. Jeder neue Thread muss eine eigene Übersetzerfunktion installieren. Daher ist jeder Thread für die eigene Übersetzungsbehandlung verantwortlich. **_set_se_translator** ist spezifisch für einen Thread. eine andere dll kann eine andere Übersetzungsfunktion installieren.

Die *Funktion* "", die Sie schreiben, muss eine systemeigene kompilierte Funktion sein (nicht mit/CLR kompiliert). Er muss eine ganze Zahl ohne Vorzeichen und einen Zeiger auf eine Win32- **_EXCEPTION_POINTERS** Struktur als Argumente annehmen. Die Argumente sind die Rückgabewerte von Aufrufen der Win32-API-Funktionen **GetExceptionCode** und **GetExceptionInformation** bzw.

```cpp
typedef void (__cdecl *_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );
```

Für **_set_se_translator**gibt es Auswirkungen beim dynamischen verknüpfen mit der CRT. eine andere dll im Prozess ruft möglicherweise **_set_se_translator** auf und ersetzt Ihren Handler durch einen eigenen.

Beachten Sie beim Verwenden von **_set_se_translator** aus verwaltetem Code (mit/CLR kompilierter Code) oder gemischtem System eigenem und verwaltetem Code. Alle verwalteten Ausnahmen, die in verwaltetem Code generiert wurden (z.B. beim Auslösen von `System::Exception`), werden nicht über die Übersetzerfunktion weitergeleitet. Ausnahmen, die in verwaltetem Code mithilfe der Win32-Funktion **RaiseException** ausgelöst werden oder durch eine System Ausnahme ausgelöst werden, wie eine Division durch 0 (null), werden durch den Konvertierer geleitet

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_set_se_translator**|\<eh.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

In diesem Beispiel werden die Aufrufe zum Festlegen eines strukturierten Ausnahme Übersetzer und zum Wiederherstellen der alten in einer RAII-Klasse () umschlossen `Scoped_SE_Translator` . Mit dieser Klasse können Sie einen Bereichs spezifischen Konvertierer als einzelne Deklaration einführen. Der klassendekonstruktor stellt den ursprünglichen Konvertierer wieder her, wenn die Steuerung den Bereich verlässt

```cpp
// crt_settrans.cpp
// compile with: cl /W4 /EHa crt_settrans.cpp
#include <stdio.h>
#include <windows.h>
#include <eh.h>
#include <exception>

class SE_Exception : public std::exception
{
private:
    const unsigned int nSE;
public:
    SE_Exception() noexcept : SE_Exception{ 0 } {}
    SE_Exception( unsigned int n ) noexcept : nSE{ n } {}
    unsigned int getSeNumber() const noexcept { return nSE; }
};

class Scoped_SE_Translator
{
private:
    const _se_translator_function old_SE_translator;
public:
    Scoped_SE_Translator( _se_translator_function new_SE_translator ) noexcept
        : old_SE_translator{ _set_se_translator( new_SE_translator ) } {}
    ~Scoped_SE_Translator() noexcept { _set_se_translator( old_SE_translator ); }
};

void SEFunc()
{
    __try
    {
        printf( "In __try, about to force exception\n" );
        int x = 5;
        int y = 0;
        int *p = &y;
        *p = x / *p;
    }
    __finally
    {
        printf( "In __finally\n" );
    }
}

void trans_func( unsigned int u, EXCEPTION_POINTERS* )
{
    throw SE_Exception( u );
}

int main()
{
    Scoped_SE_Translator scoped_se_translator{ trans_func };
    try
    {
        SEFunc();
    }
    catch( const SE_Exception& e )
    {
        printf( "Caught a __try exception, error %8.8x.\n", e.getSeNumber() );
    }
}
```

```Output
In __try, about to force exception
In __finally
Caught a __try exception, error c0000094.
```

## <a name="example"></a>Beispiel

Obwohl die von **_set_se_translator** bereitgestellte Funktionalität in verwaltetem Code nicht verfügbar ist, ist es möglich, diese Zuordnung in nativem Code zu verwenden, auch wenn sich dieser systemeigene Code in einer Kompilierung unter dem Schalter **/CLR** befindet, solange der systemeigene Code mithilfe von angegeben wird `#pragma unmanaged` . Wenn eine strukturierte Ausnahme in verwaltetem Code ausgelöst wird, der zugeordnet werden soll, muss der Code, der die Ausnahme generiert und behandelt, als markiert werden `#pragma unmanaged` . Der folgende Code veranschaulicht eine mögliche Verwendung. Weitere Informationen finden Sie unter [Pragma-Direktiven und das __Pragma-Schlüsselwort](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

```cpp
// crt_set_se_translator_clr.cpp
// compile with: cl /W4 /clr crt_set_se_translator_clr.cpp
#include <windows.h>
#include <eh.h>
#include <stdio.h>
#include <exception>

int thrower_func( int i ) {
   int y = 0;
   int *p = &y;
   *p = i / *p;
   return 0;
}

class SE_Exception : public std::exception
{
private:
    const unsigned int nSE;
public:
    SE_Exception() noexcept : SE_Exception{ 0 } {}
    SE_Exception( unsigned int n ) noexcept : nSE{ n } {}
    unsigned int getSeNumber() const noexcept { return nSE; }
};

class Scoped_SE_Translator
{
private:
    const _se_translator_function old_SE_translator;
public:
    Scoped_SE_Translator( _se_translator_function new_SE_translator ) noexcept
        : old_SE_translator{ _set_se_translator( new_SE_translator ) } {}
    ~Scoped_SE_Translator() noexcept { _set_se_translator( old_SE_translator ); }
};

#pragma unmanaged
void my_trans_func( unsigned int u, PEXCEPTION_POINTERS )
{
    throw SE_Exception( u );
}

void DoTest()
{
    try
    {
        thrower_func( 10 );
    }
    catch( const SE_Exception& e )
    {
        printf( "Caught SE_Exception, error %8.8x\n", e.getSeNumber() );
    }
    catch(...)
    {
        printf( "Caught unexpected SEH exception.\n" );
    }
}
#pragma managed

int main() {
    Scoped_SE_Translator scoped_se_translator{ my_trans_func };

    DoTest();
}
```

```Output
Caught SE_Exception, error c0000094
```

## <a name="see-also"></a>Weitere Informationen

[Ausnahme Behandlungs Routinen](../../c-runtime-library/exception-handling-routines.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[aufzu](terminate-crt.md)<br/>
[te](unexpected-crt.md)<br/>
