---
title: CPropertySheet-Klasse
ms.date: 11/04/2016
f1_keywords:
- CPropertySheet
- AFXDLGS/CPropertySheet
- AFXDLGS/CPropertySheet::CPropertySheet
- AFXDLGS/CPropertySheet::AddPage
- AFXDLGS/CPropertySheet::Construct
- AFXDLGS/CPropertySheet::Create
- AFXDLGS/CPropertySheet::DoModal
- AFXDLGS/CPropertySheet::EnableStackedTabs
- AFXDLGS/CPropertySheet::EndDialog
- AFXDLGS/CPropertySheet::GetActiveIndex
- AFXDLGS/CPropertySheet::GetActivePage
- AFXDLGS/CPropertySheet::GetPage
- AFXDLGS/CPropertySheet::GetPageCount
- AFXDLGS/CPropertySheet::GetPageIndex
- AFXDLGS/CPropertySheet::GetTabControl
- AFXDLGS/CPropertySheet::MapDialogRect
- AFXDLGS/CPropertySheet::OnInitDialog
- AFXDLGS/CPropertySheet::PressButton
- AFXDLGS/CPropertySheet::RemovePage
- AFXDLGS/CPropertySheet::SetActivePage
- AFXDLGS/CPropertySheet::SetFinishText
- AFXDLGS/CPropertySheet::SetTitle
- AFXDLGS/CPropertySheet::SetWizardButtons
- AFXDLGS/CPropertySheet::SetWizardMode
- AFXDLGS/CPropertySheet::m_psh
helpviewer_keywords:
- CPropertySheet [MFC], CPropertySheet
- CPropertySheet [MFC], AddPage
- CPropertySheet [MFC], Construct
- CPropertySheet [MFC], Create
- CPropertySheet [MFC], DoModal
- CPropertySheet [MFC], EnableStackedTabs
- CPropertySheet [MFC], EndDialog
- CPropertySheet [MFC], GetActiveIndex
- CPropertySheet [MFC], GetActivePage
- CPropertySheet [MFC], GetPage
- CPropertySheet [MFC], GetPageCount
- CPropertySheet [MFC], GetPageIndex
- CPropertySheet [MFC], GetTabControl
- CPropertySheet [MFC], MapDialogRect
- CPropertySheet [MFC], OnInitDialog
- CPropertySheet [MFC], PressButton
- CPropertySheet [MFC], RemovePage
- CPropertySheet [MFC], SetActivePage
- CPropertySheet [MFC], SetFinishText
- CPropertySheet [MFC], SetTitle
- CPropertySheet [MFC], SetWizardButtons
- CPropertySheet [MFC], SetWizardMode
- CPropertySheet [MFC], m_psh
ms.assetid: 8461ccff-d14f-46e0-a746-42ad642ef94e
ms.openlocfilehash: 23d17aee2aacbc1484c0f3e181bc824546ab49a2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865449"
---
# <a name="cpropertysheet-class"></a>CPropertySheet-Klasse

Stellt Eigenschaftenblätter dar, auch als "Dialogfelder im Registerformat" bezeichnet.

## <a name="syntax"></a>Syntax

