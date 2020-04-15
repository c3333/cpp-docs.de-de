---
title: _splitpath_s, _wsplitpath_s
ms.date: 4/2/2020
api_name:
- _wsplitpath_s
- _splitpath_s
- _o__splitpath_s
- _o__wsplitpath_s
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wsplitpath_s
- splitpath_s
- _splitpath_s
- wsplitpath_s
helpviewer_keywords:
- splitpath_s function
- pathnames
- _splitpath_s function
- _wsplitpath_s function
- path names
- wsplitpath_s function
ms.assetid: 30fff3e2-cd00-4eb6-b5a2-65db79cb688b
ms.openlocfilehash: 364544a9423668494747405e801d59b73de4e6c6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355619"
---
# <a name="_splitpath_s-_wsplitpath_s"></a>_splitpath_s, _wsplitpath_s

Unterteilen eines Pfadnamens in Komponenten Dies sind Versionen von [_splitpath, _wsplitpath](splitpath-wsplitpath.md) mit Sicherheitsverbesserungen, wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t _splitpath_s(
   const char * path,
   char * drive,
   size_t driveNumberOfElements,
   char * dir,
   size_t dirNumberOfElements,
   char * fname,
   size_t nameNumberOfElements,
   char * ext,
   size_t extNumberOfElements
);
errno_t _wsplitpath_s(
   const wchar_t * path,
   wchar_t * drive,
   size_t driveNumberOfElements,
   wchar_t *dir,
   size_t dirNumberOfElements,
   wchar_t * fname,
   size_t nameNumberOfElements,
   wchar_t * ext,
   size_t extNumberOfElements
);
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>
errno_t _splitpath_s(
   const char *path,
   char (&drive)[drivesize],
   char (&dir)[dirsize],
   char (&fname)[fnamesize],
   char (&ext)[extsize]
); // C++ only
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>
errno_t _wsplitpath_s(
   const wchar_t *path,
   wchar_t (&drive)[drivesize],
   wchar_t (&dir)[dirsize],
   wchar_t (&fname)[fnamesize],
   wchar_t (&ext)[extsize]
); // C++ only
```

### <a name="parameters"></a>Parameter

*path*<br/>
Vollständiger Pfad

*Laufwerk*<br/>
Laufwerksbuchstabe, gefolgt von einem Doppelpunkt (**:**). Sie können **NULL** für diesen Parameter übergeben, wenn Sie den Laufwerkbuchstaben nicht benötigen.

*driveNumberOfElements*<br/>
Die Größe des *Laufwerkpuffers* in Einzelbyte oder breiten Zeichen. Wenn *Laufwerk* **NULL**ist, muss dieser Wert 0 sein.

*dir*<br/>
Verzeichnispfad, einschl. nachstehender Schrägstrich. Schrägstriche ( **/** ), umgekehrte **\\** Schrägstriche ( ), oder beide können verwendet werden. Sie können **NULL** für diesen Parameter übergeben, wenn Sie den Verzeichnispfad nicht benötigen.

*dirNumberOfElements*<br/>
Die Größe *dir* des Dir-Puffers in Einzelbyte oder breiten Zeichen. Wenn *dir* **NULL**ist, muss dieser Wert 0 sein.

*Fname*<br/>
Basisdateiname (ohne Erweiterung). Sie können **NULL** für diesen Parameter übergeben, wenn Sie den Dateinamen nicht benötigen.

*nameNumberOfElements*<br/>
Die Größe des *fname-Puffers* in Einzelbyte oder breiten Zeichen. Wenn *fname* **NULL**ist, muss dieser Wert 0 sein.

*Extern*<br/>
Dateinamenerweiterung, einschließlich des führenden Zeitraums (**.**). Sie können **NULL** für diesen Parameter übergeben, wenn Sie die Dateinamenerweiterung nicht benötigen.

*extNumberOfElements*<br/>
Die Größe des *ext-Puffers* in Einzelbyte oder breiten Zeichen. Wenn *ext* **NULL**ist, muss dieser Wert 0 sein.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, ein Fehlercode, wenn ein Fehler auftritt.

### <a name="error-conditions"></a>Fehlerbedingungen

|Bedingung|Rückgabewert|
|---------------|------------------|
|*Pfad* ist **NULL**|**Einval**|
|*Laufwerk* ist **NULL**, *driveNumberOfElements* ist ungleich Null|**Einval**|
|*Laufwerk* ist nicht**NULL**, *driveNumberOfElements* ist Null|**Einval**|
|*dir* ist **NULL**, *dirNumberOfElements* ist ungleich Null|**Einval**|
|*dir* ist nicht**NULL**, *dirNumberOfElements* ist Null|**Einval**|
|*fname* ist **NULL**, *nameNumberOfElements* ist ungleich Null|**Einval**|
|*fname* ist nicht**NULL**, *nameNumberOfElements* ist Null|**Einval**|
|*ext* ist **NULL**, *extNumberOfElements* ist ungleich Null|**Einval**|
|*ext* ist nicht**NULL**, *extNumberOfElements* ist Null|**Einval**|

Wenn eine dieser Bedingungen auftritt, wird die Ausnahme für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameterüberprüfung)](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die Ausführung fortgesetzt werden darf, setzen diese Funktionen **errno** auf **EINVAL** und geben **EINVAL**zurück.

Wenn einer der Puffer zu kurz ist, um das Ergebnis zu halten, löschen diese Funktionen alle Puffer auf leere Zeichenfolgen, legen **errno** auf **ERANGE**fest und geben **ERANGE**zurück.

## <a name="remarks"></a>Bemerkungen

Die **_splitpath_s-Funktion** unterbricht einen Pfad in seine vier Komponenten. **_splitpath_s** verarbeitet automatisch Zeichenfolgenargumente mit mehreren Byte-Zeichen, wobei Multibyte-Zeichensequenzen entsprechend der derzeit in Gebrauch befindlichen Multibyte-Codepage erkannt werden. **_wsplitpath_s** ist eine breit gefächerte Version von **_splitpath_s**; Die Argumente für **_wsplitpath_s** sind Zeichenfolgen mit großen Zeichen. Andernfalls verhalten sich diese Funktionen identisch

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath_s**|**_splitpath_s**|**_splitpath_s**|**_wsplitpath_s**|

Jede Komponente des vollständigen Pfads wird in einem separaten Puffer gespeichert. die Manifestkonstanten **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**und **_MAX_EXT** (definiert in STDLIB). H) geben Sie die maximal zulässige Größe für jede Dateikomponente an. Dateikomponenten, die größer als die entsprechenden Manifestkonstanten sind, können zur Beschädigung des Heaps führen.

In der folgenden Tabelle werden die Werte der Manifestkonstanten aufgelistet.

|Name|Wert|
|----------|-----------|
|_MAX_DRIVE|3|
|_MAX_DIR|256|
|_MAX_FNAME|256|
|_MAX_EXT|256|

Wenn der vollständige Pfad keine Komponente enthält (z. B. einen Dateinamen), weist **_splitpath_s** dem entsprechenden Puffer eine leere Zeichenfolge zu.

Die Verwendung dieser Funktionen in C++ wird durch Überladungen (als Vorlagen vorhanden) vereinfacht. Überladungen können automatisch die Pufferlänge ableiten, sodass kein Größenargument angegeben werden muss. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Die Debugbibliotheksversionen dieser Funktionen füllen zunächst den Puffer mit 0xFE. Um dieses Verhalten zu deaktivieren, verwenden Sie [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_splitpath_s**|\<stdlib.h>|
|**_wsplitpath_s**|\<stdlib.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Siehe das Beispiel für [_makepath_s _wmakepath_s](makepath-s-wmakepath-s.md).

## <a name="see-also"></a>Siehe auch

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
