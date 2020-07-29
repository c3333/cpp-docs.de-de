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
ms.openlocfilehash: b5a7263ae5cac81508ab2450a530132879ed45b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222822"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>Dialogdatenaustausch-Funktionen für OLE-Steuerelemente

In diesem Thema werden die DDX_OC Funktionen aufgelistet, die zum Austauschen von Daten zwischen einer Eigenschaft eines OLE-Steuer Elements in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts verwendet werden.

### <a name="ddx_oc-functions"></a>DDX_OC Funktionen

|||
|-|-|
|[DDX_OCBool](#ddx_ocbool)|Verwaltet die Übertragung von **booleschen** Daten zwischen einer Eigenschaft eines OLE-Steuer Elements und einem **booleschen** Datenmember.|
|[DDX_OCBoolRO](#ddx_ocboolro)|Verwaltet die Übertragung von **booleschen** Daten zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuer Elements und einem **booleschen** Datenmember.|
|[DDX_OCColor](#ddx_occolor)|Verwaltet die Übertragung von **OLE_COLOR** Daten zwischen einer Eigenschaft eines OLE-Steuer Elements und einem **OLE_COLOR** Datenmember.|
|[DDX_OCColorRO](#ddx_occolorro)|Verwaltet die Übertragung von **OLE_COLOR** Daten zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuer Elements und einem **OLE_COLOR** Datenmember.|
|[DDX_OCFloat](#ddx_ocfloat)|Verwaltet die Übertragung von **`float`** Daten (oder **`double`** ) zwischen einer Eigenschaft eines OLE-Steuer Elements und einem- **`float`** **`double`** Datenmember (oder).|
|[DDX_OCFloatRO](#ddx_ocfloatro)|Verwaltet die Übertragung von **`float`** (oder **`double`** )-Daten zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuer Elements und einem- **`float`** **`double`** Datenmember (oder).|
|[DDX_OCInt](#ddx_ocint)|Verwaltet die Übertragung von **`int`** Daten (oder **`long`** ) zwischen einer Eigenschaft eines OLE-Steuer Elements und einem- **`int`** oder- **`long`** Datenmember (oder).|
|[DDX_OCIntRO](#ddx_ocintro)|Verwaltet die Übertragung von **`int`** Daten (oder **`long`** ) zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuer Elements und einem- **`int`** **`long`** Datenmember (oder).|
|[DDX_OCShort](#ddx_ocshort)|Verwaltet die Übertragung von **`short`** Daten zwischen einer Eigenschaft eines OLE-Steuer Elements und einem **`short`** Datenmember.|
|[DDX_OCShortRO](#ddx_ocshortro)|Verwaltet die Übertragung von **`short`** Daten zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuer Elements und einem **`short`** Datenmember.|
|[DDX_OCText](#ddx_octext)|Verwaltet die Übertragung von **CString** -Daten zwischen einer Eigenschaft eines OLE-Steuer Elements und einem **CString** -Datenmember.|
|[DDX_OCTextRO](#ddx_octextro)|Verwaltet die Übertragung von **CString** -Daten zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuer Elements und einem **CString** -Datenmember.|

## <a name="ddx_ocbool"></a><a name="ddx_ocbool"></a>DDX_OCBool

Die `DDX_OCBool` -Funktion verwaltet die Übertragung von **booleschen** Daten zwischen einer Eigenschaft eines OLE-Steuer Elements in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem **booleschen** Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

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

*DISPID*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header:** afxdisp.h

## <a name="ddx_ocboolro"></a><a name="ddx_ocboolro"></a>DDX_OCBoolRO

Die `DDX_OCBoolRO` -Funktion verwaltet die Übertragung von **booleschen** Daten zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuer Elements in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem **booleschen** Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

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

*DISPID*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="ddx_occolor"></a><a name="ddx_occolor"></a>DDX_OCColor

Die `DDX_OCColor` -Funktion verwaltet die Übertragung von OLE_COLOR Daten zwischen einer Eigenschaft eines OLE-Steuer Elements in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem OLE_COLOR Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

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

*DISPID*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="ddx_occolorro"></a><a name="ddx_occolorro"></a>DDX_OCColorRO

Die `DDX_OCColorRO` -Funktion verwaltet die Übertragung von OLE_COLOR Daten zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuer Elements in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem OLE_COLOR Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

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

*DISPID*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="ddx_ocfloat"></a><a name="ddx_ocfloat"></a>DDX_OCFloat

Die `DDX_OCFloat` -Funktion verwaltet die Übertragung von **`float`** Daten (oder **`double`** ) zwischen einer Eigenschaft eines OLE-Steuer Elements in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem **`float`** (oder **`double`** ) Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

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

*DISPID*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="ddx_ocfloatro"></a><a name="ddx_ocfloatro"></a>DDX_OCFloatRO

Die `DDX_OCFloatRO` -Funktion verwaltet die Übertragung von **`float`** (oder) **`double`** -Daten zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuer Elements in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem **`float`** (oder **`double`** ) Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

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

*DISPID*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="ddx_ocint"></a><a name="ddx_ocint"></a>DDX_OCInt

Die `DDX_OCInt` -Funktion verwaltet die Übertragung von **`int`** Daten (oder **`long`** ) zwischen einer Eigenschaft eines OLE-Steuer Elements in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem **`int`** (oder **`long`** ) Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

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

*DISPID*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="ddx_ocintro"></a><a name="ddx_ocintro"></a>DDX_OCIntRO

Die `DDX_OCIntRO` -Funktion verwaltet die Übertragung von **`int`** (oder) **`long`** -Daten zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuer Elements in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem **`int`** (oder **`long`** ) Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

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

*DISPID*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="ddx_ocshort"></a><a name="ddx_ocshort"></a>DDX_OCShort

Die `DDX_OCShort` -Funktion verwaltet die Übertragung kurzer Daten zwischen einer Eigenschaft eines OLE-Steuer Elements in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem kurzen Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

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

*DISPID*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="ddx_ocshortro"></a><a name="ddx_ocshortro"></a>DDX_OCShortRO

Die `DDX_OCShortRO` -Funktion verwaltet die Übertragung kurzer Daten zwischen einer schreibgeschützten Eigenschaft eines OLE-Steuer Elements in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem kurzen Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

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

*DISPID*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="ddx_octext"></a><a name="ddx_octext"></a>DDX_OCText

Die **DDX_OCText** -Funktion verwaltet die Übertragung von **CString** -Daten zwischen einer Eigenschaft eines OLE-Steuer Elements in einem Dialogfeld, einer Formularansicht oder einem Steuerungs Ansichts Objekt und einem **CString** -Datenmember des Dialog Felds, der Formularansicht oder des Steuerungs Ansichts Objekts.

```cpp
void AFXAPI DDX_OCText(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>Parameter

*pDX*<br/>
Ein Zeiger auf ein **CDataExchange** -Objekt. Das Framework stellt dieses Objekt bereit, um den Kontext des Datenaustauschs herzustellen, darunter seine Richtung.

*nIDC*<br/>
Die ID eines OLE-Steuerelements im Dialogfeld, im Formularansichts- oder Steuerungsansichtsobjekt.

*DISPID*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

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

*DISPID*<br/>
Die Verteiler-ID einer Eigenschaft des Steuerelements.

*value*<br/>
Ein Verweis auf eine Membervariable des Dialogfelds, Formularansichts- oder Steuerungsansichtsobjekts, mit dem Daten ausgetauscht werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
