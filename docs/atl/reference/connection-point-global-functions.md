---
title: Globale Funktionen des Verbindungspunkts
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
ms.openlocfilehash: 6474297f8b9adf04541f7d232fb88d5e52d4e88c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331535"
---
# <a name="connection-point-global-functions"></a>Globale Funktionen des Verbindungspunkts

Diese Funktionen bieten Unterstützung für Verbindungspunkte und Senkenzuordnungen.

> [!IMPORTANT]
> Die in der folgenden Tabelle aufgeführten Funktionen können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|||
|-|-|
|[AtlAdvise](#atladvise)|Erstellt eine Verbindung zwischen dem Verbindungspunkt eines Objekts und der Senke eines Clients.|
|[AtlUnadvise](#atlunadvise)|Beendet die über `AtlAdvise`hergestellte Verbindung .|
|[AtlAdviseSinkMap](#atladvisesinkmap)|Berät oder rät zu Einträgen in einer Event-Sink-Karte.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="atladvise"></a><a name="atladvise"></a>AtlAdvise

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

*pUnkCP*<br/>
[in] Ein Zeiger auf `IUnknown` das Objekt, mit dem der Client eine Verbindung herstellen möchte.

*Punk*<br/>
[in] Ein Zeiger auf die `IUnknown`des Clients .

*Iid*<br/>
[in] Die GUID des Verbindungspunkts. In der Regel entspricht dies der ausgehenden Schnittstelle, die vom Verbindungspunkt verwaltet wird.

*Pdw*<br/>
[out] Ein Zeiger auf das Cookie, das die Verbindung eindeutig identifiziert.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die Senke implementiert die ausgehende Schnittstelle, die vom Verbindungspunkt unterstützt wird. Der Client verwendet das *pdw-Cookie,* um die Verbindung zu entfernen, indem er sie an [AtlUnadvise](#atlunadvise)weitergibt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

## <a name="atlunadvise"></a><a name="atlunadvise"></a>AtlUnadvise

Beendet die über [AtlAdvise](#atladvise)hergestellte Verbindung .

> [!IMPORTANT]
> Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>Parameter

*pUnkCP*<br/>
[in] Ein Zeiger auf `IUnknown` das Objekt, mit dem der Client verbunden ist.

*Iid*<br/>
[in] Die GUID des Verbindungspunkts. In der Regel entspricht dies der ausgehenden Schnittstelle, die vom Verbindungspunkt verwaltet wird.

*dw*<br/>
[in] Das Cookie, das die Verbindung eindeutig identifiziert.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

## <a name="atladvisesinkmap"></a><a name="atladvisesinkmap"></a>AtlAdviseSinkMap

Mit dieser Funktion melden Sie alle Einträge in der Senkereigniszuordnung des Objekts an oder ab.

> [!IMPORTANT]
> Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>Parameter

*Pt*<br/>
[in] Ein Zeiger auf das Objekt, das die Senkenzuordnung enthält.

*bAdvise*<br/>
[in] TRUE, wenn alle Senkeneinträge zu benachmlassen sind; FALSE, wenn alle Senkeneinträge nicht empfohlen werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>Siehe auch

[Functions](../../atl/reference/atl-functions.md)<br/>
[Verbindungspunktmakros](../../atl/reference/connection-point-macros.md)
