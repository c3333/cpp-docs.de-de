---
title: CEditView-Klasse
ms.date: 11/04/2016
f1_keywords:
- CEditView
- AFXEXT/CEditView
- AFXEXT/CEditView::CEditView
- AFXEXT/CEditView::FindText
- AFXEXT/CEditView::GetBufferLength
- AFXEXT/CEditView::GetEditCtrl
- AFXEXT/CEditView::GetPrinterFont
- AFXEXT/CEditView::GetSelectedText
- AFXEXT/CEditView::LockBuffer
- AFXEXT/CEditView::PrintInsideRect
- AFXEXT/CEditView::SerializeRaw
- AFXEXT/CEditView::SetPrinterFont
- AFXEXT/CEditView::SetTabStops
- AFXEXT/CEditView::UnlockBuffer
- AFXEXT/CEditView::OnFindNext
- AFXEXT/CEditView::OnReplaceAll
- AFXEXT/CEditView::OnReplaceSel
- AFXEXT/CEditView::OnTextNotFound
- AFXEXT/CEditView::dwStyleDefault
helpviewer_keywords:
- CEditView [MFC], CEditView
- CEditView [MFC], FindText
- CEditView [MFC], GetBufferLength
- CEditView [MFC], GetEditCtrl
- CEditView [MFC], GetPrinterFont
- CEditView [MFC], GetSelectedText
- CEditView [MFC], LockBuffer
- CEditView [MFC], PrintInsideRect
- CEditView [MFC], SerializeRaw
- CEditView [MFC], SetPrinterFont
- CEditView [MFC], SetTabStops
- CEditView [MFC], UnlockBuffer
- CEditView [MFC], OnFindNext
- CEditView [MFC], OnReplaceAll
- CEditView [MFC], OnReplaceSel
- CEditView [MFC], OnTextNotFound
- CEditView [MFC], dwStyleDefault
ms.assetid: bf38255c-fcbe-450c-95b2-3c5e35f86c37
ms.openlocfilehash: e9b7dea980e607c776e2d50c679042c765080fdb
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78872494"
---
# <a name="ceditview-class"></a>CEditView-Klasse

Ein Ansichtsklassentyp, die die Funktionalität eines Windows-Bearbeitungssteuerelements bereitstellt und verwendet werden kann, um einfache Textbearbeitungsfunktionalität zu implementieren.

## <a name="syntax"></a>Syntax

