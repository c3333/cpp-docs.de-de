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
ms.openlocfilehash: 33b5975eea534eeaf308f73b5ca7fca2cd76787f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753201"
---
# <a name="ceditview-class"></a>CEditView-Klasse

Ein Ansichtsklassentyp, die die Funktionalität eines Windows-Bearbeitungssteuerelements bereitstellt und verwendet werden kann, um einfache Textbearbeitungsfunktionalität zu implementieren.

## <a name="syntax"></a>Syntax

```
class CEditView : public CCtrlView
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CEditView::CEditView](#ceditview)|Konstruiert ein Objekt vom Typ `CEditView`.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CEditView::FindText](#findtext)|Sucht nach einer Zeichenfolge im Text.|
|[CEditView::GetBufferLength](#getbufferlength)|Ruft die Länge des Zeichenpuffers ab.|
|[CEditView::GetEditCtrl](#geteditctrl)|Bietet Zugriff `CEdit` auf den `CEditView` Teil eines Objekts (das Windows-Bearbeitungssteuerelement).|
|[CEditView::GetPrinterFont](#getprinterfont)|Ruft die aktuelle Druckerschriftart ab.|
|[CEditView::GetSelectedText](#getselectedtext)|Ruft die aktuelle Textauswahl ab.|
|[CEditView::LockBuffer](#lockbuffer)|Sperrt den Puffer.|
|[CEditView::PrintInsideRect](#printinsiderect)|Rendert Text innerhalb eines bestimmten Rechtecks.|
|[CEditView::SerializeRaw](#serializeraw)|Serialisiert ein `CEditView` Objekt auf dem Datenträger als Rohtext.|
|[CEditView::SetPrinterFont](#setprinterfont)|Legt eine neue Druckerschriftart fest.|
|[CEditView::SetTabStops](#settabstops)|Legt Tabstopps für die Bildschirmanzeige und den Druck fest.|
|[CEditView::UnlockBuffer](#unlockbuffer)|Entsperrt den Puffer.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CEditView::OnFindNext](#onfindnext)|Sucht das nächste Vorkommen einer Textzeichenfolge.|
|[CEditView::OnReplaceAll](#onreplaceall)|Ersetzt alle Vorkommen einer bestimmten Zeichenfolge durch eine neue Zeichenfolge.|
|[CEditView::OnReplaceSel](#onreplacesel)|Ersetzt die aktuelle Auswahl.|
|[CEditView::OnTextNotFound](#ontextnotfound)|Wird aufgerufen, wenn ein Findvorgang nicht mit weiterem Text übereinstimmt.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CEditView::dwStyleDefault](#dwstyledefault)|Standardformat für Objekte `CEditView`vom Typ .|

## <a name="remarks"></a>Bemerkungen

Die `CEditView` Klasse bietet die folgenden zusätzlichen Funktionen:

- Drucken

- Suchen und ersetzen.

Da `CEditView` die Klasse eine `CView`Ableitung `CEditView` der Klasse ist, können Objekte der Klasse mit Dokumenten und Dokumentvorlagen verwendet werden.

Der `CEditView` Text jedes Steuerelements wird in seinem eigenen globalen Speicherobjekt gespeichert. Ihre Anwendung kann eine `CEditView` beliebige Anzahl von Objekten haben.

Erstellen Sie `CEditView` Objekte vom Typ, wenn Sie ein Bearbeitungsfenster mit den oben aufgeführten Funktionen oder einfache Texteditor-Funktionalität wünschen. Ein `CEditView` Objekt kann den gesamten Clientbereich eines Fensters einnehmen. Leiten Sie Ihre `CEditView` eigenen Klassen ab, um die grundlegende Funktionalität hinzuzufügen oder zu ändern oder Klassen zu deklarieren, die einer Dokumentvorlage hinzugefügt werden können.

Die Standardimplementierung `CEditView` der Klasse behandelt die folgenden Befehle: ID_EDIT_SELECT_ALL, ID_EDIT_FIND, ID_EDIT_REPLACE, ID_EDIT_REPEAT und ID_FILE_PRINT.

Die Standardzeichengrenze `CEditView` für ist (1024 \* 1024 - 1 = 1048575). Dies kann durch Aufrufen der EM_LIMITTEXT Funktion des zugrunde liegenden Bearbeitungssteuerelements geändert werden. Die Grenzwerte sind jedoch je nach Betriebssystem und Art der Bearbeitungssteuerung (ein- oder mehrzeilig) unterschiedlich. Weitere Informationen zu diesen Grenzwerten finden Sie unter [EM_LIMITTEXT](/windows/win32/Controls/em-limittext).

Um diesen Grenzwert in Ihrem Steuerelement `OnCreate()` zu `CEditView` ändern, überschreiben Sie die Funktion für Ihre Klasse und fügen Sie die folgende Codezeile ein:

[!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]

Objekte des `CEditView` Typs (oder `CEditView`von ) haben die folgenden Einschränkungen:

- `CEditView`implementiert nicht wahr, was Sie sehen, ist, was Sie erhalten (WYSIWYG) Bearbeitung. Wenn es eine Wahl zwischen Lesbarkeit auf dem `CEditView` Bildschirm und passender gedruckter Ausgabe gibt, entscheidet man sich für die Lesbarkeit des Bildschirms.

- `CEditView`kann Text nur in einer einzigen Schriftart anzeigen. Es wird keine Sonderzeichenformatierung unterstützt. Weitere Funktionen finden Sie unter Klasse [CRichEditView.](../../mfc/reference/cricheditview-class.md)

- Die Textmenge, `CEditView` die ein enthalten kann, ist begrenzt. Die Grenzwerte sind die `CEdit` gleichen wie für das Steuerelement.

Weitere Informationen `CEditView`zu finden Sie [unter Abgeleitete Ansichtsklassen, die in MFC verfügbar sind.](../../mfc/derived-view-classes-available-in-mfc.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CEditView`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxext.h

