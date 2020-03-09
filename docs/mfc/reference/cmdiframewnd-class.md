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
ms.openlocfilehash: 20d74030cdc90ed2e1a7809c121967e74db21b4a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866559"
---
# <a name="cmdiframewnd-class"></a>CMDIFrameWnd-Klasse

Stellt die Funktionalität eines untergeordneten Windows-MDI-Rahmenfensters (Multiple Document Interface) bereit, zusammen mit Membern zum Verwalten des Fensters.

## <a name="syntax"></a>Syntax

```
class CMDIFrameWnd : public CFrameWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMDIFrameWnd:: CMDIFrameWnd](#cmdiframewnd)|Erstellt ein Objekt vom Typ `CMDIFrameWnd`.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMDIFrameWnd:: anateclient](#createclient)|Erstellt ein Windows MDICLIENT-Fenster für dieses `CMDIFrameWnd`. Wird von der `OnCreate` Member-Funktion von `CWnd`aufgerufen.|
|[CMDIFrameWnd:: kreatenewchild](#createnewchild)|Erstellt ein neues untergeordnetes Fenster.|
|[CMDIFrameWnd:: getwindowmenupopup](#getwindowmenupopup)|Gibt das Popup Menü des Fensters zurück.|
|[CMDIFrameWnd:: mdiaktivierungs](#mdiactivate)|Aktiviert ein anderes untergeordnetes MDI-Fenster.|
|[CMDIFrameWnd:: mdicascade](#mdicascade)|Ordnet alle untergeordneten Fenster in einem kaskadierenden Format an.|
|[CMDIFrameWnd:: mdigetactive](#mdigetactive)|Ruft das momentan aktive untergeordnete MDI-Fenster zusammen mit einem Flag ab, das angibt, ob das untergeordnete Element maximiert ist.|
|[CMDIFrameWnd:: mdiiconarrange](#mdiiconarrange)|Ordnet alle untergeordneten Fenster von Dokumenten an.|
|[CMDIFrameWnd:: mdimaximi](#mdimaximize)|Maximiert ein untergeordnetes MDI-Fenster.|
|[CMDIFrameWnd:: mdinext](#mdinext)|Aktiviert das untergeordnete Fenster direkt hinter dem momentan aktiven untergeordneten Fenster und platziert das momentan aktive untergeordnete Fenster hinter allen anderen untergeordneten Fenstern.|
|[CMDIFrameWnd:: mdiprev](#mdiprev)|Aktiviert das vorherige untergeordnete Fenster und platziert das momentan aktive untergeordnete Fenster direkt dahinter.|
|[CMDIFrameWnd:: mumgeleitet Store](#mdirestore)|Stellt ein untergeordnetes MDI-Fenster von maximierter oder minimierter Größe wieder her.|
|[CMDIFrameWnd:: mdisetmenu](#mdisetmenu)|Ersetzt das Menü eines MDI-Rahmen Fensters, das Popup Menü des Fensters oder beides.|
|[CMDIFrameWnd:: mditile](#mditile)|Ordnet alle untergeordneten Fenster in einem gekachelten Format an.|

## <a name="remarks"></a>Bemerkungen

Um ein nützliches MDI-Rahmen Fenster für die Anwendung zu erstellen, leiten Sie eine Klasse von `CMDIFrameWnd`ab. Fügen Sie der abgeleiteten Klasse Element Variablen hinzu, um Daten zu speichern, die für Ihre Anwendung spezifisch sind. Implementieren Sie Meldungshandler-Memberfunktionen und eine Meldungszuordnung in der abgeleiteten Klasse, um anzugeben, was passiert, wenn Meldungen an das Fenster weitergeleitet werden.

Sie können ein MDI-Rahmen Fenster erstellen, indem Sie die [Create](../../mfc/reference/cframewnd-class.md#create) -oder [LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe) -Member-Funktion von `CFrameWnd`aufrufen.

Bevor Sie `Create` oder `LoadFrame`aufgerufen haben, müssen Sie das Rahmen Fenster Objekt auf dem Heap mithilfe des C++ Operators **New** erstellen. Vor dem Aufrufen von `Create` können Sie auch eine Fenster Klasse mit der globalen Funktion [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) registrieren, um das Symbol und die Klassen Stile für den Frame festzulegen.

Verwenden Sie die `Create` Member-Funktion, um die Erstellungs Parameter des Frames als unmittelbare Argumente zu übergeben.

`LoadFrame` erfordert weniger Argumente als `Create`und ruft stattdessen die meisten Standardwerte aus den Ressourcen ab, einschließlich der Beschriftung, des Symbols, der Zugriffstasten Tabelle und des Menüs des Frames. Für den Zugriff auf `LoadFrame`müssen alle diese Ressourcen dieselbe Ressourcen-ID aufweisen (z. b. IDR_MAINFRAME).

Obwohl `MDIFrameWnd` von `CFrameWnd`abgeleitet ist, muss eine von `CMDIFrameWnd` abgeleitete Frame Fenster Klasse nicht mit `DECLARE_DYNCREATE`deklariert werden.

Die `CMDIFrameWnd`-Klasse erbt einen Großteil ihrer Standard Implementierung von `CFrameWnd`. Eine ausführliche Liste dieser Features finden Sie in der Beschreibung der [CFrameWnd](../../mfc/reference/cframewnd-class.md) -Klasse. Die `CMDIFrameWnd`-Klasse verfügt über die folgenden zusätzlichen Funktionen:

- Ein MDI-Rahmen Fenster verwaltet das MDICLIENT-Fenster und positioniert es in Verbindung mit Steuer leisten neu. Das MDI-Client Fenster ist das direkt übergeordnete Element der untergeordneten MDI-Rahmen Fenster. Die WS_HSCROLL-und WS_VSCROLL Fenster Stile, die in einem `CMDIFrameWnd` angegeben werden, gelten für das MDI-Client Fenster anstatt für das Hauptrahmen Fenster, sodass der Benutzer einen Bildlauf im MDI-Client Bereich durchführen kann (z. b. im Windows-Programm-Manager).

- Ein MDI-Rahmen Fenster besitzt ein Standardmenü, das als Menüleiste verwendet wird, wenn kein aktives untergeordnetes MDI-Fenster vorhanden ist. Wenn ein aktives untergeordnetes MDI-Element vorhanden ist, wird die Menüleiste des MDI-Frame Fensters automatisch durch das untergeordnete MDI-Fenstermenü ersetzt.

- Ein MDI-Rahmen Fenster funktioniert zusammen mit dem aktuellen untergeordneten MDI-Fenster, sofern vorhanden. Beispielsweise werden Befehls Meldungen vor dem MDI-Rahmen Fenster an das momentan aktive untergeordnete MDI-Fenster delegiert.

- Ein MDI-Rahmen Fenster verfügt über Standard Handler für die folgenden Standardmenü Befehle im Fenster:

    - ID_WINDOW_TILE_VERT

    - ID_WINDOW_TILE_HORZ

    - ID_WINDOW_CASCADE

    - ID_WINDOW_ARRANGE

- Ein MDI-Rahmen Fenster verfügt auch über eine Implementierung von ID_WINDOW_NEW, das einen neuen Frame und eine Ansicht für das aktuelle Dokument erstellt. Eine Anwendung kann diese Standard Befehls Implementierungen überschreiben, um die MDI-Fenster Verarbeitung anzupassen.

Verwenden Sie nicht den C++ **Delete** -Operator, um ein Rahmen Fenster zu zerstören. Verwenden Sie stattdessen `CWnd::DestroyWindow`. Die `CFrameWnd` Implementierung von `PostNcDestroy` löscht das C++ Objekt, wenn das Fenster zerstört wird. Wenn der Benutzer das Rahmen Fenster schließt, ruft der Standard `OnClose` Handler `DestroyWindow`auf.

Weitere Informationen zu `CMDIFrameWnd`finden Sie unter [Rahmen Fenster](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIFrameWnd`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

