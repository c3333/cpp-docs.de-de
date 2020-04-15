---
title: _umask_s
ms.date: 4/2/2020
api_name:
- _umask_s
- _o__umask_s
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
- unmask_s
- _umask_s
helpviewer_keywords:
- masks, file-permission-setting
- _umask_s function
- masks
- file permissions [C++]
- umask_s function
- files [C++], permission settings for
ms.assetid: 70898f61-bf2b-4d8d-8291-0ccaa6d33145
ms.openlocfilehash: d590910d5f5092a78ad64c8f9ef0aa259211e226
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362178"
---
# <a name="_umask_s"></a>_umask_s

Legt die Standard-Dateiberechtigungsmaske fest. Dies ist eine Version von [_umask](umask.md) mit Sicherheitserweiterungen wie in den [Sicherheitsfunktionen in CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t _umask_s(
   int mode,
   int * pOldMode
);
```

### <a name="parameters"></a>Parameter

*Modus*<br/>
Standard-Berechtigungseinstellung.

*pOldMode*<br/>
Der vorherige Wert der Berechtigungseinstellung.

## <a name="return-value"></a>Rückgabewert

Gibt einen Fehlercode zurück, wenn *der Modus* keinen gültigen Modus angibt oder der *pOldMode-Zeiger* **NULL**ist.

### <a name="error-conditions"></a>Fehlerbedingungen

|*Modus*|*pOldMode*|Rückgabewert|Inhalt von *pOldMode*|
|------------|----------------|----------------------|--------------------------------|
|any|**Null**|**Einval**|nicht geändert|
|ungültiger Modus|any|**Einval**|nicht geändert|

Wenn eine der obengenannten Bedingungen auftritt, wird der Handler für ungültige Parameter aufgerufen wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die Ausführung fortgesetzt werden darf, **gibt _umask_s** **EINVAL** zurück und setzt **errno** auf **EINVAL**.

## <a name="remarks"></a>Bemerkungen

Die **_umask_s-Funktion** legt die Dateiberechtigungsmaske des aktuellen Prozesses in den vom *Modus*angegebenen Modus fest. Die Dateiberechtigungsmaske ändert die Berechtigungseinstellung für neue Dateien, die von **_creat**, **_open**oder **_sopen**erstellt wurden. Wenn ein Bit in der Maske 1 ist, wird das entsprechende Bit im angeforderten Berechtigungswert der Datei auf 0 (nicht zulässig) festgelegt. Wenn ein Bit in der Maske 0 ist, bleibt das entsprechende Bit unverändert. Die Berechtigungseinstellung für eine neue Datei wird erst festgelegt, wenn die Datei zum ersten Mal geschlossen wird.

Der ganzzahlige Ausdruck *pmode* enthält eine oder beide der folgenden Manifestkonstanten, die in SYS-STAT definiert sind. H:

|*Pmode*||
|-|-|
|**_S_IWRITE**|Schreiben erlaubt.|
|**_S_IREAD**|Lesen erlaubt.|
|**_S_IREAD** \| **_S_IWRITE**|Lesen und Schreiben erlaubt.|

Wenn beide Konstanten angegeben werden, werden sie mit **|** dem bitwise-OR-Operator ( ) verbunden. Wenn das *Modusargument* **_S_IREAD**ist, ist das Lesen nicht zulässig (die Datei ist schreibgeschützt). Wenn das *Modeargument* **_S_IWRITE**ist, ist das Schreiben nicht zulässig (die Datei ist schreibgeschützt). Wenn z.B. das Schreib-Bit in der Maske festgelegt ist, sind alle neuen Dateien schreibgeschützt. Beachten Sie, dass in MS-DOS und Windows-Betriebssystemen alle Dateien lesbar sind und es nicht möglich ist, nur Schreibberechtigungen zu vergeben. Daher hat das Festlegen des Lesebits mit **_umask_s** keine Auswirkungen auf die Modi der Datei.

Wenn *pmode* keine Kombination aus einer der Manifestkonstanten ist oder einen alternativen Satz von Konstanten enthält, ignoriert die Funktion diese einfach.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_umask_s**|\<io.h> und \<sys/stat.h> und \<sys/types.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_umask_s.c
/* This program uses _umask_s to set
* the file-permission mask so that all future
* files will be created as read-only files.
* It also displays the old mask.
*/

#include <sys/stat.h>
#include <sys/types.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int oldmask, err;

   /* Create read-only files: */
   err = _umask_s( _S_IWRITE, &oldmask );
   if (err)
   {
      printf("Error setting the umask.\n");
      exit(1);
   }
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
[_umask](umask.md)<br/>