## <a name="ceditviewceditview"></a><a name="ceditview"></a>CEditView::CEditView

Konstruiert ein Objekt vom Typ `CEditView`.

```
CEditView();
```

### <a name="remarks"></a>Bemerkungen

Nach dem Erstellen des Objekts müssen Sie die [Funktion CWnd::Create](../../mfc/reference/cwnd-class.md#create) aufrufen, bevor das Bearbeitungssteuerelement verwendet wird. Wenn Sie eine Klasse `CEditView` von der Vorlage `CWinApp::AddDocTemplate`ableiten und sie mithilfe von `Create` hinzufügen, ruft das Framework sowohl diesen Konstruktor als auch die Funktion auf.

## <a name="ceditviewdwstyledefault"></a><a name="dwstyledefault"></a>CEditView::dwStyleDefault

Enthält den Standardstil `CEditView` des Objekts.

```
static const DWORD dwStyleDefault;
```

### <a name="remarks"></a>Bemerkungen

Übergeben Sie diesen statischen Member als *dwStyle-Parameter* `Create` der `CEditView` Funktion, um den Standardstil für das Objekt abzuerhalten.

## <a name="ceditviewfindtext"></a><a name="findtext"></a>CEditView::FindText

Rufen `FindText` Sie die `CEditView` Funktion auf, um den Textpuffer des Objekts zu durchsuchen.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bNext = TRUE,
    BOOL bCase = TRUE);
