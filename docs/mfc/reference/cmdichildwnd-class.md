---
title: CMDIChildWnd-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMDIChildWnd
- AFXWIN/CMDIChildWnd
- AFXWIN/CMDIChildWnd::CMDIChildWnd
- AFXWIN/CMDIChildWnd::Create
- AFXWIN/CMDIChildWnd::GetMDIFrame
- AFXWIN/CMDIChildWnd::MDIActivate
- AFXWIN/CMDIChildWnd::MDIDestroy
- AFXWIN/CMDIChildWnd::MDIMaximize
- AFXWIN/CMDIChildWnd::MDIRestore
- AFXWIN/CMDIChildWnd::SetHandles
helpviewer_keywords:
- CMDIChildWnd [MFC], CMDIChildWnd
- CMDIChildWnd [MFC], Create
- CMDIChildWnd [MFC], GetMDIFrame
- CMDIChildWnd [MFC], MDIActivate
- CMDIChildWnd [MFC], MDIDestroy
- CMDIChildWnd [MFC], MDIMaximize
- CMDIChildWnd [MFC], MDIRestore
- CMDIChildWnd [MFC], SetHandles
ms.assetid: 6d07f5d4-9a3e-4723-9fa5-e65bb669fdd5
ms.openlocfilehash: 0fbcb47f3148b72a3155e7c17cc913d652c70c2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370083"
---
# <a name="cmdichildwnd-class"></a>CMDIChildWnd-Klasse

Stellt die Funktionalität eines untergeordneten Windows-MDI-Fensters (Multiple Document Interface) bereit, zusammen mit Membern zum Verwalten des Fensters.

## <a name="syntax"></a>Syntax

