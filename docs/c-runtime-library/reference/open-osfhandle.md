---
title: _open_osfhandle
ms.date: 4/2/2020
api_name:
- _open_osfhandle
- _o__open_osfhandle
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _open_osfhandle
- open_osfhandle
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
ms.openlocfilehash: 9fbe4a4079fcbb8414e09d0f7dd814a3957e0822
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910675"
---
# <a name="_open_osfhandle"></a>_open_osfhandle

Ordnet einen C-Lauf Zeit Dateideskriptor einem vorhandenen Betriebssystem-Datei Handle zu.

## <a name="syntax"></a>Syntax

```cpp
int _open_osfhandle (
   intptr_t osfhandle,
   int flags
);
```

### <a name="parameters"></a>Parameter

*osfhandle*<br/>
Datei Handle des Betriebssystems.

*flags*<br/>
Zulässige Vorgangsarten.

## <a name="return-value"></a>Rückgabewert

Im Erfolgsfall gibt **_open_osfhandle** einen C-Laufzeit-Dateideskriptor zurück. Andernfalls wird –1 zurückgegeben.

## <a name="remarks"></a>Hinweise

Die **_open_osfhandle** -Funktion weist einen C-Lauf Zeit Dateideskriptor zu. Dieser Dateideskriptor wird dem von *OSF handle*angegebenen Betriebssystem-Datei Handle zugeordnet. Um eine Compilerwarnung zu vermeiden, wandeln Sie das *osfhandle*-Argument von **HANDLE** zu **intptr_t** um. Das *flags*-Argument ist ein Ganzzahlausdruck, der von einer oder mehreren der folgenden Manifestkonstanten gebildet wurde, die in \<fcntl.h> definiert sind. Sie können den bitweisen OR-Operator ( **&#124;** ) verwenden, um zwei oder mehr Manifest-Konstanten zu kombinieren, um das *Flags* -Argument zu bilden.

Die Manifestkonstanten werden in \<fcntl.h> definiert:

|||
|-|-|
| **\_O\_anfügen** | Positioniert einen Dateizeiger vor jedem Schreibvorgang am Ende der Datei. |
| **\_O\_rdonly** | Öffnet eine Datei nur zum Lesen. |
| **\_O\_-Text** | Öffnet eine Datei im Textmodus (übersetzt). |
| **\_O\_wtext** | Öffnet eine Datei in Unicode (übersetzt UTF-16). |

Der **_open_osfhandle**-Aufruf überträgt den Besitz am Win32-Dateihandle auf den Dateideskriptor. Um eine mit **_open_osfhandle** geöffnete Datei zu schließen, rufen Sie [\_close](close.md) auf. Das zugrundeliegende OS-Dateihandle wird auch mit einem **_close**-Aufruf geschlossen. Rufen Sie nicht die Win32-Funktion **CloseHandle** für das ursprüngliche Handle auf. Wenn sich der Dateideskriptor im Besitz einer **Datei &#42;** Streams befindet, schließt ein [fclose](fclose-fcloseall.md) -aufrufswert sowohl den Dateideskriptor als auch das zugrunde liegende Handle. In diesem Fall rufen Sie nicht **_close** für den Dateideskriptor oder **CloseHandle** für das ursprüngliche Handle auf.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[\_get_osfhandle](get-osfhandle.md)