```

### <a name="parameters"></a>Parameter

*lpszFind*<br/>
Der zu findende Text.

*bNext*<br/>
Gibt die Richtung der Suche an. Wenn TRUE, befindet sich die Suchrichtung am Ende des Puffers. Wenn FALSE, ist die Suchrichtung zum Anfang des Puffers.

*bCase*<br/>
Gibt an, ob bei der Suche die Groß-/Kleinschreibung beachtet wird. Wenn TRUE, wird bei der Suche die Groß-/Kleinschreibung beachtet. Wenn FALSE, wird bei der Suche die Groß-/Kleinschreibung nicht berücksichtigt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Suchtext gefunden wird; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion durchsucht den Text im Puffer nach dem von *lpszFind*angegebenen Text, beginnend bei der aktuellen Auswahl, in die von *bNext*angegebene Richtung und mit der von *bCase*angegebenen Groß-/Kleinschreibung. Wenn der Text gefunden wird, wird die Auswahl auf den gefundenen Text festgelegt und ein Wert ungleich Null zurückgegeben. Wenn der Text nicht gefunden wird, gibt die Funktion 0 zurück.

Normalerweise müssen Sie die `FindText` Funktion nur aufrufen, wenn Sie überschreiben, `OnFindNext`die aufruft. `FindText`

## <a name="ceditviewgetbufferlength"></a><a name="getbufferlength"></a>CEditView::GetBufferLength

Rufen Sie diese Memberfunktion auf, um die Anzahl der Zeichen abzurufen, die sich derzeit im Puffer des Bearbeitungssteuerelements befinden, ohne den Nullabschluss.

```
UINT GetBufferLength() const;
```

### <a name="return-value"></a>Rückgabewert

Die Länge der Zeichenfolge im Puffer.

## <a name="ceditviewgeteditctrl"></a><a name="geteditctrl"></a>CEditView::GetEditCtrl

Rufen `GetEditCtrl` Sie auf, um einen Verweis auf das Bearbeitungssteuerelement abzurufen, das von der Bearbeitungsansicht verwendet wird.

```
CEdit& GetEditCtrl() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf ein `CEdit`-Objekt.

### <a name="remarks"></a>Bemerkungen

Dieses Steuerelement hat den Typ [CEdit](../../mfc/reference/cedit-class.md), sodass Sie `CEdit` das Windows-Bearbeitungssteuerelement direkt mit den Memberfunktionen bearbeiten können.

