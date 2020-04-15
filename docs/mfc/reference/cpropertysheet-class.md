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
ms.openlocfilehash: 167c99f734e4538ff2704e032a6ca98fb1d82004
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363950"
---
# <a name="cpropertysheet-class"></a>CPropertySheet-Klasse

Stellt Eigenschaftenblätter dar, auch als "Dialogfelder im Registerformat" bezeichnet.

## <a name="syntax"></a>Syntax

```
class CPropertySheet : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPropertySheet::CPropertySheet](#cpropertysheet)|Erstellt ein `CPropertySheet`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPropertySheet::AddPage](#addpage)|Fügt dem Eigenschaftsblatt eine Seite hinzu.|
|[CPropertySheet::Konstrukt](#construct)|Erstellt ein `CPropertySheet`-Objekt.|
|[CPropertySheet::Erstellen](#create)|Zeigt ein modusloses Eigenschaftenblatt an.|
|[CPropertySheet::DoModal](#domodal)|Zeigt ein modales Eigenschaftenblatt an.|
|[CPropertySheet::EnableStackedTabs](#enablestackedtabs)|Gibt an, ob das Eigenschaftenblatt gestapelte oder scrollende Registerkarten verwendet.|
|[CPropertySheet::EndDialog](#enddialog)|Beendet das Eigenschaftenblatt.|
|[CPropertySheet::GetActiveIndex](#getactiveindex)|Ruft den Index der aktiven Seite des Eigenschaftenblatts ab.|
|[CPropertySheet::GetActivePage](#getactivepage)|Gibt das aktive Seitenobjekt zurück.|
|[CPropertySheet::GetPage](#getpage)|Ruft einen Zeiger auf die angegebene Seite ab.|
|[CPropertySheet::GetPageCount](#getpagecount)|Ruft die Anzahl der Seiten im Eigenschaftenblatt ab.|
|[CPropertySheet::GetPageIndex](#getpageindex)|Ruft den Index der angegebenen Seite des Eigenschaftenblatts ab.|
|[CPropertySheet::GetTabControl](#gettabcontrol)|Ruft einen Zeiger auf ein Registerkartensteuerelement ab.|
|[CPropertySheet::MapDialogRect](#mapdialogrect)|Konvertiert die Dialogfeldeinheiten eines Rechtecks in Bildschirmeinheiten.|
|[CPropertySheet::OnInitDialog](#oninitdialog)|Überschreiben, um die Initialisierung von Eigenschaftenblättern zu erweitern.|
|[CPropertySheet::PressButton](#pressbutton)|Simuliert die Auswahl der angegebenen Schaltfläche in einem Eigenschaftenblatt.|
|[CPropertySheet::RemovePage](#removepage)|Entfernt eine Seite aus dem Eigenschaftenblatt.|
|[CPropertySheet::SetActivePage](#setactivepage)|Das aktive Seitenobjekt legt programmgesteuert fest.|
|[CPropertySheet::SetFinishText](#setfinishtext)|Legt den Text für die Schaltfläche Fertig stellen fest.|
|[CPropertySheet::SetTitle](#settitle)|Legt die Beschriftung des Eigenschaftenblatts fest.|
|[CPropertySheet::SetWizardButtons](#setwizardbuttons)|Aktiviert die Assistentenschaltflächen.|
|[CPropertySheet::SetWizardMode](#setwizardmode)|Aktiviert den Assistentenmodus.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPropertySheet::m_psh](#m_psh)|Die Windows [PROPSHEETHEADER-Struktur.](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) Bietet Zugriff auf grundlegende Eigenschaftenblattparameter.|

## <a name="remarks"></a>Bemerkungen

Ein Eigenschaftenblatt besteht `CPropertySheet` aus einem Objekt und einem oder mehreren [CPropertyPage-Objekten.](../../mfc/reference/cpropertypage-class.md) Das Framework zeigt ein Eigenschaftenblatt als Fenster mit einer Reihe von Registerkartenindizes und einem Bereich an, der die aktuell ausgewählte Seite enthält. Der Benutzer navigiert mithilfe der entsprechenden Registerkarte zu einer bestimmten Seite.

`CPropertySheet`unterstützt die erweiterte [PROPSHEETHEADER-Struktur,](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) die in Windows 98 und Windows NT 2000 eingeführt wurde. Die Struktur enthält zusätzliche Flags und Member, die die Verwendung einer "Wasserzeichen"-Hintergrundbitmap unterstützen.

Um diese neuen Bilder automatisch in Ihrem Eigenschaftenblattobjekt anzuzeigen, übergeben Sie gültige Werte für die Bitmap- und Palettenbilder im Aufruf von [CPropertySheet::Construct](#construct) oder [CPropertySheet::CPropertySheet](#cpropertysheet).

Obwohl `CPropertySheet` die Verwaltung eines Objekts `CPropertySheet` nicht von [CDialog](../../mfc/reference/cdialog-class.md)abgeleitet ist, ist die Verwaltung eines Objekts wie die Verwaltung eines `CDialog` Objekts. Zum Beispiel erfordert die Erstellung eines Eigenschaftenblatts eine zweiteilige Konstruktion: Rufen Sie den Konstruktor auf, und rufen Sie dann [DoModal](#domodal) für ein modales Eigenschaftenblatt oder [Erstellen](#create) für ein modusloses Eigenschaftenblatt auf. `CPropertySheet`hat zwei Typen von Konstruktoren: [CPropertySheet::Construct](#construct) und [CPropertySheet::CPropertySheet](#cpropertysheet).

Wenn Sie `CPropertySheet` ein Objekt erstellen, können einige [Fensterstile](../../mfc/reference/styles-used-by-mfc.md#window-styles) dazu führen, dass eine Ausnahme der ersten Chance auftritt. Dies ergibt sich aus dem System, das versucht, den Stil des Eigenschaftenblatts zu ändern, bevor das Blatt erstellt wird. Um diese Ausnahme zu vermeiden, stellen Sie sicher, `CPropertySheet`dass Sie beim Erstellen der folgenden Formatvorlagen die folgenden Formatvorlagen festlegen:

- DS_3DLOOK

- DS_CONTROL

- Ws_child

- Ws_tabstop

Die folgenden Formatvorlagen sind optional und verursachen keine Ausnahme der ersten Chance:

- DS_SHELLFONT

- DS_LOCALEDIT

- Ws_clipchildren

Alle `Window Styles` anderen sind verboten und Sie sollten sie nicht aktivieren.

Der Austausch `CPropertySheet` von Daten zwischen einem Objekt und `CDialog` einem externen Objekt ähnelt dem Austausch von Daten mit einem Objekt. Der wichtige Unterschied besteht darin, dass die Einstellungen `CPropertyPage` eines Eigenschaftenblatts `CPropertySheet` in der Regel Membervariablen der Objekte und nicht des Objekts selbst sind.

Sie können einen Typ von Registerkartendialogfeld namens Assistent erstellen, der aus einem Eigenschaftenblatt mit einer Sequenz von Eigenschaftenseiten besteht, die den Benutzer durch die Schritte eines Vorgangs führen, z. B. das Einrichten eines Geräts oder das Erstellen eines Newsletters. In einem Dialogfeld für den Assistenten-Registerkarte verfügen die Eigenschaftenseiten nicht über Registerkarten, und jeweils ist jeweils nur eine Eigenschaftenseite sichtbar. Anstatt **über die Schaltflächen OK** und Jetzt **anwenden** zu verfügen, verfügt das Dialogfeld "Registerkarte" vom Assistenten-Typ über eine **Schaltfläche "Zurück",** eine Schaltfläche **"Weiter"** oder **"Beenden",** die Schaltfläche **Abbrechen** und die **Schaltfläche "Hilfe".**

Um ein Dialogfeld vom Typ Assistent zu erstellen, führen Sie die gleichen Schritte aus, die Sie befolgen würden, um ein Standardeigenschaftenblatt zu erstellen, rufen Sie jedoch [SetWizardMode](#setwizardmode) auf, bevor Sie [DoModal](#domodal)aufrufen. Um die Assistentenschaltflächen zu aktivieren, rufen Sie [SetWizardButtons](#setwizardbuttons)mithilfe von Flags auf, um ihre Funktion und darstellung anzupassen. Um die Schaltfläche **Fertig stellen zu** aktivieren, rufen Sie [SetFinishText](#setfinishtext) auf, nachdem der Benutzer auf der letzten Seite des Assistenten Eine Aktion ausgeführt hat.

Weitere Informationen zur Verwendung `CPropertySheet` von Objekten finden Sie im Artikel [Eigenschaftenblätter und Eigenschaftenseiten](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxdlgs.h

## <a name="cpropertysheetaddpage"></a><a name="addpage"></a>CPropertySheet::AddPage

Fügt die mitgelieferte Seite mit der rechten Registerkarte im Eigenschaftenblatt hinzu.

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parameter

*pPage*<br/>
Zeigt auf die Seite, die dem Eigenschaftenblatt hinzugefügt werden soll. Lässt keine NULL-Werte zu.

### <a name="remarks"></a>Bemerkungen

Fügen Sie dem Eigenschaftenblatt Seiten in der Reihenfolge von links nach rechts hinzu, in der sie angezeigt werden sollen.

`AddPage`fügt das [CPropertyPage-Objekt](../../mfc/reference/cpropertypage-class.md#cpropertypage) der `CPropertySheet` Seitenliste des Objekts hinzu, erstellt jedoch nicht das Fenster für die Seite. Das Framework verschiebt die Erstellung des Fensters für die Seite, bis der Benutzer diese Seite auswählt.

Wenn Sie eine Eigenschaftenseite `AddPage` `CPropertySheet` mit hinzufügen, `CPropertyPage`ist der das übergeordnete Element der . Um über die Eigenschaftenseite auf das Eigenschaftenblatt zuzugreifen, rufen Sie [CWnd::GetParent](../../mfc/reference/cwnd-class.md#getparent)auf.

Es ist nicht notwendig, bis zum Erstellen `AddPage`des Eigenschaftenblattfensters zu warten, um aufzurufen. In der Regel `AddPage` rufen Sie vor dem Aufruf von [DoModal](#domodal) oder [Create](#create)an.

Wenn Sie `AddPage` nach dem Anzeigen der Eigenschaftenseite anrufen, spiegelt die Registerkartenzeile die neu hinzugefügte Seite wider.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]

## <a name="cpropertysheetconstruct"></a><a name="construct"></a>CPropertySheet::Konstrukt

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

*nIDCaption*<br/>
ID der Beschriftung, die für das Eigenschaftenblatt verwendet werden soll.

*pParentWnd*<br/>
Zeigen Sie auf das übergeordnete Fenster des Eigenschaftenblatts. Wenn NULL, ist das übergeordnete Fenster das Hauptfenster der Anwendung.

*iSelectPage*<br/>
Der Index der Seite, die sich zunächst oben befindet. Standard ist die erste Seite, die dem Blatt hinzugefügt wurde.

*pszCaption*<br/>
Zeiger auf eine Zeichenfolge, die die Beschriftung enthält, die für das Eigenschaftenblatt verwendet werden soll. Lässt keine NULL-Werte zu.

*hbmWatermark*<br/>
Behandeln Sie die Wasserzeichen-Bitmap der Eigenschaftenseite.

*hpalWassermark*<br/>
Behandeln Sie die Palette der Wasserzeichen-Bitmap und/oder Header-Bitmap.

*hbmHeader*<br/>
Behandeln Sie die Header-Bitmap der Eigenschaftenseite.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion auf, wenn einer der Klassenkonstruktoren noch nicht aufgerufen wurde. Rufen Sie `Construct` z. B. auf, `CPropertySheet` wenn Sie Arrays von Objekten deklarieren oder zuweisen. Bei Arrays müssen Sie für `Construct` jedes Element im Array aufrufen.

Um das Eigenschaftenblatt anzuzeigen, rufen Sie [DoModal](#domodal) oder [Create](#create)auf. Die im ersten Parameter enthaltene Zeichenfolge wird in der Beschriftungsleiste für das Eigenschaftenblatt platziert.

Sie können Wasserzeichen- und/oder Kopfzeilenbilder automatisch anzeigen, `Construct`wenn Sie den dritten oder vierten Prototyp von verwenden und gültige Werte für die Parameter *hbmWatermark*, *hpalWatermark*und/oder *hbmHeader* übergeben.

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, unter `Construct`welchen Umständen Sie aufrufen würden.

[!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]

## <a name="cpropertysheetcpropertysheet"></a><a name="cpropertysheet"></a>CPropertySheet::CPropertySheet

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

*nIDCaption*<br/>
ID der Beschriftung, die für das Eigenschaftenblatt verwendet werden soll.

*pParentWnd*<br/>
Zeigt auf das übergeordnete Fenster des Eigenschaftenblatts. Wenn NULL, ist das übergeordnete Fenster das Hauptfenster der Anwendung.

*iSelectPage*<br/>
Der Index der Seite, die sich zunächst oben befindet. Standard ist die erste Seite, die dem Blatt hinzugefügt wurde.

*pszCaption*<br/>
Zeigt auf eine Zeichenfolge, die die Beschriftung enthält, die für das Eigenschaftenblatt verwendet werden soll. Lässt keine NULL-Werte zu.

*hbmWatermark*<br/>
Ein Handle für die Hintergrundbitmap des Eigenschaftenblatts.

*hpalWassermark*<br/>
Ein Handle für die Palette der Wasserzeichen-Bitmap und/oder Header-Bitmap.

*hbmHeader*<br/>
Ein Handle für die Header-Bitmap der Eigenschaftenseite.

### <a name="remarks"></a>Bemerkungen

Um das Eigenschaftenblatt anzuzeigen, rufen Sie [DoModal](#domodal) oder [Create](#create)auf. Die im ersten Parameter enthaltene Zeichenfolge wird in der Beschriftungsleiste für das Eigenschaftenblatt platziert.

Wenn Sie über mehrere Parameter verfügen (z. B. wenn `CPropertySheet`Sie ein Array verwenden), verwenden Sie [Construct](#construct) anstelle von .

Sie können Wasserzeichen- und/oder Kopfzeilenbilder automatisch anzeigen, `CPropertySheet`wenn Sie den dritten oder vierten Prototyp von verwenden und gültige Werte für die Parameter *hbmWatermark*, *hpalWatermark*und/oder *hbmHeader* übergeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]

## <a name="cpropertysheetcreate"></a><a name="create"></a>CPropertySheet::Erstellen

Zeigt ein modusloses Eigenschaftenblatt an.

```
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
Zeigt auf das übergeordnete Fenster. Wenn NULL, ist parent der Desktop.

