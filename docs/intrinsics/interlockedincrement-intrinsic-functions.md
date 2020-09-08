---
title: _InterlockedIncrement intrinsische Funktionen
description: Intrinsische Microsoft C/C++-Compilerfunktionen für das Interlocked-Inkrement.
ms.date: 09/03/2020
f1_keywords:
- _InterlockedIncrement_acq
- _InterlockedIncrement16_rel_cpp
- _InterlockedIncrement16_cpp
- _InterlockedIncrement64_rel
- _InterlockedIncrement_rel
- _InterlockedIncrement64_nf
- _InterlockedIncrement16_acq_cpp
- _InterlockedIncrement_rel_cpp
- _InterlockedIncrement64
- _InterlockedIncrement64_rel_cpp
- _InterlockedIncrement16_nf
- _InterlockedIncrement16_rel
- _InterlockedIncrement16_acq
- _InterlockedIncrement_nf
- _InterlockedIncrement_acq_cpp
- _InterlockedIncrement64_cpp
- _InterlockedIncrement64_acq_cpp
- _InterlockedIncrement
- _InterlockedIncrement_cpp
- _InterlockedIncrement64_acq
- _InterlockedIncrement16
helpviewer_keywords:
- _InterlockedIncrement64_rel intrinsic
- _InterlockedIncrement16_rel intrinsic
- InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16 intrinsic
- _InterlockedIncrement16_acq intrinsic
- _InterlockedIncrement_nf intrinsic
- _InterlockedIncrement_rel intrinsic
- _InterlockedIncrement64_nf intrinsic
- InterlockedIncrement_rel intrinsic
- InterlockedIncrement_acq intrinsic
- _InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16_nf intrinsic
- _InterlockedIncrement intrinsic
- _InterlockedIncrement64 intrinsic
- InterlockedIncrement64_rel intrinsic
- InterlockedIncrement64 intrinsic
- InterlockedIncrement16 intrinsic
- _InterlockedIncrement_acq intrinsic
- InterlockedIncrement intrinsic
ms.assetid: 37700615-f372-438b-bcef-d76e11839482
ms.openlocfilehash: 2148ae31f3eb03e398372db3bf15fc64e4857dd1
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556320"
---
# <a name="_interlockedincrement-intrinsic-functions"></a>`_InterlockedIncrement` intrinsische Funktionen

Bereitstellen von System interner Compilerunterstützung für die Win32-Windows SDK [interlockedinkrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement) -Funktion. Die `_InterlockedIncrement` intrinsischen Funktionen sind **Microsoft-spezifisch**.

## <a name="syntax"></a>Syntax

```C
long _InterlockedIncrement(
   long volatile * lpAddend
);
long _InterlockedIncrement_acq(
   long volatile * lpAddend
);
long _InterlockedIncrement_rel(
   long volatile * lpAddend
);
long _InterlockedIncrement_nf(
   long volatile * lpAddend
);
short _InterlockedIncrement16(
   short volatile * lpAddend
);
short _InterlockedIncrement16_acq(
   short volatile * lpAddend
);
short _InterlockedIncrement16_rel(
   short volatile * lpAddend
);
short _InterlockedIncrement16_nf (
   short volatile * lpAddend
);
__int64 _InterlockedIncrement64(
   __int64 volatile * lpAddend
);
__int64 _InterlockedIncrement64_acq(
   __int64 volatile * lpAddend
);
__int64 _InterlockedIncrement64_rel(
   __int64 volatile * lpAddend
);
__int64 _InterlockedIncrement64_nf(
   __int64 volatile * lpAddend
);
```

### <a name="parameters"></a>Parameter

*lpaddend*\
[in, out] Ein Zeiger auf die Variable, die inkrementiert werden soll.

## <a name="return-value"></a>Rückgabewert

Der Rückgabewert ist der resultierende erhöhte Wert.

## <a name="requirements"></a>Anforderungen

|Intrinsic|Architektur|Header|
|---------------|------------------|------------|
|`_InterlockedIncrement`, `_InterlockedIncrement16`|x86, arm, x64, ARM64|\<intrin.h>|
|`_InterlockedIncrement64`|Arm, x64, ARM64|\<intrin.h>|
|`_InterlockedIncrement_acq`, `_InterlockedIncrement_rel`, `_InterlockedIncrement_nf`, `_InterlockedIncrement16_acq`, `_InterlockedIncrement16_rel`, `_InterlockedIncrement16_nf`, `_InterlockedIncrement64_acq`, `_InterlockedIncrement64_rel`, `_InterlockedIncrement64_nf`|Arm, ARM64|\<intrin.h>|

## <a name="remarks"></a>Hinweise

Es gibt mehrere Varianten von `_InterlockedIncrement`, die sich basierend auf den beinhalteten Datentypen und in Abhängigkeit davon unterscheiden, ob prozessorspezifische Semantiken zum Abrufen bzw. Freigeben verwendet werden.

Während die `_InterlockedIncrement`-Funktion mit 32-Bit-Ganzzahlwerten arbeitet, verwendet `_InterlockedIncrement16`16-Bit-Ganzzahlwerte und `_InterlockedIncrement64` 64-Bit-Ganzzahlwerte.

Verwenden Sie auf ARM-Plattformen die systeminternen Funktionen mit den Suffixen `_acq` und `_rel`, wenn Sie Semantiken zum Abrufen bzw. Freigeben benötigen, wie am Anfang und Ende eines kritischen Abschnitts. Das systeminterne- `_nf` Suffix mit dem Suffix ("No fence") fungiert nicht als Arbeitsspeicher Barriere.

Die Variable, auf die der `lpAddend`-Parameter zeigt, muss an einer 32-Bit-Grenze ausgerichtet sein; andernfalls schlägt diese Funktion auf x86-Multiprozessorsystemen und allen Nicht-x86-Systemen fehl. Weitere Informationen finden Sie unter [Ausrichten](../cpp/align-cpp.md).

Die Win32-Funktion wird in `Wdm.h` oder `Ntddk.h` deklariert.

Diese Routinen sind nur als systeminterne Funktionen verfügbar.

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `_InterlockedIncrement` finden Sie unter [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).

## <a name="see-also"></a>Weitere Informationen

[Systeminterne Compilerfunktionen](../intrinsics/compiler-intrinsics.md)\
[Keywords](../cpp/keywords-cpp.md)\
[Konflikte mit dem x86-Compiler](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
