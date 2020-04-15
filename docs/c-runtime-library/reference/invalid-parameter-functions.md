---
title: _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson
ms.date: 4/2/2020
api_name:
- _invalid_parameter
- _invalid_parameter_noinfo
- _invalid_parameter_noinfo_noreturn
- _invoke_watson
- _o__invalid_parameter_noinfo
- _o__invalid_parameter_noinfo_noreturn
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CORECRT/_invalid_parameter
- _invalid_parameter
- CORECRT/_invalid_parameter_noinfo
- _invalid_parameter_noinfo
- CORECRT/_invalid_parameter_noinfo_noreturn
- _invalid_parameter_noinfo_noreturn
- CORECRT/_invoke_watson
- _invoke_watson
ms.assetid: a4d6f1fd-ce56-4783-8719-927151a7a814
ms.openlocfilehash: 0f0a3ea3e1f2e43d53650b4017905c696269ce20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343943"
---
# <a name="_invalid_parameter-_invalid_parameter_noinfo-_invalid_parameter_noinfo_noreturn-_invoke_watson"></a>_invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson

Diese Funktionen werden von der C-Laufzeitbibliothek verwendet, um ungültige Parameter zu behandeln, die an CRT-Bibliotheksfunktionen übergeben werden. Ihr Code verwendet diese Funktionen möglicherweise auch zur Unterstützung der Standard- oder anpassbaren Behandlung der ungültigen Parameter.

## <a name="syntax"></a>Syntax

```C
extern "C" void __cdecl
_invalid_parameter(
    wchar_t const* const expression,
    wchar_t const* const function_name,
    wchar_t const* const file_name,
    unsigned int   const line_number,
    uintptr_t      const reserved);

extern "C" void __cdecl
_invalid_parameter_noinfo(void);

extern "C" __declspec(noreturn) void __cdecl
_invalid_parameter_noinfo_noreturn(void);

extern "C" __declspec(noreturn) void __cdecl
_invoke_watson(
    wchar_t const* const expression,
    wchar_t const* const function_name,
    wchar_t const* const file_name,
    unsigned int   const line_number,
    uintptr_t      const reserved);
```

## <a name="parameters"></a>Parameter

*Ausdruck*<br/>
Eine Zeichenfolge mit dem Quellcode-Parameterausdruck, der nicht gültig ist.

*function_name*<br/>
Der Name der Funktion, die den Handler aufgerufen hat.

*File_name*<br/>
Die Quellcodedatei, in der der Handler aufgerufen wurde.

*line_number*<br/>
Die Zeilennummer im Quellcode, in der der Handler aufgerufen wurde.

*Reserviert*<br/>
Nicht verwendet.

## <a name="return-value"></a>Rückgabewert

Die Funktionen geben keinen Wert zurück. Die **Funktionen _invalid_parameter_noinfo_noreturn** und **_invoke_watson** kehren nicht an den Aufrufer zurück, und in einigen Fällen werden **_invalid_parameter** und **_invalid_parameter_noinfo** möglicherweise nicht an den Aufrufer zurückgegeben.

## <a name="remarks"></a>Bemerkungen

Wenn Funktionen der C-Laufzeitbibliothek ungültige Parameter übergeben, rufen die Bibliotheksfunktionen einen *Handler für ungültige Parameter* auf, eine Funktion, die möglicherweise vom Programmierer angegeben wird, um mehrere Aufgaben auszuführen. Es kann dem Benutzer möglicherweise das Problem melden, in ein Protokoll schreiben, einen Debugger anhalten, das Programm beenden oder gar nichts machen. Wenn vom Programmierer keine Funktion angegeben wird, wird ein Standardhandler **_invoke_watson**aufgerufen.

Wenn ein ungültiger Parameter im Debugcode identifiziert wird, rufen CRT-Bibliotheksfunktionen standardmäßig die Funktion **auf, die _invalid_parameter** mit ausführlichen Parametern. Im Nicht-Debugcode wird die **_invalid_parameter_noinfo-Funktion** aufgerufen, die die **_invalid_parameter** Funktion mit leeren Parametern aufruft. Wenn die Nicht-Debug-CRT-Bibliotheksfunktion eine Programmbeendigung erfordert, wird die **_invalid_parameter_noinfo_noreturn-Funktion** aufgerufen, die die **_invalid_parameter-Funktion** mit leeren Parametern aufruft, gefolgt von einem Aufruf der **_invoke_watson-Funktion,** um die Programmbeendigung zu erzwingen.

Die **_invalid_parameter-Funktion** überprüft, ob ein benutzerdefinierter ungültiger Parameterhandler festgelegt wurde, und ruft ihn, wenn ja, auf. Beispielsweise wird die Funktion zurückgegebene, wenn ein benutzerdefinierter lokaler Threadhandler durch einen Aufruf von [set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) im aktuellen Thread festgelegt wurde. Andernfalls wird sie aufgerufen, wenn ein benutzerdefinierter globaler ungültiger Parametertyphandler durch einen Aufruf von [set_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) festgelegt wurde; danach springt die Funktion zurück. Andernfalls wird der Standardhandler **_invoke_watson** aufgerufen. Das Standardverhalten von **_invoke_watson** besteht darin, das Programm zu beenden. Benutzerdefinierte Handler werden möglicherweise beendet oder zurückgegeben. Es wird empfohlen, dass benutzerdefinierte Handler das Programm beenden, es sei denn, die Wiederherstellung ist sicher.

Wenn der Standardhandler **_invoke_watson** aufgerufen wird, wenn der Prozessor einen [__fastfail-Vorgang](../../intrinsics/fastfail.md) unterstützt, wird er mit einem Parameter von **FAST_FAIL_INVALID_ARG** aufgerufen, und der Prozess wird beendet. Andernfalls wird eine Fast-Fail-Ausnahme ausgelöst, die durch einen angefügten Debugger abgefangen wird. Wenn der Prozess fortgesetzt werden darf, wird er durch einen Aufruf der Windows **TerminateProcess-Funktion** unter Verwendung des Ausnahmecodestatus **STATUS_INVALID_CRUNTIME_PARAMETER**beendet.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|------------------|
|**_invalid_parameter**, **_invalid_parameter_noinfo**, **_invalid_parameter_noinfo_noreturn**, **_invoke_watson**|\<corecrt.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Parameterüberprüfung](../../c-runtime-library/parameter-validation.md)<br/>