*dwStyle*<br/>
Fensterstile für Eigenschaftenblatt. Eine vollständige Liste der verfügbaren Stile finden Sie unter [Fensterformate](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*dwExStyle*<br/>
Erweiterte Fensterstile für Eigenschaftenblatt. Eine vollständige Liste der verfügbaren Stile finden Sie unter [Erweiterte Fensterstile](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Eigenschaftenblatt erfolgreich erstellt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Der Aufruf, der `Create` sich innerhalb des Konstruktors befinden kann, oder Sie können ihn aufrufen, nachdem der Konstruktor aufgerufen wurde.

Der Standardstil, ausgedrückt durch Übergeben von -1 als *dwStyle*, ist tatsächlich WS_SYSMENU&#124;WS_POPUP WS_CAPTION&#124;WS_CAPTION WS_CAPTION&#124;DS_MODALFRAME&#124;&#124;DS_CONTEXTHELP&#124;WS_VISIBLE. Der standardmäßige erweiterte Fensterstil, ausgedrückt durch Übergeben von 0 als *dwExStyle*, ist tatsächlich WS_EX_DLGMODALFRAME.

Die `Create` Memberfunktion kehrt unmittelbar nach dem Erstellen des Eigenschaftenblatts zurück. Um das Eigenschaftenblatt zu zerstören, rufen Sie [CWnd::DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow)auf.

Moduslose Eigenschaftenblätter, die `Create` mit einem Aufruf angezeigt werden, um nicht über OK, Abbrechen, Jetzt anwenden und Hilfe schaltflächen, wie modale Eigenschaftenblätter tun. Gewünschte Schaltflächen müssen vom Benutzer erstellt werden.

Um ein modales Eigenschaftenblatt anzuzeigen, rufen Sie stattdessen [DoModal](#domodal) auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]

[!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]

## <a name="cpropertysheetdomodal"></a><a name="domodal"></a>CPropertySheet::DoModal

Zeigt ein modales Eigenschaftenblatt an.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Rückgabewert

IDOK oder IDCANCEL, wenn die Funktion erfolgreich war; andernfalls 0 oder -1. Wenn das Eigenschaftenblatt als Assistent eingerichtet wurde (siehe [SetWizardMode](#setwizardmode)), `DoModal` gibt entweder ID_WIZFINISH oder IDCANCEL zurück.

### <a name="remarks"></a>Bemerkungen

Der Rückgabewert entspricht der ID des Steuerelements, das das Eigenschaftenblatt geschlossen hat. Nachdem diese Funktion zurückgegeben wurde, wurden die Fenster, die dem Eigenschaftenblatt entsprechen, und alle Seiten zerstört. Die Objekte selbst werden weiterhin existieren. In der Regel rufen Sie Daten aus `DoModal` den [CPropertyPage-Objekten](../../mfc/reference/cpropertypage-class.md) ab, nachdem IDOK zurückgegeben wurde.

Um ein modusloses Eigenschaftenblatt anzuzeigen, rufen Sie stattdessen [Create](#create) auf.

Wenn eine Eigenschaftenseite aus der entsprechenden Dialogressource erstellt wird, kann sie eine Ausnahme der ersten Chance verursachen. Dies ergibt sich aus der Eigenschaftsseite, die den Stil der Dialogressource in den erforderlichen Stil ändert, bevor die Seite erstellt wird. Da Ressourcen im Allgemeinen schreibgeschützt sind, führt dies zu einer Ausnahme. Das System behandelt die Ausnahme und erstellt eine Kopie der geänderten Ressource. Die Ausnahme der ersten Chance kann daher ignoriert werden.

> [!NOTE]
> Diese Ausnahme muss vom Betriebssystem behandelt werden, wenn Sie mit dem asynchronen Ausnahmebehandlungsmodell kompilieren. Weitere Informationen zu Ausnahmebehandlungsmodellen finden Sie unter [/EH (Exception Handling Model)](../../build/reference/eh-exception-handling-model.md). Umschließen Sie in diesem `CPropertySheet::DoModal` Fall keine Aufrufe an einen C++-try-catch-Block, in `catch (...)`dem der catch alle Ausnahmen behandelt, z. B. . Dieser Block würde die für das Betriebssystem vorgesehene Ausnahme behandeln und unvorhersehbares Verhalten verursachen. Sie können jedoch die C++-Ausnahmebehandlung mit bestimmten Ausnahmetypen oder die strukturierte Ausnahmebehandlung verwenden, wenn die Zugriffsverletzungsausnahme an das Betriebssystem übergeben wird.

Um das Generieren dieser Ausnahme der ersten Chance zu vermeiden, können Sie manuell sicherstellen, dass das Eigenschaftenblatt über die richtigen [Fensterstile](../../mfc/reference/styles-used-by-mfc.md#window-styles)verfügt. Sie müssen die folgenden Formatvorlagen für ein Eigenschaftenblatt festlegen:

- DS_3DLOOK

- DS_CONTROL

- Ws_child

- Ws_tabstop

Sie können die folgenden optionalen Stile verwenden, ohne eine Ausnahme der ersten Chance zu verursachen:

- DS_SHELLFONT

- DS_LOCALEDIT

- Ws_clipchildren

Deaktivieren Sie alle anderen Windows-Stile, da sie nicht mit Eigenschaftenblättern kompatibel sind. Diese Empfehlung gilt nicht für erweiterte Stile. Durch das entsprechende Festlegen dieser Standardstile wird sichergestellt, dass das Eigenschaftenblatt nicht geändert werden muss, und es wird vermieden, die Ausnahme der ersten Chance zu generieren.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CPropertySheet::AddPage](#addpage).

## <a name="cpropertysheetenablestackedtabs"></a><a name="enablestackedtabs"></a>CPropertySheet::EnableStackedTabs

Gibt an, ob Zeilen von Registerkarten in einem Eigenschaftenblatt gestapelt werden sollen.

```
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>Parameter

*bStacked*<br/>
Gibt an, ob gestapelte Registerkarten im Eigenschaftenblatt aktiviert sind. Deaktivieren Sie gestapelte Tags-Zeilen, indem Sie *bStacked* auf FALSE setzen.

### <a name="remarks"></a>Bemerkungen

Wenn ein Eigenschaftenblatt mehr Registerkarten aufweist, als in einer einzelnen Zeile in der Breite des Eigenschaftenblatts passen, werden die Registerkarten standardmäßig in mehreren Zeilen gestapelt. Um Scroll-Registerkarten anstelle von Stapelregisterkarten `EnableStackedTabs` zu verwenden, rufen Sie mit *bStacked* auf FALSE gesetzt auf, bevor Sie [DoModal](#domodal) oder [Create](#create)aufrufen.

Sie müssen `EnableStackedTabs` aufrufen, wenn Sie ein modales oder ein modusloses Eigenschaftenblatt erstellen. Um diesen Stil `CPropertySheet`in eine -derived-Klasse zu integrieren, schreiben Sie einen Nachrichtenhandler für WM_CREATE. In der überschriebenen Version von [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)rufen Sie auf, `EnableStackedTabs( FALSE )` bevor sie die Basisklassenimplementierung aufruft.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]

## <a name="cpropertysheetenddialog"></a><a name="enddialog"></a>CPropertySheet::EndDialog

Beendet das Eigenschaftenblatt.

```
void EndDialog(int nEndID);
```

### <a name="parameters"></a>Parameter

*nEndID*<br/>
Bezeichner, der als Rückgabewert des Eigenschaftenblatts verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird vom Framework aufgerufen, wenn die Schaltfläche OK, Abbrechen oder Schließen gedrückt wird. Rufen Sie diese Memberfunktion auf, wenn ein Ereignis auftritt, das das Eigenschaftenblatt schließen soll.

Diese Memberfunktion wird nur mit einem modalen Dialogfeld verwendet.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CPropertySheet::PressButton](#pressbutton).

## <a name="cpropertysheetgetactiveindex"></a><a name="getactiveindex"></a>CPropertySheet::GetActiveIndex

Ruft die Indexnummer der aktiven Seite des Eigenschaftenblattfensters ab und `GetPage`verwendet dann die zurückgegebene Indexnummer als Parameter für .

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>Rückgabewert

Die Indexnummer der aktiven Seite.

### <a name="example"></a>Beispiel

Siehe beispielfür [CPropertySheet::GetActivePage](#getactivepage).

## <a name="cpropertysheetgetactivepage"></a><a name="getactivepage"></a>CPropertySheet::GetActivePage

Ruft die aktive Seite des Eigenschaftenblattfensters ab.

```
CPropertyPage* GetActivePage() const;
```

### <a name="return-value"></a>Rückgabewert

Der Zeiger auf die aktive Seite.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Memberfunktion, um eine Aktion auf der aktiven Seite auszuführen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]

## <a name="cpropertysheetgetpage"></a><a name="getpage"></a>CPropertySheet::GetPage

Gibt einen Zeiger auf die angegebene Seite in diesem Eigenschaftenblatt zurück.

```
CPropertyPage* GetPage(int nPage) const;
```

### <a name="parameters"></a>Parameter

*nPage*<br/>
Index der gewünschten Seite, beginnend bei 0. Muss zwischen 0 und einer kleiner als die Anzahl der Seiten im Eigenschaftenblatt sein, einschließlich.

### <a name="return-value"></a>Rückgabewert

Der Zeiger auf die Seite, die dem *nPage-Parameter* entspricht.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

## <a name="cpropertysheetgetpagecount"></a><a name="getpagecount"></a>CPropertySheet::GetPageCount

Bestimmt die Anzahl der Seiten, die sich derzeit im Eigenschaftenblatt befinden.

```
int GetPageCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Seiten im Eigenschaftenblatt.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

## <a name="cpropertysheetgetpageindex"></a><a name="getpageindex"></a>CPropertySheet::GetPageIndex

Ruft die Indexnummer der angegebenen Seite im Eigenschaftenblatt ab.

```
int GetPageIndex(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parameter

*pPage*<br/>
Zeigt auf die Seite mit dem zu findenden Index. Lässt keine NULL-Werte zu.

### <a name="return-value"></a>Rückgabewert

Die Indexnummer einer Seite.

### <a name="remarks"></a>Bemerkungen

Sie würden z. `GetPageIndex` B. den Seitenindex abrufen, um [SetActivePage](#setactivepage) oder [GetPage](#getpage)zu verwenden.

### <a name="example"></a>Beispiel

Siehe beispielfür [CPropertySheet::GetActivePage](#getactivepage).

## <a name="cpropertysheetgettabcontrol"></a><a name="gettabcontrol"></a>CPropertySheet::GetTabControl

Ruft einen Zeiger auf ein Registerkartensteuerelement ab, um etwas Spezifisches für das Registerkartensteuerelement zu tun (d. h., um eine der APIs in [CTabCtrl](../../mfc/reference/ctabctrl-class.md)zu verwenden).

```
CTabCtrl* GetTabControl() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein Registerkartensteuerelement.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion beispielsweise auf, wenn Sie während der Initialisierung Bitmaps zu jeder Registerkarte hinzufügen möchten.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]

## <a name="cpropertysheetm_psh"></a><a name="m_psh"></a>CPropertySheet::m_psh

Eine Struktur, deren Member die Eigenschaften von [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)speichern.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Struktur, um die Darstellung des Eigenschaftenblatts zu initialisieren, nachdem es erstellt wurde, aber bevor es mit der [DoModal-Memberfunktion](#domodal) angezeigt wird. Legen Sie beispielsweise den *dwSize-Member* von `m_psh` auf die Größe fest, die das Eigenschaftenblatt haben soll.

Weitere Informationen zu dieser Struktur, einschließlich einer Liste ihrer Mitglieder, finden Sie unter PROPSHEETHEADER im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

## <a name="cpropertysheetmapdialogrect"></a><a name="mapdialogrect"></a>CPropertySheet::MapDialogRect

Konvertiert die Dialogfeldeinheiten eines Rechtecks in Bildschirmeinheiten.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameter

*lpRect*<br/>
Zeigt auf eine [RECT-Struktur](/previous-versions/dd162897\(v=vs.85\)) oder ein [CRect-Objekt,](../../atl-mfc-shared/reference/crect-class.md) das die zu konvertierenden Dialogfeldkoordinaten enthält.

### <a name="remarks"></a>Bemerkungen

Dialogfeldeinheiten werden in Bezug auf die aktuelle Dialogfeld-Basiseinheit angegeben, die von der durchschnittlichen Breite und Höhe der Zeichen in der Schriftart abgeleitet ist, die für Dialogfeldtext verwendet wird. Eine horizontale Einheit ist ein Viertel der Dialogfeld-Basisbreiteneinheit, und eine vertikale Einheit ist ein Achtel der Dialogfeld-Basishöheneinheit.

Die [GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) Windows-Funktion gibt Größeninformationen für die Systemschriftart zurück, Sie können jedoch für jedes Eigenschaftenblatt eine andere Schriftart angeben, wenn Sie den stil DS_SETFONT in der Ressourcendefinitionsdatei verwenden. Die [MapDialogRect](/windows/win32/api/winuser/nf-winuser-mapdialogrect) Windows-Funktion, die im Windows SDK beschrieben wird, verwendet die entsprechende Schriftart für dieses Dialogfeld.

Die `MapDialogRect` Memberfunktion ersetzt die Dialogfeldeinheiten in *lpRect* durch Bildschirmeinheiten (Pixel), sodass das Rechteck verwendet werden kann, um ein Dialogfeld zu erstellen oder ein Steuerelement innerhalb eines Feldes zu positionieren.

## <a name="cpropertysheetoninitdialog"></a><a name="oninitdialog"></a>CPropertySheet::OnInitDialog

Überschreibungen, um die Initialisierung von Eigenschaftenblättern zu erweitern.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Rückgabewert

Gibt an, ob die Anwendung den Eingabefokus auf eines der Steuerelemente im Eigenschaftenblatt festgelegt hat. Wenn `OnInitDialog` ein Wert ungleich Null zurückgegeben wird, legt Windows den Eingabefokus auf das erste Steuerelement im Eigenschaftenblatt fest. Die Anwendung kann 0 nur zurückgeben, wenn sie den Eingabefokus explizit auf eines der Steuerelemente im Eigenschaftenblatt festgelegt hat.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird als Reaktion auf die WM_INITDIALOG Nachricht aufgerufen. Diese Nachricht wird während der [Create-](#create) oder [DoModal-Aufrufe](#domodal) an das Eigenschaftenblatt gesendet, die unmittelbar vor der Anzeige des Eigenschaftenblatts auftreten.

Überschreiben Sie diese Memberfunktion, wenn Sie eine spezielle Verarbeitung durchführen müssen, wenn das Eigenschaftenblatt initialisiert wird. Rufen Sie in der überschriebenen `OnInitDialog` Version zuerst die Basisklasse auf, ignorieren jedoch ihren Rückgabewert. Normalerweise geben Sie TRUE von Ihrer überschriebenen Memberfunktion zurück.

Sie benötigen keinen Nachrichtenzuordnungseintrag für diese Memberfunktion.

## <a name="cpropertysheetpressbutton"></a><a name="pressbutton"></a>CPropertySheet::PressButton

Simuliert die Auswahl der angegebenen Schaltfläche in einem Eigenschaftenblatt.

```
void PressButton(int nButton);
```

### <a name="parameters"></a>Parameter

*nButton*<br/>
nButton : Identifiziert die taste, die gedrückt werden soll. Dieser Parameter kann einer der folgenden Werte sein:

- PSBTN_BACK wählt die Zurück-Taste.

- PSBTN_NEXT wählt die Schaltfläche Weiter.

- PSBTN_FINISH Wählt die Schaltfläche Fertig stellen.

- PSBTN_OK Wählt die Schaltfläche OK.

- PSBTN_APPLYNOW wählt die Schaltfläche Jetzt anwenden.

- PSBTN_CANCEL Wählt die Schaltfläche Abbrechen.

- PSBTN_HELP Wählt die Hilfe-Schaltfläche aus.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zur Windows SDK-Presseschaltfläche finden Sie unter [PSM_PRESSBUTTON.](/windows/win32/Controls/psm-pressbutton)

Ein Aufruf `PressButton` an sendet die [PSN_APPLY](/windows/win32/Controls/psn-apply) Benachrichtigung nicht von einer Eigenschaftenseite an das Framework. Um diese Benachrichtigung zu senden, rufen Sie [CPropertyPage::OnOK](../../mfc/reference/cpropertypage-class.md#onok)auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]

## <a name="cpropertysheetremovepage"></a><a name="removepage"></a>CPropertySheet::RemovePage

Entfernt eine Seite aus dem Eigenschaftenblatt und zerstört das zugehörige Fenster.

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Parameter

*pPage*<br/>
Zeigt auf die Seite, die aus dem Eigenschaftenblatt entfernt werden soll. Lässt keine NULL-Werte zu.

*nPage*<br/>
Index der zu entfernenden Seite. Muss zwischen 0 und einer kleiner als die Anzahl der Seiten im Eigenschaftenblatt sein, einschließlich.

### <a name="remarks"></a>Bemerkungen

Das [CPropertyPage-Objekt](../../mfc/reference/cpropertypage-class.md) selbst wird erst `CPropertySheet` zerstört, wenn der Besitzer des Fensters geschlossen ist.

## <a name="cpropertysheetsetactivepage"></a><a name="setactivepage"></a>CPropertySheet::SetActivePage

Ändert die aktive Seite.

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parameter

*nPage*<br/>
Index der zu setzenden Seite. Sie muss zwischen 0 und einer kleiner als die Anzahl der Seiten im Eigenschaftenblatt sein, einschließlich.

*pPage*<br/>
Zeigt auf die Seite, die im Eigenschaftenblatt festgelegt werden soll. Er darf nicht NULL sein.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Eigenschaftenblatt erfolgreich aktiviert wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie `SetActivePage` z. B., wenn die Aktion eines Benutzers auf einer Seite dazu führen soll, dass eine andere Seite zur aktiven Seite wird.

### <a name="example"></a>Beispiel

Siehe beispielfür [CPropertySheet::GetActivePage](#getactivepage).

## <a name="cpropertysheetsetfinishtext"></a><a name="setfinishtext"></a>CPropertySheet::SetFinishText

Legt den Text in der Schaltfläche Fertig stellen fest.

```
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
Zeigt auf den Text, der auf der Schaltfläche Fertig stellen angezeigt werden soll.

### <a name="remarks"></a>Bemerkungen

Rufen `SetFinishText` Sie an, um den Text auf der Schaltfläche Fertig stellen anzuzeigen, und blenden Sie die Schaltflächen Weiter und Zurück aus, nachdem der Benutzer die Aktion auf der letzten Seite des Assistenten abgeschlossen hat.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

## <a name="cpropertysheetsettitle"></a><a name="settitle"></a>CPropertySheet::SetTitle

Gibt die Beschriftung des Eigenschaftenblatts an (den Text, der in der Titelleiste eines Rahmenfensters angezeigt wird).

```
void SetTitle(
    LPCTSTR lpszText,
    UINT nStyle = 0);
```

### <a name="parameters"></a>Parameter

*nStyle*<br/>
Gibt den Stil des Eigenschaftenblatttitels an. Der Stil muss bei 0 oder als PSH_PROPTITLE angegeben werden. Wenn der Stil als PSH_PROPTITLE festgelegt ist, wird das Wort "Eigenschaften" nach dem als Beschriftung angegebenen Text angezeigt. Wenn Sie `SetTitle`z. B. ("Einfach", PSH_PROPTITLE) aufrufen, wird eine Eigenschaftenblattbeschriftung "Einfache Eigenschaften" angezeigt.

*lpszText*<br/>
Zeigt auf den Text, der als Beschriftung in der Titelleiste des Eigenschaftenblatts verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Standardmäßig verwendet ein Eigenschaftenblatt den Beschriftungsparameter im Eigenschaftenblattkonstruktor.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

## <a name="cpropertysheetsetwizardbuttons"></a><a name="setwizardbuttons"></a>CPropertySheet::SetWizardButtons

Aktiviert oder deaktiviert die Schaltfläche Zurück, Weiter oder Beenden in einem Assistenten-Eigenschaftenblatt.

```
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>Parameter

*dwFlags*<br/>
Eine Reihe von Flags, die die Funktion und Darstellung der Assistentenschaltflächen anpassen. Dieser Parameter kann eine Kombination der folgenden Werte sein:

- PSWIZB_BACK Zurück-Taste

- PSWIZB_NEXT Schaltfläche Weiter

- PSWIZB_FINISH Finish-Taste

- PSWIZB_DISABLEDFINISH Schaltfläche "Deaktiviertes Beenden"

### <a name="remarks"></a>Bemerkungen

Rufen `SetWizardButtons` Sie erst an, nachdem das Dialogfeld geöffnet ist. Sie können doModal nicht anrufen, `SetWizardButtons` bevor Sie [DoModal](#domodal)aufrufen. In der Regel `SetWizardButtons` sollten Sie von [CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive)aufrufen.

Wenn Sie den Text auf der Schaltfläche Fertig stellen oder die Schaltflächen "Weiter" und "Zurück" ausblenden möchten, sobald der Benutzer den Assistenten abgeschlossen hat, rufen Sie [SetFinishText](#setfinishtext)auf. Beachten Sie, dass dieselbe Schaltfläche für Finish und Next freigegeben ist. Sie können eine Schaltfläche "Fertig" oder "Weiter" gleichzeitig anzeigen, jedoch nicht beides.

### <a name="example"></a>Beispiel

A `CPropertySheet` verfügt über drei `CStylePage` `CColorPage`Assistenteneigenschaftenseiten: , , und `CShapePage`.  Das Folgende Codefragment zeigt, wie Sie die Schaltflächen **"Zurück"** und **"Weiter"** auf der Eigenschaftenseite des Assistenten aktivieren und deaktivieren.

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

## <a name="cpropertysheetsetwizardmode"></a><a name="setwizardmode"></a>CPropertySheet::SetWizardMode

Richtet eine Eigenschaftenseite als Assistenten ein.

```
void SetWizardMode();
```

### <a name="remarks"></a>Bemerkungen

Ein wesentliches Merkmal einer Eigenschaftenseite des Assistenten ist, dass der Benutzer mit den Schaltflächen "Weiter" oder "Beenden", "Zurück" und "Abbrechen" anstelle von Registerkarten navigiert.

Rufen `SetWizardMode` Sie an, bevor Sie [DoModal](#domodal)aufrufen. Nach dem `SetWizardMode` `DoModal` Aufruf gibt entweder ID_WIZFINISH (wenn der Benutzer mit der Schaltfläche Fertig stellen schließt) oder IDCANCEL zurück.

`SetWizardMode`setzt das PSH_WIZARD-Flag.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
