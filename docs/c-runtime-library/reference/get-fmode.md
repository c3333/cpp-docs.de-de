---
title: _get_fmode
ms.date: 4/2/2020
api_name:
- _get_fmode
- _o__get_fmode
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
- get_fmode
- _get_fmode
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
ms.openlocfilehash: 3e59e608f83874088b64d316c04053b94d8fbfdd
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909874"
---
# <a name="_get_fmode"></a>_get_fmode

Ruft den Standarddateiübersetzungsmodus für Datei E/A-Vorgänge auf.

## <a name="syntax"></a>Syntax

```C
errno_t _get_fmode(
   int * pmode
);
```

### <a name="parameters"></a>Parameter

*pmode*<br/>
Ein Zeiger auf eine Ganzzahl, die mit dem aktuellen Standardmodus aufgefüllt wird: **_O_TEXT** oder **_O_BINARY**.

## <a name="return-value"></a>Rückgabewert

Gibt 0 (null) zurück, wenn der Vorgang erfolgreich war. Wenn ein Fehler auftritt, erscheint ein Fehlercode. Wenn *pmode* **null**ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, wird **errno** auf **EINVAL** festgelegt, und die Funktion gibt **EINVAL**zurück.

## <a name="remarks"></a>Hinweise

Die Funktion legt die globale Variable [_fmode](../../c-runtime-library/fmode.md) fest. Diese Variable gibt den Standard-Datei Übersetzungsmodus für e/a-Vorgänge auf niedriger Ebene und Stream-Datei an, wie z. b. **_open**, **_pipe**, **f Open**und [freopen](freopen-wfreopen.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_get_fmode**|\<stdlib.h>|\<fcntl.h >|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Siehe das Beispiel in [_set_fmode](set-fmode.md).

## <a name="see-also"></a>Weitere Informationen

[_fmode](../../c-runtime-library/fmode.md)<br/>
[_set_fmode](set-fmode.md)<br/>
[_setmode](setmode.md)<br/>
[Text-und Binärmodus-Datei-e/a](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
