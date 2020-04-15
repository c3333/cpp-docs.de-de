---
title: _get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler
ms.date: 4/2/2020
api_name:
- _get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
- _o__get_invalid_parameter_handler
- _o__get_thread_local_invalid_parameter_handler
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
- _get_invalid_parameter_handler
- stdlib/_get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
- stdlib/_get_thread_local_invalid_parameter_handler
helpviewer_keywords:
- _get_thread_local_invalid_parameter_handler function
- _get_invalid_parameter_handler function
ms.assetid: a176da0e-38ca-4d99-92bb-b0e2b8072f53
ms.openlocfilehash: 2465852b7bcc0251f218c68df14ff33930ad2378
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345075"
---
# <a name="_get_invalid_parameter_handler-_get_thread_local_invalid_parameter_handler"></a>_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler

Ruft die Funktion auf, die aufzurufen ist, wenn CRT ein ungültiges Argument erkennt.

## <a name="syntax"></a>Syntax

```C
_invalid_parameter_handler _get_invalid_parameter_handler(void);
_invalid_parameter_handler _get_thread_local_invalid_parameter_handler(void);
```

## <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die derzeit festgelegte Funktion für ungültige Parameterhandler oder ein NULL-Zeiger, wenn keine festgelegt wurde.

## <a name="remarks"></a>Bemerkungen

Die **_get_invalid_parameter_handler-Funktion** ruft den aktuell festgelegten globalen ungültigen Parameterhandler ab. Sie gibt einen NULL-Zeiger zurück, wenn kein globaler Handler für ungültige Parameter festgelegt wurde. Ebenso ruft die **_get_thread_local_invalid_parameter_handler** den aktuellen threadlokalen ungültigen Parameterhandler des Threads ab, auf dem er aufgerufen wird, oder einen Nullzeiger, wenn kein Handler festgelegt wurde. Informationen zum Festlegen von globalen und Thread-lokalen ungültigen Parameterhandlern finden Sie unter [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

Der zurückgegebene Funktionszeiger des ungültigen Parameterhandlers hat den folgenden Typ:

```C
typedef void (__cdecl* _invalid_parameter_handler)(
    wchar_t const*,
    wchar_t const*,
    wchar_t const*,
    unsigned int,
    uintptr_t
    );
```

Mehr Informationen über ungültige Parameterhandler finden sie unter dem Prototyp in [set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_get_invalid_parameter_handler** **_get_thread_local_invalid_parameter_handler** ,|C: \<stdlib.h><br /><br /> C++: \<cstdlib> oder \<stdlib.h>|

Die **_get_invalid_parameter_handler-** und **_get_thread_local_invalid_parameter_handler-Funktionen** sind Microsoft-spezifisch. Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Sicherheitsverstärkte Versionen von CRT-Funktionen](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
