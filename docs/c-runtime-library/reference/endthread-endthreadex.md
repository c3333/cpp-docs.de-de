---
title: _endthread, _endthreadex
ms.date: 4/2/2020
api_name:
- _endthread
- _endthreadex
- _o__endthread
- _o__endthreadex
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _endthread
- endthreadex
- _endthreadex
- endthread
helpviewer_keywords:
- _endthread function
- endthread function
- terminating threads
- endthreadex function
- _endthreadex function
- threading [C++], terminating threads
ms.assetid: 18a91f2f-659e-40b4-b266-ec12dcf2abf5
ms.openlocfilehash: a3889adcc90bd62e766102b72aae68577915e55b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915084"
---
# <a name="_endthread-_endthreadex"></a>_endthread, _endthreadex

Beendet einen Thread. **_endthread** beendet einen Thread, der von **_beginthread** erstellt wurde, und **_endthreadex** beendet einen von **_beginthreadex**erstellten Thread.

## <a name="syntax"></a>Syntax

```C
void _endthread( void );
void _endthreadex(
   unsigned retval
);
```

### <a name="parameters"></a>Parameter

*retval*<br/>
Threadexitcode.

## <a name="remarks"></a>Hinweise

Sie können **_endthread** oder explizit **_endthreadex** zum Beenden eines Threads abrufen. **_endthread** oder **_endthreadex** wird jedoch automatisch aufgerufen, wenn der Thread aus der als Parameter an **_beginthread** oder **_beginthreadex**übergebenen Routine zurückgegeben wird. Wenn Sie einen Thread mit einem- **Endpunkt** **_endthreadex** oder einem-Endpunkt beenden, können Sie sicherstellen, dass für den Thread zugewiesene Ressourcen ordnungsgemäß wieder hergestellt werden

> [!NOTE]
> Rufen Sie für eine mit „Libcmt.lib“ verknüpfte ausführbare Datei die [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) -Win32-API nicht auf, damit das Laufzeitsystem nicht an der Freigabe von zugeordneten Ressourcen gehindert wird. **_endthread** und **_endthreadex** zugeordnete Thread Ressourcen freizugeben und dann **ExitThread**aufzurufen.

**_endthread** schließt das Thread Handle automatisch. (Dieses Verhalten unterscheidet sich von der Win32- **ExitThread** -API.) Wenn Sie **_beginthread** und **_endthread**verwenden, schließen Sie das Thread handle daher nicht explizit, indem Sie die Win32- [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) -API aufrufen.

Wie die Win32- **ExitThread** -API schließt **_endthreadex** nicht das Thread handle. Wenn Sie **_beginthreadex** und **_endthreadex**verwenden, müssen Sie daher das Thread handle schließen, indem Sie die Win32- **CloseHandle** -API aufrufen.

> [!NOTE]
> **_endthread** und **_endthreadex** führen dazu, dass im Thread ausstehende C++-de-dektoren nicht aufgerufen werden.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**_endthread**|\<process.h>|
|**_endthreadex**|\<process.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Nur Multithread-Versionen von [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [_beginthread](beginthread-beginthreadex.md).

## <a name="see-also"></a>Weitere Informationen

[Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
