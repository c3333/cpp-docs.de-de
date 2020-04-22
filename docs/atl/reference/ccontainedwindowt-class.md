---
title: CcontainedWindowT-Klasse
ms.date: 11/04/2016
f1_keywords:
- CContainedWindowT
- ATLWIN/ATL::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::Create
- ATLWIN/ATL::CContainedWindowT::DefWindowProc
- ATLWIN/ATL::CContainedWindowT::GetCurrentMessage
- ATLWIN/ATL::CContainedWindowT::RegisterWndSuperclass
- ATLWIN/ATL::CContainedWindowT::SubclassWindow
- ATLWIN/ATL::CContainedWindowT::SwitchMessageMap
- ATLWIN/ATL::CContainedWindowT::UnsubclassWindow
- ATLWIN/ATL::CContainedWindowT::WindowProc
- ATLWIN/ATL::CContainedWindowT::m_dwMsgMapID
- ATLWIN/ATL::CContainedWindowT::m_lpszClassName
- ATLWIN/ATL::CContainedWindowT::m_pfnSuperWindowProc
- ATLWIN/ATL::CContainedWindowT::m_pObject
helpviewer_keywords:
- CContainedWindow class
- contained windows
- CContainedWindowT class
ms.assetid: cde0ca36-9347-4068-995a-d294dae57ca9
ms.openlocfilehash: 7b89346bbc62cdda808b193a199fdf121f052ebb
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747745"
---
# <a name="ccontainedwindowt-class"></a>CcontainedWindowT-Klasse

