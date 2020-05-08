---
title: _findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64
ms.date: 4/2/2020
api_name:
- _findnext
- _findnext32
- _findnext32i64
- _findnext64
- _findnext64i32
- _findnexti64
- _wfindnext
- _wfindnext32
- _wfindnext32i64
- _wfindnext64
- _wfindnext64i32
- _wfindnexti64
- _o__findnext32
- _o__findnext32i64
- _o__findnext64
- _o__findnext64i32
- _o__wfindnext32
- _o__wfindnext32i64
- _o__wfindnext64
- _o__wfindnext64i32
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- findnext
- _wfindnext32i64
- _tfindnext64i32
- findnext32
- findnext32i64
- wfindnext64i32
- _wfindnext
- tfindnext64
- findnexti64
- _findnexti64
- _tfindnexti64
- _findnext64i32
- tfindnexti64
- tfindnext32
- _wfindnext64i32
- findnext64i32
- _findnext
- _tfindnext32i64
- _wfindnext64
- wfindnext
- wfindnext32
- tfindnext32i64
- _findnext64
- _tfindnext64
- _wfindnext32
- findnext64
- _findnext32i64
- tfindnext
- wfindnexti64
- tfindnext64i32
- _tfindnext32
- wfindnext32i64
- wfindnext64
- _wfindnexti64
- _tfindnext
- _findnext32
helpviewer_keywords:
- _wfindnexti64 function
- _tfindnext32 function
- wfindnexti64 function
- _wfindnext32i64 function
- findnext32i64 function
- tfindnext64i32 function
- _tfindnext64i32 function
- _findnext function
- findnext64i32 function
- _tfindnext function
- findnext32 function
- tfindnext32 function
- _findnext32 function
- _tfindnext32i64 function
- _wfindnext function
- tfindnext function
- _findnext64 function
- findnext64 function
- _findnext64i32 function
- wfindnext32i64 function
- findnext function
- wfindnext32 function
- _wfindnext64i32 function
- findnexti64 function
- _wfindnext64 function
- _findnext32i64 function
- _findnexti64 function
- _tfindnext64 function
- wfindnext64i32 function
- tfindnexti64 function
- wfindnext64 function
- wfindnext function
- tfindnext64 function
- _wfindnext32 function
- tfindnext32i64 function
- _tfindnexti64 function
ms.assetid: 75d97188-5add-4698-a46c-4c492378f0f8
ms.openlocfilehash: acb680db3b07b0f600b758401f1270deccf03da7
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911663"
---
# <a name="_findnext-_findnext32-_findnext32i64-_findnext64-_findnext64i32-_findnexti64-_wfindnext-_wfindnext32-_wfindnext32i64-_wfindnext64-_wfindnext64i32-_wfindnexti64"></a>_findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64

Suchen Sie ggf. nach dem nächsten Namen, der mit dem *Datei Angabe* -Argument in einem vorherigen- [_findfirst](findfirst-functions.md)übereinstimmt, und ändern Sie dann den *FileInfo* -Struktur Inhalt entsprechend.

## <a name="syntax"></a>Syntax

```C
int _findnext(
   intptr_t handle,
   struct _finddata_t *fileinfo
);
int _findnext32(
   intptr_t handle,
   struct _finddata32_t *fileinfo
);
int _findnext64(
   intptr_t handle,
   struct __finddata64_t *fileinfo
);
int _findnexti64(
   intptr_t handle,
   struct __finddatai64_t *fileinfo
);
int _findnext32i64(
   intptr_t handle,
   struct _finddata32i64_t *fileinfo
);
int _findnext64i32(
   intptr_t handle,
   struct _finddata64i32_t *fileinfo
);
int _wfindnext(
   intptr_t handle,
   struct _wfinddata_t *fileinfo
);
int _wfindnext32(
   intptr_t handle,
   struct _wfinddata32_t *fileinfo
);
int _wfindnext64(
   intptr_t handle,
   struct _wfinddata64_t *fileinfo
);
int _wfindnexti64(
   intptr_t handle,
   struct _wfinddatai64_t *fileinfo
);
int _wfindnext32i64(
   intptr_t handle,
   struct _wfinddatai64_t *fileinfo
);
int _wfindnext64i32(
   intptr_t handle,
   struct _wfinddata64i32_t *fileinfo
);
```

### <a name="parameters"></a>Parameter

*bewältigen*<br/>
Das Suchhandle, das von einem vorherigen- **_findfirst**zurückgegeben wurde.

*FileInfo*<br/>
Puffer für Dateiinformationen.

## <a name="return-value"></a>Rückgabewert

Bei Erfolg wird 0 zurückgegeben. Andernfalls wird-1 zurückgegeben, und **errno** wird auf einen Wert festgelegt, der die Art des Fehlers angibt. Mögliche Fehlercodes werden in der folgenden Tabelle dargestellt.

|errno-Wert|Bedingung|
|-|-|
| **Eingabe** | Ungültiger Parameter: " *filinput Info* " war **null**. oder das Betriebssystem hat einen unerwarteten Fehler zurückgegeben. |
| **ENOENT** | Es konnten keine übereinstimmenden Dateien gefunden werden. |
| **Umomem** | Nicht genügend Arbeitsspeicher, oder die Länge des Datei namens wurde **MAX_PATH**überschritten. |

