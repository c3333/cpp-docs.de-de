---
title: CWindowImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CWindowImpl
- ATLWIN/ATL::CWindowImpl
- ATLWIN/ATL::CWindowImpl::Create
- ATLWIN/ATL::CWindowImpl::DefWindowProc
- ATLWIN/ATL::CWindowImpl::GetCurrentMessage
- ATLWIN/ATL::CWindowImpl::GetWindowProc
- ATLWIN/ATL::CWindowImpl::OnFinalMessage
- ATLWIN/ATL::CWindowImpl::SubclassWindow
- ATLWIN/ATL::CWindowImpl::UnsubclassWindow
- ATLWIN/ATL::CWindowImpl::GetWndClassInfo
- ATLWIN/ATL::CWindowImpl::WindowProc
- ATLWIN/ATL::CWindowImpl::m_pfnSuperWindowProc
helpviewer_keywords:
- CWindowImpl class
- subclassing windows, ATL
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
ms.openlocfilehash: b8b633dcf4ea14e899ee00552b553476cf697689
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78862967"
---
# <a name="cwindowimpl-class"></a>CWindowImpl-Klasse

Stellt Methoden für das Erstellen eines Fensters oder von Unterklassen eines Fensters bereit

> [!IMPORTANT]
>  Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Die neue Klasse, die von `CWindowImpl` abgeleitet ist.

*Tbase*<br/>
Die Basisklasse der Klasse. Standardmäßig ist die Basisklasse [CWindow](../../atl/reference/cwindow-class.md).

*Twinmerkmalen*<br/>
Eine [Eigenschaften Klasse](../../atl/understanding-window-traits.md) , die Stile für das Fenster definiert. Der Standardwert lautet `CControlWinTraits`.

