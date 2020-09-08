---
title: _set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler
description: API-Referenz für _set_invalid_parameter_handler und _set_thread_local_invalid_parameter_handler; , die eine Funktion festlegen, die aufgerufen werden soll, wenn die CRT ein ungültiges Argument erkennt.
ms.date: 4/2/2020
api_name:
- _set_invalid_parameter_handler
- _set_thread_local_invalid_parameter_handler
- _o__set_invalid_parameter_handler
- _o__set_thread_local_invalid_parameter_handler
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
- set_invalid_parameter_handler
- _set_invalid_parameter_handler
- _set_thread_local_invalid_parameter_handler
helpviewer_keywords:
- invalid parameter handler
- set_invalid_parameter_handler function
- _set_invalid_parameter_handler function
- _set_thread_local_invalid_parameter_handler function
ms.assetid: c0e67934-1a41-4016-ad8e-972828f3ac11
ms.openlocfilehash: a965bd71af18a57c31d3cfef927be02005c407c0
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555617"
---
# <a name="_set_invalid_parameter_handler-_set_thread_local_invalid_parameter_handler"></a>_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler

Legt eine Funktion fest, die aufzurufen ist, wenn die CRT ein ungültiges Argument erkennt.

## <a name="syntax"></a>Syntax

```C
_invalid_parameter_handler _set_invalid_parameter_handler(
   _invalid_parameter_handler pNew
);
_invalid_parameter_handler _set_thread_local_invalid_parameter_handler(
   _invalid_parameter_handler pNew
);
```

### <a name="parameters"></a>Parameter

*Pnew*<br/>
Der Funktionszeiger auf den neuen Handler für ungültige Parameter.

## <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Handler für ungültigen Parameter vor dem Aufruf.

## <a name="remarks"></a>Hinweise

Viele C-Laufzeitfunktionen überprüfen die Gültigkeit der an sie übergebenen Argumente. Wenn ein ungültiges Argument ausgegeben wird, kann die Funktion die **errno** -Fehlernummer festlegen oder einen Fehlercode zurückgeben. In solchen Fällen wird der Handler für ungültige Parameter ebenfalls aufgerufen. Die C-Laufzeit stellt einen globalen Standardhandler für ungültige Parameter bereit, der das Programm beendet und eine Laufzeitfehlermeldung anzeigt. Sie können den **_set_invalid_parameter_handler** verwenden, um eine eigene Funktion als einen globalen ungültigen Parameter Handler festzulegen. Die C-Laufzeitbibliothek unterstützt auch einen threadlokalen Handler für ungültige Parameter. Wenn ein Thread lokaler Parameter Handler mithilfe von **_set_thread_local_invalid_parameter_handler**in einem Thread festgelegt wird, verwenden die C-Lauf Zeitfunktionen, die vom Thread aufgerufen werden, diesen Handler anstelle des globalen Handlers. Es kann jederzeit immer nur eine Funktion als globaler Handler für ungültige Argumente angegeben werden. Nur eine Funktion kann als threadlokaler Handler für ungültige Argumente pro Thread angegeben werden, aber verschiedene Threads können über unterschiedliche threadlokale Handler verfügen. Dadurch können Sie den in einem Teil des Codes verwendeten Handler ohne Auswirkung auf das Verhalten anderer Threads zu ändern.

Wenn die Laufzeit die Funktion für ungültige Parameter aufruft, bedeutet dies normalerweise, dass ein nicht behebbarer Fehler aufgetreten ist. Die Funktion Handler für ungültige Parameter sollte alle Daten speichern, bei denen dies möglich ist, und dann abbrechen. Es sollte nur dann die Steuerung an die Main-Funktion zurückgegeben werden, wenn Sie sicher sind, dass der Fehler wiederherstellbar ist.

Die Handler-Funktion für ungültige Parameter muss folgenden Prototyp besitzen:

```C
void _invalid_parameter(
   const wchar_t * expression,
   const wchar_t * function,
   const wchar_t * file,
   unsigned int line,
   uintptr_t pReserved
);
```

Das *Expression* -Argument ist eine Breite Zeichen folgen Darstellung des Argument Ausdrucks, der den Fehler ausgelöst hat. Das *Function* -Argument ist der Name der CRT-Funktion, die das ungültige Argument empfangen hat. Das *Datei* Argument ist der Name der CRT-Quelldatei, die die Funktion enthält. Das *Zeilen* Argument ist die Zeilennummer in dieser Datei. Das letzte Argument ist reserviert. Alle Parameter haben den Wert **null** , es sei denn, es wird eine Debugversion der CRT-Bibliothek verwendet.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_set_invalid_parameter_handler** **_set_thread_local_invalid_parameter_handler**|Scher \<stdlib.h><br /><br /> C++: \<cstdlib> oder \<stdlib.h>|

Die Funktionen **_set_invalid_parameter_handler** und **_set_thread_local_invalid_parameter_handler** sind Microsoft-spezifisch. Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein Fehlerhandler für ungültige Parameter verwendet, um die Funktion zu auszugeben, die den ungültigen Parameter empfangen hat, sowie deren Dateiname und die Zeile in den CRT-Quellen. Wird die CRT-Debugbibliothek verwendet, dann lösen Fehler durch ungültige Parameter auch eine Assertion aus, die in diesem Beispiel mit [_CrtSetReportMode](crtsetreportmode.md) deaktiviert ist.

```C
// crt_set_invalid_parameter_handler.c
// compile with: /Zi /MTd
#include <stdio.h>
#include <stdlib.h>
#include <crtdbg.h>  // For _CrtSetReportMode

void myInvalidParameterHandler(const wchar_t* expression,
   const wchar_t* function,
   const wchar_t* file,
   unsigned int line,
   uintptr_t pReserved)
{
   wprintf(L"Invalid parameter detected in function %s."
            L" File: %s Line: %d\n", function, file, line);
   wprintf(L"Expression: %s\n", expression);
   abort();
}

int main( )
{
   char* formatString;

   _invalid_parameter_handler oldHandler, newHandler;
   newHandler = myInvalidParameterHandler;
   oldHandler = _set_invalid_parameter_handler(newHandler);

   // Disable the message box for assertions.
   _CrtSetReportMode(_CRT_ASSERT, 0);

   // Call printf_s with invalid parameters.

   formatString = NULL;
   printf(formatString);
}
```

```Output
Invalid parameter detected in function common_vfprintf. File: minkernel\crts\ucrt\src\appcrt\stdio\output.cpp Line: 32
Expression: format != nullptr
```

## <a name="see-also"></a>Weitere Informationen

[_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[Erweiterte Versionen der CRT-Funktionen mit erweiterter Sicherheit](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
[errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
