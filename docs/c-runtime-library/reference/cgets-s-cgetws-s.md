---
title: _cgets_s, _cgetws_s
ms.date: 4/2/2020
api_name:
- _cgetws_s
- _cgets_s
- _o__cgets_s
- _o__cgetws_s
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
- api-ms-win-crt-conio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cgets_s
- cgets_s
- cgetws_s
- _cgetws_s
helpviewer_keywords:
- strings [C++], getting from console
- console, getting strings from
- _cgets_s function
- cget_s function
- _cgetws_s function
- cgetws_s function
ms.assetid: 38b74897-afe6-4dd9-a43f-36a3c0d72c5c
ms.openlocfilehash: b4871ff2c362e2c6cbe37be6a31bde4e6e258709
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333549"
---
# <a name="_cgets_s-_cgetws_s"></a>_cgets_s, _cgetws_s

Ruft eine Zeichenfolge aus der Konsole ab. Diese Versionen von [_cgets und _cgetws](../../c-runtime-library/cgets-cgetws.md) enthalten Sicherheitserweiterungen, wie dies unter [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben wird.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
errno_t _cgets_s(
   char *buffer,
   size_t numberOfElements,
   size_t *pSizeRead
);
errno_t _cgetws_s(
   wchar_t *buffer
   size_t numberOfElements,
   size_t *pSizeRead
);
template <size_t size>
errno_t _cgets_s(
   char (&buffer)[size],
   size_t *pSizeRead
); // C++ only
template <size_t size>
errno_t _cgetws_s(
   wchar_t (&buffer)[size],
   size_t *pSizeRead
); // C++ only
```

### <a name="parameters"></a>Parameter

*Puffer*<br/>
Speicherort für Daten.

*Sizeinbytes*<br/>
Die Größe des Puffers in Einzelbyte- oder Breitzeichen. Hierbei handelt es sich auch um die maximale Anzahl der zu lesenden Zeichen.

*pSizeRead*<br/>
Die Anzahl der tatsächlich gelesenen Zeichen.

## <a name="return-value"></a>Rückgabewert

Der Rückgabewert ist im Erfolgsfall „0“, andernfalls wird ein Fehlercode ausgegeben, wenn ein Fehler auftritt.

### <a name="error-conditions"></a>Fehlerbedingungen

|*Puffer*|*Sizeinbytes*|*pSizeRead*|Rückgabewert|Inhalt des *Puffers*|
|--------------|------------------------|-----------------|------------|--------------------------|
|**Null**|any|any|**Einval**|–|
|nicht **NULL**|Null|any|**Einval**|nicht geändert|
|nicht **NULL**|any|**Null**|**Einval**|Zeichenfolge mit der Länge 0|

## <a name="remarks"></a>Bemerkungen

**_cgets_s** und **_cgetws_s** eine Zeichenfolge aus der Konsole lesen und die Zeichenfolge (mit einem Null-Terminator) in *den Puffer*kopieren. **_cgetws_s** ist die Breitzeichenversion der Funktion; abgesehen von der Zeichengröße ist das Verhalten dieser beiden Funktionen identisch. Die maximale Größe der zu lesenden Zeichenfolge wird als *parameter numberOfElements* übergeben. Diese Größe sollte ein zusätzliches Zeichen für das abschließende Nullzeichen enthalten. Die tatsächliche Anzahl der gelesenen Zeichen wird in *pSizeRead*platziert.

Wenn während des Vorgangs oder im Zuge der Validierung der Parameter ein Fehler auftritt, wird der Handler für ungültige Parameter aufgerufen, wie dies unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben wird. Wenn die Ausführung fortgesetzt werden darf, wird **errno** auf **EINVAL** gesetzt und **EINVAL** zurückgegeben.

In C++ wird die Verwendung dieser Funktionen durch Vorlagenüberladungen vereinfacht. Die Überladungen können automatisch Rückschlüsse auf die Pufferlänge ziehen (wodurch kein „size“-Argument mehr angegeben werden muss), und sie können automatisch die älteren, nicht sicheren Funktionen durch ihre neueren, sicheren Entsprechungen ersetzen. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Die Debugbibliotheksversionen dieser Funktionen füllen zunächst den Puffer mit 0xFE. Um dieses Verhalten zu deaktivieren, verwenden Sie [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_cgetts_s**|**_cgets_s**|**_cgets_s**|**_cgetws_s**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_cgets_s**|\<conio.h>|
|**_cgetws_s**|\<conio.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Konsole und Port-I/O](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