##  <a name="cmdiframewnd"></a>CMDIFrameWnd:: CMDIFrameWnd

Erstellt ein `CMDIFrameWnd`-Objekt.

```
CMDIFrameWnd();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie die `Create`-oder `LoadFrame` Member-Funktion auf, um das sichtbare MDI-Rahmen Fenster zu erstellen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]

##  <a name="createclient"></a>CMDIFrameWnd:: anateclient

Erstellt das MDI-Client Fenster, das die `CMDIChildWnd`-Objekte verwaltet.

```
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Parameter

*lpkreatestruct*<br/>
Ein langer Zeiger auf eine [kreatestruct](/windows/win32/api/winuser/ns-winuser-createstructw) -Struktur.

*pwindowmenu*<br/>
Ein Zeiger auf das Fenster Popup-Menü.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion sollte aufgerufen werden, wenn Sie die `OnCreate` Member-Funktion direkt überschreiben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]

##  <a name="createnewchild"></a>CMDIFrameWnd:: kreatenewchild

Erstellt ein neues untergeordnetes Fenster.

```
CMDIChildWnd* CreateNewChild(
    CRuntimeClass* pClass,
    UINT nResource,
    HMENU hMenu = NULL,
    HACCEL hAccel = NULL);
```

### <a name="parameters"></a>Parameter

