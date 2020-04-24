---
title: CMDIFrameWnd-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMDIFrameWnd
- AFXWIN/CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CreateClient
- AFXWIN/CMDIFrameWnd::CreateNewChild
- AFXWIN/CMDIFrameWnd::GetWindowMenuPopup
- AFXWIN/CMDIFrameWnd::MDIActivate
- AFXWIN/CMDIFrameWnd::MDICascade
- AFXWIN/CMDIFrameWnd::MDIGetActive
- AFXWIN/CMDIFrameWnd::MDIIconArrange
- AFXWIN/CMDIFrameWnd::MDIMaximize
- AFXWIN/CMDIFrameWnd::MDINext
- AFXWIN/CMDIFrameWnd::MDIPrev
- AFXWIN/CMDIFrameWnd::MDIRestore
- AFXWIN/CMDIFrameWnd::MDISetMenu
- AFXWIN/CMDIFrameWnd::MDITile
helpviewer_keywords:
- CMDIFrameWnd [MFC], CMDIFrameWnd
- CMDIFrameWnd [MFC], CreateClient
- CMDIFrameWnd [MFC], CreateNewChild
- CMDIFrameWnd [MFC], GetWindowMenuPopup
- CMDIFrameWnd [MFC], MDIActivate
- CMDIFrameWnd [MFC], MDICascade
- CMDIFrameWnd [MFC], MDIGetActive
- CMDIFrameWnd [MFC], MDIIconArrange
- CMDIFrameWnd [MFC], MDIMaximize
- CMDIFrameWnd [MFC], MDINext
- CMDIFrameWnd [MFC], MDIPrev
- CMDIFrameWnd [MFC], MDIRestore
- CMDIFrameWnd [MFC], MDISetMenu
- CMDIFrameWnd [MFC], MDITile
ms.assetid: fa8736e6-511b-4c51-8b4d-eba78378aeb9
ms.openlocfilehash: d5c9bc12e6c3f0ab4742a940547087c9742caf73
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754545"
---
# <a name="cmdiframewnd-class"></a>CMDIFrameWnd-Klasse

Stellt die Funktionalität eines untergeordneten Windows-MDI-Rahmenfensters (Multiple Document Interface) bereit, zusammen mit Membern zum Verwalten des Fensters.

## <a name="syntax"></a>Syntax

