---
title: Globale Funktionen von Verbindungs Punkten
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
ms.openlocfilehash: 1a648f49b0f3715fd322b1099dcebbf194f57a10
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833529"
---
# <a name="connection-point-global-functions"></a>Globale Funktionen von Verbindungs Punkten

Diese Funktionen bieten Unterstützung für Verbindungspunkte und senkenzuordnungen.

> [!IMPORTANT]
> Die in der folgenden Tabelle aufgeführten Funktionen können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|Funktion|Beschreibung|
|-|-|
|[AtlAdvise](#atladvise)|Erstellt eine Verbindung zwischen dem Verbindungspunkt eines Objekts und der Senke eines Clients.|
|[AtlUnadvise](#atlunadvise)|Beendet die Verbindung, die durch hergestellt wurde `AtlAdvise` .|
|[AtlAdviseSinkMap](#atladvisesinkmap)|Benachrichtigt oder benachrichtigt Einträge in einer Ereignis Senke-Zuordnung.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="atladvise"></a><a name="atladvise"></a> AtlAdvise

Erstellt eine Verbindung zwischen dem Verbindungspunkt eines Objekts und der Senke eines Clients.

> [!IMPORTANT]
> Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```

### <a name="parameters"></a>Parameter

*punkcp*<br/>
in Ein Zeiger auf den `IUnknown` des Objekts, mit dem der Client eine Verbindung herstellen möchte.

*Kro*<br/>
in Ein Zeiger auf den des Clients `IUnknown` .

*IID*<br/>
in Die GUID des Verbindungs Punkts. In der Regel ist dies identisch mit der ausgehenden Schnittstelle, die vom Verbindungspunkt verwaltet wird.

*PDW*<br/>
vorgenommen Ein Zeiger auf das Cookie, das die Verbindung eindeutig identifiziert.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Bemerkungen

Die Senke implementiert die ausgehende Schnittstelle, die vom Verbindungspunkt unterstützt wird. Der Client verwendet das *PDW* -Cookie, um die Verbindung zu entfernen, indem Sie Sie an [atlunrat](#atlunadvise)übergibt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

## <a name="atlunadvise"></a><a name="atlunadvise"></a> Atlunrat

Beendet die Verbindung, die durch [AtlAdvise](#atladvise)hergestellt wurde.

> [!IMPORTANT]
> Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>Parameter

*punkcp*<br/>
in Ein Zeiger auf den `IUnknown` des Objekts, mit dem der Client verbunden ist.

*IID*<br/>
in Die GUID des Verbindungs Punkts. In der Regel ist dies identisch mit der ausgehenden Schnittstelle, die vom Verbindungspunkt verwaltet wird.

*dw*<br/>
in Das Cookie, das die Verbindung eindeutig identifiziert.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

## <a name="atladvisesinkmap"></a><a name="atladvisesinkmap"></a> Atladvisesinkmap

Mit dieser Funktion melden Sie alle Einträge in der Senkereigniszuordnung des Objekts an oder ab.

> [!IMPORTANT]
> Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>Parameter

*PT*<br/>
in Ein Zeiger auf das-Objekt, das die senkmap enthält.

*bEmpfehlung*<br/>
in TRUE, wenn alle Senke-Einträge empfohlen werden. FALSE, wenn alle Senke-Einträge nicht empfohlen werden.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>Siehe auch

[Funktionen](../../atl/reference/atl-functions.md)<br/>
[Verbindungspunkt Makros](../../atl/reference/connection-point-macros.md)