> [!CAUTION]
> Die `CEdit` Verwendung des Objekts kann den Status des zugrunde liegenden Windows-Bearbeitungssteuerelements ändern. Beispielsweise sollten Sie die Registerkarteneinstellungen nicht mit der Funktion [CEdit::SetTabStops](../../mfc/reference/cedit-class.md#settabstops) ändern, da `CEditView` diese Einstellungen sowohl im Bearbeitungssteuerelement als auch beim Drucken zwischengespeichert werden. Verwenden Sie stattdessen [CEditView::SetTabStops](#settabstops).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]

## <a name="ceditviewgetprinterfont"></a><a name="getprinterfont"></a>CEditView::GetPrinterFont

Rufen `GetPrinterFont` Sie auf, um einen Zeiger auf ein [CFont-Objekt](../../mfc/reference/cfont-class.md) zu erhalten, das die aktuelle Druckerschriftart beschreibt.

```
CFont* GetPrinterFont() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CFont` ein Objekt, das die aktuelle Druckerschriftart angibt; NULL, wenn die Druckerschriftart nicht festgelegt wurde. Der Zeiger kann temporär sein und sollte nicht für eine spätere Verwendung gespeichert werden.

### <a name="remarks"></a>Bemerkungen

Wenn die Druckerschriftart nicht festgelegt wurde, `CEditView` besteht das Standarddruckverhalten der Klasse darin, mit derselben Schriftart zu drucken, die für die Anzeige verwendet wird.

Verwenden Sie diese Funktion, um die aktuelle Druckerschriftart zu bestimmen. Wenn es sich nicht um die gewünschte Druckerschriftart handelt, verwenden Sie [CEditView::SetPrinterFont,](#setprinterfont) um sie zu ändern.

## <a name="ceditviewgetselectedtext"></a><a name="getselectedtext"></a>CEditView::GetSelectedText

Rufen `GetSelectedText` Sie auf, den `CString` markierten Text in ein Objekt zu kopieren, bis zum Ende der Auswahl oder das Zeichen vor dem ersten Wagenrückgabezeichen in der Auswahl.

```cpp
void GetSelectedText(CString& strResult) const;
```

### <a name="parameters"></a>Parameter

*strResult*<br/>
Ein Verweis `CString` auf das Objekt, das den markierten Text empfangen soll.

## <a name="ceditviewlockbuffer"></a><a name="lockbuffer"></a>CEditView::LockBuffer

Rufen Sie diese Memberfunktion auf, um einen Zeiger auf den Puffer abzurufen. Der Puffer sollte nicht geändert werden.

```
LPCTSTR LockBuffer() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Puffer des Bearbeitungssteuerelements.

## <a name="ceditviewonfindnext"></a><a name="onfindnext"></a>CEditView::OnFindNext

Durchsucht den Text im Puffer nach dem von *lpszFind*angegebenen Text in die von *bNext*angegebene Richtung mit der von *bCase*angegebenen Groß-/Kleinschreibung.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase);
```

### <a name="parameters"></a>Parameter

*lpszFind*<br/>
Der zu findende Text.

*bNext*<br/>
Gibt die Richtung der Suche an. Wenn TRUE, befindet sich die Suchrichtung am Ende des Puffers. Wenn FALSE, ist die Suchrichtung zum Anfang des Puffers.

*bCase*<br/>
Gibt an, ob bei der Suche die Groß-/Kleinschreibung beachtet wird. Wenn TRUE, wird bei der Suche die Groß-/Kleinschreibung beachtet. Wenn FALSE, wird bei der Suche die Groß-/Kleinschreibung nicht berücksichtigt.

### <a name="remarks"></a>Bemerkungen

Die Suche beginnt am Anfang der aktuellen Auswahl und wird durch einen Aufruf von [FindText](#findtext)durchgeführt. Ruft in der `OnFindNext` Standardimplementierung [OnTextNotFound](#ontextnotfound) auf, wenn der Text nicht gefunden wird.

Überschreiben, `OnFindNext` um die `CEditView`Art und Weise zu ändern, wie ein -abgeleitetes Objekt Text durchsucht. `CEditView`wird `OnFindNext` angezeigt, wenn der Benutzer die Schaltfläche Weiter suchen im Standarddialogfeld Suchen auswählt.

## <a name="ceditviewonreplaceall"></a><a name="onreplaceall"></a>CEditView::OnReplaceAll

`CEditView`wird `OnReplaceAll` angezeigt, wenn der Benutzer im Standarddialogfeld Ersetzen die Schaltfläche Alle ersetzen auswählt.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase);
```

### <a name="parameters"></a>Parameter

*lpszFind*<br/>
Der zu findende Text.

*lpszReplace*<br/>
Der Text, der den Suchtext ersetzen soll.

*bCase*<br/>
Gibt an, ob bei der Suche die Groß-/Kleinschreibung beachtet wird. Wenn TRUE, wird bei der Suche die Groß-/Kleinschreibung beachtet. Wenn FALSE, wird bei der Suche die Groß-/Kleinschreibung nicht berücksichtigt.

### <a name="remarks"></a>Bemerkungen

`OnReplaceAll`durchsucht den Text im Puffer nach dem von *lpszFind*angegebenen Text mit der von *bCase*angegebenen Groß-/Kleinschreibung . Die Suche beginnt am Anfang der aktuellen Auswahl. Jedes Mal, wenn der Suchtext gefunden wird, ersetzt diese Funktion das Vorkommen des Textes durch den von *lpszReplace*angegebenen Text. Die Suche erfolgt über einen Aufruf von [FindText](#findtext). In der Standardimplementierung wird [OnTextNotFound](#ontextnotfound) aufgerufen, wenn der Text nicht gefunden wird.

Wenn die aktuelle Auswahl nicht mit *lpszFind*übereinstimmt, wird die Auswahl auf das erste Vorkommen des von *lpszFind* angegebenen Textes aktualisiert, und es wird kein Ersetzen ausgeführt. Auf diese Weise kann der Benutzer bestätigen, dass dies der Fall ist, wenn die Auswahl nicht mit dem zu ersetzenden Text übereinstimmt.

Überschreiben, `OnReplaceAll` um die `CEditView`Art und Weise zu ändern, wie ein -abgeleitetes Objekt Text ersetzt.

## <a name="ceditviewonreplacesel"></a><a name="onreplacesel"></a>CEditView::OnReplaceSel

`CEditView`wird `OnReplaceSel` angezeigt, wenn der Benutzer die Schaltfläche Ersetzen im Standarddialogfeld Ersetzen auswählt.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Parameter

*lpszFind*<br/>
Der zu findende Text.

*bNext*<br/>
Gibt die Richtung der Suche an. Wenn TRUE, befindet sich die Suchrichtung am Ende des Puffers. Wenn FALSE, ist die Suchrichtung zum Anfang des Puffers.

*bCase*<br/>
Gibt an, ob bei der Suche die Groß-/Kleinschreibung beachtet wird. Wenn TRUE, wird bei der Suche die Groß-/Kleinschreibung beachtet. Wenn FALSE, wird bei der Suche die Groß-/Kleinschreibung nicht berücksichtigt.

*lpszReplace*<br/>
Der Text, der den gefundenen Text ersetzen soll.

### <a name="remarks"></a>Bemerkungen

Nach dem Ersetzen der Auswahl durchsucht diese Funktion den Text im Puffer nach dem nächsten Vorkommen des von *lpszFind*angegebenen Textes in die von *bNext*angegebene Richtung mit der von *bCase*angegebenen Groß-/Kleinschreibung. Die Suche erfolgt über einen Aufruf von [FindText](#findtext). Wenn der Text nicht gefunden wird, wird [OnTextNotFound](#ontextnotfound) aufgerufen.

Überschreiben, `OnReplaceSel` um die `CEditView`Art und Weise zu ändern, wie ein -derivedes Objekt den markierten Text ersetzt.

## <a name="ceditviewontextnotfound"></a><a name="ontextnotfound"></a>CEditView::OnTextNotFound

Überschreiben Sie diese Funktion, um die Standardimplementierung zu ändern, die die Windows-Funktion `MessageBeep`aufruft.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parameter

*lpszFind*<br/>
Der zu findende Text.

## <a name="ceditviewprintinsiderect"></a><a name="printinsiderect"></a>CEditView::PrintInsideRect

Aufruf `PrintInsideRect` zum Drucken von Text in dem von *rectLayout*angegebenen Rechteck.

```
UINT PrintInsideRect(
    CDC *pDC,
    RECT& rectLayout,
    UINT nIndexStart,
    UINT nIndexStop);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Zeiger auf den Druckergerätekontext.

*rectLayout*<br/>
Verweis auf ein [CRect-Objekt](../../atl-mfc-shared/reference/crect-class.md) oder eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die das Rechteck angibt, in dem der Text gerendert werden soll.

*nIndexStart*<br/>
Index innerhalb des Puffers des ersten zu rendernden Zeichens.

*nIndexStop*<br/>
Index innerhalb des Puffers des Zeichens, das dem letzten zu rendernden Zeichen folgt.

### <a name="return-value"></a>Rückgabewert

Der Index des nächsten zu druckenden Zeichens (d. h. das Zeichen, das dem zuletzt gerenderten Zeichen folgt).

### <a name="remarks"></a>Bemerkungen

Wenn `CEditView` das Steuerelement nicht über die Formatvorlage ES_AUTOHSCROLL verfügt, wird Text innerhalb des Renderrechtecks umbrochen. Wenn das Steuerelement den Stil ES_AUTOHSCROLL hat, wird der Text am rechten Rand des Rechtecks abgeschnitten.

Das `rect.bottom` Element des *rectLayout-Objekts* wird so geändert, dass die Abmessungen des Rechtecks den Teil des ursprünglichen Rechtecks definieren, der vom Text belegt wird.

## <a name="ceditviewserializeraw"></a><a name="serializeraw"></a>CEditView::SerializeRaw

Rufen `SerializeRaw` Sie `CArchive` auf, um ein Objekt `CEditView` lesen zu lassen oder den Text im Objekt in eine Textdatei zu schreiben.

```cpp
void SerializeRaw(CArchive& ar);
```

### <a name="parameters"></a>Parameter

*ar*<br/>
Verweis auf `CArchive` das Objekt, in dem der serialisierte Text gespeichert wird.

### <a name="remarks"></a>Bemerkungen

`SerializeRaw`unterscheidet sich `CEditView`von der `Serialize` internen Implementierung von insofern, als sie nur den Text liest und schreibt, ohne dass die Daten der Objektbeschreibung vorangehen.

## <a name="ceditviewsetprinterfont"></a><a name="setprinterfont"></a>CEditView::SetPrinterFont

Rufen `SetPrinterFont` Sie an, um die Druckerschriftart auf die von *pFont*angegebene Schriftart festzulegen.

```cpp
void SetPrinterFont(CFont* pFont);
```

### <a name="parameters"></a>Parameter

*pFont*<br/>
Ein Zeiger auf ein `CFont`Objekt vom Typ . Wenn NULL, basiert die Schriftart, die für den Druck verwendet wird, auf der Anzeigeschriftart.

### <a name="remarks"></a>Bemerkungen

Wenn Sie möchten, dass Ihre Ansicht immer eine bestimmte `SetPrinterFont` Schriftart zum `OnPreparePrinting` Drucken verwendet, fügen Sie einen Aufruf an in die Funktion Ihrer Klasse ein. Diese virtuelle Funktion wird aufgerufen, bevor der Druck vorgangt, sodass die Schriftartänderung vor dem Drucken des Ansichtsinhalts erfolgt.

## <a name="ceditviewsettabstops"></a><a name="settabstops"></a>CEditView::SetTabStops

Rufen Sie diese Funktion auf, um die Tabstopps festzulegen, die für die Anzeige und den Druck verwendet werden.

```cpp
void SetTabStops(int nTabStops);
```

### <a name="parameters"></a>Parameter

*nTabStops*<br/>
Breite jedes Tabstopps in Dialogeinheiten.

### <a name="remarks"></a>Bemerkungen

Es wird nur eine einzelne Tabstoppbreite unterstützt. ( `CEdit` Objekte unterstützen mehrere Registerkartenbreiten.) Breiten sind in Dialogeinheiten, die ein Viertel der durchschnittlichen Zeichenbreite (nur basierend auf Groß- und Kleinbuchstaben) der Schriftart entsprechen, die zum Zeitpunkt des Druckens oder Anzeigens verwendet wurde. Sie sollten `CEdit::SetTabStops` nicht `CEditView` verwenden, da muss der Tabstoppwert zwischenspeichern.

Diese Funktion ändert nur die Registerkarten des Objekts, für das sie aufgerufen wird. Um die Tabstopps `CEditView` für jedes Objekt in der `SetTabStops` Anwendung zu ändern, rufen Sie die Funktion jedes Objekts auf.

### <a name="example"></a>Beispiel

Dieses Codefragment legt die Tabstopps im Steuerelement auf jedes vierte Zeichen fest, indem die Schriftart, die das Steuerelement verwendet, sorgfältig misst.

[!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]

## <a name="ceditviewunlockbuffer"></a><a name="unlockbuffer"></a>CEditView::UnlockBuffer

Rufen Sie diese Memberfunktion auf, um den Puffer zu entsperren.

```cpp
void UnlockBuffer() const;
```

### <a name="remarks"></a>Bemerkungen

Rufen `UnlockBuffer` Sie an, nachdem Sie den von [LockBuffer](#lockbuffer)zurückgegebenen Zeiger verwendet haben.

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView-Klasse](../../mfc/reference/cctrlview-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CDocument-Klasse](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate-Klasse](../../mfc/reference/cdoctemplate-class.md)<br/>
[CCtrlView-Klasse](../../mfc/reference/cctrlview-class.md)<br/>
[CRichEditView-Klasse](../../mfc/reference/cricheditview-class.md)