```
class CEditView : public CCtrlView
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CEditView:: CEditView](#ceditview)|Konstruiert ein Objekt vom Typ `CEditView`.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CEditView:: FindText](#findtext)|Sucht im Text nach einer Zeichenfolge.|
|[CEditView:: getbufferlength](#getbufferlength)|Ruft die Länge des Zeichen Puffers ab.|
|[CEditView:: geteditctrl](#geteditctrl)|Bietet Zugriff auf den `CEdit` Teil eines `CEditView` Objekts (das Windows-Bearbeitungs Steuerelement).|
|[CEditView:: getprinterfont](#getprinterfont)|Ruft die aktuelle Drucker Schriftart ab.|
|[CEditView:: getSelectedText](#getselectedtext)|Ruft die aktuelle Textauswahl ab.|
|[CEditView:: LockBuffer](#lockbuffer)|Sperrt den Puffer.|
|[CEditView::P rintinsiderect](#printinsiderect)|Rendert Text innerhalb eines angegebenen Rechtecks.|
|[CEditView:: SerializeRaw](#serializeraw)|Serialisiert ein `CEditView` Objekt als unformatierten Text auf den Datenträger.|
|[CEditView:: SetPrinterFont](#setprinterfont)|Legt eine neue Drucker Schriftart fest.|
|[CEditView:: settabstopps](#settabstops)|Legt Tabstopps für Bildschirm Anzeige und-Druck fest.|
|[CEditView:: UnlockBuffer](#unlockbuffer)|Entsperrt den Puffer.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CEditView:: onfindnext](#onfindnext)|Findet das nächste Vorkommen einer Text Zeichenfolge.|
|[CEditView:: onreplaceall](#onreplaceall)|Ersetzt alle Vorkommen einer angegebenen Zeichenfolge durch eine neue Zeichenfolge.|
|[CEditView:: onreplacesel](#onreplacesel)|Ersetzt die aktuelle Auswahl.|
|[CEditView:: ontextnotfound](#ontextnotfound)|Wird aufgerufen, wenn ein Suchvorgang keinem weiteren Text entspricht.|

### <a name="public-data-members"></a>Öffentliche Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CEditView::d wstyledefault](#dwstyledefault)|Der Standardstil für Objekte vom Typ `CEditView`.|

## <a name="remarks"></a>Bemerkungen

Die `CEditView`-Klasse bietet die folgenden zusätzlichen Funktionen:

- Drucken

- Suchen und ersetzen.

Da Class `CEditView` eine Ableitung von Class `CView`ist, können Objekte der Klasse `CEditView` mit Dokumenten und Dokumentvorlagen verwendet werden.

Der Text jedes `CEditView` Steuer Elements wird in seinem eigenen globalen Speicher Objekt aufbewahrt. Die Anwendung kann über eine beliebige Anzahl von `CEditView` Objekten verfügen.

Erstellen Sie Objekte vom Typ `CEditView`, wenn Sie ein Bearbeitungsfenster mit der zusätzlich hinzugefügten Funktionalität benötigen, oder wenn Sie eine einfache Text-Editor-Funktionalität wünschen. Ein `CEditView`-Objekt kann den gesamten Client Bereich eines Fensters belegen. Leiten Sie Ihre eigenen Klassen von `CEditView` ab, um die Grundfunktionen hinzuzufügen oder zu ändern, oder um Klassen zu deklarieren, die einer Dokument Vorlage hinzugefügt werden können.

Die Standard Implementierung der-Klasse `CEditView` verarbeitet die folgenden Befehle: ID_EDIT_SELECT_ALL, ID_EDIT_FIND, ID_EDIT_REPLACE, ID_EDIT_REPEAT und ID_FILE_PRINT.

Die standardmäßige Zeichen Beschränkung für `CEditView` ist (1024 \* 1024-1 = 1048575). Dies kann durch Aufrufen der EM_LIMITTEXT-Funktion des zugrunde liegenden Bearbeitungs Steuer Elements geändert werden. Die Grenzwerte unterscheiden sich jedoch je nach Betriebssystem und Typ des Bearbeitungs Steuer Elements (ein-oder mehrzeilige Zeilen). Weitere Informationen zu diesen Grenzwerten finden Sie unter [EM_LIMITTEXT](/windows/win32/Controls/em-limittext).

Wenn Sie dieses Limit in Ihrem Steuerelement ändern möchten, überschreiben Sie die `OnCreate()`-Funktion für die `CEditView`-Klasse, und fügen Sie die folgende Codezeile ein:

[!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]

Für Objekte vom Typ "`CEditView`" (oder für Typen, die von `CEditView`abgeleitet sind) gelten die folgenden Einschränkungen:

- `CEditView` implementiert nicht "true", was Sie sehen, was Sie sehen (WYSIWYG) bearbeiten. Wenn eine Auswahl zwischen der Lesbarkeit auf dem Bildschirm und dem Abgleich der gedruckten Ausgabe besteht, `CEditView` OPTs für die Lesbarkeit des Bildschirms.

- in `CEditView` kann Text nur in einer einzelnen Schriftart angezeigt werden. Es wird keine Sonderzeichen Formatierung unterstützt. Weitere Funktionen finden Sie in der [CRichEditView](../../mfc/reference/cricheditview-class.md) -Klasse.

- Der Text, den ein `CEditView` enthalten kann, ist begrenzt. Die Grenzwerte sind identisch mit denen für das `CEdit`-Steuerelement.

Weitere Informationen zu `CEditView`finden Sie unter [in MFC verfügbare abgeleitete Ansichts Klassen](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[Cctrlview](../../mfc/reference/cctrlview-class.md)

`CEditView`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Afxext. h

##  <a name="ceditview"></a>CEditView:: CEditView

Konstruiert ein Objekt vom Typ `CEditView`.

```
CEditView();
```

### <a name="remarks"></a>Bemerkungen

Nach dem Erstellen des-Objekts müssen Sie die [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) -Funktion vor der Verwendung des Bearbeitungs Steuer Elements abrufen. Wenn Sie eine Klasse von `CEditView` ableiten und Sie mithilfe von `CWinApp::AddDocTemplate`der Vorlage hinzufügen, ruft das Framework diesen Konstruktor und die `Create`-Funktion auf.

##  <a name="dwstyledefault"></a>CEditView::d wstyledefault

Enthält den Standardstil des `CEditView` Objekts.

```
static const DWORD dwStyleDefault;
```

### <a name="remarks"></a>Bemerkungen

Übergeben Sie dieses statische Element als *dwstyle* -Parameter der `Create`-Funktion, um den Standardstil für das `CEditView` Objekt zu erhalten.

##  <a name="findtext"></a>CEditView:: FindText

Ruft die `FindText`-Funktion auf, um den Text Puffer des `CEditView` Objekts zu durchsuchen.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bNext = TRUE,
    BOOL bCase = TRUE);
```

