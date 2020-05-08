---
title: _purecall
ms.date: 4/2/2020
api_name:
- _purecall
- _o__purecall
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- purecall
- _purecall
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
ms.openlocfilehash: 19ad6c2f517d9ddf277a7bdda6e46c7940f0d3f1
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913338"
---
# <a name="_purecall"></a>_purecall

Der standardmäßige rein virtuelle Fehlerhandler für Funktionsaufrufe. Der Compiler generiert Code zum Aufrufen dieser Funktion, wenn eine rein virtuelle Memberfunktion aufgerufen wird.

## <a name="syntax"></a>Syntax

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>Hinweise

Die **_purecall** -Funktion ist ein Microsoft-spezifisches Implementierungsdetail des Microsoft C++-Compilers. Diese Funktion soll nicht direkt von Ihrem Code aufgerufen werden, und sie hat keine öffentliche Header-Deklaration. Es ist hier dokumentiert, da es sich um einen öffentlichen Export der C-Laufzeitbibliothek handelt.

Ein Aufruf an eine rein virtuelle Funktion ist ein Fehler, da sie keine Implementierung hat. Der Compiler generiert Code zum Aufrufen der **_purecall** Fehlerhandlerfunktion, wenn eine rein virtuelle Funktion aufgerufen wird. Standardmäßig beendet **_purecall** das Programm. Vor dem Beenden Ruft die **_purecall** -Funktion eine **_purecall_handler** Funktion auf, wenn eine für den Prozess festgelegt wurde. Sie können Ihre eigene Fehlerhandlerfunktion für rein virtuelle Funktionsaufrufe installieren, um sie für das Debuggen und für Berichtszwecke abzufangen. Um einen eigenen Fehlerhandler zu verwenden, erstellen Sie eine Funktion, die über die **_purecall_handler** Signatur verfügt, und verwenden Sie [_set_purecall_handler](get-purecall-handler-set-purecall-handler.md) , um Sie als aktuellen Handler festzulegen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

Die **_purecall** -Funktion hat keine Header Deklaration. Die **_purecall_handler** typedef wird in \<STDLIB. h> definiert.

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler, _set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
