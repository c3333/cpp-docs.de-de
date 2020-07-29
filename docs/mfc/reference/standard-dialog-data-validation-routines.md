---
title: Standardroutinen zur Prüfung der Dialogfelddaten
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
ms.openlocfilehash: 2511e2ec6dbd4e27c0e12e35bdc1cd671bf72eaa
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213982"
---
# <a name="standard-dialog-data-validation-routines"></a>Standardroutinen zur Prüfung der Dialogfelddaten

In diesem Thema werden die Standard Routinen für die Dialog Datenüberprüfung (DDV) aufgelistet, die für allgemeine MFC-Dialogfelder verwendet werden.

> [!NOTE]
> Die Standard Routinen für den Dialog Datenaustausch werden in der Header Datei afxdd_. h definiert. Anwendungen sollten jedoch AFXWIN. h enthalten.

### <a name="ddv-functions"></a>DDV-Funktionen

|||
|-|-|
|[DDV_MaxChars](#ddv_maxchars)|Überprüft, ob die Anzahl der Zeichen in einem angegebenen Steuerelement einen angegebenen Höchstwert nicht überschreitet.|
|[DDV_MinMaxByte](#ddv_minmaxbyte)|Überprüft, ob ein angegebener Steuerelement Wert einen angegebenen **Byte** Bereich nicht überschreitet.|
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|Überprüft, ob ein angegebener Steuerelement Wert einen bestimmten Zeitbereich nicht überschreitet.|
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|Überprüft, ob ein angegebener Steuerelement Wert einen angegebenen Bereich nicht überschreitet **`double`** .|
|[DDV_MinMaxDWord](#ddv_minmaxdword)|Überprüft, ob ein angegebener Steuerelement Wert einen angegebenen **DWORD** -Bereich nicht überschreitet.|
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|Überprüft, ob ein angegebener Steuerelement Wert einen angegebenen Bereich nicht überschreitet **`float`** .|
|[DDV_MinMaxInt](#ddv_minmaxint)|Überprüft, ob ein angegebener Steuerelement Wert einen angegebenen Bereich nicht überschreitet **`int`** .|
|[DDV_MinMaxLong](#ddv_minmaxlong)|Überprüft, ob ein angegebener Steuerelement Wert einen angegebenen Bereich nicht überschreitet **`long`** .|
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|Überprüft, ob ein angegebener Steuerelement Wert einen angegebenen **Longlong** -Bereich nicht überschreitet.|
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|Überprüft, ob ein angegebener Steuerelement Wert einen bestimmten Datumsbereich nicht überschreitet.|
|[DDV_MinMaxShort](#ddv_minmaxshort)|Überprüft, ob ein angegebener Steuerelement Wert einen angegebenen Bereich nicht überschreitet **`short`** .|
|[DDV_MinMaxSlider](#ddv_minmaxslider)|Überprüft, ob ein angegebener Schieberegler-Steuerelement Wert innerhalb des angegebenen Bereichs liegt.|
|[DDV_MinMaxUInt](#ddv_minmaxuint)|Überprüft, ob ein angegebener Steuerelement Wert einen angegebenen **uint** -Bereich nicht überschreitet.|
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|Überprüft, ob ein angegebener Steuerelement Wert zwischen zwei angegebenen Werten liegt.|
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|Überprüft, ob ein angegebener Steuerelement Wert einen angegebenen **ULONGLONG** -Bereich nicht überschreitet.|

## <a name="ddv_maxchars"></a><a name="ddv_maxchars"></a>DDV_MaxChars

Ruft `DDV_MaxChars` auf, um zu überprüfen, ob die Anzahl der Zeichen im Steuerelement, das dem *Wert* zugeordnet ist, nicht mehr als *nchars*

```cpp
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,
    CString const& value,
    int nChars);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*value*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten überprüft werden.

*nchars*<br/>
Die maximal zulässige Anzahl von Zeichen.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialog Datenaustausch und-Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddv_minmaxbyte"></a><a name="ddv_minmaxbyte"></a>DDV_MinMaxByte

Wird aufgerufen `DDV_MinMaxByte` , um zu überprüfen, ob der Wert im dem *Wert* zugeordneten Steuerelement zwischen *MinVal* und *MaxVal*liegt.

```cpp
void AFXAPI DDV_MinMaxByte(
    CDataExchange* pDX,
    BYTE value,
    BYTE minVal,
    BYTE maxVal);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*value*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten überprüft werden.

*MinVal*<br/>
Der Minimalwert (vom Typ Byte) ist zulässig.

*MaxVal*<br/>
Maximal zulässiger Wert (vom Typ "Byte").

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialog Datenaustausch und-Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddv_minmaxdatetime"></a><a name="ddv_minmaxdatetime"></a>DDV_MinMaxDateTime

Wird aufgerufen, `DDV_MinMaxDateTime` um zu überprüfen, ob der Zeit-/Uhrzeitwert im Steuerelement für Datums-und Zeitauswahl ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)), das *refvalue* zugeordnet ist, zwischen *refminrange* und *refmaxrange*fällt.

```cpp
void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,
    CTime& refValue,
    const CTime* refMinRange,
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,
    COleDateTime& refValue,
    const COleDateTime* refMinRange,
    const COleDateTime* refMaxRange);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung. Sie müssen dieses Objekt nicht löschen.

*Ref-Wert*<br/>
Ein Verweis auf ein [ctime](../../atl-mfc-shared/reference/ctime-class.md) -oder ein [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -Objekt, das einer Element Variablen des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts zugeordnet ist. Dieses Objekt enthält die zu validierenden Daten.

*Ref-Bereich*<br/>
Der minimale Datums-/Uhrzeitwert ist zulässig.

*Ref maxrange*<br/>
Der maximal zulässige Datums-/Uhrzeitwert.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialog Datenaustausch und-Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddv_minmaxdouble"></a><a name="ddv_minmaxdouble"></a>DDV_MinMaxDouble

Wird aufgerufen `DDV_MinMaxDouble` , um zu überprüfen, ob der Wert im dem *Wert* zugeordneten Steuerelement zwischen *MinVal* und *MaxVal*liegt.

```cpp
void AFXAPI DDV_MinMaxDouble(
    CDataExchange* pDX,
    double const& value,
    double minVal,
    double maxVal);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*value*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten überprüft werden.

*MinVal*<br/>
Der Minimalwert (vom Typ **`double`** ) ist zulässig.

*MaxVal*<br/>
Maximal zulässiger Wert (vom Typ **`double`** ).

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialog Datenaustausch und-Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddv_minmaxdword"></a><a name="ddv_minmaxdword"></a>DDV_MinMaxDWord

Wird aufgerufen `DDV_MinMaxDWord` , um zu überprüfen, ob der Wert im dem *Wert* zugeordneten Steuerelement zwischen *MinVal* und *MaxVal*liegt.

```cpp
void AFXAPI DDV_MinMaxDWord(
    CDataExchange* pDX,
    DWORD const& value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*value*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten überprüft werden.

*MinVal*<br/>
Der Minimalwert (vom Typ DWORD) ist zulässig.

*MaxVal*<br/>
Der maximal zulässige Wert (vom Typ DWORD) ist zulässig.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialog Datenaustausch und-Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddv_minmaxfloat"></a><a name="ddv_minmaxfloat"></a>DDV_MinMaxFloat

Wird aufgerufen `DDV_MinMaxFloat` , um zu überprüfen, ob der Wert im dem *Wert* zugeordneten Steuerelement zwischen *MinVal* und *MaxVal*liegt.

```cpp
void AFXAPI DDV_MinMaxFloat(
    CDataExchange* pDX,
    float value,
    float minVal,
    float maxVal);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*value*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten überprüft werden.

*MinVal*<br/>
Der Minimalwert (vom Typ **`float`** ) ist zulässig.

*MaxVal*<br/>
Maximal zulässiger Wert (vom Typ **`float`** ).

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialog Datenaustausch und-Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddv_minmaxint"></a><a name="ddv_minmaxint"></a>DDV_MinMaxInt

Wird aufgerufen `DDV_MinMaxInt` , um zu überprüfen, ob der Wert im dem *Wert* zugeordneten Steuerelement zwischen *MinVal* und *MaxVal*liegt.

```cpp
void AFXAPI DDV_MinMaxInt(
    CDataExchange* pDX,
    int value,
    int minVal,
    int maxVal);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*value*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten überprüft werden.

*MinVal*<br/>
Der Minimalwert (vom Typ **`int`** ) ist zulässig.

*MaxVal*<br/>
Maximal zulässiger Wert (vom Typ **`int`** ).

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialog Datenaustausch und-Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddv_minmaxlong"></a><a name="ddv_minmaxlong"></a>DDV_MinMaxLong

Wird aufgerufen `DDV_MinMaxLong` , um zu überprüfen, ob der Wert im dem *Wert* zugeordneten Steuerelement zwischen *MinVal* und *MaxVal*liegt.

```cpp
void AFXAPI DDV_MinMaxLong(
    CDataExchange* pDX,
    long value,
    long minVal,
    long maxVal);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*value*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten überprüft werden.

*MinVal*<br/>
Der Minimalwert (vom Typ **`long`** ) ist zulässig.

*MaxVal*<br/>
Maximal zulässiger Wert (vom Typ **`long`** ).

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialog Datenaustausch und-Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddv_minmaxlonglong"></a><a name="ddv_minmaxlonglong"></a>DDV_MinMaxLongLong

Wird aufgerufen `DDV_MinMaxLongLong` , um zu überprüfen, ob der Wert im dem *Wert* zugeordneten Steuerelement zwischen *MinVal* und *MaxVal*liegt.

```cpp
void AFXAPI DDV_MinMaxLongLong(
    CDataExchange* pDX,
    LONGLONG value,
    LONGLONG minVal,
    LONGLONG maxVal);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*value*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten überprüft werden.

*MinVal*<br/>
Der Minimalwert (vom Typ longlong) ist zulässig.

*MaxVal*<br/>
Der maximal zulässige Wert (vom Typ longlong) ist zulässig.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialog Datenaustausch und-Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddv_minmaxmonth"></a><a name="ddv_minmaxmonth"></a>DDV_MinMaxMonth

Wird aufgerufen, `DDV_MinMaxMonth` um zu überprüfen, ob der Wert für Datum und Uhrzeit im Monatskalender-Steuerelement ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)), das *refvalue* zugeordnet ist, zwischen *refminrange* und *refmaxrange*fällt.

```cpp
void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,
    CTime& refValue,
    const CTime* refMinRange,
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,
    COleDateTime& refValue,
    const COleDateTime* refMinRange,
    const COleDateTime* refMaxRange);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*Ref-Wert*<br/>
Ein Verweis auf ein Objekt vom Typ `CTime` oder `COleDateTime` , das einer Element Variablen des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts zugeordnet ist. Dieses Objekt enthält die zu validierenden Daten. MFC übergibt diesen Verweis, wenn `DDV_MinMaxMonth` aufgerufen wird.

*Ref-Bereich*<br/>
Der minimale Datums-/Uhrzeitwert ist zulässig.

*Ref maxrange*<br/>
Der maximal zulässige Datums-/Uhrzeitwert.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialog Datenaustausch und-Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddv_minmaxshort"></a><a name="ddv_minmaxshort"></a>DDV_MinMaxShort

Wird aufgerufen `DDV_MinMaxShort` , um zu überprüfen, ob der Wert im dem *Wert* zugeordneten Steuerelement zwischen *MinVal* und *MaxVal*liegt.

```cpp
void AFXAPI DDV_MinMaxShort(
    CDataExchange* pDX,
    short value,
    short minVal,
    short maxVal);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*value*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten überprüft werden.

*MinVal*<br/>
Der Minimalwert (vom Typ **`short`** ) ist zulässig.

*MaxVal*<br/>
Maximal zulässiger Wert (vom Typ **`short`** ).

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialog Datenaustausch und-Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddv_minmaxslider"></a><a name="ddv_minmaxslider"></a>DDV_MinMaxSlider

Wird aufgerufen `DDV_MinMaxSlider` , um zu überprüfen, ob der Wert im dem *Wert* zugeordneten Steuerelement zwischen *MinVal* und *MaxVal*liegt.

```cpp
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,
    DWORD value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*value*<br/>
Ein Verweis auf den zu validierenden Wert. Dieser Parameter enthält die aktuelle Thumb-Position des Schieberegler-Steuer Elements oder legt diese fest.

*MinVal*<br/>
Minimal zulässiger Wert.

*MaxVal*<br/>
Maximal zulässiger Wert.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialog Datenaustausch und-Validierung](../../mfc/dialog-data-exchange-and-validation.md). Weitere Informationen zu Schieberegler-Steuerelementen finden [Sie unter Verwenden von CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddv_minmaxuint"></a><a name="ddv_minmaxuint"></a>DDV_MinMaxUInt

Wird aufgerufen `DDV_MinMaxUInt` , um zu überprüfen, ob der Wert im dem *Wert* zugeordneten Steuerelement zwischen *MinVal* und *MaxVal*liegt.

```cpp
void AFXAPI DDV_MinMaxUInt(
    CDataExchange* pDX,
    UINT value,
    UINT minVal,
    UINT maxVal);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*value*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten überprüft werden.

*MinVal*<br/>
Der Minimalwert (vom Typ uint) ist zulässig.

*MaxVal*<br/>
Der maximal zulässige Wert (vom Typ uint) ist zulässig.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialog Datenaustausch und-Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddv_minmaxulonglong"></a><a name="ddv_minmaxulonglong"></a>DDV_MinMaxULongLong

Wird aufgerufen `DDV_MinMaxULongLong` , um zu überprüfen, ob der Wert im dem *Wert* zugeordneten Steuerelement zwischen *MinVal* und *MaxVal*liegt.

```cpp
void AFXAPI DDV_MinMaxULongLong(
    CDataExchange* pDX,
    ULONGLONG value,
    ULONGLONG  minVal ,
    ULONGLONG  maxVal);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*value*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten überprüft werden.

*MinVal*<br/>
Der Minimalwert (vom Typ ULONGLONG) ist zulässig.

*MaxVal*<br/>
Maximal zulässiger Wert (vom Typ ULONGLONG).

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialog Datenaustausch und-Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdd_. h

## <a name="ddv_minmaxunsigned"></a>DDV_MinMaxUnsigned

Wird aufgerufen `DDV_MinMaxUnsigned` , um zu überprüfen, ob der Wert im dem *Wert* zugeordneten Steuerelement zwischen *MinVal* und *MaxVal*liegt.

### <a name="syntax"></a>Syntax

```cpp
   void AFXAPI DDV_MinMaxUnsigned(
       CDataExchange* pDX,
       unsigned value,
       unsigned minVal,
       unsigned maxVal );
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*value*<br/>
Ein Verweis auf eine Member-Variable des Dialog Felds, der Formularansicht oder des Steuerelement Ansichts Objekts, mit dem Daten überprüft werden.

*MinVal*<br/>
Der Minimalwert (vom Typ **`unsigned`** ) ist zulässig.

*MaxVal*<br/>
Maximal zulässiger Wert (vom Typ **`unsigned`** ).

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialog Datenaustausch und-Validierung](../dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdd_. h

## <a name="see-also"></a>Weitere Informationen

[Standard-Dialog Datenaustausch Routinen](standard-dialog-data-exchange-routines.md)<br/>
[MFC-Makros, globale Funktionen und globale Variablen](mfc-macros-and-globals.md)<br/>
[DDX_Slider](standard-dialog-data-exchange-routines.md#ddx_slider)<br/>
[DDX_FieldSlider](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md#ddx_fieldslider)
