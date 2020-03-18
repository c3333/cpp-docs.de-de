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
ms.openlocfilehash: 548d2aed0644187b4b8dee1e472b581f1f92d6a1
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423393"
---
# <a name="caxdialogimpl-class"></a>CAxDialogImpl-Klasse

Diese Klasse implementiert ein (modales oder nicht modales) Dialogfeld, das ActiveX-Steuerelemente hostet.

> [!IMPORTANT]
>  Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
template <class T, class TBase = CWindow>
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Die von `CAxDialogImpl`abgeleitete Klasse.

*Tbase*<br/>
Die Basis Fenster Klasse für `CDialogImplBaseT`.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CAxDialogImpl:: AdviseSinkMap](#advisesinkmap)|Mit dieser Methode können Sie alle Einträge in der senderzuordnungs-Ereignis Zuordnung des Objekts anweisen oder deren Empfehlung aufheben.|
|[CAxDialogImpl:: Create](#create)|Rufen Sie diese Methode auf, um ein Dialogfeld ohne Modus zu erstellen.|
|[CAxDialogImpl::D estroywindow](#destroywindow)|Mit dieser Methode können Sie ein nicht modalem Dialogfeld zerstören.|
|[CAxDialogImpl::D omodal](#domodal)|Rufen Sie diese Methode auf, um ein modales Dialogfeld zu erstellen.|
|[CAxDialogImpl:: EndDialog](#enddialog)|Diese Methode wird aufgerufen, um ein modales Dialogfeld zu zerstören.|
|[CAxDialogImpl:: getdialogproc](#getdialogproc)|Rufen Sie diese Methode auf, um einen Zeiger auf die `DialogProc` Rückruffunktion abzurufen.|
|[CAxDialogImpl:: getidd](#getidd)|Diese Methode zum Abrufen der Ressourcen-ID der Dialog Vorlage abrufen|
|[CAxDialogImpl:: IsDialogMessage](#isdialogmessage)|Ruft diese Methode auf, um zu bestimmen, ob eine Nachricht für dieses Dialogfeld vorgesehen ist, und verarbeitet die Nachricht, wenn dies der Fall ist.|

### <a name="protected-data-members"></a>Geschützte Datenelemente

|Name|Beschreibung|
|----------|-----------------|
|[CAxDialogImpl:: m_bModal](#m_bmodal)|Eine Variable, die nur in Debugbuilds vorhanden und auf true festgelegt ist, wenn das Dialogfeld modal ist.|

## <a name="remarks"></a>Hinweise

mit `CAxDialogImpl` können Sie ein modales oder nicht modales Dialogfeld erstellen. `CAxDialogImpl` stellt die Dialogfeld Prozedur bereit, in der die standardmäßige Meldungs Zuordnung verwendet wird, um Nachrichten an die entsprechenden Handler weiterzuleiten.

`CAxDialogImpl` von `CDialogImplBaseT`abgeleitet, die wiederum von *tbase* (standardmäßig `CWindow`) und `CMessageMap`abgeleitet ist.

Die Klasse muss einen IDD-Member definieren, der die Ressourcen-ID der Dialogfeld Vorlage angibt. Wenn Sie z. b. ein ATL-Dialogfeld Objekt mit dem Dialogfeld **Klasse hinzufügen** hinzufügen, wird der Klasse automatisch die folgende Zeile hinzugefügt:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]

Dabei ist `MyDialog` der **Kurzname** , der im ATL-Dialog-Assistenten eingegeben wurde.

Weitere Informationen finden Sie unter [Implementieren eines Dialog](../../atl/implementing-a-dialog-box.md) Felds.

Beachten Sie, dass ein ActiveX-Steuerelement in einem modalen Dialogfeld, das mit `CAxDialogImpl` erstellt wurde, keine Zugriffstasten unterstützt Um Zugriffstasten in einem Dialogfeld zu unterstützen, das mit `CAxDialogImpl`erstellt wurde, erstellen Sie ein nicht modalem Dialogfeld, und verwenden Sie eine eigene Nachrichten Schleife, und verwenden Sie [CAxDialogImpl:: IsDialogMessage](#isdialogmessage) , nachdem Sie eine Nachricht aus der Warteschlange zum Verarbeiten einer Zugriffstaste erhalten haben.

Weitere Informationen zu `CAxDialogImpl`finden Sie unter Häufig gestellte Fragen zur [ATL-Kontrolle](../../atl/atl-control-containment-faq.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CDialogImplBaseT`

`CAxDialogImpl`

## <a name="requirements"></a>Voraussetzungen

**Header:** atlwin. h

##  <a name="advisesinkmap"></a>CAxDialogImpl:: AdviseSinkMap

Mit dieser Methode können Sie alle Einträge in der senderzuordnungs-Ereignis Zuordnung des Objekts anweisen oder deren Empfehlung aufheben.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Parameter

*bEmpfehlung*<br/>
Auf "true" festgelegt, wenn alle Senke-Einträge empfohlen werden. false, wenn alle Senke-Einträge nicht empfohlen werden.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

##  <a name="create"></a>CAxDialogImpl:: Create

Rufen Sie diese Methode auf, um ein Dialogfeld ohne Modus zu erstellen.

```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parameter

*hwndParent*<br/>
in Das Handle für das Besitzer Fenster.

*dwinitparam*<br/>
in Gibt den Wert an, der dem Dialogfeld im *LPARAM* -Parameter der WM_INITDIALOG Nachricht übergeben werden soll.

*Rect-&*<br/>
Dieser Parameter wird nicht verwendet. Dieser Parameter wird von `CComControl`übergeben.

### <a name="return-value"></a>Rückgabewert

Das Handle für das neu erstellte Dialogfeld.

### <a name="remarks"></a>Hinweise

Dieses Dialogfeld wird automatisch an das `CAxDialogImpl` Objekt angefügt. Um ein modales Dialogfeld zu erstellen, rufen Sie [DoModal](#domodal)auf.

Die zweite außer Kraft setzung wird nur bereitgestellt, sodass Dialogfelder mit [CComControl](../../atl/reference/ccomcontrol-class.md)verwendet werden können.

##  <a name="destroywindow"></a>CAxDialogImpl::D estroywindow

Mit dieser Methode können Sie ein nicht modalem Dialogfeld zerstören.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Fenster erfolgreich zerstört wird. andernfalls false.

### <a name="remarks"></a>Hinweise

Nicht `DestroyWindow` aufgerufen werden, um ein modales Dialogfeld zu zerstören. Ruft stattdessen [EndDialog](#enddialog) auf.

##  <a name="domodal"></a>CAxDialogImpl::D omodal

Rufen Sie diese Methode auf, um ein modales Dialogfeld zu erstellen.

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parameter

*hwndParent*<br/>
in Das Handle für das Besitzer Fenster. Der Standardwert ist der Rückgabewert der Win32-Funktion [GetActiveWindow](/windows/win32/api/winuser/nf-winuser-getactivewindow) .

*dwinitparam*<br/>
in Gibt den Wert an, der dem Dialogfeld im *LPARAM* -Parameter der WM_INITDIALOG Nachricht übergeben werden soll.

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, der Wert des *nretcode* -Parameters, der im Aufrufen von [EndDialog](#enddialog); angegeben ist. andernfalls-1.

### <a name="remarks"></a>Hinweise

Dieses Dialogfeld wird automatisch an das `CAxDialogImpl` Objekt angefügt.

Um ein nicht modalem Dialogfeld zu erstellen, rufen Sie [Create](#create)auf.

##  <a name="enddialog"></a>CAxDialogImpl:: EndDialog

Diese Methode wird aufgerufen, um ein modales Dialogfeld zu zerstören.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Parameter

*nretcode*<br/>
in Der Wert, der von " [DoModal](#domodal)" zurückgegeben werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Dialogfeld zerstört wird. andernfalls false.

### <a name="remarks"></a>Hinweise

`EndDialog` müssen über die Dialogfeld Prozedur aufgerufen werden. Nachdem das Dialogfeld zerstört wurde, verwendet Windows den Wert von *nretcode* als Rückgabewert für `DoModal`, der das Dialogfeld erstellt hat.

> [!NOTE]
>  Nicht `EndDialog` aufgerufen werden, um ein nicht modalem Dialogfeld zu zerstören. Stattdessen wird [DestroyWindow](#destroywindow) aufgerufen.

##  <a name="getdialogproc"></a>CAxDialogImpl:: getdialogproc

Rufen Sie diese Methode auf, um einen Zeiger auf die `DialogProc` Rückruffunktion abzurufen.

```
virtual DLGPROC GetDialogProc();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf die `DialogProc` Rückruffunktion zurück.

### <a name="remarks"></a>Hinweise

Die `DialogProc`-Funktion ist eine Anwendungs definierte Rückruffunktion.

##  <a name="getidd"></a>CAxDialogImpl:: getidd

Mit dieser Methode können Sie die Ressourcen-ID der Dialogfeld Vorlage abrufen.

```
int GetIDD();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Ressourcen-ID der Dialogfeld Vorlage zurück.

##  <a name="isdialogmessage"></a>CAxDialogImpl:: IsDialogMessage

Ruft diese Methode auf, um zu bestimmen, ob eine Nachricht für dieses Dialogfeld vorgesehen ist, und verarbeitet die Nachricht, wenn dies der Fall ist.

```
BOOL IsDialogMessage(LPMSG pMsg);
```

### <a name="parameters"></a>Parameter

*pmsg*<br/>
Zeiger auf eine [msg](/windows/win32/api/winuser/ns-winuser-msg) -Struktur, die die zu überprüfende Nachricht enthält.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Nachricht verarbeitet wurde, andernfalls false.

### <a name="remarks"></a>Hinweise

Diese Methode soll innerhalb einer Nachrichten Schleife aufgerufen werden.

##  <a name="m_bmodal"></a>CAxDialogImpl:: m_bModal

Eine Variable, die nur in Debugbuilds vorhanden und auf true festgelegt ist, wenn das Dialogfeld modal ist.

```
bool m_bModal;
```

## <a name="see-also"></a>Siehe auch

[CDialogImpl-Klasse](../../atl/reference/cdialogimpl-class.md)<br/>
[Klassen Übersicht](../../atl/atl-class-overview.md)