```
class CMDIChildWnd : public CFrameWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMDIChildWnd::CMDIChildWnd](#cmdichildwnd)|Erstellt ein `CMDIChildWnd`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMDIChildWnd::Erstellen](#create)|Erstellt das untergeordnete Windows MDI-Fenster, das dem `CMDIChildWnd` Objekt zugeordnet ist.|
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|Gibt den übergeordneten MDI-Frame des MDI-Clientfensters zurück.|
|[CMDIChildWnd::MDIActivate](#mdiactivate)|Aktiviert dieses untergeordnete MDI-Fenster.|
|[CMDIChildWnd::MDIDestroy](#mdidestroy)|Zerstört dieses untergeordnete MDI-Fenster.|
|[CMDIChildWnd::MDIMaximieren](#mdimaximize)|Maximiert dieses untergeordnete MDI-Fenster.|
|[CMDIChildWnd::MDIRestore](#mdirestore)|Stellt dieses untergeordnete MDI-Fenster von einer maximierten oder minimierten Größe wieder her.|
|[CMDIChildWnd::SetHandles](#sethandles)|Legt die Handles für Menü- und Beschleunigerressourcen fest.|

## <a name="remarks"></a>Bemerkungen

Ein untergeordnetes MDI-Fenster sieht ähnlich wie ein typisches Rahmenfenster aus, mit der Ausnahme, dass das untergeordnete MDI-Fenster in einem MDI-Rahmenfenster und nicht auf dem Desktop angezeigt wird. Ein untergeordnetes MDI-Fenster verfügt nicht über eine eigene Menüleiste, sondern teilt das Menü des MDI-Rahmenfensters. Das Framework ändert automatisch das MDI-Framemenü, um das aktuell aktive untergeordnete MDI-Fenster darzustellen.

Um ein nützliches untergeordnetes MDI-Fenster für `CMDIChildWnd`Ihre Anwendung zu erstellen, leiten Sie eine Klasse aus ab. Fügen Sie der abgeleiteten Klasse Membervariablen hinzu, um daten zu speichern, die für Ihre Anwendung spezifisch sind. Implementieren Sie Meldungshandler-Memberfunktionen und eine Meldungszuordnung in der abgeleiteten Klasse, um anzugeben, was passiert, wenn Meldungen an das Fenster weitergeleitet werden.

Es gibt drei Möglichkeiten, ein untergeordnetes MDI-Fenster zu erstellen:

- Erstellen Sie `Create`es direkt mit .

- Erstellen Sie `LoadFrame`es direkt mit .

- Erstellen Sie sie indirekt über eine Dokumentvorlage.

Bevor Sie `Create` `LoadFrame`oder aufrufen, müssen Sie das Framewindowobjekt auf dem Heap mit dem **neuen** C++-Operator erstellen. Vor `Create` dem Aufruf können Sie auch eine Fensterklasse mit der globalen Funktion [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) registrieren, um das Symbol und die Klassenstile für den Frame festzulegen.

Verwenden `Create` Sie die Memberfunktion, um die Erstellungsparameter des Frames als unmittelbare Argumente zu übergeben.

`LoadFrame`erfordert weniger `Create`Argumente als und ruft stattdessen die meisten Standardwerte aus Ressourcen ab, einschließlich Beschriftung, Symbol, Beschleunigertabelle und Menü des Frames. Um von `LoadFrame`zugreifen zu können, müssen alle diese Ressourcen über dieselbe Ressourcen-ID verfügen (z. B. IDR_MAINFRAME).

Wenn `CMDIChildWnd` ein Objekt Ansichten und Dokumente enthält, werden sie indirekt vom Framework und nicht direkt vom Programmierer erstellt. Das `CDocTemplate` Objekt orchestriert die Erstellung des Rahmens, die Erstellung der enthaltenden Ansichten und die Verbindung der Ansichten mit dem entsprechenden Dokument. Die Parameter `CDocTemplate` des Konstruktors geben die `CRuntimeClass` der drei beteiligten Klassen an (Dokument, Rahmen und Ansicht). Ein `CRuntimeClass` Objekt wird vom Framework verwendet, um dynamisch neue Frames zu erstellen, wenn vom Benutzer angegeben (z. B. mithilfe des Befehls Datei neu oder des Befehls MDI Window New).

Eine von `CMDIChildWnd` der Frame-Window-Klasse abgeleitete Frame-Window-Klasse muss mit DECLARE_DYNCREATE deklariert werden, damit der obige RUNTIME_CLASS Mechanismus ordnungsgemäß funktioniert.

Die `CMDIChildWnd` Klasse erbt einen Großteil `CFrameWnd`ihrer Standardimplementierung von . Eine detaillierte Liste dieser Funktionen finden Sie in der [CFrameWnd-Klassenbeschreibung.](../../mfc/reference/cframewnd-class.md) Die `CMDIChildWnd` Klasse verfügt über die folgenden zusätzlichen Funktionen:

- In Verbindung `CMultiDocTemplate` mit der `CMDIChildWnd` Klasse verwenden mehrere Objekte aus derselben Dokumentvorlage dasselbe Menü, wodurch Windows-Systemressourcen gespart werden.

- Das derzeit aktive untergeordnete MDI-Fenstermenü ersetzt das Menü des MDI-Rahmenfensters vollständig, und die Beschriftung des aktuell aktiven untergeordneten MDI-Fensters wird der Beschriftung des MDI-Rahmenfensters hinzugefügt. Weitere Beispiele für untergeordnete MDI-Fensterfunktionen, die in Verbindung mit `CMDIFrameWnd` einem MDI-Rahmenfenster implementiert werden, finden Sie in der Klassenbeschreibung.

Verwenden Sie den **C++-Löschoperator** nicht, um ein Rahmenfenster zu zerstören. Verwenden Sie stattdessen `CWnd::DestroyWindow`. Die `CFrameWnd` Implementierung `PostNcDestroy` von löscht das C++-Objekt, wenn das Fenster zerstört wird. Wenn der Benutzer das Rahmenfenster `OnClose` schließt, `DestroyWindow`ruft der Standardhandler auf .

Weitere Informationen `CMDIChildWnd`zu finden Sie unter [Frame Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cmdichildwndcmdichildwnd"></a><a name="cmdichildwnd"></a>CMDIChildWnd::CMDIChildWnd

Rufen Sie `CMDIChildWnd` auf, um ein Objekt zu erstellen.

```
CMDIChildWnd();
```

### <a name="remarks"></a>Bemerkungen

Rufen `Create` Sie an, um das sichtbare Fenster zu erstellen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CMDIChildWnd::Create](#create).

## <a name="cmdichildwndcreate"></a><a name="create"></a>CMDIChildWnd::Erstellen

Rufen Sie diese Memberfunktion auf, um ein untergeordnetes Windows MDI-Fenster zu erstellen und es an das `CMDIChildWnd` Objekt anzuhängen.

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_OVERLAPPEDWINDOW,
    const RECT& rect = rectDefault,
    CMDIFrameWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parameter

*lpszClassName*<br/>
Verweist auf eine null-beendete Zeichenfolge, die die Windows-Klasse benennt (eine [WNDCLASS-Struktur).](/windows/win32/api/winuser/ns-winuser-wndclassw) Der Klassenname kann ein beliebiger Name sein, der mit der globalen Funktion [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) registriert ist. Sollte NULL für `CMDIChildWnd`einen Standard sein.

*lpszWindowName*<br/>
Zeigt auf eine null-terminierte Zeichenfolge, die den Fensternamen darstellt. Wird als Text für die Titelleiste verwendet.

*dwStyle*<br/>
Gibt die [Fensterstilattribute](../../mfc/reference/styles-used-by-mfc.md#window-styles) an. Der WS_CHILD Stil ist erforderlich.

*Rect*<br/>
Enthält die Größe und Position des Fensters. Mit `rectDefault` dem Wert kann Windows die Größe `CMDIChildWnd`und Position der neuen angeben.

*pParentWnd*<br/>
Gibt das übergeordnete Fenster an. Wenn NULL, wird das Hauptanwendungsfenster verwendet.

*pContext*<br/>
Gibt eine [CCreateContext-Struktur](../../mfc/reference/ccreatecontext-structure.md) an. Dieser Parameter kann NULL sein.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Das derzeit aktive untergeordnete MDI-Rahmenfenster kann die Beschriftung des übergeordneten Rahmenfensters bestimmen. Diese Funktion wird deaktiviert, indem Sie das FWS_ADDTOTITLE Stilbit des untergeordneten Rahmenfensters deaktivieren.

Das Framework ruft diese Memberfunktion als Antwort auf einen Benutzerbefehl auf, um ein untergeordnetes Fenster zu erstellen, und das Framework verwendet den *parameter pContext,* um das untergeordnete Fenster ordnungsgemäß mit der Anwendung zu verbinden. Beim Aufrufen `Create`kann *pContext* NULL sein.

### <a name="example"></a>Beispiel

Beispiel 1:

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>Beispiel

Beispiel 2:

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

## <a name="cmdichildwndgetmdiframe"></a><a name="getmdiframe"></a>CMDIChildWnd::GetMDIFrame

Rufen Sie diese Funktion auf, um den übergeordneten MDI-Frame zurückzugeben.

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das übergeordnete MDI-Rahmenfenster.

### <a name="remarks"></a>Bemerkungen

Der zurückgegebene Frame ist `CMDIChildWnd` zwei übergeordnete Zeichen, die aus dem fenster `CMDIChildWnd` vom Typ MDICLIENT entfernt wurden und das Objekt verwaltet. Rufen Sie die [GetParent-Memberfunktion](../../mfc/reference/cwnd-class.md#getparent) auf, um das `CMDIChildWnd` unmittelbare `CWnd` MDICLIENT-Übergeordnete des Objekts als temporären Zeiger zurückzugeben.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CMDIFrameWnd::MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu).

## <a name="cmdichildwndmdiactivate"></a><a name="mdiactivate"></a>CMDIChildWnd::MDIActivate

Rufen Sie diese Memberfunktion auf, um ein untergeordnetes MDI-Fenster unabhängig vom MDI-Rahmenfenster zu aktivieren.

```
void MDIActivate();
```

### <a name="remarks"></a>Bemerkungen

Wenn der Rahmen aktiv wird, wird auch das zuletzt aktivierte untergeordnete Fenster aktiviert.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CMDIFrameWnd::GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup).

## <a name="cmdichildwndmdidestroy"></a><a name="mdidestroy"></a>CMDIChildWnd::MDIDestroy

Rufen Sie diese Memberfunktion auf, um ein untergeordnetes MDI-Fenster zu zerstören.

```
void MDIDestroy();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion entfernt den Titel des untergeordneten Fensters aus dem Rahmenfenster und deaktiviert das untergeordnete Fenster.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]

