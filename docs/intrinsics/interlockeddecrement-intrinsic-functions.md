---
title: _InterlockedDecrement intrinsische Funktionen
description: Intrinsische Microsoft C/C++-Compilerfunktionen für die Interlocked-Dekrement.
ms.date: 09/03/2020
f1_keywords:
- _InterlockedDecrement16_rel_cpp
- _InterlockedDecrement16_acq_cpp
- _InterlockedDecrement16_rel
- _InterlockedDecrement64_acq
- _InterlockedDecrement_nf
- _InterlockedDecrement16_nf
- _InterlockedDecrement64_rel_cpp
- _InterlockedDecrement_rel_cpp
- _InterlockedDecrement16_acq
- _InterlockedDecrement64_acq_cpp
- _InterlockedDecrement_rel
- _InterlockedDecrement64_nf
- _InterlockedDecrement16_cpp
- _InterlockedDecrement64
- _InterlockedDecrement_cpp
- _InterlockedDecrement64_rel
- _InterlockedDecrement16
- _InterlockedDecrement
- _InterlockedDecrement64_cpp
- _InterlockedDecrement_acq
- _InterlockedDecrement_acq_cpp
helpviewer_keywords:
- InterlockedDecrement64_rel intrinsic
- InterlockedDecrement64 intrinsic
- _InterlockedDecrement16 intrinsic
- _InterlockedDecrement16_acq intrinsic
- _InterlockedDecrement intrinsic
- _InterlockedDecrement_nf intrinsic
- _InterlockedDecrement_acq intrinsic
- _InterlockedDecrement64_rel intrinsic
- _InterlockedDecrement16_rel intrinsic
- InterlockedDecrement intrinsic
- InterlockedDecrement16 intrinsic
- _InterlockedDecrement16_nf intrinsic
- InterlockedDecrement64_acq intrinsic
- _InterlockedDecrement_rel intrinsic
- InterlockedDecrement_acq intrinsic
- _InterlockedDecrement64_acq intrinsic
- _InterlockedDecrement64 intrinsic
- _InterlockedDecrement64_nf intrinsic
- InterlockedDecrement_rel intrinsic
ms.assetid: 5268fce3-86b5-4b2b-b96c-2e531a3fb9b5
ms.openlocfilehash: b3ca624ba54f70750ecc303fb44f4fa242b4edc2
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556333"
---
# <a name="_interlockeddecrement-intrinsic-functions"></a>`_InterlockedDecrement` intrinsische Funktionen

Bietet systeminterne Compilerunterstützung für die Win32-Windows SDK [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement) -Funktion. Die `_InterlockedDecrement` intrinsischen Funktionen sind **Microsoft-spezifisch**.

## <a name="syntax"></a>Syntax

```C
long _InterlockedDecrement(
   long volatile * lpAddend
);
long _InterlockedDecrement_acq(
   long volatile * lpAddend
);
long _InterlockedDecrement_rel(
   long volatile * lpAddend
);
long _InterlockedDecrement_nf(
   long volatile * lpAddend
);
short _InterlockedDecrement16(
   short volatile * lpAddend
);
short _InterlockedDecrement16_acq(
   short volatile * lpAddend
);
short _InterlockedDecrement16_rel(
   short volatile * lpAddend
);
short _InterlockedDecrement16_nf(
   short volatile * lpAddend
);
__int64 _InterlockedDecrement64(
   __int64 volatile * lpAddend
);
__int64 _InterlockedDecrement64_acq(
   __int64 volatile * lpAddend
);
__int64 _InterlockedDecrement64_rel(
   __int64 volatile * lpAddend
);
__int64 _InterlockedDecrement64_nf(
   __int64 volatile * lpAddend
);
```

### <a name="parameters"></a>Parameter

*lpaddend*\
[in, out] Flüchtiger Zeiger auf die Variable, die dekrementiert werden soll.

## <a name="return-value"></a>Rückgabewert

Der Rückgabewert ist der resultierende verringerte Wert.

## <a name="requirements"></a>Anforderungen

