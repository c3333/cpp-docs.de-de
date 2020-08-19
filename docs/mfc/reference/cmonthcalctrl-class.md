---
title: CMonthCalCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::Create
- AFXDTCTL/CMonthCalCtrl::GetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::GetCalendarCount
- AFXDTCTL/CMonthCalCtrl::GetCalendarGridInfo
- AFXDTCTL/CMonthCalCtrl::GetCalID
- AFXDTCTL/CMonthCalCtrl::GetColor
- AFXDTCTL/CMonthCalCtrl::GetCurrentView
- AFXDTCTL/CMonthCalCtrl::GetCurSel
- AFXDTCTL/CMonthCalCtrl::GetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::GetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::GetMaxTodayWidth
- AFXDTCTL/CMonthCalCtrl::GetMinReqRect
- AFXDTCTL/CMonthCalCtrl::GetMonthDelta
- AFXDTCTL/CMonthCalCtrl::GetMonthRange
- AFXDTCTL/CMonthCalCtrl::GetRange
- AFXDTCTL/CMonthCalCtrl::GetSelRange
- AFXDTCTL/CMonthCalCtrl::GetToday
- AFXDTCTL/CMonthCalCtrl::HitTest
- AFXDTCTL/CMonthCalCtrl::IsCenturyView
- AFXDTCTL/CMonthCalCtrl::IsDecadeView
- AFXDTCTL/CMonthCalCtrl::IsMonthView
- AFXDTCTL/CMonthCalCtrl::IsYearView
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorderDefault
- AFXDTCTL/CMonthCalCtrl::SetCalID
- AFXDTCTL/CMonthCalCtrl::SetCenturyView
- AFXDTCTL/CMonthCalCtrl::SetColor
- AFXDTCTL/CMonthCalCtrl::SetCurrentView
- AFXDTCTL/CMonthCalCtrl::SetCurSel
- AFXDTCTL/CMonthCalCtrl::SetDayState
- AFXDTCTL/CMonthCalCtrl::SetDecadeView
- AFXDTCTL/CMonthCalCtrl::SetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::SetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::SetMonthDelta
- AFXDTCTL/CMonthCalCtrl::SetMonthView
- AFXDTCTL/CMonthCalCtrl::SetRange
- AFXDTCTL/CMonthCalCtrl::SetSelRange
- AFXDTCTL/CMonthCalCtrl::SetToday
- AFXDTCTL/CMonthCalCtrl::SetYearView
- AFXDTCTL/CMonthCalCtrl::SizeMinReq
- AFXDTCTL/CMonthCalCtrl::SizeRectToMin
helpviewer_keywords:
- CMonthCalCtrl [MFC], CMonthCalCtrl
- CMonthCalCtrl [MFC], Create
- CMonthCalCtrl [MFC], GetCalendarBorder
- CMonthCalCtrl [MFC], GetCalendarCount
- CMonthCalCtrl [MFC], GetCalendarGridInfo
- CMonthCalCtrl [MFC], GetCalID
- CMonthCalCtrl [MFC], GetColor
- CMonthCalCtrl [MFC], GetCurrentView
- CMonthCalCtrl [MFC], GetCurSel
- CMonthCalCtrl [MFC], GetFirstDayOfWeek
- CMonthCalCtrl [MFC], GetMaxSelCount
- CMonthCalCtrl [MFC], GetMaxTodayWidth
- CMonthCalCtrl [MFC], GetMinReqRect
- CMonthCalCtrl [MFC], GetMonthDelta
- CMonthCalCtrl [MFC], GetMonthRange
- CMonthCalCtrl [MFC], GetRange
- CMonthCalCtrl [MFC], GetSelRange
- CMonthCalCtrl [MFC], GetToday
- CMonthCalCtrl [MFC], HitTest
- CMonthCalCtrl [MFC], IsCenturyView
- CMonthCalCtrl [MFC], IsDecadeView
- CMonthCalCtrl [MFC], IsMonthView
- CMonthCalCtrl [MFC], IsYearView
- CMonthCalCtrl [MFC], SetCalendarBorder
- CMonthCalCtrl [MFC], SetCalendarBorderDefault
- CMonthCalCtrl [MFC], SetCalID
- CMonthCalCtrl [MFC], SetCenturyView
- CMonthCalCtrl [MFC], SetColor
- CMonthCalCtrl [MFC], SetCurrentView
- CMonthCalCtrl [MFC], SetCurSel
- CMonthCalCtrl [MFC], SetDayState
- CMonthCalCtrl [MFC], SetDecadeView
- CMonthCalCtrl [MFC], SetFirstDayOfWeek
- CMonthCalCtrl [MFC], SetMaxSelCount
- CMonthCalCtrl [MFC], SetMonthDelta
- CMonthCalCtrl [MFC], SetMonthView
- CMonthCalCtrl [MFC], SetRange
- CMonthCalCtrl [MFC], SetSelRange
- CMonthCalCtrl [MFC], SetToday
- CMonthCalCtrl [MFC], SetYearView
- CMonthCalCtrl [MFC], SizeMinReq
- CMonthCalCtrl [MFC], SizeRectToMin
ms.assetid: a42f6bd6-ab5c-4335-82f8-839982fc64a2
ms.openlocfilehash: d986aa5f8e232f0ab94858dbdfae5754536ccdb9
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562141"
---
# <a name="cmonthcalctrl-class"></a>CMonthCalCtrl-Klasse

Kapselt die Funktionalität eines Monatskalender-Steuerelements.

## <a name="syntax"></a>Syntax

