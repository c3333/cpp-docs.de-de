---
title: CDateTimeCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CloseMonthCal
- AFXDTCTL/CDateTimeCtrl::Create
- AFXDTCTL/CDateTimeCtrl::GetDateTimePickerInfo
- AFXDTCTL/CDateTimeCtrl::GetIdealSize
- AFXDTCTL/CDateTimeCtrl::GetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::GetMonthCalCtrl
- AFXDTCTL/CDateTimeCtrl::GetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::GetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::GetRange
- AFXDTCTL/CDateTimeCtrl::GetTime
- AFXDTCTL/CDateTimeCtrl::SetFormat
- AFXDTCTL/CDateTimeCtrl::SetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::SetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::SetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::SetRange
- AFXDTCTL/CDateTimeCtrl::SetTime
helpviewer_keywords:
- CDateTimeCtrl [MFC], CDateTimeCtrl
- CDateTimeCtrl [MFC], CloseMonthCal
- CDateTimeCtrl [MFC], Create
- CDateTimeCtrl [MFC], GetDateTimePickerInfo
- CDateTimeCtrl [MFC], GetIdealSize
- CDateTimeCtrl [MFC], GetMonthCalColor
- CDateTimeCtrl [MFC], GetMonthCalCtrl
- CDateTimeCtrl [MFC], GetMonthCalFont
- CDateTimeCtrl [MFC], GetMonthCalStyle
- CDateTimeCtrl [MFC], GetRange
- CDateTimeCtrl [MFC], GetTime
- CDateTimeCtrl [MFC], SetFormat
- CDateTimeCtrl [MFC], SetMonthCalColor
- CDateTimeCtrl [MFC], SetMonthCalFont
- CDateTimeCtrl [MFC], SetMonthCalStyle
- CDateTimeCtrl [MFC], SetRange
- CDateTimeCtrl [MFC], SetTime
ms.assetid: 7113993b-5d37-4148-939f-500a190c5bdc
ms.openlocfilehash: d0433507c32c7359f8033836bf845defa8ad7f7a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321914"
---
# <a name="cdatetimectrl-class"></a>CDateTimeCtrl-Klasse

Kapselt die Funktionalität eines Steuerelements für die Datums- und Zeitauswahl.

## <a name="syntax"></a>Syntax

