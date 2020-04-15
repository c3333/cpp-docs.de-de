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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: c76f479255080400e07678ef5dbde572b7a9dffc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348036"
---
# <a name="_endthread-_endthreadex"></a>_endthread, _endthreadex

Beendet einen Thread; **_endthread** einen Thread beendet, **der** von _beginthread erstellt wird, und **beendet _endthreadex** einen Thread, der von **_beginthreadex**erstellt wird.

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

## <a name="remarks"></a>Bemerkungen

Sie können **_endthread** aufrufen oder **_endthreadex** explizit aufrufen, um einen Thread zu beenden. **_endthread** oder **_endthreadex** wird jedoch automatisch aufgerufen, wenn der Thread von der als Parameter übergebenen Routine an **_beginthread** oder **_beginthreadex**zurückgibt. Das Beenden eines Threads mit einem Aufruf von **Endthread** oder **_endthreadex** trägt dazu bei, die ordnungsgemäße Wiederherstellung der für den Thread zugewiesenen Ressourcen sicherzustellen.

> [!NOTE]
> Rufen Sie für eine mit „Libcmt.lib“ verknüpfte ausführbare Datei die [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) -Win32-API nicht auf, damit das Laufzeitsystem nicht an der Freigabe von zugeordneten Ressourcen gehindert wird. **_endthread** und **_endthreadex** zugeordnete Threadressourcen zurückfordern und dann **ExitThread**aufrufen.

**_endthread** schließt den Gewindegriff automatisch. (Dieses Verhalten unterscheidet sich von **ExitThread** der Win32 ExitThread-API.) Wenn Sie **_beginthread** und **_endthread**verwenden, schließen Sie das Threadhandle daher nicht explizit, indem Sie die Win32 [CloseHandle-API](/windows/win32/api/handleapi/nf-handleapi-closehandle) aufrufen.

Wie die Win32 **ExitThread-API** schließt **_endthreadex** das Threadhandle nicht. Wenn Sie **_beginthreadex** und **_endthreadex**verwenden, müssen Sie daher das Threadhandle schließen, indem Sie die Win32 **CloseHandle-API** aufrufen.

> [!NOTE]
> **_endthread** und **_endthreadex** dazu führen, dass im Thread ausstehende C++-Destruktoren nicht aufgerufen werden.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Siehe auch

[Prozess- und Umweltkontrolle](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