*pclass*<br/>
Die Lauf Zeit Klasse des zu erstellenden untergeordneten Fensters.

*nressource*<br/>
Die ID der freigegebenen Ressourcen, die dem untergeordneten Fenster zugeordnet sind.

*HMENU*<br/>
Das Menü des untergeordneten Fensters.

*haccel*<br/>
Die Zugriffstaste des untergeordneten Fensters.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um untergeordnete Fenster eines MDI-Rahmen Fensters zu erstellen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]

##  <a name="getwindowmenupopup"></a>CMDIFrameWnd:: getwindowmenupopup

Rufen Sie diese Member-Funktion auf, um ein Handle für das aktuelle Popup Menü namens "Window" (das Popup Menü mit Menü Elementen für die MDI-Fensterverwaltung) abzurufen.

```
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```

### <a name="parameters"></a>Parameter

*hmenubar*<br/>
Die aktuelle Menüleiste.

### <a name="return-value"></a>Rückgabewert

Das Popup Menü des Fensters, wenn ein solches vorhanden ist. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung sucht nach einem Popupmenü, das Standardmenü Befehle für Fenster wie ID_WINDOW_NEW und ID_WINDOW_TILE_HORZ enthält.

Überschreiben Sie diese Member-Funktion, wenn Sie über ein Fenstermenü verfügen, in dem die Standardmenü Befehls-IDs nicht verwendet werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]

##  <a name="mdiactivate"></a>CMDIFrameWnd:: mdiaktivierungs

Aktiviert ein anderes untergeordnetes MDI-Fenster.

```
void MDIActivate(CWnd* pWndActivate);
```

### <a name="parameters"></a>Parameter

*pwndaktivierung*<br/>
Verweist auf das untergeordnete MDI-Fenster, das aktiviert werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion sendet die [WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate) Nachricht an das untergeordnete Fenster, das aktiviert wird, und das untergeordnete Fenster, das deaktiviert wird.

Dabei handelt es sich um dieselbe Nachricht, die gesendet wird, wenn der Fokus mithilfe der Maus oder der Tastatur auf ein untergeordnetes MDI-Fenster geändert wird.

