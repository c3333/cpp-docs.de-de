---
title: _set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 0637937d4596d28875c40efec62f79a32f533dcf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337679"
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

*pNeu*<br/>
Der Funktionszeiger auf den neuen Handler für ungültige Parameter.

## <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Handler für ungültigen Parameter vor dem Aufruf.

## <a name="remarks"></a>Bemerkungen

Viele C-Laufzeitfunktionen überprüfen die Gültigkeit der an sie übergebenen Argumente. Wenn ein ungültiges Argument übergeben wird, kann die Funktion die **errno-Fehlernummer** festlegen oder einen Fehlercode zurückgeben. In solchen Fällen wird der Handler für ungültige Parameter ebenfalls aufgerufen. Die C-Laufzeit stellt einen globalen Standardhandler für ungültige Parameter bereit, der das Programm beendet und eine Laufzeitfehlermeldung anzeigt. Sie können die **_set_invalid_parameter_handler** verwenden, um Ihre eigene Funktion als globalen ungültigen Parameterhandler festzulegen. Die C-Laufzeitbibliothek unterstützt auch einen threadlokalen Handler für ungültige Parameter. Wenn ein threadlokaler Parameterhandler in einem Thread mithilfe **von _set_thread_local_invalid_parameter_handler**festgelegt wird, verwenden die C-Laufzeitfunktionen, die vom Thread aufgerufen werden, diesen Handler anstelle des globalen Handlers. Es kann jederzeit immer nur eine Funktion als globaler Handler für ungültige Argumente angegeben werden. Nur eine Funktion kann als threadlokaler Handler für ungültige Argumente pro Thread angegeben werden, aber verschiedene Threads können über unterschiedliche threadlokale Handler verfügen. Dadurch können Sie den in einem Teil des Codes verwendeten Handler ohne Auswirkung auf das Verhalten anderer Threads zu ändern.

Wenn die Laufzeit die Funktion für ungültige Parameter aufruft, bedeutet dies normalerweise, dass ein nicht behebbarer Fehler aufgetreten ist. Die Funktion Handler für ungültige Parameter sollte alle Daten speichern, bei denen dies möglich ist, und dann abbrechen. Sie sollte die Steuerung nur dann an die Funktion "main" zurückgeben, wenn Sie sicher sind, dass der Fehler behebbar ist.

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

Das *Ausdrucksargument* ist eine weite Zeichenfolgendarstellung des Argumentausdrucks, der den Fehler ausgelöst hat. Das *Funktionsargument* ist der Name der CRT-Funktion, die das ungültige Argument empfangen hat. Das *Dateiargument* ist der Name der CRT-Quelldatei, die die Funktion enthält. Das *Zeilenargument* ist die Zeilennummer in dieser Datei. Das letzte Argument ist reserviert. Die Parameter haben alle den Wert **NULL,** es sei denn, es wird eine Debugversion der CRT-Bibliothek verwendet.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_set_invalid_parameter_handler**, **_set_thread_local_invalid_parameter_handler**|C: \<stdlib.h><br /><br /> C++: \<cstdlib> oder \<stdlib.h>|

Die **_set_invalid_parameter_handler-** und **_set_thread_local_invalid_parameter_handler-Funktionen** sind Microsoft-spezifisch. Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Siehe auch

[_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[Sicherheitsverstärkte Versionen von CRT-Funktionen](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
[errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
