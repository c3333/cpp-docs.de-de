---
title: Dialogdatenaustausch-Funktionen für OLE-Steuerelemente
ms.date: 11/04/2016
f1_keywords:
- AFXDISP/DDX_OCBool
- AFXDISP/DDX_OCBoolRO
- AFXDISP/DDX_OCColor
- AFXDISP/DDX_OCColorRO
- AFXDISP/DDX_OCFloat
- AFXDISP/DDX_OCFloatRO
- AFXDISP/DDX_OCInt
- AFXDISP/DDX_OCIntRO
- AFXDISP/DDX_OCShort
- AFXDISP/DDX_OCShortRO
- AFXDISP/DDX_OCText
- AFXDISP/DDX_OCTextRO
helpviewer_keywords:
- OLE controls [MFC], DDX functions
- DDX (dialog data exchange), OLE support
ms.assetid: 7ef1f288-ff65-40d4-aad2-5497bc00bb27
ms.openlocfilehash: 61a5983eec13902ed4b0e397e3befca4860977d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365764"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>Dialogdatenaustausch-Funktionen für OLE-Steuerelemente

In diesem Thema werden die DDX_OC Funktionen aufgeführt, die zum Austauschen von Daten zwischen einer Eigenschaft eines OLE-Steuerelements in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem Datenmember des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts verwendet werden.

### <a name="ddx_oc-functions"></a>DDX_OC Funktionen