> [!NOTE]
>  Ein untergeordnetes MDI-Fenster wird unabhängig vom MDI-Rahmen Fenster aktiviert. Wenn der Frame aktiv wird, wird dem untergeordneten Fenster, das zuletzt aktiviert wurde, eine [WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate) Nachricht gesendet, um einen aktiven Fensterrahmen und eine Titelleiste zu zeichnen, es wird jedoch keine andere WM_MDIACTIVATE Meldung empfangen.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CMDIFrameWnd:: getwindowmenupopup](#getwindowmenupopup).

##  <a name="mdicascade"></a>CMDIFrameWnd:: mdicascade

Ordnet alle untergeordneten MDI-Fenster in einem kaskadierenden Format an.

```
void MDICascade();
void MDICascade(int nType);
```

### <a name="parameters"></a>Parameter

*nType*<br/>
Gibt ein Cascade-Flag an. Es kann nur das folgende Flag angegeben werden: MDITILE_SKIPDISABLED, das verhindert, dass deaktivierte untergeordnete MDI-Fenster kaskadiert werden.

### <a name="remarks"></a>Bemerkungen

In der ersten Version `MDICascade`ohne Parameter werden alle untergeordneten MDI-Fenster, einschließlich der deaktivierten, kaskadiert. Die zweite Version führt optional zu deaktivierten untergeordneten MDI-Fenstern, wenn Sie MDITILE_SKIPDISABLED für den *nType* -Parameter angeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]

##  <a name="mdigetactive"></a>CMDIFrameWnd:: mdigetactive

Ruft das aktuelle aktive untergeordnete MDI-Fenster zusammen mit einem Flag ab, das angibt, ob das untergeordnete Fenster maximiert ist.

```
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;
```

### <a name="parameters"></a>Parameter

