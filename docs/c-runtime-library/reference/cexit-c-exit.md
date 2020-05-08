---
title: _cexit, _c_exit
ms.date: 4/2/2020
api_name:
- _c_exit
- _cexit
- _o__cexit
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cexit
- c_exit
- _c_exit
- cexit
helpviewer_keywords:
- cleanup operations during processes
- cexit function
- _c_exit function
- _cexit function
- c_exit function
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
ms.openlocfilehash: 78675ef91c2ab68e18f6111b4908886017ae1f79
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917145"
---
# <a name="_cexit-_c_exit"></a>_cexit, _c_exit

Führt Bereinigungsvorgänge aus und kehrt zurück, ohne dass der Prozess beendet wird.

## <a name="syntax"></a>Syntax

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>Hinweise

Die **_cexit** -Funktion ruft in der LIFO-Reihenfolge (Last in, First Out) die von **atexit** und **_onexit**registrierten Funktionen auf. **_Cexit** leert dann alle e/a-Puffer und schließt alle geöffneten Streams, bevor Sie zurückgegeben werden. **_c_exit** ist identisch mit **_exit** , kehrt aber zum aufrufenden Prozess zurück, ohne **atexit** oder **_onexit** zu verarbeiten oder Streampuffer zu leeren. Das Verhalten von **Exit**, **_exit**, **_cexit**und **_c_exit** ist in der folgenden Tabelle dargestellt.

|Funktion|Verhalten|
|--------------|--------------|
|**exit**|Führt vollständige C-Bibliotheksbeendigungsprozeduren aus, beendet den Prozess und beendet mit dem angegebenen Statuscode.|
|**_exit**|Führt schnelle C-Bibliotheksbeendigungsprozeduren aus, beendet den Prozess und beendet mit dem angegebenen Statuscode.|
|**_cexit**|Führt vollständige C-Bibliotheksbeendigungsprozeduren aus und kehrt zum Aufrufer zurück, beendet jedoch nicht den Prozess.|
|**_c_exit**|Führt schnelle C-Bibliotheksbeendigungsprozeduren aus und kehrt zum Aufrufer zurück, beendet jedoch nicht den Prozess.|

Wenn Sie die Funktionen **_cexit** oder **_c_exit** aufrufen, werden die dekodebugtoren für alle temporären oder automatischen Objekte, die zum Zeitpunkt des Aufrufs vorhanden sind, nicht aufgerufen. Ein automatisches Objekt ist ein Objekt, das in einer Funktion definiert wird, in der das Objekt nicht als statisch deklariert ist. Ein temporäres Objekt ist ein Objekt, das vom Compiler erstellt wird. Zum Zerstören eines automatischen Objekts vor dem Aufrufen von **_cexit** oder **_c_exit**rufen Sie den Dekonstruktor für das Objekt explizit wie folgt auf:

```cpp
myObject.myClass::~myClass( );
```

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_cexit**|\<process.h>|
|**_c_exit**|\<process.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[Abbruch](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec Funktionen](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn-, _wspawn-Funktionen](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
