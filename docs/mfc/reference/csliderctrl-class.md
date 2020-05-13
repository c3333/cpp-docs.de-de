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
ms.openlocfilehash: 2e3572b34f930bb6a7d99b437c01c8aaf970e6c3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751273"
---
# <a name="csliderctrl-class"></a>CSliderCtrl-Klasse

Stellt die Funktionalität des allgemeinen Windows-Schieberegler-Steuerelements bereit.

## <a name="syntax"></a>Syntax

```
class CSliderCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSliderCtrl::CSliderCtrl](#csliderctrl)|Erstellt ein `CSliderCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSliderCtrl::ClearSel](#clearsel)|Löscht die aktuelle Auswahl in einem Schieberegler-Steuerelement.|
|[CSliderCtrl::ClearTics](#cleartics)|Entfernt die aktuellen Teilstriche aus einem Schieberegler-Steuerelement.|
|[CSliderCtrl::Erstellen](#create)|Erstellt ein Schiebereglersteuerelement und `CSliderCtrl` fügt es an ein Objekt an.|
|[CSliderCtrl::CreateEx](#createex)|Erstellt ein Schiebereglersteuerelement mit den angegebenen erweiterten `CSliderCtrl` Windows-Stilen und fügt es an ein Objekt an.|
|[CSliderCtrl::GetBuddy](#getbuddy)|Ruft das Handle zu einem Schieberegler-Steuerelement-Buddy-Fenster an einer bestimmten Position ab.|
|[CSliderCtrl::GetChannelRect](#getchannelrect)|Ruft die Größe des Kanals des Schiebereglersteuerelements ab.|
|[CSliderCtrl::GetLineSize](#getlinesize)|Ruft die Zeilengröße eines Schiebereglersteuerelements ab.|
|[CSliderCtrl::GetNumTics](#getnumtics)|Ruft die Anzahl der Teilstriche in einem Schieberegler-Steuerelement ab.|
|[CSliderCtrl::GetPageSize](#getpagesize)|Ruft die Seitengröße eines Schiebereglersteuerelements ab.|
|[CSliderCtrl::GetPos](#getpos)|Ruft die aktuelle Position des Schiebereglers ab.|
|[CSliderCtrl::GetRange](#getrange)|Ruft die minimalen und maximalen Positionen für einen Schieberegler ab.|
|[CSliderCtrl::GetRangeMax](#getrangemax)|Ruft die maximale Position für einen Schieberegler ab.|
|[CSliderCtrl::GetRangeMin](#getrangemin)|Ruft die Mindestposition für einen Schieberegler ab.|
|[CSliderCtrl::GetSelection](#getselection)|Ruft den Bereich der aktuellen Auswahl ab.|
|[CSliderCtrl::GetThumbLength](#getthumblength)|Ruft die Länge des Schiebereglers im aktuellen Spurleistensteuerelement ab.|
|[CSliderCtrl::GetThumbRect](#getthumbrect)|Ruft die Größe des Daumens des Schiebereglersteuerelements ab.|
|[CSliderCtrl::GetTic](#gettic)|Ruft die Position des angegebenen Häkchens zeichen ab.|
|[CSliderCtrl::GetTicArray](#getticarray)|Ruft das Array von Teilstrichpositionen für ein Schiebereglersteuerelement ab.|
|[CSliderCtrl::GetTicPos](#getticpos)|Ruft die Position des angegebenen Teilstrichs in Clientkoordinaten ab.|
|[CSliderCtrl::GetToolTipps](#gettooltips)|Ruft das Handle für das QuickInfo-Steuerelement ab, das dem Schieberegler-Steuerelement zugewiesen ist, falls vorhanden.|
|[CSliderCtrl::SetBuddy](#setbuddy)|Weist ein Fenster als Buddy-Fenster für ein Schieberegler-Steuerelement zu.|
|[CSliderCtrl::SetLineSize](#setlinesize)|Legt die Liniengröße eines Schiebereglersteuerelements fest.|
|[CSliderCtrl::SetPageSize](#setpagesize)|Legt die Seitengröße eines Schiebereglersteuerelements fest.|
|[CSliderCtrl::SetPos](#setpos)|Legt die aktuelle Position des Schiebereglers fest.|
|[CSliderCtrl::SetRange](#setrange)|Legt die minimalen und maximalen Positionen für einen Schieberegler fest.|
|[CSliderCtrl::SetRangeMax](#setrangemax)|Legt die maximale Position für einen Schieberegler fest.|
|[CSliderCtrl::SetRangeMin](#setrangemin)|Legt die Mindestposition für einen Schieberegler fest.|
|[CSliderCtrl::SetSelection](#setselection)|Legt den Bereich der aktuellen Auswahl fest.|
|[CSliderCtrl::SetThumbLength](#setthumblength)|Legt die Länge des Schiebereglers im aktuellen Spurleistensteuerelement fest.|
|[CSliderCtrl::SetTic](#settic)|Legt die Position des angegebenen Häkchens zeichen fest.|
|[CSliderCtrl::SetTicFreq](#setticfreq)|Legt die Häufigkeit von Teilstrichen pro Schieberegler-Steuerschrittinkrement fest.|
|[CSliderCtrl::SetTipSide](#settipside)|Positioniert ein QuickInfo-Steuerelement, das von einem Spurleistensteuerelement verwendet wird.|
|[CSliderCtrl::SetToolTips](#settooltips)|Weist einem Schiebereglersteuerelement ein QuickInfo-Steuerelement zu.|

## <a name="remarks"></a>Bemerkungen

Ein "Schieberegler" (auch als Trackbar bezeichnet) ist ein Fenster mit einem Schieberegler und optionalen Teilstrichen. Wenn der Benutzer den Schieberegler mit der Maus oder den Richtungstasten bewegt, sendet das Steuerelement Benachrichtigungen, um die Änderung anzuzeigen.

Schiebereglersteuerelemente sind nützlich, wenn der Benutzer einen diskreten Wert oder einen Satz aufeinander folgender Werte in einem Bereich auswählen soll. Sie können z. B. ein Schieberegler-Steuerelement verwenden, um dem Benutzer zu ermöglichen, die Wiederholungsrate der Tastatur festzulegen, indem Sie den Schieberegler auf ein bestimmtes Häkchen verschieben.

Dieses Steuerelement (und `CSliderCtrl` damit die Klasse) ist nur für Programme verfügbar, die unter Windows 95/98 und Windows NT Version 3.51 und höher ausgeführt werden.

Der Schieberegler wird in Schritten verschoben, die Sie beim Erstellen angeben. Wenn Sie z. B. angeben, dass der Schieberegler einen Bereich von fünf haben soll, kann der Schieberegler nur sechs Positionen einnehmen: eine Position auf der linken Seite des Schiebereglers und eine Position für jedes Inkrement im Bereich. In der Regel wird jede dieser Positionen durch ein Häkchen gekennzeichnet.

Sie erstellen einen Schieberegler mithilfe `Create` des `CSliderCtrl`Konstruktors und der Memberfunktion von . Nachdem Sie ein Schiebereglersteuerelement erstellt haben, können Sie Memberfunktionen in `CSliderCtrl` verwenden, um viele seiner Eigenschaften zu ändern. Zu den Änderungen, die Sie vornehmen können, gehören das Festlegen der minimalen und maximalen Positionen für den Schieberegler, das Zeichnen von Teilstrichen, das Festlegen eines Auswahlbereichs und das Neupositionieren des Schiebereglers.

Weitere Informationen zur `CSliderCtrl`Verwendung finden Sie unter [Steuerelemente](../../mfc/controls-mfc.md) und [Verwenden von CSliderCtrl](../../mfc/using-csliderctrl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSliderCtrl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcmn.h

## <a name="csliderctrlclearsel"></a><a name="clearsel"></a>CSliderCtrl::ClearSel

Löscht die aktuelle Auswahl in einem Schieberegler-Steuerelement.

```cpp
void ClearSel(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parameter

*bZeichnung*<br/>
Zeichnen Sie die Flagge neu. Wenn dieser Parameter TRUE ist, wird der Schieberegler neu gezeichnet, nachdem die Auswahl gelöscht wurde. Andernfalls wird der Schieberegler nicht neu gezeichnet.

## <a name="csliderctrlcleartics"></a><a name="cleartics"></a>CSliderCtrl::ClearTics

Entfernt die aktuellen Teilstriche aus einem Schieberegler-Steuerelement.

```cpp
void ClearTics(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parameter

*bZeichnung*<br/>
Zeichnen Sie die Flagge neu. Wenn dieser Parameter TRUE ist, wird der Schieberegler neu gezeichnet, nachdem die Teilstriche gelöscht wurden. Andernfalls wird der Schieberegler nicht neu gezeichnet.

## <a name="csliderctrlcreate"></a><a name="create"></a>CSliderCtrl::Erstellen

Erstellt ein Schiebereglersteuerelement und `CSliderCtrl` fügt es an ein Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Gibt den Stil des Schiebereglersteuerelements an. Wenden Sie eine beliebige Kombination von [Schiebereglersteuerelementstilen](/windows/win32/Controls/trackbar-control-styles), die im Windows SDK beschrieben werden, auf das Steuerelement an.

*Rect*<br/>
Gibt die Größe und Position des Schiebereglersteuerelements an. Dabei kann es sich entweder um ein [CRect-Objekt](../../atl-mfc-shared/reference/crect-class.md) oder eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) handelt.

*pParentWnd*<br/>
Gibt das übergeordnete Fenster des Schiebereglersteuerelements an, in der Regel eine `CDialog`. Es darf nicht NULL sein.

*nID*<br/>
Gibt die ID des Schiebereglersteuerelements an.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Initialisierung erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CSliderCtrl` eine in zwei Schritten. Rufen Sie zuerst den Konstruktor `Create`auf, und rufen Sie dann `CSliderCtrl` auf, das das Schiebereglersteuerelement erstellt und an das Objekt anfügt.

Abhängig von den für *dwStyle*festgelegten Werten kann das Schiebereglersteuerelement entweder eine vertikale oder horizontale Ausrichtung aufweisen. Es kann Zeckenzeichen auf beiden Seiten haben, auf beiden Seiten, oder keine. Es kann auch verwendet werden, um einen Bereich von aufeinander folgenden Werten anzugeben.

Um erweiterte Fensterstile auf das Schiebereglersteuerelement `Create`anzuwenden, rufen Sie [CreateEx](#createex) anstelle von auf.

## <a name="csliderctrlcreateex"></a><a name="createex"></a>CSliderCtrl::CreateEx

Erstellt ein Steuerelement (ein untergeordnetes Fenster) und ordnet es dem `CSliderCtrl` Objekt zu.

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
Gibt den Stil des Schiebereglersteuerelements an. Wenden Sie eine beliebige Kombination von [Schiebereglersteuerelementstilen](/windows/win32/Controls/trackbar-control-styles), die im Windows SDK beschrieben werden, auf das Steuerelement an.

*Rect*<br/>
Ein Verweis auf eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die die Größe und Position des zu erstellenden Fensters in den Clientkoordinaten von *pParentWnd*beschreibt.

*pParentWnd*<br/>
Ein Zeiger auf das Fenster, das das übergeordnete Steuerelement ist.

*nID*<br/>
Die untergeordnete Fenster-ID des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Verwenden `CreateEx` Sie anstelle von [Erstellen,](#create) um erweiterte Windows-Formatvorlagen anzuwenden, die durch das Erweiterte Windows-Stilvorwort **WS_EX_** angegeben werden.

## <a name="csliderctrlcsliderctrl"></a><a name="csliderctrl"></a>CSliderCtrl::CSliderCtrl

Erstellt ein `CSliderCtrl`-Objekt.

```
CSliderCtrl();
```

## <a name="csliderctrlgetbuddy"></a><a name="getbuddy"></a>CSliderCtrl::GetBuddy

Ruft das Handle zu einem Schieberegler-Steuerelement-Buddy-Fenster an einer bestimmten Position ab.

```
CWnd* GetBuddy(BOOL fLocation = TRUE) const;
```

### <a name="parameters"></a>Parameter

*fLocation*<br/>
Ein boolescher Wert, der angibt, welche der beiden Buddy-Fenster-Handles abgerufen werden sollen. Es kann sich um einen der folgenden Werte handeln:

- TRUE Ruft das Handle an den Buddy links neben dem Schieberegler ab. Wenn das Schiebereglersteuerelement den TBS_VERT-Stil verwendet, ruft die Nachricht den Buddy über dem Schieberegler ab.

- FALSE Ruft das Handle an den Buddy rechts neben dem Schieberegler ab. Wenn das Schiebereglersteuerelement den TBS_VERT-Stil verwendet, ruft die Nachricht den Buddy unter dem Schieberegler ab.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CWnd-Objekt,](../../mfc/reference/cwnd-class.md) das das Buddy-Fenster an der von *fLocation*angegebenen Position oder NULL ist, wenn an dieser Position kein Buddy-Fenster vorhanden ist.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [TBM_GETBUDDY](/windows/win32/Controls/tbm-getbuddy)Win32-TBM_GETBUDDY , wie im Windows SDK beschrieben. Eine Beschreibung der Schiebereglersteuerungsstile finden Sie unter [Spurleistensteuerungsstile](/windows/win32/Controls/trackbar-control-styles) im Windows SDK.

## <a name="csliderctrlgetchannelrect"></a><a name="getchannelrect"></a>CSliderCtrl::GetChannelRect

Ruft die Größe und Position des umgrenzenden Rechtecks für den Kanal eines Schiebereglersteuerelements ab.

```cpp
void GetChannelRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Parameter

*lprc*<br/>
Ein Zeiger auf ein [CRect-Objekt,](../../atl-mfc-shared/reference/crect-class.md) das die Größe und Position des umgrenzten Rechtecks des Kanals enthält, wenn die Funktion zurückkehrt.

### <a name="remarks"></a>Bemerkungen

Der Kanal ist der Bereich, über den sich der Schieberegler bewegt und der die Hervorhebung enthält, wenn ein Bereich ausgewählt wird.

## <a name="csliderctrlgetlinesize"></a><a name="getlinesize"></a>CSliderCtrl::GetLineSize

Ruft die Größe der Linie für ein Schiebereglersteuerelement ab.

```
int GetLineSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Größe einer Linie für das Schiebereglersteuerelement.

### <a name="remarks"></a>Bemerkungen

Die Liniengröße wirkt sich darauf aus, wie stark sich der Schieberegler für die TB_LINEUP und TB_LINEDOWN Benachrichtigungen bewegt. Die Standardeinstellung für die Zeilengröße ist 1.

## <a name="csliderctrlgetnumtics"></a><a name="getnumtics"></a>CSliderCtrl::GetNumTics

Ruft die Anzahl der Teilstriche in einem Schieberegler-Steuerelement ab.

```
UINT GetNumTics() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Teilstriche im Schieberegler-Steuerelement.

## <a name="csliderctrlgetpagesize"></a><a name="getpagesize"></a>CSliderCtrl::GetPageSize

Ruft die Größe der Seite für ein Schiebereglersteuerelement ab.

```
int GetPageSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Größe einer Seite für das Schiebereglersteuerelement.

### <a name="remarks"></a>Bemerkungen

Die Seitengröße wirkt sich darauf aus, wie stark sich der Schieberegler für die TB_PAGEUP und TB_PAGEDOWN Benachrichtigungen bewegt.

## <a name="csliderctrlgetpos"></a><a name="getpos"></a>CSliderCtrl::GetPos

Ruft die aktuelle Position des Schiebereglers in einem Schieberegler-Steuerelement ab.

```
int GetPos() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Position.

## <a name="csliderctrlgetrange"></a><a name="getrange"></a>CSliderCtrl::GetRange

Ruft die maximalen und minimalen Positionen für den Schieberegler in einem Schieberegler-Steuerelement ab.

```cpp
void GetRange(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Parameter

*Nmin*<br/>
Verweis auf eine ganze Zahl, die die Mindestposition empfängt.

*nMax*<br/>
Verweis auf eine ganze Zahl, die die maximale Position empfängt.

### <a name="remarks"></a>Bemerkungen

Diese Funktion kopiert die Werte in die ganzen Zahlen, auf die *nMin* und *nMax*verweisen.

## <a name="csliderctrlgetrangemax"></a><a name="getrangemax"></a>CSliderCtrl::GetRangeMax

Ruft die maximale Position für den Schieberegler in einem Schieberegler-Steuerelement ab.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Rückgabewert

Die maximale Position des Steuerelements.

## <a name="csliderctrlgetrangemin"></a><a name="getrangemin"></a>CSliderCtrl::GetRangeMin

Ruft die Mindestposition für den Schieberegler in einem Schieberegler-Steuerelement ab.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Rückgabewert

Die Mindestposition des Steuerelements.

## <a name="csliderctrlgetselection"></a><a name="getselection"></a>CSliderCtrl::GetSelection

Ruft die Start- und Endpositionen der aktuellen Auswahl in einem Schieberegler-Steuerelement ab.

```cpp
void GetSelection(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Parameter

*Nmin*<br/>
Verweis auf eine ganze Zahl, die die Startposition der aktuellen Auswahl empfängt.

*nMax*<br/>
Verweis auf eine ganze Zahl, die die Endposition der aktuellen Auswahl empfängt.

## <a name="csliderctrlgetthumblength"></a><a name="getthumblength"></a>CSliderCtrl::GetThumbLength

Ruft die Länge des Schiebereglers im aktuellen Spurleistensteuerelement ab.

```
int GetThumbLength() const;
```

### <a name="return-value"></a>Rückgabewert

Die Länge des Schiebereglers in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [TBM_GETTHUMBLENGTH](/windows/win32/Controls/tbm-getthumblength) Nachricht, die im Windows SDK beschrieben wird.

## <a name="csliderctrlgetthumbrect"></a><a name="getthumbrect"></a>CSliderCtrl::GetThumbRect

Ruft die Größe und Position des umgrenzenden Rechtecks für den Schieberegler (Daumen) in einem Schieberegler-Steuerelement ab.

```cpp
void GetThumbRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Parameter

*lprc*<br/>
Ein Zeiger auf `CRect` ein Objekt, das das umgrenzende Rechteck für den Schieberegler enthält, wenn die Funktion zurückkehrt.

## <a name="csliderctrlgettic"></a><a name="gettic"></a>CSliderCtrl::GetTic

Ruft die Position eines Teilstrichs in einem Schieberegler-Steuerelement ab.

```
int GetTic(int nTic) const;
```

### <a name="parameters"></a>Parameter

*nTic*<br/>
Nullbasierter Index, der ein Teilstrich identifiziert.

### <a name="return-value"></a>Rückgabewert

Die Position des angegebenen Häkchens oder - 1, wenn *nTic* keinen gültigen Index angibt.

## <a name="csliderctrlgetticarray"></a><a name="getticarray"></a>CSliderCtrl::GetTicArray

Ruft die Adresse des Arrays ab, das die Positionen von Teilstrichen für ein Schiebereglersteuerelement enthält.

```
DWORD* GetTicArray() const;
```

### <a name="return-value"></a>Rückgabewert

Die Adresse des Arrays, das Tick-Mark-Positionen für das Schiebereglersteuerelement enthält.

## <a name="csliderctrlgetticpos"></a><a name="getticpos"></a>CSliderCtrl::GetTicPos

Ruft die aktuelle physische Position eines Teilstrichs in einem Schieberegler-Steuerelement ab.

```
int GetTicPos(int nTic) const;
```

### <a name="parameters"></a>Parameter

*nTic*<br/>
Nullbasierter Index, der ein Teilstrich identifiziert.

### <a name="return-value"></a>Rückgabewert

Die physische Position in Client-Koordinaten des angegebenen Teilstrichs oder - 1, wenn *nTic* keinen gültigen Index angibt.

## <a name="csliderctrlgettooltips"></a><a name="gettooltips"></a>CSliderCtrl::GetToolTipps

Ruft das Handle für das QuickInfo-Steuerelement ab, das dem Schieberegler-Steuerelement zugewiesen ist, falls vorhanden.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CToolTipCtrl-Objekt](../../mfc/reference/ctooltipctrl-class.md) oder NULL, wenn QuickInfos nicht verwendet werden. Wenn das Schiebereglersteuerelement den Stil TBS_TOOLTIPS nicht verwendet, lautet der Rückgabewert NULL.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [TBM_GETTOOLTIPS](/windows/win32/Controls/tbm-gettooltips)Win32-TBM_GETTOOLTIPS , wie im Windows SDK beschrieben. Beachten Sie, dass `CToolTipCtrl` diese Memberfunktion ein Objekt anstelle eines Handles an ein Steuerelement zurückgibt.

Eine Beschreibung der Schiebereglersteuerungsstile finden Sie unter [Spurleistensteuerungsstile](/windows/win32/Controls/trackbar-control-styles) im Windows SDK.

## <a name="csliderctrlsetbuddy"></a><a name="setbuddy"></a>CSliderCtrl::SetBuddy

Weist ein Fenster als Buddy-Fenster für ein Schieberegler-Steuerelement zu.

```
CWnd* SetBuddy(
    CWnd* pWndBuddy,
    BOOL fLocation = TRUE);
```

### <a name="parameters"></a>Parameter

*pWndBuddy*<br/>
Ein Zeiger auf `CWnd` ein Objekt, das als Buddy des Schiebereglersteuerelements festgelegt wird.

*fLocation*<br/>
Wert, der die Position angibt, an der das Buddy-Fenster angezeigt werden soll. Die folgenden Werte sind möglich:

- TRUE Der Buddy wird links neben der Spurleiste angezeigt, wenn das Trackbar-Steuerelement den stil TBS_HORZ verwendet. Wenn die Trackbar den TBS_VERT-Stil verwendet, wird der Buddy über dem Spurleistensteuerelement angezeigt.

- FALSE Der Buddy wird rechts neben der Spurleiste angezeigt, wenn das Trackbar-Steuerelement den TBS_HORZ-Stil verwendet. Wenn die Spurleiste den TBS_VERT-Stil verwendet, wird der Buddy unter dem Spurleistensteuerelement angezeigt.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CWnd-Objekt,](../../mfc/reference/cwnd-class.md) das zuvor dem Schiebereglersteuerelement an dieser Position zugewiesen wurde.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [TBM_SETBUDDY](/windows/win32/Controls/tbm-setbuddy)Win32-TBM_SETBUDDY , wie im Windows SDK beschrieben. Beachten Sie, dass diese Memberfunktion Zeiger auf `CWnd` Objekte anstelle von Fensterhandles für den Rückgabewert und den Parameter verwendet.

Eine Beschreibung der Schiebereglersteuerungsstile finden Sie unter [Spurleistensteuerungsstile](/windows/win32/Controls/trackbar-control-styles) im Windows SDK.

## <a name="csliderctrlsetlinesize"></a><a name="setlinesize"></a>CSliderCtrl::SetLineSize

Legt die Größe der Linie für ein Schiebereglersteuerelement fest.

```
int SetLineSize(int nSize);
```

### <a name="parameters"></a>Parameter

*nGröße*<br/>
Die neue Liniengröße des Schiebereglersteuerelements.

### <a name="return-value"></a>Rückgabewert

Die vorherige Zeilengröße.

### <a name="remarks"></a>Bemerkungen

Die Liniengröße wirkt sich darauf aus, wie stark sich der Schieberegler für die TB_LINEUP und TB_LINEDOWN Benachrichtigungen bewegt.

## <a name="csliderctrlsetpagesize"></a><a name="setpagesize"></a>CSliderCtrl::SetPageSize

Legt die Größe der Seite für ein Schiebereglersteuerelement fest.

```
int SetPageSize(int nSize);
```

### <a name="parameters"></a>Parameter

*nGröße*<br/>
Die neue Seitengröße des Schiebereglersteuerelements.

### <a name="return-value"></a>Rückgabewert

Die vorherige Seitengröße.

### <a name="remarks"></a>Bemerkungen

Die Seitengröße wirkt sich darauf aus, wie stark sich der Schieberegler für die TB_PAGEUP und TB_PAGEDOWN Benachrichtigungen bewegt.

## <a name="csliderctrlsetpos"></a><a name="setpos"></a>CSliderCtrl::SetPos

Legt die aktuelle Position des Schiebereglers in einem Schiebereglerfest fest.

```cpp
void SetPos(int nPos);
```

### <a name="parameters"></a>Parameter

*Npos*<br/>
Gibt die neue Schiebereglerposition an.

## <a name="csliderctrlsetrange"></a><a name="setrange"></a>CSliderCtrl::SetRange

Legt den Bereich (minimale und maximale Positionen) für den Schieberegler in einem Schiebereglerfest fest.

```cpp
void SetRange(
    int nMin,
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parameter

*Nmin*<br/>
Minimale Position für den Schieberegler.

*nMax*<br/>
Maximale Position für den Schieberegler.

*bZeichnung*<br/>
Das Neuzeichnungsflag. Wenn dieser Parameter TRUE ist, wird der Schieberegler neu gezeichnet, nachdem der Bereich festgelegt wurde. Andernfalls wird der Schieberegler nicht neu gezeichnet.

## <a name="csliderctrlsetrangemax"></a><a name="setrangemax"></a>CSliderCtrl::SetRangeMax

Legt den maximalen Bereich für den Schieberegler in einem Schieberegler-Steuerelement fest.

```cpp
void SetRangeMax(
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parameter

*nMax*<br/>
Maximale Position für den Schieberegler.

*bZeichnung*<br/>
Das Neuzeichnungsflag. Wenn dieser Parameter TRUE ist, wird der Schieberegler neu gezeichnet, nachdem der Bereich festgelegt wurde. Andernfalls wird der Schieberegler nicht neu gezeichnet.

## <a name="csliderctrlsetrangemin"></a><a name="setrangemin"></a>CSliderCtrl::SetRangeMin

Legt den Minimalbereich für den Schieberegler in einem Schiebereglerfest fest.

```cpp
void SetRangeMin(
    int nMin,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parameter

*Nmin*<br/>
Minimale Position für den Schieberegler.

*bZeichnung*<br/>
Das Neuzeichnungsflag. Wenn dieser Parameter TRUE ist, wird der Schieberegler neu gezeichnet, nachdem der Bereich festgelegt wurde. Andernfalls wird der Schieberegler nicht neu gezeichnet.

## <a name="csliderctrlsetselection"></a><a name="setselection"></a>CSliderCtrl::SetSelection

Legt die Start- und Endpositionen für die aktuelle Auswahl in einem Schieberegler-Steuerelement fest.

```cpp
void SetSelection(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parameter

*Nmin*<br/>
Startposition für den Schieberegler.

*nMax*<br/>
Endposition für den Schieberegler.

## <a name="csliderctrlsetthumblength"></a><a name="setthumblength"></a>CSliderCtrl::SetThumbLength

Legt die Länge des Schiebereglers im aktuellen Spurleistensteuerelement fest.

```cpp
void SetThumbLength(int nLength);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*nLänge*|[in] Länge des Schiebereglers in Pixel.|

### <a name="remarks"></a>Bemerkungen

Diese Methode erfordert, dass das Spurleistensteuerelement auf [TBS_FIXEDLENGTH](/windows/win32/Controls/trackbar-control-styles) Stil festgelegt wird.

Diese Methode sendet die [TBM_SETTHUMBLENGTH](/windows/win32/Controls/tbm-setthumblength) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird `m_sliderCtrl`die Variable , definiert, die für den Zugriff auf das aktuelle Spurleistensteuerelement verwendet wird. Im Beispiel wird auch `thumbLength`eine Variable definiert, , die zum Speichern der Standardlänge der Daumenkomponente des Spurleistensteuerelements verwendet wird. Diese Variablen werden im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die Daumenkomponente des Spurleistensteuerelements auf die doppelte Standardlänge festgelegt.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]

## <a name="csliderctrlsettic"></a><a name="settic"></a>CSliderCtrl::SetTic

Legt die Position eines Teilstrichs in einem Schieberegler-Steuerelement fest.

```
BOOL SetTic(int nTic);
```

### <a name="parameters"></a>Parameter

*nTic*<br/>
Position des Häkchens. Dieser Parameter muss einen positiven Wert angeben.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Häkchen gesetzt ist; andernfalls 0.

## <a name="csliderctrlsetticfreq"></a><a name="setticfreq"></a>CSliderCtrl::SetTicFreq

Legt die Häufigkeit fest, mit der Teilstriche in einem Schieberegler angezeigt werden.

```cpp
void SetTicFreq(int nFreq);
```

### <a name="parameters"></a>Parameter

*nFreq*<br/>
Häufigkeit der Teilstriche.

### <a name="remarks"></a>Bemerkungen

Wenn die Frequenz beispielsweise auf 2 eingestellt ist, wird für jedes zweite Inkrement im Bereich des Schiebereglers ein Häkchen angezeigt. Die Standardeinstellung für die Frequenz ist 1 (d. h., jedes Inkrement im Bereich ist mit einem Häkchen verknüpft).

Sie müssen das Steuerelement mit dem TBS_AUTOTICKS-Stil erstellen, um diese Funktion verwenden zu können. Weitere Informationen finden Sie unter [CSliderCtrl::Create](#create).

## <a name="csliderctrlsettipside"></a><a name="settipside"></a>CSliderCtrl::SetTipSide

Positioniert ein QuickInfo-Steuerelement, das von einem Spurleistensteuerelement verwendet wird.

```
int SetTipSide(int nLocation);
```

### <a name="parameters"></a>Parameter

*nLocation*<br/>
Wert, der die Position darstellt, an der das QuickInfo-Steuerelement angezeigt werden soll. Eine Liste möglicher Werte finden Sie in [TBM_SETTIPSIDE](/windows/win32/Controls/tbm-settipside)der Win32-TBM_SETTIPSIDE , wie im Windows SDK beschrieben.

### <a name="return-value"></a>Rückgabewert

Ein Wert, der die vorherige Position des QuickInfo-Steuerelements darstellt. Der Rückgabewert entspricht einem der möglichen Werte für *nLocation*.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-TBM_SETTIPSIDE, wie im Windows SDK beschrieben. Schiebereglersteuerelemente, die die TBS_TOOLTIPS Stilanzeige-Quickinfos verwenden. Eine Beschreibung der Schiebereglersteuerungsstile finden Sie unter [Spurleistensteuerungsstile](/windows/win32/Controls/trackbar-control-styles) im Windows SDK.

## <a name="csliderctrlsettooltips"></a><a name="settooltips"></a>CSliderCtrl::SetToolTips

Weist einem Schiebereglersteuerelement ein QuickInfo-Steuerelement zu.

```cpp
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parameter

*pWndTip*<br/>
Ein Zeiger auf ein [CToolTipCtrl-Objekt,](../../mfc/reference/ctooltipctrl-class.md) das die QuickInfos enthält, die mit dem Schieberegler-Steuerelement verwendet werden sollen.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Nachricht [TBM_SETTOOLTIPS](/windows/win32/Controls/tbm-settooltips), wie im Windows SDK beschrieben. Wenn ein Schiebereglersteuerelement mit dem stil TBS_TOOLTIPS erstellt wird, wird ein Standard-Quickinfo-Steuerelement erstellt, das neben dem Schieberegler angezeigt wird und die aktuelle Position des Schiebereglers anzeigt. Eine Beschreibung der Schiebereglersteuerungsstile finden Sie unter [Spurleistensteuerungsstile](/windows/win32/Controls/trackbar-control-styles) im Windows SDK.

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CProgressCtrl-Klasse](../../mfc/reference/cprogressctrl-class.md)
