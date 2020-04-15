---
title: _umask
ms.date: 4/2/2020
api_name:
- _umask
- _o__umask
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _umask
helpviewer_keywords:
- masks, file-permission-setting
- _umask function
- masks
- umask function
- file permissions [C++]
- files [C++], permission settings for
ms.assetid: 5e9a13ba-5321-4536-8721-6afb6f4c8483
ms.openlocfilehash: b451f979f2925a31f5baaac52351c5d2c0a76da0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362023"
---
# <a name="_umask"></a>_umask

Legt die Standard-Dateiberechtigungsmaske fest. Es ist eine sicherere Version dieser Funktion verfügbar. Informationen dazu finden Sie unter [_umask_s](umask-s.md).

## <a name="syntax"></a>Syntax

```C
int _umask( int pmode );
```

### <a name="parameters"></a>Parameter

*Pmode*<br/>
Standard-Berechtigungseinstellung.

## <a name="return-value"></a>Rückgabewert

**_umask** gibt den vorherigen Wert von *pmode*zurück. Es gibt keine Fehlerrückgabe.

## <a name="remarks"></a>Bemerkungen

Die **_umask-Funktion** legt die Dateiberechtigungsmaske des aktuellen Prozesses in den von *pmode*angegebenen Modus fest. Die Dateiberechtigungsmaske ändert die Berechtigungseinstellung für neue Dateien, die von **_creat**, **_open**oder **_sopen**erstellt wurden. Wenn ein Bit in der Maske 1 ist, wird das entsprechende Bit im angeforderten Berechtigungswert der Datei auf 0 (nicht zulässig) festgelegt. Wenn ein Bit in der Maske 0 ist, bleibt das entsprechende Bit unverändert. Die Berechtigungseinstellung für eine neue Datei wird erst festgelegt, wenn die Datei zum ersten Mal geschlossen wird.

Der ganzzahlige Ausdruck *pmode* enthält eine oder beide der folgenden Manifestkonstanten, die in SYS-STAT definiert sind. H:

|*Pmode*| |
|-|-|
| **_S_IWRITE** | Schreiben erlaubt. |
| **_S_IREAD** | Lesen erlaubt. |
| **_S_IREAD** &#124; **_S_IWRITE** | Lesen und Schreiben erlaubt. |

Wenn beide Konstanten angegeben werden, werden sie mit dem bitwise-OR-Operator ( **&#124;** ) verbunden. Wenn das *pmode-Argument* **_S_IREAD**ist, ist das Lesen nicht zulässig (die Datei ist schreibgeschützt). Wenn das *pmode-Argument* **_S_IWRITE**ist, ist das Schreiben nicht zulässig (die Datei ist schreibgeschützt). Wenn z.B. das Schreib-Bit in der Maske festgelegt ist, sind alle neuen Dateien schreibgeschützt. Beachten Sie, dass in MS-DOS und Windows-Betriebssystemen alle Dateien lesbar sind und es nicht möglich ist, nur Schreibberechtigungen zu vergeben. Daher hat das Festlegen des Lesebits mit **_umask** keine Auswirkungen auf die Modi der Datei.

Wenn *pmode* keine Kombination aus einer der Manifestkonstanten ist oder einen alternativen Satz von Konstanten enthält, ignoriert die Funktion diese einfach.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_umask**|\<io.h>, \<sys/stat.h>, \<sys/types.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

```C
// crt_umask.c
// compile with: /W3
// This program uses _umask to set
// the file-permission mask so that all future
// files will be created as read-only files.
// It also displays the old mask.
#include <sys/stat.h>
#include <sys/types.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int oldmask;

   /* Create read-only files: */
   oldmask = _umask( _S_IWRITE ); // C4996
   // Note: _umask is deprecated; consider using _umask_s instead
   printf( "Oldmask = 0x%.4x\n", oldmask );
}
```

```Output
Oldmask = 0x0000
```

## <a name="see-also"></a>Siehe auch

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[Low-Level-E/A](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
