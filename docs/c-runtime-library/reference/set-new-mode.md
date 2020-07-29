---
title: _set_new_mode
ms.date: 4/2/2020
api_name:
- _set_new_mode
- _o__set_new_mode
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_new_mode
- _set_new_mode
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
ms.openlocfilehash: aa21854f6a8c4b58a510b16e824449a53b91f329
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218532"
---
# <a name="_set_new_mode"></a>_set_new_mode

Legt einen neuen handlermodus für **malloc**fest.

## <a name="syntax"></a>Syntax

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>Parameter

*"nwhandlermode"*<br/>
Neuer handlermodus für **malloc**; der gültige Wert ist 0 oder 1.

## <a name="return-value"></a>Rückgabewert

Gibt den vorherigen handlermodus für **malloc**zurück. Der Rückgabewert 1 gibt an, dass bei einem Speicher Belegungs Fehler **malloc** zuvor als neue Handlerroutine bezeichnet wurde. der Rückgabewert 0 gibt an, dass dies nicht der Fall war. Wenn das Argument " *netwhandlermode* " nicht gleich 0 oder 1 ist, wird-1 zurückgegeben.

## <a name="remarks"></a>Bemerkungen

Die C++-Funktion **_set_new_mode** legt den neuen Handlermodus für [malloc](malloc.md) fest. Der neue handlermodus gibt an, ob **malloc** bei einem Fehler die neue Handlerroutine aufrufen soll, wie Sie von [_set_new_handler](set-new-handler.md)festgelegt wird. Standardmäßig ruft **malloc** die neue Handlerroutine nicht bei einem Fehler auf, um Arbeitsspeicher zuzuweisen. Sie können dieses Standardverhalten überschreiben, sodass **malloc** die neue Handlerroutine auf dieselbe Weise aufruft, wenn **malloc** keinen Arbeitsspeicher zuordnen kann, **`new`** Wenn es aus demselben Grund fehlschlägt. Weitere Informationen finden Sie unter den Operatoren [new](../../cpp/new-operator-cpp.md) und [delete](../../cpp/delete-operator-cpp.md) in der *C++-Sprachreferenz*. Um den Standardwert zu überschreiben, rufen Sie

```cpp
_set_new_mode(1);
```

Frühe in Ihrem Programm oder Verknüpfung mit NEWMODE. obj (siehe [Link Optionen](../../c-runtime-library/link-options.md)).

Diese Funktion überprüft seine Parameter. Wenn " *nwhandlermode* " etwas anderes als "0" oder "1" ist, ruft die Funktion den Handler für ungültige Parameter auf, wie unter [Parameter Validierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt <strong>_set_new_mode</strong> -1 zurück und legt **errno** auf fest `EINVAL` .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_set_new_mode**|\<new.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Speicher Belegung](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[Kosten](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
[_query_new_mode](query-new-mode.md)<br/>