```
class CMDIFrameWnd : public CFrameWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMDIFrameWnd::CMDIFrameWnd](#cmdiframewnd)|Erstellt ein Objekt vom Typ `CMDIFrameWnd`.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMDIFrameWnd::CreateClient](#createclient)|Erstellt ein Windows MDICLIENT-Fenster für diese `CMDIFrameWnd`. Wird von `OnCreate` der `CWnd`Memberfunktion von aufgerufen.|
|[CMDIFrameWnd::CreateNewChild](#createnewchild)|Erstellt ein neues untergeordnetes Fenster.|
|[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)|Gibt das Fenster-Popupmenü zurück.|
|[CMDIFrameWnd::MDIActivate](#mdiactivate)|Aktiviert ein anderes untergeordnetes MDI-Fenster.|
|[CMDIFrameWnd::MDICascade](#mdicascade)|Ordnet alle untergeordneten Fenster in einem kaskadierten Format an.|
|[CMDIFrameWnd::MDIGetActive](#mdigetactive)|Ruft das aktuell aktive untergeordnete MDI-Fenster zusammen mit einem Flag ab, das angibt, ob das untergeordnete Element maximiert ist oder nicht.|
|[CMDIFrameWnd::MDIIconArrange](#mdiiconarrange)|Ordnet alle minimierten untergeordneten Dokumentfenster an.|
|[CMDIFrameWnd::MDIMaximieren](#mdimaximize)|Maximiert ein untergeordnetes MDI-Fenster.|
|[CMDIFrameWnd::MDINext](#mdinext)|Aktiviert das untergeordnete Fenster direkt hinter dem aktuell aktiven untergeordneten Fenster und platziert das aktuell aktive untergeordnete Fenster hinter allen anderen untergeordneten Fenstern.|
|[CMDIFrameWnd::MDIPrev](#mdiprev)|Aktiviert das vorherige untergeordnete Fenster und platziert das aktuell aktive untergeordnete Fenster direkt dahinter.|
|[CMDIFrameWnd::MDIRestore](#mdirestore)|Stellt ein untergeordnetes MDI-Fenster von einer maximierten oder minimierten Größe wieder her.|
|[CMDIFrameWnd::MDISetMenu](#mdisetmenu)|Ersetzt das Menü eines MDI-Rahmenfensters, das Fenster-Popupmenü oder beides.|
|[CMDIFrameWnd::MDITile](#mditile)|Ordnet alle untergeordneten Fenster in einem gekachelten Format an.|

## <a name="remarks"></a>Bemerkungen

Um ein nützliches MDI-Rahmenfenster für Ihre `CMDIFrameWnd`Anwendung zu erstellen, leiten Sie eine Klasse aus ab. Fügen Sie der abgeleiteten Klasse Membervariablen hinzu, um daten zu speichern, die für Ihre Anwendung spezifisch sind. Implementieren Sie Meldungshandler-Memberfunktionen und eine Meldungszuordnung in der abgeleiteten Klasse, um anzugeben, was passiert, wenn Meldungen an das Fenster weitergeleitet werden.

Sie können ein MDI-Rahmenfenster erstellen, indem Sie `CFrameWnd`die [Memberfunktion Erstellen](../../mfc/reference/cframewnd-class.md#create) oder [LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe) von aufrufen.

Bevor Sie `Create` `LoadFrame`oder aufrufen, müssen Sie das Rahmenfensterobjekt auf dem Heap mit dem **neuen** C++-Operator erstellen. Vor `Create` dem Aufruf können Sie auch eine Fensterklasse mit der globalen Funktion [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) registrieren, um das Symbol und die Klassenstile für den Frame festzulegen.

Verwenden `Create` Sie die Memberfunktion, um die Erstellungsparameter des Frames als unmittelbare Argumente zu übergeben.

`LoadFrame`erfordert weniger `Create`Argumente als und ruft stattdessen die meisten Standardwerte aus Ressourcen ab, einschließlich Beschriftung, Symbol, Beschleunigertabelle und Menü des Frames. Um von `LoadFrame`zugreifen zu können, müssen alle diese Ressourcen über dieselbe Ressourcen-ID verfügen (z. B. IDR_MAINFRAME).

Obwohl `MDIFrameWnd` von `CFrameWnd`abgeleitet ist, muss `CMDIFrameWnd` eine von abgeleitete Rahmenfensterklasse nicht mit `DECLARE_DYNCREATE`deklariert werden.

Die `CMDIFrameWnd` Klasse erbt einen Großteil `CFrameWnd`ihrer Standardimplementierung von . Eine detaillierte Liste dieser Features finden Sie in der [CFrameWnd-Klassenbeschreibung.](../../mfc/reference/cframewnd-class.md) Die `CMDIFrameWnd` Klasse verfügt über die folgenden zusätzlichen Funktionen:

- Ein MDI-Rahmenfenster verwaltet das MDICLIENT-Fenster und positioniert es in Verbindung mit Steuerleisten neu. Das MDI-Clientfenster ist das direkte übergeordnete Element von untergeordneten MDI-Rahmenfenstern. Die WS_HSCROLL und WS_VSCROLL Fensterstile, die in einem `CMDIFrameWnd` Auftragen auf das MDI-Clientfenster und nicht auf das Hauptrahmenfenster angegeben sind, damit der Benutzer den MDI-Clientbereich scrollen kann (z. B. im Windows-Programm-Manager).

- Ein MDI-Rahmenfenster besitzt ein Standardmenü, das als Menüleiste verwendet wird, wenn kein aktives untergeordnetes MDI-Fenster vorhanden ist. Wenn ein aktives MDI-Kind vorhanden ist, wird die Menüleiste des MDI-Rahmenfensters automatisch durch das untergeordnete MDI-Fenstermenü ersetzt.

- Ein MDI-Rahmenfenster funktioniert in Verbindung mit dem aktuellen untergeordneten MDI-Fenster, falls vorhanden. Beispielsweise werden Befehlsmeldungen vor dem MDI-Rahmenfenster an das aktuell aktive MDI-Kind delegiert.

- Ein MDI-Rahmenfenster verfügt über Standardhandler für die folgenden Standardmenübefehle des Fensters:

  - ID_WINDOW_TILE_VERT

  - ID_WINDOW_TILE_HORZ

  - ID_WINDOW_CASCADE

  - ID_WINDOW_ARRANGE

- Ein MDI-Rahmenfenster verfügt auch über eine Implementierung von ID_WINDOW_NEW, die einen neuen Rahmen und eine neue Ansicht für das aktuelle Dokument erstellt. Eine Anwendung kann diese Standardbefehlsimplementierungen überschreiben, um die MDI-Fensterbehandlung anzupassen.

Verwenden Sie den **C++-Löschoperator** nicht, um ein Rahmenfenster zu zerstören. Verwenden Sie stattdessen `CWnd::DestroyWindow`. Die `CFrameWnd` Implementierung `PostNcDestroy` von löscht das C++-Objekt, wenn das Fenster zerstört wird. Wenn der Benutzer das Rahmenfenster `OnClose` schließt, `DestroyWindow`ruft der Standardhandler auf .

Weitere Informationen `CMDIFrameWnd`zu finden Sie unter [Frame Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIFrameWnd`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="cmdiframewndcmdiframewnd"></a><a name="cmdiframewnd"></a>CMDIFrameWnd::CMDIFrameWnd

