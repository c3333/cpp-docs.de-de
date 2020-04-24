---
title: CSpinButtonCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::Create
- AFXCMN/CSpinButtonCtrl::CreateEx
- AFXCMN/CSpinButtonCtrl::GetAccel
- AFXCMN/CSpinButtonCtrl::GetBase
- AFXCMN/CSpinButtonCtrl::GetBuddy
- AFXCMN/CSpinButtonCtrl::GetPos
- AFXCMN/CSpinButtonCtrl::GetRange
- AFXCMN/CSpinButtonCtrl::SetAccel
- AFXCMN/CSpinButtonCtrl::SetBase
- AFXCMN/CSpinButtonCtrl::SetBuddy
- AFXCMN/CSpinButtonCtrl::SetPos
- AFXCMN/CSpinButtonCtrl::SetRange
helpviewer_keywords:
- CSpinButtonCtrl [MFC], CSpinButtonCtrl
- CSpinButtonCtrl [MFC], Create
- CSpinButtonCtrl [MFC], CreateEx
- CSpinButtonCtrl [MFC], GetAccel
- CSpinButtonCtrl [MFC], GetBase
- CSpinButtonCtrl [MFC], GetBuddy
- CSpinButtonCtrl [MFC], GetPos
- CSpinButtonCtrl [MFC], GetRange
- CSpinButtonCtrl [MFC], SetAccel
- CSpinButtonCtrl [MFC], SetBase
- CSpinButtonCtrl [MFC], SetBuddy
- CSpinButtonCtrl [MFC], SetPos
- CSpinButtonCtrl [MFC], SetRange
ms.assetid: 509bfd76-1c5a-4af6-973f-e133c0b87734
ms.openlocfilehash: cedfe16a6870bc779121e8e864866cfcb711b148
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753106"
---
# <a name="cspinbuttonctrl-class"></a>CSpinButtonCtrl-Klasse

Stellt die Funktionalität des allgemeinen Windows-Drehfeld-Steuerelements bereit.

## <a name="syntax"></a>Syntax