## <a name="cmdichildwndmdimaximize"></a><a name="mdimaximize"></a>CMDIChildWnd::MDIMaximieren

Rufen Sie diese Memberfunktion auf, um ein untergeordnetes MDI-Fenster zu maximieren.

```
void MDIMaximize();
```

### <a name="remarks"></a>Bemerkungen

Wenn ein untergeordnetes Fenster maximiert wird, ändert Windows die Größe, sodass der Clientbereich den Clientbereich des Rahmenfensters ausfüllt. Windows platziert das Steuerelementmenü des untergeordneten Fensters in der Menüleiste des Rahmens, damit der Benutzer das untergeordnete Fenster wiederherstellen oder schließen kann, und fügt den Titel des untergeordneten Fensters zum Framefenstertitel hinzu.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]

## <a name="cmdichildwndmdirestore"></a><a name="mdirestore"></a>CMDIChildWnd::MDIRestore

Rufen Sie diese Memberfunktion auf, um ein untergeordnetes MDI-Fenster von einer maximierten oder minimierten Größe wiederherzustellen.

```
void MDIRestore();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]

## <a name="cmdichildwndsethandles"></a><a name="sethandles"></a>CMDIChildWnd::SetHandles

Legt die Handles für Menü- und Beschleunigerressourcen fest.

```
void SetHandles(
    HMENU hMenu,
    HACCEL hAccel);
```

### <a name="parameters"></a>Parameter

*Hmenu*<br/>
Das Handle einer Menüressource.

*hAccel*<br/>
Das Handle einer Beschleunigerressource.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um das Menü und die Beschleunigerressourcen festzulegen, die vom untergeordneten MDI-Fensterobjekt verwendet werden.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd-Klasse](../../mfc/reference/cframewnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd-Klasse](../../mfc/reference/cmdiframewnd-class.md)
