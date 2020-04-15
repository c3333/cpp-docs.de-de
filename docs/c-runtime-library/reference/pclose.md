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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: c66a749d6aeb74fdc677b2d6088e1b5093f3570b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338524"
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

*Stream*<br/>
Rückgabewert vom vorherigen Aufruf an **_popen**.

## <a name="return-value"></a>Rückgabewert

Gibt den Beendigungsstatus des beendenden Befehlsprozessors zurück, oder -1, wenn ein Fehler auftritt. Das Format des Rückgabewerts ist das gleiche wie für **_cwait**, mit Ausnahme der Bytes niedriger Ordnung und hoher Ordnung, die ausgetauscht werden. Wenn Stream **NULL**ist, **setzt _pclose** **errno** auf **EINVAL** und gibt -1 zurück.

Weitere Informationen über diese und andere Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **_pclose-Funktion** sucht die Prozess-ID des Befehlsprozessors (Cmd.exe), der vom zugeordneten **_popen-Aufruf** gestartet wurde, führt einen [_cwait](cwait.md) Aufruf des neuen Befehlsprozessors aus und schließt den Stream auf der zugeordneten Pipe.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_pclose**|\<stdio.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Siehe auch

[Prozess- und Umweltkontrolle](../../c-runtime-library/process-and-environment-control.md)<br/>
[_pipe](pipe.md)<br/>
[_popen, _wpopen](popen-wpopen.md)<br/>
