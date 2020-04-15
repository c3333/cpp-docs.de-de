---
title: CComControl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComControl
- ATLCTL/ATL::CComControl
- ATLCTL/ATL::CComControl::CComControl
- ATLCTL/ATL::CComControl::ControlQueryInterface
- ATLCTL/ATL::CComControl::CreateControlWindow
- ATLCTL/ATL::CComControl::FireOnChanged
- ATLCTL/ATL::CComControl::FireOnRequestEdit
- ATLCTL/ATL::CComControl::MessageBox
helpviewer_keywords:
- control flags
- CComControlBase class, CComControl class
- stock properties, ATL
- CComControl class
- controls [ATL], control helper functions
- ambient properties
- controls [ATL], properties
ms.assetid: 55368c27-bd16-45a7-b701-edb36157c8e8
ms.openlocfilehash: 3518de3596748fa284c1f898b69d1576903e9510
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320767"
---
# <a name="ccomcontrol-class"></a>CComControl-Klasse

Diese Klasse stellt Methoden zum Erstellen und Verwalten von ATL-Steuerelementen bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <class T, class WinBase = CWindowImpl<T>>
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Die Klasse, die das Steuerelement implementiert.

*WinBase*<br/>
Die Basisklasse, die Fensterfunktionen implementiert. Standardwerte für [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComControl::CComControl](#ccomcontrol)|Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComControl::ControlQueryInterface](#controlqueryinterface)|Ruft einen Zeiger auf die angeforderte Schnittstelle ab.|
|[CComControl::CreateControlWindow](#createcontrolwindow)|Erstellt ein Fenster für das Steuerelement.|
|[CComControl::FireOnChanged](#fireonchanged)|Benachrichtigt die Senke des Containers, dass sich eine Steuerelementeigenschaft geändert hat.|
|[CComControl::FireOnRequestBearbeiten](#fireonrequestedit)|Benachrichtigt die Senke des Containers, dass sich eine Steuerelementeigenschaft ändern wird und dass das Objekt die Senke fragt, wie sie vorgehen soll.|
|[CComControl::MessageBox](#messagebox)|Rufen Sie diese Methode auf, um ein Meldungsfeld zu erstellen, anzuzeigen und zu betreiben.|

## <a name="remarks"></a>Bemerkungen

`CComControl`ist eine Reihe nützlicher Steuerungshilfsfunktionen und wesentlicher Datenmember für ATL-Steuerelemente. Wenn Sie ein Standardsteuerelement oder ein DHTML-Steuerelement mithilfe des ATL-Steuerelement-Assistenten erstellen, leitet der Assistent Ihre Klasse automatisch von `CComControl`ab. `CComControl`leitet die meisten seiner Methoden von [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)ab.

Weitere Informationen zum Erstellen eines Steuerelements finden Sie im [ATL-Tutorial](../../atl/active-template-library-atl-tutorial.md). Weitere Informationen zum ATL-Projekt-Assistenten finden Sie im Artikel [Erstellen eines ATL-Projekts](../../atl/reference/creating-an-atl-project.md).

Eine Demonstration `CComControl` von Methoden und Datenmembern finden Sie im [CIRC-Beispiel.](../../overview/visual-cpp-samples.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

`CComControl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlctl.h

## <a name="ccomcontrolccomcontrol"></a><a name="ccomcontrol"></a>CComControl::CComControl

Der Konstruktor.

```
CComControl();
```

### <a name="remarks"></a>Bemerkungen

Ruft den [CComControlBase-Konstruktor](ccomcontrolbase-class.md#ccomcontrolbase) auf und übergibt das `m_hWnd` über [CWindowImpl](../../atl/reference/cwindowimpl-class.md)geerbte Datenelement.

## <a name="ccomcontrolcontrolqueryinterface"></a><a name="controlqueryinterface"></a>CComControl::ControlQueryInterface

Ruft einen Zeiger auf die angeforderte Schnittstelle ab.

```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
[in] Die GUID der angeforderten Schnittstelle.

*Ppv*<br/>
[out] Ein Zeiger auf den Schnittstellenzeiger, der von *iid*oder NULL identifiziert wird, wenn die Schnittstelle nicht gefunden wird.

### <a name="remarks"></a>Bemerkungen

Behandelt nur Schnittstellen in der COM-Map-Tabelle.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]

## <a name="ccomcontrolcreatecontrolwindow"></a><a name="createcontrolwindow"></a>CComControl::CreateControlWindow

Erstellt standardmäßig ein Fenster für das `CWindowImpl::Create`Steuerelement, indem aufgerufen wird.

```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```

### <a name="parameters"></a>Parameter

*hWndEltern*<br/>
[in] Behandeln Sie das übergeordnete oder Besitzerfenster. Es muss ein gültiges Fensterhandle angegeben werden. Das Steuerelementfenster ist auf den Bereich des übergeordneten Fensters beschränkt.

*rcPos*<br/>
[in] Die Anfangsgröße und Position des zu erstellenden Fensters.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, wenn Sie etwas anderes tun möchten, als ein einzelnes Fenster zu erstellen, z. B. um zwei Fenster zu erstellen, von denen eines zu einer Symbolleiste für ihr Steuerelement wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]

## <a name="ccomcontrolfireonchanged"></a><a name="fireonchanged"></a>CComControl::FireOnChanged

Benachrichtigt die Senke des Containers, dass sich eine Steuerelementeigenschaft geändert hat.

```
HRESULT FireOnChanged(DISPID dispID);
```

### <a name="parameters"></a>Parameter

*Dispid*<br/>
[in] Bezeichner der eigenschaft, die geändert wurde.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

Wenn Ihre Steuerelementklasse von [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)abstammt, ruft diese Methode [CFirePropNotifyEvent::FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged) auf, um alle verbundenen `IPropertyNotifySink` Schnittstellen zu benachrichtigen, dass die angegebene Steuerelementeigenschaft geändert wurde. Wenn Ihre Steuerelementklasse nicht `IPropertyNotifySink`von ableitet, gibt diese Methode S_OK zurück.

Diese Methode kann auch dann aufzurufen, wenn ihr Steuerelement keine Verbindungspunkte unterstützt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]

## <a name="ccomcontrolfireonrequestedit"></a><a name="fireonrequestedit"></a>CComControl::FireOnRequestBearbeiten

Benachrichtigt die Senke des Containers, dass sich eine Steuerelementeigenschaft ändern wird und dass das Objekt die Senke fragt, wie sie vorgehen soll.

```
HRESULT FireOnRequestEdit(DISPID dispID);
```

### <a name="parameters"></a>Parameter

*Dispid*<br/>
[in] Bezeichner der Eigenschaft, die sich ändern soll.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

Wenn Ihre Steuerelementklasse von [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)ableitet, ruft diese Methode [CFirePropNotifyEvent::FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit) auf, um alle verbundenen `IPropertyNotifySink` Schnittstellen zu benachrichtigen, dass die angegebene Steuerelementeigenschaft geändert werden soll. Wenn Ihre Steuerelementklasse nicht `IPropertyNotifySink`von ableitet, gibt diese Methode S_OK zurück.

Diese Methode kann auch dann aufzurufen, wenn ihr Steuerelement keine Verbindungspunkte unterstützt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]

## <a name="ccomcontrolmessagebox"></a><a name="messagebox"></a>CComControl::MessageBox

Rufen Sie diese Methode auf, um ein Meldungsfeld zu erstellen, anzuzeigen und zu betreiben.

```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
Der Text, der im Meldungsfeld angezeigt werden soll.

*lpszCaption*<br/>
Der Dialogfeldtitel. Wenn NULL (Standard), wird der Titel "Error" verwendet.

*nType*<br/>
Gibt den Inhalt und das Verhalten des Dialogfelds an. Eine Liste der verschiedenen verfügbaren Meldungsfelder finden Sie im [MessageBox-Eintrag](/windows/win32/api/winuser/nf-winuser-messagebox) in der Windows SDK-Dokumentation. Die Standardeinstellung bietet eine einfache **OK-Schaltfläche.**

### <a name="return-value"></a>Rückgabewert

Gibt einen Ganzzahlwert zurück, der einen der unter [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) in der Windows SDK-Dokumentation aufgeführten Menüelementwerte angibt.

### <a name="remarks"></a>Bemerkungen

`MessageBox`ist sowohl während der Entwicklung als auch als einfache Möglichkeit zum Anzeigen eines Fehlers oder einer Warnmeldung für den Benutzer nützlich.

## <a name="see-also"></a>Siehe auch

[CWindowImpl-Klasse](../../atl/reference/cwindowimpl-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[CComControlBase-Klasse](../../atl/reference/ccomcontrolbase-class.md)<br/>
[CComCompositeControl-Klasse](../../atl/reference/ccomcompositecontrol-class.md)
