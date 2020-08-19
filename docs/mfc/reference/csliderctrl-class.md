---
title: CSliderCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSliderCtrl
- AFXCMN/CSliderCtrl
- AFXCMN/CSliderCtrl::CSliderCtrl
- AFXCMN/CSliderCtrl::ClearSel
- AFXCMN/CSliderCtrl::ClearTics
- AFXCMN/CSliderCtrl::Create
- AFXCMN/CSliderCtrl::CreateEx
- AFXCMN/CSliderCtrl::GetBuddy
- AFXCMN/CSliderCtrl::GetChannelRect
- AFXCMN/CSliderCtrl::GetLineSize
- AFXCMN/CSliderCtrl::GetNumTics
- AFXCMN/CSliderCtrl::GetPageSize
- AFXCMN/CSliderCtrl::GetPos
- AFXCMN/CSliderCtrl::GetRange
- AFXCMN/CSliderCtrl::GetRangeMax
- AFXCMN/CSliderCtrl::GetRangeMin
- AFXCMN/CSliderCtrl::GetSelection
- AFXCMN/CSliderCtrl::GetThumbLength
- AFXCMN/CSliderCtrl::GetThumbRect
- AFXCMN/CSliderCtrl::GetTic
- AFXCMN/CSliderCtrl::GetTicArray
- AFXCMN/CSliderCtrl::GetTicPos
- AFXCMN/CSliderCtrl::GetToolTips
- AFXCMN/CSliderCtrl::SetBuddy
- AFXCMN/CSliderCtrl::SetLineSize
- AFXCMN/CSliderCtrl::SetPageSize
- AFXCMN/CSliderCtrl::SetPos
- AFXCMN/CSliderCtrl::SetRange
- AFXCMN/CSliderCtrl::SetRangeMax
- AFXCMN/CSliderCtrl::SetRangeMin
- AFXCMN/CSliderCtrl::SetSelection
- AFXCMN/CSliderCtrl::SetThumbLength
- AFXCMN/CSliderCtrl::SetTic
- AFXCMN/CSliderCtrl::SetTicFreq
- AFXCMN/CSliderCtrl::SetTipSide
- AFXCMN/CSliderCtrl::SetToolTips
helpviewer_keywords:
- CSliderCtrl [MFC], CSliderCtrl
- CSliderCtrl [MFC], ClearSel
- CSliderCtrl [MFC], ClearTics
- CSliderCtrl [MFC], Create
- CSliderCtrl [MFC], CreateEx
- CSliderCtrl [MFC], GetBuddy
- CSliderCtrl [MFC], GetChannelRect
- CSliderCtrl [MFC], GetLineSize
- CSliderCtrl [MFC], GetNumTics
- CSliderCtrl [MFC], GetPageSize
- CSliderCtrl [MFC], GetPos
- CSliderCtrl [MFC], GetRange
- CSliderCtrl [MFC], GetRangeMax
- CSliderCtrl [MFC], GetRangeMin
- CSliderCtrl [MFC], GetSelection
- CSliderCtrl [MFC], GetThumbLength
- CSliderCtrl [MFC], GetThumbRect
- CSliderCtrl [MFC], GetTic
- CSliderCtrl [MFC], GetTicArray
- CSliderCtrl [MFC], GetTicPos
- CSliderCtrl [MFC], GetToolTips
- CSliderCtrl [MFC], SetBuddy
- CSliderCtrl [MFC], SetLineSize
- CSliderCtrl [MFC], SetPageSize
- CSliderCtrl [MFC], SetPos
- CSliderCtrl [MFC], SetRange
- CSliderCtrl [MFC], SetRangeMax
- CSliderCtrl [MFC], SetRangeMin
- CSliderCtrl [MFC], SetSelection
- CSliderCtrl [MFC], SetThumbLength
- CSliderCtrl [MFC], SetTic
- CSliderCtrl [MFC], SetTicFreq
- CSliderCtrl [MFC], SetTipSide
- CSliderCtrl [MFC], SetToolTips
ms.assetid: dd12b084-4eda-4550-a810-8f3cfb06b871
ms.openlocfilehash: 8dfdcf34474027180708045131a19bf6f7e14512
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562531"
---
# <a name="csliderctrl-class"></a>CSliderCtrl-Klasse

Stellt die Funktionalität des allgemeinen Windows-Schieberegler-Steuerelements bereit.

## <a name="syntax"></a>Syntax