Erstellt ein `CMDIFrameWnd`-Objekt.

```
CMDIFrameWnd();
```

### <a name="remarks"></a>Bemerkungen

Rufen `Create` Sie `LoadFrame` die or member-Funktion auf, um das sichtbare MDI-Rahmenfenster zu erstellen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]

## <a name="cmdiframewndcreateclient"></a><a name="createclient"></a>CMDIFrameWnd::CreateClient

Erstellt das MDI-Clientfenster, in dem die Objekte verwaltet werden. `CMDIChildWnd`

```
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Parameter

*lpCreateStruct*<br/>
Ein langer Zeiger auf eine [CREATESTRUCT-Struktur.](/windows/win32/api/winuser/ns-winuser-createstructw)

*pWindowMenu*<br/>
Ein Zeiger auf das Fenster-Popupmenü.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion sollte aufgerufen werden, `OnCreate` wenn Sie die Memberfunktion direkt überschreiben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]

## <a name="cmdiframewndcreatenewchild"></a><a name="createnewchild"></a>CMDIFrameWnd::CreateNewChild

Erstellt ein neues untergeordnetes Fenster.

```
CMDIChildWnd* CreateNewChild(
    CRuntimeClass* pClass,
    UINT nResource,
    HMENU hMenu = NULL,
    HACCEL hAccel = NULL);
