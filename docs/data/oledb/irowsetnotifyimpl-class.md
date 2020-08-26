---
title: IRowsetNotifyImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL.IRowsetNotifyImpl
- ATL::IRowsetNotifyImpl
- IRowsetNotifyImpl
- IRowsetNotifyImpl.OnFieldChange
- IRowsetNotifyImpl::OnFieldChange
- OnFieldChange
- IRowsetNotifyImpl::OnRowChange
- IRowsetNotifyImpl.OnRowChange
- OnRowChange
- OnRowsetChange
- IRowsetNotifyImpl::OnRowsetChange
- IRowsetNotifyImpl.OnRowsetChange
helpviewer_keywords:
- IRowsetNotifyImpl class
- OnFieldChange method
- OnRowChange method
- OnRowsetChange method
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
ms.openlocfilehash: f938d9e92bc2f447ecfa82f2bfb27c8fda7652ab
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845106"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl-Klasse

Implementiert und registriert [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) für den Consumer (auch als "Sink" bezeichnet), sodass Benachrichtigungen verarbeitet werden können.

## <a name="syntax"></a>Syntax

```cpp
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

| Name | Beschreibung |
|-|-|
|[OnFieldChange](#onfieldchange)|Benachrichtigt den Consumer über alle Änderungen am Wert einer Spalte.|
|[OnRowChange](#onrowchange)|Benachrichtigt den Consumer über die erste Änderung an einer Zeile oder über jede Änderung, die Auswirkungen auf die ganze Zeile hat.|
|[OnRowsetChange](#onrowsetchange)|Benachrichtigt den Consumer über alle Änderungen, die Auswirkungen auf das gesamte Rowset haben.|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [empfangen von Benachrichtigungen](../../data/oledb/receiving-notifications.md) zum Implementieren der Verbindungspunkt Schnittstelle für den Consumer.

`IRowsetNotifyImpl` stellt eine Pseudo Implementierung für `IRowsetNotify` mit leeren Funktionen für die `IRowsetNotify` Methoden [OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)), [OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85))und [OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85))bereit. Wenn Sie von dieser Klasse erben, wenn Sie eine `IRowsetNotify` Schnittstelle implementieren, können Sie nur die benötigten Methoden implementieren. Außerdem müssen Sie für die anderen Methoden selbst leere Implementierungen bereitstellen.

## <a name="irowsetnotifyimplonfieldchange"></a><a name="onfieldchange"></a> IRowsetNotifyImpl:: OnFieldChange

Benachrichtigt den Consumer über alle Änderungen am Wert einer Spalte.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(OnFieldChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ HROW /* hRow */,
/* [in] */ DBORDINAL /* cColumns */,
/* [size_is][in] */ DBORDINAL /* rgColumns */ [] ,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IRowsetNotify:: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) für Parameter Beschreibungen.

### <a name="return-value"></a>Rückgabewert

Weitere Beschreibungen von Rückgabe Werten finden Sie unter [IRowsetNotify:: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) .

### <a name="remarks"></a>Bemerkungen

Diese Methode umschließt die [IRowsetNotify:: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) -Methode. Weitere Informationen finden Sie in der Beschreibung der Methode in der OLE DB Programmierer-Referenz.

## <a name="irowsetnotifyimplonrowchange"></a><a name="onrowchange"></a> IRowsetNotifyImpl:: OnRowChange

Benachrichtigt den Consumer über die erste Änderung an einer Zeile oder über jede Änderung, die Auswirkungen auf die ganze Zeile hat.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(OnRowChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ DBCOUNTITEM /* cRows */,
/* [size_is][in] */ const HROW /* rghRows*/ [] ,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IRowsetNotify:: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) für Parameter Beschreibungen.

### <a name="return-value"></a>Rückgabewert

Weitere Beschreibungen von Rückgabe Werten finden Sie unter [IRowsetNotify:: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) .

### <a name="remarks"></a>Bemerkungen

Diese Methode umschließt die [IRowsetNotify:: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) -Methode. Weitere Informationen finden Sie in der Beschreibung der Methode in der OLE DB Programmierer-Referenz.

## <a name="irowsetnotifyimplonrowsetchange"></a><a name="onrowsetchange"></a> IRowsetNotifyImpl:: OnRowsetChange

Benachrichtigt den Consumer über alle Änderungen, die Auswirkungen auf das gesamte Rowset haben.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(OnRowsetChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IRowsetNotify:: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) für Parameter Beschreibungen.

### <a name="return-value"></a>Rückgabewert

Informationen zu Rückgabewert Beschreibungen finden Sie unter [IRowsetNotify:: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) .

### <a name="remarks"></a>Bemerkungen

Diese Methode [umschließt die IRowsetNotify:: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) -Methode. Weitere Informationen finden Sie in der Beschreibung der Methode in der OLE DB Programmierer-Referenz.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) 
 [IRowsetNotifyCP-Klasse](../../data/oledb/irowsetnotifycp-class.md)