Diese Klasse implementiert ein Fenster, das in einem anderen Objekt enthalten ist.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>
class CContainedWindowT : public TBase
```

#### <a name="parameters"></a>Parameter

*TBase*<br/>
Die Basisklasse Ihrer neuen Klasse. Die Standardbasisklasse `CWindow`ist .

*TWinTraits*<br/>
Eine Trait-Klasse, die Formatvorlagen für das Fenster definiert. Der Standardwert lautet `CControlWinTraits`.

> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md) ist eine `CContainedWindowT`Spezialisierung von . Wenn Sie die Basisklasse oder -merkmale `CContainedWindowT` ändern möchten, verwenden Sie dies direkt.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CcontainedWindowT::CcontainedWindowT](#ccontainedwindowt)|Konstruktor. Initialisiert Datenmember, um anzugeben, welche Nachrichtenzuordnung die Nachrichten des enthaltenen Fensters verarbeitet.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CcontainedWindowT::Erstellen](#create)|Erstellt ein Fenster.|
|[CContainedWindowT::DefWindowProc](#defwindowproc)|Stellt die Standardverarbeitung von Nachrichten bereit.|
|[CcontainedWindowT::GetCurrentMessage](#getcurrentmessage)|Die gibt die aktuelle Nachricht zurück.|
|[CContainedWindowT::RegisterWndSuper-Klasse](#registerwndsuperclass)|Registriert die Fensterklasse des enthaltenen Fensters.|
|[CContainedWindowT::SubclassWindow](#subclasswindow)|Erstellt Unterklassen eines Fensters.|
|[CcontainedWindowT::SwitchMessageMap](#switchmessagemap)|Ändert, welche Meldungszuordnung zum Verarbeiten der Nachrichten des enthaltenen Fensters verwendet wird.|
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|Stellt ein zuvor untergeordnetes Fenster wieder her.|
|[CContainedWindowT::WindowProc](#windowproc)|(Statisch) Verarbeitet Nachrichten, die an das enthaltene Fenster gesendet werden.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|Gibt an, welche Meldungszuordnung die Nachrichten des enthaltenen Fensters verarbeitet.|
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|Gibt den Namen einer vorhandenen Fensterklasse an, auf der eine neue Fensterklasse basiert.|
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Zeigt auf die ursprüngliche Fensterprozedur der Fensterklasse.|
|[CContainedWindowT::m_pObject](#m_pobject)|Zeigt auf das enthaltende Objekt.|

## <a name="remarks"></a>Bemerkungen

`CContainedWindowT`implementiert ein Fenster, das in einem anderen Objekt enthalten ist. `CContainedWindowT`Die Fensterprozedur von verwendet eine Nachrichtenzuordnung im enthaltenden Objekt, um Nachrichten an die entsprechenden Handler weiterzuleiten. Beim Erstellen `CContainedWindowT` eines Objekts geben Sie an, welche Meldungszuordnung verwendet werden soll.

`CContainedWindowT`ermöglicht es Ihnen, ein neues Fenster zu erstellen, indem Sie eine vorhandene Fensterklasse überklassen. Die `Create` Methode registriert zuerst eine Fensterklasse, die auf `CContainedWindowT::WindowProc`einer vorhandenen Klasse basiert, aber verwendet. `Create`erstellt dann ein Fenster basierend auf dieser neuen Fensterklasse. Jede Instanz `CContainedWindowT` von kann eine andere Fensterklasse überlagern.

`CContainedWindowT` unterstützt auch die Erstellung von Unterklassen von Fenstern. Die `SubclassWindow`-Methode fügt ein vorhandenes Fenster an das `CContainedWindowT`-Objekt an und ändert die Fensterprozedur in `CContainedWindowT::WindowProc`. Jede Instanz von `CContainedWindowT` kann ein anderes Fenster unterordnen.

> [!NOTE]
> Rufen Sie `CContainedWindowT` für ein `Create` `SubclassWindow`bestimmtes Objekt entweder oder an. Sie sollten nicht beide Methoden für dasselbe Objekt aufrufen.

Wenn Sie das **Steuerelement Hinzufügen basierend auf** der Option im ATL-Projekt-Assistenten verwenden, fügt der Assistent automatisch einen `CContainedWindowT` Datenmember zur Klasse hinzu, die das Steuerelement implementiert. Das folgende Beispiel zeigt, wie das enthaltene Fenster deklariert wird:

[!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]

[!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]

[!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]

|Weitere Informationen über|Finden Sie unter|
|--------------------------------|---------|
|Erstellen von Steuerelementen|[ATL-Tutorial](../../atl/active-template-library-atl-tutorial.md)|
|Verwenden von Fenstern in ATL|[ATL-Fensterklassen](../../atl/atl-window-classes.md)|
|ATL-Projekt-Assistent|[Erstellen eines ATL-Projekts](../../atl/reference/creating-an-atl-project.md)|
|Windows|[Windows](/windows/win32/winmsg/windows) und nachfolgende Themen im Windows SDK|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`TBase`

`CContainedWindowT`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlwin.h

## <a name="ccontainedwindowtccontainedwindowt"></a><a name="ccontainedwindowt"></a>CcontainedWindowT::CcontainedWindowT

Der Konstruktor initialisiert Datenmember.

```
CContainedWindowT(
    LPTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);

CContainedWindowT(
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0)
    CContainedWindowT();