## <a name="members"></a>Members

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWindowImpl:: Create](#create)|Erstellt ein Fenster.|

### <a name="cwindowimplbaset-methods"></a>CWindowImplBaseT-Methoden

|||
|-|-|
|[Defwindowproc](#defwindowproc)|Stellt die Standardverarbeitung von Nachrichten bereit.|
|[GetCurrentMessage](#getcurrentmessage)|Die gibt die aktuelle Nachricht zurück.|
|[Getwindowproc](#getwindowproc)|Gibt die aktuelle Fensterprozedur zurück.|
|[Onfinalmessage](#onfinalmessage)|Wird aufgerufen, nachdem die letzte Meldung empfangen wurde (in der Regel WM_NCDESTROY).|
|[Unterklassen Fenster](#subclasswindow)|Erstellt Unterklassen eines Fensters.|
|[Unsubclasswindow](#unsubclasswindow)|Stellt ein zuvor untergeordnetes Fenster wieder her.|

### <a name="static-methods"></a>Statische Methoden

|||
|-|-|
|[GetWndClassInfo](#getwndclassinfo)|Gibt eine statische Instanz von [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)zurück, die die Fenster Klassen Informationen verwaltet.|
|[WindowProc](#windowproc)|Verarbeitet die Nachrichten, die an das Fenster gesendet werden.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Zeigt auf die ursprüngliche Fensterprozedur der Fensterklasse.|

## <a name="remarks"></a>Bemerkungen

Sie können `CWindowImpl` zum Erstellen eines Fensters oder einer Unterklasse eines vorhandenen Fensters verwenden. die `CWindowImpl` Fenster Prozedur verwendet eine Meldungs Zuordnung, um Nachrichten an die entsprechenden Handler weiterzuleiten.

`CWindowImpl::Create` erstellt ein Fenster auf der Grundlage der Fenster Klassen Informationen, die von [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)verwaltet werden. `CWindowImpl` enthält das [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) -Makro, was bedeutet, dass `CWndClassInfo` eine neue Fenster Klasse registriert. Wenn Sie eine übergeordnete Klasse einer vorhandenen Fenster Klasse übernehmen möchten, leiten Sie die Klasse von `CWindowImpl` ab, und schließen Sie das [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) Makro ein. In diesem Fall wird mit `CWndClassInfo` eine Fensterklasse registriert, die auf einer vorhandenen Klasse basiert, aber `CWindowImpl::WindowProc` verwendet. Beispiel:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
>  Da `CWndClassInfo` nur die Informationen für eine Fensterklasse verwaltet, basiert jedes Fenster, das durch eine Instanz von `CWindowImpl` erstellt wird, auf der gleichen Fensterklasse.

`CWindowImpl` unterstützt auch die Erstellung von Unterklassen von Fenstern. Die `SubclassWindow`-Methode fügt ein vorhandenes Fenster an das `CWindowImpl`-Objekt an und ändert die Fensterprozedur in `CWindowImpl::WindowProc`. Jede Instanz von `CWindowImpl` kann ein anderes Fenster unterordnen.

> [!NOTE]
>  Für ein beliebiges `CWindowImpl` Objekt wird entweder `Create` oder `SubclassWindow`aufgerufen. Rufen Sie nicht beide Methoden für dasselbe Objekt auf.

Zusätzlich zu `CWindowImpl`stellt ATL [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) zum Erstellen eines Fensters bereit, das in einem anderen Objekt enthalten ist.

Der basisklassendebugtor (~ `CWindowImplRoot`) stellt sicher, dass das Fenster nicht mehr vorhanden ist, bevor das Objekt zerstört wird.

`CWindowImpl` wird von `CWindowImplBaseT`abgeleitet, das von `CWindowImplRoot`abgeleitet ist, das von `TBase` und [cmessagemap](../../atl/reference/cmessagemap-class.md)abgeleitet ist.

|Weitere Informationen über|Finden Sie unter|
|--------------------------------|---------|
|Erstellen von Steuerelementen|[ATL-Tutorial](../../atl/active-template-library-atl-tutorial.md)|
|Verwenden von Fenstern in ATL|[ATL-Fensterklassen](../../atl/atl-window-classes.md)|
|ATL-Projekt-Assistent|[Erstellen eines ATL-Projekts](../../atl/reference/creating-an-atl-project.md)|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CWindowImplBaseT`

`CWindowImpl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

##  <a name="create"></a>CWindowImpl:: Create

Erstellt ein Fenster, das auf einer neuen Fenster Klasse basiert.

```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```

### <a name="parameters"></a>Parameter

*hwndParent*<br/>
in Das Handle für das übergeordnete Fenster oder Besitzer Fenster.

*Rect*<br/>
in Eine [Rect](/previous-versions/dd162897\(v=vs.85\)) -Struktur, die die Position des Fensters angibt. Der `RECT` kann als Zeiger oder als Verweis übermittelt werden.

*szwindowname*<br/>
in Gibt den Namen des Fensters an. Der Standardwert ist NULL.

*dwstyle*<br/>
in Der Stil des Fensters. Dieser Wert wird mit dem Format kombiniert, das von der Merkmale-Klasse für das Fenster bereitgestellt wird. Mit dem Standardwert erhält die Klasse "Merkmale" vollständige Kontrolle über den Stil. Eine Liste möglicher Werte finden Sie unter " [kreatewindow](/windows/win32/api/winuser/nf-winuser-createwindoww) " in der Windows SDK.

*dwExStyle*<br/>
in Der erweiterte Fenster Stil. Dieser Wert wird mit dem Format kombiniert, das von der Merkmale-Klasse für das Fenster bereitgestellt wird. Mit dem Standardwert erhält die Klasse "Merkmale" vollständige Kontrolle über den Stil. Eine Liste möglicher Werte finden Sie unter " [kreatewindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) " in der Windows SDK.

*Menuorid*<br/>
in Für ein untergeordnetes Fenster der Fenster Bezeichner. Für ein Fenster der obersten Ebene ein Menü Handle für das Fenster. Der Standardwert ist **0U**.

*lpkreateparam*<br/>
in Ein Zeiger auf Fenster Erstellungs Daten. Eine vollständige Beschreibung finden Sie in der Beschreibung des letzten Parameters für " [kreatewindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw)".

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, das Handle für das neu erstellte Fenster. Andernfalls wird NULL verwendet.

### <a name="remarks"></a>Bemerkungen

`Create` registriert zuerst die Fenster Klasse, wenn Sie noch nicht registriert wurde. Das neu erstellte Fenster wird automatisch an das `CWindowImpl` Objekt angefügt.

> [!NOTE]
>  Wenn Sie bereits [SubclassWindow](#subclasswindow)aufgerufen haben, können Sie `Create` nicht aufrufen.

Um eine Fenster Klasse zu verwenden, die auf einer vorhandenen Fenster Klasse basiert, leiten Sie die Klasse von `CWindowImpl` ab, und schließen Sie das [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) -Makro ein. Die Fenster Prozedur der vorhandenen Fenster Klasse wird in [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)gespeichert. Weitere Informationen finden Sie in der Übersicht über [CWindowImpl](../../atl/reference/cwindowimpl-class.md) .

> [!NOTE]
>  Wenn 0 als Wert für den *menuorid-* Parameter verwendet wird, muss es als 0U (Standardwert) angegeben werden, um einen Compilerfehler zu vermeiden.

##  <a name="defwindowproc"></a>CWindowImpl::D efwindowproc

Wird von [WindowProc](#windowproc) aufgerufen, um Meldungen zu verarbeiten, die nicht von der Meldungs Zuordnung behandelt werden.

```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```

### <a name="parameters"></a>Parameter

*Umschlag*<br/>
in Die an das Fenster gesendete Nachricht.

*wParam*<br/>
in Zusätzliche Nachrichten spezifische Informationen.

*lParam*<br/>
in Zusätzliche Nachrichten spezifische Informationen.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis der Nachrichtenverarbeitung.

### <a name="remarks"></a>Bemerkungen

Standardmäßig wird von `DefWindowProc` die Win32-Funktion [callwindowproc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) aufgerufen, um die Nachrichten Informationen an die in [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)angegebene Fenster Prozedur zu senden.

Die-Funktion ohne Parameter ruft automatisch die erforderlichen Parameter aus der aktuellen Nachricht ab.

##  <a name="getcurrentmessage"></a>CWindowImpl:: GetCurrentMessage

Gibt die aktuelle Meldung zurück, die in der `MSG` Struktur verpackt ist.

```
const MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Meldung.

##  <a name="getwindowproc"></a>CWindowImpl:: getwindowproc

Gibt `WindowProc`zurück, die aktuelle Fenster Prozedur.

```
virtual WNDPROC GetWindowProc();
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Fenster Prozedur.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um die Fenster Prozedur durch ihre eigenen zu ersetzen.

##  <a name="getwndclassinfo"></a>CWindowImpl:: GetWndClassInfo

Wird von [Create](#create) aufgerufen, um auf die Fenster Klassen Informationen zuzugreifen.

```
static CWndClassInfo& GetWndClassInfo();
```

### <a name="return-value"></a>Rückgabewert

Eine statische Instanz von [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md).

### <a name="remarks"></a>Bemerkungen

Standardmäßig erhält `CWindowImpl` diese Methode über das [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) -Makro, das eine neue Fenster Klasse angibt.

Leiten Sie die Klasse von `CWindowImpl` ab, und schließen Sie das [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) -Makro ein, um `GetWndClassInfo`zu überschreiben. Weitere Informationen finden Sie in der Übersicht über [CWindowImpl](../../atl/reference/cwindowimpl-class.md) .

Neben der Verwendung des DECLARE_WND_CLASS-und DECLARE_WND_SUPERCLASS Makros können Sie `GetWndClassInfo` mit ihrer eigenen Implementierung überschreiben.

##  <a name="m_pfnsuperwindowproc"></a>CWindowImpl:: m_pfnSuperWindowProc

Abhängig vom Fenster zeigt auf eine der folgenden Fenster Prozeduren.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Bemerkungen

|Fenstertyp|Fenster Prozedur|
|--------------------|----------------------|
|Ein Fenster, das auf einer neuen Fenster Klasse basiert, die durch das [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) -Makro angegeben wird.|Die " [defwindowproc](/windows/win32/api/winuser/nf-winuser-defwindowprocw) Win32"-Funktion.|
|Ein Fenster, das auf einer Fenster Klasse basiert, die eine vorhandene Klasse ändert, die durch das [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) Makro angegeben wird.|Die Fenster Prozedur der vorhandenen Fenster Klasse.|
|Ein untergeordnetes Fenster.|Die ursprüngliche Fenster Prozedur des untergeordneten Fensters.|

[CWindowImpl::D efwindowproc](#defwindowproc) sendet Nachrichten Informationen an die in `m_pfnSuperWindowProc`gespeicherte Fenster Prozedur.

##  <a name="onfinalmessage"></a>CWindowImpl:: onfinalmessage

Wird nach dem Empfang der letzten Meldung aufgerufen (in der Regel WM_NCDESTROY).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
in Ein Handle für das Fenster, das zerstört wird.

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung von `OnFinalMessage` führt keine Aktion aus, Sie können diese Funktion jedoch außer Kraft setzen, um die Bereinigung vor dem Zerstören eines Fensters zu verarbeiten. Wenn Sie das Objekt bei der Fenster Zerstörung automatisch löschen möchten, können Sie **delete this;** in dieser Funktion aufzurufen.

##  <a name="subclasswindow"></a>CWindowImpl:: SubclassWindow

Unterklassen das von *HWND* identifizierte Fenster und fügt es an das `CWindowImpl` Objekt an.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
in Das Handle für das Fenster, das untergeordnet wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Fenster erfolgreich untergeordnet ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Das untergeordnete Fenster verwendet nun [CWindowImpl:: WindowProc](#windowproc). Die ursprüngliche Fenster Prozedur wird in [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)gespeichert.

> [!NOTE]
>  Rufen Sie `SubclassWindow` nicht auf, wenn Sie " [Create](#create)" bereits aufgerufen haben.

##  <a name="unsubclasswindow"></a>CWindowImpl:: unsubclasswindow

Trennt das untergeordnete Fenster vom `CWindowImpl` Objekt und stellt die ursprüngliche Fenster Prozedur wieder her, die in [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)gespeichert ist.

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>Rückgabewert

Das Handle für das Fenster, das zuvor untergeordnet ist.

##  <a name="windowproc"></a>CWindowImpl:: WindowProc

Diese statische Funktion implementiert die Fenster Prozedur.

```
static LRESULT CALLBACK WindowProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
in Das Handle für das Fenster.

*Umschlag*<br/>
in Die an das Fenster gesendete Nachricht.

*wParam*<br/>
in Zusätzliche Nachrichten spezifische Informationen.

*lParam*<br/>
in Zusätzliche Nachrichten spezifische Informationen.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis der Nachrichtenverarbeitung.

### <a name="remarks"></a>Bemerkungen

`WindowProc` verwendet die standardmäßige Meldungs Zuordnung (mit [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)deklariert) zum Weiterleiten von Nachrichten an die entsprechenden Handler. Bei Bedarf ruft `WindowProc` [defwindowproc](#defwindowproc) auf, um zusätzliche Nachrichtenverarbeitung zu erhalten. Wenn die endgültige Nachricht nicht behandelt wird, führt `WindowProc` folgende Schritte aus:

- Führt nicht Unterklassen aus, wenn das Fenster nicht untergeordnet ist.

- Löscht `m_hWnd`.

- Ruft [onfinalmessage](#onfinalmessage) auf, bevor das Fenster zerstört wird.

Sie können `WindowProc` überschreiben, um einen anderen Mechanismus für die Verarbeitung von Nachrichten bereitzustellen.

## <a name="see-also"></a>Weitere Informationen

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[CComControl-Klasse](../../atl/reference/ccomcontrol-class.md)<br/>
[Klassen Übersicht](../../atl/atl-class-overview.md)
