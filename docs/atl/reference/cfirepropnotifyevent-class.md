---
title: Cfirepropnotimayevent-Klasse
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
ms.openlocfilehash: 694127ceccc1d1b55e5da9abca799dff77dcfc60
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864917"
---
# <a name="cfirepropnotifyevent-class"></a>Cfirepropnotimayevent-Klasse

Diese Klasse stellt Methoden zum Benachrichtigen der Senke des Containers bezüglich Änderungen an Steuerelement Eigenschaften bereit.

> [!IMPORTANT]
>  Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
class CFirePropNotifyEvent
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cfirepropnotischyevent:: fireonchanged](#fireonchanged)|Kum Benachrichtigt die Senke des Containers, dass sich eine Steuerelement Eigenschaft geändert hat.|
|[Cfirepropnotieyevent:: fireonrequestedit](#fireonrequestedit)|Kum Benachrichtigt die Senke des Containers, dass eine Steuerelement Eigenschaft gerade geändert wird.|

## <a name="remarks"></a>Bemerkungen

`CFirePropNotifyEvent` verfügt über zwei Methoden, die die Senke des Containers Benachrichtigen, dass eine Steuerelement Eigenschaft geändert wurde oder gerade geändert wird.

Wenn die Klasse, die das Steuerelement implementiert, von `IPropertyNotifySink`abgeleitet ist, werden die `CFirePropNotifyEvent` Methoden aufgerufen, wenn Sie `FireOnRequestEdit` oder `FireOnChanged`aufrufen. Wenn Ihre Steuerelement Klasse nicht von `IPropertyNotifySink`abgeleitet ist, geben Aufrufe dieser Funktionen S_OK zurück.

Weitere Informationen zum Erstellen von Steuerelementen finden Sie im [ATL-Tutorial](../../atl/active-template-library-atl-tutorial.md).

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlctl. h

##  <a name="fireonchanged"></a>Cfirepropnotischyevent:: fireonchanged

Benachrichtigt alle verbundenen [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) -Schnittstellen (auf jedem Verbindungspunkt des-Objekts), dass die angegebene Objekt Eigenschaft geändert wurde.

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parameter

*Kro*<br/>
in Zeiger auf den `IUnknown` des Objekts, das die Benachrichtigung sendet.

*dispID*<br/>
in Der Bezeichner der geänderten Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Einer der HRESULT-Standardwerte.

### <a name="remarks"></a>Bemerkungen

Diese Funktion kann auch dann aufgerufen werden, wenn das Steuerelement keine Verbindungspunkte unterstützt.

##  <a name="fireonrequestedit"></a>Cfirepropnotieyevent:: fireonrequestedit

Benachrichtigt alle verbundenen [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) -Schnittstellen (auf jedem Verbindungspunkt des-Objekts), die von der angegebenen Objekt Eigenschaft geändert werden.

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parameter

*Kro*<br/>
in Zeiger auf den `IUnknown` des Objekts, das die Benachrichtigung sendet.

*dispID*<br/>
in Der Bezeichner der Eigenschaft, die geändert werden soll.

### <a name="return-value"></a>Rückgabewert

Einer der HRESULT-Standardwerte.

### <a name="remarks"></a>Bemerkungen

Diese Funktion kann auch dann aufgerufen werden, wenn das Steuerelement keine Verbindungspunkte unterstützt.

## <a name="see-also"></a>Weitere Informationen

[Klassen Übersicht](../../atl/atl-class-overview.md)