Wenn ein ungültiger Parameter übergeben wird, rufen diese Funktionen den Handler für ungültige Parameter auf, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben wird.

## <a name="remarks"></a>Hinweise

Sie müssen [_findclose](findclose.md) abrufen, nachdem Sie die **_findfirst** -oder **_findnext** -Funktion (oder eine beliebige Variante) verwendet haben. Auf diese Weise werden Ressourcen frei, die von diesen Funktionen in Ihrer Anwendung verwendet werden.

Die Variationen dieser Funktionen mit dem **w** -Präfix sind breit Zeichen Versionen. Andernfalls sind Sie identisch mit den entsprechenden Einzel Byte Funktionen.

Varianten dieser Funktionen unterstützen 32-Bit- oder 64-Bit-Zeittypen und 32-Bit- oder 64-Bit-Dateigrößen. Das erste numerische Suffix (**32** oder **64**) gibt die Größe des verwendeten Zeittyps an. Das zweite Suffix ist entweder **i32** oder **I64**, das angibt, ob die Dateigröße als 32-Bit-oder 64-Bit-Ganzzahl dargestellt wird. Informationen darüber, welche Versionen 32-Bit- und 64-Bit-Zeittypen und -Dateigrößen unterstützen, finden Sie in der folgenden Tabelle. In Varianten, die einen 64-Bit-Zeittyp verwenden, kann das Erstellungsdatum der Datei bis 23:59:59 am 31. Dezember 3000 (UTC) ausgedrückt werden. Die Varianten, die 32-Bit-Zeittypen verwenden, stellen Datumsangaben nur bis 23:59:59 am 18. Januar 2038 (UTC) dar. Der 1. Januar 1970 (Mitternacht) ist der älteste mögliche Datumsbereich für beide Funktionen.

Wenn Sie nicht über einen bestimmten Grund für die Verwendung der Versionen verfügen, die die zeitgröße explizit angeben, verwenden Sie **_findnext** oder **_wfindnext** oder wenn Sie Dateigrößen von mehr als 3 GB unterstützen müssen, verwenden Sie **_findnexti64** oder **_wfindnexti64**. All diese Funktionen verwenden den 64-Bit-Zeittyp. In früheren Versionen verwendeten diese Funktionen einen 32-Bit-Zeittyp. Wenn dies eine Breaking Change für eine Anwendung ist, können Sie **_USE_32BIT_TIME_T** definieren, um das alte Verhalten zu erhalten. Wenn **_USE_32BIT_TIME_T** definiert ist, **_findnext**verwenden _findnext **_finnexti64** und die entsprechenden Unicode-Versionen eine 32-Bit-Zeit.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_findnext"></a>_findnext-Varianten des Uhrzeittyps und Dateilängentyps

|Functions|**_USE_32BIT_TIME_T** definiert?|Uhrzeittyp|Dateilängentyp|
|---------------|----------------------------------|---------------|----------------------|
|**_findnext** **_wfindnext**|Nicht definiert|64-Bit|32-Bit|
|**_findnext** **_wfindnext**|Definiert|32-Bit|32-Bit|
|**_findnext32** **_wfindnext32**|Nicht von der Makrodefinition betroffen|32-Bit|32-Bit|
|**_findnext64** **_wfindnext64**|Nicht von der Makrodefinition betroffen|64-Bit|64-Bit|
|**_findnexti64** **_wfindnexti64**|Nicht definiert|64-Bit|64-Bit|
|**_findnexti64** **_wfindnexti64**|Definiert|32-Bit|64-Bit|
|**_findnext32i64** **_wfindnext32i64**|Nicht von der Makrodefinition betroffen|32-Bit|64-Bit|
|**_findnext64i32** **_wfindnext64i32**|Nicht von der Makrodefinition betroffen|64-Bit|32-Bit|

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfindnext**|**_findnext**|**_findnext**|**_wfindnext**|
|**_tfindnext32**|**_findnext32**|**_findnext32**|**_wfindnext32**|
|**_tfindnext64**|**_findnext64**|**_findnext64**|**_wfindnext64**|
|**_tfindnexti64**|**_findnexti64**|**_findnexti64**|**_wfindnexti64**|
|**_tfindnext32i64**|**_findnext32i64**|**_findnext32i64**|**_wfindnext32i64**|
|**_tfindnext64i32**|**_findnext64i32**|**_findnext64i32**|**_wfindnext64i32**|

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**_findnext**|\<io.h>|
|**_findnext32**|\<io.h>|
|**_findnext64**|\<io.h>|
|**_findnexti64**|\<io.h>|
|**_findnext32i64**|\<io.h>|
|**_findnext64i32**|\<io.h>|
|**_wfindnext**|\<io.h> oder \<wchar.h>|
|**_wfindnext32**|\<io.h> oder \<wchar.h>|
|**_wfindnext64**|\<io.h> oder \<wchar.h>|
|**_wfindnexti64**|\<io.h> oder \<wchar.h>|
|**_wfindnext32i64**|\<io.h> oder \<wchar.h>|
|**_wfindnext64i32**|\<io.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Weitere Informationen

[Systemaufrufe](../../c-runtime-library/system-calls.md)<br/>
[Dateinamen-Suchfunktionen](../../c-runtime-library/filename-search-functions.md)<br/>