```
class CMonthCalCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|BESCHREIBUNG|
|----------|-----------------|
|[CMonthCalCtrl:: CMonthCalCtrl](#cmonthcalctrl)|Erstellt ein `CMonthCalCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CMonthCalCtrl:: Create](#create)|Erstellt ein Monatskalender-Steuerelement und fügt es an das- `CMonthCalCtrl` Objekt an.|
|[CMonthCalCtrl:: getcalendarborder](#getcalendarborder)|Ruft die Breite des Rahmens des Kalender Steuer Elements des aktuellen Monats ab.|
|[CMonthCalCtrl:: getcalendarcount](#getcalendarcount)|Ruft die Anzahl der Kalender ab, die im Kalender Steuerelement des aktuellen Monats angezeigt werden.|
|[CMonthCalCtrl:: getcalendargridinfo](#getcalendargridinfo)|Ruft Informationen über das Kalender Steuerelement des aktuellen Monats ab.|
|[CMonthCalCtrl:: getcalid](#getcalid)|Ruft den Kalender Bezeichner für das Kalender Steuerelement des aktuellen Monats ab.|
|[CMonthCalCtrl:: GetColor](#getcolor)|Ruft die Farbe eines angegebenen Bereichs eines Monatskalender-Steuer Elements ab.|
|[CMonthCalCtrl:: getcurrentview](#getcurrentview)|Ruft die Ansicht ab, die derzeit vom Kalender Steuerelement für den aktuellen Monat angezeigt wird.|
|[CMonthCalCtrl:: getcurrsel](#getcursel)|Ruft die Systemzeit ab, die durch das aktuell ausgewählte Datum angegeben wird.|
|[CMonthCalCtrl:: getfirstdayof-Woche](#getfirstdayofweek)|Ruft den ersten Tag der Woche ab, der in der Spalte ganz links des Kalenders angezeigt werden soll.|
|[CMonthCalCtrl:: getmaxselcount](#getmaxselcount)|Ruft die aktuelle maximale Anzahl von Tagen ab, die in einem Monatskalender-Steuerelement ausgewählt werden können.|
|[CMonthCalCtrl:: getmaxredaywidth](#getmaxtodaywidth)|Ruft die maximale Breite der "Today"-Zeichenfolge für das Kalender Steuerelement des aktuellen Monats ab.|
|[CMonthCalCtrl:: getminreqrect](#getminreqrect)|Ruft die Mindestgröße ab, die erforderlich ist, um einen vollen Monat in einem Monatskalender-Steuerelement anzuzeigen.|
|[CMonthCalCtrl:: getmonthdelta](#getmonthdelta)|Ruft die Bild Lauf Rate für ein Monatskalender-Steuerelement ab.|
|[CMonthCalCtrl:: getmonthrange](#getmonthrange)|Ruft Datumsinformationen ab, die die hohen und unteren Grenzen der Anzeige eines Monatskalender-Steuer Elements darstellen.|
|[CMonthCalCtrl:: GetRange](#getrange)|Ruft das aktuelle Mindest-und maximal Datum ab, das in einem Monatskalender-Steuerelement festgelegt ist.|
|[CMonthCalCtrl:: getselrange](#getselrange)|Ruft Datumsinformationen ab, die die obere und untere Grenze des Datums Bereichs darstellen, der derzeit vom Benutzer ausgewählt wird.|
|[CMonthCalCtrl:: gettoday](#gettoday)|Ruft die Datumsinformationen für das als "heute" angegebene Datum für ein Monatskalender-Steuerelement ab.|
|[CMonthCalCtrl:: HitTest](#hittest)|Bestimmt, welcher Abschnitt eines Monatskalender-Steuer Elements sich an einem angegebenen Punkt auf dem Bildschirm befindet.|
|[CMonthCalCtrl:: iscenturyview](#iscenturyview)|Gibt an, ob die aktuelle Ansicht des Kalender Steuer Elements des aktuellen Monats die Jahrhundert Ansicht ist.|
|[CMonthCalCtrl:: isdecadeview](#isdecadeview)|Gibt an, ob die aktuelle Ansicht des Kalender Steuer Elements des aktuellen Monats die Dekade-Ansicht ist.|
|[CMonthCalCtrl:: ismonthview](#ismonthview)|Gibt an, ob die aktuelle Ansicht des Kalender Steuer Elements des aktuellen Monats die Monatsansicht ist.|
|[CMonthCalCtrl:: isyearview](#isyearview)|Gibt an, ob die aktuelle Ansicht des Kalender Steuer Elements des aktuellen Monats die Jahr Ansicht ist.|
|[CMonthCalCtrl:: setcalendarborder](#setcalendarborder)|Legt die Breite des Rahmens des Kalender Steuer Elements des aktuellen Monats fest.|
|[CMonthCalCtrl:: setcalendarborderdefault](#setcalendarborderdefault)|Legt die Standardbreite des Rahmens des Kalender Steuer Elements des aktuellen Monats fest.|
|[CMonthCalCtrl:: setcalid](#setcalid)|Legt den Kalender Bezeichner für das Kalender Steuerelement des aktuellen Monats fest.|
|[CMonthCalCtrl:: setcenturyview](#setcenturyview)|Legt das Kalender Steuerelement für den aktuellen Monat fest, um die Jahrhundert Ansicht anzuzeigen.|
|[CMonthCalCtrl:: setColor](#setcolor)|Legt die Farbe eines angegebenen Bereichs eines Monatskalender-Steuer Elements fest.|
|[CMonthCalCtrl:: SetCurrentView](#setcurrentview)|Legt das Kalender Steuerelement für den aktuellen Monat fest, um die angegebene Ansicht anzuzeigen.|
|[CMonthCalCtrl:: setcurrsel](#setcursel)|Legt das aktuell ausgewählte Datum für ein Monatskalender-Steuerelement fest.|
|[CMonthCalCtrl:: SetDayState](#setdaystate)|Legt die Anzeige für Tage in einem Monatskalender-Steuerelement fest.|
|[CMonthCalCtrl:: setdecadeview](#setdecadeview)|Legt das Kalender Steuerelement des aktuellen Monats auf die Dekade-Ansicht fest.|
|[CMonthCalCtrl:: setfirstdayof-Woche](#setfirstdayofweek)|Legt den Wochentag fest, der in der Spalte ganz links des Kalenders angezeigt werden soll.|
|[CMonthCalCtrl:: setmaxselcount](#setmaxselcount)|Legt die maximale Anzahl von Tagen fest, die in einem Monatskalender-Steuerelement ausgewählt werden können.|
|[CMonthCalCtrl:: setmonthdelta](#setmonthdelta)|Legt die Bild Lauf Rate für ein Monatskalender-Steuerelement fest.|
|[CMonthCalCtrl:: setmonthview](#setmonthview)|Legt das Kalender Steuerelement des aktuellen Monats zum Anzeigen der Monatsansicht fest.|
|[CMonthCalCtrl:: abge](#setrange)|Legt das minimal-und maximal zulässige Datum für ein Monatskalender-Steuerelement fest.|
|[CMonthCalCtrl:: setselrange](#setselrange)|Legt die Auswahl für ein Monatskalender-Steuerelement auf einen bestimmten Datumsbereich fest.|
|[CMonthCalCtrl:: settoday](#settoday)|Legt das Kalender Steuerelement für den aktuellen Tag fest.|
|[CMonthCalCtrl:: setyearview](#setyearview)|Legt das Kalender Steuerelement des aktuellen Monats auf die Year-Ansicht fest.|
|[CMonthCalCtrl:: sizeminreq](#sizeminreq)|Zeichnet das Monatskalender-Steuerelement auf seine minimale, einmonatige Größe auf.|
|[CMonthCalCtrl:: sizerecttomin](#sizerecttomin)|Berechnet für das Kalender Steuerelement des aktuellen Monats das kleinste Rechteck, das alle Kalender enthalten kann, die in ein angegebenes Rechteck passen.|

## <a name="remarks"></a>Bemerkungen

Das Month Calendar-Steuerelement stellt dem Benutzer eine einfache Kalender Schnittstelle bereit, von der der Benutzer ein Datum auswählen kann. Der Benutzer kann die Anzeige wie folgt ändern:

- Bildlauf rückwärts und vorwärts, von Monat zu Monat.

- Klicken auf den heute-Text, um den aktuellen Tag anzuzeigen (wenn der MCS_NOTODAY Stil nicht verwendet wird).

- Auswählen eines Monats oder eines Jahres aus einem Popupmenü.

Sie können das Monatskalender-Steuerelement anpassen, indem Sie eine Vielzahl von Formaten auf das Objekt anwenden, wenn Sie es erstellen. Diese Stile werden in der Windows SDK des [Monatskalender-Steuer](/windows/win32/Controls/month-calendar-control-styles) Elements beschrieben.

Das Monatskalender-Steuerelement kann mehr als einen Monat anzeigen, und es kann bestimmte Tage (z. b. Feiertage) durch das Fett Formatieren des Datums angeben.

Weitere Informationen zur Verwendung des Monatskalender-Steuer Elements finden [Sie unter Using CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CMonthCalCtrl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdtctl. h

## <a name="cmonthcalctrlcmonthcalctrl"></a><a name="cmonthcalctrl"></a> CMonthCalCtrl:: CMonthCalCtrl

Erstellt ein `CMonthCalCtrl`-Objekt.

```
CMonthCalCtrl();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen `Create` nach dem Erstellen des-Objekts aufzurufen.

## <a name="cmonthcalctrlcreate"></a><a name="create"></a> CMonthCalCtrl:: Create

Erstellt ein Monatskalender-Steuerelement und fügt es an das- `CMonthCalCtrl` Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL Create(
    DWORD dwStyle,
    const POINT& pt,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwstyle*<br/>
Gibt die Kombination der Windows-Stile an, die auf das Steuerelement month Calendar angewendet werden Weitere Informationen zu den Stilen finden Sie unter [Month Calendar-Steuerelement Stile](/windows/win32/Controls/month-calendar-control-styles) in der Windows SDK.

*Rect*<br/>
Ein Verweis auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur. Enthält die Position und Größe des Monatskalender-Steuer Elements.

*pt*<br/>
Ein Verweis auf eine [Punkt](/windows/win32/api/windef/ns-windef-point) Struktur, die den Speicherort des Monatskalender-Steuer Elements angibt.

*pparser*<br/>
Ein Zeiger auf ein [CWnd](../../mfc/reference/cwnd-class.md) -Objekt, das das übergeordnete Fenster des Monatskalender-Steuer Elements ist. Er darf nicht NULL sein.

*nID*<br/>
Gibt die Steuerelement-ID des Monatskalender-Steuer Elements an.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn die Initialisierung erfolgreich war. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Erstellen Sie ein Monatskalender-Steuerelement in zwei Schritten:

1. [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) zum Erstellen eines- `CMonthCalCtrl` Objekts aufzurufen.

1. Diese Member-Funktion wird aufgerufen, wodurch ein Monatskalender-Steuerelement erstellt und an das-Objekt angefügt wird `CMonthCalCtrl` .

Wenn Sie aufzurufen `Create` , werden die allgemeinen Steuerelemente initialisiert. Die von `Create` Ihnen aufrufende Version bestimmt, wie die Größenanpassung erfolgt:

- Wenn MFC das Steuerelement automatisch auf einen Monat festlegen soll, müssen Sie die außer Kraft Setzung aufrufen, die den *PT* -Parameter verwendet.

- Um das Steuerelement selbst zu vergrößern, müssen Sie die außer Kraft setzung dieser Funktion aufrufen, die den *Rect* -Parameter verwendet.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]

## <a name="cmonthcalctrlgetcalendarborder"></a><a name="getcalendarborder"></a> CMonthCalCtrl:: getcalendarborder

Ruft die Breite des Rahmens des Kalender Steuer Elements des aktuellen Monats ab.

```
int GetCalendarBorder() const;
```

### <a name="return-value"></a>Rückgabewert

Die Breite des Steuerelement Rahmens in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [MCM_GETCALENDARBORDER](/windows/win32/Controls/mcm-getcalendarborder) Nachricht, die in der Windows SDK beschrieben wird.

## <a name="cmonthcalctrlgetcalendarcount"></a><a name="getcalendarcount"></a> CMonthCalCtrl:: getcalendarcount

Ruft die Anzahl der Kalender ab, die im Kalender Steuerelement des aktuellen Monats angezeigt werden.

```
int GetCalendarCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der derzeit im Monatskalender-Steuerelement angezeigten Kalender. Die maximal zulässige Anzahl von Kalendern ist 12.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [MCM_GETCALENDARCOUNT](/windows/win32/Controls/mcm-getcalendarcount) Nachricht, die in der Windows SDK beschrieben wird.

## <a name="cmonthcalctrlgetcalendargridinfo"></a><a name="getcalendargridinfo"></a> CMonthCalCtrl:: getcalendargridinfo

Ruft Informationen über das Kalender Steuerelement des aktuellen Monats ab.

```
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;
```

### <a name="parameters"></a>Parameter

*pmcgridinfo*\
vorgenommen Ein Zeiger auf eine [mcgridinfo](/windows/win32/api/commctrl/ns-commctrl-mcgridinfo) -Struktur, die Informationen über das Kalender Steuerelement des aktuellen Monats empfängt. Der Aufrufer ist dafür verantwortlich, diese Struktur zuzuordnen und zu initialisieren.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [MCM_GETCALENDARGRIDINFO](/windows/win32/Controls/mcm-getcalendargridinfo) Nachricht, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die-Variable definiert, die `m_monthCalCtrl` für den programmgesteuerten Zugriff auf das Month Calendar-Steuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die- `GetCalendarGridInfo` Methode verwendet, um das Kalenderdatum abzurufen, das im Kalender Steuerelement des aktuellen Monats angezeigt wird.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]

## <a name="cmonthcalctrlgetcalid"></a><a name="getcalid"></a> CMonthCalCtrl:: getcalid

Ruft den Kalender Bezeichner für das Kalender Steuerelement des aktuellen Monats ab.

```
CALID GetCalID() const;
```

### <a name="return-value"></a>Rückgabewert

Eine der [kalenderbezeichnerkonstanten](/windows/win32/Intl/calendar-identifiers) .

### <a name="remarks"></a>Bemerkungen

Ein Kalender Bezeichner bezeichnet einen regionsspezifischen Kalender, z. b. die gregorianischen (lokalisierten), japanischen oder Hijri-Kalender. Die Anwendung kann einen Kalender Bezeichner verwenden, der über verschiedene sprach Unterstützungsfunktionen verfügt.

Diese Methode sendet die [MCM_GETCALID](/windows/win32/Controls/mcm-getcalid) Nachricht, die in der Windows SDK beschrieben wird.

## <a name="cmonthcalctrlgetcolor"></a><a name="getcolor"></a> CMonthCalCtrl:: GetColor

Ruft die Farbe eines Bereichs des Monatskalender-Steuer Elements ab, das von *nregion*angegeben wird.

```
COLORREF GetColor(int nRegion) const;
```

### <a name="parameters"></a>Parameter

*nregion*<br/>
Der Bereich des Monatskalender-Steuer Elements, aus dem die Farbe abgerufen wird. Eine Liste der Werte finden Sie unter dem *nregion* -Parameter von [SetColor](#setcolor).

### <a name="return-value"></a>Rückgabewert

Ein [COLORREF](/windows/win32/gdi/colorref) -Wert, der die Farbe angibt, die dem Teil des Monatskalender-Steuer Elements zugeordnet ist, wenn erfolgreich. Andernfalls gibt diese Member-Funktion-1 zurück.

## <a name="cmonthcalctrlgetcurrentview"></a><a name="getcurrentview"></a> CMonthCalCtrl:: getcurrentview

Ruft die Ansicht ab, die derzeit vom Kalender Steuerelement für den aktuellen Monat angezeigt wird.

```
DWORD GetCurrentView() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Ansicht, die durch einen der folgenden Werte angezeigt wird:

|Wert|Bedeutung|
|-----------|-------------|
|MCMV_MONTH|Monatliche Ansicht|
|MCMV_YEAR|Jährliche Ansicht|
|MCMV_DECADE|Dekade (Ansicht)|
|MCMV_CENTURY|Jahrhundert Ansicht|

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) Nachricht, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die-Variable definiert, die `m_monthCalCtrl` für den programmgesteuerten Zugriff auf das Month Calendar-Steuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die Anzeige des Monatskalender-Steuer Elements angezeigt.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]

## <a name="cmonthcalctrlgetcursel"></a><a name="getcursel"></a> CMonthCalCtrl:: getcurrsel

Ruft die Systemzeit ab, die durch das aktuell ausgewählte Datum angegeben wird.

```
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;

BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Parameter

*Ref DateTime*<br/>
Ein Verweis auf ein [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -Objekt oder ein [ctime](../../atl-mfc-shared/reference/ctime-class.md) -Objekt. Empfängt die aktuelle Zeit.

*pdatetime*<br/>
Ein Zeiger auf eine [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) -Struktur, die die aktuell ausgewählten Datumsinformationen empfängt. Dieser Parameter muss eine gültige Adresse sein und darf nicht NULL sein.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn erfolgreich; otherwize 0.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [MCM_GETCURSEL](/windows/win32/Controls/mcm-getcursel), wie in der Windows SDK beschrieben.

> [!NOTE]
> Diese Member-Funktion schlägt fehl, wenn die Format MCS_MULTISELECT festgelegt ist.

In der MFC-Implementierung von `GetCurSel` können Sie eine Verwendungs- `COleDateTime` , Verwendungs- `CTime` oder `SYSTEMTIME` Struktur Verwendung angeben.

## <a name="cmonthcalctrlgetfirstdayofweek"></a><a name="getfirstdayofweek"></a> CMonthCalCtrl:: getfirstdayof-Woche

Ruft den ersten Tag der Woche ab, der in der Spalte ganz links des Kalenders angezeigt werden soll.

```
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;
```

### <a name="parameters"></a>Parameter

*pblocal*<br/>
Ein Zeiger auf einen booleschen Wert. Wenn der Wert ungleich 0 (null) ist, entspricht die Einstellung des-Steuer Elements nicht der-Einstellung in der Systemsteuerung.

### <a name="return-value"></a>Rückgabewert

Ein ganzzahliger Wert, der den ersten Tag der Woche darstellt. Weitere Informationen dazu, was diese Ganzzahlen darstellen, finden Sie unter " **Hinweise** ".

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [MCM_GETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-getfirstdayofweek), wie in der Windows SDK beschrieben. Die Wochentage werden wie folgt als ganze Zahlen dargestellt.

|Wert|Wochentag|
|-----------|---------------------|
|0|Montag|
|1|Tuesday|
|2|Wednesday|
|3|Thursday|
|4|Freitag|
|5|Samstag|
|6|Sonntag|

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMonthCalCtrl:: setfirstdayof Week](#setfirstdayofweek).

## <a name="cmonthcalctrlgetmaxselcount"></a><a name="getmaxselcount"></a> CMonthCalCtrl:: getmaxselcount

Ruft die aktuelle maximale Anzahl von Tagen ab, die in einem Monatskalender-Steuerelement ausgewählt werden können.

```
int GetMaxSelCount() const;
```

### <a name="return-value"></a>Rückgabewert

Ein ganzzahliger Wert, der die Gesamtzahl der Tage darstellt, die für das-Steuerelement ausgewählt werden können.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [MCM_GETMAXSELCOUNT](/windows/win32/Controls/mcm-getmaxselcount), wie in der Windows SDK beschrieben. Verwenden Sie diese Member-Funktion für Steuerelemente mit dem MCS_MULTISELECT-Stilsatz.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMonthCalCtrl:: setmaxselcount](#setmaxselcount).

## <a name="cmonthcalctrlgetmaxtodaywidth"></a><a name="getmaxtodaywidth"></a> CMonthCalCtrl:: getmaxredaywidth

Ruft die maximale Breite der "Today"-Zeichenfolge für das Kalender Steuerelement des aktuellen Monats ab.

```
DWORD GetMaxTodayWidth() const;
```

### <a name="return-value"></a>Rückgabewert

Die Breite der "Today"-Zeichenfolge in Pixel.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die-Variable definiert, die `m_monthCalCtrl` für den programmgesteuerten Zugriff auf das Month Calendar-Steuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die- `GetMaxTodayWidth` Methode veranschaulicht.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]

### <a name="remarks"></a>Bemerkungen

Der Benutzer kann zum aktuellen Datum zurückkehren, indem er auf die Zeichenfolge "Today" (heute) klickt, die unten im Monatskalender-Steuerelement angezeigt wird. Die Zeichenfolge "Today" enthält Bezeichnungs Text und Datums Text.

Diese Methode sendet die [MCM_GETMAXTODAYWIDTH](/windows/win32/Controls/mcm-getmaxtodaywidth) Nachricht, die in der Windows SDK beschrieben wird.

## <a name="cmonthcalctrlgetminreqrect"></a><a name="getminreqrect"></a> CMonthCalCtrl:: getminreqrect

Ruft die Mindestgröße ab, die erforderlich ist, um einen vollen Monat in einem Monatskalender-Steuerelement anzuzeigen.

```
BOOL GetMinReqRect(RECT* pRect) const;
```

### <a name="parameters"></a>Parameter

*vorab ausführen*<br/>
Ein Zeiger auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur, die Informationen zu umschließenden Rechtecks empfängt. Dieser Parameter muss eine gültige Adresse sein und darf nicht NULL sein.

### <a name="return-value"></a>Rückgabewert

Bei erfolgreicher Ausführung gibt diese Member-Funktion einen Wert ungleich 0 (null) zurück und `lpRect` empfängt die anwendbaren umgebenden Informationen. Wenn nicht erfolgreich, gibt die Member-Funktion 0 zurück.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [MCM_GETMINREQRECT](/windows/win32/Controls/mcm-getminreqrect), wie in der Windows SDK beschrieben.

## <a name="cmonthcalctrlgetmonthdelta"></a><a name="getmonthdelta"></a> CMonthCalCtrl:: getmonthdelta

Ruft die Bild Lauf Rate für ein Monatskalender-Steuerelement ab.

```
int GetMonthDelta() const;
```

### <a name="return-value"></a>Rückgabewert

Die Scrollrate für das Monatskalender-Steuerelement. Die Scrollrate entspricht der Anzahl von Monaten, die das Steuerelement seine Anzeige verschiebt, wenn der Benutzer einmal auf eine Bild Lauf Schaltfläche klickt.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [MCM_GETMONTHDELTA](/windows/win32/Controls/mcm-getmonthdelta), wie in der Windows SDK beschrieben.

## <a name="cmonthcalctrlgetmonthrange"></a><a name="getmonthrange"></a> CMonthCalCtrl:: getmonthrange

Ruft Datumsinformationen ab, die die hohen und unteren Grenzen der Anzeige eines Monatskalender-Steuer Elements darstellen.

```
int GetMonthRange(
    COleDateTime& refMinRange,
    COleDateTime& refMaxRange,
    DWORD dwFlags) const;

int GetMonthRange(
    CTime& refMinRange,
    CTime& refMaxRange,
    DWORD dwFlags) const;

int GetMonthRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange,
    DWORD dwFlags) const;
```

### <a name="parameters"></a>Parameter

*Ref-Bereich*<br/>
Ein Verweis auf ein [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -oder [ctime](../../atl-mfc-shared/reference/ctime-class.md) -Objekt, das das minimal zulässige Datum enthält.

*Ref maxrange*<br/>
Ein Verweis auf ein `COleDateTime` - `CTime` Objekt oder-Objekt, das das maximal zulässige Datum enthält.

*pminrange*<br/>
Ein Zeiger auf eine [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) -Struktur, die das Datum am niedrigsten Ende des Bereichs enthält.

*pmaxrange*<br/>
Ein Zeiger auf eine- `SYSTEMTIME` Struktur, die das Datum am höchsten Ende des Bereichs enthält.

*dwFlags*<br/>
-Wert, der den Gültigkeitsbereich der abzurufenden Bereichs Begrenzungen angibt. Dieser Wert muss einer der folgenden Werte sein.

|Wert|Bedeutung|
|-----------|-------------|
|GMR_DAYSTATE|Schließt vorangestellte und nachfolgende Monate des sichtbaren Bereichs ein, die nur teilweise angezeigt werden.|
|GMR_VISIBLE|Schließen Sie nur die Monate ein, die vollständig angezeigt werden.|

### <a name="return-value"></a>Rückgabewert

Eine ganze Zahl, die den Bereich in Monaten darstellt, über den die beiden von *reberminrange* und *ref maxrange* in der ersten und zweiten Version oder *pminrange* und *pmaxrange* in der dritten Version festgelegten Grenzwerte liegen.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [MCM_GETMONTHRANGE](/windows/win32/Controls/mcm-getmonthrange), wie in der Windows SDK beschrieben. In der MFC-Implementierung von `GetMonthRange` können Sie `COleDateTime` Verwendungs-, Verwendungs- `CTime` oder `SYSTEMTIME` Struktur Verwendung angeben.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMonthCalCtrl:: SetDayState](#setdaystate).

## <a name="cmonthcalctrlgetrange"></a><a name="getrange"></a> CMonthCalCtrl:: GetRange

Ruft das aktuelle Mindest-und maximal Datum ab, das in einem Monatskalender-Steuerelement festgelegt ist.

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;

DWORD GetRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange) const;
```

### <a name="parameters"></a>Parameter

*pminrange*<br/>
Ein Zeiger auf ein- `COleDateTime` Objekt, ein- `CTime` Objekt oder eine [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) -Struktur, die das Datum am niedrigsten Ende des Bereichs enthält.

*pmaxrange*<br/>
Ein Zeiger auf ein- `COleDateTime` Objekt, ein- `CTime` Objekt oder eine [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) -Struktur, die das Datum am höchsten Ende des Bereichs enthält.

### <a name="return-value"></a>Rückgabewert

Ein DWORD, das 0 (null) (keine Limits) oder eine Kombination der folgenden Werte sein kann, die Informationen zum Grenzwert angeben.

|Wert|Bedeutung|
|-----------|-------------|
|GDTR_MAX|Für das Steuerelement ist eine Obergrenze festgelegt. *pmaxrange* ist gültig und enthält die anwendbaren Datumsinformationen.|
|GDTR_MIN|Für das Steuerelement ist ein minimal Grenzwert festgelegt. *pminrange* ist gültig und enthält die anwendbaren Datumsinformationen.|

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [MCM_GETRANGE](/windows/win32/Controls/mcm-getrange), wie in der Windows SDK beschrieben. In der MFC-Implementierung von `GetRange` können Sie eine Verwendungs- `COleDateTime` , Verwendungs- `CTime` oder `SYSTEMTIME` Struktur Verwendung angeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]

## <a name="cmonthcalctrlgetselrange"></a><a name="getselrange"></a> CMonthCalCtrl:: getselrange

Ruft Datumsinformationen ab, die die obere und untere Grenze des Datums Bereichs darstellen, der derzeit vom Benutzer ausgewählt wird.

```
BOOL GetSelRange(
    COleDateTime& refMinRange,
    COleDateTime& refMaxRange) const;

BOOL GetSelRange(
    CTime& refMinRange,
    CTime& refMaxRange) const;

BOOL GetSelRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange) const;
```

### <a name="parameters"></a>Parameter

*Ref-Bereich*<br/>
Ein Verweis auf ein [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -oder [ctime](../../atl-mfc-shared/reference/ctime-class.md) -Objekt, das das minimal zulässige Datum enthält.

*Ref maxrange*<br/>
Ein Verweis auf ein `COleDateTime` - `CTime` Objekt oder-Objekt, das das maximal zulässige Datum enthält.

*pminrange*<br/>
Ein Zeiger auf eine [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) -Struktur, die das Datum am niedrigsten Ende des Bereichs enthält.

*pmaxrange*<br/>
Ein Zeiger auf eine- `SYSTEMTIME` Struktur, die das Datum am höchsten Ende des Bereichs enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [MCM_GETSELRANGE](/windows/win32/Controls/mcm-getselrange), wie in der Windows SDK beschrieben. `GetSelRange` schlägt fehl, wenn Sie auf ein Monatskalender-Steuerelement angewendet wird, das den MCS_MULTISELECT Stil nicht verwendet.

In der MFC-Implementierung von `GetSelRange` können Sie `COleDateTime` Verwendungs-, Verwendungs- `CTime` oder `SYSTEMTIME` Struktur Verwendung angeben.

## <a name="cmonthcalctrlgettoday"></a><a name="gettoday"></a> CMonthCalCtrl:: gettoday

Ruft die Datumsinformationen für das als "heute" angegebene Datum für ein Monatskalender-Steuerelement ab.

```
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;

BOOL GetToday(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Parameter

*Ref DateTime*<br/>
Ein Verweis auf ein [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -oder [ctime](../../atl-mfc-shared/reference/ctime-class.md) -Objekt, das den aktuellen Tag angibt.

*pdatetime*<br/>
Ein Zeiger auf eine [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) -Struktur, die die Datumsinformationen empfängt. Dieser Parameter muss eine gültige Adresse sein und darf nicht NULL sein.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [MCM_GETTODAY](/windows/win32/Controls/mcm-gettoday), wie in der Windows SDK beschrieben. In der MFC-Implementierung von `GetToday` können Sie eine Verwendungs- `COleDateTime` , Verwendungs- `CTime` oder `SYSTEMTIME` Struktur Verwendung angeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]

## <a name="cmonthcalctrlhittest"></a><a name="hittest"></a> CMonthCalCtrl:: HitTest

Bestimmt, welches Monatskalender-Steuerelement, sofern vorhanden, an einer angegebenen Position liegt.

```
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```

### <a name="parameters"></a>Parameter

*pMCHitTest*<br/>
Ein Zeiger auf eine [MCHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-mchittestinfo) -Struktur mit Treffer Testpunkten für das Monatskalender-Steuerelement.

### <a name="return-value"></a>Rückgabewert

Ein DWORD-Wert. Entspricht dem **uhit** -Member der- `MCHITTESTINFO` Struktur.

### <a name="remarks"></a>Bemerkungen

`HitTest` verwendet die- `MCHITTESTINFO` Struktur, die Informationen über den Treffer Test enthält.

## <a name="cmonthcalctrliscenturyview"></a><a name="iscenturyview"></a> CMonthCalCtrl:: iscenturyview

Gibt an, ob die aktuelle Ansicht des Kalender Steuer Elements des aktuellen Monats die Jahrhundert Ansicht ist.

```
BOOL IsCenturyView() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die aktuelle Ansicht die Jahrhundert Ansicht ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) Nachricht, die in der Windows SDK beschrieben wird. Wenn diese Meldung MCMV_CENTURY zurückgibt, gibt diese Methode true zurück.

## <a name="cmonthcalctrlisdecadeview"></a><a name="isdecadeview"></a> CMonthCalCtrl:: isdecadeview

Gibt an, ob die aktuelle Ansicht des Kalender Steuer Elements des aktuellen Monats die Dekade-Ansicht ist.

```
BOOL IsDecadeView() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die aktuelle Ansicht die Dekade-Ansicht ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) Nachricht, die in der Windows SDK beschrieben wird. Wenn diese Meldung MCMV_DECADE zurückgibt, gibt diese Methode true zurück.

## <a name="cmonthcalctrlismonthview"></a><a name="ismonthview"></a> CMonthCalCtrl:: ismonthview

Gibt an, ob die aktuelle Ansicht des Kalender Steuer Elements des aktuellen Monats die Monatsansicht ist.

```
BOOL IsMonthView() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die aktuelle Ansicht die Monatsansicht ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) Nachricht, die in der Windows SDK beschrieben wird. Wenn diese Meldung MCMV_MONTH zurückgibt, gibt diese Methode true zurück.

## <a name="cmonthcalctrlisyearview"></a><a name="isyearview"></a> CMonthCalCtrl:: isyearview

Gibt an, ob die aktuelle Ansicht des Kalender Steuer Elements des aktuellen Monats die Jahr Ansicht ist.

```
BOOL IsYearView() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die aktuelle Ansicht die Jahr Ansicht ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) Nachricht, die in der Windows SDK beschrieben wird. Wenn diese Meldung MCMV_YEAR zurückgibt, gibt diese Methode true zurück.

## <a name="cmonthcalctrlsetcalendarborder"></a><a name="setcalendarborder"></a> CMonthCalCtrl:: setcalendarborder

Legt die Breite des Rahmens des Kalender Steuer Elements des aktuellen Monats fest.

```cpp
void SetCalendarBorder(int cxyBorder);
```

### <a name="parameters"></a>Parameter

*cxyborder*\
in Die Breite des Rahmens in Pixel.

### <a name="remarks"></a>Bemerkungen

Wenn diese Methode erfolgreich ist, wird die Rahmenbreite auf den *cxyborder* -Parameter festgelegt. Andernfalls wird die Rahmenbreite auf den Standardwert zurückgesetzt, der durch das aktuelle Design angegeben wird, oder 0 (NULL [), wenn](/windows/win32/Controls/visual-styles-overview)keine Designs verwendet werden.

Diese Methode sendet die [MCM_SETCALENDARBORDER](/windows/win32/Controls/mcm-setcalendarborder) Nachricht, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die-Variable definiert, die `m_monthCalCtrl` für den programmgesteuerten Zugriff auf das Month Calendar-Steuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die Rahmenbreite des Monatskalender-Steuer Elements auf acht Pixel festgelegt. Verwenden Sie die [CMonthCalCtrl:: getcalendarborder](#getcalendarborder) -Methode, um zu bestimmen, ob diese Methode erfolgreich ausgeführt wurde.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]

## <a name="cmonthcalctrlsetcalendarborderdefault"></a><a name="setcalendarborderdefault"></a> CMonthCalCtrl:: setcalendarborderdefault

Legt die Standardbreite des Rahmens des Kalender Steuer Elements des aktuellen Monats fest.

```cpp
void SetCalendarBorderDefault();
```

### <a name="remarks"></a>Bemerkungen

Die Rahmenbreite wird auf den Standardwert festgelegt, der durch [das aktuelle Design angegeben wird,](/windows/win32/Controls/visual-styles-overview)oder 0 (null), wenn keine Designs verwendet werden.

Diese Methode sendet die [MCM_SETCALENDARBORDER](/windows/win32/Controls/mcm-setcalendarborder) Nachricht, die in der Windows SDK beschrieben wird.

## <a name="cmonthcalctrlsetcalid"></a><a name="setcalid"></a> CMonthCalCtrl:: setcalid

Legt den Kalender Bezeichner für das Kalender Steuerelement des aktuellen Monats fest.

```
BOOL SetCalID(CALID calid);
```

### <a name="parameters"></a>Parameter

*Calid*\
in Eine der [kalenderbezeichnerkonstanten](/windows/win32/Intl/calendar-identifiers) .

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Ein Kalender Bezeichner gibt einen regionsspezifischen Kalender an, z. b. die gregorianischen (lokalisierten), japanischen oder Hijri-Kalender. Verwenden Sie die- `SetCalID` Methode, um einen Kalender anzuzeigen, der durch den Parameter " *Calid* " angegeben wird, wenn das Gebiets Schema, das den Kalender enthält, auf dem Computer installiert ist.

Diese Methode sendet die [MCM_SETCALID](/windows/win32/Controls/mcm-setcalid) Nachricht, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die-Variable definiert, die `m_monthCalCtrl` für den programmgesteuerten Zugriff auf das Month Calendar-Steuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird das Monatskalender-Steuerelement für die Anzeige des japanischen Kaiserzeit Kalenders festgelegt. Die `SetCalID` Methode ist nur erfolgreich, wenn der Kalender auf dem Computer installiert ist.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]

## <a name="cmonthcalctrlsetcenturyview"></a><a name="setcenturyview"></a> CMonthCalCtrl:: setcenturyview

Legt das Kalender Steuerelement für den aktuellen Monat fest, um die Jahrhundert Ansicht anzuzeigen.

```
BOOL SetCenturyView();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet die [CMonthCalCtrl:: SetCurrentView](#setcurrentview) -Methode, um die Ansicht auf festzulegen `MCMV_CENTURY` , die die Jahrhundert Ansicht darstellt.

## <a name="cmonthcalctrlsetcolor"></a><a name="setcolor"></a> CMonthCalCtrl:: setColor

Legt die Farbe eines angegebenen Bereichs eines Monatskalender-Steuer Elements fest.

```
COLORREF SetColor(
    int nRegion,
    COLORREF ref);
```

### <a name="parameters"></a>Parameter

*nregion*<br/>
Ein ganzzahliger Wert, der die festzulegende Monatskalender Farbe angibt. Dieser Wert kann einer der folgenden Werte sein:

|Wert|Bedeutung|
|-----------|-------------|
|MCSC_BACKGROUND|Die zwischen Monaten angezeigte Hintergrundfarbe.|
|MCSC_MONTHBK|Die im Monat angezeigte Hintergrundfarbe.|
|MCSC_TEXT|Die Farbe, die verwendet wird, um Text innerhalb eines Monats anzuzeigen.|
|MCSC_TITLEBK|Die im Titel des Kalenders angezeigte Hintergrundfarbe.|
|MCSC_TITLETEXT|Die Farbe, die verwendet wird, um Text innerhalb des Kalender Titels anzuzeigen.|
|MCSC_TRAILINGTEXT|Die Farbe, die verwendet wird, um den Header und den nachfolgenden tagtext anzuzeigen. Header und nachfolgende Tage sind die Tage aus den vorherigen und den nächsten Monaten, die im aktuellen Kalender angezeigt werden.|

*ref*<br/>
Ein COLORREF-Wert für die neue Farbeinstellung für den angegebenen Teil des Monatskalender-Steuer Elements.

### <a name="return-value"></a>Rückgabewert

Ein COLORREF-Wert, der die vorherige Farbeinstellung für den angegebenen Teil des Monatskalender-Steuer Elements darstellt, falls erfolgreich. Andernfalls gibt diese Meldung-1 zurück.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [MCM_SETCOLOR](/windows/win32/Controls/mcm-setcolor), wie in der Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]

## <a name="cmonthcalctrlsetcurrentview"></a><a name="setcurrentview"></a> CMonthCalCtrl:: SetCurrentView

Legt das Kalender Steuerelement für den aktuellen Monat fest, um die angegebene Ansicht anzuzeigen.

```
BOOL SetCurrentView(DWORD dwNewView);
```

### <a name="parameters"></a>Parameter

*dwnewview*\
in Einer der folgenden-Werte, der eine monatliche, Jahres-, Jahrzehnt-oder Jahrhundert Ansicht angibt.

- `MCMV_MONTH`: Monatliche Ansicht
- `MCMV_YEAR`: Jährliche Ansicht
- `MCMV_DECADE`: Dekade-Ansicht
- `MCMV_CENTURY`: Jahrhundert Ansicht

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [MCM_SETCURRENTVIEW](/windows/win32/Controls/mcm-setcurrentview) Nachricht, die in der Windows SDK beschrieben wird.

## <a name="cmonthcalctrlsetcursel"></a><a name="setcursel"></a> CMonthCalCtrl:: setcurrsel

Legt das aktuell ausgewählte Datum für ein Monatskalender-Steuerelement fest.

```
BOOL SetCurSel(const COleDateTime& refDateTime);
BOOL SetCurSel(const CTime& refDateTime);
BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Parameter

*Ref DateTime*<br/>
Ein Verweis auf ein [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -oder [ctime](../../atl-mfc-shared/reference/ctime-class.md) -Objekt, das das derzeit ausgewählte Monatskalender-Steuerelement angibt.

*pdatetime*<br/>
Ein Zeiger auf eine [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) -Struktur, die das Datum enthält, das als aktuelle Auswahl festgelegt werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [MCM_SETCURSEL](/windows/win32/Controls/mcm-setcursel), wie in der Windows SDK beschrieben. In der MFC-Implementierung von `SetCurSel` können Sie eine Verwendungs- `COleDateTime` , Verwendungs- `CTime` oder `SYSTEMTIME` Struktur Verwendung angeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]

## <a name="cmonthcalctrlsetdaystate"></a><a name="setdaystate"></a> CMonthCalCtrl:: SetDayState

Legt die Anzeige für Tage in einem Monatskalender-Steuerelement fest.

```
BOOL SetDayState(
    int nMonths,
    LPMONTHDAYSTATE pStates);
```

### <a name="parameters"></a>Parameter

*nmonate*<br/>
Ein Wert, der angibt, wie viele Elemente im Array sind, auf das *pstates* zeigt.

*pstates*<br/>
Ein Zeiger auf ein [MONTHDAYSTATE](/windows/win32/Controls/monthdaystate) -Array von Werten, die definieren, wie das Monatskalender-Steuerelement jeden Tag in der Anzeige zeichnen wird. Der MONTHDAYSTATE-Datentyp ist ein Bitfeld, bei dem jedes Bit (1 bis 31) den Status eines Tags in einem Monat darstellt. Wenn ein Bit ist, wird der entsprechende Tag fett angezeigt. Andernfalls wird Sie ohne Betonung angezeigt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [MCM_SETDAYSTATE](/windows/win32/Controls/mcm-setdaystate), wie in der Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]

## <a name="cmonthcalctrlsetdecadeview"></a><a name="setdecadeview"></a> CMonthCalCtrl:: setdecadeview

Legt das Kalender Steuerelement des aktuellen Monats auf die Dekade-Ansicht fest.

```
BOOL SetDecadeView();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet die [CMonthCalCtrl:: SetCurrentView](#setcurrentview) -Methode, um die Ansicht auf festzulegen `MCMV_DECADE` , was die Dekade-Ansicht darstellt.

## <a name="cmonthcalctrlsetfirstdayofweek"></a><a name="setfirstdayofweek"></a> CMonthCalCtrl:: setfirstdayof-Woche

Legt den Wochentag fest, der in der Spalte ganz links des Kalenders angezeigt werden soll.

```
BOOL SetFirstDayOfWeek(
    int iDay,
    int* lpnOld = NULL);
```

### <a name="parameters"></a>Parameter

*iDay*<br/>
Ein ganzzahliger Wert, der angibt, welcher Tag als erster Tag der Woche festgelegt werden soll. Dieser Wert muss einer der Tages Zahlen sein. Eine Beschreibung der Tages Zahlen finden Sie unter [getfirstdayosweek](#getfirstdayofweek) .

*lpnold*<br/>
Ein Zeiger auf eine ganze Zahl, die den ersten Tag der Woche angibt, der zuvor festgelegt wurde.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn der vorherige erste Tag der Woche auf einen anderen Wert als LOCALE_IFIRSTDAYOFWEEK festgelegt ist. Dies ist der Tag, der in der System Steuerungs Einstellung angegeben wird. Andernfalls gibt diese Funktion 0 zurück.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [MCM_SETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-setfirstdayofweek), wie in der Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]

## <a name="cmonthcalctrlsetmaxselcount"></a><a name="setmaxselcount"></a> CMonthCalCtrl:: setmaxselcount

Legt die maximale Anzahl von Tagen fest, die in einem Monatskalender-Steuerelement ausgewählt werden können.

```
BOOL SetMaxSelCount(int nMax);
```

### <a name="parameters"></a>Parameter

*nMax*<br/>
Der Wert, der festgelegt wird, um die maximale Anzahl auswählbarer Tage darzustellen.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [MCM_SETMAXSELCOUNT](/windows/win32/Controls/mcm-setmaxselcount), wie in der Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]

## <a name="cmonthcalctrlsetmonthdelta"></a><a name="setmonthdelta"></a> CMonthCalCtrl:: setmonthdelta

Legt die Bild Lauf Rate für ein Monatskalender-Steuerelement fest.

```
int SetMonthDelta(int iDelta);
```

### <a name="parameters"></a>Parameter

*iDelta*<br/>
Die Anzahl der Monate, die als Bild Lauf Rate des-Steuer Elements festgelegt werden sollen. Wenn dieser Wert 0 (null) ist, wird der Monat Delta auf den Standardwert zurückgesetzt. Dies ist die Anzahl der Monate, die im Steuerelement angezeigt werden.

### <a name="return-value"></a>Rückgabewert

Die vorherige Scrollrate. Wenn die Scrollrate zuvor nicht festgelegt wurde, ist der Rückgabewert 0.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [MCM_SETMONTHDELTA](/windows/win32/Controls/mcm-setmonthdelta), wie in der Windows SDK beschrieben.

## <a name="cmonthcalctrlsetmonthview"></a><a name="setmonthview"></a> CMonthCalCtrl:: setmonthview

Legt das Kalender Steuerelement des aktuellen Monats zum Anzeigen der Monatsansicht fest.

```
BOOL SetMonthView();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet die [CMonthCalCtrl:: SetCurrentView](#setcurrentview) -Methode, um die Ansicht auf MCMV_MONTH festzulegen, der die Monatsansicht darstellt.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die-Variable definiert, die `m_monthCalCtrl` für den programmgesteuerten Zugriff auf das Month Calendar-Steuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird das Monatskalender-Steuerelement so festgelegt, dass die Ansichten month, year, Decade und Jahrhundert angezeigt werden.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]

## <a name="cmonthcalctrlsetrange"></a><a name="setrange"></a> CMonthCalCtrl:: abge

Legt das minimal-und maximal zulässige Datum für ein Monatskalender-Steuerelement fest.

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);

BOOL SetRange(
    const LPSYSTEMTIME pMinRange,
    const LPSYSTEMTIME pMaxRange);
```

### <a name="parameters"></a>Parameter

*pminrange*<br/>
Ein Zeiger auf ein- `COleDateTime` Objekt, ein- `CTime` Objekt oder eine [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) -Struktur, die das Datum am niedrigsten Ende des Bereichs enthält.

*pmaxrange*<br/>
Ein Zeiger auf ein- `COleDateTime` Objekt, ein- `CTime` Objekt oder eine-Struktur, `SYSTEMTIME` die das Datum am höchsten Ende des Bereichs enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [MCM_SETRANGE](/windows/win32/Controls/mcm-setrange), wie in der Windows SDK beschrieben. In der MFC-Implementierung von `SetRange` können Sie `COleDateTime` Verwendungs-, Verwendungs- `CTime` oder `SYSTEMTIME` Struktur Verwendung angeben.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMonthCalCtrl:: GetRange](#getrange).

## <a name="cmonthcalctrlsetselrange"></a><a name="setselrange"></a> CMonthCalCtrl:: setselrange

Legt die Auswahl für ein Monatskalender-Steuerelement auf einen bestimmten Datumsbereich fest.

```
BOOL SetSelRange(
    const COleDateTime& pMinRange,
    const COleDateTime& pMaxRange);

BOOL SetSelRange(
    const CTime& pMinRange,
    const CTime& pMaxRange);

BOOL SetSelRange(
    const LPSYSTEMTIME pMinRange,
    const LPSYSTEMTIME pMaxRange);
```

### <a name="parameters"></a>Parameter

*pminrange*<br/>
Ein Zeiger auf ein- `COleDateTime` Objekt, ein- `CTime` Objekt oder eine [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) -Struktur, die das Datum am niedrigsten Ende des Bereichs enthält.

*pmaxrange*<br/>
Ein Zeiger auf ein- `COleDateTime` Objekt, ein- `CTime` Objekt oder eine-Struktur, `SYSTEMTIME` die das Datum am höchsten Ende des Bereichs enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [MCM_SETSELRANGE](/windows/win32/Controls/mcm-setselrange), wie in der Windows SDK beschrieben. In der MFC-Implementierung von `SetSelRange` können Sie `COleDateTime` Verwendungs-, Verwendungs- `CTime` oder `SYSTEMTIME` Struktur Verwendung angeben.

## <a name="cmonthcalctrlsettoday"></a><a name="settoday"></a> CMonthCalCtrl:: settoday

Legt das Kalender Steuerelement für den aktuellen Tag fest.

```cpp
void SetToday(const COleDateTime& refDateTime);
void SetToday(const CTime* pDateTime);
void SetToday(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Parameter

*Ref DateTime*<br/>
Ein Verweis auf ein [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -Objekt, das das aktuelle Datum enthält.

*pdatetime*<br/>
In der zweiten Version ein Zeiger auf ein [ctime](../../atl-mfc-shared/reference/ctime-class.md) -Objekt, das die aktuellen Datumsinformationen enthält. In der dritten Version ein Zeiger auf eine [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) -Struktur, die die aktuellen Datumsinformationen enthält.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [MCM_SETTODAY](/windows/win32/Controls/mcm-settoday), wie in der Windows SDK beschrieben.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CMonthCalCtrl:: gettoday](#gettoday).

## <a name="cmonthcalctrlsetyearview"></a><a name="setyearview"></a> CMonthCalCtrl:: setyearview

Legt das Kalender Steuerelement des aktuellen Monats auf die Year-Ansicht fest.

```
BOOL SetYearView();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet die [CMonthCalCtrl:: SetCurrentView](#setcurrentview) -Methode, um die Ansicht auf MCMV_YEAR festzulegen, der die jährliche Ansicht darstellt.

## <a name="cmonthcalctrlsizeminreq"></a><a name="sizeminreq"></a> CMonthCalCtrl:: sizeminreq

Zeigt das Monatskalender-Steuerelement mit der minimalen Größe an, die einen Monat anzeigt.

```
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```

### <a name="parameters"></a>Parameter

*brepaint*<br/>
Gibt an, ob das Steuerelement neu gezeichnet werden soll. Standardmäßig ist der Wert true. FALSE gibt an, dass kein Neuzeichnen auftritt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Monatskalender-Steuerelement auf das Minimalwert vergrößert wird andernfalls 0.

### <a name="remarks"></a>Bemerkungen

`SizeMinReq`Beim Aufrufen von wird das gesamte Monatskalender-Steuerelement für den Kalender eines Monats angezeigt.

## <a name="cmonthcalctrlsizerecttomin"></a><a name="sizerecttomin"></a> CMonthCalCtrl:: sizerecttomin

Berechnet für das Kalender Steuerelement des aktuellen Monats das kleinste Rechteck, das alle Kalender enthalten kann, die in ein angegebenes Rechteck passen.

```
LPRECT SizeRectToMin(LPRECT lpRect);
```

### <a name="parameters"></a>Parameter

*lprect*\
in Ein Zeiger auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur, die ein Rechteck definiert, das die gewünschte Anzahl von Kalendern enthält.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur, die ein Rechteck definiert, dessen Größe kleiner oder gleich dem Rechteck ist, das durch den *lprect* -Parameter definiert wird.

### <a name="remarks"></a>Bemerkungen

Diese Methode berechnet, wie viele Kalender in das durch den *lprect* -Parameter angegebene Rechteck passen und gibt dann das kleinste Rechteck zurück, das die Anzahl der Kalender enthalten kann. Tatsächlich verkleinert diese Methode das angegebene Rechteck, sodass es exakt der gewünschten Anzahl von Kalendern entspricht.

Diese Methode sendet die [MCM_SIZERECTTOMIN](/windows/win32/Controls/mcm-sizerecttomin) Nachricht, die in der Windows SDK beschrieben wird.

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CDateTimeCtrl-Klasse](../../mfc/reference/cdatetimectrl-class.md)