```

### <a name="parameters"></a>Parameter

*pKlasse*<br/>
Die Laufzeitklasse des zu erstellenden untergeordneten Fensters.

*nResource*<br/>
Die ID der freigegebenen Ressourcen, die dem untergeordneten Fenster zugeordnet sind.

*Hmenu*<br/>
Das Menü des untergeordneten Fensters.

*hAccel*<br/>
Der Beschleuniger des untergeordneten Fensters.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um untergeordnete Fenster eines MDI-Rahmenfensters zu erstellen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]

## <a name="cmdiframewndgetwindowmenupopup"></a><a name="getwindowmenupopup"></a>CMDIFrameWnd::GetWindowMenuPopup

Rufen Sie diese Memberfunktion auf, um ein Handle für das aktuelle Popup-Menü mit dem Namen "Fenster" (das Popup-Menü mit Menüelementen für die MDI-Fensterverwaltung) zu erhalten.

```
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```

### <a name="parameters"></a>Parameter

*hMenuBar*<br/>
Die aktuelle Menüleiste.

### <a name="return-value"></a>Rückgabewert

Das Fenster-Popup-Menü, falls vorhanden; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung sucht nach einem Popupmenü, das Standardmäßige Menübefehle für das Fenster enthält, z. B. ID_WINDOW_NEW und ID_WINDOW_TILE_HORZ.

Überschreiben Sie diese Memberfunktion, wenn Sie über ein Fenstermenü verfügen, das nicht die Standardmenübefehls-IDs verwendet.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]

## <a name="cmdiframewndmdiactivate"></a><a name="mdiactivate"></a>CMDIFrameWnd::MDIActivate

Aktiviert ein anderes untergeordnetes MDI-Fenster.

```cpp
void MDIActivate(CWnd* pWndActivate);
```

### <a name="parameters"></a>Parameter

*pWndActivate*<br/>
Zeigt auf das zu aktivierende MDI-Untergeordnete Fenster.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion sendet die [WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate) Nachricht sowohl an das aktivierte untergeordnete Fenster als auch an das deaktivierte untergeordnete Fenster.

Dies ist die gleiche Meldung, die gesendet wird, wenn der Benutzer den Fokus mithilfe der Maus oder Tastatur in ein untergeordnetes MDI-Fenster ändert.

> [!NOTE]
> Ein untergeordnetes MDI-Fenster wird unabhängig vom MDI-Rahmenfenster aktiviert. Wenn der Rahmen aktiv wird, wird dem zuletzt aktivierten untergeordneten Fenster eine [WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate) Nachricht gesendet, um einen aktiven Fensterrahmen und eine Beschriftungsleiste zu zeichnen, aber es erhält keine weitere WM_MDIACTIVATE Nachricht.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup).

## <a name="cmdiframewndmdicascade"></a><a name="mdicascade"></a>CMDIFrameWnd::MDICascade

Ordnet alle untergeordneten MDI-Fenster in einem Kaskadenformat an.

```cpp
void MDICascade();
void MDICascade(int nType);
```

### <a name="parameters"></a>Parameter

*nType*<br/>
Gibt ein Kaskadenflag an. Es kann nur das folgende Flag angegeben werden: MDITILE_SKIPDISABLED, wodurch verhindert wird, dass deaktivierte untergeordnete MDI-Fenster kaskadiert werden.

### <a name="remarks"></a>Bemerkungen

Die erste `MDICascade`Version von , ohne Parameter, kaskadiert alle untergeordneten MDI-Fenster, einschließlich deaktivierter Fenster. Die zweite Version wird optional nicht kaskadiert deaktivierte untergeordnete MDI-Fenster, wenn Sie MDITILE_SKIPDISABLED für den *nType-Parameter* angeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]

## <a name="cmdiframewndmdigetactive"></a><a name="mdigetactive"></a>CMDIFrameWnd::MDIGetActive

Ruft das aktuelle aktive untergeordnete MDI-Fenster zusammen mit einem Flag ab, das angibt, ob das untergeordnete Fenster maximiert ist.

```
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;
```

### <a name="parameters"></a>Parameter

*pbMaximiert*<br/>
Ein Zeiger auf einen BOOL-Rückgabewert. Wird bei Rückgabe auf TRUE gesetzt, wenn das Fenster maximiert ist. andernfalls FALSE.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das aktive MDI-Untergeordnete Fenster.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

## <a name="cmdiframewndmdiiconarrange"></a><a name="mdiiconarrange"></a>CMDIFrameWnd::MDIIconArrange

Ordnet alle minimierten untergeordneten Dokumentfenster an.

```cpp
void MDIIconArrange();
```

### <a name="remarks"></a>Bemerkungen

Sie wirkt sich nicht auf untergeordnete Fenster aus, die nicht minimiert werden.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CMDIFrameWnd::MDICascade](#mdicascade).

## <a name="cmdiframewndmdimaximize"></a><a name="mdimaximize"></a>CMDIFrameWnd::MDIMaximieren

Maximiert das angegebene untergeordnete MDI-Fenster.

```cpp
void MDIMaximize(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Zeigt auf das Fenster, um es zu maximieren.

### <a name="remarks"></a>Bemerkungen

Wenn ein untergeordnetes Fenster maximiert wird, ändert Windows die Größe, sodass der Clientbereich das Clientfenster ausfüllt. Windows platziert das Steuerelementmenü des untergeordneten Fensters in der Menüleiste des Rahmens, damit der Benutzer das untergeordnete Fenster wiederherstellen oder schließen kann. Außerdem wird dem Framefenstertitel der Titel des untergeordneten Fensters hinzugefügt.

Wenn ein anderes untergeordnetes MDI-Fenster aktiviert ist, wenn das aktuell aktive untergeordnete MDI-Fenster maximiert wird, stellt Windows das aktuell aktive untergeordnete Fenster wieder her und maximiert das neu aktivierte untergeordnete Fenster.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

## <a name="cmdiframewndmdinext"></a><a name="mdinext"></a>CMDIFrameWnd::MDINext

Aktiviert das untergeordnete Fenster direkt hinter dem aktuell aktiven untergeordneten Fenster und platziert das aktuell aktive untergeordnete Fenster hinter allen anderen untergeordneten Fenstern.

```cpp
void MDINext();
```

### <a name="remarks"></a>Bemerkungen

Wenn das aktuell aktive untergeordnete MDI-Fenster maximiert ist, stellt die Memberfunktion das aktuell aktive untergeordnete Fenster wieder her und maximiert das neu aktivierte untergeordnete Element.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]

