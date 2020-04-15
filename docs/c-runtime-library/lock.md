---
title: _lock
ms.date: 11/04/2016
api_name:
- _lock
api_location:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lock
- _lock
helpviewer_keywords:
- lock function
- _lock function
ms.assetid: 29f77c37-30de-4b3d-91b6-030216e645a6
ms.openlocfilehash: 30cd84f008c7174d767ecf5e2b744a58b21e5000
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351093"
---
# <a name="_lock"></a>_lock

Ruft eine Multi-Thread-Sperre ab.

> [!IMPORTANT]
> Diese Funktion ist veraltet. Von Visual Studio 2015 an ist sie nicht in der CRT verfügbar.

## <a name="syntax"></a>Syntax

```
void __cdecl _lock
   int locknum
);
```

#### <a name="parameters"></a>Parameter

*locknum*<br/>
[in]: Der Bezeichner der abzurufenden Sperre.

## <a name="remarks"></a>Bemerkungen

Wenn die Sperre bereits abgerufen wurde, ruft diese Methode die Sperre dennoch ab und verursacht einen internen C-Laufzeitfehler (CRT). Wenn die Methode keine Sperre abrufen kann, wird sie mit einem schwerwiegenden Fehler beendet und der Fehlercode auf `_RT_LOCK`festgelegt.

## <a name="requirements"></a>Anforderungen

**Quelle:** mlock.c

## <a name="see-also"></a>Siehe auch

[Alphabetische Funktionsreferenz](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[_unlock](../c-runtime-library/unlock.md)