*pbmaximized*<br/>
Ein Zeiger auf einen booleschen Rückgabewert. Wird bei Rückgabe auf true festgelegt, wenn das Fenster maximiert ist. andernfalls false.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das aktive untergeordnete MDI-Fenster.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CMDIChildWnd:: mdimaximi.](../../mfc/reference/cmdichildwnd-class.md#mdimaximize)

##  <a name="mdiiconarrange"></a>CMDIFrameWnd:: mdiiconarrange

Ordnet alle untergeordneten Fenster von Dokumenten an.

```
void MDIIconArrange();
```

### <a name="remarks"></a>Bemerkungen

Untergeordnete Fenster, die nicht minimiert sind, sind nicht betroffen.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CMDIFrameWnd:: mdicascade](#mdicascade).

##  <a name="mdimaximize"></a>CMDIFrameWnd:: mdimaximi

Maximiert das angegebene untergeordnete MDI-Fenster.

```
void MDIMaximize(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*folgenden*<br/>
Zeigt auf das Fenster, das maximiert werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn ein untergeordnetes Fenster maximiert ist, ändert Windows seine Größe, damit der Client Bereich das Client Fenster ausfüllen kann. Windows legt das Steuerelement Menü des untergeordneten Fensters in der Menüleiste des Frames ab, sodass der Benutzer das untergeordnete Fenster wiederherstellen oder schließen kann. Außerdem wird dem Rahmen Fenstertitel der Titel des untergeordneten Fensters hinzugefügt.

Wenn ein anderes untergeordnetes MDI-Fenster aktiviert wird, wenn das momentan aktive untergeordnete MDI-Fenster maximiert ist, stellt Windows das momentan aktive untergeordnete Fenster wieder her und maximiert das neu aktivierte untergeordnete Fenster.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CMDIChildWnd:: mdimaximi.](../../mfc/reference/cmdichildwnd-class.md#mdimaximize)

##  <a name="mdinext"></a>CMDIFrameWnd:: mdinext

Aktiviert das untergeordnete Fenster direkt hinter dem momentan aktiven untergeordneten Fenster und platziert das momentan aktive untergeordnete Fenster hinter allen anderen untergeordneten Fenstern.

```
void MDINext();
```

### <a name="remarks"></a>Bemerkungen

Wenn das momentan aktive untergeordnete MDI-Fenster maximiert ist, stellt die Member-Funktion das momentan aktive untergeordnete Element wieder her und maximiert das neu aktivierte untergeordnete Element.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]

##  <a name="mdiprev"></a>CMDIFrameWnd:: mdiprev

Aktiviert das vorherige untergeordnete Fenster und platziert das momentan aktive untergeordnete Fenster direkt dahinter.

```
void MDIPrev();
```

### <a name="remarks"></a>Bemerkungen

Wenn das momentan aktive untergeordnete MDI-Fenster maximiert ist, stellt die Member-Funktion das momentan aktive untergeordnete Element wieder her und maximiert das neu aktivierte untergeordnete Element.

##  <a name="mdirestore"></a>CMDIFrameWnd:: mumgeleitet Store

Stellt ein untergeordnetes MDI-Fenster von maximierter oder minimierter Größe wieder her.

```
void MDIRestore(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*folgenden*<br/>
Verweist auf das Fenster, das wieder hergestellt werden soll.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CMDIChildWnd:: mdirestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore).

##  <a name="mdisetmenu"></a>CMDIFrameWnd:: mdisetmenu

Ersetzt das Menü eines MDI-Rahmen Fensters, das Popup Menü des Fensters oder beides.

```
CMenu* MDISetMenu(
    CMenu* pFrameMenu,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Parameter

*pframemenu*<br/>
Gibt das Menü des neuen Frame-Fenster-Menüs an. Wenn der Wert NULL ist, wird das Menü nicht geändert.

*pwindowmenu*<br/>
Gibt das Menü des Popup Menüs für das neue Fenster an. Wenn der Wert NULL ist, wird das Menü nicht geändert.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Rahmen Fenstermenü, das durch diese Meldung ersetzt wurde. Der Zeiger kann temporär sein und sollte nicht für eine spätere Verwendung gespeichert werden.

### <a name="remarks"></a>Bemerkungen

Nach dem Aufrufen von `MDISetMenu`muss eine Anwendung die [DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar) -Member-Funktion von `CWnd` aufrufen, um die Menüleiste zu aktualisieren.

Wenn dieser Befehl das Popup Menü des Fensters ersetzt, werden die Menü Elemente des untergeordneten MDI-Fensters aus dem vorherigen Fenstermenü entfernt und zum Popup Menü des neuen Fensters hinzugefügt.

Wenn ein untergeordnetes MDI-Fenster maximiert ist und dieser Befehl das MDI-Frame-Fenster-Menü ersetzt, werden das Menü Steuerelement und die Wiederherstellungs Steuerelemente aus dem vorherigen Menü Fenster entfernt und dem neuen Menü hinzugefügt.

Verwenden Sie diese Member-Funktion nicht, wenn Sie das-Framework zum Verwalten der untergeordneten MDI-Fenster verwenden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]

[!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]

##  <a name="mditile"></a>CMDIFrameWnd:: mditile

Ordnet alle untergeordneten Fenster in einem gekachelten Format an.

```
void MDITile();
void MDITile(int nType);
```

### <a name="parameters"></a>Parameter

*nType*<br/>
Gibt ein tilinger-Flag an. Dieser Parameter kann eines der folgenden Flags sein:

- MDITILE_HORIZONTAL Kacheln untergeordneter MDI-Fenster, sodass ein Fenster oberhalb eines anderen angezeigt wird.

- MDITILE_SKIPDISABLED verhindert, dass deaktivierte untergeordnete MDI-Fenster nebeneinander angeordnet werden

- MDITILE_VERTICAL Kacheln untergeordneter MDI-Fenster, sodass ein Fenster neben einem anderen Fenster angezeigt wird.

### <a name="remarks"></a>Bemerkungen

Mit der ersten Version von `MDITile`ohne Parameter werden die Fenster in den Windows-Versionen 3,1 und höher vertikal nebeneinander angezeigt. Die zweite Version Kacheln Fenster vertikal oder horizontal, abhängig vom Wert des *nType* -Parameters.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CMDIFrameWnd:: mdicascade](#mdicascade).

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel-MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd-Klasse](../../mfc/reference/cframewnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[CMDIChildWnd-Klasse](../../mfc/reference/cmdichildwnd-class.md)
