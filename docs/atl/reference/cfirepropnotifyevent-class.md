---
title: CFirePropNotifyEvent-Klasse
ms.date: 11/04/2016
f1_keywords:
- CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnChanged
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnRequestEdit
helpviewer_keywords:
- sinks, notifying of ATL events
- CFirePropNotifyEvent class
- connection points [C++], notifying of events
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
ms.openlocfilehash: 1dfce42176341d74ffc7d9b42f856e71b17bf4f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326969"
---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent-Klasse

Diese Klasse stellt Methoden zum Benachrichtigen der Senke des Containers über Steuerelementeigenschaftsänderungen bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CFirePropNotifyEvent
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CfirePropnotifyEvent::FireOnChanged](#fireonchanged)|(Statisch) Benachrichtigt die Senke des Containers, dass sich eine Steuerelementeigenschaft geändert hat.|
|[CfirePropnotifyEvent::FireonRequestBearbeiten](#fireonrequestedit)|(Statisch) Benachrichtigt die Senke des Containers, dass sich eine Steuerelementeigenschaft ändern wird.|

## <a name="remarks"></a>Bemerkungen

`CFirePropNotifyEvent`verfügt über zwei Methoden, die die Senke des Containers benachrichtigen, dass sich eine Steuerelementeigenschaft geändert hat oder sich ändern wird.

Wenn die Klasse, die `IPropertyNotifySink`Ihr `CFirePropNotifyEvent` Steuerelement implementiert, von `FireOnRequestEdit` abgeleitet `FireOnChanged`ist, werden die Methoden aufgerufen, wenn Sie aufrufen oder . Wenn Ihre Steuerelementklasse nicht `IPropertyNotifySink`von abgeleitet ist, geben Aufrufe dieser Funktionen S_OK zurück.

Weitere Informationen zum Erstellen von Steuerelementen finden Sie im [ATL-Tutorial](../../atl/active-template-library-atl-tutorial.md).

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlctl.h

## <a name="cfirepropnotifyeventfireonchanged"></a><a name="fireonchanged"></a>CfirePropnotifyEvent::FireOnChanged

Benachrichtigt alle verbundenen [IPropertyNotifySink-Schnittstellen](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) (auf jedem Verbindungspunkt des Objekts), dass die angegebene Objekteigenschaft geändert wurde.

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parameter

*Punk*<br/>
[in] Zeigen Sie `IUnknown` auf die des Objekts, das die Benachrichtigung sendet.

*Dispid*<br/>
[in] Bezeichner der eigenschaft, die geändert wurde.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

Diese Funktion kann auch dann sicher aufzurufen sein, wenn Ihr Steuerelement keine Verbindungspunkte unterstützt.

## <a name="cfirepropnotifyeventfireonrequestedit"></a><a name="fireonrequestedit"></a>CfirePropnotifyEvent::FireonRequestBearbeiten

Benachrichtigt alle verbundenen [IPropertyNotifySink-Schnittstellen](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) (auf jedem Verbindungspunkt des Objekts), dass sich die angegebene Objekteigenschaft ändern wird.

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parameter

*Punk*<br/>
[in] Zeigen Sie `IUnknown` auf die des Objekts, das die Benachrichtigung sendet.

*Dispid*<br/>
[in] Bezeichner der Eigenschaft, die sich ändern soll.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

Diese Funktion kann auch dann sicher aufzurufen sein, wenn Ihr Steuerelement keine Verbindungspunkte unterstützt.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