### <a name="parameters"></a>Parameter

*lpszfind*<br/>
Der zu verwendende Text.

*bnext*<br/>
Gibt die Suchrichtung an. TRUE gibt an, dass die Suchrichtung an das Ende des Puffers gerichtet ist. FALSE gibt an, dass die Suchrichtung an den Anfang des Puffers gerichtet ist.

*bcase*<br/>
Gibt an, ob bei der Suche Groß-und Kleinschreibung Bei "true" wird die Groß-/Kleinschreibung beachtet. Bei "false" wird die Groß-/Kleinschreibung nicht beachtet.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Suchtext gefunden wurde. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion durchsucht den Text im Puffer nach dem von *lpszfind*angegebenen Text, beginnend bei der aktuellen Auswahl, in der durch *bnext*angegebenen Richtung und bei Angabe der Groß-/Kleinschreibung, die in *bcase*angegeben ist. Wenn der Text gefunden wird, wird die Auswahl auf den gefundenen Text festgelegt, und es wird ein Wert ungleich 0 (null) zurückgegeben. Wenn der Text nicht gefunden wird, gibt die Funktion 0 zurück.

Normalerweise ist es nicht erforderlich, die `FindText` Funktion aufzurufen, es sei denn, Sie überschreiben `OnFindNext`, der `FindText`aufruft.

##  <a name="getbufferlength"></a>CEditView:: getbufferlength

Mit dieser Member-Funktion können Sie die Anzahl von Zeichen abrufen, die sich derzeit im Puffer des Bearbeitungs Steuer Elements befinden, ohne das NULL-Terminator zu einschließen.

```
UINT GetBufferLength() const;
```

### <a name="return-value"></a>Rückgabewert

Die Länge der Zeichenfolge im Puffer.

##  <a name="geteditctrl"></a>CEditView:: geteditctrl

Ruft `GetEditCtrl` auf, um einen Verweis auf das Bearbeitungs Steuerelement zu erhalten, das von der Bearbeitungs Ansicht verwendet wird.

```
CEdit& GetEditCtrl() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf ein `CEdit`-Objekt.

### <a name="remarks"></a>Bemerkungen

Dieses Steuerelement ist vom Typ [CEdit](../../mfc/reference/cedit-class.md), sodass Sie das Windows-Bearbeitungs Steuerelement direkt mithilfe der `CEdit` Member-Funktionen bearbeiten können.

> [!CAUTION]
>  Wenn Sie das `CEdit`-Objekt verwenden, kann der Zustand des zugrunde liegenden Windows-Bearbeitungs Steuer Elements geändert werden. Sie sollten z. b. die Registerkarten Einstellungen nicht mithilfe der [CEdit:: settabstopps](../../mfc/reference/cedit-class.md#settabstops) -Funktion ändern, da `CEditView` diese Einstellungen für die Verwendung im Bearbeitungs Steuerelement und beim Drucken zwischenspeichert. Verwenden Sie stattdessen [CEditView:: settabstopps](#settabstops).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]

##  <a name="getprinterfont"></a>CEditView:: getprinterfont

Ruft `GetPrinterFont` auf, um einen Zeiger auf ein [CFont](../../mfc/reference/cfont-class.md) -Objekt zu erhalten, das die aktuelle Drucker Schriftart beschreibt.

```
CFont* GetPrinterFont() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `CFont` Objekt, das die aktuelle Drucker Schriftart angibt. NULL, wenn die Drucker Schriftart nicht festgelegt wurde. Der Zeiger kann temporär sein und sollte nicht für eine spätere Verwendung gespeichert werden.

