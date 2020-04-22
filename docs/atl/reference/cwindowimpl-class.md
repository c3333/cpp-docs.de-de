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
ms.openlocfilehash: ea150195f06d12cd6549b9026714d9e1bbf392df
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745999"
---
# <a name="cwindowimpl-class"></a>CWindowImpl-Klasse

Stellt Methoden für das Erstellen eines Fensters oder von Unterklassen eines Fensters bereit

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Die neue Klasse, die von `CWindowImpl` abgeleitet ist.

*TBase*<br/>
Die Basisklasse der Klasse. Standardmäßig ist die Basisklasse [CWindow](../../atl/reference/cwindow-class.md).

*TWinTraits*<br/>
Eine [Traits-Klasse,](../../atl/understanding-window-traits.md) die Stile für Ihr Fenster definiert. Der Standardwert lautet `CControlWinTraits`.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWindowImpl::Erstellen](#create)|Erstellt ein Fenster.|

### <a name="cwindowimplbaset-methods"></a>CWindowImplBaseT-Methoden

|||
|-|-|
|[DefWindowProc](#defwindowproc)|Stellt die Standardverarbeitung von Nachrichten bereit.|
|[GetCurrentMessage](#getcurrentmessage)|Die gibt die aktuelle Nachricht zurück.|
|[GetWindowProc](#getwindowproc)|Gibt die aktuelle Fensterprozedur zurück.|
|[OnFinalMessage](#onfinalmessage)|Wird aufgerufen, nachdem die letzte Nachricht empfangen wurde (in der Regel WM_NCDESTROY).|
|[SubclassWindow](#subclasswindow)|Erstellt Unterklassen eines Fensters.|
|[UnsubclassWindow](#unsubclasswindow)|Stellt ein zuvor untergeordnetes Fenster wieder her.|

### <a name="static-methods"></a>Statische Methoden

|||
|-|-|
|[GetWndClassInfo](#getwndclassinfo)|Gibt eine statische Instanz von [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)zurück, die die Fensterklasseninformationen verwaltet.|
|[WindowProc](#windowproc)|Verarbeitet die Nachrichten, die an das Fenster gesendet werden.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Zeigt auf die ursprüngliche Fensterprozedur der Fensterklasse.|

## <a name="remarks"></a>Bemerkungen

Sie können `CWindowImpl` ein Fenster oder eine Unterklasse eines vorhandenen Fensters erstellen. Die `CWindowImpl` Fensterprozedur verwendet eine Nachrichtenzuordnung, um Nachrichten an die entsprechenden Handler weiterzuleiten.

`CWindowImpl::Create`erstellt ein Fenster basierend auf den Fensterklasseninformationen, die von [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)verwaltet werden. `CWindowImpl`enthält das [DECLARE_WND_CLASS-Makro,](window-class-macros.md#declare_wnd_class) d. h. `CWndClassInfo` registriert eine neue Fensterklasse. Wenn Sie eine vorhandene Fensterklasse überlagern möchten, `CWindowImpl` leiten Sie Ihre Klasse ab und schließen Sie das [DECLARE_WND_SUPERCLASS-Makro](window-class-macros.md#declare_wnd_superclass) ein. In diesem Fall wird mit `CWndClassInfo` eine Fensterklasse registriert, die auf einer vorhandenen Klasse basiert, aber `CWindowImpl::WindowProc` verwendet. Beispiel:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
> Da `CWndClassInfo` nur die Informationen für eine Fensterklasse verwaltet, basiert jedes Fenster, das durch eine Instanz von `CWindowImpl` erstellt wird, auf der gleichen Fensterklasse.

`CWindowImpl` unterstützt auch die Erstellung von Unterklassen von Fenstern. Die `SubclassWindow`-Methode fügt ein vorhandenes Fenster an das `CWindowImpl`-Objekt an und ändert die Fensterprozedur in `CWindowImpl::WindowProc`. Jede Instanz von `CWindowImpl` kann ein anderes Fenster unterordnen.

> [!NOTE]
> Rufen Sie `CWindowImpl` für ein `Create` `SubclassWindow`bestimmtes Objekt entweder oder an. Rufen Sie nicht beide Methoden für dasselbe Objekt auf.

Zusätzlich zu `CWindowImpl`stellt ATL [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) bereit, um ein Fenster zu erstellen, das in einem anderen Objekt enthalten ist.

Der Zerstörungserder der `CWindowImplRoot`Basisklasse stellt sicher, dass das Fenster vor dem Zerstören des Objekts verschwunden ist.

`CWindowImpl`leitet sich `CWindowImplBaseT`von ab , `CWindowImplRoot`der von ableitet, das von `TBase` und [CMessageMap](../../atl/reference/cmessagemap-class.md)abstammt.

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

**Kopfzeile:** atlwin.h

## <a name="cwindowimplcreate"></a><a name="create"></a>CWindowImpl::Erstellen

Erstellt ein Fenster basierend auf einer neuen Fensterklasse.

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

*hWndEltern*<br/>
[in] Das Handle für das übergeordnete oder Besitzerfenster.

*Rect*<br/>
[in] Eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die die Position des Fensters angibt. Der `RECT` kann durch Zeiger oder durch Verweis übergeben werden.

*szWindowName*<br/>
[in] Gibt den Namen des Fensters an. Der Standardwert ist NULL.

*dwStyle*<br/>
[in] Der Stil des Fensters. Dieser Wert wird mit dem Stil kombiniert, der von der Eigenschaftsklasse für das Fenster bereitgestellt wird. Der Standardwert gibt der Traits-Klasse die volle Kontrolle über den Stil. Eine Liste möglicher Werte finden Sie unter [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) im Windows SDK.

*dwExStyle*<br/>
[in] Der erweiterte Fensterstil. Dieser Wert wird mit dem Stil kombiniert, der von der Eigenschaftsklasse für das Fenster bereitgestellt wird. Der Standardwert gibt der Traits-Klasse die volle Kontrolle über den Stil. Eine Liste möglicher Werte finden Sie unter [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) im Windows SDK.

*MenuOrID*<br/>
[in] Bei einem untergeordneten Fenster die Fensterkennung. Für ein Fenster der obersten Ebene ein Menühandle für das Fenster. Der Standardwert ist **0U**.

*lpCreateParam*<br/>
[in] Ein Zeiger auf Fenstererstellungsdaten. Eine vollständige Beschreibung finden Sie in der Beschreibung für den letzten Parameter [für CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw).

### <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, wird das Handle für das neu erstellte Fenster angezeigt. Andernfalls wird NULL verwendet.

### <a name="remarks"></a>Bemerkungen

`Create`registriert zuerst die Fensterklasse, wenn sie noch nicht registriert wurde. Das neu erstellte Fenster `CWindowImpl` wird automatisch an das Objekt angefügt.

> [!NOTE]
> Rufen Sie `Create` nicht auf, wenn Sie bereits [SubclassWindow](#subclasswindow)aufgerufen haben.

Um eine Fensterklasse zu verwenden, die auf einer vorhandenen `CWindowImpl` Fensterklasse basiert, leiten Sie Ihre Klasse ab und schließen Sie das [DECLARE_WND_SUPERCLASS-Makro](window-class-macros.md#declare_wnd_superclass) ein. Die Fensterprozedur der vorhandenen Fensterklasse wird in [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)gespeichert. Weitere Informationen finden Sie in der [CWindowImpl-Übersicht.](../../atl/reference/cwindowimpl-class.md)

> [!NOTE]
> Wenn 0 als Wert für den *Parameter MenuOrID* verwendet wird, muss es als 0U (der Standardwert) angegeben werden, um einen Compilerfehler zu vermeiden.

## <a name="cwindowimpldefwindowproc"></a><a name="defwindowproc"></a>CWindowImpl::DefWindowProc

Wird von [WindowProc](#windowproc) aufgerufen, um Nachrichten zu verarbeiten, die nicht von der Nachrichtenzuordnung verarbeitet werden.

```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```

### <a name="parameters"></a>Parameter

*uMsg*<br/>
[in] Die an das Fenster gesendete Nachricht.

*wParam*<br/>
[in] Zusätzliche nachrichtenspezifische Informationen.

*lParam*<br/>
[in] Zusätzliche nachrichtenspezifische Informationen.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis der Nachrichtenverarbeitung.

### <a name="remarks"></a>Bemerkungen

Ruft standardmäßig `DefWindowProc` die [Funktion CallWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) Win32 auf, um die Nachrichteninformationen an die in [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)angegebene Fensterprozedur zu senden.

Die Funktion ohne Parameter ruft automatisch die benötigten Parameter aus der aktuellen Meldung ab.

## <a name="cwindowimplgetcurrentmessage"></a><a name="getcurrentmessage"></a>CWindowImpl::GetCurrentMessage

Gibt die aktuelle Nachricht zurück, die in der `MSG` Struktur verpackt ist.

```
const MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Meldung.

## <a name="cwindowimplgetwindowproc"></a><a name="getwindowproc"></a>CWindowImpl::GetWindowProc

Gibt `WindowProc`zurück, die aktuelle Fensterprozedur.

```
virtual WNDPROC GetWindowProc();
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Fensterprozedur.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, um die Fensterprozedur durch Ihre eigene zu ersetzen.

## <a name="cwindowimplgetwndclassinfo"></a><a name="getwndclassinfo"></a>CWindowImpl::GetWndClassInfo

Wird von [Create](#create) aufgerufen, um auf die Fensterklasseninformationen zuzugreifen.

```
static CWndClassInfo& GetWndClassInfo();
```

### <a name="return-value"></a>Rückgabewert

Eine statische Instanz von [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md).

### <a name="remarks"></a>Bemerkungen

Ruft diese `CWindowImpl` Methode standardmäßig über das [DECLARE_WND_CLASS-Makro](window-class-macros.md#declare_wnd_class) ab, das eine neue Fensterklasse angibt.

Um eine vorhandene Fensterklasse zu überklassen, leiten Sie Ihre Klasse ab, `CWindowImpl` und schließen Sie das [DECLARE_WND_SUPERCLASS-Makro](window-class-macros.md#declare_wnd_superclass) ein, um zu überschreiben. `GetWndClassInfo` Weitere Informationen finden Sie in der [CWindowImpl-Übersicht.](../../atl/reference/cwindowimpl-class.md)

Neben der Verwendung der DECLARE_WND_CLASS- und `GetWndClassInfo` DECLARE_WND_SUPERCLASS-Makros können Sie auch ihre eigene Implementierung überschreiben.

## <a name="cwindowimplm_pfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a>CWindowImpl::m_pfnSuperWindowProc

Zeigt abhängig vom Fenster auf eine der folgenden Fensterprozeduren.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Bemerkungen

|Art des Fensters|Fensterprozedur|
|--------------------|----------------------|
|Ein Fenster, das auf einer neuen Fensterklasse basiert und durch das [DECLARE_WND_CLASS-Makro](window-class-macros.md#declare_wnd_class) angegeben wird.|Die [DefWindowProc](/windows/win32/api/winuser/nf-winuser-defwindowprocw) Win32-Funktion.|
|Ein Fenster, das auf einer Fensterklasse basiert, die eine vorhandene Klasse ändert, die durch das [DECLARE_WND_SUPERCLASS-Makro](window-class-macros.md#declare_wnd_superclass) angegeben wird.|Die Fensterprozedur der vorhandenen Fensterklasse.|
|Ein unterklassiertes Fenster.|Die ursprüngliche Fensterprozedur des unterklassigen Fensters.|

[CWindowImpl::DefWindowProc](#defwindowproc) sendet Nachrichteninformationen an die `m_pfnSuperWindowProc`in gespeicherte Fensterprozedur .

## <a name="cwindowimplonfinalmessage"></a><a name="onfinalmessage"></a>CWindowImpl::OnFinalMessage

Wird nach dem Empfang der letzten Nachricht aufgerufen (in der Regel WM_NCDESTROY).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
[in] Ein Griff zum Fenster wird zerstört.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung `OnFinalMessage` von tut nichts, aber Sie können diese Funktion überschreiben, um die Bereinigung zu behandeln, bevor Sie ein Fenster zerstören. Wenn Sie Ihr Objekt bei der Fensterzerstörung automatisch löschen möchten, können Sie **dies löschen;** in dieser Funktion.

## <a name="cwindowimplsubclasswindow"></a><a name="subclasswindow"></a>CWindowImpl::SubclassWindow

Unterklassen das von *hWnd* identifizierte Fenster `CWindowImpl` und fügen es an das Objekt an.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
[in] Das Handle für das Fenster, das unterklassifiziert wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Fenster erfolgreich unterklassig ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Das unterklassige Fenster verwendet jetzt [CWindowImpl::WindowProc](#windowproc). Die ursprüngliche Fensterprozedur wird in [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)gespeichert.

> [!NOTE]
> Rufen Sie `SubclassWindow` nicht auf, wenn Sie bereits [Create](#create)aufgerufen haben.

## <a name="cwindowimplunsubclasswindow"></a><a name="unsubclasswindow"></a>CWindowImpl::UnsubclassWindow

Trennt das unterklassige Fenster `CWindowImpl` vom Objekt und stellt die ursprüngliche Fensterprozedur wieder her, die in [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)gespeichert wurde.

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>Rückgabewert

Das Handle für das Fenster, das zuvor unterclassiert wurde.

## <a name="cwindowimplwindowproc"></a><a name="windowproc"></a>CWindowImpl::WindowProc

Diese statische Funktion implementiert die Fensterprozedur.

```
static LRESULT CALLBACK WindowProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
[in] Das Handle zum Fenster.

*uMsg*<br/>
[in] Die an das Fenster gesendete Nachricht.

*wParam*<br/>
[in] Zusätzliche nachrichtenspezifische Informationen.

*lParam*<br/>
[in] Zusätzliche nachrichtenspezifische Informationen.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis der Nachrichtenverarbeitung.

### <a name="remarks"></a>Bemerkungen

`WindowProc`verwendet die Standardnachrichtenzuordnung (deklariert mit [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)), um Nachrichten an die entsprechenden Handler weiterzuleiten. `WindowProc` Ruft bei Bedarf [DefWindowProc](#defwindowproc) zur zusätzlichen Nachrichtenverarbeitung auf. Wenn die endgültige Nachricht nicht `WindowProc` behandelt wird, gehen Sie wie folgt vor:

- Führt eine Unterklassenunterklasse aus, wenn das Fenster nicht unterklassifiziert war.

- Löscht `m_hWnd`.

- Ruft [OnFinalMessage auf,](#onfinalmessage) bevor das Fenster zerstört wird.

Sie können `WindowProc` überschreiben, um einen anderen Mechanismus für die Verarbeitung von Nachrichten bereitzustellen.

## <a name="see-also"></a>Weitere Informationen

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[CComControl-Klasse](../../atl/reference/ccomcontrol-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
