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
ms.openlocfilehash: ec9060ba60c4d9877e5ee32bc68da0134f0ccf20
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424446"
---
# <a name="cdatetimectrl-class"></a>CDateTimeCtrl-Klasse

Kapselt die Funktionalität eines Steuerelements für die Datums- und Zeitauswahl.

## <a name="syntax"></a>Syntax

```
class CDateTimeCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CDateTimeCtrl:: CDateTimeCtrl](#cdatetimectrl)|Erstellt ein `CDateTimeCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CDateTimeCtrl:: closemonthcal](#closemonthcal)|Schließt das aktuelle Steuerelement für Datums-und Zeitauswahl.|
|[CDateTimeCtrl:: Create](#create)|Erstellt das Steuerelement für die Datums-und Uhrzeit Auswahl und fügt es an das `CDateTimeCtrl` Objekt an.|
|[CDateTimeCtrl:: getdatetimepickerinfo](#getdatetimepickerinfo)|Ruft Informationen über das aktuelle Steuerelement für Datums-und Zeitauswahl ab.|
|[CDateTimeCtrl:: getidealsize](#getidealsize)|Gibt die ideale Größe des Steuer Elements für die Datums-und Uhrzeit Auswahl zurück, das zum Anzeigen des aktuellen Datums oder der Uhrzeit erforderlich ist.|
|[CDateTimeCtrl:: getmonthcalcolor](#getmonthcalcolor)|Ruft die Farbe für einen bestimmten Teil des Monats Kalenders innerhalb des Datums-und Zeitauswahl Steuer Elements ab.|
|[CDateTimeCtrl:: GetMonthCalCtrl](#getmonthcalctrl)|Ruft das `CMonthCalCtrl` Objekt ab, das dem Steuerelement für die Datums-und Uhrzeit Auswahl zugeordnet ist.|
|[CDateTimeCtrl:: getmonthcalfont](#getmonthcalfont)|Ruft die Schriftart ab, die derzeit vom Steuerelement für den untergeordneten Monatskalender des Datums-und Zeitauswahl Steuer Elements verwendet wird.|
|[CDateTimeCtrl:: getmonthcalstyle](#getmonthcalstyle)|Ruft den Stil des aktuellen Steuer Elements für die Datums-und Uhrzeit Auswahl ab.|
|[CDateTimeCtrl:: GetRange](#getrange)|Ruft die aktuellen minimal-und maximal zulässigen Systemzeiten für ein Steuerelement für Datums-und Zeitauswahl ab.|
|[CDateTimeCtrl:: getTime](#gettime)|Ruft den aktuell ausgewählten Zeitpunkt von einem Steuerelement für die Datums-und Uhrzeit Auswahl ab und legt ihn in einer angegebenen `SYSTEMTIME` Struktur ab.|
|[CDateTimeCtrl:: SetFormat](#setformat)|Legt die Anzeige eines Steuer Elements für die Datums-und Uhrzeit Auswahl in Übereinstimmung mit einer angegebenen Format Zeichenfolge fest.|
|[CDateTimeCtrl:: setmonthcalcolor](#setmonthcalcolor)|Legt die Farbe für einen bestimmten Teil des Monats Kalenders innerhalb eines Datums-und Zeitauswahl Steuer Elements fest.|
|[CDateTimeCtrl:: SetMonthCalFont](#setmonthcalfont)|Legt die Schriftart fest, die vom Steuerelement für den untergeordneten Monatskalender des Datums-und Zeitauswahl Steuer Elements verwendet wird|
|[CDateTimeCtrl:: setmonthcalstyle](#setmonthcalstyle)|Legt den Stil des aktuellen Steuer Elements für die Datums-und Uhrzeit Auswahl fest.|
|[CDateTimeCtrl:: ctrange](#setrange)|Legt die minimalen und maximalen zulässigen Systemzeiten für ein Steuerelement für Datums-und Zeitauswahl fest.|
|[CDateTimeCtrl:: setTime](#settime)|Legt die Zeit in einem Steuerelement für Datums-und Zeitauswahl fest.|

## <a name="remarks"></a>Hinweise

Das Steuerelement für Datums-und Zeitauswahl (DTP-Steuerelement) stellt eine einfache Schnittstelle zum Austauschen von Datums-und Uhrzeit Informationen mit einem Benutzer bereit. Diese Schnittstelle enthält Felder, von denen jede einen Teil der Datums-und Uhrzeit Informationen anzeigt, die im Steuerelement gespeichert sind. Der Benutzer kann die im Steuerelement gespeicherten Informationen ändern, indem er den Inhalt der Zeichenfolge in einem bestimmten Feld ändert. Der Benutzer kann mit der Maus oder der Tastatur von Feld zu Feld wechseln.

Sie können das Steuerelement für die Datums-und Uhrzeit Auswahl anpassen, indem Sie eine Vielzahl von Formaten auf das Objekt anwenden, wenn Sie es erstellen. Weitere Informationen zu den Formatvorlagen für Datums-und Zeitauswahl finden Sie unter [Steuerelement Stile für Datums-und Zeit](/windows/win32/Controls/date-and-time-picker-control-styles) Auswahl im Windows SDK. Sie können das Anzeige Format des DTP-Steuer Elements mithilfe von Format Formaten festlegen. Diese Format Stile werden unter "Format Stile" in den Windows SDK Themen Formatvorlagen für [Datums-und Uhrzeit](/windows/win32/Controls/date-and-time-picker-control-styles)Auswahl beschrieben.

Das Steuerelement für die Datums-und Uhrzeit Auswahl verwendet auch Benachrichtigungen und Rückrufe, die unter [Verwenden von CDateTimeCtrl](../../mfc/using-cdatetimectrl.md)beschrieben werden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>Voraussetzungen

**Header:** afxdtctl. h

##  <a name="cdatetimectrl"></a>CDateTimeCtrl:: CDateTimeCtrl

Erstellt ein `CDateTimeCtrl`-Objekt.

```
CDateTimeCtrl();
```

##  <a name="closemonthcal"></a>CDateTimeCtrl:: closemonthcal

Schließt das aktuelle Steuerelement für Datums-und Zeitauswahl.

```
void CloseMonthCal() const;
```

### <a name="remarks"></a>Hinweise

Diese Methode sendet die [DTM_CLOSEMONTHCAL](/windows/win32/Controls/dtm-closemonthcal) Nachricht, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die-Variable definiert, *m_dateTimeCtrl*, die verwendet wird, um Programm gesteuert auf das Steuerelement für Datums-und Uhrzeit Auswahl zuzugreifen. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird der Dropdown Kalender für das aktuelle Steuerelement für Datums-und Uhrzeit Auswahl geschlossen.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

##  <a name="create"></a>CDateTimeCtrl:: Create

Erstellt das Steuerelement für die Datums-und Uhrzeit Auswahl und fügt es an das `CDateTimeCtrl` Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwstyle*<br/>
Gibt die Kombination von Datums-/uhrzeitsteuerungstyp an Weitere Informationen zu Datums-und Zeitauswahl Formaten finden Sie unter [Steuerelement Stile für Datums-und Zeit](/windows/win32/Controls/date-and-time-picker-control-styles) Auswahl im Windows SDK.

*Rect*<br/>
Ein Verweis auf eine [Rect](/previous-versions/dd162897\(v=vs.85\)) -Struktur, die die Position und Größe des Steuer Elements für die Datums-und Uhrzeit Auswahl ist.

*pparser*<br/>
Ein Zeiger auf ein [CWnd](../../mfc/reference/cwnd-class.md) -Objekt, das das übergeordnete Fenster des Steuer Elements für die Datums-und Uhrzeit Auswahl ist. Er darf nicht NULL sein.

*NID*<br/>
Gibt die Steuerelement-ID des Steuer Elements für Datum und Uhrzeit an.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Erstellung erfolgreich war. andernfalls 0.

### <a name="remarks"></a>Hinweise

##### <a name="to-create-a-date-and-time-picker-control"></a>So erstellen Sie ein Steuerelement für Datums-und Zeitauswahl

1. [CDateTimeCtrl](#cdatetimectrl) zum Erstellen eines `CDateTimeCtrl` Objekts aufzurufen.

1. Mit dieser Member-Funktion wird das Steuerelement für die Datums-und Uhrzeit Auswahl von Windows erstellt und an das `CDateTimeCtrl` Objekt angefügt.

Wenn Sie `Create`aufzurufen, werden die allgemeinen Steuerelemente initialisiert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

##  <a name="getdatetimepickerinfo"></a>CDateTimeCtrl:: getdatetimepickerinfo

Ruft Informationen über das aktuelle Steuerelement für Datums-und Zeitauswahl ab.

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*pdatetimepickerinfo*|vorgenommen Ein Zeiger auf eine [datetimepickerinfo](/windows/win32/api/commctrl/ns-commctrl-datetimepickerinfo) -Struktur, die eine Beschreibung des aktuellen Steuer Elements für die Datums-und Uhrzeit Auswahl empfängt.<br /><br /> Der Aufrufer ist für das Zuordnen dieser Struktur verantwortlich. Diese Methode initialisiert jedoch den *CBSIZE* -Member der-Struktur.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Hinweise

Diese Methode sendet die [DTM_GETDATETIMEPICKERINFO](/windows/win32/Controls/dtm-getdatetimepickerinfo) Nachricht, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die-Variable definiert, *m_dateTimeCtrl*, die verwendet wird, um Programm gesteuert auf das Steuerelement für Datums-und Uhrzeit Auswahl zuzugreifen. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird angegeben, ob Informationen über das aktuelle Steuerelement für Datums-und Uhrzeit Auswahl erfolgreich abgerufen werden.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

##  <a name="getmonthcalcolor"></a>CDateTimeCtrl:: getmonthcalcolor

Ruft die Farbe für einen bestimmten Teil des Monats Kalenders innerhalb des Datums-und Zeitauswahl Steuer Elements ab.

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>Parameter

*iColor*<br/>
Ein **int** -Wert, der angibt, welcher Farbbereich des Monats Kalenders abgerufen werden soll. Eine Liste der Werte finden Sie unter dem *iColor* -Parameter für [setmonthcalcolor](#setmonthcalcolor).

### <a name="return-value"></a>Rückgabewert

Ein COLORREF-Wert, der die Farbeinstellungen für den angegebenen Teil des Monatskalender-Steuer Elements darstellt, wenn erfolgreich. Wenn nicht erfolgreich, gibt die Funktion-1 zurück.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [DTM_GETMCCOLOR](/windows/win32/Controls/dtm-getmccolor), wie in der Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

##  <a name="getmonthcalctrl"></a>CDateTimeCtrl:: GetMonthCalCtrl

Ruft das `CMonthCalCtrl` Objekt ab, das dem Steuerelement für die Datums-und Uhrzeit Auswahl zugeordnet ist.

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) -Objekt oder NULL, wenn es nicht erfolgreich ist oder wenn das Fenster nicht sichtbar ist.

### <a name="remarks"></a>Hinweise

Steuerelemente für die Datums-und Uhrzeit Auswahl erstellen ein untergeordnetes Monatskalender-Steuerelement, wenn der Benutzer auf den Dropdown Pfeil klickt. Wenn das `CMonthCalCtrl` Objekt nicht mehr benötigt wird, wird es zerstört, sodass die Anwendung nicht auf das Speichern des Objekts, das den untergeordneten Monatskalender des Datums-/uhrzeitauswahlsteuerungs darstellt, basieren darf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

##  <a name="getmonthcalfont"></a>CDateTimeCtrl:: getmonthcalfont

Ruft die Schriftart ab, die derzeit vom Monatskalender-Steuerelement des Steuer Elements für Datum und Uhrzeit verwendet wird.

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CFont](../../mfc/reference/cfont-class.md) -Objekt oder NULL, wenn kein Fehler aufgetreten ist.

### <a name="remarks"></a>Hinweise

Das `CFont` Objekt, auf das der Rückgabewert verweist, ist ein temporäres Objekt und wird während der nächsten Leerlauf Verarbeitungszeit zerstört.

##  <a name="getmonthcalstyle"></a>CDateTimeCtrl:: getmonthcalstyle

Ruft den Stil des Dropdown-Monatskalender-Steuer Elements ab, das dem aktuellen Steuerelement für Datums-und Zeitauswahl zugeordnet ist.

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>Rückgabewert

Der Stil des Dropdown Monats-Kalender Steuer Elements, bei dem es sich um eine bitweise Kombination (or) von Steuerelement Stilen für Datums-und Zeitauswahl handelt. Weitere Informationen finden Sie unter [Month Calendar Control Styles](/windows/win32/Controls/month-calendar-control-styles).

### <a name="remarks"></a>Hinweise

Diese Methode sendet die [DTM_GETMCSTYLE](/windows/win32/Controls/dtm-getmcstyle) Nachricht, die in der Windows SDK beschrieben wird.

##  <a name="getrange"></a>CDateTimeCtrl:: GetRange

Ruft die aktuellen minimal-und maximal zulässigen Systemzeiten für ein Steuerelement für Datums-und Zeitauswahl ab.

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;
```

### <a name="parameters"></a>Parameter

*pminrange*<br/>
Ein Zeiger auf ein [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -Objekt oder ein [ctime](../../atl-mfc-shared/reference/ctime-class.md) -Objekt, das die früheste im `CDateTimeCtrl` Objekt zulässige Zeit enthält.

*pmaxrange*<br/>
Ein Zeiger auf ein `COleDateTime` Objekt oder ein `CTime` Objekt, das den letzten zulässigen Zeitpunkt im `CDateTimeCtrl`-Objekt enthält.

### <a name="return-value"></a>Rückgabewert

Ein DWORD-Wert, der Flags enthält, die angeben, welche Bereiche festgelegt sind. Wenn virtuelle Maschinen mit

`return value & GDTR_MAX` == 0

Anschließend ist der zweite Parameter gültig. Ebenso, wenn

`return value & GDTR_MIN` == 0

Anschließend ist der erste Parameter gültig.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [DTM_GETRANGE](/windows/win32/Controls/dtm-getrange), wie in der Windows SDK beschrieben. In der MFC-Implementierung können Sie entweder `COleDateTime` oder `CTime` Verwendungen angeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

##  <a name="gettime"></a>CDateTimeCtrl:: getTime

Ruft den aktuell ausgewählten Zeitpunkt von einem Steuerelement für die Datums-und Uhrzeit Auswahl ab und legt ihn in einer angegebenen `SYSTEMTIME` Struktur ab.

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Parameter

*timedest*<br/>
In der ersten Version ein Verweis auf ein [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -Objekt, das die Systemzeit Informationen empfängt. In der zweiten Version ein Verweis auf ein [ctime](../../atl-mfc-shared/reference/ctime-class.md) -Objekt, das die Systemzeit Informationen empfängt.

*ptimedest*<br/>
Ein Zeiger auf die [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) -Struktur, um die Systemzeit Informationen zu erhalten. Darf nicht NULL sein.

### <a name="return-value"></a>Rückgabewert

In der ersten Version ungleich 0 (null), wenn die Uhrzeit erfolgreich in das `COleDateTime` Objekt geschrieben wurde. andernfalls 0. In der zweiten und dritten Version ist ein DWORD-Wert gleich dem *dwFlag* -Member, der in der [nmdatetimechange](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) -Struktur festgelegt ist. Weitere Informationen finden Sie im Abschnitt " **Hinweise** " weiter unten.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [DTM_GETSYSTEMTIME](/windows/win32/Controls/dtm-getsystemtime), wie in der Windows SDK beschrieben. In der MFC-Implementierung von `GetTime`können Sie `COleDateTime`-oder `CTime` Klassen verwenden, oder Sie können eine `SYSTEMTIME` Struktur verwenden, um die Zeit Informationen zu speichern.

Der Rückgabewert DWORD in der zweiten und dritten Version (oben) gibt an, ob das Steuerelement für die Datums-und Uhrzeit Auswahl auf den Status "kein Datum" festgelegt ist, wie in den *dwFlags*der [nmdatetimechange](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) -Strukturmember angegeben. Wenn der zurückgegebene Wert GDT_NONE ist, wird das Steuerelement auf den Status "kein Date" festgelegt und verwendet den DTS_SHOWNONE-Stil. Wenn der zurückgegebene Wert GDT_VALID ist, wird die Systemzeit erfolgreich am Ziel Speicherort gespeichert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

##  <a name="getidealsize"></a>CDateTimeCtrl:: getidealsize

Gibt die ideale Größe des Steuer Elements für die Datums-und Uhrzeit Auswahl zurück, das zum Anzeigen des aktuellen Datums oder der Uhrzeit erforderlich ist.

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*Psize*|vorgenommen Ein Zeiger auf eine [Größen](/windows/win32/api/windef/ns-windef-size) Struktur, die die ideale Größe für das Steuerelement enthält.|

### <a name="return-value"></a>Rückgabewert

Der Rückgabewert ist immer "true".

### <a name="remarks"></a>Hinweise

Diese Methode sendet die [DTM_GETIDEALSIZE](/windows/win32/Controls/dtm-getidealsize) Nachricht, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die-Variable definiert, *m_dateTimeCtrl*, die verwendet wird, um Programm gesteuert auf das Steuerelement für Datums-und Uhrzeit Auswahl zuzugreifen. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die ideale Größe abgerufen, um das Steuerelement für die Datums-und Uhrzeit Auswahl anzuzeigen.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

##  <a name="setformat"></a>CDateTimeCtrl:: SetFormat

Legt die Anzeige eines Steuer Elements für die Datums-und Uhrzeit Auswahl in Übereinstimmung mit einer angegebenen Format Zeichenfolge fest.

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>Parameter

*pstrinformat*<br/>
Ein Zeiger auf eine NULL terminierte Format Zeichenfolge, die die gewünschte Anzeige definiert. Wenn dieser Parameter auf NULL festgelegt wird, wird das Steuerelement auf die Standardformat Zeichenfolge für den aktuellen Stil zurückgesetzt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

> [!NOTE]
>  Benutzereingaben bestimmen nicht, ob der Vorgang erfolgreich war oder fehlgeschlagen ist.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [DTM_SETFORMAT](/windows/win32/Controls/dtm-setformat), wie in der Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

##  <a name="setmonthcalcolor"></a>CDateTimeCtrl:: setmonthcalcolor

Legt die Farbe für einen bestimmten Teil des Monats Kalenders innerhalb eines Datums-und Zeitauswahl Steuer Elements fest.

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>Parameter

*iColor*<br/>
**int** -Wert, der angibt, welcher Bereich des Monatskalender Steuer Elements festgelegt werden soll. Dieser Wert kann einer der folgenden Werte sein:

|Wert|Bedeutung|
|-----------|-------------|
|MCSC_BACKGROUND|Legen Sie die zwischen den Monaten angezeigte Hintergrundfarbe fest.|
|MCSC_MONTHBK|Legen Sie die im Rahmen eines Monats angezeigte Hintergrundfarbe fest.|
|MCSC_TEXT|Legen Sie die Farbe fest, mit der Text innerhalb eines Monats angezeigt wird.|
|MCSC_TITLEBK|Legen Sie die im Titel des Kalenders angezeigte Hintergrundfarbe fest.|
|MCSC_TITLETEXT|Legen Sie die Farbe fest, die verwendet wird, um Text innerhalb des Kalender Titels anzuzeigen.|
|MCSC_TRAILINGTEXT|Legen Sie die Farbe fest, die verwendet wird, um den Text für die Kopfzeile und den Header und nachfolgende Tage sind die Tage aus den vorherigen und den nächsten Monaten, die im aktuellen Kalender angezeigt werden.|

*ref*<br/>
Ein COLORREF-Wert, der die Farbe darstellt, die für den angegebenen Bereich des Monats Kalenders festgelegt wird.

### <a name="return-value"></a>Rückgabewert

Ein COLORREF-Wert, der die vorherige Farbeinstellung für den angegebenen Teil des Monatskalender-Steuer Elements darstellt, wenn erfolgreich. Andernfalls gibt die Meldung-1 zurück.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [DTM_SETMCCOLOR](/windows/win32/Controls/dtm-setmccolor), wie in der Windows SDK beschrieben.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CDateTimeCtrl:: getmonthcalcolor](#getmonthcalcolor).

##  <a name="setmonthcalfont"></a>CDateTimeCtrl:: SetMonthCalFont

Legt die Schriftart fest, die vom Steuerelement für den untergeordneten Monatskalender des Datums-und Zeitauswahl Steuer Elements verwendet wird

```
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parameter

*hFont*<br/>
Handle für die Schriftart, die festgelegt wird.

*bredraw*<br/>
Gibt an, ob das Steuerelement sofort nach dem Festlegen der Schriftart neu gezeichnet werden soll. Wenn Sie diesen Parameter auf "true" festlegen, wird das Steuerelement neu gezeichnet.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [DTM_SETMCFONT](/windows/win32/Controls/dtm-setmcfont), wie in der Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
>  Wenn Sie diesen Code verwenden, möchten Sie einen Member ihrer `CDialog`abgeleiteten Klasse als *m_MonthFont* vom Typ `CFont`erstellen.

##  <a name="setmonthcalstyle"></a>CDateTimeCtrl:: setmonthcalstyle

Legt den Stil des Dropdown-Monatskalender-Steuer Elements fest, das dem aktuellen Steuerelement für die Datums-und Uhrzeit Auswahl zugeordnet ist.

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*dwstyle*|in Ein neuer Monatskalender-Steuerelement Stil, bei dem es sich um eine bitweise Kombination (or) von Monatskalender-Steuerelement Stilen handelt. Weitere Informationen finden Sie unter [Month Calendar Control Styles](/windows/win32/Controls/month-calendar-control-styles).|

### <a name="return-value"></a>Rückgabewert

Der vorherige Stil des Kalender Steuer Elements für den Dropdown Monat.

### <a name="remarks"></a>Hinweise

Diese Methode sendet die [DTM_SETMCSTYLE](/windows/win32/Controls/dtm-setmcstyle) Nachricht, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die-Variable definiert, *m_dateTimeCtrl*, die verwendet wird, um Programm gesteuert auf das Steuerelement für Datums-und Uhrzeit Auswahl zuzugreifen. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird das Steuerelement für die Datums-und Zeitauswahl so festgelegt, dass Wochen Nummern, abgekürzte Namen von Wochentagen und kein heutiger Indikator angezeigt werden.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

##  <a name="setrange"></a>CDateTimeCtrl:: ctrange

Legt die minimalen und maximalen zulässigen Systemzeiten für ein Steuerelement für Datums-und Zeitauswahl fest.

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);
```

### <a name="parameters"></a>Parameter

*pminrange*<br/>
Ein Zeiger auf ein [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -Objekt oder ein [ctime](../../atl-mfc-shared/reference/ctime-class.md) -Objekt, das die früheste im `CDateTimeCtrl` Objekt zulässige Zeit enthält.

*pmaxrange*<br/>
Ein Zeiger auf ein `COleDateTime` Objekt oder ein `CTime` Objekt, das den letzten zulässigen Zeitpunkt im `CDateTimeCtrl`-Objekt enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [DTM_SETRANGE](/windows/win32/Controls/dtm-setrange), wie in der Windows SDK beschrieben. In der MFC-Implementierung können Sie entweder `COleDateTime` oder `CTime` Verwendungen angeben. Wenn das `COleDateTime` Objekt über einen NULL-Status verfügt, wird der Bereich entfernt. Wenn der `CTime` Zeiger oder der `COleDateTime` Zeiger NULL ist, wird der Bereich entfernt.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CDateTimeCtrl:: GetRange](#getrange).

##  <a name="settime"></a>CDateTimeCtrl:: setTime

Legt die Zeit in einem Steuerelement für Datums-und Zeitauswahl fest.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>Parameter

*timenew*<br/>
Ein Verweis auf ein [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -Objekt, das den enthält, in den das Steuerelement festgelegt wird.

*ptimenew*<br/>
In der zweiten Version oben ein Zeiger auf ein [ctime](../../atl-mfc-shared/reference/ctime-class.md) -Objekt, das die Uhrzeit enthält, zu der das Steuerelement festgelegt wird. In der dritten Version oben ein Zeiger auf eine [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) -Struktur, die die Uhrzeit enthält, zu der das Steuerelement festgelegt wird.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [DTM_SETSYSTEMTIME](/windows/win32/Controls/dtm-setsystemtime), wie in der Windows SDK beschrieben. In der MFC-Implementierung von `SetTime`können Sie die Klassen `COleDateTime` oder `CTime` verwenden, oder Sie können eine `SYSTEMTIME` Struktur verwenden, um die Zeit Informationen festzulegen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CMonthCalCtrl-Klasse](../../mfc/reference/cmonthcalctrl-class.md)