### <a name="remarks"></a>Bemerkungen

Wenn die Drucker Schriftart nicht festgelegt wurde, wird das Standarddruck Verhalten der `CEditView` Klasse mit derselben Schriftart gedruckt, die für die Anzeige verwendet wird.

Verwenden Sie diese Funktion, um die aktuelle Drucker Schriftart zu bestimmen. Wenn Sie nicht die gewünschte Drucker Schriftart ist, verwenden Sie [CEditView:: SetPrinterFont](#setprinterfont) , um Sie zu ändern.

##  <a name="getselectedtext"></a>CEditView:: getSelectedText

Ruft `GetSelectedText` auf, um den markierten Text in ein `CString` Objekt zu kopieren, bis zum Ende der Auswahl oder das Zeichen, das dem ersten Wagen Rücklauf Zeichen in der Auswahl vorangestellt ist.

```
void GetSelectedText(CString& strResult) const;
```

### <a name="parameters"></a>Parameter

*Strauch Ergebnis*<br/>
Ein Verweis auf das `CString` Objekt, das den ausgewählten Text empfangen soll.

##  <a name="lockbuffer"></a>CEditView:: LockBuffer

Rufen Sie diese Member-Funktion auf, um einen Zeiger auf den Puffer zu erhalten. Der Puffer sollte nicht geändert werden.

```
LPCTSTR LockBuffer() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Puffer des Bearbeitungs Steuer Elements.

##  <a name="onfindnext"></a>CEditView:: onfindnext

Durchsucht den Text im Puffer nach dem Text, der von *lpszfind*in der durch *bnext*angegebenen Richtung angegeben wird, wobei die Groß-/Kleinschreibung von *bcase*angegeben wird.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase);
```

### <a name="parameters"></a>Parameter

*lpszfind*<br/>
Der zu verwendende Text.

*bnext*<br/>
Gibt die Suchrichtung an. TRUE gibt an, dass die Suchrichtung an das Ende des Puffers gerichtet ist. FALSE gibt an, dass die Suchrichtung an den Anfang des Puffers gerichtet ist.

*bcase*<br/>
Gibt an, ob bei der Suche Groß-und Kleinschreibung Bei "true" wird die Groß-/Kleinschreibung beachtet. Bei "false" wird die Groß-/Kleinschreibung nicht beachtet.

### <a name="remarks"></a>Bemerkungen

Die Suche beginnt am Anfang der aktuellen Auswahl und wird durch einen [FindText](#findtext)-Aufrufvorgang erreicht. In der Standard Implementierung ruft `OnFindNext` [ontextnotfound](#ontextnotfound) auf, wenn der Text nicht gefunden wird.

Überschreiben Sie `OnFindNext`, um die Art zu ändern, in der ein `CEditView`abgeleitetes Objekt Text `CEditView` ruft `OnFindNext` auf, wenn der Benutzer im Dialogfeld Standardsuche die Schaltfläche weiter suchen auswählt.

##  <a name="onreplaceall"></a>CEditView:: onreplaceall

`CEditView` ruft `OnReplaceAll` auf, wenn der Benutzer die Schaltfläche Alle ersetzen im Dialogfeld Standard Ersetzung auswählt.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase);
```

### <a name="parameters"></a>Parameter

*lpszfind*<br/>
Der zu verwendende Text.

*lpszreplace*<br/>
Der Text, durch den der Suchtext ersetzt werden soll.

*bcase*<br/>
Gibt an, ob bei der Suche Groß-und Kleinschreibung Bei "true" wird die Groß-/Kleinschreibung beachtet. Bei "false" wird die Groß-/Kleinschreibung nicht beachtet.

### <a name="remarks"></a>Bemerkungen

`OnReplaceAll` durchsucht den Text im Puffer nach dem Text, der von *lpszfind*angegeben wird, wobei die Groß-/Kleinschreibung von *bcase*angegeben wird. Die Suche beginnt am Anfang der aktuellen Auswahl. Jedes Mal, wenn der Suchtext gefunden wird, ersetzt diese Funktion das Vorkommen des Texts durch den von *lpszreplace*angegebenen Text. Die Suche erfolgt durch einen Befehl von [FindText](#findtext). In der Standard Implementierung wird [ontextnotfound](#ontextnotfound) aufgerufen, wenn der Text nicht gefunden wird.

Wenn die aktuelle Auswahl nicht mit *lpszfind*identisch ist, wird die Auswahl auf das erste Vorkommen des von *lpszfind* angegebenen Texts aktualisiert, und es wird kein Replace-Vorgang ausgeführt. Dadurch kann der Benutzer bestätigen, dass dies beabsichtigt ist, wenn die Auswahl nicht dem zu ersetzenden Text entspricht.

Überschreiben Sie `OnReplaceAll`, um die Art und Weise zu ändern, wie ein `CEditView`abgeleitetes Objekt

##  <a name="onreplacesel"></a>CEditView:: onreplacesel

`CEditView` ruft `OnReplaceSel` auf, wenn der Benutzer im Dialogfeld Standard Ersetzung die Schaltfläche ersetzen auswählt.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Parameter

*lpszfind*<br/>
Der zu verwendende Text.

*bnext*<br/>
Gibt die Suchrichtung an. TRUE gibt an, dass die Suchrichtung an das Ende des Puffers gerichtet ist. FALSE gibt an, dass die Suchrichtung an den Anfang des Puffers gerichtet ist.

*bcase*<br/>
Gibt an, ob bei der Suche Groß-und Kleinschreibung Bei "true" wird die Groß-/Kleinschreibung beachtet. Bei "false" wird die Groß-/Kleinschreibung nicht beachtet.

*lpszreplace*<br/>
Der Text, durch den der gefundene Text ersetzt werden soll.

### <a name="remarks"></a>Bemerkungen

Nachdem Sie die Auswahl ersetzt haben, durchsucht diese Funktion den Text im Puffer nach dem nächsten Vorkommen des Texts, der von *lpszfind*in der durch *bnext*angegebenen Richtung angegeben wird, wobei die Groß-/Kleinschreibung von *bcase*angegeben wird. Die Suche erfolgt durch einen Befehl von [FindText](#findtext). Wenn der Text nicht gefunden wird, wird " [ontextnotfound](#ontextnotfound) " aufgerufen.

Überschreiben Sie `OnReplaceSel`, um die Methode zu ändern, mit der ein `CEditView`abgeleitetes Objekt den markierten Text ersetzt

##  <a name="ontextnotfound"></a>CEditView:: ontextnotfound

Überschreiben Sie diese Funktion, um die Standard Implementierung zu ändern, mit der die Windows-Funktion `MessageBeep`aufgerufen wird.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parameter

*lpszfind*<br/>
Der zu verwendende Text.

##  <a name="printinsiderect"></a>CEditView::P rintinsiderect

Ruft `PrintInsideRect` auf, um Text in dem durch *rectlayout*angegebenen Rechteck auszugeben.

```
UINT PrintInsideRect(
    CDC *pDC,
    RECT& rectLayout,
    UINT nIndexStart,
    UINT nIndexStop);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Zeiger auf den Drucker Gerätekontext.

*Neulayout*<br/>
Verweis auf ein [CRect](../../atl-mfc-shared/reference/crect-class.md) -Objekt oder eine [Rect-Struktur](/windows/win32/api/windef/ns-windef-rect) , die das Rechteck angibt, in dem der Text gerendert werden soll.

*nindexstart*<br/>
Index innerhalb des Puffers des ersten Zeichens, das gerendert werden soll.

*nindexstoppt*<br/>
Index innerhalb des Puffers des Zeichens nach dem letzten Zeichen, das gerendert werden soll.

### <a name="return-value"></a>Rückgabewert

Der Index des nächsten zu druckenden Zeichens (d. h. das Zeichen nach dem letzten Zeichen, das gerendert wird).

### <a name="remarks"></a>Bemerkungen

Wenn das `CEditView` Steuerelement nicht über die Format ES_AUTOHSCROLL verfügt, wird Text innerhalb des renderingrechtecks umschließt. Wenn das Steuerelement den Stil ES_AUTOHSCROLL hat, wird der Text am rechten Rand des Rechtecks abgeschnitten.

Das `rect.bottom` Element des *rectlayout* -Objekts wird so geändert, dass die Abmessungen des Rechtecks den Teil des ursprünglichen Rechtecks definieren, der durch den Text belegt ist.

##  <a name="serializeraw"></a>CEditView:: SerializeRaw

Ruft `SerializeRaw` auf, damit ein `CArchive`-Objekt den Text im `CEditView`-Objekt in eine Textdatei liest oder schreibt.

```
void SerializeRaw(CArchive& ar);
```

### <a name="parameters"></a>Parameter

*Tempel*<br/>
Verweis auf das `CArchive` Objekt, in dem der serialisierte Text gespeichert wird.

### <a name="remarks"></a>Bemerkungen

`SerializeRaw` unterscheidet sich von `CEditView`internen Implementierung von `Serialize` darin, dass nur der Text gelesen und geschrieben wird, ohne dass Objekt Beschreibungsdaten vorangestellt sind.

##  <a name="setprinterfont"></a>CEditView:: SetPrinterFont

Ruft `SetPrinterFont` auf, um die Drucker Schriftart auf die von *pfont*angegebene Schriftart festzulegen.

```
void SetPrinterFont(CFont* pFont);
```

### <a name="parameters"></a>Parameter

*pfont*<br/>
Ein Zeiger auf ein Objekt vom Typ `CFont`. Wenn der Wert NULL ist, basiert die Schriftart, die für den Druck verwendet wird, auf der Anzeige Schriftart.

### <a name="remarks"></a>Bemerkungen

Wenn Sie möchten, dass Ihre Ansicht immer eine bestimmte Schriftart zum Drucken verwendet, fügen Sie einen `SetPrinterFont` in der `OnPreparePrinting`-Funktion Ihrer Klasse ein. Diese virtuelle Funktion wird vor dem Drucken aufgerufen, sodass die Schriftart Änderung stattfindet, bevor der Inhalt der Ansicht gedruckt wird.

##  <a name="settabstops"></a>CEditView:: settabstopps

Mit dieser Funktion können Sie die Tabstopps festlegen, die für die Anzeige und den Druck verwendet werden.

```
void SetTabStops(int nTabStops);
```

### <a name="parameters"></a>Parameter

*ntabstopps*<br/>
Breite der einzelnen Tabstopps in Dialogfeld Einheiten.

### <a name="remarks"></a>Bemerkungen

Nur eine einzelne Tab-Stopp-Breite wird unterstützt. (`CEdit`-Objekte unterstützen mehrere Registerkarten.) Breiten befinden sich in Dialog Einheiten, bei denen ein-vierter der durchschnittlichen Zeichenbreite (auf Grundlage von Groß-und Kleinbuchstaben nur alphabetische Zeichen) der Schriftart verwendet wird, die zum Zeitpunkt der Druck-oder Anzeige verwendet wurde. Sie sollten `CEdit::SetTabStops` nicht verwenden, da `CEditView` den Tabstopp Wert Zwischenspeichern muss.

Diese Funktion ändert nur die Registerkarten des Objekts, für das Sie aufgerufen wird. Um die Tabstopps für jedes `CEditView` Objekt in der Anwendung zu ändern, müssen Sie die `SetTabStops`-Funktion jedes Objekts aufzurufen.

### <a name="example"></a>Beispiel

Dieses Code Fragment legt die Tabstopps im-Steuerelement auf jedes vierte Zeichen fest, indem die vom Steuerelement verwendete Schriftart sorgfältig gemessen wird.

[!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]

##  <a name="unlockbuffer"></a>CEditView:: UnlockBuffer

Mit dieser Member-Funktion können Sie den Puffer entsperren.

```
void UnlockBuffer() const;
```

### <a name="remarks"></a>Bemerkungen

Ruft `UnlockBuffer` auf, nachdem Sie den von [LockBuffer](#lockbuffer)zurückgegebenen Zeiger verwendet haben.

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel-SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView-Klasse](../../mfc/reference/cctrlview-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CEdit-Klasse](../../mfc/reference/cedit-class.md)<br/>
[CDocument-Klasse](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate-Klasse](../../mfc/reference/cdoctemplate-class.md)<br/>
[CCtrlView-Klasse](../../mfc/reference/cctrlview-class.md)<br/>
[CRichEditView-Klasse](../../mfc/reference/cricheditview-class.md)