```
class CSliderCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|BESCHREIBUNG|
|----------|-----------------|
|[CSliderCtrl:: CSliderCtrl](#csliderctrl)|Erstellt ein `CSliderCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CSliderCtrl:: ClearSEL](#clearsel)|Löscht die aktuelle Auswahl in einem Schieberegler-Steuerelement.|
|[CSliderCtrl:: ClearTics](#cleartics)|Entfernt die aktuellen Teil Striche von einem Schieberegler-Steuerelement.|
|[CSliderCtrl:: Create](#create)|Erstellt ein Schieberegler-Steuerelement und fügt es an ein- `CSliderCtrl` Objekt an.|
|[CSliderCtrl:: kreateex](#createex)|Erstellt ein Schieberegler-Steuerelement mit den angegebenen erweiterten Windows-Stilen und fügt es an ein- `CSliderCtrl` Objekt an.|
|[CSliderCtrl:: GetBuddy](#getbuddy)|Ruft das Handle für ein Fenster des Schieberegler-Steuerelement-Steuer Elements an einem angegebenen Speicherort ab.|
|[CSliderCtrl:: GetChannelRect](#getchannelrect)|Ruft die Größe des Kanals des Schieberegler-Steuer Elements ab.|
|[CSliderCtrl:: getlinesize](#getlinesize)|Ruft die Zeilengröße eines Schieberegler-Steuer Elements ab.|
|[CSliderCtrl:: GetNumTics](#getnumtics)|Ruft die Anzahl von Teil Strichen in einem Schieberegler-Steuerelement ab.|
|[CSliderCtrl:: getpagesize](#getpagesize)|Ruft die Seitengröße eines Schieberegler-Steuer Elements ab.|
|[CSliderCtrl:: GetPos](#getpos)|Ruft die aktuelle Position des Schiebereglers ab.|
|[CSliderCtrl:: GetRange](#getrange)|Ruft die minimalen und maximalen Positionen für einen Schieberegler ab.|
|[CSliderCtrl:: getrangemax](#getrangemax)|Ruft die maximale Position für einen Schieberegler ab.|
|[CSliderCtrl:: getrangemin](#getrangemin)|Ruft die minimale Position für einen Schieberegler ab.|
|[CSliderCtrl:: GetSelection](#getselection)|Ruft den Bereich der aktuellen Auswahl ab.|
|[CSliderCtrl:: getthumblength](#getthumblength)|Ruft die Länge des Schiebereglers im aktuellen TrackBar-Steuerelement ab.|
|[CSliderCtrl:: getthumbrect](#getthumbrect)|Ruft die Größe des Zieh Punkts des Schieberegler-Steuer Elements ab.|
|[CSliderCtrl:: GetTic](#gettic)|Ruft die Position des angegebenen Teil Strichs ab.|
|[CSliderCtrl:: GetTicArray](#getticarray)|Ruft das Array von Teil Strich Positionen für ein Schieberegler-Steuerelement ab.|
|[CSliderCtrl:: GetTicPos](#getticpos)|Ruft die Position des angegebenen Teil Strichs in Client Koordinaten ab.|
|[CSliderCtrl:: gettooltips](#gettooltips)|Ruft das Handle für das QuickInfo-Steuerelement ab, das dem Schieberegler-Steuerelement zugewiesen ist, sofern vorhanden|
|[CSliderCtrl:: SetBuddy](#setbuddy)|Weist ein Fenster als Buddy-Fenster für ein Schieberegler-Steuerelement zu.|
|[CSliderCtrl:: setlinesize](#setlinesize)|Legt die Zeilengröße eines Schieberegler-Steuer Elements fest.|
|[CSliderCtrl:: setPageSize](#setpagesize)|Legt die Seitengröße eines Schieberegler-Steuer Elements fest.|
|[CSliderCtrl:: SetPos](#setpos)|Legt die aktuelle Position des Schiebereglers fest.|
|[CSliderCtrl:: abge](#setrange)|Legt die minimalen und maximalen Positionen für einen Schieberegler fest.|
|[CSliderCtrl:: s-max](#setrangemax)|Legt die maximale Position für einen Schieberegler fest.|
|[CSliderCtrl:: Server](#setrangemin)|Legt die minimale Position für einen Schieberegler fest.|
|[CSliderCtrl:: setSelection](#setselection)|Legt den Bereich der aktuellen Auswahl fest.|
|[CSliderCtrl:: setthumblength](#setthumblength)|Legt die Länge des Schiebereglers im aktuellen TrackBar-Steuerelement fest.|
|[CSliderCtrl:: SetTic](#settic)|Legt die Position des angegebenen Teil Strichs fest.|
|[CSliderCtrl:: absorcfreq](#setticfreq)|Legt die Häufigkeit von Teil Strichen pro Schieberegler-Steuerelement Inkrement fest.|
|[CSliderCtrl:: Setup Page](#settipside)|Positioniert ein QuickInfo-Steuerelement von einem TrackBar-Steuerelement.|
|[CSliderCtrl:: SetToolTips](#settooltips)|Weist einem Schieberegler-Steuerelement ein ToolTip-Steuerelement zu.|

## <a name="remarks"></a>Bemerkungen

Ein "Schieberegler-Steuerelement" (auch als TrackBar bezeichnet) ist ein Fenster mit einem Schieberegler und optionalen Teil Strichen. Wenn der Benutzer den Schieberegler mit der Maus oder der Richtungs Taste verschiebt, sendet das Steuerelement Benachrichtigungs Meldungen, um die Änderung anzugeben.

Schieberegler-Steuerelemente sind hilfreich, wenn Sie möchten, dass der Benutzer einen diskreten Wert oder einen Satz aufeinander folgender Werte in einem Bereich auswählt. Beispielsweise können Sie ein Schieberegler-Steuerelement verwenden, um dem Benutzer die Möglichkeit zu geben, die Wiederholungsrate der Tastatur festzulegen, indem Sie den Schieberegler auf einen bestimmten Teil Strich verschieben.

Dieses Steuerelement (und damit auch die- `CSliderCtrl` Klasse) ist nur für Programme verfügbar, die unter Windows 95/98 und Windows NT, Version 3,51 und höher, ausgeführt werden.

Der Schieberegler wird in Inkrementen verschoben, die Sie bei der Erstellung angeben. Wenn Sie z. b. angeben, dass der Schieberegler einen Bereich von fünf aufweisen soll, kann der Schieberegler nur sechs Positionen belegen: eine Position auf der linken Seite des Schieberegler-Steuer Elements und eine Position für jedes Inkrement im Bereich. In der Regel wird jede dieser Positionen durch einen Teil Strich identifiziert.

Sie erstellen einen Schieberegler, indem Sie den-Konstruktor und die- `Create` Member-Funktion von verwenden `CSliderCtrl` . Nachdem Sie ein Schieberegler-Steuerelement erstellt haben, können Sie mit Element Funktionen in `CSliderCtrl` viele seiner Eigenschaften ändern. Zu den Änderungen, die Sie vornehmen können, gehören das Festlegen der minimalen und maximalen Positionen für den Schieberegler, das Zeichnen von Teil Strichen, das Festlegen eines Auswahl Bereichs und das Neupositionieren des Schiebereglers

Weitere Informationen zum Verwenden von finden Sie unter Steuer `CSliderCtrl` [Elemente](../../mfc/controls-mfc.md) und [Verwenden von CSliderCtrl](../../mfc/using-csliderctrl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSliderCtrl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcmn.h

## <a name="csliderctrlclearsel"></a><a name="clearsel"></a> CSliderCtrl:: ClearSEL

Löscht die aktuelle Auswahl in einem Schieberegler-Steuerelement.

```cpp
void ClearSel(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parameter

*bredraw*<br/>
Flag neu zeichnen. Wenn dieser Parameter true ist, wird der Schieberegler nach dem Löschen der Auswahl neu gezeichnet. Andernfalls wird der Schieberegler nicht neu gezeichnet.

## <a name="csliderctrlcleartics"></a><a name="cleartics"></a> CSliderCtrl:: ClearTics

Entfernt die aktuellen Teil Striche von einem Schieberegler-Steuerelement.

```cpp
void ClearTics(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parameter

*bredraw*<br/>
Flag neu zeichnen. Wenn dieser Parameter true ist, wird der Schieberegler neu gezeichnet, nachdem die Teil Striche gelöscht wurden. Andernfalls wird der Schieberegler nicht neu gezeichnet.

## <a name="csliderctrlcreate"></a><a name="create"></a> CSliderCtrl:: Create

Erstellt ein Schieberegler-Steuerelement und fügt es an ein- `CSliderCtrl` Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwstyle*<br/>
Gibt den Stil des Schieberegler-Steuer Elements an. Wenden Sie eine beliebige Kombination aus [Schieberegler-Steuerelement Stilen](/windows/win32/Controls/trackbar-control-styles), die im Windows SDK beschrieben werden, auf das Steuerelement

*Rect*<br/>
Gibt die Größe und Position des Schieberegler-Steuer Elements an. Dabei kann es sich entweder um ein [CRect](../../atl-mfc-shared/reference/crect-class.md) -Objekt oder um eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur handeln.

*pparser*<br/>
Gibt das übergeordnete Fenster des Schieberegler-Steuer Elements an, Normal `CDialog` erweise ein Er darf nicht NULL sein.

*nID*<br/>
Gibt die ID des Schieberegler-Steuer Elements an.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn die Initialisierung erfolgreich war. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie erstellen einen `CSliderCtrl` in zwei Schritten. Zuerst wird der-Konstruktor aufgerufen, und dann `Create` wird aufgerufen, wodurch das Schieberegler-Steuerelement erstellt und an das-Objekt angefügt wird `CSliderCtrl` .

Abhängig von den für *dwstyle*festgelegten Werten kann das Schieberegler-Steuerelement entweder vertikal oder horizontal ausgerichtet sein. Es können Teil Striche auf beiden Seiten, beide Seiten oder keines der beiden Seiten vorhanden sein. Sie kann auch verwendet werden, um einen Bereich von aufeinander folgenden Werten anzugeben.

Um erweiterte Fenster Stile auf das Schieberegler-Steuerelement anzuwenden [, aufrufen Sie](#createex) anstelle von den Befehl "" `Create` .

## <a name="csliderctrlcreateex"></a><a name="createex"></a> CSliderCtrl:: kreateex

Erstellt ein-Steuerelement (ein untergeordnetes Fenster) und ordnet es dem- `CSliderCtrl` Objekt zu.

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
Gibt die erweiterte Art des zu erstellenden Steuer Elements an. Eine Liste erweiterter Windows-Stile finden Sie unter dem *dwExStyle* -Parameter für " [kreatewindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) " in der Windows SDK.

*dwstyle*<br/>
Gibt den Stil des Schieberegler-Steuer Elements an. Wenden Sie eine beliebige Kombination aus [Schieberegler-Steuerelement Stilen](/windows/win32/Controls/trackbar-control-styles), die im Windows SDK beschrieben werden, auf das Steuerelement

*Rect*<br/>
Ein Verweis auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur, die die Größe und Position des zu erstellenden Fensters in Client Koordinaten von *pparser*beschreibt.

*pparser*<br/>
Ein Zeiger auf das Fenster, das das übergeordnete Element des Steuer Elements ist.

*nID*<br/>
Die ID des untergeordneten Fensters des Steuer Elements.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Verwenden `CreateEx` Sie anstelle von [Create](#create) , um erweiterte Windows-Stile anzuwenden, die durch den erweiterten Windows-Stil **WS_EX_** angegeben werden.

## <a name="csliderctrlcsliderctrl"></a><a name="csliderctrl"></a> CSliderCtrl:: CSliderCtrl

Erstellt ein `CSliderCtrl`-Objekt.

```
CSliderCtrl();
```

## <a name="csliderctrlgetbuddy"></a><a name="getbuddy"></a> CSliderCtrl:: GetBuddy

Ruft das Handle für ein Fenster des Schieberegler-Steuerelement-Steuer Elements an einem angegebenen Speicherort ab.

```
CWnd* GetBuddy(BOOL fLocation = TRUE) const;
```

### <a name="parameters"></a>Parameter

*fLocation*<br/>
Ein boolescher Wert, der angibt, welcher der beiden zu abzurufenden Buddy-Fenster Handles. Es kann sich um einen der folgenden Werte handeln:

- TRUE Ruft das Handle für den Kumpel auf der linken Seite des Schiebereglers ab. Wenn das Schieberegler-Steuerelement den TBS_VERT Stil verwendet, ruft die Meldung den Kumpel oberhalb des Schiebereglers ab.

- FALSE Ruft das Handle für den Buddy rechts vom Schieberegler ab. Wenn das Schieberegler-Steuerelement den TBS_VERT Stil verwendet, ruft die Nachricht den Kumpel unterhalb des Schiebereglers ab.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CWnd](../../mfc/reference/cwnd-class.md) -Objekt, bei dem es sich um das Buddy-Fenster an der durch *flokation*angegebenen Position handelt, oder NULL, wenn kein Buddy-Fenster an diesem Speicherort vorhanden ist.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TBM_GETBUDDY](/windows/win32/Controls/tbm-getbuddy), wie in der Windows SDK beschrieben. Eine Beschreibung der Stile des Schieberegler-Steuer Elements finden Sie unter [TrackBar-Steuerelement Stile](/windows/win32/Controls/trackbar-control-styles) in der Windows SDK.

## <a name="csliderctrlgetchannelrect"></a><a name="getchannelrect"></a> CSliderCtrl:: GetChannelRect

Ruft die Größe und Position des umgebenden Rechtecks für den Channel eines Schieberegler-Steuer Elements ab.

```cpp
void GetChannelRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Parameter

*LPRC*<br/>
Ein Zeiger auf ein [CRect](../../atl-mfc-shared/reference/crect-class.md) -Objekt, das die Größe und Position des umgebenden Rechtecks des Kanals enthält, wenn die Funktion zurückgibt.

### <a name="remarks"></a>Bemerkungen

Der Kanal ist der Bereich, in dem der Schieberegler verschoben wird und der die Hervorhebung enthält, wenn ein Bereich ausgewählt wird.

## <a name="csliderctrlgetlinesize"></a><a name="getlinesize"></a> CSliderCtrl:: getlinesize

Ruft die Größe der Zeile für ein Schieberegler-Steuerelement ab.

```
int GetLineSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Größe einer Zeile für das Schieberegler-Steuerelement.

### <a name="remarks"></a>Bemerkungen

Die Zeilengröße wirkt sich darauf aus, wie viel der Schieberegler für die TB_LINEUP-und TB_LINEDOWN Benachrichtigungen bewegt wird. Die Standardeinstellung für die Zeilengröße ist 1.

## <a name="csliderctrlgetnumtics"></a><a name="getnumtics"></a> CSliderCtrl:: GetNumTics

Ruft die Anzahl von Teil Strichen in einem Schieberegler-Steuerelement ab.

```
UINT GetNumTics() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Teil Striche im Schieberegler-Steuerelement.

## <a name="csliderctrlgetpagesize"></a><a name="getpagesize"></a> CSliderCtrl:: getpagesize

Ruft die Größe der Seite für ein Schieberegler-Steuerelement ab.

```
int GetPageSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Größe einer Seite für das Schieberegler-Steuerelement.

### <a name="remarks"></a>Bemerkungen

Die Seitengröße wirkt sich darauf aus, wie viel der Schieberegler für die TB_PAGEUP-und TB_PAGEDOWN Benachrichtigungen bewegt wird.

## <a name="csliderctrlgetpos"></a><a name="getpos"></a> CSliderCtrl:: GetPos

Ruft die aktuelle Position des Schiebereglers in einem Schieberegler-Steuerelement ab.

```
int GetPos() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Position.

## <a name="csliderctrlgetrange"></a><a name="getrange"></a> CSliderCtrl:: GetRange

Ruft die maximalen und minimalen Positionen für den Schieberegler in einem Schieberegler-Steuerelement ab.

```cpp
void GetRange(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Parameter

*nmin.*<br/>
Verweis auf eine Ganzzahl, die die minimale Position empfängt.

*nMax*<br/>
Verweis auf eine Ganzzahl, die die maximale Position empfängt.

### <a name="remarks"></a>Bemerkungen

Diese Funktion kopiert die Werte in die ganzen Zahlen, auf die von *nmin* und *nmax*verwiesen wird.

## <a name="csliderctrlgetrangemax"></a><a name="getrangemax"></a> CSliderCtrl:: getrangemax

Ruft die maximale Position für den Schieberegler in einem Schieberegler-Steuerelement ab.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Rückgabewert

Die maximale Position des-Steuer Elements.

## <a name="csliderctrlgetrangemin"></a><a name="getrangemin"></a> CSliderCtrl:: getrangemin

Ruft die minimale Position für den Schieberegler in einem Schieberegler-Steuerelement ab.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Rückgabewert

Die minimale Position des Steuer Elements.

## <a name="csliderctrlgetselection"></a><a name="getselection"></a> CSliderCtrl:: GetSelection

Ruft die Anfangs-und Endpositionen der aktuellen Auswahl in einem Schieberegler-Steuerelement ab.

```cpp
void GetSelection(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Parameter

*nmin.*<br/>
Verweis auf eine Ganzzahl, die die Anfangsposition der aktuellen Auswahl empfängt.

*nMax*<br/>
Verweis auf eine Ganzzahl, die die Endposition der aktuellen Auswahl empfängt.

## <a name="csliderctrlgetthumblength"></a><a name="getthumblength"></a> CSliderCtrl:: getthumblength

Ruft die Länge des Schiebereglers im aktuellen TrackBar-Steuerelement ab.

```
int GetThumbLength() const;
```

### <a name="return-value"></a>Rückgabewert

Die Länge des Schiebereglers in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [TBM_GETTHUMBLENGTH](/windows/win32/Controls/tbm-getthumblength) Nachricht, die in der Windows SDK beschrieben wird.

## <a name="csliderctrlgetthumbrect"></a><a name="getthumbrect"></a> CSliderCtrl:: getthumbrect

Ruft die Größe und Position des umgebenden Rechtecks für den Schieberegler (Thumb) in einem Schieberegler-Steuerelement ab.

```cpp
void GetThumbRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Parameter

*LPRC*<br/>
Ein Zeiger auf ein- `CRect` Objekt, das das umschließende Rechteck für den Schieberegler enthält, wenn die Funktion zurückgegeben wird.

## <a name="csliderctrlgettic"></a><a name="gettic"></a> CSliderCtrl:: GetTic

Ruft die Position eines Teil Strichs in einem Schieberegler-Steuerelement ab.

```
int GetTic(int nTic) const;
```

### <a name="parameters"></a>Parameter

*ntisch*<br/>
NULL basierter Index, der einen Teil Strich identifiziert.

### <a name="return-value"></a>Rückgabewert

Die Position des angegebenen Teil Strichs oder-1, wenn *NTIC* keinen gültigen Index angibt.

## <a name="csliderctrlgetticarray"></a><a name="getticarray"></a> CSliderCtrl:: GetTicArray

Ruft die Adresse des Arrays ab, das die Positionen von Teil Strichen für ein Schieberegler-Steuerelement enthält.

```
DWORD* GetTicArray() const;
```

### <a name="return-value"></a>Rückgabewert

Die Adresse des Arrays, das Teil Strich Positionen für das Schieberegler-Steuerelement enthält.

## <a name="csliderctrlgetticpos"></a><a name="getticpos"></a> CSliderCtrl:: GetTicPos

Ruft die aktuelle physische Position eines Teil Strichs in einem Schieberegler-Steuerelement ab.

```
int GetTicPos(int nTic) const;
```

### <a name="parameters"></a>Parameter

*ntisch*<br/>
NULL basierter Index, der einen Teil Strich identifiziert.

### <a name="return-value"></a>Rückgabewert

Die physische Position des angegebenen Teil Strichs in Client Koordinaten oder-1, wenn *NTIC* keinen gültigen Index angibt.

## <a name="csliderctrlgettooltips"></a><a name="gettooltips"></a> CSliderCtrl:: gettooltips

Ruft das Handle für das QuickInfo-Steuerelement ab, das dem Schieberegler-Steuerelement zugewiesen ist, sofern vorhanden

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) -Objekt oder NULL, wenn Quick Infos nicht verwendet werden. Wenn das Schieberegler-Steuerelement nicht den TBS_TOOLTIPS Stil verwendet, ist der Rückgabewert NULL.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TBM_GETTOOLTIPS](/windows/win32/Controls/tbm-gettooltips), wie in der Windows SDK beschrieben. Beachten Sie, dass diese Member-Funktion `CToolTipCtrl` anstelle eines Handles an ein-Steuerelement ein-Objekt zurückgibt.

Eine Beschreibung der Stile des Schieberegler-Steuer Elements finden Sie unter [TrackBar-Steuerelement Stile](/windows/win32/Controls/trackbar-control-styles) in der Windows SDK.

## <a name="csliderctrlsetbuddy"></a><a name="setbuddy"></a> CSliderCtrl:: SetBuddy

Weist ein Fenster als Buddy-Fenster für ein Schieberegler-Steuerelement zu.

```
CWnd* SetBuddy(
    CWnd* pWndBuddy,
    BOOL fLocation = TRUE);
```

### <a name="parameters"></a>Parameter

*pwndbuddy*<br/>
Ein Zeiger auf ein `CWnd` -Objekt, das als Buddy des Schiebereglers festgelegt wird.

*fLocation*<br/>
-Wert, der die Position angibt, an der das Buddy-Fenster angezeigt werden soll. Die folgenden Werte sind möglich:

- TRUE der Kumpel wird links neben der TrackBar angezeigt, wenn das TrackBar-Steuerelement den TBS_HORZ Stil verwendet. Wenn die TrackBar den TBS_VERT Stil verwendet, wird der Buddy über dem TrackBar-Steuerelement angezeigt.

- FALSE: der Kumpel wird rechts von der TrackBar angezeigt, wenn das TrackBar-Steuerelement den TBS_HORZ Stil verwendet. Wenn die TrackBar das TBS_VERT-Format verwendet, wird der Buddy unterhalb des TrackBar-Steuer Elements angezeigt.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CWnd](../../mfc/reference/cwnd-class.md) -Objekt, das zuvor dem Schieberegler-Steuerelement an dieser Position zugewiesen wurde.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TBM_SETBUDDY](/windows/win32/Controls/tbm-setbuddy), wie in der Windows SDK beschrieben. Beachten Sie, dass diese Member-Funktion Zeiger auf- `CWnd` Objekte und nicht auf Fenster Handles sowohl für den Rückgabewert als auch für den-Parameter verwendet.

Eine Beschreibung der Stile des Schieberegler-Steuer Elements finden Sie unter [TrackBar-Steuerelement Stile](/windows/win32/Controls/trackbar-control-styles) in der Windows SDK.

## <a name="csliderctrlsetlinesize"></a><a name="setlinesize"></a> CSliderCtrl:: setlinesize

Legt die Größe der Linie für ein Schieberegler-Steuerelement fest.

```
int SetLineSize(int nSize);
```

### <a name="parameters"></a>Parameter

*nSize*<br/>
Die neue Zeilengröße des Schieberegler-Steuer Elements.

### <a name="return-value"></a>Rückgabewert

Die vorherige Zeilengröße.

### <a name="remarks"></a>Bemerkungen

Die Zeilengröße wirkt sich darauf aus, wie viel der Schieberegler für die TB_LINEUP-und TB_LINEDOWN Benachrichtigungen bewegt wird.

## <a name="csliderctrlsetpagesize"></a><a name="setpagesize"></a> CSliderCtrl:: setPageSize

Legt die Größe der Seite für ein Schieberegler-Steuerelement fest.

```
int SetPageSize(int nSize);
```

### <a name="parameters"></a>Parameter

*nSize*<br/>
Die neue Seitengröße des Schieberegler-Steuer Elements.

### <a name="return-value"></a>Rückgabewert

Die vorherige Seitengröße.

### <a name="remarks"></a>Bemerkungen

Die Seitengröße wirkt sich darauf aus, wie viel der Schieberegler für die TB_PAGEUP-und TB_PAGEDOWN Benachrichtigungen bewegt wird.

## <a name="csliderctrlsetpos"></a><a name="setpos"></a> CSliderCtrl:: SetPos

Legt die aktuelle Position des Schiebereglers in einem Schieberegler-Steuerelement fest.

```cpp
void SetPos(int nPos);
```

### <a name="parameters"></a>Parameter

*NPOs*<br/>
Gibt die neue Position des Schiebereglers an.

## <a name="csliderctrlsetrange"></a><a name="setrange"></a> CSliderCtrl:: abge

Legt den Bereich (minimale und maximale Position) für den Schieberegler in einem Schieberegler-Steuerelement fest.

```cpp
void SetRange(
    int nMin,
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parameter

*nmin.*<br/>
Minimale Position für den Schieberegler.

*nMax*<br/>
Maximale Position für den Schieberegler.

*bredraw*<br/>
Das neu zeichnen-Flag. Wenn dieser Parameter true ist, wird der Schieberegler nach dem Festlegen des Bereichs neu gezeichnet. Andernfalls wird der Schieberegler nicht neu gezeichnet.

## <a name="csliderctrlsetrangemax"></a><a name="setrangemax"></a> CSliderCtrl:: s-max

Legt den maximalen Bereich für den Schieberegler in einem Schieberegler-Steuerelement fest.

```cpp
void SetRangeMax(
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parameter

*nMax*<br/>
Maximale Position für den Schieberegler.

*bredraw*<br/>
Das neu zeichnen-Flag. Wenn dieser Parameter true ist, wird der Schieberegler nach dem Festlegen des Bereichs neu gezeichnet. Andernfalls wird der Schieberegler nicht neu gezeichnet.

## <a name="csliderctrlsetrangemin"></a><a name="setrangemin"></a> CSliderCtrl:: Server

Legt den minimalen Bereich für den Schieberegler in einem Schieberegler-Steuerelement fest.

```cpp
void SetRangeMin(
    int nMin,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parameter

*nmin.*<br/>
Minimale Position für den Schieberegler.

*bredraw*<br/>
Das neu zeichnen-Flag. Wenn dieser Parameter true ist, wird der Schieberegler nach dem Festlegen des Bereichs neu gezeichnet. Andernfalls wird der Schieberegler nicht neu gezeichnet.

## <a name="csliderctrlsetselection"></a><a name="setselection"></a> CSliderCtrl:: setSelection

Legt die Anfangs-und Endpositionen für die aktuelle Auswahl in einem Schieberegler-Steuerelement fest.

```cpp
void SetSelection(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parameter

*nmin.*<br/>
Die Anfangsposition für den Schieberegler.

*nMax*<br/>
Endposition für den Schieberegler.

## <a name="csliderctrlsetthumblength"></a><a name="setthumblength"></a> CSliderCtrl:: setthumblength

Legt die Länge des Schiebereglers im aktuellen TrackBar-Steuerelement fest.

```cpp
void SetThumbLength(int nLength);
```

### <a name="parameters"></a>Parameter

*nlength*\
in Länge des Schiebereglers in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Methode erfordert, dass das TrackBar-Steuerelement auf [TBS_FIXEDLENGTH](/windows/win32/Controls/trackbar-control-styles) Stil festgelegt wird.

Diese Methode sendet die [TBM_SETTHUMBLENGTH](/windows/win32/Controls/tbm-setthumblength) Nachricht, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die-Variable definiert, die `m_sliderCtrl` für den Zugriff auf das aktuelle TrackBar-Steuerelement verwendet wird. Im Beispiel wird auch eine-Variable definiert, die `thumbLength` zum Speichern der Standardlänge der Thumb-Komponente des TrackBar-Steuer Elements verwendet wird. Diese Variablen werden im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die Thumb-Komponente des TrackBar-Steuer Elements auf die doppelte Standardlänge festgelegt.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]

## <a name="csliderctrlsettic"></a><a name="settic"></a> CSliderCtrl:: SetTic

Legt die Position eines Teil Strichs in einem Schieberegler-Steuerelement fest.

```
BOOL SetTic(int nTic);
```

### <a name="parameters"></a>Parameter

*ntisch*<br/>
Position des Teil Strichs. Dieser Parameter muss einen positiven Wert angeben.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Teil Strich festgelegt ist. andernfalls 0.

## <a name="csliderctrlsetticfreq"></a><a name="setticfreq"></a> CSliderCtrl:: absorcfreq

Legt die Häufigkeit fest, mit der Teil Striche in einem Schieberegler angezeigt werden.

```cpp
void SetTicFreq(int nFreq);
```

### <a name="parameters"></a>Parameter

*nfreq*<br/>
Häufigkeit der Teil Striche.

### <a name="remarks"></a>Bemerkungen

Wenn die Häufigkeit beispielsweise auf 2 festgelegt ist, wird für jedes andere Inkrement im Gültigkeitsbereich des Schiebereglers ein Teil Strich angezeigt. Die Standardeinstellung für die Häufigkeit ist 1 (d. h., jedes Inkrement im Bereich ist einem Teil Strich zugeordnet).

Sie müssen das-Steuerelement mit dem TBS_AUTOTICKS-Stil erstellen, um diese Funktion zu verwenden. Weitere Informationen finden Sie unter [CSliderCtrl:: Create](#create).

## <a name="csliderctrlsettipside"></a><a name="settipside"></a> CSliderCtrl:: Setup Page

Positioniert ein QuickInfo-Steuerelement von einem TrackBar-Steuerelement.

```
int SetTipSide(int nLocation);
```

### <a name="parameters"></a>Parameter

*nspeicherort*<br/>
Wert, der die Position darstellt, an der das QuickInfo-Steuerelement angezeigt werden soll Eine Liste möglicher Werte finden Sie in der Win32-Meldung [TBM_SETTIPSIDE](/windows/win32/Controls/tbm-settipside), wie in der Windows SDK beschrieben.

### <a name="return-value"></a>Rückgabewert

Ein-Wert, der die vorherige Position des QuickInfo-Steuer Elements darstellt. Der Rückgabewert ist mit einem der möglichen Werte für *nlocation*.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht TBM_SETTIPSIDE, wie in der Windows SDK beschrieben. Schieberegler-Steuerelemente, die den TBS_TOOLTIPS Stil Anzeige Quick Infos verwenden. Eine Beschreibung der Stile des Schieberegler-Steuer Elements finden Sie unter [TrackBar-Steuerelement Stile](/windows/win32/Controls/trackbar-control-styles) in der Windows SDK.

## <a name="csliderctrlsettooltips"></a><a name="settooltips"></a> CSliderCtrl:: SetToolTips

Weist einem Schieberegler-Steuerelement ein ToolTip-Steuerelement zu.

```cpp
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parameter

*pwndtip*<br/>
Ein Zeiger auf ein [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) -Objekt, das die Quick Infos enthält, die mit dem Schieberegler-Steuerelement verwendet werden.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TBM_SETTOOLTIPS](/windows/win32/Controls/tbm-settooltips), wie in der Windows SDK beschrieben. Wenn ein Schieberegler-Steuerelement mit dem TBS_TOOLTIPS Stil erstellt wird, wird ein Standardmäßiges QuickInfo-Steuerelement erstellt, das neben dem Schieberegler angezeigt wird und die aktuelle Position des Schiebereglers anzeigt Eine Beschreibung der Stile des Schieberegler-Steuer Elements finden Sie unter [TrackBar-Steuerelement Stile](/windows/win32/Controls/trackbar-control-styles) in der Windows SDK.

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CProgressCtrl-Klasse](../../mfc/reference/cprogressctrl-class.md)
