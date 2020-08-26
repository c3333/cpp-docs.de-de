---
title: IThreadPoolConfig-Schnittstelle
ms.date: 11/04/2016
f1_keywords:
- IThreadPoolConfig
- ATLUTIL/ATL::IThreadPoolConfig
- ATLUTIL/ATL::GetSize
- ATLUTIL/ATL::GetTimeout
- ATLUTIL/ATL::SetSize
- ATLUTIL/ATL::SetTimeout
helpviewer_keywords:
- IThreadPoolConfig interface
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
ms.openlocfilehash: cba82055c292fc966dc2328773cce4aa64d45a64
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835427"
---
# <a name="ithreadpoolconfig-interface"></a>IThreadPoolConfig-Schnittstelle

Diese Schnittstelle stellt Methoden zum Konfigurieren eines Thread Pools bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|Name|Beschreibung|
|-|-|
|[GetSize](#getsize)|Mit dieser Methode können Sie die Anzahl der Threads im Pool abrufen.|
|[GetTimeout](#gettimeout)|Mit dieser Methode können Sie die maximale Zeit in Millisekunden abrufen, die der Thread Pool darauf wartet, dass ein Thread heruntergefahren wird.|
|[SetSize](#setsize)|Mit dieser Methode können Sie die Anzahl der Threads im Pool festlegen.|
|[SetTimeout](#settimeout)|Mit dieser Methode können Sie die maximale Zeit in Millisekunden festlegen, die der Thread Pool darauf wartet, dass ein Thread heruntergefahren wird.|

## <a name="remarks"></a>Bemerkungen

Diese Schnittstelle wird von [CThreadPool](../../atl/reference/cthreadpool-class.md)implementiert.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlutil. h

## <a name="ithreadpoolconfiggetsize"></a><a name="getsize"></a> IThreadPoolConfig:: GetSize

Mit dieser Methode können Sie die Anzahl der Threads im Pool abrufen.

```
STDMETHOD(GetSize)(int* pnNumThreads);
```

### <a name="parameters"></a>Parameter

*pnnumthreads*<br/>
vorgenommen Adresse der Variablen, die bei Erfolg die Anzahl der Threads im Pool empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]

## <a name="ithreadpoolconfiggettimeout"></a><a name="gettimeout"></a> IThreadPoolConfig:: getTimeout

Mit dieser Methode können Sie die maximale Zeit in Millisekunden abrufen, die der Thread Pool darauf wartet, dass ein Thread heruntergefahren wird.

```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```

### <a name="parameters"></a>Parameter

*pdwmaxwait*<br/>
vorgenommen Die Adresse der Variablen, die bei Erfolg die maximale Zeit in Millisekunden empfängt, die der Thread Pool auf das Herunterfahren eines Threads wartet.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [IThreadPoolConfig:: GetSize](#getsize).

## <a name="ithreadpoolconfigsetsize"></a><a name="setsize"></a> IThreadPoolConfig:: SetSize

Mit dieser Methode können Sie die Anzahl der Threads im Pool festlegen.

```
STDMETHOD(SetSize)int nNumThreads);
```

### <a name="parameters"></a>Parameter

*nnumthreads*<br/>
Die angeforderte Anzahl von Threads im Pool.

Wenn *nnumthreads* negativ ist, wird der absolute Wert mit der Anzahl der Prozessoren auf dem Computer multipliziert, um die Gesamtzahl der Threads zu erhalten.

Wenn *nnumthreads* gleich 0 (null) ist, werden ATLS_DEFAULT_THREADSPERPROC mit der Anzahl der Prozessoren auf dem Computer multipliziert, um die Gesamtzahl der Threads zu erhalten.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [IThreadPoolConfig:: GetSize](#getsize).

## <a name="ithreadpoolconfigsettimeout"></a><a name="settimeout"></a> IThreadPoolConfig:: setTimeout

Mit dieser Methode können Sie die maximale Zeit in Millisekunden festlegen, die der Thread Pool darauf wartet, dass ein Thread heruntergefahren wird.

```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```

### <a name="parameters"></a>Parameter

*dwmaxwait*<br/>
Die angeforderte maximale Zeit in Millisekunden, die der Thread Pool darauf wartet, dass ein Thread heruntergefahren wird.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [IThreadPoolConfig:: GetSize](#getsize).

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../atl/reference/atl-classes.md)<br/>
[CThreadPool-Klasse](../../atl/reference/cthreadpool-class.md)
