---
title: IRowsetNotifyCP-Klasse
ms.date: 11/04/2016
f1_keywords:
- IRowsetNotifyCP
- Fire_OnFieldChange
- ATL::IRowsetNotifyCP::Fire_OnFieldChange
- ATL.IRowsetNotifyCP.Fire_OnFieldChange
- IRowsetNotifyCP.Fire_OnFieldChange
- IRowsetNotifyCP::Fire_OnFieldChange
- IRowsetNotifyCP.Fire_OnRowChange
- ATL.IRowsetNotifyCP.Fire_OnRowChange
- Fire_OnRowChange
- ATL::IRowsetNotifyCP::Fire_OnRowChange
- IRowsetNotifyCP::Fire_OnRowChange
- Fire_OnRowsetChange
- IRowsetNotifyCP::Fire_OnRowsetChange
- IRowsetNotifyCP.Fire_OnRowsetChange
- ATL::IRowsetNotifyCP::Fire_OnRowsetChange
- ATL.IRowsetNotifyCP.Fire_OnRowsetChange
helpviewer_keywords:
- IRowsetNotifyCP class
- Fire_OnFieldChange method
- Fire_OnRowChange method
- Fire_OnRowsetChange method
ms.assetid: ccef402b-94a0-4c2e-9a13-7e854ef82390
ms.openlocfilehash: 481c2c0ec28972e9cef8d1103e49afa2037c2393
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544567"
---
# <a name="irowsetnotifycp-class"></a>IRowsetNotifyCP-Klasse

Implementiert die Anbieter Website für die Verbindungspunkt Schnittstelle [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)).

## <a name="syntax"></a>Syntax

```cpp
template <class T, class ReentrantEventSync = CComSharedMutex>
class IRowsetNotifyCP :
   public IConnectionPointImpl<
      T,
      piid = &__uuidof(IRowsetNotify),
      CComDynamicUnkArray DynamicUnkArray>,
   public ReentrantEventSync
```

### <a name="parameters"></a>Parameter

*T*<br/>
Eine von `IRowsetNotifyCP`abgeleitete Klasse.

*Reentranteventsync*<br/>
Eine Mutex-Klasse, die das erneute eintreten unterstützt (Standardwert ist `CComSharedMutex`). Bei einem Mutex handelt es sich um ein Synchronisierungs Objekt, das einem Thread den Zugriff auf eine Ressource gegenseitig ausschließt.

*piid*<br/>
Ein Schnittstellen-ID-Zeiger (`IID*`) für eine `IRowsetNotify` Verbindungspunkt-Schnittstelle. Standardwert: `&__uuidof(IRowsetNotify)`.

*Dynamicunkarray*<br/>
Ein Array vom Typ [ccomdynamicunkarray](../../atl/reference/ccomdynamicunkarray-class.md), bei dem es sich um ein dynamisch zugewiesenes Array von `IUnknown` Zeigern auf die clientsenke-Schnittstellen handelt.

## <a name="requirements"></a>Voraussetzungen

**Header:** atldb.h

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[Fire_OnFieldChange](#onfieldchange)|Benachrichtigt den Consumer über eine Änderung des Werts einer Spalte.|
|[Fire_OnRowChange](#onrowchange)|Benachrichtigt den Consumer über eine Änderung, die sich auf die Zeilen auswirkt.|
|[Fire_OnRowsetChange](#onrowsetchange)|Benachrichtigt den Consumer über eine Änderung, die sich auf das gesamte Rowset auswirkt.|

## <a name="remarks"></a>Hinweise

`IRowsetNotifyCP` implementiert Broadcast Funktionen, um Listener auf dem Verbindungspunkt `IID_IRowsetNotify` Änderungen am Inhalt des Rowsets zu informieren.

Beachten Sie, dass Sie mit [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) auch `IRowsetNotify` für den Consumer (auch als "Sink" bezeichnet) implementieren und registrieren müssen, damit der Consumer Benachrichtigungen verarbeiten kann. Weitere Informationen finden Sie unter [empfangen von Benachrichtigungen](../../data/oledb/receiving-notifications.md) zum Implementieren der Verbindungspunkt Schnittstelle für den Consumer.

Ausführliche Informationen zum Implementieren von Benachrichtigungen finden Sie unter "unterstützen von Benachrichtigungen" unter [Erstellen eines aktualisierbaren Anbieters](../../data/oledb/creating-an-updatable-provider.md).

## <a name="irowsetnotifycpfire_onfieldchange"></a><a name="onfieldchange"></a>IRowsetNotifyCP:: Fire_OnFieldChange

Überträgt ein [OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) -Ereignis, um Consumer über eine Änderung des Werts einer Spalte zu benachrichtigen.

### <a name="syntax"></a>Syntax

```cpp
HRESULT Fire_OnFieldChange(IRowset* pRowset,
   HROW hRow,
   DBORDINAL cColumns,
   DBORDINAL* rgColumns,
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IRowsetNotify:: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="irowsetnotifycpfire_onrowchange"></a><a name="onrowchange"></a>IRowsetNotifyCP:: Fire_OnRowChange

Überträgt ein [OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) -Ereignis an alle Listener auf dem Verbindungspunkt `IID_IRowsetNotify`, um Consumer über eine Änderung zu benachrichtigen, die sich auf die Zeilen auswirkt.

### <a name="syntax"></a>Syntax

```cpp
HRESULT Fire_OnRowChange(IRowset* pRowset,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IRowsetNotify:: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="irowsetnotifycpfire_onrowsetchange"></a><a name="onrowsetchange"></a>IRowsetNotifyCP:: Fire_OnRowsetChange

Überträgt ein [OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) -Ereignis an alle Listener auf dem Verbindungspunkt `IID_IRowsetNotify`, um Consumer über eine Änderung zu benachrichtigen, die das gesamte Rowset betrifft.

### <a name="syntax"></a>Syntax

```cpp
HRESULT Fire_OnRowsetChange(IRowset* pRowset,
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IRowsetNotify:: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="see-also"></a>Siehe auch

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Benachrichtigungen (com)](/windows/win32/com/notifications)<br/>
[BEGIN_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#begin_connection_point_map)<br/>
[END_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#end_connection_point_map)<br/>
[CONNECTION_POINT_ENTRY](../../atl/reference/connection-point-macros.md#connection_point_entry)<br/>
[Erstellen eines aktualisierbaren Anbieters](../../data/oledb/creating-an-updatable-provider.md)