```

### <a name="parameters"></a>Parameter

*lpszClassName*<br/>
[in] Der Name einer vorhandenen Fensterklasse, auf der das enthaltene Fenster basiert.

*pObject*<br/>
[in] Ein Zeiger auf das enthaltende Objekt, das die Nachrichtenzuordnung deklariert. Die Klasse dieses Objekts muss von [CMessageMap](../../atl/reference/cmessagemap-class.md)abstammen.

*dwMsgMapID*<br/>
[in] Identifiziert die Nachrichtenzuordnung, die die Nachrichten des enthaltenen Fensters verarbeitet. Der Standardwert 0 gibt die mit [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)deklarierte Standardmeldungszuordnung an. Um eine alternative Meldungszuordnung zu verwenden, die `msgMapID`mit [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)deklariert wurde, übergeben Sie .

### <a name="remarks"></a>Bemerkungen

Wenn Sie ein neues Fenster über [Erstellen](#create)erstellen möchten, müssen Sie den Namen einer vorhandenen Fensterklasse für den Parameter *lpszClassName* übergeben. Ein Beispiel finden Sie in der [CContainedWindow-Übersicht.](../../atl/reference/ccontainedwindowt-class.md)

Es gibt drei Konstruktoren:

- Der Konstruktor mit drei Argumenten ist das Konstruktor, das normalerweise aufgerufen wird.

- Der Konstruktor mit zwei Argumenten `TBase::GetWndClassName`verwendet den Klassennamen aus .

- Der Konstruktor ohne Argumente wird verwendet, wenn Sie die Argumente später angeben möchten. Sie müssen beim späteren Aufruf `Create`den Namen der Fensterklasse, das Meldungszuordnungsobjekt und die Meldungszuordnungs-ID angeben.

Wenn Sie ein vorhandenes Fenster über [SubclassWindow](#subclasswindow)unterklassigen, wird der *wert lpszClassName* nicht verwendet. Daher können Sie NULL für diesen Parameter übergeben.

## <a name="ccontainedwindowtcreate"></a><a name="create"></a>CcontainedWindowT::Erstellen

Ruft [die RegisterWndSuperclass](#registerwndsuperclass) auf, um eine Fensterklasse zu registrieren, die auf einer vorhandenen Klasse basiert, aber [CContainedWindowT::WindowProc](#windowproc)verwendet.

```
HWND Create(
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    LPCTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```

### <a name="parameters"></a>Parameter

*lpszClassName*<br/>
[in] Der Name einer vorhandenen Fensterklasse, auf der das enthaltene Fenster basiert.

*pObject*<br/>
[in] Ein Zeiger auf das enthaltende Objekt, das die Nachrichtenzuordnung deklariert. Die Klasse dieses Objekts muss von [CMessageMap](../../atl/reference/cmessagemap-class.md)abstammen.

*dwMsgMapID*<br/>
[in] Identifiziert die Nachrichtenzuordnung, die die Nachrichten des enthaltenen Fensters verarbeitet. Der Standardwert 0 gibt die mit [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)deklarierte Standardmeldungszuordnung an. Um eine alternative Meldungszuordnung zu verwenden, die `msgMapID`mit [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)deklariert wurde, übergeben Sie .

*hWndEltern*<br/>
[in] Das Handle für das übergeordnete oder Besitzerfenster.

*Rect*<br/>
[in] Eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die die Position des Fensters angibt. Der `RECT` kann durch Zeiger oder durch Verweis übergeben werden.

*szWindowName*<br/>
[in] Gibt den Namen des Fensters an. Der Standardwert ist NULL.

*dwStyle*<br/>
[in] Der Stil des Fensters. Der Standardwert ist &#124; WS_VISIBLE WS_CHILD. Eine Liste möglicher Werte finden Sie unter [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) im Windows SDK.

*dwExStyle*<br/>
[in] Der erweiterte Fensterstil. Der Standardwert ist 0, d. h. kein erweiterter Stil. Eine Liste möglicher Werte finden Sie unter [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) im Windows SDK.

*MenuOrID*<br/>
[in] Bei einem untergeordneten Fenster die Fensterkennung. Für ein Fenster der obersten Ebene ein Menühandle für das Fenster. Der Standardwert ist **0U**.

*lpCreateParam*<br/>
[in] Ein Zeiger auf Fenstererstellungsdaten. Eine vollständige Beschreibung finden Sie in der Beschreibung für den letzten Parameter [für CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw).

### <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, wird das Handle für das neu erstellte Fenster angezeigt. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Der vorhandene Fensterklassenname wird in [m_lpszClassName](#m_lpszclassname)gespeichert. `Create`erstellt dann ein Fenster basierend auf dieser neuen Klasse. Das neu erstellte Fenster `CContainedWindowT` wird automatisch an das Objekt angefügt.

> [!NOTE]
> Rufen Sie `Create` nicht auf, wenn Sie bereits [SubclassWindow](#subclasswindow)aufgerufen haben.

> [!NOTE]
> Wenn 0 als Wert für den *Parameter MenuOrID* verwendet wird, muss es als 0U (der Standardwert) angegeben werden, um einen Compilerfehler zu vermeiden.

## <a name="ccontainedwindowtdefwindowproc"></a><a name="defwindowproc"></a>CContainedWindowT::DefWindowProc

Wird von [WindowProc](#windowproc) aufgerufen, um Nachrichten zu verarbeiten, die nicht von der Nachrichtenzuordnung verarbeitet werden.

```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
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

## <a name="ccontainedwindowtgetcurrentmessage"></a><a name="getcurrentmessage"></a>CcontainedWindowT::GetCurrentMessage

Gibt die aktuelle`m_pCurrentMsg`Meldung zurück ( ).

```
const _ATL_MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Nachricht, die `MSG` in der Struktur gepackt ist.

## <a name="ccontainedwindowtm_dwmsgmapid"></a><a name="m_dwmsgmapid"></a>CContainedWindowT::m_dwMsgMapID

Enthält den Bezeichner der Nachrichtenzuordnung, die derzeit für das enthaltene Fenster verwendet wird.

```
DWORD m_dwMsgMapID;
```

### <a name="remarks"></a>Bemerkungen

Diese Meldungszuordnung muss im enthaltenden Objekt deklariert werden.

Die Mit [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)deklarierte Standardmeldungszuordnung wird immer mit Null gekennzeichnet. Eine alternative Meldungszuordnung, die mit [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)deklariert wurde, wird durch `msgMapID`identifiziert.

`m_dwMsgMapID`wird zuerst vom Konstruktor initialisiert und kann durch Aufrufen von [SwitchMessageMap](#switchmessagemap)geändert werden. Ein Beispiel finden Sie in der [CContainedWindowT-Übersicht](../../atl/reference/ccontainedwindowt-class.md).

## <a name="ccontainedwindowtm_lpszclassname"></a><a name="m_lpszclassname"></a>CContainedWindowT::m_lpszClassName

Gibt den Namen einer vorhandenen Fensterklasse an.

```
LPTSTR m_lpszClassName;
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie ein Fenster erstellen, registriert [Create](#create) eine neue Fensterklasse, die auf dieser vorhandenen Klasse basiert, aber [CContainedWindowT::WindowProc](#windowproc)verwendet.

`m_lpszClassName`wird vom Konstruktor initialisiert. Ein Beispiel finden Sie in der [CContainedWindowT-Übersicht.](../../atl/reference/ccontainedwindowt-class.md)

## <a name="ccontainedwindowtm_pfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a>CContainedWindowT::m_pfnSuperWindowProc

Wenn das enthaltene Fenster `m_pfnSuperWindowProc` unterklassifiziert ist, zeigt es auf die ursprüngliche Fensterprozedur der Fensterklasse.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Bemerkungen

Wenn das enthaltene Fenster überklass ist, d. h. es basiert `m_pfnSuperWindowProc` auf einer Fensterklasse, die eine vorhandene Klasse ändert, zeigt es auf die Fensterprozedur der vorhandenen Fensterklasse.

Die [DefWindowProc-Methode](#defwindowproc) sendet Nachrichteninformationen an `m_pfnSuperWindowProc`die in gespeicherte Fensterprozedur .

## <a name="ccontainedwindowtm_pobject"></a><a name="m_pobject"></a>CContainedWindowT::m_pObject

Zeigt auf das `CContainedWindowT` Objekt, das das Objekt enthält.

```
CMessageMap* m_pObject;
```

### <a name="remarks"></a>Bemerkungen

Dieser Container, dessen Klasse von [CMessageMap](../../atl/reference/cmessagemap-class.md)ableiten muss, deklariert die Nachrichtenzuordnung, die vom enthaltenen Fenster verwendet wird.

`m_pObject`wird vom Konstruktor initialisiert. Ein Beispiel finden Sie in der [CContainedWindowT-Übersicht.](../../atl/reference/ccontainedwindowt-class.md)

## <a name="ccontainedwindowtregisterwndsuperclass"></a><a name="registerwndsuperclass"></a>CContainedWindowT::RegisterWndSuper-Klasse

Wird von [Create](#create) aufgerufen, um die Fensterklasse des enthaltenen Fensters zu registrieren.

```
ATOM RegisterWndSuperClass();
```

### <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, ein Atom, das die registrierte Fensterklasse eindeutig identifiziert; andernfalls Null.

### <a name="remarks"></a>Bemerkungen

Diese Fensterklasse basiert auf einer vorhandenen Klasse, verwendet jedoch [CContainedWindowT::WindowProc](#windowproc). Der Name und die Fensterprozedur der vorhandenen Fensterklasse werden in [m_lpszClassName](#m_lpszclassname) bzw. [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)gespeichert.

## <a name="ccontainedwindowtsubclasswindow"></a><a name="subclasswindow"></a>CContainedWindowT::SubclassWindow

Unterklassen das von *hWnd* identifizierte Fenster `CContainedWindowT` und fügen es an das Objekt an.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
[in] Das Handle für das Fenster, das unterklassifiziert wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Fenster erfolgreich unterklassig ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Das unterklassige Fenster verwendet jetzt [CContainedWindowT::WindowProc](#windowproc). Die ursprüngliche Fensterprozedur wird in [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)gespeichert.

> [!NOTE]
> Rufen Sie `SubclassWindow` nicht auf, wenn Sie bereits [Create](#create)aufgerufen haben.

## <a name="ccontainedwindowtswitchmessagemap"></a><a name="switchmessagemap"></a>CcontainedWindowT::SwitchMessageMap

Ändert, welche Meldungszuordnung zum Verarbeiten der Nachrichten des enthaltenen Fensters verwendet wird.

```cpp
void SwitchMessageMap(DWORD dwMsgMapID);
```

### <a name="parameters"></a>Parameter

*dwMsgMapID*<br/>
[in] Der Nachrichtenzuordnungsbezeichner. Um die mit [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)deklarierte Standardmeldungszuordnung zu verwenden, übergeben Sie Null. Um eine alternative Meldungszuordnung zu verwenden, die `msgMapID`mit [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)deklariert wurde, übergeben Sie .

### <a name="remarks"></a>Bemerkungen

Die Meldungszuordnung muss im enthaltenden Objekt definiert werden.

Sie geben zunächst den Nachrichtenzuordnungsbezeichner im Konstruktor an.

## <a name="ccontainedwindowtunsubclasswindow"></a><a name="unsubclasswindow"></a>CContainedWindowT::UnsubclassWindow

Trennt das unterklassige Fenster `CContainedWindowT` vom Objekt und stellt die ursprüngliche Fensterprozedur wieder her, die in [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)gespeichert wurde.

```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```

### <a name="parameters"></a>Parameter

*bForce*<br/>
[in] Legen Sie TRUE fest, dass die ursprüngliche Fensterprozedur wiederhergestellt `CContainedWindowT` wird, auch wenn die Fensterprozedur für dieses Objekt derzeit nicht aktiv ist. Wenn *bForce* auf FALSE festgelegt ist `CContainedWindowT` und die Fensterprozedur für dieses Objekt derzeit nicht aktiv ist, wird die ursprüngliche Fensterprozedur nicht wiederhergestellt.

### <a name="return-value"></a>Rückgabewert

Das Handle für das Fenster, das zuvor unterclassiert wurde. Wenn *bForce* auf FALSE gesetzt ist `CContainedWindowT` und die Fensterprozedur für dieses Objekt derzeit nicht aktiv ist, gibt NULL zurück.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode nur, wenn Sie die ursprüngliche Fensterprozedur wiederherstellen möchten, bevor das Fenster zerstört wird. Andernfalls wird [WindowProc](#windowproc) dies automatisch tun, wenn das Fenster zerstört wird.

## <a name="ccontainedwindowtwindowproc"></a><a name="windowproc"></a>CContainedWindowT::WindowProc

Diese statische Methode implementiert die Fensterprozedur.

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

`WindowProc`leitet Nachrichten an die Nachrichtenzuordnung weiter, die von [m_dwMsgMapID](#m_dwmsgmapid)identifiziert wurde. `WindowProc` Ruft bei Bedarf [DefWindowProc](#defwindowproc) zur zusätzlichen Nachrichtenverarbeitung auf.

## <a name="see-also"></a>Weitere Informationen

[CWindow-Klasse](../../atl/reference/cwindow-class.md)<br/>
[CWindowImpl-Klasse](../../atl/reference/cwindowimpl-class.md)<br/>
[CMessageMap-Klasse](../../atl/reference/cmessagemap-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
