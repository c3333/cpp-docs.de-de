---
title: Iworkerthreadclient-Schnittstelle
ms.date: 11/04/2016
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
ms.openlocfilehash: aa72f090a006d6936339582a919b0faf5cab6b03
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835349"
---
# <a name="iworkerthreadclient-interface"></a>Iworkerthreadclient-Schnittstelle

`IWorkerThreadClient` ist die Schnittstelle, die von Clients der [CWorkerThread](../../atl/reference/cworkerthread-class.md) -Klasse implementiert wird.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
__interface IWorkerThreadClient
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|Name|Beschreibung|
|-|-|
|[CloseHandle](#closehandle)|Implementieren Sie diese Methode, um das Handle zu schließen, das diesem Objekt zugeordnet ist.|
|[Ausführen](#execute)|Implementieren Sie diese Methode, um Code auszuführen, wenn das Handle, das diesem Objekt zugeordnet ist, signalisiert wird.|

## <a name="remarks"></a>Bemerkungen

Implementieren Sie diese Schnittstelle, wenn Sie über Code verfügen, der als Reaktion auf ein zu signalisierendes Handle auf einem Arbeits Thread ausgeführt werden muss.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlutil. h

## <a name="iworkerthreadclientclosehandle"></a><a name="closehandle"></a> Iworkerthreadclient:: CloseHandle

Implementieren Sie diese Methode, um das Handle zu schließen, das diesem Objekt zugeordnet ist.

```
HRESULT CloseHandle(HANDLE  hHandle);
```

### <a name="parameters"></a>Parameter

*hHandle*<br/>
Das Handle, das geschlossen werden soll.

### <a name="return-value"></a>Rückgabewert

Rückgabe S_OK bei Erfolg oder ein Fehler HRESULT bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Das an diese Methode über gegebene Handle wurde diesem-Objekt zuvor durch einen [CWorkerThread:: addhandle](../../atl/reference/cworkerthread-class.md#addhandle)-Befehl zugeordnet.

### <a name="example"></a>Beispiel

Der folgende Code zeigt eine einfache Implementierung von `IWorkerThreadClient::CloseHandle` .

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]

## <a name="iworkerthreadclientexecute"></a><a name="execute"></a> Iworkerthreadclient:: Execute

Implementieren Sie diese Methode, um Code auszuführen, wenn das Handle, das diesem Objekt zugeordnet ist, signalisiert wird.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Parameter

*dwparam*<br/>
Der Benutzerparameter.

*hobject*<br/>
Das Handle, das signalisiert wurde.

### <a name="return-value"></a>Rückgabewert

Rückgabe S_OK bei Erfolg oder ein Fehler HRESULT bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Das Handle und der DWORD/Zeiger, die an diese Methode übergeben wurden, wurden diesem-Objekt zuvor durch einen [CWorkerThread:: addhandle](../../atl/reference/cworkerthread-class.md#addhandle)-Befehl zugeordnet.

### <a name="example"></a>Beispiel

Der folgende Code zeigt eine einfache Implementierung von `IWorkerThreadClient::Execute` .

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../atl/reference/atl-classes.md)<br/>
[CWorkerThread-Klasse](../../atl/reference/cworkerthread-class.md)