|Intrinsic|Architektur|
|---------------|------------------|
|`_InterlockedDecrement`, `_InterlockedDecrement16`|x86, arm, x64, ARM64|
|`_InterlockedDecrement64`|Arm, x64, ARM64|
|`_InterlockedDecrement_acq`, `_InterlockedDecrement_rel`, `_InterlockedDecrement_nf`, `_InterlockedDecrement16_acq`, `_InterlockedDecrement16_rel`, `_InterlockedDecrement16_nf`, `_InterlockedDecrement64_acq`, `_InterlockedDecrement64_rel`, `_InterlockedDecrement64_nf`,|Arm, ARM64|

**Headerdatei** \<intrin.h>

## <a name="remarks"></a>Hinweise

Es gibt mehrere Varianten von `_InterlockedDecrement`, die sich basierend auf den beinhalteten Datentypen und in Abhängigkeit davon unterscheiden, ob prozessorspezifische Semantiken zum Abrufen bzw. Freigeben verwendet werden.

Während die `_InterlockedDecrement`-Funktion mit 32-Bit-Ganzzahlwerten arbeitet, verwendet `_InterlockedDecrement16`16-Bit-Ganzzahlwerte und `_InterlockedDecrement64` 64-Bit-Ganzzahlwerte.

Verwenden Sie auf ARM-Plattformen die systeminternen Funktionen mit den Suffixen `_acq` und `_rel`, wenn Sie Semantiken zum Abrufen bzw. Freigeben benötigen, wie am Anfang und Ende eines kritischen Abschnitts. Die intrinsischen Funktionen mit dem `_nf` Suffix ("No fence") fungieren nicht als Arbeitsspeicher Barriere.

Die Variable, auf die der `lpAddend`-Parameter zeigt, muss an einer 32-Bit-Grenze ausgerichtet sein; andernfalls schlägt diese Funktion auf x86-Multiprozessorsystemen und allen Nicht-x86-Systemen fehl. Weitere Informationen finden Sie unter [Ausrichten](../cpp/align-cpp.md).

Diese Routinen sind nur als systeminterne Funktionen verfügbar.

## <a name="example"></a>Beispiel

```cpp
// compiler_intrinsics_interlocked.cpp
// compile with: /Oi
#define _CRT_RAND_S

#include <cstdlib>
#include <cstdio>
#include <process.h>
#include <windows.h>

// To declare an interlocked function for use as an intrinsic,
// include intrin.h and put the function in a #pragma intrinsic
// statement.
#include <intrin.h>

#pragma intrinsic (_InterlockedIncrement)

// Data to protect with the interlocked functions.
volatile LONG data = 1;

void __cdecl SimpleThread(void* pParam);

const int THREAD_COUNT = 6;

int main() {
   DWORD num;
   HANDLE threads[THREAD_COUNT];
   int args[THREAD_COUNT];
   int i;

   for (i = 0; i < THREAD_COUNT; i++) {
      args[i] = i + 1;
      threads[i] = reinterpret_cast<HANDLE>(_beginthread(SimpleThread, 0,
                           args + i));
      if (threads[i] == reinterpret_cast<HANDLE>(-1))
         // error creating threads
         break;
   }

   WaitForMultipleObjects(i, threads, true, INFINITE);
}

// Code for our simple thread
void __cdecl SimpleThread(void* pParam) {
   int threadNum = *((int*)pParam);
   int counter;
   unsigned int randomValue;
   unsigned int time;
   errno_t err = rand_s(&randomValue);

   if (err == 0) {
      time = (unsigned int) ((double) randomValue / (double) UINT_MAX * 500);
      while (data < 100) {
         if (data < 100) {
            _InterlockedIncrement(&data);
            printf_s("Thread %d: %d\n", threadNum, data);
         }

         Sleep(time);   // wait up to half of a second
      }
   }

   printf_s("Thread %d complete: %d\n", threadNum, data);
}
```

## <a name="see-also"></a>Weitere Informationen

[Systeminterne Compilerfunktionen](../intrinsics/compiler-intrinsics.md)\
[Keywords](../cpp/keywords-cpp.md)\
[Konflikte mit dem x86-Compiler](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
