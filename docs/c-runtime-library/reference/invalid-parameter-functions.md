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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 7138e9cb7381e4d40911054e1473536b6e639e2d
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919826"
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

*expression*<br/>
Eine Zeichenfolge mit dem Quellcode-Parameterausdruck, der nicht gültig ist.

*function_name*<br/>
Der Name der Funktion, die den Handler aufgerufen hat.

*file_name*<br/>
Die Quellcodedatei, in der der Handler aufgerufen wurde.

*line_number*<br/>
Die Zeilennummer im Quellcode, in der der Handler aufgerufen wurde.

*bleiben*<br/>
Nicht verwendet.

## <a name="return-value"></a>Rückgabewert

Die Funktionen geben keinen Wert zurück. Die Funktionen **_invalid_parameter_noinfo_noreturn** und **_invoke_watson** werden nicht an den Aufrufer zurückgegeben, und in einigen Fällen werden **_invalid_parameter** und **_invalid_parameter_noinfo** möglicherweise nicht an den Aufrufer zurückgegeben.

## <a name="remarks"></a>Hinweise

Wenn Funktionen der C-Laufzeitbibliothek ungültige Parameter übergeben, rufen die Bibliotheksfunktionen einen *Handler für ungültige Parameter* auf, eine Funktion, die möglicherweise vom Programmierer angegeben wird, um mehrere Aufgaben auszuführen. Es kann dem Benutzer möglicherweise das Problem melden, in ein Protokoll schreiben, einen Debugger anhalten, das Programm beenden oder gar nichts machen. Wenn vom Programmierer keine Funktion angegeben wird, wird ein Standard Handler ( **_invoke_watson**) aufgerufen.

Wenn ein ungültiger Parameter im Debugcode identifiziert wird, wird die Funktion von CRT-Bibliotheksfunktionen standardmäßig **_invalid_parameter** mithilfe ausführlicher Parameter aufgerufen. In nicht-Debugcode wird die **_invalid_parameter_noinfo** -Funktion aufgerufen, die die **_invalid_parameter** -Funktion mithilfe von leeren Parametern aufruft. Wenn die nicht Debuggen-CRT-Bibliotheksfunktion eine Programm Beendigung erfordert, wird die **_invalid_parameter_noinfo_noreturn** -Funktion aufgerufen, die die **_invalid_parameter** -Funktion mithilfe von leeren Parametern aufruft, gefolgt von einem Aufruf der **_invoke_watson** -Funktion, um die Beendigung des Programms zu erzwingen.

Die **_invalid_parameter** -Funktion überprüft, ob ein benutzerdefinierter Handler für ungültige Parameter festgelegt wurde, und ruft, wenn ja, ihn auf. Beispielsweise wird die Funktion zurückgegebene, wenn ein benutzerdefinierter lokaler Threadhandler durch einen Aufruf von [set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) im aktuellen Thread festgelegt wurde. Andernfalls wird sie aufgerufen, wenn ein benutzerdefinierter globaler ungültiger Parametertyphandler durch einen Aufruf von [set_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) festgelegt wurde; danach springt die Funktion zurück. Andernfalls wird der Standard Handler **_invoke_watson** aufgerufen. Das Standardverhalten von **_invoke_watson** besteht darin, das Programm zu beenden. Benutzerdefinierte Handler werden möglicherweise beendet oder zurückgegeben. Es wird empfohlen, dass benutzerdefinierte Handler das Programm beenden, es sei denn, die Wiederherstellung ist sicher.

Wenn der Standard Handler **_invoke_watson** aufgerufen wird und der Prozessor einen [__fastfail](../../intrinsics/fastfail.md) -Vorgang unterstützt, wird er mit einem Parameter von **FAST_FAIL_INVALID_ARG** aufgerufen, und der Prozess wird beendet. Andernfalls wird eine Fast-Fail-Ausnahme ausgelöst, die durch einen angefügten Debugger abgefangen wird. Wenn der Prozess fortgesetzt werden kann, wird er durch einen Aufrufen der Windows-Funktion **TerminateProcess** mit dem Ausnahme Code Status **STATUS_INVALID_CRUNTIME_PARAMETER**beendet.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|------------------|
|**_invalid_parameter**, **_invalid_parameter_noinfo** **_invalid_parameter_noinfo_noreturn**, **_invoke_watson**|\<corecrt.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Parameter Validierung](../../c-runtime-library/parameter-validation.md)<br/>
