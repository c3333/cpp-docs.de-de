---
title: IWorkerThreadClient-Schnittstelle
ms.date: 11/04/2016
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
ms.openlocfilehash: 6a68f25f153a0ad2cf42ebfaa374ff63c5746fcd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326301"
---
# <a name="iworkerthreadclient-interface"></a>IWorkerThreadClient-Schnittstelle

`IWorkerThreadClient`ist die Schnittstelle, die von Clients der [CWorkerThread-Klasse](../../atl/reference/cworkerthread-class.md) implementiert wird.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
__interface IWorkerThreadClient
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[Closehandle](#closehandle)|Implementieren Sie diese Methode, um das diesem Objekt zugeordnete Handle zu schließen.|
|[Ausführen](#execute)|Implementieren Sie diese Methode, um Code auszuführen, wenn das diesem Objekt zugeordnete Handle signalisiert wird.|

## <a name="remarks"></a>Bemerkungen

Implementieren Sie diese Schnittstelle, wenn Sie Code haben, der auf einem Arbeitsthread ausgeführt werden muss, als Reaktion auf ein gesignalisiertes Handle.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlutil.h

## <a name="iworkerthreadclientclosehandle"></a><a name="closehandle"></a>IWorkerThreadClient::CloseHandle

Implementieren Sie diese Methode, um das diesem Objekt zugeordnete Handle zu schließen.

```
HRESULT CloseHandle(HANDLE  hHandle);
```

### <a name="parameters"></a>Parameter

*hHandle*<br/>
Der zu schließende Griff.

### <a name="return-value"></a>Rückgabewert

Geben Sie S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Das an diese Methode übergebene Handle wurde diesem Objekt zuvor durch einen Aufruf von [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)zugeordnet.

### <a name="example"></a>Beispiel

Der folgende Code zeigt `IWorkerThreadClient::CloseHandle`eine einfache Implementierung von .

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]

## <a name="iworkerthreadclientexecute"></a><a name="execute"></a>IWorkerThreadClient::Ausführen

Implementieren Sie diese Methode, um Code auszuführen, wenn das diesem Objekt zugeordnete Handle signalisiert wird.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Parameter

*dwParam*<br/>
Der Benutzerparameter.

*hObject*<br/>
Der Griff, der signalisiert wurde.

### <a name="return-value"></a>Rückgabewert

Geben Sie S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Das handle und der DWORD/Pointer, der an diese Methode übergeben wurde, wurden diesem Objekt zuvor durch einen Aufruf von [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)zugeordnet.

### <a name="example"></a>Beispiel

Der folgende Code zeigt `IWorkerThreadClient::Execute`eine einfache Implementierung von .

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]

## <a name="see-also"></a>Siehe auch

[Klassen](../../atl/reference/atl-classes.md)<br/>
[CWorkerThread-Klasse](../../atl/reference/cworkerthread-class.md)
