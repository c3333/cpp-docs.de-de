---
title: CDialogImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDialogImpl
- ATLWIN/ATL::CDialogImpl
- ATLWIN/ATL::Create
- ATLWIN/ATL::DestroyWindow
- ATLWIN/ATL::DoModal
- ATLWIN/ATL::EndDialog
- ATLWIN/ATL::GetDialogProc
- ATLWIN/ATL::MapDialogRect
- ATLWIN/ATL::OnFinalMessage
- ATLWIN/ATL::DialogProc
- ATLWIN/ATL::StartDialogProc
helpviewer_keywords:
- dialog boxes, ATL
- CDialogImpl class
ms.assetid: d430bc7b-8a28-4ad3-9507-277bdd2c2c2e
ms.openlocfilehash: d5ab7293f73429a93c3fcab243c2e34d3c78f28a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747707"
---
# <a name="cdialogimpl-class"></a>CDialogImpl-Klasse

Diese Klasse stellt Methoden zum Erstellen eines modalen oder moduslosen Dialogfelds bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <class T,
    class TBase = CWindow>
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `CDialogImpl`abgeleitet von .

*TBase*<br/>
Die Basisklasse Ihrer neuen Klasse. Die Standardbasisklasse ist [CWindow](../../atl/reference/cwindow-class.md).

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[Erstellen](#create)|Erstellt ein modusloses Dialogfeld.|
|[DestroyWindow](#destroywindow)|Zerstört ein modusloses Dialogfeld.|
|[DoModal](#domodal)|Erstellt ein modales Dialogfeld.|
|[EndDialog](#enddialog)|Zerstört ein modales Dialogfeld.|

### <a name="cdialogimplbaset-methods"></a>CDialogImplBaseT-Methoden

|||
|-|-|
|[GetDialogProc](#getdialogproc)|Gibt die aktuelle Dialogfeldprozedur zurück.|
|[MapDialogRect](#mapdialogrect)|Ordnet die Dialogfeldeinheiten des angegebenen Rechtecks Bildschirmeinheiten (Pixel) zu.|
|[OnFinalMessage](#onfinalmessage)|Wird nach dem Empfang der letzten Nachricht aufgerufen, in der Regel WM_NCDESTROY.|

### <a name="static-functions"></a>Statische Funktionen

|||
|-|-|
|[DialogProc](#dialogproc)|Verarbeitet Nachrichten, die an das Dialogfeld gesendet werden.|
|[StartDialogProc](#startdialogproc)|Wird aufgerufen, wenn die erste Nachricht empfangen wird, um nachrichten zu verarbeiten, die an das Dialogfeld gesendet werden.|

## <a name="remarks"></a>Bemerkungen

Mit `CDialogImpl` können Sie ein modales oder modusloses Dialogfeld erstellen. `CDialogImpl`stellt die Dialogfeldprozedur bereit, die die Standardnachrichtenzuordnung verwendet, um Nachrichten an die entsprechenden Handler weiterzuleiten.

Der Zerstörungser `~CWindowImplRoot` der Basisklasse stellt sicher, dass das Fenster vor dem Zerstören des Objekts verschwunden ist.

`CDialogImpl` wird von `CDialogImplBaseT` abgeleitet, was wiederum von `CWindowImplRoot` abgeleitet wird.

> [!NOTE]
> Ihre Klasse muss `IDD` einen Member definieren, der die Dialogvorlagenressourcen-ID angibt. Der ATL-Projekt-Assistent fügt Ihrer Klasse beispielsweise automatisch die folgende Zeile hinzu:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]

Wobei `MyDlg` der **Name Kurz** ist, der auf der Seite **Namen** des Assistenten eingegeben wurde.

|Weitere Informationen über|Finden Sie unter|
|--------------------------------|---------|
|Erstellen von Steuerelementen|[ATL-Tutorial](../../atl/active-template-library-atl-tutorial.md)|
|Verwenden von Dialogfeldern in ATL|[ATL-Fensterklassen](../../atl/atl-window-classes.md)|
|ATL-Projekt-Assistent|[Erstellen eines ATL-Projekts](../../atl/reference/creating-an-atl-project.md)|
|Dialogfelder|[Dialogfelder](/windows/win32/dlgbox/dialog-boxes) und nachfolgende Themen im Windows SDK|

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlwin.h

## <a name="cdialogimplcreate"></a><a name="create"></a>CDialogImpl::Erstellen

Erstellt ein modusloses Dialogfeld.

```
HWND Create(
    HWND hWndParent,
    LPARAM dwInitParam = NULL );

HWND Create(
    HWND hWndParent,
    RECT&,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parameter

*hWndEltern*<br/>
[in] Das Handle zum Besitzerfenster.

**RECT&** *korrigieren* [in] Eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die die Größe und Position des Dialogs angibt.

*dwInitParam*<br/>
[in] Gibt den Wert an, der an das Dialogfeld im *LParam-Parameter* der WM_INITDIALOG-Nachricht übergeben werden soll.

### <a name="return-value"></a>Rückgabewert

Das Handle zum neu erstellten Dialogfeld.

### <a name="remarks"></a>Bemerkungen

Dieses Dialogfeld wird automatisch `CDialogImpl` an das Objekt angefügt. Um ein modales Dialogfeld zu erstellen, rufen Sie [DoModal](#domodal)auf. Die zweite Obschreibung oben wird nur mit [CComControl](../../atl/reference/ccomcontrol-class.md)verwendet.

## <a name="cdialogimpldestroywindow"></a><a name="destroywindow"></a>CDialogImpl::DestroyWindow

Zerstört ein modusloses Dialogfeld.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Dialogfeld erfolgreich zerstört wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Gibt TRUE zurück, wenn das Dialogfeld erfolgreich zerstört wurde. andernfalls FALSE.

## <a name="cdialogimpldialogproc"></a><a name="dialogproc"></a>CDialogImpl::DialogProc

Diese statische Funktion implementiert die Dialogfeldprozedur.

```
static LRESULT CALLBACK DialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
[in] Das Handle zum Dialogfeld.

*uMsg*<br/>
[in] Die an das Dialogfeld gesendete Nachricht.

*wParam*<br/>
[in] Zusätzliche nachrichtenspezifische Informationen.

*lParam*<br/>
[in] Zusätzliche nachrichtenspezifische Informationen.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Nachricht verarbeitet wird; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

`DialogProc`verwendet die Standardnachrichtenzuordnung, um Nachrichten an die entsprechenden Handler weiterzuleiten.

Sie können `DialogProc` überschreiben, um einen anderen Mechanismus für die Verarbeitung von Nachrichten bereitzustellen.

## <a name="cdialogimpldomodal"></a><a name="domodal"></a>CDialogImpl::DoModal

Erstellt ein modales Dialogfeld.

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

Wenn erfolgreich, wird der Wert des *nRetCode-Parameters,* der im Aufruf von [EndDialog](#enddialog)angegeben ist. Andernfalls: -1

### <a name="remarks"></a>Bemerkungen

Dieses Dialogfeld wird automatisch `CDialogImpl` an das Objekt angefügt.

Um ein modusloses Dialogfeld zu erstellen, rufen Sie [Create auf.](#create)

## <a name="cdialogimplenddialog"></a><a name="enddialog"></a>CDialogImpl::EndDialog

Zerstört ein modales Dialogfeld.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Parameter

*nRetCode*<br/>
[in] Der Wert, der von [CDialogImpl::DoModal](#domodal)zurückgegeben werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Dialogfeld zerstört wird; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

`EndDialog`muss über die Dialogprozedur aufgerufen werden. Nachdem das Dialogfeld zerstört wurde, verwendet Windows den Wert `DoModal`von *nRetCode* als Rückgabewert für , der das Dialogfeld erstellt hat.

> [!NOTE]
> Rufen `EndDialog` Sie nicht auf, um ein modusloses Dialogfeld zu zerstören. Rufen Sie stattdessen [CWindow::DestroyWindow](../../atl/reference/cwindow-class.md#destroywindow) auf.

## <a name="cdialogimplgetdialogproc"></a><a name="getdialogproc"></a>CDialogImpl::GetDialogProc

Gibt `DialogProc`zurück , die aktuelle Dialogfeldprozedur.

```
virtual WNDPROC GetDialogProc();
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Dialogfeldprozedur.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um die Dialogprozedur durch Ihre eigene zu ersetzen.

## <a name="cdialogimplmapdialogrect"></a><a name="mapdialogrect"></a>CDialogImpl::MapDialogRect

Konvertiert (Zuordnungen) der Dialogfeldeinheiten des angegebenen Rechtecks in Bildschirmeinheiten (Pixel).

```
BOOL MapDialogRect(LPRECT lpRect);
```

### <a name="parameters"></a>Parameter

*lpRect*<br/>
Zeigt auf `CRect` ein Objekt oder eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die die Clientkoordinaten der Aktualisierung empfangen soll, die den Aktualisierungsbereich umschließt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Aktualisierung erfolgreich ist; 0, wenn die Aktualisierung fehlschlägt. Um erweiterte Fehlerinformationen abzurufen, rufen Sie `GetLastError` auf.

### <a name="remarks"></a>Bemerkungen

Die Funktion ersetzt die Koordinaten `RECT` in der angegebenen Struktur durch die konvertierten Koordinaten, wodurch die Struktur verwendet werden kann, um ein Dialogfeld zu erstellen oder ein Steuerelement innerhalb eines Dialogfelds zu positionieren.

## <a name="cdialogimplonfinalmessage"></a><a name="onfinalmessage"></a>CDialogImpl::OnFinalMessage

Wird nach dem Empfang `WM_NCDESTROY`der letzten Nachricht aufgerufen (in der Regel ).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
[in] Ein Griff zum Fenster wird zerstört.

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass, wenn Sie Ihr Objekt bei der Fensterzerstörung automatisch löschen möchten, Sie dies löschen **können;** hier.

## <a name="cdialogimplstartdialogproc"></a><a name="startdialogproc"></a>CDialogImpl::StartDialogProc

Wird nur einmal aufgerufen, wenn die erste Nachricht empfangen wird, um an das Dialogfeld gesendete Nachrichten zu verarbeiten.

```
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
[in] Das Handle zum Dialogfeld.

*uMsg*<br/>
[in] Die an das Dialogfeld gesendete Nachricht.

*wParam*<br/>
[in] Zusätzliche nachrichtenspezifische Informationen.

*lParam*<br/>
[in] Zusätzliche nachrichtenspezifische Informationen.

### <a name="return-value"></a>Rückgabewert

Die Fensterprozedur.

### <a name="remarks"></a>Bemerkungen

Nach dem ersten `StartDialogProc` `DialogProc` Aufruf von wird als Dialogprozedur festgelegt, und weitere Aufrufe werden dorthin gesetzt.

## <a name="see-also"></a>Weitere Informationen

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
