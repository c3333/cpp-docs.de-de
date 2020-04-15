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
ms.openlocfilehash: e4b90534fa89ef2aeffe4cd682d92efc16452487
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326358"
---
# <a name="ithreadpoolconfig-interface"></a>IThreadPoolConfig-Schnittstelle

Diese Schnittstelle stellt Methoden zum Konfigurieren eines Threadpools bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[GetSize](#getsize)|Rufen Sie diese Methode auf, um die Anzahl der Threads im Pool abzurufen.|
|[GetTimeout](#gettimeout)|Rufen Sie diese Methode auf, um die maximale Zeit in Millisekunden abzurufen, die der Threadpool auf das Herunterfahren eines Threads wartet.|
|[Setsize](#setsize)|Rufen Sie diese Methode auf, um die Anzahl der Threads im Pool festzulegen.|
|[Settimeout](#settimeout)|Rufen Sie diese Methode auf, um die maximale Zeit in Millisekunden festzulegen, die der Threadpool auf das Herunterfahren eines Threads wartet.|

## <a name="remarks"></a>Bemerkungen

Diese Schnittstelle wird von [CThreadPool](../../atl/reference/cthreadpool-class.md)implementiert.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlutil.h

## <a name="ithreadpoolconfiggetsize"></a><a name="getsize"></a>IThreadPoolConfig::GetSize

Rufen Sie diese Methode auf, um die Anzahl der Threads im Pool abzurufen.

```
STDMETHOD(GetSize)(int* pnNumThreads);
```

### <a name="parameters"></a>Parameter

*pnNumThreads*<br/>
[out] Adresse der Variablen, die bei Erfolg die Anzahl der Threads im Pool empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]

## <a name="ithreadpoolconfiggettimeout"></a><a name="gettimeout"></a>IThreadPoolConfig::GetTimeout

Rufen Sie diese Methode auf, um die maximale Zeit in Millisekunden abzurufen, die der Threadpool auf das Herunterfahren eines Threads wartet.

```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```

### <a name="parameters"></a>Parameter

*pdwMaxWait*<br/>
[out] Adresse der Variablen, die bei Erfolg die maximale Zeit in Millisekunden erhält, die der Threadpool auf das Herunterfahren eines Threads wartet.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="example"></a>Beispiel

Siehe [IThreadPoolConfig::GetSize](#getsize).

## <a name="ithreadpoolconfigsetsize"></a><a name="setsize"></a>IThreadPoolConfig::SetSize

Rufen Sie diese Methode auf, um die Anzahl der Threads im Pool festzulegen.

```
STDMETHOD(SetSize)int nNumThreads);
```

### <a name="parameters"></a>Parameter

*nNumThreads*<br/>
Die angeforderte Anzahl von Threads im Pool.

Wenn *nNumThreads* negativ ist, wird der absolute Wert mit der Anzahl der Prozessoren auf dem Computer multipliziert, um die Gesamtzahl der Threads abzubekommen.

Wenn *nNumThreads* Null ist, werden ATLS_DEFAULT_THREADSPERPROC mit der Anzahl der Prozessoren auf dem Computer multipliziert, um die Gesamtzahl der Threads abzubekommen.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="example"></a>Beispiel

Siehe [IThreadPoolConfig::GetSize](#getsize).

## <a name="ithreadpoolconfigsettimeout"></a><a name="settimeout"></a>IThreadPoolConfig::SetTimeout

Rufen Sie diese Methode auf, um die maximale Zeit in Millisekunden festzulegen, die der Threadpool auf das Herunterfahren eines Threads wartet.

```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```

### <a name="parameters"></a>Parameter

*dwMaxWait*<br/>
Die angeforderte maximale Zeit in Millisekunden, die der Threadpool wartet, bis ein Thread heruntergefahren wird.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="example"></a>Beispiel

Siehe [IThreadPoolConfig::GetSize](#getsize).

## <a name="see-also"></a>Siehe auch

[Klassen](../../atl/reference/atl-classes.md)<br/>
[CThreadPool-Klasse](../../atl/reference/cthreadpool-class.md)
