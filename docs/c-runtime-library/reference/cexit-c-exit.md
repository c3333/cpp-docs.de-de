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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 9eb856efca054423465aa7d30092edaf83a65eeb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333529"
---
# <a name="_cexit-_c_exit"></a>_cexit, _c_exit

Führt Bereinigungsvorgänge aus und kehrt zurück, ohne dass der Prozess beendet wird.

## <a name="syntax"></a>Syntax

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>Bemerkungen

Die **_cexit-Funktion** ruft in der LET-, First-Out-Reihenfolge (LIFO) die von **atexit** und **_onexit**registrierten Funktionen auf. Anschließend **wird _cexit** alle E/A-Puffer geleert und alle geöffneten Streams geschlossen, bevor sie zurückkehren. **_c_exit** ist identisch mit **_exit,** kehrt jedoch zum aufrufenden Prozess zurück, ohne **atexit-** oder **_onexit** oder das Leeren von Streampuffern zu verarbeiten. Das Verhalten **exit**, **_exit**, **_cexit**und **_c_exit** wird in der folgenden Tabelle angezeigt.

|Funktion|Verhalten|
|--------------|--------------|
|**Ausfahrt**|Führt vollständige C-Bibliotheksbeendigungsprozeduren aus, beendet den Prozess und beendet mit dem angegebenen Statuscode.|
|**_exit**|Führt schnelle C-Bibliotheksbeendigungsprozeduren aus, beendet den Prozess und beendet mit dem angegebenen Statuscode.|
|**_cexit**|Führt vollständige C-Bibliotheksbeendigungsprozeduren aus und kehrt zum Aufrufer zurück, beendet jedoch nicht den Prozess.|
|**_c_exit**|Führt schnelle C-Bibliotheksbeendigungsprozeduren aus und kehrt zum Aufrufer zurück, beendet jedoch nicht den Prozess.|

Wenn Sie die **_cexit-** oder **_c_exit-Funktionen** aufrufen, werden die Destruktoren für temporäre oder automatische Objekte, die zum Zeitpunkt des Aufrufs vorhanden sind, nicht aufgerufen. Ein automatisches Objekt ist ein Objekt, das in einer Funktion definiert wird, in der das Objekt nicht als statisch deklariert ist. Ein temporäres Objekt ist ein Objekt, das vom Compiler erstellt wird. Um ein automatisches Objekt zu zerstören, bevor **_cexit** oder **_c_exit**aufgerufen wird, rufen Sie den Destruktor für das Objekt wie folgt explizit auf:

```cpp
myObject.myClass::~myClass( );
```

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_cexit**|\<process.h>|
|**_c_exit**|\<process.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Prozess- und Umweltkontrolle](../../c-runtime-library/process-and-environment-control.md)<br/>
[Abbrechen](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec Funktionen](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn-, _wspawn-Funktionen](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
