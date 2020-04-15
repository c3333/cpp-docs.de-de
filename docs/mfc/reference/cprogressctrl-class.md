---
title: CProgressCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CProgressCtrl
- AFXCMN/CProgressCtrl
- AFXCMN/CProgressCtrl::CProgressCtrl
- AFXCMN/CProgressCtrl::Create
- AFXCMN/CProgressCtrl::CreateEx
- AFXCMN/CProgressCtrl::GetBarColor
- AFXCMN/CProgressCtrl::GetBkColor
- AFXCMN/CProgressCtrl::GetPos
- AFXCMN/CProgressCtrl::GetRange
- AFXCMN/CProgressCtrl::GetState
- AFXCMN/CProgressCtrl::GetStep
- AFXCMN/CProgressCtrl::OffsetPos
- AFXCMN/CProgressCtrl::SetBarColor
- AFXCMN/CProgressCtrl::SetBkColor
- AFXCMN/CProgressCtrl::SetMarquee
- AFXCMN/CProgressCtrl::SetPos
- AFXCMN/CProgressCtrl::SetRange
- AFXCMN/CProgressCtrl::SetState
- AFXCMN/CProgressCtrl::SetStep
- AFXCMN/CProgressCtrl::StepIt
helpviewer_keywords:
- CProgressCtrl [MFC], CProgressCtrl
- CProgressCtrl [MFC], Create
- CProgressCtrl [MFC], CreateEx
- CProgressCtrl [MFC], GetBarColor
- CProgressCtrl [MFC], GetBkColor
- CProgressCtrl [MFC], GetPos
- CProgressCtrl [MFC], GetRange
- CProgressCtrl [MFC], GetState
- CProgressCtrl [MFC], GetStep
- CProgressCtrl [MFC], OffsetPos
- CProgressCtrl [MFC], SetBarColor
- CProgressCtrl [MFC], SetBkColor
- CProgressCtrl [MFC], SetMarquee
- CProgressCtrl [MFC], SetPos
- CProgressCtrl [MFC], SetRange
- CProgressCtrl [MFC], SetState
- CProgressCtrl [MFC], SetStep
- CProgressCtrl [MFC], StepIt
ms.assetid: 222630f4-1598-4026-8198-51649b1192ab
ms.openlocfilehash: c5eb6a93cd68c2dafb76af3b0e42da8b56566e25
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364007"
---
# <a name="cprogressctrl-class"></a>CProgressCtrl-Klasse

Stellt die Funktionalität des allgemeinen Windows-Statusanzeige-Steuerelements bereit.

## <a name="syntax"></a>Syntax