```
class CPropertySheet : public CWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPropertySheet:: CPropertySheet](#cpropertysheet)|Erstellt ein `CPropertySheet`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPropertySheet:: addPage](#addpage)|Fügt dem Eigenschaftsblatt eine Seite hinzu.|
|[CPropertySheet:: Construct](#construct)|Erstellt ein `CPropertySheet`-Objekt.|
|[CPropertySheet:: Create](#create)|Zeigt ein Eigenschaften Blatt ohne Modell an.|
|[CPropertySheet::D omodal](#domodal)|Zeigt ein modales Eigenschaften Blatt an.|
|[CPropertySheet:: enablestackedtabs](#enablestackedtabs)|Gibt an, ob auf dem Eigenschaften Blatt gestapelte oder scrollkarten verwendet werden.|
|[CPropertySheet:: EndDialog](#enddialog)|Beendet das Eigenschaften Blatt.|
|[CPropertySheet:: getactiveingedex](#getactiveindex)|Ruft den Index der aktiven Seite des Eigenschaften Blatts ab.|
|[CPropertySheet:: getactivepage](#getactivepage)|Gibt das aktive Seiten Objekt zurück.|
|[CPropertySheet:: GetPage](#getpage)|Ruft einen Zeiger auf die angegebene Seite ab.|
|[CPropertySheet:: getPageCount](#getpagecount)|Ruft die Anzahl der Seiten im Eigenschaften Blatt ab.|
|[CPropertySheet:: getpageingedex](#getpageindex)|Ruft den Index der angegebenen Seite des Eigenschaften Blatts ab.|
|[CPropertySheet:: gettabcontrol](#gettabcontrol)|Ruft einen Zeiger auf ein Registerkarten-Steuerelement ab.|
|[CPropertySheet:: mapdialogrect](#mapdialogrect)|Konvertiert die Dialogfeld Einheiten eines Rechtecks in Bildschirm Einheiten.|
|[CPropertySheet:: OnInitDialog](#oninitdialog)|Überschreiben, um die Eigenschaften Blatt Initialisierung zu erweitern.|
|[CPropertySheet::P ressbutton](#pressbutton)|Simuliert die Auswahl der angegebenen Schaltfläche in einem Eigenschaften Blatt.|
|[CPropertySheet:: RemovePage](#removepage)|Entfernt eine Seite aus dem Eigenschaften Blatt.|
|[CPropertySheet:: "abtativepage"](#setactivepage)|Legt das aktive Seiten Objekt Programm gesteuert fest.|
|[CPropertySheet:: setfinishtext](#setfinishtext)|Legt den Text für die Schaltfläche Fertigstellen fest.|
|[CPropertySheet:: SetTitle](#settitle)|Legt die Beschriftung des Eigenschaften Blatts fest.|
|[CPropertySheet:: "CPropertySheet"](#setwizardbuttons)|Aktiviert die Assistenten Schaltflächen.|
|[CPropertySheet:: "CPropertySheet"](#setwizardmode)|Aktiviert den Assistenten Modus.|

### <a name="public-data-members"></a>Öffentliche Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPropertySheet:: m_psh](#m_psh)|Die Windows- [propsheethader](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) -Struktur. Ermöglicht den Zugriff auf grundlegende Eigenschaften Blatt Parameter.|

## <a name="remarks"></a>Bemerkungen

Ein Eigenschaften Blatt besteht aus einem `CPropertySheet` Objekt und einem oder mehreren [CPropertyPage](../../mfc/reference/cpropertypage-class.md) -Objekten. Das Framework zeigt ein Eigenschaften Blatt als Fenster mit einem Satz von Registerkarten Indizes und einem Bereich an, der die aktuell ausgewählte Seite enthält. Der Benutzer navigiert zu einer bestimmten Seite, indem er die entsprechende Registerkarte verwendet.

`CPropertySheet` bietet Unterstützung für die erweiterte [propsheethader](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) -Struktur, die in Windows 98 und Windows NT 2000 eingeführt wurde. Die Struktur enthält zusätzliche Flags und Member, die die Verwendung einer "Wasserzeichen"-Hintergrund Bitmap unterstützen.

Wenn Sie diese neuen Bilder automatisch in Ihrem Eigenschaften Blatt Objekt anzeigen möchten, übergeben Sie gültige Werte für das Bitmap-und Palettenbild im [CPropertySheet:: Construct](#construct) -oder [CPropertySheet:: CPropertySheet](#cpropertysheet)-Befehl.

Obwohl `CPropertySheet` nicht von [CDialog](../../mfc/reference/cdialog-class.md)abgeleitet ist, entspricht die Verwaltung eines `CPropertySheet` Objekts der Verwaltung eines `CDialog` Objekts. Beispielsweise ist für die Erstellung eines Eigenschaften Blatts eine zweiteilige Konstruktion erforderlich: Rufen Sie den Konstruktor auf, und rufen Sie dann [DoModal](#domodal) für ein modales Eigenschaften Blatt auf, oder [Erstellen](#create) Sie für ein nicht modales Eigenschaften Blatt. `CPropertySheet` verfügt über zwei Arten von Konstruktoren: [CPropertySheet:: Construct](#construct) und [CPropertySheet:: CPropertySheet](#cpropertysheet).

Wenn Sie ein `CPropertySheet` Objekt erstellen, können einige [Fenster Stile](../../mfc/reference/styles-used-by-mfc.md#window-styles) dazu führen, dass eine Ausnahme der ersten Chance auftritt. Dies führt dazu, dass das System versucht, den Stil des Eigenschaften Blatts zu ändern, bevor das Blatt erstellt wird. Um diese Ausnahme zu vermeiden, stellen Sie sicher, dass Sie beim Erstellen des `CPropertySheet`die folgenden Stile festgelegt haben:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Die folgenden Stile sind optional und verursachen nicht die Ausnahme der ersten Chance:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Alle anderen `Window Styles` sind unzulässig, und Sie sollten Sie nicht aktivieren.

Der Austausch von Daten zwischen einem `CPropertySheet`-Objekt und einem externen Objekt ähnelt dem Austauschen von Daten mit einem `CDialog`-Objekt. Der entscheidende Unterschied besteht darin, dass die Einstellungen eines Eigenschaften Blatts in der Regel Member-Variablen der `CPropertyPage` Objekte und nicht das `CPropertySheet` Objekt selbst sind.

Sie können ein Dialogfeld vom Typ "Registerkarte" erstellen, das als Assistent bezeichnet wird, der aus einem Eigenschaften Blatt mit einer Sequenz von Eigenschaften Seiten besteht, die den Benutzer durch die Schritte eines Vorgangs leiten, wie z. b. das Einrichten eines Geräts oder das Erstellen eines Newsletter. Im Dialogfeld der Registerkarte "Wizard-Type" sind auf den Eigenschaften Seiten keine Registerkarten enthalten, und es ist jeweils nur eine Eigenschaften Seite sichtbar. Anstatt die Schaltflächen " **OK** " und " **jetzt anwenden** " zu verwenden, verfügt das Dialogfeld "Wizard-Type" über eine Schaltfläche " **zurück** ", eine Schaltfläche " **weiter** " oder " **Fertig** stellen", eine **Schaltfläche "** **Abbrechen** "

Um das Dialogfeld "Wizard-Type" zu erstellen, führen Sie dieselben Schritte aus, die Sie zum Erstellen eines Standardeigenschaften Blatts ausführen, und rufen Sie dann "" "" "" "" " [, bevor Sie](#setwizardmode) " [DoModal](#domodal)"aufruft Um die Assistenten Schaltflächen zu aktivieren, geben Sie "* [twizardbuttons](#setwizardbuttons)" an und verwenden Flags, um ihre Funktion und Darstellung anzupassen. Um die Schaltfläche **Fertig** stellen zu aktivieren, müssen Sie [setfinishtext](#setfinishtext) aufrufen, nachdem der Benutzer auf der letzten Seite des Assistenten eine Aktion durchgeführt hat.

Weitere Informationen zur Verwendung von `CPropertySheet` Objekten finden Sie im Artikel [Eigenschaften Blätter und Eigenschaften Seiten](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdlgs. h

##  <a name="addpage"></a>CPropertySheet:: addPage

Fügt die angegebene Seite mit der rechten Registerkarte auf dem Eigenschaften Blatt hinzu.

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parameter

*pPage*<br/>
Zeigt auf die Seite, die dem Eigenschaften Blatt hinzugefügt werden soll. Lässt keine NULL-Werte zu.

### <a name="remarks"></a>Bemerkungen

Fügen Sie dem Eigenschaften Blatt in der Reihenfolge von links nach rechts Seiten hinzu, in der Sie angezeigt werden sollen.

`AddPage` fügt der Liste der Seiten des `CPropertySheet` Objekts das [CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage) -Objekt hinzu, erstellt jedoch nicht das Fenster für die Seite. Das Framework erstellt das Fenster für die Seite so lange, bis der Benutzer diese Seite auswählt.

Wenn Sie eine Eigenschaften Seite mithilfe von `AddPage`hinzufügen, ist die `CPropertySheet` das übergeordnete Element des `CPropertyPage`. Um auf der Eigenschaften Seite auf das Eigenschaften Blatt zuzugreifen, nennen Sie [CWnd:: GetParent](../../mfc/reference/cwnd-class.md#getparent).

Es ist nicht erforderlich, zu warten, bis die Erstellung des Eigenschaften Blatt Fensters zum Abrufen `AddPage`erfolgt. In der Regel werden Sie `AddPage` aufrufen, bevor Sie [DoModal](#domodal) aufrufen oder [Erstellen](#create).

Wenn Sie `AddPage` nach dem Anzeigen der Eigenschaften Seite aufzurufen, wird die neu hinzugefügte Seite in der Registerkarten Zeile angezeigt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]

##  <a name="construct"></a>CPropertySheet:: Construct

Erstellt ein `CPropertySheet`-Objekt.

```
void Construct(
    UINT nIDCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

void Construct(
    LPCTSTR pszCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

void Construct(
    UINT nIDCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);

void Construct(
    LPCTSTR pszCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);
```

### <a name="parameters"></a>Parameter

*nidcaption*<br/>
Die ID der Beschriftung, die für das Eigenschaften Blatt verwendet werden soll.

*pparser*<br/>
Ein Zeiger auf das übergeordnete Fenster des Eigenschaften Blatts. Wenn der Wert NULL ist, wird das übergeordnete Fenster das Hauptfenster der Anwendung.

*iselectpage*<br/>
Der Index der Seite, die anfänglich im Vordergrund steht. Der Standardwert ist die erste Seite, die dem Blatt hinzugefügt wird.

*pszcaption*<br/>
Ein Zeiger auf eine Zeichenfolge, die die Beschriftung enthält, die für das Eigenschaften Blatt verwendet werden soll. Lässt keine NULL-Werte zu.

*hbmwatermark*<br/>
Handle für das Wasserzeichen Bitmap der Eigenschaften Seite.

*hpalwatermark*<br/>
Handle für die Palette des Wasserzeichen Bitmap-und/oder Header Bitmap.

*hbmheader*<br/>
Handle für die Header Bitmap der Eigenschaften Seite.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion aufrufen, wenn einer der Klassenkonstruktoren nicht bereits aufgerufen wurde. Rufen Sie `Construct` z. b. auf, wenn Sie Arrays von `CPropertySheet` Objekten deklarieren oder zuordnen. Im Fall von Arrays müssen Sie für jedes Element im Array `Construct` abrufen.

Um das Eigenschaften Blatt anzuzeigen, rufen Sie [DoModal](#domodal) auf, oder [Erstellen](#create)Sie. Die Zeichenfolge, die im ersten Parameter enthalten ist, wird in der Titelleiste für das Eigenschaften Blatt platziert.

Sie können Wasserzeichen und/oder Header Bilder automatisch anzeigen, wenn Sie den dritten oder vierten Prototypen der oben aufgeführten `Construct`verwenden, und Sie gültige Werte für die Parameter " *hbmwatermark*", " *hpalwatermark*" und " *hbmheader* " übergeben.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, unter welchen Umständen `Construct`aufgerufen wird.

[!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]

##  <a name="cpropertysheet"></a>CPropertySheet:: CPropertySheet

Erstellt ein `CPropertySheet`-Objekt.

```
CPropertySheet();

explicit CPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

explicit CPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

CPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);

CPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);
```

### <a name="parameters"></a>Parameter

*nidcaption*<br/>
Die ID der Beschriftung, die für das Eigenschaften Blatt verwendet werden soll.

*pparser*<br/>
Zeigt auf das übergeordnete Fenster des Eigenschaften Blatts. Wenn der Wert NULL ist, wird das übergeordnete Fenster das Hauptfenster der Anwendung.

*iselectpage*<br/>
Der Index der Seite, die anfänglich im Vordergrund steht. Der Standardwert ist die erste Seite, die dem Blatt hinzugefügt wird.

*pszcaption*<br/>
Verweist auf eine Zeichenfolge, die die Beschriftung enthält, die für das Eigenschaften Blatt verwendet werden soll. Lässt keine NULL-Werte zu.

*hbmwatermark*<br/>
Ein Handle für die Hintergrund Bitmap des Eigenschaften Blatts.

*hpalwatermark*<br/>
Ein Handle für die Palette des Wasserzeichen Bitmap-und/oder Header Bitmap.

*hbmheader*<br/>
Ein Handle für die Header Bitmap der Eigenschaften Seite.

### <a name="remarks"></a>Bemerkungen

Um das Eigenschaften Blatt anzuzeigen, rufen Sie [DoModal](#domodal) auf, oder [Erstellen](#create)Sie. Die Zeichenfolge, die im ersten Parameter enthalten ist, wird in der Titelleiste für das Eigenschaften Blatt platziert.

Wenn Sie über mehrere Parameter verfügen (z. b. Wenn Sie ein Array verwenden), verwenden Sie " [Construct](#construct) " anstelle von "`CPropertySheet`".

Sie können ein Wasserzeichen und/oder Kopfzeile automatisch anzeigen, wenn Sie den dritten oder vierten Prototypen `CPropertySheet`oben verwenden, und Sie gültige Werte für die Parameter " *hbmwatermark*", " *hpalwatermark*" und " *hbmheader* " übergeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]

##  <a name="create"></a>CPropertySheet:: Create

Zeigt ein Eigenschaften Blatt ohne Modell an.

```
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);
```

### <a name="parameters"></a>Parameter

*pparser*<br/>
Zeigt auf das übergeordnete Fenster. Wenn NULL, ist das übergeordnete Element der Desktop.

*dwstyle*<br/>
Fenster Stile für das Eigenschaften Blatt. Eine umfassende Liste der verfügbaren Stile finden Sie unter [Fenster Stile](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*dwExStyle*<br/>
Erweiterte Fenster Stile für das Eigenschaften Blatt. Eine umfassende Liste der verfügbaren Stile finden Sie unter [Erweiterte Fenster Stile](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) .

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Eigenschaften Blatt erfolgreich erstellt wird. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Der Aufruf von `Create` kann sich innerhalb des Konstruktors befinden, oder Sie können ihn aufrufen, nachdem der Konstruktor aufgerufen wurde.

Der Standardstil, ausgedrückt durch Übergeben von "-1" als *dwstyle*,&#124;ist&#124;tatsächlich&#124;WS_SYSMENU&#124;WS_POPUP&#124;WS_CAPTION DS_MODALFRAME DS_CONTEXTHELP WS_VISIBLE. Der standardmäßige erweiterte Fenster Stil, ausgedrückt durch Übergeben von 0 als *dwExStyle*, ist tatsächlich WS_EX_DLGMODALFRAME.

Die `Create` Member-Funktion gibt unmittelbar nach dem Erstellen des Eigenschaften Blatts zurück. Um das Eigenschaften Blatt zu zerstören, nennen Sie [CWnd::D estroywindow](../../mfc/reference/cwnd-class.md#destroywindow).

Nicht modale Eigenschaften Blätter, die mit einem `Create` angezeigt werden, verfügen nicht über die Schaltflächen "OK", "Abbrechen", "jetzt anwenden" und "Hilfe". Die gewünschten Schaltflächen müssen vom Benutzer erstellt werden.

Um ein modales Eigenschaften Blatt anzuzeigen, müssen Sie stattdessen [DoModal](#domodal) aufrufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]

[!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]

##  <a name="domodal"></a>CPropertySheet::D omodal

Zeigt ein modales Eigenschaften Blatt an.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Rückgabewert

IDOK oder IDCANCEL, wenn die Funktion erfolgreich war. andernfalls 0 oder-1. Wenn das Eigenschaften Blatt als Assistent festgelegt wurde [(siehe "](#setwizardmode)See" (siehe ""), gibt `DoModal` entweder ID_WIZFINISH oder IDCANCEL zurück.

### <a name="remarks"></a>Bemerkungen

Der Rückgabewert entspricht der ID des Steuer Elements, das das Eigenschaften Blatt geschlossen hat. Nachdem diese Funktion zurückgegeben wurde, werden die Fenster, die dem Eigenschaften Blatt und allen Seiten entsprechen, zerstört. Die Objekte selbst sind weiterhin vorhanden. In der Regel rufen Sie Daten aus den [CPropertyPage](../../mfc/reference/cpropertypage-class.md) -Objekten ab, nachdem `DoModal` IDOK zurückgegeben hat.

Um ein nicht modalem Eigenschaften Blatt anzuzeigen, rufen Sie stattdessen [Create](#create) auf.

Wenn eine Eigenschaften Seite aus der entsprechenden Dialog Ressource erstellt wird, kann Sie eine Ausnahme der ersten Chance auslösen. Das Ergebnis ist, dass auf der Eigenschaften Seite der Stil der Dialogfeld Ressource in den erforderlichen Stil geändert wird, bevor die Seite erstellt wird. Da Ressourcen im Allgemeinen schreibgeschützt sind, wird eine Ausnahme ausgelöst. Das System verarbeitet die Ausnahme und erstellt eine Kopie der geänderten Ressource. Daher kann die Ausnahme der ersten Chance ignoriert werden.

> [!NOTE]
>  Diese Ausnahme muss vom Betriebssystem behandelt werden, wenn Sie mit dem Modell für die asynchrone Ausnahmebehandlung kompilieren. Weitere Informationen zu Ausnahme Behandlungs Modellen finden Sie unter [/eh (Ausnahme Behandlungsmodell)](../../build/reference/eh-exception-handling-model.md). Wrappen Sie in diesem Fall keine Aufrufe von `CPropertySheet::DoModal` mit einem C++ try-catch-Block, in dem der catch alle Ausnahmen behandelt, z. b. `catch (...)`. Dieser Block behandelt die für das Betriebssystem vorgesehene Ausnahme und führt zu unvorhersehbarem Verhalten. Allerdings können Sie die Ausnahme C++ Behandlung für bestimmte Ausnahme Typen oder die strukturierte Ausnahmebehandlung, bei der die Zugriffs Verletzungs Ausnahme an das Betriebssystem übermittelt wird, sicher verwenden.

Um zu vermeiden, dass diese Ausnahme der ersten Chance erzeugt wird, können Sie manuell sicherstellen, dass das Eigenschaften Blatt über die richtigen [Fenster Stile](../../mfc/reference/styles-used-by-mfc.md#window-styles)verfügt. Sie müssen die folgenden Stile für ein Eigenschaften Blatt festlegen:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Sie können die folgenden optionalen Stile verwenden, ohne eine Ausnahme der ersten Chance zu verursachen:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Deaktivieren Sie alle anderen Windows-Stile, da Sie nicht mit Eigenschaften Blättern kompatibel sind. Diese Ratschläge gelten nicht für erweiterte Stile. Wenn diese Standard Stile entsprechend festgelegt werden, wird sichergestellt, dass das Eigenschaften Blatt nicht geändert werden muss, und es wird vermieden, dass die Ausnahme der ersten Chance erzeugt wird.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CPropertySheet:: addPage](#addpage).

##  <a name="enablestackedtabs"></a>CPropertySheet:: enablestackedtabs

Gibt an, ob Zeilen von Registerkarten in einem Eigenschaften Blatt gestapelt werden.

```
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>Parameter

