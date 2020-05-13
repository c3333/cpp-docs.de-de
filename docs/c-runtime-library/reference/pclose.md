---
title: _pclose
ms.date: 4/2/2020
api_name:
- _pclose
- _o__pclose
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
- _pclose
- pclose
helpviewer_keywords:
- _pclose function
- pclose function
- pipes, closing
ms.assetid: e2e31a9e-ba3a-4124-bcbb-c4040110b3d3
ms.openlocfilehash: 6b35b8e3faa2f1a193dce102a6f8a11b9fcbb82b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910388"
---
# <a name="_pclose"></a>_pclose

Wartet auf einen neuen Befehlsprozessor und schließt den Stream auf der zugeordneten Pipe.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int _pclose(
FILE *stream
);
```

### <a name="parameters"></a>Parameter

*Streich*<br/>
Rückgabewert des vorherigen Aufrufes **_popen**.

## <a name="return-value"></a>Rückgabewert

Gibt den Beendigungs Status des beendenden Befehls Prozessors zurück, oder-1, wenn ein Fehler auftritt. Das Format des Rückgabewerts ist mit dem Wert für **_cwait**identisch, mit dem Unterschied, dass die nieder wertigen und höherwertigen Bytes vertauscht werden. Wenn der Stream **null**ist, legt **_pclose** **errno** auf **EINVAL** fest und gibt-1 zurück.

Weitere Informationen über diese und andere Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Die **_pclose** -Funktion sucht die Prozess-ID des Befehls Prozessors (cmd. exe), die vom zugeordneten **_popen** -Befehl gestartet wurde, führt einen [_cwait](cwait.md) -Befehl für den neuen Befehlsprozessor aus und schließt den Stream auf der zugeordneten Pipe.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_pclose**|\<stdio.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Weitere Informationen

[Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[_pipe](pipe.md)<br/>
[_popen, _wpopen](popen-wpopen.md)<br/>
