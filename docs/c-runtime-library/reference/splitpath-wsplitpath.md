---
title: _splitpath, _wsplitpath
ms.date: 4/2/2020
api_name:
- _wsplitpath
- _splitpath
- _o__splitpath
- _o__wsplitpath
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
- wsplitpath
- _splitpath
- splitpath
- _wsplitpath
- _tsplitpath
helpviewer_keywords:
- _splitpath function
- pathnames
- wsplitpath function
- splitpath function
- _wsplitpath function
- tsplitpath function
- path names
- _tsplitpath function
ms.assetid: 32bd76b5-1385-4ee8-a64c-abcb541cd2e4
ms.openlocfilehash: 6798f93b2d1bc18a190b3b015bf8c882a3fa8a37
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355613"
---
# <a name="_splitpath-_wsplitpath"></a>_splitpath, _wsplitpath

Unterteilen Sie einen Pfadnamen in Komponenten. Sicherere Versionen dieser Funktionen sind verfügbar. Informationen dazu finden Sie unter [_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md).

## <a name="syntax"></a>Syntax

```C
void _splitpath(
   const char *path,
   char *drive,
   char *dir,
   char *fname,
   char *ext
);
void _wsplitpath(
   const wchar_t *path,
   wchar_t *drive,
   wchar_t *dir,
   wchar_t *fname,
   wchar_t *ext
);
```

### <a name="parameters"></a>Parameter

*path*<br/>
Vollständiger Pfad

*Laufwerk*<br/>
Laufwerksbuchstabe, gefolgt von einem Doppelpunkt (**:**). Sie können **NULL** für diesen Parameter übergeben, wenn Sie den Laufwerkbuchstaben nicht benötigen.

*dir*<br/>
Verzeichnispfad, einschl. nachstehender Schrägstrich. Schrägstriche ( **/** ), umgekehrte **\\** Schrägstriche ( ), oder beide können verwendet werden. Sie können **NULL** für diesen Parameter übergeben, wenn Sie den Verzeichnispfad nicht benötigen.

*Fname*<br/>
Basisdateiname (ohne Erweiterung). Sie können **NULL** für diesen Parameter übergeben, wenn Sie den Dateinamen nicht benötigen.

*Extern*<br/>
Dateinamenerweiterung, einschließlich des führenden Zeitraums (**.**). Sie können **NULL** für diesen Parameter übergeben, wenn Sie die Dateinamenerweiterung nicht benötigen.

## <a name="remarks"></a>Bemerkungen

Die **_splitpath-Funktion** unterbricht einen Pfad in seine vier Komponenten. **_splitpath** verarbeitet automatisch Zeichenfolgenargumente mit mehreren Byte-Zeichen, wobei Multibyte-Zeichensequenzen entsprechend der derzeit in Gebrauch befindlichen Multibyte-Codepage erkannt werden. **_wsplitpath** ist eine breitgefächerte Version von **_splitpath**; Die Argumente für **_wsplitpath** sind Zeichenfolgen mit großen Zeichen. Anderenfalls verhalten sich diese Funktionen identisch.

**Sicherheitshinweis**: Diese Funktionen stellen eine mögliche Bedrohung aufgrund eines Pufferüberlaufproblems dar. Pufferüberlaufprobleme werden häufig bei Systemangriffen eingesetzt, da sie zu einer unbefugten Ausweitung der Berechtigungen führen. Weitere Informationen finden Sie unter [Vermeiden von Pufferüberläufen](/windows/win32/SecBP/avoiding-buffer-overruns). Sicherere Versionen dieser Funktionen sind verfügbar; siehe [_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath**|**_splitpath**|**_splitpath**|**_wsplitpath**|

Jede Komponente des vollständigen Pfads wird in einem separaten Puffer gespeichert. die Manifestkonstanten **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**und **_MAX_EXT** (definiert in STDLIB). H) Geben Sie die maximale Größe für jede Dateikomponente an. Dateikomponenten, die größer als die entsprechenden Manifestkonstanten sind, können zur Beschädigung des Heaps führen.

Jeder Puffer muss so groß wie die entsprechende Manifestkonstante sein, damit ein potenzieller Pufferüberlauf vermieden werden kann.

In der folgenden Tabelle werden die Werte der Manifestkonstanten aufgelistet.

|Name|Wert|
|----------|-----------|
|**_MAX_DRIVE**|3|
|**_MAX_DIR**|256|
|**_MAX_FNAME**|256|
|**_MAX_EXT**|256|

Wenn der vollständige Pfad keine Komponente enthält (z. B. einen Dateinamen), weist **_splitpath** den entsprechenden Puffern leere Zeichenfolgen zu.

Sie können **NULL** an **_splitpath** für einen anderen Parameter als den *Pfad* übergeben, den Sie nicht benötigen.

Wenn *pfad* **NULL**ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, wird **errno** auf **EINVAL** gesetzt und die Funktion gibt **EINVAL**zurück.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_splitpath**|\<stdlib.h>|
|**_wsplitpath**|\<stdlib.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Siehe Beispiel für [_makepath](makepath-wmakepath.md).

## <a name="see-also"></a>Siehe auch

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