```
class CSpinButtonCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSpinButtonCtrl::CSpinButtonCtrl](#cspinbuttonctrl)|Erstellt ein `CSpinButtonCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSpinButtonCtrl::Erstellen](#create)|Erstellt ein Drehtastensteuerelement und fügt `CSpinButtonCtrl` es an ein Objekt an.|
|[CSpinButtonCtrl::CreateEx](#createex)|Erstellt ein Drehschaltflächensteuerelement mit den angegebenen erweiterten `CSpinButtonCtrl` Windows-Stilen und fügt es an ein Objekt an.|
|[CSpinButtonCtrl::GetAccel](#getaccel)|Ruft Beschleunigungsinformationen für ein Drehtastensteuerelement ab.|
|[CSpinButtonCtrl::GetBase](#getbase)|Ruft die aktuelle Basis für ein Drehtastensteuerelement ab.|
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|Ruft einen Zeiger auf das aktuelle Buddy-Fenster ab.|
|[CSpinButtonCtrl::GetPos](#getpos)|Ruft die aktuelle Position eines Drehtastensteuerelements ab.|
|[CSpinButtonCtrl::GetRange](#getrange)|Ruft die oberen und unteren Grenzwerte (Bereich) für ein Drehtastensteuerelement ab.|
|[CSpinButtonCtrl::SetAccel](#setaccel)|Legt die Beschleunigung für ein Drehtastensteuerelement fest.|
|[CSpinButtonCtrl::SetBase](#setbase)|Legt die Basis für ein Drehtastensteuerelement fest.|
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|Legt das Buddy-Fenster für ein Drehtastensteuerelement fest.|
|[CSpinButtonCtrl::SetPos](#setpos)|Legt die aktuelle Position für das Steuerelement fest.|
|[CSpinButtonCtrl::SetRange](#setrange)|Legt die oberen und unteren Grenzwerte (Bereich) für ein Drehtastensteuerelement fest.|

## <a name="remarks"></a>Bemerkungen

Ein "Spin-Button-Steuerelement" (auch als Up-Down-Steuerelement bezeichnet) ist ein Paar VonPfeiltasten, auf die der Benutzer klicken kann, um einen Wert zu erhöhen oder zu dekrementieren, z. B. eine Bildlaufposition oder eine Zahl, die in einem Begleitsteuerelement angezeigt wird. Der Wert, der einem Drehtastensteuerelement zugeordnet ist, wird als seine aktuelle Position bezeichnet. Ein Drehtastensteuerelement wird am häufigsten mit einem Begleitsteuerelement verwendet, das als "Buddy-Fenster" bezeichnet wird.

Dieses Steuerelement (und `CSpinButtonCtrl` damit die Klasse) ist nur für Programme verfügbar, die unter Windows 95/98 und Windows NT Version 3.51 und höher ausgeführt werden.

Für den Benutzer sehen ein Drehtastensteuerelement und sein Buddy-Fenster oft wie ein einzelnes Steuerelement aus. Sie können festlegen, dass sich ein Drehtastensteuerelement automatisch neben seinem Buddy-Fenster positioniert und die Beschriftung des Buddy-Fensters automatisch auf seine aktuelle Position setzt. Sie können ein Drehtastensteuerelement mit einem Bearbeitungssteuerelement verwenden, um den Benutzer zur numerischen Eingabe aufzufordern.

Wenn Sie auf den Pfeil nach oben klicken, wird die aktuelle Position in Richtung des Maximums verschoben, und durch Klicken auf den Pfeil nach unten wird die aktuelle Position in Richtung des Minimums verschoben. Standardmäßig ist das Minimum 100 und das Maximum 0. Jedes Mal, wenn die Mindesteinstellung größer als die maximale Einstellung ist (z. B. wenn die Standardeinstellungen verwendet werden), verringert das Klicken auf den Pfeil nach oben den Positionswert, und durch Klicken auf den Abwärtspfeil wird er erhöht.

Ein Drehtastensteuerelement ohne Buddy-Fenster fungiert als eine Art vereinfachte Bildlaufleiste. Beispielsweise zeigt ein Registerkartensteuerelement manchmal ein Drehschaltflächensteuerelement an, damit der Benutzer zusätzliche Registerkarten in die Ansicht scrollen kann.

Weitere Informationen zur `CSpinButtonCtrl`Verwendung finden Sie unter [Steuerelemente](../../mfc/controls-mfc.md) und [Verwenden von CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSpinButtonCtrl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcmn.h

## <a name="cspinbuttonctrlcreate"></a><a name="create"></a>CSpinButtonCtrl::Erstellen

Erstellt ein Drehschaltflächensteuerelement und `CSpinButtonCtrl` fügt es an ein Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Gibt den Stil des Drehschaltflächensteuerelements an. Wenden Sie eine beliebige Kombination von Drehtastensteuerungsstilen auf das Steuerelement an. Diese Stile werden im Windows SDK unter [Up-Down Control Styles](/windows/win32/Controls/up-down-control-styles) beschrieben.

*Rect*<br/>
Gibt die Größe und Position des Drehschaltflächensteuerelements an. Es kann entweder ein [CRect-Objekt](../../atl-mfc-shared/reference/crect-class.md) oder eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) sein.

*pParentWnd*<br/>
Ein Zeiger auf das übergeordnete Fenster des Drehschaltflächensteuerelements, in der Regel eine `CDialog`. Es darf nicht NULL sein.

*nID*<br/>
Gibt die ID des Drehschaltflächensteuerelements an.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Initialisierung erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CSpinButtonCtrl` ein Objekt in zwei Schritten Zuerst aufrufen `Create`Sie den Konstruktor und rufen dann `CSpinButtonCtrl` auf, das das Drehschaltflächensteuerelement erstellt und an das Objekt anfügt.

Um ein Drehschaltflächensteuerelement mit erweiterten Fensterstilen zu erstellen, rufen `Create`Sie [CSpinButtonCtrl::CreateEx](#createex) anstelle von auf.

## <a name="cspinbuttonctrlcreateex"></a><a name="createex"></a>CSpinButtonCtrl::CreateEx

Erstellt ein Steuerelement (ein untergeordnetes Fenster) und ordnet es dem `CSpinButtonCtrl` Objekt zu.

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
Gibt den erweiterten Stil des zu erstellenden Steuerelements an. Eine Liste der erweiterten Fensterstile finden Sie im *dwExStyle-Parameter* für [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) im Windows SDK.

*dwStyle*<br/>
Gibt den Stil des Drehschaltflächensteuerelements an. Wenden Sie eine beliebige Kombination von Drehtastensteuerungsstilen auf das Steuerelement an. Diese Stile werden im Windows SDK unter [Up-Down Control Styles](/windows/win32/Controls/up-down-control-styles) beschrieben.

*Rect*<br/>
Ein Verweis auf eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die die Größe und Position des zu erstellenden Fensters in den Clientkoordinaten von *pParentWnd*beschreibt.

*pParentWnd*<br/>
Ein Zeiger auf das Fenster, das das übergeordnete Steuerelement ist.

*nID*<br/>
Die untergeordnete Fenster-ID des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Verwenden `CreateEx` Sie anstelle von [Erstellen,](#create) um erweiterte Windows-Formatvorlagen anzuwenden, die durch das Windows-Vorwort für erweiterte Stile WS_EX_ angegeben werden.

## <a name="cspinbuttonctrlcspinbuttonctrl"></a><a name="cspinbuttonctrl"></a>CSpinButtonCtrl::CSpinButtonCtrl

Erstellt ein `CSpinButtonCtrl`-Objekt.

```
CSpinButtonCtrl();
```

## <a name="cspinbuttonctrlgetaccel"></a><a name="getaccel"></a>CSpinButtonCtrl::GetAccel

Ruft Beschleunigungsinformationen für ein Drehtastensteuerelement ab.

```
UINT GetAccel(
    int nAccel,
    UDACCEL* pAccel) const;
```

### <a name="parameters"></a>Parameter

*nAccel*<br/>
Anzahl der Elemente im Array, die von *pAccel*angegeben werden.

*pAccel*<br/>
Zeiger auf ein Array von [UDACCEL-Strukturen,](/windows/win32/api/commctrl/ns-commctrl-udaccel) das Beschleunigungsinformationen empfängt.

### <a name="return-value"></a>Rückgabewert

Anzahl der abgerufenen Beschleunigerstrukturen.

## <a name="cspinbuttonctrlgetbase"></a><a name="getbase"></a>CSpinButtonCtrl::GetBase

Ruft die aktuelle Basis für ein Drehtastensteuerelement ab.

```
UINT GetBase() const;
```

### <a name="return-value"></a>Rückgabewert

Der aktuelle Basiswert.

## <a name="cspinbuttonctrlgetbuddy"></a><a name="getbuddy"></a>CSpinButtonCtrl::GetBuddy

Ruft einen Zeiger auf das aktuelle Buddy-Fenster ab.

```
CWnd* GetBuddy() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das aktuelle Buddy-Fenster.

## <a name="cspinbuttonctrlgetpos"></a><a name="getpos"></a>CSpinButtonCtrl::GetPos

Ruft die aktuelle Position eines Drehtastensteuerelements ab.

```
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;
```

### <a name="parameters"></a>Parameter

*lpbError*<br/>
Ein Zeiger auf einen booleschen Wert, der auf Null gesetzt ist, wenn der Wert erfolgreich abgerufen wird, oder ungleich Null, wenn ein Fehler auftritt. Wenn dieser Parameter auf NULL festgelegt ist, werden keine Fehler gemeldet.

### <a name="return-value"></a>Rückgabewert

Die erste Version gibt die aktuelle 16-Bit-Position im Wort niedriger Ordnung zurück. Das Wort mit hoher Ordnung ist ungleich Null, wenn ein Fehler aufgetreten ist.

Die zweite Version gibt die 32-Bit-Position zurück.

### <a name="remarks"></a>Bemerkungen

Wenn der zurückgegebene Wert verarbeitet wird, aktualisiert das Steuerelement seine aktuelle Position basierend auf der Beschriftung des Buddy-Fensters. Das Steuerelement gibt einen Fehler zurück, wenn kein Buddy-Fenster vorhanden ist oder wenn die Beschriftung einen ungültigen oder anicht enden den Bereich wert angibt.

## <a name="cspinbuttonctrlgetrange"></a><a name="getrange"></a>CSpinButtonCtrl::GetRange

Ruft die oberen und unteren Grenzwerte (Bereich) für ein Drehtastensteuerelement ab.

```
DWORD GetRange() const;

void GetRange(
    int& lower,
    int& upper) const;

void GetRange32(
    int& lower,
    int &upper) const;
```

### <a name="parameters"></a>Parameter

*Niedriger*<br/>
Verweis auf eine ganze Zahl, die die untere Grenze für das Steuerelement empfängt.

*Oberen*<br/>
Verweis auf eine ganze Zahl, die die Obergrenze für das Steuerelement empfängt.

### <a name="return-value"></a>Rückgabewert

Die erste Version gibt einen 32-Bit-Wert zurück, der die oberen und unteren Grenzwerte enthält. Das Wort niedriger Ordnung ist die obere Grenze für das Steuerelement, und das Wort hoher Ordnung ist die untere Grenze.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion `GetRange32` ruft den Bereich des Drehtastensteuerelements als 32-Bit-Ganzzahl ab.

## <a name="cspinbuttonctrlsetaccel"></a><a name="setaccel"></a>CSpinButtonCtrl::SetAccel

Legt die Beschleunigung für ein Drehtastensteuerelement fest.

```
BOOL SetAccel(
    int nAccel,
    UDACCEL* pAccel);
```

### <a name="parameters"></a>Parameter

*nAccel*<br/>
Anzahl der von *pAccel*angegebenen [UDACCEL-Strukturen](/windows/win32/api/commctrl/ns-commctrl-udaccel) .

*pAccel*<br/>
Zeiger auf ein Array von UDACCEL-Strukturen, die Beschleunigungsinformationen enthalten. Elemente sollten basierend auf dem `nSec` Element in aufsteigender Reihenfolge sortiert werden.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

## <a name="cspinbuttonctrlsetbase"></a><a name="setbase"></a>CSpinButtonCtrl::SetBase

Legt die Basis für ein Drehtastensteuerelement fest.

```
int SetBase(int nBase);
```

### <a name="parameters"></a>Parameter

*nBase*<br/>
Neuer Basiswert für das Steuerelement. Es kann 10 für Dezimal- oder 16 für Hexadezimal sein.

### <a name="return-value"></a>Rückgabewert

Der vorherige Basiswert bei Erfolg oder Null, wenn eine ungültige Basis angegeben wird.

### <a name="remarks"></a>Bemerkungen

Der Basiswert bestimmt, ob das Buddy-Fenster Zahlen in Dezimal- oder Hexadezimalziffern anzeigt. Hexadezimale Zahlen sind immer nicht signiert; Dezimalzahlen sind signiert.

## <a name="cspinbuttonctrlsetbuddy"></a><a name="setbuddy"></a>CSpinButtonCtrl::SetBuddy

Legt das Buddy-Fenster für ein Drehtastensteuerelement fest.

```
CWnd* SetBuddy(CWnd* pWndBuddy);
```

### <a name="parameters"></a>Parameter

*pWndBuddy*<br/>
Zeiger auf das neue Buddy-Fenster.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das vorherige Buddy-Fenster.

### <a name="remarks"></a>Bemerkungen

Ein Spin-Steuerelement ist fast immer einem anderen Fenster zugeordnet, z. B. einem Bearbeitungssteuerelement, das einige Inhalte anzeigt. Dieses andere Fenster wird als "Buddy" des Spin-Steuerelements bezeichnet.

## <a name="cspinbuttonctrlsetpos"></a><a name="setpos"></a>CSpinButtonCtrl::SetPos

Legt die aktuelle Position für ein Drehtastensteuerelement fest.

```
int SetPos(int nPos);
int SetPos32(int nPos);
```

### <a name="parameters"></a>Parameter

*Npos*<br/>
Neue Position für das Steuerelement. Dieser Wert muss sich in dem Bereich befinden, der durch die oberen und unteren Grenzwerte für das Steuerelement angegeben wird.

### <a name="return-value"></a>Rückgabewert

Die vorherige Position (16-Bit-Präzision für `SetPos`, `SetPos32`32-Bit-Präzision für ).

### <a name="remarks"></a>Bemerkungen

`SetPos32`setzt die 32-Bit-Position.

## <a name="cspinbuttonctrlsetrange"></a><a name="setrange"></a>CSpinButtonCtrl::SetRange

Legt die oberen und unteren Grenzwerte (Bereich) für ein Drehtastensteuerelement fest.

```cpp
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>Parameter

*nLower* und *nUpper*<br/>
Obere und untere Grenzwerte für die Steuerung. Für `SetRange`darf kein Grenzwert größer als UD_MAXVAL oder kleiner als UD_MINVAL sein. Außerdem darf die Differenz zwischen den beiden Grenzwerten UD_MAXVAL nicht überschreiten. `SetRange32`setzt keine Beschränkungen für die Grenzwerte; ganzzahlen.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion `SetRange32` legt den 32-Bit-Bereich für die Drehtastensteuerung fest.

> [!NOTE]
> Der Standardbereich für die Drehschaltfläche hat den maximalen Wert auf Null (0) und das Minimum auf 100. Da der Maximalwert kleiner als der Mindestwert ist, verringert durch Klicken auf den Pfeil nach oben die Position, und durch Klicken auf den Abwärtspfeil wird er erhöht. Verwenden `CSpinButtonCtrl::SetRange` Sie diese Werte, um diese Werte anzupassen.

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CSliderCtrl-Klasse](../../mfc/reference/csliderctrl-class.md)
