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
ms.openlocfilehash: 8c24c638d7006be112a53ec1e4f622ad528e348c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752817"
---
# <a name="cmonthcalctrl-class"></a>CMonthCalCtrl-Klasse

Kapselt die Funktionalität eines Monatskalender-Steuerelements.

## <a name="syntax"></a>Syntax

```
class CMonthCalCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMonthCalCtrl::CMonthCalCtrl](#cmonthcalctrl)|Erstellt ein `CMonthCalCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMonthCalCtrl::Erstellen](#create)|Erstellt ein Monatskalendersteuerelement und fügt `CMonthCalCtrl` es an das Objekt an.|
|[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)|Ruft die Breite des Rahmens des aktuellen Monatskalendersteuerelements ab.|
|[CMonthCalCtrl::GetCalendarCount](#getcalendarcount)|Ruft die Anzahl der Kalender ab, die im aktuellen Monatskalendersteuerelement angezeigt werden.|
|[CMonthCalCtrl::GetCalendarGridInfo](#getcalendargridinfo)|Ruft Informationen zum aktuellen Monatskalendersteuerelement ab.|
|[CMonthCalCtrl::GetCalID](#getcalid)|Ruft den Kalenderbezeichner für das aktuelle Monatskalendersteuerelement ab.|
|[CMonthCalCtrl::GetColor](#getcolor)|Ruft die Farbe eines angegebenen Bereichs eines Monatskalendersteuerelements ab.|
|[CMonthCalCtrl::GetCurrentView](#getcurrentview)|Ruft die Ansicht ab, die derzeit vom aktuellen Monatskalendersteuerelement angezeigt wird.|
|[CMonthCalCtrl::GetCurSel](#getcursel)|Ruft die Systemzeit ab, die durch das aktuell ausgewählte Datum angegeben wird.|
|[CMonthCalCtrl::GetFirstDayOfWeek](#getfirstdayofweek)|Ruft den ersten Tag der Woche ab, der in der linken Spalte des Kalenders angezeigt wird.|
|[CMonthCalCtrl::GetMaxSelCount](#getmaxselcount)|Ruft die aktuelle maximale Anzahl von Tagen ab, die in einem Monatskalendersteuerelement ausgewählt werden können.|
|[CMonthCalCtrl::GetMaxTodayWidth](#getmaxtodaywidth)|Ruft die maximale Breite der Zeichenfolge "Heute" für das aktuelle Monatskalendersteuerelement ab.|
|[CMonthCalCtrl::GetMinReqRect](#getminreqrect)|Ruft die Mindestgröße ab, die erforderlich ist, um einen vollständigen Monat in einem Monatskalendersteuerelement anzuzeigen.|
|[CMonthCalCtrl::GetMonthDelta](#getmonthdelta)|Ruft die Bildlaufrate für ein Monatskalendersteuerelement ab.|
|[CMonthCalCtrl::GetMonthRange](#getmonthrange)|Ruft Datumsinformationen ab, die die anzeige der hohen und niedrigen Grenzwerte eines Monatskalendersteuerelements darstellen.|
|[CMonthCalCtrl::GetRange](#getrange)|Ruft die aktuellen minimalen und maximalen Datumsangaben ab, die in einem Monatskalendersteuerelement festgelegt sind.|
|[CMonthCalCtrl::GetSelRange](#getselrange)|Ruft Datumsinformationen ab, die die oberen und unteren Grenzwerte des datumsbereichs darstellen, der derzeit vom Benutzer ausgewählt wurde.|
|[CMonthCalCtrl::GetToday](#gettoday)|Ruft die Datumsinformationen für das datum ab, das als "heute" für ein Monatskalendersteuerelement angegeben ist.|
|[CMonthCalCtrl::HitTest](#hittest)|Bestimmt, welcher Abschnitt eines Monatskalendersteuerelements sich an einem bestimmten Punkt auf dem Bildschirm befindet.|
|[CMonthCalCtrl::IsCenturyView](#iscenturyview)|Gibt an, ob die aktuelle Ansicht des aktuellen Monatskalendersteuerelements die Jahrhundertansicht ist.|
|[CMonthCalCtrl::IsDecadeView](#isdecadeview)|Gibt an, ob die aktuelle Ansicht des aktuellen Monatskalendersteuerelements die Dekadenansicht ist.|
|[CMonthCalCtrl::IsMonthView](#ismonthview)|Gibt an, ob die aktuelle Ansicht des aktuellen Monatskalendersteuerelements die Monatsansicht ist.|
|[CMonthCalCtrl::IsYearView](#isyearview)|Gibt an, ob die aktuelle Ansicht des aktuellen Monatskalendersteuerelements die Jahresansicht ist.|
|[CMonthCalCtrl::SetCalendarBorder](#setcalendarborder)|Legt die Breite des Rahmens des aktuellen Monatskalendersteuerelements fest.|
|[CMonthCalCtrl::SetCalendarBorderDefault](#setcalendarborderdefault)|Legt die Standardbreite des Rahmens des aktuellen Monatskalendersteuerelements fest.|
|[CMonthCalCtrl::SetCalID](#setcalid)|Legt den Kalenderbezeichner für das aktuelle Monatskalendersteuerelement fest.|
|[CMonthCalCtrl::SetCenturyView](#setcenturyview)|Legt das aktuelle Monatskalendersteuerelement so fest, dass die Jahrhundertansicht angezeigt wird.|
|[CMonthCalCtrl::SetColor](#setcolor)|Legt die Farbe eines angegebenen Bereichs eines Monatskalendersteuerelements fest.|
|[CMonthCalCtrl::SetCurrentView](#setcurrentview)|Legt das aktuelle Monatskalendersteuerelement so fest, dass die angegebene Ansicht angezeigt wird.|
|[CMonthCalCtrl::SetCurSel](#setcursel)|Legt das aktuell ausgewählte Datum für ein Monatskalendersteuerelement fest.|
|[CMonthCalCtrl::SetDayState](#setdaystate)|Legt die Anzeige für Tage in einem Monatskalendersteuerelement fest.|
|[CMonthCalCtrl::SetDecadeView](#setdecadeview)|Legt das aktuelle Monatskalendersteuerelement auf die Dekadenansicht fest.|
|[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)|Legt den Wochentag fest, der in der linken Spalte des Kalenders angezeigt werden soll.|
|[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)|Legt die maximale Anzahl von Tagen fest, die in einem Monatskalendersteuerelement ausgewählt werden können.|
|[CMonthCalCtrl::SetMonthDelta](#setmonthdelta)|Legt die Bildlaufrate für ein Monatskalendersteuerelement fest.|
|[CMonthCalCtrl::SetMonthView](#setmonthview)|Legt das aktuelle Monatskalendersteuerelement so fest, dass die Monatsansicht angezeigt wird.|
|[CMonthCalCtrl::SetRange](#setrange)|Legt die minimalen und maximal zulässigen Datumsangaben für ein Monatskalendersteuerelement fest.|
|[CMonthCalCtrl::SetSelRange](#setselrange)|Legt die Auswahl für ein Monatskalendersteuerelement auf einen bestimmten Datumsbereich fest.|
|[CMonthCalCtrl::SetToday](#settoday)|Legt das Kalendersteuerelement für den aktuellen Tag fest.|
|[CMonthCalCtrl::SetYearView](#setyearview)|Legt das aktuelle Monatskalendersteuerelement auf die Jahresansicht fest.|
|[CMonthCalCtrl::SizeMinReq](#sizeminreq)|Malt das Monatskalendersteuerelement auf seine Mindestgröße von einem Monat neu.|
|[CMonthCalCtrl::SizeRectToMin](#sizerecttomin)|Berechnet für das aktuelle Monatskalendersteuerelement das kleinste Rechteck, das alle Kalender enthalten kann, die in ein angegebenes Rechteck passen.|

## <a name="remarks"></a>Bemerkungen

Das Monatskalendersteuerelement stellt dem Benutzer eine einfache Kalenderoberfläche zur Verfügung, aus der der Benutzer ein Datum auswählen kann. Der Benutzer kann die Anzeige ändern, indem er:

- Scrollen Sie rückwärts und vorwärts, von Monat zu Monat.

- Klicken Sie auf den Text Heute, um den aktuellen Tag anzuzeigen (wenn der MCS_NOTODAY Stil nicht verwendet wird).

- Auswählen eines Monats oder Jahres aus einem Popup-Menü.

Sie können das Monatskalendersteuerelement anpassen, indem Sie beim Erstellen eine Vielzahl von Formatvorlagen auf das Objekt anwenden. Diese Stile werden in [Monatskalendersteuerungsstilen](/windows/win32/Controls/month-calendar-control-styles) im Windows SDK beschrieben.

Das Monatskalendersteuerelement kann mehr als einen Monat anzeigen und spezielle Tage (z. B. Feiertage) anzeigen, indem das Datum fett gefettt wird.

Weitere Informationen zur Verwendung des Monatskalendersteuerelements finden Sie unter [Verwenden von CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CMonthCalCtrl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxdtctl.h

## <a name="cmonthcalctrlcmonthcalctrl"></a><a name="cmonthcalctrl"></a>CMonthCalCtrl::CMonthCalCtrl

Erstellt ein `CMonthCalCtrl`-Objekt.

```
CMonthCalCtrl();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen `Create` aufrufen, nachdem Sie das Objekt erstellt haben.

## <a name="cmonthcalctrlcreate"></a><a name="create"></a>CMonthCalCtrl::Erstellen

Erstellt ein Monatskalendersteuerelement und fügt `CMonthCalCtrl` es an das Objekt an.

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

*dwStyle*<br/>
Gibt die Kombination von Windows-Formatvorlagen an, die auf das Monatskalendersteuerelement angewendet werden. Weitere Informationen zu den Stilen finden Sie unter [Monatskalendersteuerungsstile](/windows/win32/Controls/month-calendar-control-styles) im Windows SDK.

*Rect*<br/>
Ein Verweis auf eine [RECT-Struktur.](/windows/win32/api/windef/ns-windef-rect) Enthält die Position und Größe des Monatskalendersteuerelements.

*Pt*<br/>
Ein Verweis [POINT](/windows/win32/api/windef/ns-windef-point) auf eine POINT-Struktur, die die Position des Monatskalendersteuerelements identifiziert.

*pParentWnd*<br/>
Ein Zeiger auf ein [CWnd-Objekt,](../../mfc/reference/cwnd-class.md) das das übergeordnete Fenster des Monatskalendersteuerelements ist. Es darf nicht NULL sein.

*nID*<br/>
Gibt die Steuerelement-ID des Monatskalendersteuerelements an.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Initialisierung erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Erstellen Sie ein Monatskalendersteuerelement in zwei Schritten:

1. Rufen Sie [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) auf, um ein `CMonthCalCtrl` Objekt zu erstellen.

1. Rufen Sie diese Memberfunktion auf, die ein Monatskalendersteuerelement erstellt und an das `CMonthCalCtrl` Objekt anfügt.

Wenn Sie `Create`aufrufen, werden die allgemeinen Steuerelemente initialisiert. Die Version `Create` Ihres Aufrufs bestimmt die Größe der Größe:

- Um die Größe des Steuerelements durch MFC automatisch auf einen Monat zu ändern, rufen Sie die Außerkraftsetzung auf, die den *pt-Parameter* verwendet.

- Um das Steuerelement selbst zu vergrößern, rufen Sie die Außerkraftsetzung dieser Funktion auf, die den *Parameter rect* verwendet.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]

## <a name="cmonthcalctrlgetcalendarborder"></a><a name="getcalendarborder"></a>CMonthCalCtrl::GetCalendarBorder

Ruft die Breite des Rahmens des aktuellen Monatskalendersteuerelements ab.

```
int GetCalendarBorder() const;
```

### <a name="return-value"></a>Rückgabewert

Die Breite des Kontrollrahmens in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [MCM_GETCALENDARBORDER](/windows/win32/Controls/mcm-getcalendarborder) Nachricht, die im Windows SDK beschrieben wird.

## <a name="cmonthcalctrlgetcalendarcount"></a><a name="getcalendarcount"></a>CMonthCalCtrl::GetCalendarCount

Ruft die Anzahl der Kalender ab, die im aktuellen Monatskalendersteuerelement angezeigt werden.

```
int GetCalendarCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Kalender, die derzeit im Monatskalendersteuerelement angezeigt werden. Die maximal zulässige Anzahl von Kalendern beträgt 12.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [MCM_GETCALENDARCOUNT](/windows/win32/Controls/mcm-getcalendarcount) Nachricht, die im Windows SDK beschrieben wird.

## <a name="cmonthcalctrlgetcalendargridinfo"></a><a name="getcalendargridinfo"></a>CMonthCalCtrl::GetCalendarGridInfo

Ruft Informationen zum aktuellen Monatskalendersteuerelement ab.

```
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*pmcGridInfo*|[out] Zeiger auf eine [MCGRIDINFO-Struktur,](/windows/win32/api/commctrl/ns-commctrl-mcgridinfo) die Informationen über das aktuelle Monatskalendersteuerelement empfängt. Der Aufrufer ist für die Zuweisung und Initialisierung dieser Struktur verantwortlich.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [MCM_GETCALENDARGRIDINFO](/windows/win32/Controls/mcm-getcalendargridinfo) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird `m_monthCalCtrl`die Variable , definiert, die für den programmgesteuerten Zugriff auf das Monatskalendersteuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel `GetCalendarGridInfo` wird die Methode zum Abrufen des Kalenderdatums verwendet, das im aktuellen Monatskalendersteuerelement angezeigt wird.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]

## <a name="cmonthcalctrlgetcalid"></a><a name="getcalid"></a>CMonthCalCtrl::GetCalID

Ruft den Kalenderbezeichner für das aktuelle Monatskalendersteuerelement ab.

```
CALID GetCalID() const;
```

### <a name="return-value"></a>Rückgabewert

Eine der [Kalenderbezeichnerkonstanten.](/windows/win32/Intl/calendar-identifiers)

### <a name="remarks"></a>Bemerkungen

Ein Kalenderbezeichner bezeichnet einen regionsspezifischen Kalender, z. B. den Gregorianischen (lokalisierten), japanischen oder Hijri-Kalender. Ihre Anwendung kann einen Kalenderbezeichner mit verschiedenen Sprachunterstützungsfunktionen verwenden.

Diese Methode sendet die [MCM_GETCALID](/windows/win32/Controls/mcm-getcalid) Nachricht, die im Windows SDK beschrieben wird.

## <a name="cmonthcalctrlgetcolor"></a><a name="getcolor"></a>CMonthCalCtrl::GetColor

Ruft die Farbe eines Bereichs des Monatskalendersteuerelements ab, der von *nRegion*angegeben wurde.

```
COLORREF GetColor(int nRegion) const;
```

### <a name="parameters"></a>Parameter

*nRegion*<br/>
Der Bereich des Monatskalendersteuerelements, aus dem die Farbe abgerufen wird. Eine Liste von Werten finden Sie im *nRegion-Parameter* von [SetColor](#setcolor).

### <a name="return-value"></a>Rückgabewert

Ein [COLORREF-Wert,](/windows/win32/gdi/colorref) der die Farbe angibt, die dem Teil des Monatskalendersteuerelements zugeordnet ist, wenn dies erfolgreich ist. Andernfalls gibt diese Memberfunktion -1 zurück.

## <a name="cmonthcalctrlgetcurrentview"></a><a name="getcurrentview"></a>CMonthCalCtrl::GetCurrentView

Ruft die Ansicht ab, die derzeit vom aktuellen Monatskalendersteuerelement angezeigt wird.

```
DWORD GetCurrentView() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Ansicht, die durch einen der folgenden Werte angezeigt wird:

|Wert|Bedeutung|
|-----------|-------------|
|MCMV_MONTH|Monatliche Ansicht|
|MCMV_YEAR|Jahresansicht|
|MCMV_DECADE|Dekadenansicht|
|MCMV_CENTURY|Jahrhundertansicht|

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird `m_monthCalCtrl`die Variable , definiert, die für den programmgesteuerten Zugriff auf das Monatskalendersteuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird berichtet, welche Anzeige das Monatskalendersteuerelement derzeit anzeigt.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]

## <a name="cmonthcalctrlgetcursel"></a><a name="getcursel"></a>CMonthCalCtrl::GetCurSel

Ruft die Systemzeit ab, die durch das aktuell ausgewählte Datum angegeben wird.

```
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;

BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Parameter

*refDateTime*<br/>
Ein Verweis auf ein [COleDateTime-Objekt](../../atl-mfc-shared/reference/coledatetime-class.md) oder ein [CTime-Objekt.](../../atl-mfc-shared/reference/ctime-class.md) Empfängt die aktuelle Uhrzeit.

*pDateTime*<br/>
Ein Zeiger auf eine [SYSTEMTIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) die die aktuell ausgewählten Datumsinformationen empfängt. Dieser Parameter muss eine gültige Adresse sein und darf nicht NULL sein.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich; otherwize 0.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [MCM_GETCURSEL](/windows/win32/Controls/mcm-getcursel)Win32-MCM_GETCURSEL , wie im Windows SDK beschrieben.

> [!NOTE]
> Diese Memberfunktion schlägt fehl, wenn die Formatvorlage MCS_MULTISELECT festgelegt ist.

In der MFC-Implementierung `GetCurSel`von können `COleDateTime` Sie `CTime` eine Verwendung, `SYSTEMTIME` eine Verwendung oder eine Strukturverwendung angeben.

## <a name="cmonthcalctrlgetfirstdayofweek"></a><a name="getfirstdayofweek"></a>CMonthCalCtrl::GetFirstDayOfWeek

Ruft den ersten Tag der Woche ab, der in der linken Spalte des Kalenders angezeigt wird.

```
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;
```

### <a name="parameters"></a>Parameter

*pbLokal*<br/>
Ein Zeiger auf einen BOOL-Wert. Wenn der Wert ungleich Null ist, stimmt die Einstellung des Steuerelements nicht mit der Einstellung in der Systemsteuerung überein.

### <a name="return-value"></a>Rückgabewert

Ein ganzzahliger Wert, der den ersten Tag der Woche darstellt. Weitere Informationen dazu, was diese ganzzahlchen darstellen, finden Sie unter **Hinweise.**

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [MCM_GETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-getfirstdayofweek)Win32-MCM_GETFIRSTDAYOFWEEK , wie im Windows SDK beschrieben. Die Wochentage werden wie folgt als ganze Zahlen dargestellt.

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

  Siehe Beispiel für [CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek).

## <a name="cmonthcalctrlgetmaxselcount"></a><a name="getmaxselcount"></a>CMonthCalCtrl::GetMaxSelCount

Ruft die aktuelle maximale Anzahl von Tagen ab, die in einem Monatskalendersteuerelement ausgewählt werden können.

```
int GetMaxSelCount() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Ganzzahlwert, der die Gesamtzahl der Tage darstellt, die für das Steuerelement ausgewählt werden können.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [MCM_GETMAXSELCOUNT](/windows/win32/Controls/mcm-getmaxselcount)Win32-MCM_GETMAXSELCOUNT , wie im Windows SDK beschrieben. Verwenden Sie diese Memberfunktion für Steuerelemente mit dem Stilsatz MCS_MULTISELECT.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CMonthCalCtrl::SetMaxSelCount](#setmaxselcount).

## <a name="cmonthcalctrlgetmaxtodaywidth"></a><a name="getmaxtodaywidth"></a>CMonthCalCtrl::GetMaxTodayWidth

Ruft die maximale Breite der Zeichenfolge "Heute" für das aktuelle Monatskalendersteuerelement ab.

```
DWORD GetMaxTodayWidth() const;
```

### <a name="return-value"></a>Rückgabewert

Die Breite der Zeichenfolge "Heute" in Pixel.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird `m_monthCalCtrl`die Variable , definiert, die für den programmgesteuerten Zugriff auf das Monatskalendersteuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel `GetMaxTodayWidth` wird die Methode veranschaulicht.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]

### <a name="remarks"></a>Bemerkungen

Der Benutzer kann zum aktuellen Datum zurückkehren, indem er auf die Zeichenfolge "Heute" klickt, die am unteren Rand des Monatskalendersteuerelements angezeigt wird. Die Zeichenfolge "Heute" enthält Beschriftungstext und Datumstext.

Diese Methode sendet die [MCM_GETMAXTODAYWIDTH](/windows/win32/Controls/mcm-getmaxtodaywidth) Nachricht, die im Windows SDK beschrieben wird.

## <a name="cmonthcalctrlgetminreqrect"></a><a name="getminreqrect"></a>CMonthCalCtrl::GetMinReqRect

Ruft die Mindestgröße ab, die erforderlich ist, um einen vollständigen Monat in einem Monatskalendersteuerelement anzuzeigen.

```
BOOL GetMinReqRect(RECT* pRect) const;
```

### <a name="parameters"></a>Parameter

*pRect*<br/>
Ein Zeiger auf eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die umkreisende Rechteckinformationen empfängt. Dieser Parameter muss eine gültige Adresse sein und darf nicht NULL sein.

### <a name="return-value"></a>Rückgabewert

Bei Erfolg gibt diese Memberfunktion `lpRect` einen Wert ungleich Null zurück und empfängt die entsprechenden Begrenzungsinformationen. Wenn dies nicht der Falle ist, gibt die Memberfunktion 0 zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [MCM_GETMINREQRECT](/windows/win32/Controls/mcm-getminreqrect)Win32-MCM_GETMINREQRECT , wie im Windows SDK beschrieben.

## <a name="cmonthcalctrlgetmonthdelta"></a><a name="getmonthdelta"></a>CMonthCalCtrl::GetMonthDelta

Ruft die Bildlaufrate für ein Monatskalendersteuerelement ab.

```
int GetMonthDelta() const;
```

### <a name="return-value"></a>Rückgabewert

Die Bildlaufrate für das Monatskalendersteuerelement. Die Bildlaufrate ist die Anzahl der Monate, in denen das Steuerelement seine Anzeige verschiebt, wenn der Benutzer einmal auf eine Bildlaufschaltfläche klickt.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [MCM_GETMONTHDELTA](/windows/win32/Controls/mcm-getmonthdelta)Win32-MCM_GETMONTHDELTA , wie im Windows SDK beschrieben.

## <a name="cmonthcalctrlgetmonthrange"></a><a name="getmonthrange"></a>CMonthCalCtrl::GetMonthRange

Ruft Datumsinformationen ab, die die anzeige der hohen und niedrigen Grenzwerte eines Monatskalendersteuerelements darstellen.

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

*refMinRange*<br/>
Ein Verweis auf ein [COleDateTime-](../../atl-mfc-shared/reference/coledatetime-class.md) oder [CTime-Objekt,](../../atl-mfc-shared/reference/ctime-class.md) das das zulässige Mindestdatum enthält.

*refMaxRange*<br/>
Ein Verweis `COleDateTime` auf `CTime` ein oder ein Objekt, das das maximal zulässige Datum enthält.

*pMinRange*<br/>
Ein Zeiger auf eine [SYSTEMTIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) die das Datum am unteren Ende des Bereichs enthält.

*pMaxRange*<br/>
Ein Zeiger auf `SYSTEMTIME` eine Struktur, die das Datum am höchsten Ende des Bereichs enthält.

*dwFlags*<br/>
Wert, der den Bereich der abrufbaren Bereichsgrenzen angibt. Dieser Wert muss einer der folgenden sein.

|Wert|Bedeutung|
|-----------|-------------|
|GMR_DAYSTATE|Schließen Sie vorangehende und nachfolgende Monate mit sichtbarem Bereich ein, die nur teilweise angezeigt werden.|
|GMR_VISIBLE|Schließen Sie nur die Monate ein, die vollständig angezeigt werden.|

### <a name="return-value"></a>Rückgabewert

Eine ganze Zahl, die den Bereich in Monaten darstellt, der sich über die beiden Grenzwerte erstreckt, die durch *refMinRange* und *refMaxRange* in der ersten und zweiten Version oder *pMinRange* und *pMaxRange* in der dritten Version angegeben sind.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [MCM_GETMONTHRANGE](/windows/win32/Controls/mcm-getmonthrange)Win32-MCM_GETMONTHRANGE , wie im Windows SDK beschrieben. In der `GetMonthRange`MFC-Implementierung von `COleDateTime` können Sie `CTime` die Verwendung, eine Verwendung oder eine `SYSTEMTIME` Strukturverwendung angeben.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CMonthCalCtrl::SetDayState](#setdaystate).

## <a name="cmonthcalctrlgetrange"></a><a name="getrange"></a>CMonthCalCtrl::GetRange

Ruft die aktuellen minimalen und maximalen Datumsangaben ab, die in einem Monatskalendersteuerelement festgelegt sind.

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

*pMinRange*<br/>
Ein Zeiger auf `COleDateTime` ein `CTime` Objekt, ein Objekt oder [eine SYSTEMTIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) die das Datum am unteren Ende des Bereichs enthält.

*pMaxRange*<br/>
Ein Zeiger auf `COleDateTime` ein `CTime` Objekt, ein Objekt oder [eine SYSTEMTIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) die das Datum am höchsten Ende des Bereichs enthält.

### <a name="return-value"></a>Rückgabewert

Ein DWORD, das Null sein kann (es werden keine Grenzwerte festgelegt) oder eine Kombination der folgenden Werte, die Grenzwertinformationen angeben.

|Wert|Bedeutung|
|-----------|-------------|
|GDTR_MAX|Für das Steuerelement wird ein Höchstwert festgelegt. *pMaxRange* ist gültig und enthält die entsprechenden Datumsinformationen.|
|GDTR_MIN|Für das Steuerelement wird ein Mindestgrenzwert festgelegt. *pMinRange* ist gültig und enthält die entsprechenden Datumsinformationen.|

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Meldung [MCM_GETRANGE](/windows/win32/Controls/mcm-getrange), wie im Windows SDK beschrieben. In der MFC-Implementierung `GetRange`von können `COleDateTime` Sie `CTime` eine Verwendung, `SYSTEMTIME` eine Verwendung oder eine Strukturverwendung angeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]

## <a name="cmonthcalctrlgetselrange"></a><a name="getselrange"></a>CMonthCalCtrl::GetSelRange

Ruft Datumsinformationen ab, die die oberen und unteren Grenzwerte des datumsbereichs darstellen, der derzeit vom Benutzer ausgewählt wurde.

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

*refMinRange*<br/>
Ein Verweis auf ein [COleDateTime-](../../atl-mfc-shared/reference/coledatetime-class.md) oder [CTime-Objekt,](../../atl-mfc-shared/reference/ctime-class.md) das das zulässige Mindestdatum enthält.

*refMaxRange*<br/>
Ein Verweis `COleDateTime` auf `CTime` ein oder ein Objekt, das das maximal zulässige Datum enthält.

*pMinRange*<br/>
Ein Zeiger auf eine [SYSTEMTIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) die das Datum am unteren Ende des Bereichs enthält.

*pMaxRange*<br/>
Ein Zeiger auf `SYSTEMTIME` eine Struktur, die das Datum am höchsten Ende des Bereichs enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [MCM_GETSELRANGE](/windows/win32/Controls/mcm-getselrange)Win32-MCM_GETSELRANGE , wie im Windows SDK beschrieben. `GetSelRange`schlägt fehl, wenn es auf ein Monatskalendersteuerelement angewendet wird, das nicht den MCS_MULTISELECT-Format verwendet.

In der `GetSelRange`MFC-Implementierung von `COleDateTime` können Sie `CTime` die Verwendung, eine Verwendung oder eine `SYSTEMTIME` Strukturverwendung angeben.

## <a name="cmonthcalctrlgettoday"></a><a name="gettoday"></a>CMonthCalCtrl::GetToday

Ruft die Datumsinformationen für das datum ab, das als "heute" für ein Monatskalendersteuerelement angegeben ist.

```
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;

BOOL GetToday(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Parameter

*refDateTime*<br/>
Ein Verweis auf ein [COleDateTime-](../../atl-mfc-shared/reference/coledatetime-class.md) oder [CTime-Objekt,](../../atl-mfc-shared/reference/ctime-class.md) das den aktuellen Tag angibt.

*pDateTime*<br/>
Ein Zeiger auf eine [SYSTEMTIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) die die Datumsinformationen empfängt. Dieser Parameter muss eine gültige Adresse sein und darf nicht NULL sein.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [MCM_GETTODAY](/windows/win32/Controls/mcm-gettoday)Win32-MCM_GETTODAY , wie im Windows SDK beschrieben. In der MFC-Implementierung `GetToday`von können `COleDateTime` Sie `CTime` eine Verwendung, `SYSTEMTIME` eine Verwendung oder eine Strukturverwendung angeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]

## <a name="cmonthcalctrlhittest"></a><a name="hittest"></a>CMonthCalCtrl::HitTest

Bestimmt, welches Kalendersteuerelement sich ggf. an einer angegebenen Position befindet.

```
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```

### <a name="parameters"></a>Parameter

*pMCHitTest*<br/>
Ein Zeiger auf eine [MCHITTESTINFO-Struktur,](/windows/win32/api/commctrl/ns-commctrl-mchittestinfo) die Treffertestpunkte für das Monatskalendersteuerelement enthält.

### <a name="return-value"></a>Rückgabewert

Ein DWORD-Wert. Entspricht dem **uHit-Member** der `MCHITTESTINFO` Struktur.

### <a name="remarks"></a>Bemerkungen

`HitTest`verwendet `MCHITTESTINFO` die Struktur, die Informationen über den Treffertest enthält.

## <a name="cmonthcalctrliscenturyview"></a><a name="iscenturyview"></a>CMonthCalCtrl::IsCenturyView

Gibt an, ob die aktuelle Ansicht des aktuellen Monatskalendersteuerelements die Jahrhundertansicht ist.

```
BOOL IsCenturyView() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die aktuelle Ansicht die Jahrhundertansicht ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) Nachricht, die im Windows SDK beschrieben wird. Wenn diese Meldung MCMV_CENTURY zurückgibt, gibt diese Methode TRUE zurück.

## <a name="cmonthcalctrlisdecadeview"></a><a name="isdecadeview"></a>CMonthCalCtrl::IsDecadeView

Gibt an, ob die aktuelle Ansicht des aktuellen Monatskalendersteuerelements die Dekadenansicht ist.

```
BOOL IsDecadeView() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die aktuelle Ansicht die Dekadenansicht ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) Nachricht, die im Windows SDK beschrieben wird. Wenn diese Nachricht MCMV_DECADE zurückgibt, gibt diese Methode TRUE zurück.

## <a name="cmonthcalctrlismonthview"></a><a name="ismonthview"></a>CMonthCalCtrl::IsMonthView

Gibt an, ob die aktuelle Ansicht des aktuellen Monatskalendersteuerelements die Monatsansicht ist.

```
BOOL IsMonthView() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die aktuelle Ansicht die Monatsansicht ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) Nachricht, die im Windows SDK beschrieben wird. Wenn diese Meldung MCMV_MONTH zurückgibt, gibt diese Methode TRUE zurück.

## <a name="cmonthcalctrlisyearview"></a><a name="isyearview"></a>CMonthCalCtrl::IsYearView

Gibt an, ob die aktuelle Ansicht des aktuellen Monatskalendersteuerelements die Jahresansicht ist.

```
BOOL IsYearView() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die aktuelle Ansicht die Jahresansicht ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) Nachricht, die im Windows SDK beschrieben wird. Wenn diese Nachricht MCMV_YEAR zurückgibt, gibt diese Methode TRUE zurück.

## <a name="cmonthcalctrlsetcalendarborder"></a><a name="setcalendarborder"></a>CMonthCalCtrl::SetCalendarBorder

Legt die Breite des Rahmens des aktuellen Monatskalendersteuerelements fest.

```cpp
void SetCalendarBorder(int cxyBorder);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*cxyBorder*|[in] Die Breite des Rahmens in Pixel.|

### <a name="remarks"></a>Bemerkungen

Wenn diese Methode erfolgreich ist, wird die Rahmenbreite auf den Parameter *cxyBorder* festgelegt. Andernfalls wird die Rahmenbreite auf den Standardwert zurückgesetzt, der vom aktuellen [Design](/windows/win32/Controls/visual-styles-overview)angegeben wird, oder Null, wenn Designs nicht verwendet werden.

Diese Methode sendet die [MCM_SETCALENDARBORDER](/windows/win32/Controls/mcm-setcalendarborder) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird `m_monthCalCtrl`die Variable , definiert, die für den programmgesteuerten Zugriff auf das Monatskalendersteuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die Rahmenbreite des Monatskalendersteuerelements auf acht Pixel festgelegt. Verwenden Sie die [CMonthCalCtrl::GetCalendarBorder-Methode,](#getcalendarborder) um zu bestimmen, ob diese Methode erfolgreich war.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]

## <a name="cmonthcalctrlsetcalendarborderdefault"></a><a name="setcalendarborderdefault"></a>CMonthCalCtrl::SetCalendarBorderDefault

Legt die Standardbreite des Rahmens des aktuellen Monatskalendersteuerelements fest.

```cpp
void SetCalendarBorderDefault();
```

### <a name="remarks"></a>Bemerkungen

Die Rahmenbreite wird auf den Vom aktuellen [Design](/windows/win32/Controls/visual-styles-overview)angegebenen Standardwert oder Null festgelegt, wenn Designs nicht verwendet werden.

Diese Methode sendet die [MCM_SETCALENDARBORDER](/windows/win32/Controls/mcm-setcalendarborder) Nachricht, die im Windows SDK beschrieben wird.

## <a name="cmonthcalctrlsetcalid"></a><a name="setcalid"></a>CMonthCalCtrl::SetCalID

Legt den Kalenderbezeichner für das aktuelle Monatskalendersteuerelement fest.

```
BOOL SetCalID(CALID calid);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*calid*|[in] Eine der [Kalenderbezeichnerkonstanten.](/windows/win32/Intl/calendar-identifiers)|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Ein Kalenderbezeichner gibt einen regionsspezifischen Kalender an, z. B. den Gregorianischen (lokalisierten), japanischen oder Hijri-Kalender. Verwenden `SetCalID` Sie die Methode, um einen Kalender anzuzeigen, der durch den *calid-Parameter* angegeben wird, wenn das Gebietsschema, das den Kalender enthält, auf Ihrem Computer installiert ist.

Diese Methode sendet die [MCM_SETCALID](/windows/win32/Controls/mcm-setcalid) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird `m_monthCalCtrl`die Variable , definiert, die für den programmgesteuerten Zugriff auf das Monatskalendersteuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird das Monatskalendersteuerelement so festgelegt, dass der Kalender der japanischen Kaiserzeit angezeigt wird. Die `SetCalID` Methode ist nur erfolgreich, wenn dieser Kalender auf Ihrem Computer installiert ist.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]

## <a name="cmonthcalctrlsetcenturyview"></a><a name="setcenturyview"></a>CMonthCalCtrl::SetCenturyView

Legt das aktuelle Monatskalendersteuerelement so fest, dass die Jahrhundertansicht angezeigt wird.

```
BOOL SetCenturyView();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet die [CMonthCalCtrl::SetCurrentView-Methode,](#setcurrentview) um die Ansicht auf festzulegen, `MCMV_CENTURY`die die Jahrhundertansicht darstellt.

## <a name="cmonthcalctrlsetcolor"></a><a name="setcolor"></a>CMonthCalCtrl::SetColor

Legt die Farbe eines angegebenen Bereichs eines Monatskalendersteuerelements fest.

```
COLORREF SetColor(
    int nRegion,
    COLORREF ref);
```

### <a name="parameters"></a>Parameter

*nRegion*<br/>
Ein Ganzzahlwert, der angibt, welche Monatskalenderfarbe festgelegt werden soll. Dieser Wert kann einer der folgenden sein.

|Wert|Bedeutung|
|-----------|-------------|
|MCSC_BACKGROUND|Die Zwischenmonatsfarbe angezeigte Hintergrundfarbe.|
|MCSC_MONTHBK|Die Hintergrundfarbe, die innerhalb des Monats angezeigt wird.|
|MCSC_TEXT|Die Farbe, die zum Anzeigen von Text innerhalb eines Monats verwendet wird.|
|MCSC_TITLEBK|Die Hintergrundfarbe, die im Titel des Kalenders angezeigt wird.|
|MCSC_TITLETEXT|Die Farbe, die zum Anzeigen von Text im Kalendertitel verwendet wird.|
|MCSC_TRAILINGTEXT|Die Farbe, die zum Anzeigen von Kopf- und Trailing-Day-Text verwendet wird. Kopf- und Nachverfolgungstage sind die Tage aus dem vorherigen und den folgenden Monaten, die im aktuellen Kalender angezeigt werden.|

*ref*<br/>
Ein COLORREF-Wert für die neue Farbeinstellung für den angegebenen Teil des Monatskalendersteuerelements.

### <a name="return-value"></a>Rückgabewert

Ein COLORREF-Wert, der die vorherige Farbeinstellung für den angegebenen Teil des Monatskalendersteuerelements darstellt, falls erfolgreich. Andernfalls gibt diese Meldung -1 zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [MCM_SETCOLOR](/windows/win32/Controls/mcm-setcolor)Win32-MCM_SETCOLOR , wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]

## <a name="cmonthcalctrlsetcurrentview"></a><a name="setcurrentview"></a>CMonthCalCtrl::SetCurrentView

Legt das aktuelle Monatskalendersteuerelement so fest, dass die angegebene Ansicht angezeigt wird.

```
BOOL SetCurrentView(DWORD dwNewView);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*dwNewView*|[in] Einer der folgenden Werte, der eine monatliche, jährliche, zehnjährige oder Jahrhundertansicht angibt.<br /><br /> MCMV_MONTH: Monatsansicht<br /><br /> MCMV_YEAR: Jahresansicht<br /><br /> MCMV_DECADE: Dekadenansicht<br /><br /> MCMV_CENTURY: Jahrhundertansicht|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [MCM_SETCURRENTVIEW](/windows/win32/Controls/mcm-setcurrentview) Nachricht, die im Windows SDK beschrieben wird.

## <a name="cmonthcalctrlsetcursel"></a><a name="setcursel"></a>CMonthCalCtrl::SetCurSel

Legt das aktuell ausgewählte Datum für ein Monatskalendersteuerelement fest.

```
BOOL SetCurSel(const COleDateTime& refDateTime);
BOOL SetCurSel(const CTime& refDateTime);
BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Parameter

*refDateTime*<br/>
Ein Verweis auf ein [COleDateTime-](../../atl-mfc-shared/reference/coledatetime-class.md) oder [CTime-Objekt,](../../atl-mfc-shared/reference/ctime-class.md) das das aktuell ausgewählte Monatskalendersteuerelement angibt.

*pDateTime*<br/>
Zeigen Sie auf eine [SYSTEMTIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) die das Datum enthält, das als aktuelle Auswahl festgelegt werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [MCM_SETCURSEL](/windows/win32/Controls/mcm-setcursel)Win32-MCM_SETCURSEL , wie im Windows SDK beschrieben. In der MFC-Implementierung `SetCurSel`von können `COleDateTime` Sie `CTime` eine Verwendung, `SYSTEMTIME` eine Verwendung oder eine Strukturverwendung angeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]

## <a name="cmonthcalctrlsetdaystate"></a><a name="setdaystate"></a>CMonthCalCtrl::SetDayState

Legt die Anzeige für Tage in einem Monatskalendersteuerelement fest.

```
BOOL SetDayState(
    int nMonths,
    LPMONTHDAYSTATE pStates);
```

### <a name="parameters"></a>Parameter

*nMonate*<br/>
Wert, der angibt, wie viele Elemente sich im Array befinden, auf das *PStates* verweist.

*PStates*<br/>
Ein Zeiger auf ein [MONTHDAYSTATE-Array](/windows/win32/Controls/monthdaystate) von Werten, die definieren, wie das Monatskalendersteuerelement jeden Tag in seiner Anzeige gezeichnet wird. Der MONTHDAYSTATE-Datentyp ist ein Bitfeld, in dem jedes Bit (1 bis 31) den Status eines Tages in einem Monat darstellt. Wenn ein Bit eingeschaltet ist, wird der entsprechende Tag fett angezeigt. andernfalls wird es ohne Betonung angezeigt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [MCM_SETDAYSTATE](/windows/win32/Controls/mcm-setdaystate)Win32-MCM_SETDAYSTATE , wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]

## <a name="cmonthcalctrlsetdecadeview"></a><a name="setdecadeview"></a>CMonthCalCtrl::SetDecadeView

Legt das aktuelle Monatskalendersteuerelement auf die Dekadenansicht fest.

```
BOOL SetDecadeView();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet die [CMonthCalCtrl::SetCurrentView-Methode,](#setcurrentview) um die Ansicht auf festzulegen, `MCMV_DECADE`die die Dekadenansicht darstellt.

## <a name="cmonthcalctrlsetfirstdayofweek"></a><a name="setfirstdayofweek"></a>CMonthCalCtrl::SetFirstDayOfWeek

Legt den Wochentag fest, der in der linken Spalte des Kalenders angezeigt werden soll.

```
BOOL SetFirstDayOfWeek(
    int iDay,
    int* lpnOld = NULL);
```

### <a name="parameters"></a>Parameter

*Iday*<br/>
Ein ganzzahliger Wert, der angibt, welcher Tag als erster Tag der Woche festgelegt werden soll. Dieser Wert muss eine der Tageszahlen sein. Eine Beschreibung der Tageszahlen finden Sie unter [GetFirstDayOfWeek.](#getfirstdayofweek)

*lpnOld*<br/>
Ein Zeiger auf eine ganze Zahl, die den ersten Tag der zuvor festgelegten Woche angibt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der vorherige erste Tag der Woche auf einen anderen Wert als den wert LOCALE_IFIRSTDAYOFWEEK festgelegt ist, d. h. auf den in der Systemsteuerungseinstellung angegebenen Tag. Andernfalls gibt diese Funktion 0 zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Meldung [MCM_SETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-setfirstdayofweek), wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]

## <a name="cmonthcalctrlsetmaxselcount"></a><a name="setmaxselcount"></a>CMonthCalCtrl::SetMaxSelCount

Legt die maximale Anzahl von Tagen fest, die in einem Monatskalendersteuerelement ausgewählt werden können.

```
BOOL SetMaxSelCount(int nMax);
```

### <a name="parameters"></a>Parameter

*nMax*<br/>
Der Wert, der so festgelegt wird, dass er die maximale Anzahl von wählbaren Tagen darstellt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Meldung [MCM_SETMAXSELCOUNT](/windows/win32/Controls/mcm-setmaxselcount), wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]

## <a name="cmonthcalctrlsetmonthdelta"></a><a name="setmonthdelta"></a>CMonthCalCtrl::SetMonthDelta

Legt die Bildlaufrate für ein Monatskalendersteuerelement fest.

```
int SetMonthDelta(int iDelta);
```

### <a name="parameters"></a>Parameter

*iDelta*<br/>
Die Anzahl der Monate, die als Bildlaufrate des Steuerelements festgelegt werden sollen. Wenn dieser Wert Null ist, wird das Monatsdelta auf den Standardwert zurückgesetzt, d. h. die Anzahl der Monate, die im Steuerelement angezeigt werden.

### <a name="return-value"></a>Rückgabewert

Die vorherige Bildlaufrate. Wenn die Bildlaufrate noch nicht festgelegt wurde, ist der Rückgabewert 0.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Meldung [MCM_SETMONTHDELTA](/windows/win32/Controls/mcm-setmonthdelta), wie im Windows SDK beschrieben.

## <a name="cmonthcalctrlsetmonthview"></a><a name="setmonthview"></a>CMonthCalCtrl::SetMonthView

Legt das aktuelle Monatskalendersteuerelement so fest, dass die Monatsansicht angezeigt wird.

```
BOOL SetMonthView();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet die [CMonthCalCtrl::SetCurrentView-Methode,](#setcurrentview) um die Ansicht auf MCMV_MONTH festzulegen, die die Monatsansicht darstellt.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird `m_monthCalCtrl`die Variable , definiert, die für den programmgesteuerten Zugriff auf das Monatskalendersteuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird das Monatskalendersteuerelement so festgelegt, dass die Monats-, Jahres-, Dekaden- und Jahrhundertansichten angezeigt werden.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]

## <a name="cmonthcalctrlsetrange"></a><a name="setrange"></a>CMonthCalCtrl::SetRange

Legt die minimalen und maximal zulässigen Datumsangaben für ein Monatskalendersteuerelement fest.

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

*pMinRange*<br/>
Ein Zeiger auf `COleDateTime` ein `CTime` Objekt, ein Objekt oder [eine SYSTEMTIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) die das Datum am unteren Ende des Bereichs enthält.

*pMaxRange*<br/>
Ein Zeiger auf `COleDateTime` ein `CTime` Objekt, `SYSTEMTIME` ein Objekt oder eine Struktur, die das Datum am höchsten Ende des Bereichs enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [MCM_SETRANGE](/windows/win32/Controls/mcm-setrange)Win32-MCM_SETRANGE , wie im Windows SDK beschrieben. In der `SetRange`MFC-Implementierung von `COleDateTime` können Sie `CTime` die Verwendung, eine Verwendung oder eine `SYSTEMTIME` Strukturverwendung angeben.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CMonthCalCtrl::GetRange](#getrange).

## <a name="cmonthcalctrlsetselrange"></a><a name="setselrange"></a>CMonthCalCtrl::SetSelRange

Legt die Auswahl für ein Monatskalendersteuerelement auf einen bestimmten Datumsbereich fest.

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

*pMinRange*<br/>
Ein Zeiger auf `COleDateTime` ein `CTime` Objekt, ein Objekt oder [eine SYSTEMTIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) die das Datum am unteren Ende des Bereichs enthält.

*pMaxRange*<br/>
Ein Zeiger auf `COleDateTime` ein `CTime` Objekt, `SYSTEMTIME` ein Objekt oder eine Struktur, die das Datum am höchsten Ende des Bereichs enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [MCM_SETSELRANGE](/windows/win32/Controls/mcm-setselrange)Win32-MCM_SETSELRANGE , wie im Windows SDK beschrieben. In der `SetSelRange`MFC-Implementierung von `COleDateTime` können Sie `CTime` die Verwendung, eine Verwendung oder eine `SYSTEMTIME` Strukturverwendung angeben.

## <a name="cmonthcalctrlsettoday"></a><a name="settoday"></a>CMonthCalCtrl::SetToday

Legt das Kalendersteuerelement für den aktuellen Tag fest.

```cpp
void SetToday(const COleDateTime& refDateTime);
void SetToday(const CTime* pDateTime);
void SetToday(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Parameter

*refDateTime*<br/>
Ein Verweis auf ein [COleDateTime-Objekt,](../../atl-mfc-shared/reference/coledatetime-class.md) das das aktuelle Datum enthält.

*pDateTime*<br/>
In der zweiten Version ein Zeiger auf ein [CTime-Objekt,](../../atl-mfc-shared/reference/ctime-class.md) das die aktuellen Datumsinformationen enthält. In der dritten Version ein Zeiger auf eine [SYSTEMTIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) die die aktuellen Datumsinformationen enthält.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [MCM_SETTODAY](/windows/win32/Controls/mcm-settoday)Win32-MCM_SETTODAY , wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CMonthCalCtrl::GetToday](#gettoday).

## <a name="cmonthcalctrlsetyearview"></a><a name="setyearview"></a>CMonthCalCtrl::SetYearView

Legt das aktuelle Monatskalendersteuerelement auf die Jahresansicht fest.

```
BOOL SetYearView();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode verwendet die [CMonthCalCtrl::SetCurrentView-Methode,](#setcurrentview) um die Ansicht auf MCMV_YEAR festzulegen, die die Jahresansicht darstellt.

## <a name="cmonthcalctrlsizeminreq"></a><a name="sizeminreq"></a>CMonthCalCtrl::SizeMinReq

Zeigt das Monatskalendersteuerelement auf die Mindestgröße an, die einen Monat anzeigt.

```
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```

### <a name="parameters"></a>Parameter

*bRepaint*<br/>
Gibt an, ob das Steuerelement neu gezeichnet werden soll. Standardmäßig TRUE. Wenn FALSE, wird keine Neulackierung ausgeführt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Größe des Monatskalendersteuerelements auf das Minimum beschränkt ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Beim `SizeMinReq` Aufruf wird das gesamte Monatskalendersteuerelement für den Kalender eines Monats angezeigt.

## <a name="cmonthcalctrlsizerecttomin"></a><a name="sizerecttomin"></a>CMonthCalCtrl::SizeRectToMin

Berechnet für das aktuelle Monatskalendersteuerelement das kleinste Rechteck, das alle Kalender enthalten kann, die in ein angegebenes Rechteck passen.

```
LPRECT SizeRectToMin(LPRECT lpRect);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*lpRect*|[in] Zeiger auf eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die ein Rechteck definiert, das die gewünschte Anzahl von Kalendern enthält.|

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die ein Rechteck definiert, dessen Größe kleiner oder gleich dem durch den *Parameter lpRect* definierten Rechteck ist.

### <a name="remarks"></a>Bemerkungen

Diese Methode berechnet, wie viele Kalender in das durch den Parameter *lpRect* angegebene Rechteck passen können, und gibt dann das kleinste Rechteck zurück, das diese Anzahl von Kalendern enthalten kann. Diese Methode verkleinert das angegebene Rechteck genau so, dass es genau an die gewünschte Anzahl von Kalendern anpasst.

Diese Methode sendet die [MCM_SIZERECTTOMIN](/windows/win32/Controls/mcm-sizerecttomin) Nachricht, die im Windows SDK beschrieben wird.

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDateTimeCtrl-Klasse](../../mfc/reference/cdatetimectrl-class.md)