*bstacked*<br/>
Gibt an, ob gestapelte Registerkarten im Eigenschaften Blatt aktiviert sind. Deaktivieren Sie gestapelte Zeilen von Tags, indem Sie *bstacked* auf false festlegen.

### <a name="remarks"></a>Bemerkungen

Wenn ein Eigenschaften Blatt mehr Registerkarten enthält, als in eine einzelne Zeile in der Breite des Eigenschaften Blatts passen, werden die Registerkarten standardmäßig in mehreren Zeilen gestapelt. Um Tabstopps anstelle der Stapel Registerkarten zu verwenden, rufen Sie `EnableStackedTabs` auf, wobei *bstacked* auf false festgelegt ist, bevor Sie [DoModal](#domodal) aufrufen oder [Erstellen](#create).

Beim Erstellen eines modalen oder nicht modalen Eigenschaften Blatts muss `EnableStackedTabs` aufgerufen werden. Um diesen Stil in eine `CPropertySheet`abgeleitete Klasse zu integrieren, schreiben Sie einen Meldungs Handler für WM_CREATE. Rufen Sie in der überschriebenen Version von [CWnd:: OnCreate](../../mfc/reference/cwnd-class.md#oncreate)`EnableStackedTabs( FALSE )` auf, bevor Sie die Implementierung der Basisklasse aufrufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]

##  <a name="enddialog"></a>CPropertySheet:: EndDialog

Beendet das Eigenschaften Blatt.

```
void EndDialog(int nEndID);
```

### <a name="parameters"></a>Parameter

*nendid*<br/>
Der Bezeichner, der als Rückgabewert des Eigenschaften Blatts verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion wird vom Framework aufgerufen, wenn die Schaltfläche OK, Abbrechen oder schließen gedrückt wird. Diese Member-Funktion wird aufgerufen, wenn ein Ereignis auftritt, das das Eigenschaften Blatt schließen soll.

Diese Member-Funktion wird nur in einem modalen Dialogfeld verwendet.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CPropertySheet::P ressbutton](#pressbutton).

##  <a name="getactiveindex"></a>CPropertySheet:: getactiveingedex

Ruft die Indexnummer der aktiven Seite des Eigenschaften Blatt Fensters ab und verwendet dann die zurückgegebene Indexnummer als Parameter für `GetPage`.

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>Rückgabewert

Die Indexnummer der aktiven Seite.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CPropertySheet:: getactivepage](#getactivepage).

##  <a name="getactivepage"></a>CPropertySheet:: getactivepage

Ruft die aktive Seite des Eigenschaften Blatt Fensters ab.

```
CPropertyPage* GetActivePage() const;
```

### <a name="return-value"></a>Rückgabewert

Der Zeiger auf die aktive Seite.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Member-Funktion, um eine Aktion auf der aktiven Seite auszuführen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]

##  <a name="getpage"></a>CPropertySheet:: GetPage

Gibt einen Zeiger auf die angegebene Seite in diesem Eigenschaften Blatt zurück.

```
CPropertyPage* GetPage(int nPage) const;
```

### <a name="parameters"></a>Parameter

*nPage*<br/>
Index der gewünschten Seite, beginnend bei 0. Muss zwischen 0 und eins kleiner als die Anzahl der Seiten im Eigenschaften Blatt (einschließlich) liegen.

### <a name="return-value"></a>Rückgabewert

Der Zeiger auf die Seite, die dem *nPage* -Parameter entspricht.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CPropertyPage:: onwizardfinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

##  <a name="getpagecount"></a>CPropertySheet:: getPageCount

Bestimmt die Anzahl der Seiten, die derzeit im Eigenschaften Blatt angezeigt werden.

```
int GetPageCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Seiten im Eigenschaften Blatt.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CPropertyPage:: onwizardfinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

##  <a name="getpageindex"></a>CPropertySheet:: getpageingedex

Ruft die Indexnummer der angegebenen Seite im Eigenschaften Blatt ab.

```
int GetPageIndex(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parameter

*pPage*<br/>
Verweist auf die Seite mit dem Index, der gefunden werden soll. Lässt keine NULL-Werte zu.

### <a name="return-value"></a>Rückgabewert

Die Indexnummer einer Seite.

### <a name="remarks"></a>Bemerkungen

Beispielsweise können Sie mit `GetPageIndex` den Seitenindex abrufen, um " [stactivepage](#setactivepage) " oder " [GetPage](#getpage)" zu verwenden.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CPropertySheet:: getactivepage](#getactivepage).

##  <a name="gettabcontrol"></a>CPropertySheet:: gettabcontrol

Ruft einen Zeiger auf ein Registerkarten-Steuerelement ab, um einen spezifischen Vorgang für das Registerkarten-Steuerelement zu verwenden (d. h., um eine der APIs in [CTabCtrl](../../mfc/reference/ctabctrl-class.md)zu verwenden).

```
CTabCtrl* GetTabControl() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein Registerkarten-Steuerelement.

### <a name="remarks"></a>Bemerkungen

Beispiel: diese Member-Funktion wird aufgerufen, wenn Sie jeder Registerkarte während der Initialisierung Bitmaps hinzufügen möchten.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]

##  <a name="m_psh"></a>CPropertySheet:: m_psh

Eine-Struktur, deren Member die Merkmale von [propsheeder Ader](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)speichern.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Struktur, um die Darstellung des Eigenschaften Blatts zu initialisieren, nachdem es erstellt wurde, aber bevor es mit der [DoModal](#domodal) -Member-Funktion angezeigt wird. Legen Sie beispielsweise den *dwSize* -Member von `m_psh` auf die Größe fest, die das Eigenschaften Blatt enthalten soll.

Weitere Informationen zu dieser Struktur, einschließlich einer Auflistung der zugehörigen Member, finden Sie unter propsheetheiader in der Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

##  <a name="mapdialogrect"></a>CPropertySheet:: mapdialogrect

Konvertiert die Dialogfeld Einheiten eines Rechtecks in Bildschirm Einheiten.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameter

*lprect*<br/>
Verweist auf eine [Rect](/previous-versions/dd162897\(v=vs.85\)) -Struktur oder ein [CRect](../../atl-mfc-shared/reference/crect-class.md) -Objekt, das die zu konvertierenden Dialogfeld Koordinaten enthält.

### <a name="remarks"></a>Bemerkungen

Dialog Feld Einheiten werden in Bezug auf die aktuelle Dialogfeld-Basiseinheit angegeben, die von der durchschnittlichen Breite und Höhe der Zeichen in der Schriftart abgeleitet ist, die für Text im Dialogfeld verwendet wird. Eine horizontale Einheit ist ein vierte der Dialogfeld-Basis breiten Einheit, und eine vertikale Einheit ist ein Achtel der Dialogfeld-Basis Höheneinheit.

Die Windows-Funktion [GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) gibt Größen Informationen für die System Schriftart zurück, Sie können jedoch für jedes Eigenschaften Blatt eine andere Schriftart angeben, wenn Sie den DS_SETFONT Stil in der Ressourcen Definitionsdatei verwenden. Die in der Windows SDK beschriebene Windows-Funktion [mapdialogrect](/windows/win32/api/winuser/nf-winuser-mapdialogrect) verwendet die entsprechende Schriftart für dieses Dialogfeld.

Die `MapDialogRect` Member-Funktion ersetzt die Dialogfeld Einheiten in *lprect* durch Bildschirm Einheiten (Pixel), sodass das Rechteck verwendet werden kann, um ein Dialogfeld zu erstellen oder ein Steuerelement in einem Feld zu positionieren.

##  <a name="oninitdialog"></a>CPropertySheet:: OnInitDialog

Überschreibt, um die Eigenschaften Blatt Initialisierung zu erweitern.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Rückgabewert

Gibt an, ob die Anwendung den Eingabefokus auf eines der Steuerelemente im Eigenschaften Blatt festgelegt hat. Wenn `OnInitDialog` einen Wert ungleich 0 (null) zurückgibt, legt Windows den Eingabefokus auf das erste Steuerelement im Eigenschaften Blatt fest. Die Anwendung kann 0 nur zurückgeben, wenn Sie den Eingabefokus explizit auf eines der Steuerelemente im Eigenschaften Blatt festgelegt hat.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion wird als Reaktion auf die WM_INITDIALOG Nachricht aufgerufen. Diese Meldung wird während der [Create](#create) -oder [DoModal](#domodal) -Aufrufe an das Eigenschaften Blatt gesendet, die unmittelbar vor dem Anzeigen des Eigenschaften Blatts auftreten.

Überschreiben Sie diese Element Funktion, wenn Sie eine besondere Verarbeitung durchführen müssen, wenn das Eigenschaften Blatt initialisiert wird. In der überschriebenen Version wird zuerst die Basisklasse aufgerufen `OnInitDialog`, aber der Rückgabewert wird ignoriert. Normalerweise wird von der überschriebenen Member-Funktion "true" zurückgegeben.

Sie benötigen keinen Message-Map-Eintrag für diese Element Funktion.

##  <a name="pressbutton"></a>CPropertySheet::P ressbutton

Simuliert die Auswahl der angegebenen Schaltfläche in einem Eigenschaften Blatt.

```
void PressButton(int nButton);
```

### <a name="parameters"></a>Parameter

*nschaltfläche*<br/>
nbutton: identifiziert die zu drückende Schaltfläche. Dieser Parameter kann einen der folgenden Werte aufweisen:

- PSBTN_BACK die Schaltfläche "zurück" auswählt.

- PSBTN_NEXT die Schaltfläche Weiter.

- PSBTN_FINISH wählt die Schaltfläche Fertigstellen aus.

- PSBTN_OK die Schaltfläche OK.

- PSBTN_APPLYNOW die Schaltfläche jetzt anwenden auswählen.

- PSBTN_CANCEL die Schaltfläche Abbrechen auswählt.

- PSBTN_HELP die Schaltfläche Hilfe.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zur Windows SDK pressbutton-Nachricht finden Sie unter [PSM_PRESSBUTTON](/windows/win32/Controls/psm-pressbutton) .

Beim `PressButton` wird die [PSN_APPLY](/windows/win32/Controls/psn-apply) Benachrichtigung von einer Eigenschaften Seite nicht an das Framework gesendet. Um diese Benachrichtigung zu senden, wenden Sie [CPropertyPage:: OnOK](../../mfc/reference/cpropertypage-class.md#onok)an.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]

##  <a name="removepage"></a>CPropertySheet:: RemovePage

Entfernt eine Seite aus dem Eigenschaften Blatt und zerstört das zugehörige Fenster.

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Parameter

*pPage*<br/>
Zeigt auf die Seite, die aus dem Eigenschaften Blatt entfernt werden soll. Lässt keine NULL-Werte zu.

*nPage*<br/>
Der Index der zu entfernenden Seite. Muss zwischen 0 und eins kleiner als die Anzahl der Seiten im Eigenschaften Blatt (einschließlich) liegen.

### <a name="remarks"></a>Bemerkungen

Das [CPropertyPage](../../mfc/reference/cpropertypage-class.md) -Objekt selbst wird erst zerstört, wenn der Besitzer des `CPropertySheet` Fensters geschlossen wird.

##  <a name="setactivepage"></a>CPropertySheet:: "abtativepage"

Ändert die aktive Seite.

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parameter

*nPage*<br/>
Der Index der festzulegenden Seite. Der Wert muss zwischen 0 und eins kleiner als die Anzahl der Seiten im Eigenschaften Blatt (einschließlich) liegen.

*pPage*<br/>
Verweist auf die Seite, die im Eigenschaften Blatt festgelegt werden soll. Er darf nicht NULL sein.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Eigenschaften Blatt erfolgreich aktiviert wurde. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie beispielsweise `SetActivePage`, wenn die Aktion eines Benutzers auf einer Seite dazu führen soll, dass eine andere Seite zur aktiven Seite wird.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CPropertySheet:: getactivepage](#getactivepage).

##  <a name="setfinishtext"></a>CPropertySheet:: setfinishtext

Legt den Text in der Befehls Schaltfläche Fertigstellen fest.

```
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
Zeigt auf den Text, der auf der Befehls Schaltfläche Fertigstellen angezeigt werden soll.

### <a name="remarks"></a>Bemerkungen

`SetFinishText` aufrufen, um den Text auf der Befehls Schaltfläche Fertigstellen anzuzeigen und die Schaltflächen weiter und zurück zu blenden, nachdem der Benutzer die Aktion auf der letzten Seite des Assistenten abgeschlossen hat.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="settitle"></a>CPropertySheet:: SetTitle

Gibt die Beschriftung des Eigenschaften Blatts an (der Text, der in der Titelleiste eines Rahmen Fensters angezeigt wird).

```
void SetTitle(
    LPCTSTR lpszText,
    UINT nStyle = 0);
```

### <a name="parameters"></a>Parameter

*nstyle*<br/>
Gibt den Stil des Eigenschaften Blatt Titels an. Der Stil muss bei 0 oder als PSH_PROPTITLE angegeben werden. Wenn das Format als PSH_PROPTITLE festgelegt ist, wird das Wort "Properties" nach dem als Beschriftung angegebenen Text angezeigt. Wenn Sie z. b. `SetTitle`("Simple", PSH_PROPTITLE) aufrufen, führt dies dazu, dass eine Eigenschaften Blatt Beschriftung "Simple Properties" lautet.

*lpszText*<br/>
Zeigt auf den Text, der in der Titelleiste des Eigenschaften Blatts als Beschriftung verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Standardmäßig verwendet ein Eigenschaften Blatt den Caption-Parameter im Eigenschaften Blatt-Konstruktor.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

##  <a name="setwizardbuttons"></a>CPropertySheet:: "CPropertySheet"

Aktiviert oder deaktiviert die Schaltfläche "zurück", "weiter" oder "Fertigstellen" auf dem Eigenschaften Blatt eines Assistenten.

```
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>Parameter

*dwFlags*<br/>
Ein Satz von Flags, die die Funktion und das Aussehen der Assistenten Schaltflächen anpassen. Dieser Parameter kann eine Kombination der folgenden Werte sein:

- Schaltfläche "zurück PSWIZB_BACK

- Schaltfläche "PSWIZB_NEXT"

- Schaltfläche zum PSWIZB_FINISH beenden

- Schaltfläche zum Fertigstellen PSWIZB_DISABLEDFINISH deaktiviert

### <a name="remarks"></a>Bemerkungen

Ruft `SetWizardButtons` nur auf, nachdem das Dialogfeld geöffnet wurde. Sie können `SetWizardButtons` nicht anrufen, bevor Sie " [DoModal](#domodal)" aufgerufen haben. In der Regel sollten Sie `SetWizardButtons` aus [CPropertyPage:: OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive)aufrufen.

Wenn Sie den Text auf der Schaltfläche Fertigstellen ändern oder die Schaltflächen "weiter" und "zurück" ausblenden möchten, sobald der Benutzer den Assistenten abgeschlossen hat, können Sie [setfinishtext](#setfinishtext)aufrufen. Beachten Sie, dass die gleiche Schaltfläche für den Abschluss und den nächsten freigegeben ist. Sie können eine Schaltfläche "Fertigstellen" oder "weiter" gleichzeitig anzeigen, aber nicht beides.

### <a name="example"></a>Beispiel

Eine `CPropertySheet` verfügt über drei Eigenschaften Seiten des Assistenten: `CStylePage`, `CColorPage`und `CShapePage`.  Das folgende Code Fragment zeigt, wie die Schaltflächen " **zurück** " und **"weiter"** auf der Eigenschaften Seite des Assistenten aktiviert und deaktiviert werden.

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="setwizardmode"></a>CPropertySheet:: "CPropertySheet"

Legt eine Eigenschaften Seite als Assistenten fest.

```
void SetWizardMode();
```

### <a name="remarks"></a>Bemerkungen

Ein wichtiges Merkmal einer Eigenschaften Seite des Assistenten besteht darin, dass der Benutzer über die Schaltflächen "weiter" oder "Fertigstellen", "zurück" und "Abbrechen" anstelle von Registerkarten

Rufen Sie `SetWizardMode` auf, bevor Sie [DoModal](#domodal)aufrufen. Nachdem Sie `SetWizardMode`aufgerufen haben, geben `DoModal` entweder ID_WIZFINISH zurück (wenn der Benutzer mit der Schaltfläche "Fertigstellen" geschlossen wird) oder IDCANCEL.

`SetWizardMode` legt das PSH_WIZARD-Flag fest.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
