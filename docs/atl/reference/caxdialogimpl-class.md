---
title: CAxDialogImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl::AdviseSinkMap
- ATLWIN/ATL::CAxDialogImpl::Create
- ATLWIN/ATL::CAxDialogImpl::DestroyWindow
- ATLWIN/ATL::CAxDialogImpl::DoModal
- ATLWIN/ATL::CAxDialogImpl::EndDialog
- ATLWIN/ATL::CAxDialogImpl::GetDialogProc
- ATLWIN/ATL::CAxDialogImpl::GetIDD
- ATLWIN/ATL::CAxDialogImpl::IsDialogMessage
- ATLWIN/ATL::CAxDialogImpl::m_bModal
helpviewer_keywords:
- CAxDialogImpl class
- ATL, dialog boxes
ms.assetid: 817df483-3fa8-44e7-8487-72ba0881cd27
ms.openlocfilehash: d8e60a817d197f67c14318a7d50ddf796e570142
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318741"
---
# <a name="caxdialogimpl-class"></a>CAxDialogImpl-Klasse

Diese Klasse implementiert ein Dialogfeld (modal oder moduslos), das ActiveX-Steuerelemente hostet.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <class T, class TBase = CWindow>
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `CAxDialogImpl`abgeleitet von .

*TBase*<br/>
Die Basisfensterklasse `CDialogImplBaseT`für .

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAxDialogImpl::AdviseSinkMap](#advisesinkmap)|Rufen Sie diese Methode auf, um alle Einträge in der Senkenzuordnungszuordnung des Objekts zu beraten oder zu unterberaten.|
|[CAxDialogImpl::Erstellen](#create)|Rufen Sie diese Methode auf, um ein modusloses Dialogfeld zu erstellen.|
|[CAxDialogImpl::DestroyWindow](#destroywindow)|Rufen Sie diese Methode auf, um ein modusloses Dialogfeld zu zerstören.|
|[CAxDialogImpl::DoModal](#domodal)|Rufen Sie diese Methode auf, um ein modales Dialogfeld zu erstellen.|
|[CAxDialogImpl::EndDialog](#enddialog)|Rufen Sie diese Methode auf, um ein modales Dialogfeld zu zerstören.|
|[CAxDialogImpl::GetDialogProc](#getdialogproc)|Rufen Sie diese Methode auf, `DialogProc` um einen Zeiger auf die Rückruffunktion abzurufen.|
|[CAxDialogImpl::GetIDD](#getidd)|Rufen Sie diese Methode auf, um die Dialogvorlagenressourcen-ID abzurufen.|
|[CAxDialogImpl::IsDialogMessage](#isdialogmessage)|Rufen Sie diese Methode auf, um zu bestimmen, ob eine Nachricht für dieses Dialogfeld vorgesehen ist, und verarbeiten Sie die Nachricht, falls dies der Fall ist.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAxDialogImpl::m_bModal](#m_bmodal)|Eine Variable, die nur in Debugbuilds vorhanden ist und auf true festgelegt ist, wenn das Dialogfeld modal ist.|

## <a name="remarks"></a>Bemerkungen

`CAxDialogImpl`können Sie ein modales oder modusloses Dialogfeld erstellen. `CAxDialogImpl`stellt die Dialogfeldprozedur bereit, die die Standardnachrichtenzuordnung verwendet, um Nachrichten an die entsprechenden Handler weiterzuleiten.

`CAxDialogImpl`leitet sich `CDialogImplBaseT`von ab , was wiederum von *TBase* (standardmäßig, `CWindow`) und `CMessageMap`ableitet.

Ihre Klasse muss einen IDD-Member definieren, der die Dialogvorlagenressourcen-ID angibt. Wenn Sie beispielsweise ein ATL-Dialogobjekt mithilfe des Dialogfelds **Klassen hinzufügen** hinzufügen hinzufügen, wird Ihrer Klasse automatisch die folgende Zeile hinzugefügt:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]

Wobei `MyDialog` der **Kurzname** ist, der im ATL-Dialog-Assistenten eingegeben wurde.

Weitere Informationen finden Sie unter [Implementieren eines Dialogfelds.](../../atl/implementing-a-dialog-box.md)

Beachten Sie, dass ein ActiveX-Steuerelement `CAxDialogImpl` in einem modalen Dialogfeld, das mit erstellt wurde, keine Beschleunigerschlüssel unterstützt. Um Beschleunigerschlüssel in `CAxDialogImpl`einem mit erstellten Dialogfeld zu unterstützen, erstellen Sie ein modusloses Dialogfeld, und verwenden Sie mithilfe Ihrer eigenen Nachrichtenschleife [CAxDialogImpl::IsDialogMessage,](#isdialogmessage) nachdem Sie eine Nachricht aus der Warteschlange erhalten haben, um einen Beschleunigerschlüssel zu verarbeiten.

Weitere Informationen `CAxDialogImpl`zu finden Sie unter HÄUFIG gestellte Fragen zu [ATL Control Containment](../../atl/atl-control-containment-faq.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CDialogImplBaseT`

`CAxDialogImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="caxdialogimpladvisesinkmap"></a><a name="advisesinkmap"></a>CAxDialogImpl::AdviseSinkMap

Rufen Sie diese Methode auf, um alle Einträge in der Senkenzuordnungszuordnung des Objekts zu beraten oder zu unterberaten.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Parameter

*bAdvise*<br/>
Wird auf true gesetzt, wenn alle Senkeneinträge empfohlen werden sollen; false, wenn alle Senkeneinträge nicht empfohlen werden sollen.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="caxdialogimplcreate"></a><a name="create"></a>CAxDialogImpl::Erstellen

Rufen Sie diese Methode auf, um ein modusloses Dialogfeld zu erstellen.

```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parameter

*hWndEltern*<br/>
[in] Das Handle zum Besitzerfenster.

*dwInitParam*<br/>
[in] Gibt den Wert an, der an das Dialogfeld im *LParam-Parameter* der WM_INITDIALOG-Nachricht übergeben werden soll.

*RECT&*<br/>
Dieser Parameter wird nicht verwendet. Dieser Parameter wird `CComControl`von übergeben.

### <a name="return-value"></a>Rückgabewert

Das Handle zum neu erstellten Dialogfeld.

### <a name="remarks"></a>Bemerkungen

Dieses Dialogfeld wird automatisch `CAxDialogImpl` an das Objekt angefügt. Um ein modales Dialogfeld zu erstellen, rufen Sie [DoModal](#domodal)auf.

Die zweite Außerkraftsetzung wird nur bereitgestellt, damit Dialogfelder mit [CComControl](../../atl/reference/ccomcontrol-class.md)verwendet werden können.

## <a name="caxdialogimpldestroywindow"></a><a name="destroywindow"></a>CAxDialogImpl::DestroyWindow

Rufen Sie diese Methode auf, um ein modusloses Dialogfeld zu zerstören.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Fenster erfolgreich zerstört wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Rufen `DestroyWindow` Sie nicht auf, um ein modales Dialogfeld zu zerstören. Rufen Sie stattdessen [EndDialog](#enddialog) auf.

## <a name="caxdialogimpldomodal"></a><a name="domodal"></a>CAxDialogImpl::DoModal

Rufen Sie diese Methode auf, um ein modales Dialogfeld zu erstellen.

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parameter

*hWndEltern*<br/>
[in] Das Handle zum Besitzerfenster. Der Standardwert ist der Rückgabewert der [GetActiveWindow](/windows/win32/api/winuser/nf-winuser-getactivewindow) Win32-Funktion.

*dwInitParam*<br/>
[in] Gibt den Wert an, der an das Dialogfeld im *LParam-Parameter* der WM_INITDIALOG-Nachricht übergeben werden soll.

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, der Wert des *nRetCode-Parameters,* der im Aufruf von [EndDialog](#enddialog)angegeben ist; andernfalls -1.

### <a name="remarks"></a>Bemerkungen

Dieses Dialogfeld wird automatisch `CAxDialogImpl` an das Objekt angefügt.

Um ein modusloses Dialogfeld zu erstellen, rufen Sie [Create auf.](#create)

## <a name="caxdialogimplenddialog"></a><a name="enddialog"></a>CAxDialogImpl::EndDialog

Rufen Sie diese Methode auf, um ein modales Dialogfeld zu zerstören.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Parameter

*nRetCode*<br/>
[in] Der Wert, der von [DoModal](#domodal)zurückgegeben werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Dialogfeld zerstört wird; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

`EndDialog`muss über die Dialogfeldprozedur aufgerufen werden. Nachdem das Dialogfeld zerstört wurde, verwendet Windows den Wert `DoModal`von *nRetCode* als Rückgabewert für , der das Dialogfeld erstellt hat.

> [!NOTE]
> Rufen `EndDialog` Sie nicht auf, um ein modusloses Dialogfeld zu zerstören. Rufen Sie stattdessen [DestroyWindow](#destroywindow) auf.

## <a name="caxdialogimplgetdialogproc"></a><a name="getdialogproc"></a>CAxDialogImpl::GetDialogProc

Rufen Sie diese Methode auf, `DialogProc` um einen Zeiger auf die Rückruffunktion abzurufen.

```
virtual DLGPROC GetDialogProc();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger `DialogProc` auf die Rückruffunktion zurück.

### <a name="remarks"></a>Bemerkungen

Die `DialogProc` Funktion ist eine anwendungsdefinierte Rückruffunktion.

## <a name="caxdialogimplgetidd"></a><a name="getidd"></a>CAxDialogImpl::GetIDD

Rufen Sie diese Methode auf, um die Dialogvorlagenressourcen-ID abzurufen.

```
int GetIDD();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Dialogvorlagenressourcen-ID zurück.

## <a name="caxdialogimplisdialogmessage"></a><a name="isdialogmessage"></a>CAxDialogImpl::IsDialogMessage

Rufen Sie diese Methode auf, um zu bestimmen, ob eine Nachricht für dieses Dialogfeld vorgesehen ist, und verarbeiten Sie die Nachricht, falls dies der Fall ist.

```
BOOL IsDialogMessage(LPMSG pMsg);
```

### <a name="parameters"></a>Parameter

*pMsg*<br/>
Zeiger auf eine [MSG-Struktur,](/windows/win32/api/winuser/ns-winuser-msg) die die zu überprüfende Nachricht enthält.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Nachricht verarbeitet wurde, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode soll innerhalb einer Nachrichtenschleife aufgerufen werden.

## <a name="caxdialogimplm_bmodal"></a><a name="m_bmodal"></a>CAxDialogImpl::m_bModal

Eine Variable, die nur in Debugbuilds vorhanden ist und auf true festgelegt ist, wenn das Dialogfeld modal ist.

```
bool m_bModal;
```

## <a name="see-also"></a>Siehe auch

[CDialogImpl-Klasse](../../atl/reference/cdialogimpl-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