## <a name="cmdiframewndmdiprev"></a><a name="mdiprev"></a>CMDIFrameWnd::MDIPrev

Aktiviert das vorherige untergeordnete Fenster und platziert das aktuell aktive untergeordnete Fenster direkt dahinter.

```cpp
void MDIPrev();
```

### <a name="remarks"></a>Bemerkungen

Wenn das aktuell aktive untergeordnete MDI-Fenster maximiert ist, stellt die Memberfunktion das aktuell aktive untergeordnete Fenster wieder her und maximiert das neu aktivierte untergeordnete Element.

## <a name="cmdiframewndmdirestore"></a><a name="mdirestore"></a>CMDIFrameWnd::MDIRestore

Stellt ein untergeordnetes MDI-Fenster von einer maximierten oder minimierten Größe wieder her.

```cpp
void MDIRestore(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Zeigt auf das Fenster, um es wiederherzustellen.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CMDIChildWnd::MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore).

## <a name="cmdiframewndmdisetmenu"></a><a name="mdisetmenu"></a>CMDIFrameWnd::MDISetMenu

Ersetzt das Menü eines MDI-Rahmenfensters, das Fenster-Popupmenü oder beides.

```
CMenu* MDISetMenu(
    CMenu* pFrameMenu,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Parameter

*pFrameMenu*<br/>
Gibt das Menü des neuen Frame-Fenster-Menüs an. Wenn NULL, wird das Menü nicht geändert.

*pWindowMenu*<br/>
Gibt das Menü des neuen Popupmenüs Fenster an. Wenn NULL, wird das Menü nicht geändert.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Frame-Fenster-Menü, das durch diese Meldung ersetzt wird. Der Zeiger kann temporär sein und sollte nicht für eine spätere Verwendung gespeichert werden.

### <a name="remarks"></a>Bemerkungen

Nach `MDISetMenu`dem Aufruf muss eine Anwendung die `CWnd` [DrawMenuBar-Memberfunktion](../../mfc/reference/cwnd-class.md#drawmenubar) aufrufen, um die Menüleiste zu aktualisieren.

Wenn dieser Aufruf das Fenster-Popupmenü ersetzt, werden MDI-Menüelemente im untergeordneten MDI-Fenster aus dem vorherigen Fenstermenü entfernt und dem neuen Fenster-Popupmenü hinzugefügt.

Wenn ein untergeordnetes MDI-Fenster maximiert ist und dieser Aufruf das MDI-Framefenstermenü ersetzt, werden das Menü "Steuerung" und "Wiederherstellen" aus dem vorherigen Frame-Fenster-Menü entfernt und dem neuen Menü hinzugefügt.

Rufen Sie diese Memberfunktion nicht auf, wenn Sie das Framework zum Verwalten Ihrer untergeordneten MDI-Fenster verwenden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]

[!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]

## <a name="cmdiframewndmditile"></a><a name="mditile"></a>CMDIFrameWnd::MDITile

Ordnet alle untergeordneten Fenster in einem gekachelten Format an.

```cpp
void MDITile();
void MDITile(int nType);
```

### <a name="parameters"></a>Parameter

*nType*<br/>
Gibt ein Kachelflag an. Dieser Parameter kann eines der folgenden Flags sein:

- MDITILE_HORIZONTAL Kinderfenster für MDI-Kacheln, sodass ein Fenster über einem anderen angezeigt wird.

- MDITILE_SKIPDISABLED Verhindert, dass deaktivierte MDI-Untergeordnete Fenster gekachelt werden.

- MDITILE_VERTICAL MDI-UntergeordneteNfenster kachelt, sodass ein Fenster neben einem anderen angezeigt wird.

### <a name="remarks"></a>Bemerkungen

Die erste `MDITile`Version von , ohne Parameter, kachelt die Fenster vertikal unter Windows-Versionen 3.1 und höher. Die zweite Version kachelt Fenster vertikal oder horizontal, abhängig vom Wert des *nType-Parameters.*

### <a name="example"></a>Beispiel

Siehe Beispiel für [CMDIFrameWnd::MDICascade](#mdicascade).

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd-Klasse](../../mfc/reference/cframewnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[CMDIChildWnd-Klasse](../../mfc/reference/cmdichildwnd-class.md)