|||
|-|-|
|[DDX_OCBool](#ddx_ocbool)|Verwaltet die Übertragung von **BOOL-Daten** zwischen einer Eigenschaft eines OLE-Steuerelements und einem **BOOL-Datenmember.**|
|[DDX_OCBoolRO](#ddx_ocboolro)|Verwaltet die Übertragung von **BOOL-Daten** zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuerelements und einem **BOOL-Datenmember.**|
|[DDX_OCColor](#ddx_occolor)|Verwaltet die Übertragung **von OLE_COLOR** Daten zwischen einer Eigenschaft eines OLE-Steuerelements und einem OLE_COLOR-Datenmember. **OLE_COLOR**|
|[DDX_OCColorRO](#ddx_occolorro)|Verwaltet die Übertragung **OLE_COLOR** Daten zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuerelements und einem OLE_COLOR-Datenmember. **OLE_COLOR**|
|[DDX_OCFloat](#ddx_ocfloat)|Verwaltet die Übertragung von **float-Daten** (oder **Doppeldaten)** zwischen einer Eigenschaft eines OLE-Steuerelements und einem **float-Datenmember** (oder Double **-Datenmember).**|
|[DDX_OCFloatRO](#ddx_ocfloatro)|Verwaltet die Übertragung von **float-Daten** (oder **Double-Daten)** zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuerelements und einem **float-Datenmember** (oder Double **-Datenmember).**|
|[DDX_OCInt](#ddx_ocint)|Verwaltet die Übertragung von **int** (oder **long**)-Daten zwischen einer Eigenschaft eines OLE-Steuerelements und einem **int** (oder **long**)-Datenmember.|
|[DDX_OCIntRO](#ddx_ocintro)|Verwaltet die Übertragung von **int(oder** **long**)-Daten zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuerelements und einem **int** (oder **long**)-Datenmember.|
|[DDX_OCShort](#ddx_ocshort)|Verwaltet die Übertragung **von kurzen** Daten zwischen einer Eigenschaft eines OLE-Steuerelements und einem **kurzen** Datenmember.|
|[DDX_OCShortRO](#ddx_ocshortro)|Verwaltet die Übertragung **von kurzen** Daten zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuerelements und einem **kurzen** Datenmember.|
|[DDX_OCText](#ddx_octext)|Verwaltet die Übertragung von **CString-Daten** zwischen einer Eigenschaft eines OLE-Steuerelements und einem **CString-Datenmember.**|
|[DDX_OCTextRO](#ddx_octextro)|Verwaltet die Übertragung von **CString-Daten** zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuerelements und einem **CString-Datenmember.**|

## <a name="ddx_ocbool"></a><a name="ddx_ocbool"></a>DDX_OCBool

Die `DDX_OCBool` Funktion verwaltet die Übertragung von **BOOL-Daten** zwischen einer Eigenschaft eines OLE-Steuerelements in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem **BOOL-Datenmember** des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

```cpp
void AFXAPI DDX_OCBool(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines OLE-Steuerelements im Dialogfeld, im Formularansichts- oder Steuerungsansichtsobjekt.

*Dispid*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Header:** afxdisp.h

## <a name="ddx_ocboolro"></a><a name="ddx_ocboolro"></a>DDX_OCBoolRO

Die `DDX_OCBoolRO` Funktion verwaltet die Übertragung von **BOOL-Daten** zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuerelements in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem **BOOL-Datenmember** des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

```cpp
void AFXAPI DDX_OCBoolRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines OLE-Steuerelements im Dialogfeld, im Formularansichts- oder Steuerungsansichtsobjekt.

*Dispid*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="ddx_occolor"></a><a name="ddx_occolor"></a>DDX_OCColor

Die `DDX_OCColor` Funktion verwaltet die Übertragung von OLE_COLOR Daten zwischen einer Eigenschaft eines OLE-Steuerelements in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem OLE_COLOR Datenmember des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

```cpp
void AFXAPI DDX_OCColor(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines OLE-Steuerelements im Dialogfeld, im Formularansichts- oder Steuerungsansichtsobjekt.

*Dispid*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="ddx_occolorro"></a><a name="ddx_occolorro"></a>DDX_OCColorRO

Die `DDX_OCColorRO` Funktion verwaltet die Übertragung von OLE_COLOR Daten zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuerelements in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem OLE_COLOR Datenmember des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

```cpp
void AFXAPI DDX_OCColorRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines OLE-Steuerelements im Dialogfeld, im Formularansichts- oder Steuerungsansichtsobjekt.

*Dispid*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="ddx_ocfloat"></a><a name="ddx_ocfloat"></a>DDX_OCFloat

Die `DDX_OCFloat` Funktion verwaltet die Übertragung von **float-Daten** (oder **Doppeldaten)** zwischen einer Eigenschaft eines OLE-Steuerelements in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem **float-Datenmember** (oder Double **)-Datenmember**des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

```cpp
void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    float& value);

void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    double& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines OLE-Steuerelements im Dialogfeld, im Formularansichts- oder Steuerungsansichtsobjekt.

*Dispid*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="ddx_ocfloatro"></a><a name="ddx_ocfloatro"></a>DDX_OCFloatRO

Die `DDX_OCFloatRO` Funktion verwaltet die Übertragung von **float-Daten** (oder **Doppeldaten)** zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuerelements in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem **float-Datenmember** (oder Double **)-Datenmember**des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

```cpp
void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    float& value);

void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    double& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines OLE-Steuerelements im Dialogfeld, im Formularansichts- oder Steuerungsansichtsobjekt.

*Dispid*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="ddx_ocint"></a><a name="ddx_ocint"></a>DDX_OCInt

Die `DDX_OCInt` Funktion verwaltet die Übertragung von **int** (oder **long**)-Daten zwischen einer Eigenschaft eines OLE-Steuerelements in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem **int** (oder **long**) Datenmember des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

```cpp
void AFXAPI DDX_OCInt(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    int& value);

void AFXAPI DDX_OCInt(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    long& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines OLE-Steuerelements im Dialogfeld, im Formularansichts- oder Steuerungsansichtsobjekt.

*Dispid*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="ddx_ocintro"></a><a name="ddx_ocintro"></a>DDX_OCIntRO

Die `DDX_OCIntRO` Funktion verwaltet die Übertragung von **int** (oder **long**)-Daten zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuerelements in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem **int** (oder **long**)-Datenmember des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

```cpp
void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    int& value);

void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    long& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines OLE-Steuerelements im Dialogfeld, im Formularansichts- oder Steuerungsansichtsobjekt.

*Dispid*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="ddx_ocshort"></a><a name="ddx_ocshort"></a>DDX_OCShort

Die `DDX_OCShort` Funktion verwaltet die Übertragung von kurzen Daten zwischen einer Eigenschaft eines OLE-Steuerelements in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem kurzen Datenmember des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

```cpp
void AFXAPI DDX_OCShort(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines OLE-Steuerelements im Dialogfeld, im Formularansichts- oder Steuerungsansichtsobjekt.

*Dispid*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="ddx_ocshortro"></a><a name="ddx_ocshortro"></a>DDX_OCShortRO

Die `DDX_OCShortRO` Funktion verwaltet die Übertragung von kurzen Daten zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuerelements in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem kurzen Datenelement des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

```cpp
void AFXAPI DDX_OCShortRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines OLE-Steuerelements im Dialogfeld, im Formularansichts- oder Steuerungsansichtsobjekt.

*Dispid*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="ddx_octext"></a><a name="ddx_octext"></a>DDX_OCText

Die **Funktion DDX_OCText** verwaltet die Übertragung von **CString-Daten** zwischen einer Eigenschaft eines OLE-Steuerelements in einem Dialogfeld, einer Formularansicht oder einem Steuerelementansichtsobjekt und einem **CString-Datenmember** des Dialogfelds, der Formularansicht oder des Steuerelementansichtsobjekts.

```cpp
void AFXAPI DDX_OCText(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein **CDataExchange-Objekt.** Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines OLE-Steuerelements im Dialogfeld, im Formularansichts- oder Steuerungsansichtsobjekt.

*Dispid*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="ddx_octextro"></a><a name="ddx_octextro"></a>DDX_OCTextRO

Die `DDX_OCTextRO` -Funktion verwaltet die Übertragung von `CString` -Daten zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuerelements in einem Dialogfeld, einem Formularansichts- oder Steuerungsansichtsobjekts und einem `CString` -Datenelement des Dialogfelds, des Formularansichts- oder Steuerungsansichtsobjekts.

```cpp
void AFXAPI DDX_OCTextRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein `CDataExchange`-Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines OLE-Steuerelements im Dialogfeld, im Formularansichts- oder Steuerungsansichtsobjekt.

*Dispid*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
