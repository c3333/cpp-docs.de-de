---
title: Standardroutinen zur Prüfung der Dialogfelddaten
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
ms.openlocfilehash: 83e3e215ec8d66321bbac5a4a308b04ef69dc68c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372904"
---
# <a name="standard-dialog-data-validation-routines"></a>Standardroutinen zur Prüfung der Dialogfelddaten

In diesem Thema werden die Standarddialogdatenvalidierungsroutinen (DDV) aufgeführt, die für allgemeine MFC-Dialogsteuerelemente verwendet werden.

> [!NOTE]
> Die Standardmäßigen Dialogdatenaustauschroutinen sind in der Headerdatei afxdd_.h definiert. Die Anwendungen sollten jedoch afxwin.h enthalten.

### <a name="ddv-functions"></a>DDV-Funktionen

|||
|-|-|
|[DDV_MaxChars](#ddv_maxchars)|Überprüft, ob die Anzahl der Zeichen in einem bestimmten Steuerelementwert ein bestimmtes Maximum nicht überschreitet.|
|[DDV_MinMaxByte](#ddv_minmaxbyte)|Überprüft, ob ein gegebener Steuerelementwert einen bestimmten **BYTE-Bereich** nicht überschreitet.|
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|Überprüft, ob ein gegebener Steuerelementwert einen bestimmten Zeitbereich nicht überschreitet.|
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|Überprüft, ob ein gegebener Steuerelementwert einen bestimmten **doppelten** Bereich nicht überschreitet.|
|[DDV_MinMaxDWord](#ddv_minmaxdword)|Überprüft, ob ein gegebener Steuerelementwert einen bestimmten **DWORD-Bereich** nicht überschreitet.|
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|Überprüft, ob ein gegebener Steuerwert einen bestimmten **Floatbereich** nicht überschreitet.|
|[DDV_MinMaxInt](#ddv_minmaxint)|Überprüft, ob ein gegebener Steuerelementwert einen bestimmten **int-Bereich** nicht überschreitet.|
|[DDV_MinMaxLong](#ddv_minmaxlong)|Überprüft, ob ein gegebener Kontrollwert einen bestimmten **langen** Bereich nicht überschreitet.|
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|Überprüft, ob ein gegebener Steuerelementwert einen bestimmten **LONGLONG-Bereich** nicht überschreitet.|
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|Überprüft, ob ein gegebener Steuerelementwert einen bestimmten Datumsbereich nicht überschreitet.|
|[DDV_MinMaxShort](#ddv_minmaxshort)|Überprüft, ob ein gegebener Kontrollwert einen bestimmten **kurzen** Bereich nicht überschreitet.|
|[DDV_MinMaxSlider](#ddv_minmaxslider)|Überprüft, ob ein gegebener Schieberegler-Steuerwert innerhalb des angegebenen Bereichs liegt.|
|[DDV_MinMaxUInt](#ddv_minmaxuint)|Überprüft, ob ein gegebener Kontrollwert einen bestimmten **UINT-Bereich** nicht überschreitet.|
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|Überprüft, ob ein bestimmter Steuerelementwert zwischen zwei angegebenen Werten liegt.|
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|Überprüft, ob ein gegebener Steuerelementwert einen bestimmten **ULONGLONG-Bereich** nicht überschreitet.|

## <a name="ddv_maxchars"></a><a name="ddv_maxchars"></a>DDV_MaxChars

Rufen `DDV_MaxChars` Sie an, um sicherzustellen, dass die Anzahl der Zeichen im Steuerelement, die dem *Wert* zugeordnet sind, *nChars*nicht überschreitet.

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
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten überprüft werden.

*nChars*<br/>
Maximale Anzahl der zulässigen Zeichen.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialogdatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddv_minmaxbyte"></a><a name="ddv_minmaxbyte"></a>DDV_MinMaxByte

Rufen `DDV_MinMaxByte` Sie auf, um zu überprüfen, ob der Wert im Steuerelement, das *dem Wert* zugeordnet ist, zwischen *minVal* und *maxVal*liegt.

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
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten überprüft werden.

*minVal*<br/>
Minimalwert (vom Typ BYTE) zulässig.

*maxVal*<br/>
Maximaler Wert (vom Typ BYTE) zulässig.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialogdatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddv_minmaxdatetime"></a><a name="ddv_minmaxdatetime"></a>DDV_MinMaxDateTime

Rufen `DDV_MinMaxDateTime` Sie an, um zu überprüfen, ob der Zeit-/Datumswert im Datums- und Uhrzeitauswahlsteuerelement ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)), das *refValue* zugeordnet ist, zwischen *refMinRange* und *refMaxRange*liegt.

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
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md) Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung. Sie müssen dieses Objekt nicht löschen.

*refValue*<br/>
Ein Verweis auf ein [CTime-](../../atl-mfc-shared/reference/ctime-class.md) oder [COleDateTime-Objekt,](../../atl-mfc-shared/reference/coledatetime-class.md) das einer Membervariablen des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts zugeordnet ist. Dieses Objekt enthält die zu überprüfenden Daten.

*refMinRange*<br/>
Minimaler zulässiger Datums-/Uhrzeitwert.

*refMaxRange*<br/>
Maximaler zulässiger Datums-/Uhrzeitwert.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialogdatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddv_minmaxdouble"></a><a name="ddv_minmaxdouble"></a>DDV_MinMaxDouble

Rufen `DDV_MinMaxDouble` Sie auf, um zu überprüfen, ob der Wert im Steuerelement, das *dem Wert* zugeordnet ist, zwischen *minVal* und *maxVal*liegt.

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
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten überprüft werden.

*minVal*<br/>
Minimalwert (vom Typ **double**) zulässig.

*maxVal*<br/>
Maximaler Wert (vom Typ **double**) zulässig.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialogdatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddv_minmaxdword"></a><a name="ddv_minmaxdword"></a>DDV_MinMaxDWord

Rufen `DDV_MinMaxDWord` Sie auf, um zu überprüfen, ob der Wert im Steuerelement, das *dem Wert* zugeordnet ist, zwischen *minVal* und *maxVal*liegt.

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
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten überprüft werden.

*minVal*<br/>
Minimalwert (vom Typ DWORD) zulässig.

*maxVal*<br/>
Maximaler Wert (vom Typ DWORD) zulässig.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialogdatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddv_minmaxfloat"></a><a name="ddv_minmaxfloat"></a>DDV_MinMaxFloat

Rufen `DDV_MinMaxFloat` Sie auf, um zu überprüfen, ob der Wert im Steuerelement, das *dem Wert* zugeordnet ist, zwischen *minVal* und *maxVal*liegt.

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
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten überprüft werden.

*minVal*<br/>
Minimalwert (vom Typ **float**) zulässig.

*maxVal*<br/>
Maximaler Wert (vom Typ **float**) zulässig.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialogdatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddv_minmaxint"></a><a name="ddv_minmaxint"></a>DDV_MinMaxInt

Rufen `DDV_MinMaxInt` Sie auf, um zu überprüfen, ob der Wert im Steuerelement, das *dem Wert* zugeordnet ist, zwischen *minVal* und *maxVal*liegt.

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
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten überprüft werden.

*minVal*<br/>
Minimalwert (vom Typ **int**) zulässig.

*maxVal*<br/>
Maximaler Wert (vom Typ **int**) zulässig.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialogdatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddv_minmaxlong"></a><a name="ddv_minmaxlong"></a>DDV_MinMaxLong

Rufen `DDV_MinMaxLong` Sie auf, um zu überprüfen, ob der Wert im Steuerelement, das *dem Wert* zugeordnet ist, zwischen *minVal* und *maxVal*liegt.

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
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten überprüft werden.

*minVal*<br/>
Minimalwert (vom Typ **long**) zulässig.

*maxVal*<br/>
Maximaler Wert (vom Typ **long**) zulässig.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialogdatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddv_minmaxlonglong"></a><a name="ddv_minmaxlonglong"></a>DDV_MinMaxLongLong

Rufen `DDV_MinMaxLongLong` Sie auf, um zu überprüfen, ob der Wert im Steuerelement, das *dem Wert* zugeordnet ist, zwischen *minVal* und *maxVal*liegt.

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
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten überprüft werden.

*minVal*<br/>
Minimalwert (vom Typ LONGLONG) zulässig.

*maxVal*<br/>
Maximaler Wert (vom Typ LONGLONG) zulässig.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialogdatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddv_minmaxmonth"></a><a name="ddv_minmaxmonth"></a>DDV_MinMaxMonth

Rufen `DDV_MinMaxMonth` Sie an, um zu überprüfen, ob der Zeit-/Datumswert im Monatskalender-Steuerelement ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)), das *refValue* zugeordnet ist, zwischen *refMinRange* und *refMaxRange*liegt.

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
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md) Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*refValue*<br/>
Ein Verweis auf ein `CTime` `COleDateTime` Objekt vom Typ oder der Membervariablen des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts zugeordnet. Dieses Objekt enthält die zu überprüfenden Daten. MFC übergibt `DDV_MinMaxMonth` diesen Verweis, wenn er aufgerufen wird.

*refMinRange*<br/>
Minimaler zulässiger Datums-/Uhrzeitwert.

*refMaxRange*<br/>
Maximaler zulässiger Datums-/Uhrzeitwert.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialogdatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddv_minmaxshort"></a><a name="ddv_minmaxshort"></a>DDV_MinMaxShort

Rufen `DDV_MinMaxShort` Sie auf, um zu überprüfen, ob der Wert im Steuerelement, das *dem Wert* zugeordnet ist, zwischen *minVal* und *maxVal*liegt.

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
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten überprüft werden.

*minVal*<br/>
Minimalwert (vom Typ **kurz**) zulässig.

*maxVal*<br/>
Maximaler Wert (vom Typ **kurz**) zulässig.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialogdatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddv_minmaxslider"></a><a name="ddv_minmaxslider"></a>DDV_MinMaxSlider

Rufen `DDV_MinMaxSlider` Sie auf, um zu überprüfen, ob der Wert im Steuerelement, das *dem Wert* zugeordnet ist, zwischen *minVal* und *maxVal*liegt.

```cpp
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,
    DWORD value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein [CDataExchange-Objekt.](../../mfc/reference/cdataexchange-class.md) Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*value*<br/>
Ein Verweis auf den zu überprüfenden Wert. Dieser Parameter enthält die aktuelle Daumenposition des Schiebereglers oder legt sie fest.

*minVal*<br/>
Minimalwert zulässig.

*maxVal*<br/>
Maximaler zulässiger Wert.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialogdatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md). Informationen zu Schiebereglern finden Sie unter [Verwenden von CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddv_minmaxuint"></a><a name="ddv_minmaxuint"></a>DDV_MinMaxUInt

Rufen `DDV_MinMaxUInt` Sie auf, um zu überprüfen, ob der Wert im Steuerelement, das *dem Wert* zugeordnet ist, zwischen *minVal* und *maxVal*liegt.

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
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten überprüft werden.

*minVal*<br/>
Minimalwert (vom Typ UINT) zulässig.

*maxVal*<br/>
Maximaler Wert (vom Typ UINT) zulässig.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialogdatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddv_minmaxulonglong"></a><a name="ddv_minmaxulonglong"></a>DDV_MinMaxULongLong

Rufen `DDV_MinMaxULongLong` Sie auf, um zu überprüfen, ob der Wert im Steuerelement, das *dem Wert* zugeordnet ist, zwischen *minVal* und *maxVal*liegt.

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
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten überprüft werden.

*minVal*<br/>
Minimalwert (vom Typ ULONGLONG) zulässig.

*maxVal*<br/>
Maximaler Wert (vom Typ ULONGLONG) zulässig.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialogdatenaustausch und Validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Kopfzeile** afxdd_.h

## <a name="ddv_minmaxunsigned"></a>DDV_MinMaxUnsigned

Rufen `DDV_MinMaxUnsigned` Sie auf, um zu überprüfen, ob der Wert im Steuerelement, das *dem Wert* zugeordnet ist, zwischen *minVal* und *maxVal*liegt.

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
Ein Verweis auf eine Membervariable des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts, mit dem Daten überprüft werden.

*minVal*<br/>
Minimalwert (vom Typ **nicht signiert)** zulässig.

*maxVal*<br/>
Maximaler Wert (vom Typ **nicht signiert** ) zulässig.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu DDV finden Sie unter [Dialogdatenaustausch und Validierung](../dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdd_.h

## <a name="see-also"></a>Siehe auch

[Standard-Dialogdatenaustauschroutinen](standard-dialog-data-exchange-routines.md)<br/>
[MFC-Makros, globale Funktionen und globale Variablen](mfc-macros-and-globals.md)<br/>
[DDX_Slider](standard-dialog-data-exchange-routines.md#ddx_slider)<br/>
[DDX_FieldSlider](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md#ddx_fieldslider)
