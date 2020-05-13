---
title: _callnewh
ms.date: 4/2/2020
api_name:
- _callnewh
- _o__callnewh
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
- _callnewh
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
ms.openlocfilehash: 3990d4b15c25cfd6c753c2b1d44c112971ff59af
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918802"
---
# <a name="_callnewh"></a>_callnewh

Ruft den aktuell installierten *neuen Handler* auf.

## <a name="syntax"></a>Syntax

```cpp
int _callnewh(
   size_t size
   )
```

### <a name="parameters"></a>Parameter

*size*<br/>
Der Speicherplatz, den der [neue Operator](../../cpp/new-operator-cpp.md) zu belegen versucht hat.

## <a name="return-value"></a>Rückgabewert

|Value|Beschreibung|
|-----------|-----------------|
|0|Fehler: Entweder wurde kein neuer Handler installiert oder der neue Handler ist nicht aktiv.|
|1|Erfolg: Der neue Handler wurde installiert und ist aktiv. Die Speicherbelegung kann wiederholt werden.|

## <a name="exceptions"></a>Ausnahmen

Diese Funktion löst [bad_alloc](../../standard-library/bad-alloc-class.md) aus, wenn der *neue Handler* nicht gefunden werden kann.

## <a name="remarks"></a>Hinweise

Der *neue Handler* wird aufgerufen, wenn der [neue Operator](../../cpp/new-operator-cpp.md) die Speicherbelegung nicht erfolgreich durchführen kann. Der neue Handler initialisiert dann möglicherweise einige entsprechende Aktionen, z. B. die Freigabe des Speichers, sodass nachfolgende Belegungen erfolgreich sind.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|_callnewh|internal.h|

## <a name="see-also"></a>Weitere Informationen

[_set_new_handler](set-new-handler.md)<br/>
[_set_new_mode](set-new-mode.md)<br/>