```
class CDateTimeCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDateTimeCtrl::CDateTimeCtrl](#cdatetimectrl)|Erstellt ein `CDateTimeCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDateTimeCtrl::CloseMonthCal](#closemonthcal)|Schließt das aktuelle Datums- und Uhrzeitauswahlsteuerelement.|
|[CDateTimeCtrl::Erstellen](#create)|Erstellt das Datums- und Uhrzeitauswahlsteuerelement `CDateTimeCtrl` und fügt es an das Objekt an.|
|[CDateTimeCtrl::GetDateTimePickerInfo](#getdatetimepickerinfo)|Ruft Informationen zum aktuellen Datums- und Uhrzeitauswahlsteuerelement ab.|
|[CDateTimeCtrl::GetIdealSize](#getidealsize)|Gibt die ideale Größe des Datums- und Uhrzeitauswahlsteuerelements zurück, das zum Anzeigen des aktuellen Datums oder der aktuellen Uhrzeit erforderlich ist.|
|[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)|Ruft die Farbe für einen bestimmten Teil des Monatskalenders innerhalb des Datums- und Uhrzeitauswahlsteuerelements ab.|
|[CDateTimeCtrl::GetMonthCalCtrl](#getmonthcalctrl)|Ruft das `CMonthCalCtrl` Objekt ab, das dem Datums- und Uhrzeitauswahlsteuerelement zugeordnet ist.|
|[CDateTimeCtrl::GetMonthCalFont](#getmonthcalfont)|Ruft die Schriftart ab, die derzeit vom untergeordneten Monatskalendersteuerelement des Datums- und Uhrzeitauswahlsteuerelements verwendet wird.|
|[CDateTimeCtrl::GetMonthCalStyle](#getmonthcalstyle)|Ruft den Stil des aktuellen Datums- und Uhrzeitauswahlsteuerelements ab.|
|[CDateTimeCtrl::GetRange](#getrange)|Ruft die aktuellen minimalen und maximal zulässigen Systemzeiten für ein Datums- und Zeitauswahlsteuerelement ab.|
|[CDateTimeCtrl::GetTime](#gettime)|Ruft die aktuell ausgewählte Uhrzeit aus einem Datums- und `SYSTEMTIME` Uhrzeitauswahlsteuerelement ab und fügt sie in eine angegebene Struktur ein.|
|[CDateTimeCtrl::SetFormat](#setformat)|Legt die Anzeige eines Datums- und Uhrzeitauswahlsteuerelements entsprechend einer bestimmten Formatzeichenfolge fest.|
|[CDateTimeCtrl::SetMonthCalColor](#setmonthcalcolor)|Legt die Farbe für einen bestimmten Teil des Monatskalenders innerhalb eines Datums- und Zeitauswahlsteuerelements fest.|
|[CDateTimeCtrl::SetMonthCalFont](#setmonthcalfont)|Legt die Schriftart fest, die das Kalendersteuerelement für den untergeordneten Monat des Datums- und Uhrzeitauswahlsteuerelements verwendet.|
|[CDateTimeCtrl::SetMonthCalStyle](#setmonthcalstyle)|Legt den Stil des aktuellen Datums- und Uhrzeitauswahlsteuerelements fest.|
|[CDateTimeCtrl::SetRange](#setrange)|Legt die minimalen und maximal zulässigen Systemzeiten für ein Datums- und Zeitauswahlsteuerelement fest.|
|[CDateTimeCtrl::SetTime](#settime)|Legt die Uhrzeit in einem Datums- und Uhrzeitauswahlsteuerelement fest.|

## <a name="remarks"></a>Bemerkungen

Das Datums- und Uhrzeitauswahlsteuerelement (DTP-Steuerelement) bietet eine einfache Schnittstelle zum Austausch von Datums- und Uhrzeitinformationen mit einem Benutzer. Diese Schnittstelle enthält Felder, von denen jedes einen Teil der im Steuerelement gespeicherten Datums- und Uhrzeitinformationen anzeigt. Der Benutzer kann die im Steuerelement gespeicherten Informationen ändern, indem er den Inhalt der Zeichenfolge in einem bestimmten Feld ändert. Der Benutzer kann mit der Maus oder der Tastatur von Feld zu Feld wechseln.

Sie können das Datums- und Uhrzeitauswahlsteuerelement anpassen, indem Sie beim Erstellen eine Vielzahl von Stilen auf das Objekt anwenden. Weitere Informationen zu Stilen, die für das Datums- und Uhrzeitauswahlsteuerelement spezifisch sind, finden Sie unter [Datums- und Zeitauswahlsteuerungsstile](/windows/win32/Controls/date-and-time-picker-control-styles) im Windows SDK. Sie können das Anzeigeformat des DTP-Steuerelements mithilfe von Formatstilen festlegen. Diese Formatstile werden unter "Formatvorlagen" im Windows SDK-Thema [Datums- und Zeitauswahlsteuerungsstile](/windows/win32/Controls/date-and-time-picker-control-styles)beschrieben.

Das Datums- und Uhrzeitauswahlsteuerelement verwendet auch Benachrichtigungen und Rückrufe, die unter [Verwenden von CDateTimeCtrl](../../mfc/using-cdatetimectrl.md)beschrieben werden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxdtctl.h

## <a name="cdatetimectrlcdatetimectrl"></a><a name="cdatetimectrl"></a>CDateTimeCtrl::CDateTimeCtrl

Erstellt ein `CDateTimeCtrl`-Objekt.

```
CDateTimeCtrl();
```

## <a name="cdatetimectrlclosemonthcal"></a><a name="closemonthcal"></a>CDateTimeCtrl::CloseMonthCal

Schließt das aktuelle Datums- und Uhrzeitauswahlsteuerelement.

```
void CloseMonthCal() const;
```

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [DTM_CLOSEMONTHCAL](/windows/win32/Controls/dtm-closemonthcal) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die Variable *m_dateTimeCtrl*definiert, die für den programmgesteuerten Zugriff auf das Datums- und Uhrzeitauswahlsteuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird der Dropdownkalender für das aktuelle Datums- und Uhrzeitauswahlsteuerelement geschlossen.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

## <a name="cdatetimectrlcreate"></a><a name="create"></a>CDateTimeCtrl::Erstellen

Erstellt das Datums- und Uhrzeitauswahlsteuerelement `CDateTimeCtrl` und fügt es an das Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Gibt die Kombination von Datumszeitsteuerungsstilen an. Weitere Informationen zu Datums- und Uhrzeitauswahlstilen finden Sie unter [Datums- und Zeitauswahlsteuerungsstile](/windows/win32/Controls/date-and-time-picker-control-styles) im Windows SDK.

*Rect*<br/>
Ein Verweis auf eine [RECT-Struktur,](/previous-versions/dd162897\(v=vs.85\)) d. h. die Position und Größe des Datums- und Uhrzeitauswahlsteuerelements.

*pParentWnd*<br/>
Ein Zeiger auf ein [CWnd-Objekt,](../../mfc/reference/cwnd-class.md) das das übergeordnete Fenster des Datums- und Uhrzeitauswahlsteuerelements ist. Es darf nicht NULL sein.

*nID*<br/>
Gibt die Steuerelement-ID des Datums- und Uhrzeitauswahlsteuerelements an.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Erstellung erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

##### <a name="to-create-a-date-and-time-picker-control"></a>So erstellen Sie ein Datums- und Uhrzeitauswahlsteuerelement

1. Rufen Sie [CDateTimeCtrl](#cdatetimectrl) auf, um ein `CDateTimeCtrl` Objekt zu erstellen.

1. Rufen Sie diese Memberfunktion auf, die das Windows-Datums- `CDateTimeCtrl` und Zeitauswahlsteuerelement erstellt und an das Objekt anfügt.

Wenn Sie `Create`aufrufen, werden die allgemeinen Steuerelemente initialisiert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

## <a name="cdatetimectrlgetdatetimepickerinfo"></a><a name="getdatetimepickerinfo"></a>CDateTimeCtrl::GetDateTimePickerInfo

Ruft Informationen zum aktuellen Datums- und Uhrzeitauswahlsteuerelement ab.

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*pDateTimePickerInfo*|[out] Ein Zeiger auf eine [DATETIMEPICKERINFO-Struktur,](/windows/win32/api/commctrl/ns-commctrl-datetimepickerinfo) die eine Beschreibung des aktuellen Datums- und Zeitauswahlsteuerelements empfängt.<br /><br /> Der Aufrufer ist für die Zuweisung dieser Struktur verantwortlich. Diese Methode initialisiert jedoch den *cbSize-Member* der Struktur.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [DTM_GETDATETIMEPICKERINFO](/windows/win32/Controls/dtm-getdatetimepickerinfo) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die Variable *m_dateTimeCtrl*definiert, die für den programmgesteuerten Zugriff auf das Datums- und Uhrzeitauswahlsteuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Beispiel

Das folgende Codebeispiel gibt an, ob informationen zum aktuellen Datums- und Uhrzeitauswahlsteuerelement erfolgreich abgerufen werden.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

## <a name="cdatetimectrlgetmonthcalcolor"></a><a name="getmonthcalcolor"></a>CDateTimeCtrl::GetMonthCalColor

Ruft die Farbe für einen bestimmten Teil des Monatskalenders innerhalb des Datums- und Uhrzeitauswahlsteuerelements ab.

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>Parameter

*Icolor*<br/>
Ein **int-Wert,** der angibt, welcher Farbbereich des Monatskalenders abgerufen werden soll. Eine Liste von Werten finden Sie im *iColor-Parameter* für [SetMonthCalColor](#setmonthcalcolor).

### <a name="return-value"></a>Rückgabewert

Ein COLORREF-Wert, der die Farbeinstellung für den angegebenen Teil des Monatskalendersteuerelements darstellt, wenn er erfolgreich ist. Die Funktion gibt -1 zurück, wenn sie nicht erfolgreich ist.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [DTM_GETMCCOLOR](/windows/win32/Controls/dtm-getmccolor)Win32-DTM_GETMCCOLOR , wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

## <a name="cdatetimectrlgetmonthcalctrl"></a><a name="getmonthcalctrl"></a>CDateTimeCtrl::GetMonthCalCtrl

Ruft das `CMonthCalCtrl` Objekt ab, das dem Datums- und Uhrzeitauswahlsteuerelement zugeordnet ist.

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CMonthCalCtrl-Objekt](../../mfc/reference/cmonthcalctrl-class.md) oder NULL, wenn kein Erfolg oder wenn das Fenster nicht sichtbar ist.

### <a name="remarks"></a>Bemerkungen

Datums- und Uhrzeitauswahlsteuerelemente erstellen ein Kalendersteuerelement für untergeordnete Monate, wenn der Benutzer auf den Dropdownpfeil klickt. Wenn `CMonthCalCtrl` das Objekt nicht mehr benötigt wird, wird es zerstört, daher darf sich die Anwendung nicht darauf verlassen, das Objekt zu speichern, das den untergeordneten Monatskalender des Datumszeitauswahlsteuerelements darstellt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

## <a name="cdatetimectrlgetmonthcalfont"></a><a name="getmonthcalfont"></a>CDateTimeCtrl::GetMonthCalFont

Ruft die Schriftart ab, die derzeit vom Monatskalendersteuerelement des Datums- und Uhrzeitauswahlsteuerelements verwendet wird.

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CFont-Objekt](../../mfc/reference/cfont-class.md) oder NULL, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Das `CFont` Objekt, auf das der Rückgabewert zeigt, ist ein temporäres Objekt und wird während der nächsten Verarbeitungszeit im Leerlauf zerstört.

## <a name="cdatetimectrlgetmonthcalstyle"></a><a name="getmonthcalstyle"></a>CDateTimeCtrl::GetMonthCalStyle

Ruft den Stil des Dropdown-Monatskalendersteuerelements ab, das dem aktuellen Datums- und Uhrzeitauswahlsteuerelement zugeordnet ist.

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>Rückgabewert

Der Stil des Dropdown-Monatskalendersteuerelements, bei dem es sich um eine bitweise Kombination (OR) von Datums- und Zeitauswahlsteuerungsstilen handelt. Weitere Informationen finden Sie unter [Monatskalendersteuerungsstile](/windows/win32/Controls/month-calendar-control-styles).

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [DTM_GETMCSTYLE](/windows/win32/Controls/dtm-getmcstyle) Nachricht, die im Windows SDK beschrieben wird.

## <a name="cdatetimectrlgetrange"></a><a name="getrange"></a>CDateTimeCtrl::GetRange

Ruft die aktuellen minimalen und maximal zulässigen Systemzeiten für ein Datums- und Zeitauswahlsteuerelement ab.

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;
```

### <a name="parameters"></a>Parameter

*pMinRange*<br/>
Ein Zeiger auf ein [COleDateTime-Objekt](../../atl-mfc-shared/reference/coledatetime-class.md) oder ein [CTime-Objekt,](../../atl-mfc-shared/reference/ctime-class.md) das die früheste im `CDateTimeCtrl` Objekt zulässige Zeit enthält.

*pMaxRange*<br/>
Ein Zeiger auf `COleDateTime` ein `CTime` Objekt oder ein Objekt, `CDateTimeCtrl` das die letzte im Objekt zulässige Zeit enthält.

### <a name="return-value"></a>Rückgabewert

Ein DWORD-Wert, der Flags enthält, die angeben, welche Bereiche festgelegt sind. Wenn

`return value & GDTR_MAX` == 0

dann ist der zweite Parameter gültig. In ähnlicher Weise, wenn

`return value & GDTR_MIN` == 0

dann ist der erste Parameter gültig.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [DTM_GETRANGE](/windows/win32/Controls/dtm-getrange)Win32-DTM_GETRANGE , wie im Windows SDK beschrieben. In der MFC-Implementierung können `COleDateTime` Sie `CTime` entweder oder Verwendungen angeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

## <a name="cdatetimectrlgettime"></a><a name="gettime"></a>CDateTimeCtrl::GetTime

Ruft die aktuell ausgewählte Uhrzeit aus einem Datums- und `SYSTEMTIME` Uhrzeitauswahlsteuerelement ab und fügt sie in eine angegebene Struktur ein.

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Parameter

*timeDest*<br/>
In der ersten Version ein Verweis auf ein [COleDateTime-Objekt,](../../atl-mfc-shared/reference/coledatetime-class.md) das die Systemzeitinformationen empfängt. In der zweiten Version ein Verweis auf ein [CTime-Objekt,](../../atl-mfc-shared/reference/ctime-class.md) das die Systemzeitinformationen empfängt.

*pTimeDest*<br/>
Ein Zeiger auf die [SYSTEMTIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) um die Systemzeitinformationen zu erhalten. Darf nicht NULL sein.

### <a name="return-value"></a>Rückgabewert

In der ersten Version ungleich Null, wenn `COleDateTime` die Zeit erfolgreich in das Objekt geschrieben wurde; andernfalls 0. In der zweiten und dritten Version ist ein DWORD-Wert gleich dem *dwFlag-Membersatz* in der [NMDATETIMECHANGE-Struktur.](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) Weitere Informationen finden Sie im Abschnitt **"Bemerkungen"** weiter unten.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Meldung [DTM_GETSYSTEMTIME](/windows/win32/Controls/dtm-getsystemtime), wie im Windows SDK beschrieben. In der MFC-Implementierung `GetTime`von `COleDateTime` `CTime` können Sie oder Klassen `SYSTEMTIME` verwenden oder eine Struktur verwenden, um die Zeitinformationen zu speichern.

Der Rückgabewert DWORD in der zweiten und dritten Version oben gibt an, ob das Datums- und Uhrzeitauswahlsteuerelement auf den Status "kein Datum" festgelegt ist, wie im [NMDATETIMECHANGE-Strukturmember](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) *dwFlags*angegeben. Wenn der zurückgegebene Wert GDT_NONE entspricht, wird das Steuerelement auf den Status "kein Datum" festgelegt und verwendet den Stil DTS_SHOWNONE. Wenn der zurückgegebene Wert GDT_VALID entspricht, wird die Systemzeit erfolgreich am Zielspeicherort gespeichert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

## <a name="cdatetimectrlgetidealsize"></a><a name="getidealsize"></a>CDateTimeCtrl::GetIdealSize

Gibt die ideale Größe des Datums- und Uhrzeitauswahlsteuerelements zurück, das zum Anzeigen des aktuellen Datums oder der aktuellen Uhrzeit erforderlich ist.

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*psize*|[out] Zeiger auf [SIZE](/windows/win32/api/windef/ns-windef-size) eine SIZE-Struktur, die die ideale Größe für das Steuerelement enthält.|

### <a name="return-value"></a>Rückgabewert

Der Rückgabewert ist immer TRUE.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [DTM_GETIDEALSIZE](/windows/win32/Controls/dtm-getidealsize) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die Variable *m_dateTimeCtrl*definiert, die für den programmgesteuerten Zugriff auf das Datums- und Uhrzeitauswahlsteuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die ideale Größe abgerufen, um das Datums- und Uhrzeitauswahlsteuerelement anzuzeigen.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

## <a name="cdatetimectrlsetformat"></a><a name="setformat"></a>CDateTimeCtrl::SetFormat

Legt die Anzeige eines Datums- und Uhrzeitauswahlsteuerelements entsprechend einer bestimmten Formatzeichenfolge fest.

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>Parameter

*pstrFormat*<br/>
Ein Zeiger auf eine Null-Termin-Formatzeichenfolge, die die gewünschte Anzeige definiert. Wenn Sie diesen Parameter auf NULL setzen, wird das Steuerelement auf die Standardformatzeichenfolge für den aktuellen Stil zurückgesetzt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

> [!NOTE]
> Die Benutzereingabe bestimmt nicht den Erfolg oder Misserfolg dieses Aufrufs.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [DTM_SETFORMAT](/windows/win32/Controls/dtm-setformat)Win32-DTM_SETFORMAT , wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

## <a name="cdatetimectrlsetmonthcalcolor"></a><a name="setmonthcalcolor"></a>CDateTimeCtrl::SetMonthCalColor

Legt die Farbe für einen bestimmten Teil des Monatskalenders innerhalb eines Datums- und Zeitauswahlsteuerelements fest.

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>Parameter

*Icolor*<br/>
**int-Wert,** der angibt, welchen Bereich des Monatskalendersteuerelements festgelegt werden soll. Dieser Wert kann einer der folgenden sein.

|Wert|Bedeutung|
|-----------|-------------|
|MCSC_BACKGROUND|Legen Sie die Zwischenfarbe zwischen den Monaten fest.|
|MCSC_MONTHBK|Legen Sie die Hintergrundfarbe fest, die innerhalb eines Monats angezeigt wird.|
|MCSC_TEXT|Legen Sie die Farbe fest, die zum Anzeigen von Text innerhalb eines Monats verwendet wird.|
|MCSC_TITLEBK|Legen Sie die Hintergrundfarbe fest, die im Titel des Kalenders angezeigt wird.|
|MCSC_TITLETEXT|Legen Sie die Farbe fest, die zum Anzeigen von Text im Titel des Kalenders verwendet wird.|
|MCSC_TRAILINGTEXT|Legen Sie die Farbe fest, die zum Anzeigen von Kopf- und Trailing-Day-Text verwendet wird. Kopf- und Nachverfolgungstage sind die Tage aus dem vorherigen und den folgenden Monaten, die im aktuellen Kalender angezeigt werden.|

*ref*<br/>
Ein COLORREF-Wert, der die Farbe darstellt, die für den angegebenen Bereich des Monatskalenders festgelegt wird.

### <a name="return-value"></a>Rückgabewert

Ein COLORREF-Wert, der die vorherige Farbeinstellung für den angegebenen Teil des Monatskalendersteuerelements darstellt, wenn er erfolgreich ist. Andernfalls gibt die Nachricht -1 zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [DTM_SETMCCOLOR](/windows/win32/Controls/dtm-setmccolor)Win32-DTM_SETMCCOLOR , wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor).

## <a name="cdatetimectrlsetmonthcalfont"></a><a name="setmonthcalfont"></a>CDateTimeCtrl::SetMonthCalFont

Legt die Schriftart fest, die das Kalendersteuerelement für den untergeordneten Monat des Datums- und Uhrzeitauswahlsteuerelements verwendet.

```
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parameter

*hFont*<br/>
Handle für die Schriftart, die festgelegt wird.

*bZeichnung*<br/>
Gibt an, ob das Steuerelement sofort nach dem Festlegen der Schriftart neu gezeichnet werden soll. Wenn Sie diesen Parameter auf TRUE setzen, wird das Steuerelement selbst neu gezeichnet.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [DTM_SETMCFONT](/windows/win32/Controls/dtm-setmcfont)Win32-DTM_SETMCFONT , wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
> Wenn Sie diesen Code verwenden, sollten Sie einen `CDialog`Member Ihrer -abgeleiteten Klasse mit dem Namen *m_MonthFont* vom Typ `CFont`erstellen.

## <a name="cdatetimectrlsetmonthcalstyle"></a><a name="setmonthcalstyle"></a>CDateTimeCtrl::SetMonthCalStyle

Legt den Stil des Dropdown-Monatskalendersteuerelements fest, das dem aktuellen Datums- und Uhrzeitauswahlsteuerelement zugeordnet ist.

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*dwStyle*|[in] Ein neuer Monatskalender-Steuerelementstil, der eine bitweise Kombination (OR) von Monatskalendersteuerungsstilen ist. Weitere Informationen finden Sie unter [Monatskalendersteuerungsstile](/windows/win32/Controls/month-calendar-control-styles).|

### <a name="return-value"></a>Rückgabewert

Der vorherige Stil des Dropdownmonatskalendersteuerelements.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [DTM_SETMCSTYLE](/windows/win32/Controls/dtm-setmcstyle) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die Variable *m_dateTimeCtrl*definiert, die für den programmgesteuerten Zugriff auf das Datums- und Uhrzeitauswahlsteuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird das Datums- und Uhrzeitauswahlsteuerelement so festgelegt, dass Wochennummern, abgekürzte Namen von Wochentagen und kein Indikator heute angezeigt werden.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

## <a name="cdatetimectrlsetrange"></a><a name="setrange"></a>CDateTimeCtrl::SetRange

Legt die minimalen und maximal zulässigen Systemzeiten für ein Datums- und Zeitauswahlsteuerelement fest.

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);
```

### <a name="parameters"></a>Parameter

*pMinRange*<br/>
Ein Zeiger auf ein [COleDateTime-Objekt](../../atl-mfc-shared/reference/coledatetime-class.md) oder ein [CTime-Objekt,](../../atl-mfc-shared/reference/ctime-class.md) das die früheste im `CDateTimeCtrl` Objekt zulässige Zeit enthält.

*pMaxRange*<br/>
Ein Zeiger auf `COleDateTime` ein `CTime` Objekt oder ein Objekt, `CDateTimeCtrl` das die letzte im Objekt zulässige Zeit enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [DTM_SETRANGE](/windows/win32/Controls/dtm-setrange)Win32-DTM_SETRANGE , wie im Windows SDK beschrieben. In der MFC-Implementierung können `COleDateTime` Sie `CTime` entweder oder Verwendungen angeben. Wenn `COleDateTime` das Objekt den Status NULL hat, wird der Bereich entfernt. Wenn `CTime` der Zeiger `COleDateTime` oder Zeiger NULL ist, wird der Bereich entfernt.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CDateTimeCtrl::GetRange](#getrange).

## <a name="cdatetimectrlsettime"></a><a name="settime"></a>CDateTimeCtrl::SetTime

Legt die Uhrzeit in einem Datums- und Uhrzeitauswahlsteuerelement fest.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>Parameter

*timeNeu*<br/>
Ein Verweis auf ein [COleDateTime-Objekt,](../../atl-mfc-shared/reference/coledatetime-class.md) das das Steuerelement enthält, auf das das Steuerelement festgelegt wird.

*pTimeNew*<br/>
In der zweiten Version oben ein Zeiger auf ein [CTime-Objekt,](../../atl-mfc-shared/reference/ctime-class.md) das die Zeit enthält, auf die das Steuerelement festgelegt wird. In der dritten Version oben ein Zeiger auf eine [SYSTEMTIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) die die Zeit enthält, auf die das Steuerelement festgelegt wird.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Meldung [DTM_SETSYSTEMTIME](/windows/win32/Controls/dtm-setsystemtime), wie im Windows SDK beschrieben. In der MFC-Implementierung `SetTime`von `COleDateTime` können `CTime` Sie die oder `SYSTEMTIME` Klassen verwenden, oder Sie können eine Struktur verwenden, um die Zeitinformationen festzulegen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CMonthCalCtrl-Klasse](../../mfc/reference/cmonthcalctrl-class.md)