```
class CProgressCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CProgressCtrl::CProgressCtrl](#cprogressctrl)|Erstellt ein `CProgressCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CProgressCtrl::Erstellen](#create)|Erstellt ein Statusleistensteuerelement und fügt `CProgressCtrl` es an ein Objekt an.|
|[CProgressCtrl::CreateEx](#createex)|Erstellt ein Fortschrittssteuerelement mit den angegebenen erweiterten `CProgressCtrl` Windows-Stilen und fügt es an ein Objekt an.|
|[CProgressCtrl::GetBarColor](#getbarcolor)|Ruft die Farbe der Statusanzeigeleiste für das aktuelle Fortschrittsleistensteuerelement ab.|
|[CProgressCtrl::GetBkColor](#getbkcolor)|Ruft die Hintergrundfarbe der aktuellen Fortschrittsleiste ab.|
|[CProgressCtrl::GetPos](#getpos)|Ruft die aktuelle Position der Fortschrittsleiste ab.|
|[CProgressCtrl::GetRange](#getrange)|Ruft die unteren und oberen Grenzwerte des Bereichs des Fortschrittsleistensteuerelements ab.|
|[CProgressCtrl::GetState](#getstate)|Ruft den Status des aktuellen Fortschrittsbalkensteuerelements ab.|
|[CProgressCtrl::GetStep](#getstep)|Ruft das Schrittinkrement für den Fortschrittsbalken des aktuellen Fortschrittsbalkensteuerelements ab.|
|[CProgressCtrl::OffsetPos](#offsetpos)|Verschiebt die aktuelle Position eines Fortschrittsbalkensteuerelements um ein angegebenes Inkrement und zeichnet den Balken neu, um die neue Position widerzuspiegeln.|
|[CProgressCtrl::SetBarColor](#setbarcolor)|Legt die Farbe der Fortschrittsanzeigeleiste im aktuellen Fortschrittsbalkensteuerelement fest.|
|[CProgressCtrl::SetBkColor](#setbkcolor)|Legt die Hintergrundfarbe für die Fortschrittsleiste fest.|
|[CProgressCtrl::SetMarquee](#setmarquee)|Schaltet den Festzeltmodus für das aktuelle Fortschrittsleistensteuerelement ein oder aus.|
|[CProgressCtrl::SetPos](#setpos)|Legt die aktuelle Position für ein Fortschrittsbalkensteuerelement fest und zeichnet die Leiste neu, um die neue Position widerzuspiegeln.|
|[CProgressCtrl::SetRange](#setrange)|Legt die minimalen und maximalen Bereiche für ein Fortschrittsbalkensteuerelement fest und zeichnet die Leiste neu, um die neuen Bereiche widerzuspiegeln.|
|[CProgressCtrl::SetState](#setstate)|Legt den Status des aktuellen Statusanzeige-Steuerelements fest.|
|[CProgressCtrl::SetStep](#setstep)|Gibt das Schrittinkrement für ein Fortschrittsleistensteuerelement an.|
|[CProgressCtrl::StepIt](#stepit)|Verschiebt die aktuelle Position für ein Fortschrittsbalkensteuerelement durch das Schrittinkrement (siehe [SetStep](#setstep)) und zeichnet den Balken neu, um die neue Position widerzuspiegeln.|

## <a name="remarks"></a>Bemerkungen

Ein Fortschrittsbalkensteuerelement ist ein Fenster, das eine Anwendung verwenden kann, um den Fortschritt eines langwierigen Vorgangs anzuzeigen. Es besteht aus einem Rechteck, das nach und nach gefüllt wird, von links nach rechts, mit der Systemhervorhebung Farbe, wie eine Operation fortschreitet.

Ein Fortschrittsbalkensteuerelement hat einen Bereich und eine aktuelle Position. Der Bereich stellt die Gesamtdauer des Vorgangs dar, und die aktuelle Position stellt den Fortschritt dar, den die Anwendung zum Abschließen des Vorgangs gemacht hat. Die Fensterprozedur verwendet den Bereich und die aktuelle Position, um den Prozentsatz der Fortschrittsleiste zu bestimmen, die mit der Hervorhebungsfarbe gefüllt werden soll. Da die Bereichs- und aktuellen Positionswerte als signierte Ganzzahlen ausgedrückt werden, liegt der mögliche Bereich der aktuellen Positionswerte zwischen -2.147.483.648 und 2.147.483.647.

Weitere Informationen zur `CProgressCtrl`Verwendung von finden Sie unter [Steuerelemente](../../mfc/controls-mfc.md) und [Verwenden von CProgressCtrl](../../mfc/using-cprogressctrl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CProgressCtrl`

## <a name="requirements"></a>Anforderungen

**Header:** afxcmn.h

## <a name="cprogressctrlcprogressctrl"></a><a name="cprogressctrl"></a>CProgressCtrl::CProgressCtrl

Erstellt ein `CProgressCtrl`-Objekt.

```
CProgressCtrl();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie `CProgressCtrl` nach `CProgressCtrl::Create` dem Erstellen des Objekts das Fortschrittsleistensteuerelement auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]

## <a name="cprogressctrlcreate"></a><a name="create"></a>CProgressCtrl::Erstellen

Erstellt ein Statusleistensteuerelement und fügt `CProgressCtrl` es an ein Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Gibt den Stil des Fortschrittsleistensteuerelements an. Wenden Sie eine beliebige Kombination von Fensterstilen an, die in [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) im Windows SDK beschrieben sind, zusätzlich zu den folgenden Fortschrittsleistensteuerungsstilen auf das Steuerelement:

- PBS_VERTICAL Zeigt Fortschrittsinformationen vertikal von oben nach unten an. Ohne dieses Flag wird das Fortschrittsleistensteuerelement horizontal, von links nach rechts angezeigt.

- PBS_SMOOTH Zeigt eine schrittweise, reibungslose Füllung der Fortschrittsbalkensteuerung an. Ohne dieses Flag wird das Steuerelement mit Blöcken gefüllt.

*Rect*<br/>
Gibt die Größe und Position des Fortschrittsbalkensteuerelements an. Dabei kann es sich entweder um ein [CRect-Objekt](../../atl-mfc-shared/reference/crect-class.md) oder eine [RECT-Struktur](/previous-versions/dd162897\(v=vs.85\)) handelt. Da es sich bei dem Steuerelement um ein untergeordnetes Fenster handelt, sind die angegebenen Koordinaten relativ zum Clientbereich des *pParentWnd*.

*pParentWnd*<br/>
Gibt das übergeordnete Fenster des Fortschrittsleistensteuerelements an, in der Regel eine `CDialog`. Es darf nicht NULL sein.

*nID*<br/>
Gibt die ID des Fortschrittsbalkensteuerelements an.

### <a name="return-value"></a>Rückgabewert

TRUE, `CProgressCtrl` wenn das Objekt erfolgreich erstellt wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CProgressCtrl` ein Objekt in zwei Schritten. Rufen Sie zunächst den Konstruktor `CProgressCtrl` auf, der `Create`das Objekt erstellt, und dann aufrufen Sie , das das Fortschrittsleistensteuerelement erstellt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]

## <a name="cprogressctrlcreateex"></a><a name="createex"></a>CProgressCtrl::CreateEx

Erstellt ein Steuerelement (ein untergeordnetes Fenster) und ordnet es dem `CProgressCtrl` Objekt zu.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwExStyle*<br/>
Gibt den erweiterten Stil des zu erstellenden Steuerelements an. Eine Liste der erweiterten Windows-Stile finden Sie im *dwExStyle-Parameter* für [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) im Windows SDK.

*dwStyle*<br/>
Gibt den Stil des Fortschrittsleistensteuerelements an. Wenden Sie eine beliebige Kombination von Fensterstilen an, die in [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) im Windows SDK beschrieben sind.

*Rect*<br/>
Ein Verweis auf eine [RECT-Struktur,](/previous-versions/dd162897\(v=vs.85\)) die die Größe und Position des zu erstellenden Fensters in den Clientkoordinaten von *pParentWnd*beschreibt.

*pParentWnd*<br/>
Ein Zeiger auf das Fenster, das das übergeordnete Steuerelement ist.

*nID*<br/>
Die untergeordnete Fenster-ID des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Verwenden `CreateEx` Sie anstelle von [Erstellen,](#create) um erweiterte Windows-Formatvorlagen anzuwenden, die durch das Erweiterte Windows-Stilvorwort **WS_EX_** angegeben werden.

## <a name="cprogressctrlgetbarcolor"></a><a name="getbarcolor"></a>CProgressCtrl::GetBarColor

Ruft die Farbe der Statusanzeigeleiste für das aktuelle Fortschrittsleistensteuerelement ab.

```
COLORREF GetBarColor() const;
```

### <a name="return-value"></a>Rückgabewert

Die Farbe des aktuellen Fortschrittsbalkens, der als [COLORREF-Wert](/windows/win32/gdi/colorref) dargestellt wird, oder CLR_DEFAULT, wenn die Statusanzeigebalkenfarbe die Standardfarbe ist.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PBM_GETBARCOLOR](/windows/win32/Controls/pbm-getbarcolor) Nachricht, die im Windows SDK beschrieben wird.

## <a name="cprogressctrlgetbkcolor"></a><a name="getbkcolor"></a>CProgressCtrl::GetBkColor

Ruft die Hintergrundfarbe der aktuellen Fortschrittsleiste ab.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Rückgabewert

Die Hintergrundfarbe des aktuellen Fortschrittsbalkens, der als [COLORREF-Wert](/windows/win32/gdi/colorref) dargestellt wird.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PBM_GETBKCOLOR](/windows/win32/Controls/pbm-getbkcolor) Nachricht, die im Windows SDK beschrieben wird.

## <a name="cprogressctrlgetpos"></a><a name="getpos"></a>CProgressCtrl::GetPos

Ruft die aktuelle Position des Fortschrittsbalkens ab.

```
int GetPos();
```

### <a name="return-value"></a>Rückgabewert

Die Position der Fortschrittsbalkensteuerung.

### <a name="remarks"></a>Bemerkungen

Die Position des Fortschrittsleistensteuerelements ist nicht die physische Position auf dem Bildschirm, sondern zwischen dem oberen und unteren Bereich, der in [SetRange](#setrange)angegeben ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]

## <a name="cprogressctrlgetrange"></a><a name="getrange"></a>CProgressCtrl::GetRange

Ruft die aktuellen unteren und oberen Grenzwerte oder den Bereich des Fortschrittsleistensteuerelements ab.

```
void GetRange(
    int& nLower,
    int& nUpper);
```

### <a name="parameters"></a>Parameter

*nNieder*<br/>
Ein Verweis auf eine ganze Zahl, die die untere Grenze des Fortschrittsbalkensteuerelements empfängt.

*nUpper*<br/>
Ein Verweis auf eine ganze Zahl, die die obere Grenze des Fortschrittsbalkensteuerelements empfängt.

### <a name="remarks"></a>Bemerkungen

Diese Funktion kopiert die Werte der unteren und oberen Grenzwerte in die ganzen Zahlen, auf die *nLower* bzw. *nUpper*verweisen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]

## <a name="cprogressctrlgetstate"></a><a name="getstate"></a>CProgressCtrl::GetState

Ruft den Status des aktuellen Fortschrittsbalkensteuerelements ab.

```
int GetState() const;
```

### <a name="return-value"></a>Rückgabewert

Der Status des aktuellen Fortschrittsbalkensteuerelements, das einer der folgenden Werte ist:

|Wert|State|
|-----------|-----------|
|PBST_NORMAL|In Bearbeitung|
|PBST_ERROR|Fehler|
|PBST_PAUSED|Angehalten|

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PBM_GETSTATE](/windows/win32/Controls/pbm-getstate) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Das folgende Codebeispiel definiert die Variable `m_progressCtrl`, die für den programmgesteuerten Zugriff auf das Statusanzeige-Steuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird der Status des aktuellen Statusleistensteuerelements abgerufen.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]

## <a name="cprogressctrlgetstep"></a><a name="getstep"></a>CProgressCtrl::GetStep

Ruft das Schrittinkrement für den Fortschrittsbalken des aktuellen Fortschrittsbalkensteuerelements ab.

```
int GetStep() const;
```

### <a name="return-value"></a>Rückgabewert

Das Schrittinkrement des Fortschrittsbalkens.

### <a name="remarks"></a>Bemerkungen

Das Schrittinkrement ist der Betrag, um den ein Aufruf von [CProgressCtrl::StepIt](#stepit) die aktuelle Position des Fortschrittsbalkens erhöht.

Diese Methode sendet die [PBM_GETSTEP](/windows/win32/Controls/pbm-getstep) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Das folgende Codebeispiel definiert die Variable `m_progressCtrl`, die für den programmgesteuerten Zugriff auf das Statusanzeige-Steuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird das Schrittinkrement des aktuellen Fortschrittsleistensteuerelements abgerufen.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]

## <a name="cprogressctrloffsetpos"></a><a name="offsetpos"></a>CProgressCtrl::OffsetPos

Verschiebt die aktuelle Position des Fortschrittsbalkensteuerelements um das durch *nPos* angegebene Inkrement und zeichnet den Balken neu, um die neue Position widerzuspiegeln.

```
int OffsetPos(int nPos);
```

### <a name="parameters"></a>Parameter

*Npos*<br/>
Betrag, um die Position vorzufahren.

### <a name="return-value"></a>Rückgabewert

Die vorherige Position des Fortschrittsbalkensteuerelements.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]

## <a name="cprogressctrlsetbarcolor"></a><a name="setbarcolor"></a>CProgressCtrl::SetBarColor

Legt die Farbe der Fortschrittsanzeigeleiste im aktuellen Fortschrittsbalkensteuerelement fest.

```
COLORREF SetBarColor(COLORREF clrBar);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*clrBar*|[in] Ein [COLORREF-Wert,](/windows/win32/gdi/colorref) der die neue Farbe der Statusanzeigeleiste angibt. Geben Sie CLR_DEFAULT an, der die Standardfarbe des Statusbalkens verwenden soll.|

### <a name="return-value"></a>Rückgabewert

Die vorherige Farbe der Statusanzeigeleiste, dargestellt als [COLORREF-Wert,](/windows/win32/gdi/colorref) oder CLR_DEFAULT, wenn die Farbe der Fortschrittsanzeigediebe die Standardfarbe ist.

### <a name="remarks"></a>Bemerkungen

Die `SetBarColor` Methode legt die Farbe der Fortschrittsleiste nur fest, wenn ein Windows [Vista-Design](/windows/win32/Controls/visual-styles-overview) nicht wirksam ist.

Diese Methode sendet die [PBM_SETBARCOLOR](/windows/win32/Controls/pbm-setbarcolor) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Das folgende Codebeispiel definiert die Variable `m_progressCtrl`, die für den programmgesteuerten Zugriff auf das Statusanzeige-Steuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die Farbe der Statusleiste in Rot, Grün, Blau oder Standard geändert.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]

## <a name="cprogressctrlsetbkcolor"></a><a name="setbkcolor"></a>CProgressCtrl::SetBkColor

Legt die Hintergrundfarbe für die Fortschrittsleiste fest.

```
COLORREF SetBkColor(COLORREF clrNew);
```

### <a name="parameters"></a>Parameter

*clrNeu*<br/>
Ein COLORREF-Wert, der die neue Hintergrundfarbe angibt. Geben Sie den CLR_DEFAULT Wert für die Verwendung der Standardhintergrundfarbe für die Fortschrittsleiste an.

### <a name="return-value"></a>Rückgabewert

Der [COLORREF-Wert,](/windows/win32/gdi/colorref) der die vorherige Hintergrundfarbe angibt, oder CLR_DEFAULT, wenn die Hintergrundfarbe die Standardfarbe ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]

## <a name="cprogressctrlsetmarquee"></a><a name="setmarquee"></a>CProgressCtrl::SetMarquee

Schaltet den Festzeltmodus für das aktuelle Fortschrittsleistensteuerelement ein oder aus.

```
BOOL SetMarquee(
    BOOL fMarqueeMode,
    int nInterval);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*fMarqueeMode*|[in] TRUE, um den Festzeltmodus einzuschalten, oder FALSE, um den Festzeltmodus auszuschalten.|
|*nIntervall*|[in] Zeit in Millisekunden zwischen Aktualisierungen der Rahmenanimation.|

### <a name="return-value"></a>Rückgabewert

Diese Methode gibt immer TRUE zurück.

### <a name="remarks"></a>Bemerkungen

Wenn der Festzeltmodus aktiviert ist, wird die Fortschrittsleiste animiert und scrollt wie ein Schild auf einem Theaterzelt.

Diese Methode sendet die [PBM_SETMARQUEE](/windows/win32/Controls/pbm-setmarquee) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Das folgende Codebeispiel definiert die Variable `m_progressCtrl`, die für den programmgesteuerten Zugriff auf das Statusanzeige-Steuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die Bildlaufanimation im Festzelt gestartet und beendet.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]

## <a name="cprogressctrlsetpos"></a><a name="setpos"></a>CProgressCtrl::SetPos

Legt die aktuelle Position des Fortschrittsbalkensteuerelements fest, wie in *nPos* angegeben, und zeichnet den Balken neu, um die neue Position widerzuspiegeln.

```
int SetPos(int nPos);
```

### <a name="parameters"></a>Parameter

*Npos*<br/>
Neue Position der Fortschrittsbalkensteuerung.

### <a name="return-value"></a>Rückgabewert

Die vorherige Position des Fortschrittsbalkensteuerelements.

### <a name="remarks"></a>Bemerkungen

Die Position des Fortschrittsleistensteuerelements ist nicht die physische Position auf dem Bildschirm, sondern zwischen dem oberen und unteren Bereich, der in [SetRange](#setrange)angegeben ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]

## <a name="cprogressctrlsetrange"></a><a name="setrange"></a>CProgressCtrl::SetRange

Legt die oberen und unteren Grenzen des Bereichs des Fortschrittsbalkensteuerelements fest und zeichnet die Leiste neu, um die neuen Bereiche widerzuspiegeln.

```
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>Parameter

*nNieder*<br/>
Gibt die untere Grenze des Bereichs an (Standard ist Null).

*nUpper*<br/>
Gibt die obere Grenze des Bereichs an (Standardwert ist 100).

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion `SetRange32` legt den 32-Bit-Bereich für die Fortschrittssteuerung fest.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]

## <a name="cprogressctrlsetstate"></a><a name="setstate"></a>CProgressCtrl::SetState

Legt den Status des aktuellen Statusanzeige-Steuerelements fest.

```
int SetState(int iState);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*iState*|[in] Der Status, der die Fortschrittsleiste festgelegt werden soll. Verwenden Sie einen der folgenden Werte:<br /><br /> - PBST_NORMAL - In Arbeit<br />- PBST_ERROR - Fehler<br />- PBST_PAUSED - Angehalten|

### <a name="return-value"></a>Rückgabewert

Der vorherige Status des aktuellen Statusanzeige-Steuerelements.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [PBM_SETSTATE](/windows/win32/Controls/pbm-setstate) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Das folgende Codebeispiel definiert die Variable `m_progressCtrl`, die für den programmgesteuerten Zugriff auf das Statusanzeige-Steuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird der Status des aktuellen Statusanzeige-Steuerelements auf angehalten oder In Bearbeitung festgelegt.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]

## <a name="cprogressctrlsetstep"></a><a name="setstep"></a>CProgressCtrl::SetStep

Gibt das Schrittinkrement für ein Fortschrittsleistensteuerelement an.

```
int SetStep(int nStep);
```

### <a name="parameters"></a>Parameter

*nSchritt*<br/>
Neues Schrittinkrement.

### <a name="return-value"></a>Rückgabewert

Das vorherige Schrittinkrement.

### <a name="remarks"></a>Bemerkungen

Das Schrittinkrement ist der `CProgressCtrl::StepIt` Betrag, um den ein Aufruf zur Erhöhung der aktuellen Position des Fortschrittsbalkens erhöht.

Das Standardschrittinkrement ist 10.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]

## <a name="cprogressctrlstepit"></a><a name="stepit"></a>CProgressCtrl::StepIt

Verschiebt die aktuelle Position für ein Fortschrittsbalkensteuerelement durch das Schrittinkrement und zeichnet den Balken neu, um die neue Position widerzuspiegeln.

```
int StepIt();
```

### <a name="return-value"></a>Rückgabewert

Die vorherige Position des Fortschrittsbalkensteuerelements.

### <a name="remarks"></a>Bemerkungen

Das Schrittinkrement `CProgressCtrl::SetStep` wird von der Memberfunktion festgelegt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
