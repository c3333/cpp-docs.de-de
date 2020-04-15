---
title: Persistenz der OLE-Steuerelemente
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
ms.openlocfilehash: 88707da503b1d1cdc809827dc4d1bac0ccad9b5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373013"
---
# <a name="persistence-of-ole-controls"></a>Persistenz der OLE-Steuerelemente

Eine Funktion von OLE-Steuerelementen ist die Eigenschaftpersistenz (oder Serialisierung), die es dem OLE-Steuerelement ermöglicht, Eigenschaftswerte in und aus einer Datei oder einem Stream zu lesen oder zu schreiben. Eine Containeranwendung kann die Serialisierung verwenden, um die Eigenschaftswerte eines Steuerelements zu speichern, auch nachdem die Anwendung das Steuerelement zerstört hat. Die Eigenschaftswerte des OLE-Steuerelements können dann aus der Datei oder dem Stream gelesen werden, wenn zu einem späteren Zeitpunkt eine neue Instanz des Steuerelements erstellt wird.

### <a name="persistence-of-ole-controls"></a>Persistenz der OLE-Steuerelemente

|||
|-|-|
|[PX_Blob](#px_blob)|Tauscht eine Steuerelementeigenschaft aus, die BLOB-Daten (Binary Large Object) speichert.|
|[PX_Bool](#px_bool)|Tauscht eine Steuerelementeigenschaft vom Typ **BOOL**.|
|[PX_Color](#px_color)|Tauscht eine Color-Eigenschaft eines Steuerelements aus.|
|[PX_Currency](#px_currency)|Tauscht eine Steuerelementeigenschaft vom Typ **CY**.|
|[PX_DataPath](#px_datapath)|Tauscht eine Steuerelementeigenschaft vom Typ `CDataPathProperty`.|
|[PX_Double](#px_double)|Tauscht eine Steuerelementeigenschaft vom Typ **double**.|
|[PX_Font](#px_font)|Tauscht eine Schriftarteigenschaft eines Steuerelements aus.|
|[PX_Float](#px_float)|Tauscht eine Steuerelementeigenschaft vom Typ **float**.|
|[PX_IUnknown](#px_iunknown)|Tauscht eine Steuerelementeigenschaft des nicht definierten Typs aus.|
|[PX_Long](#px_long)|Tauscht eine Steuerelementeigenschaft vom Typ **long**.|
|[PX_Picture](#px_picture)|Tauscht eine Bildeigenschaft eines Steuerelements aus.|
|[PX_Short](#px_short)|Tauscht eine Steuerelementeigenschaft vom Typ **short**aus.|
|[PX_ULong](#px_ulong)|Tauscht eine Steuerelementeigenschaft vom Typ **ULONG**.|
|[PX_UShort](#px_ushort)|Tauscht eine Steuerelementeigenschaft vom Typ **USHORT**.|
|[PXstring](#px_string)|Tauscht eine Zeichenzeichenfolgensteuerelementeigenschaft aus.|
|[PX_VBXFontConvert](#px_vbxfontconvert)|Tauscht die schriftartbezogenen Eigenschaften eines VBX-Steuerelements in eine OLE-Steuerelementschriftarteigenschaft.|

Darüber hinaus `AfxOleTypeMatchGuid` wird die globale Funktion bereitgestellt, um eine Übereinstimmung zwischen einer TYPEDESC und einer bestimmten GUID zu testen.

## <a name="px_blob"></a><a name="px_blob"></a>PX_Blob

Rufen Sie diese Funktion `DoPropExchange` innerhalb der Memberfunktion des Steuerelements auf, um eine Eigenschaft zu serialisieren oder zu initialisieren, die bLOB-Binärdaten (BLOB) speichert.

```cpp
BOOL PX_Blob(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    HGLOBAL& hBlob,
    HGLOBAL hBlobDefault = NULL);
```

### <a name="parameters"></a>Parameter

*Ppx*<br/>
Zeiger auf das [CPropExchange-Objekt](../../mfc/reference/cpropexchange-class.md) (in `DoPropExchange`der Regel als Parameter an übergeben).

*pszPropName*<br/>
Der Name der ausgetauschten Eigenschaft.

*hBlob*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Membervariable Ihrer Klasse).

*hBlobDefault*<br/>
Standardwert für die Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Austausch erfolgreich war; 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird aus der Variablen gelesen oder in die Variable geschrieben, auf die von *hBlob*verwiesen wird. Diese Variable sollte auf NULL initialisiert werden, bevor sie zum ersten Mal aufgerufen `PX_Blob` wird (in der Regel kann dies im Konstruktor des Steuerelements erfolgen). Wenn *hBlobDefault* angegeben ist, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn aus irgendeinem Grund der Initialisierungs- oder Serialisierungsprozess des Steuerelements fehlschlägt.

Die Handles *hBlob* und *hBlobDefault* beziehen sich auf einen Speicherblock, der Folgendes enthält:

- Ein DWORD, das die Länge der folgenden Binärdaten in Bytes enthält, gefolgt

- Ein Speicherblock, der die eigentlichen Binärdaten enthält.

Beachten `PX_Blob` Sie, dass beim Laden von BLOB-Typeigenschaften Speicher mithilfe der Windows [GlobalAlloc-API](/windows/win32/api/winbase/nf-winbase-globalalloc) zugewiesen wird. Sie sind dafür verantwortlich, diesen Speicher freizugeben. Daher sollte der Destruktor Ihres Steuerelements [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) für alle BLOB-Typ-Eigenschaftshandles aufrufen, um den Speicher freizugeben, der Ihrem Steuerelement zugewiesen ist.

## <a name="px_bool"></a><a name="px_bool"></a>PX_Bool

Rufen Sie diese Funktion `DoPropExchange` innerhalb der Memberfunktion Ihres Steuerelements auf, um eine Eigenschaft vom Typ BOOL zu serialisieren oder zu initialisieren.

```cpp
BOOL PX_Bool(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    BOOL& bValue);

BOOL PX_Bool(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    BOOL& bValue,
    BOOL bDefault);
```

### <a name="parameters"></a>Parameter

*Ppx*<br/>
Zeiger auf das [CPropExchange-Objekt](../../mfc/reference/cpropexchange-class.md) (in `DoPropExchange`der Regel als Parameter an übergeben).

*pszPropName*<br/>
Der Name der ausgetauschten Eigenschaft.

*bValue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Membervariable Ihrer Klasse).

*bDefault*<br/>
Standardwert für die Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Austausch erfolgreich war; 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird aus der Variablen gelesen oder in die Variable geschrieben, auf die von *bValue*verwiesen wird. Wenn *bDefault* angegeben ist, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn aus irgendeinem Grund der Serialisierungsprozess des Steuerelements fehlschlägt.

## <a name="px_color"></a><a name="px_color"></a>PX_Color

Rufen Sie diese Funktion `DoPropExchange` innerhalb der Memberfunktion Ihres Steuerelements auf, um eine Eigenschaft vom Typ OLE_COLOR zu serialisieren oder zu initialisieren.

```cpp
BOOL PX_Color(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    OLE_COLOR& clrValue);

BOOL PX_Color(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    OLE_COLOR& clrValue,
    OLE_COLOR clrDefault);
```

### <a name="parameters"></a>Parameter

*Ppx*<br/>
Zeiger auf das [CPropExchange-Objekt](../../mfc/reference/cpropexchange-class.md) (in `DoPropExchange`der Regel als Parameter an übergeben).

*pszPropName*<br/>
Der Name der ausgetauschten Eigenschaft.

*clrValue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Membervariable Ihrer Klasse).

*clrDefault*<br/>
Standardwert für die Eigenschaft, wie vom Steuerelemententwickler definiert.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Austausch erfolgreich war; 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird aus der Variablen gelesen oder in die Variable geschrieben, auf die von *clrValue*verwiesen wird. Wenn *clrDefault* angegeben ist, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn aus irgendeinem Grund der Serialisierungsprozess des Steuerelements fehlschlägt.

## <a name="px_currency"></a><a name="px_currency"></a>PX_Currency

Rufen Sie diese Funktion `DoPropExchange` innerhalb der Memberfunktion Ihres Steuerelements auf, um eine Eigenschaft vom Typ **currency**zu serialisieren oder zu initialisieren.

```cpp
BOOL PX_Currency(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CY& cyValue);

BOOL PX_Currency(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CY& cyValue,
    CY cyDefault);
```

### <a name="parameters"></a>Parameter

*Ppx*<br/>
Zeiger auf das [CPropExchange-Objekt](../../mfc/reference/cpropexchange-class.md) (in `DoPropExchange`der Regel als Parameter an übergeben).

*pszPropName*<br/>
Der Name der ausgetauschten Eigenschaft.

*cyValue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Membervariable Ihrer Klasse).

*cyDefault*<br/>
Standardwert für die Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Austausch erfolgreich war; 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird aus der Variablen gelesen oder in die Variable geschrieben, auf die von *cyValue*verwiesen wird. Wenn *cyDefault* angegeben ist, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn aus irgendeinem Grund der Serialisierungsprozess des Steuerelements fehlschlägt.

## <a name="px_datapath"></a><a name="px_datapath"></a>PX_DataPath

Rufen Sie diese Funktion `DoPropExchange` innerhalb der Memberfunktion Ihres Steuerelements auf, um eine Datenpfadeigenschaft vom Typ [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)zu serialisieren oder zu initialisieren.

```cpp
BOOL PX_DataPath(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CDataPathProperty& dataPathProperty);

BOOL PX_DataPath(
    CPropExchange* pPX,
    CDataPathProperty& dataPathProperty);
```

### <a name="parameters"></a>Parameter

*Ppx*<br/>
Zeiger auf das [CPropExchange-Objekt](../../mfc/reference/cpropexchange-class.md) (in `DoPropExchange`der Regel als Parameter an übergeben).

*pszPropName*<br/>
Der Name der ausgetauschten Eigenschaft.

*dataPathProperty*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Membervariable Ihrer Klasse).

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Austausch erfolgreich war; 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Datenpfadeigenschaften implementieren asynchrone Steuerelementeigenschaften. Der Wert der Eigenschaft wird aus der Variablen gelesen oder in die Variable geschrieben, auf die von *dataPathProperty*verwiesen wird.

## <a name="px_double"></a><a name="px_double"></a>PX_Double

Rufen Sie diese Funktion `DoPropExchange` innerhalb der Memberfunktion Ihres Steuerelements auf, um eine Eigenschaft vom Typ **double**zu serialisieren oder zu initialisieren.

```cpp
BOOL PX_Double(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    double& doubleValue);

BOOL PX_Double(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    double& doubleValue,
    double doubleDefault);
```

### <a name="parameters"></a>Parameter

*Ppx*<br/>
Zeiger auf das [CPropExchange-Objekt](../../mfc/reference/cpropexchange-class.md) (in `DoPropExchange`der Regel als Parameter an übergeben).

*pszPropName*<br/>
Der Name der ausgetauschten Eigenschaft.

*doubleValue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Membervariable Ihrer Klasse).

*doubleDefault*<br/>
Standardwert für die Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Austausch erfolgreich war; 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird von der Variablen gelesen oder in die Variable geschrieben, auf die von *doubleValue*verwiesen wird. Wenn *doubleDefault* angegeben ist, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn aus irgendeinem Grund der Serialisierungsprozess des Steuerelements fehlschlägt.

## <a name="px_font"></a><a name="px_font"></a>PX_Font

Rufen Sie diese Funktion `DoPropExchange` innerhalb der Memberfunktion Ihres Steuerelements auf, um eine Eigenschaft vom Typ Fontart zu serialisieren oder zu initialisieren.

```cpp
BOOL PX_Font(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC FAR* pFontDesc = NULL,
    LPFONTDISP pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Parameter

*Ppx*<br/>
Zeiger auf das [CPropExchange-Objekt](../../mfc/reference/cpropexchange-class.md) (in `DoPropExchange`der Regel als Parameter an übergeben).

*pszPropName*<br/>
Der Name der ausgetauschten Eigenschaft.

*Schriftart*<br/>
Ein Verweis `CFontHolder` auf ein Objekt, das die font-Eigenschaft enthält.

*pFontDesc*<br/>
Ein Zeiger auf `FONTDESC` eine Struktur, die die Werte enthält, die beim Initialisieren des Standardstatus der font-Eigenschaft verwendet werden sollen, wenn *pFontDispAmbient* NULL ist.

*pFontDispAmbient*<br/>
Ein Zeiger auf `IFontDisp` die Schnittstelle einer Schriftart, die zum Initialisieren des Standardstatus der font-Eigenschaft verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Austausch erfolgreich war; 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird aus `font`einem `CFontHolder` Verweis gelesen oder ggf. in einen Verweis geschrieben. Wenn *pFontDesc* und *pFontDispAmbient* angegeben werden, werden sie bei Bedarf zum Initialisieren des Standardwerts der Eigenschaft verwendet. Diese Werte werden verwendet, wenn aus irgendeinem Grund der Serialisierungsprozess des Steuerelements fehlschlägt. In der Regel übergeben Sie NULL für *pFontDesc* und den Umgebungswert, der für `COleControl::AmbientFont` *pFontDispAmbient*zurückgegeben wird. Beachten Sie, dass `COleControl::AmbientFont` das von zurückgegebene Schriftartobjekt durch einen Aufruf der `IFontDisp::Release` Memberfunktion freigegeben werden muss.

## <a name="px_float"></a><a name="px_float"></a>PX_Float

Rufen Sie diese Funktion `DoPropExchange` innerhalb der Memberfunktion Ihres Steuerelements auf, um eine Eigenschaft vom Typ **float**zu serialisieren oder zu initialisieren.

```cpp
BOOL PX_Float(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    float& floatValue);

BOOL PX_Float(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    float& floatValue,
    float floatDefault);
```

### <a name="parameters"></a>Parameter

*Ppx*<br/>
Zeiger auf das [CPropExchange-Objekt](../../mfc/reference/cpropexchange-class.md) (in `DoPropExchange`der Regel als Parameter an übergeben).

*pszPropName*<br/>
Der Name der ausgetauschten Eigenschaft.

*floatValue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Membervariable Ihrer Klasse).

*floatDefault*<br/>
Standardwert für die Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Austausch erfolgreich war; 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird aus der Variablen gelesen oder in die Variable geschrieben, auf die von *floatValue*verwiesen wird. Wenn *floatDefault* angegeben ist, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn aus irgendeinem Grund der Serialisierungsprozess des Steuerelements fehlschlägt.

## <a name="px_iunknown"></a><a name="px_iunknown"></a>PX_IUnknown

Rufen Sie diese Funktion `DoPropExchange` innerhalb der Memberfunktion des Steuerelements auf, um `IUnknown`eine Eigenschaft zu serialisieren oder zu initialisieren, die durch ein Objekt mit einer -abgeleiteten Schnittstelle dargestellt wird.

```cpp
BOOL PX_IUnknown(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    LPUNKNOWN& pUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault = NULL);
```

### <a name="parameters"></a>Parameter

*Ppx*<br/>
Zeiger auf das [CPropExchange-Objekt](../../mfc/reference/cpropexchange-class.md) (in `DoPropExchange`der Regel als Parameter an übergeben).

*pszPropName*<br/>
Der Name der ausgetauschten Eigenschaft.

*Punk*<br/>
Verweis auf eine Variable, die die Schnittstelle des Objekts enthält, die den Wert der Eigenschaft darstellt.

*Iid*<br/>
Eine Schnittstellen-ID, die angibt, welche Schnittstelle des Eigenschaftsobjekts vom Steuerelement verwendet wird.

*pUnkDefault*<br/>
Standardwert für die Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Austausch erfolgreich war; 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird aus der Variablen gelesen oder in die Variable geschrieben, auf die *pUnk*verweist. Wenn *pUnkDefault* angegeben ist, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn aus irgendeinem Grund der Serialisierungsprozess des Steuerelements fehlschlägt.

## <a name="px_long"></a><a name="px_long"></a>PX_Long

Rufen Sie diese Funktion `DoPropExchange` innerhalb der Memberfunktion Ihres Steuerelements auf, um eine Eigenschaft vom Typ **long**zu serialisieren oder zu initialisieren.

```cpp
BOOL PX_Long(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    long& lValue);

BOOL PX_Long(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    long& lValue,
    long lDefault);
```

### <a name="parameters"></a>Parameter

*Ppx*<br/>
Zeiger auf das [CPropExchange-Objekt](../../mfc/reference/cpropexchange-class.md) (in `DoPropExchange`der Regel als Parameter an übergeben).

*pszPropName*<br/>
Der Name der ausgetauschten Eigenschaft.

*Lvalue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Membervariable Ihrer Klasse).

*lStandard*<br/>
Standardwert für die Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Austausch erfolgreich war; 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird aus der Variablen gelesen oder in die Variable geschrieben, auf die von *lValue*verwiesen wird. Wenn *lDefault* angegeben ist, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn aus irgendeinem Grund der Serialisierungsprozess des Steuerelements fehlschlägt.

## <a name="px_picture"></a><a name="px_picture"></a>PX_Picture

Rufen Sie diese Funktion `DoPropExchange` innerhalb der Memberfunktion Ihres Steuerelements auf, um eine Bildeigenschaft Des Steuerelements zu serialisieren oder zu initialisieren.

```cpp
BOOL PX_Picture(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CPictureHolder& pict);

BOOL PX_Picture(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CPictureHolder& pict,
    CPictureHolder& pictDefault);
```

### <a name="parameters"></a>Parameter

*Ppx*<br/>
Zeiger auf das [CPropExchange-Objekt](../../mfc/reference/cpropexchange-class.md) (in `DoPropExchange`der Regel als Parameter an übergeben).

*pszPropName*<br/>
Der Name der ausgetauschten Eigenschaft.

*Pict*<br/>
Verweis auf ein [CPictureHolder-Objekt,](../../mfc/reference/cpictureholder-class.md) in dem die Eigenschaft gespeichert ist (in der Regel eine Membervariable Ihrer Klasse).

*pictDefault*<br/>
Standardwert für die Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Austausch erfolgreich war; 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird von der Variablen gelesen oder in die Variable geschrieben, auf die *pict*verweist. Wenn *pictDefault* angegeben ist, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn aus irgendeinem Grund der Serialisierungsprozess des Steuerelements fehlschlägt.

## <a name="px_short"></a><a name="px_short"></a>PX_Short

Rufen Sie diese Funktion `DoPropExchange` innerhalb der Memberfunktion Ihres Steuerelements auf, um eine Eigenschaft vom Typ **short**zu serialisieren oder zu initialisieren.

```cpp
BOOL PX_Short(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    short& sValue);

BOOL PX_Short(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    short& sValue,
    short sDefault);
```

### <a name="parameters"></a>Parameter

*Ppx*<br/>
Zeiger auf das [CPropExchange-Objekt](../../mfc/reference/cpropexchange-class.md) (in `DoPropExchange`der Regel als Parameter an übergeben).

*pszPropName*<br/>
Der Name der ausgetauschten Eigenschaft.

*sValue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Membervariable Ihrer Klasse).

*sDefault*<br/>
Standardwert für die Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Austausch erfolgreich war; 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird aus der Variablen gelesen oder in die Variable geschrieben, auf die von *sValue*verwiesen wird. Wenn *sDefault* angegeben ist, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn aus irgendeinem Grund der Serialisierungsprozess des Steuerelements fehlschlägt.

## <a name="px_ulong"></a><a name="px_ulong"></a>PX_ULong

Rufen Sie diese Funktion `DoPropExchange` innerhalb der Memberfunktion Ihres Steuerelements auf, um eine Eigenschaft vom Typ **ULONG**zu serialisieren oder zu initialisieren.

```cpp
BOOL PX_ULong(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    ULONG& ulValue);

BOOL PX_ULong(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    ULONG& ulValue,
    long ulDefault);
```

### <a name="parameters"></a>Parameter

*Ppx*<br/>
Zeiger auf das [CPropExchange-Objekt](../../mfc/reference/cpropexchange-class.md) (in `DoPropExchange`der Regel als Parameter an übergeben).

*pszPropName*<br/>
Name der ausgetauschten Eigenschaft.

*ulValue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Membervariable Ihrer Klasse).

*ulDefault*<br/>
Standardwert für die Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Austausch erfolgreich war; 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird aus der Variablen gelesen oder in die Variable geschrieben, auf die von *ulValue*verwiesen wird. Wenn *ulDefault* angegeben ist, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn aus irgendeinem Grund der Serialisierungsprozess des Steuerelements fehlschlägt.

## <a name="px_ushort"></a><a name="px_ushort"></a>PX_UShort

Rufen Sie diese Funktion `DoPropExchange` innerhalb der Memberfunktion Ihres Steuerelements auf, um eine Eigenschaft vom Typ **unsigned short**zu serialisieren oder zu initialisieren.

```cpp
BOOL PX_UShort(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    USHORT& usValue);

BOOL PX_UShort(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    USHORT& usValue,
    USHORT usDefault);
```

### <a name="parameters"></a>Parameter

*Ppx*<br/>
Zeiger auf das [CPropExchange-Objekt](../../mfc/reference/cpropexchange-class.md) (in `DoPropExchange`der Regel als Parameter an übergeben).

*pszPropName*<br/>
Name der ausgetauschten Eigenschaft.

*usValue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Membervariable Ihrer Klasse).

*usDefault*<br/>
Standardwert für die Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Austausch erfolgreich war; 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird aus der Variablen gelesen oder in die Variable geschrieben, auf die von *usValue*verwiesen wird. Wenn *usDefault* angegeben ist, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn aus irgendeinem Grund der Serialisierungsprozess des Steuerelements fehlschlägt.

## <a name="pxstring"></a><a name="px_string"></a>PXstring

Rufen Sie diese Funktion `DoPropExchange` innerhalb der Memberfunktion des Steuerelements auf, um eine Zeichenfolgeneigenschaft zu serialisieren oder zu initialisieren.

```cpp
BOOL PXstring(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CString& strValue);

BOOL PXstring(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CString& strValue,
    CString strDefault);
```

### <a name="parameters"></a>Parameter

*Ppx*<br/>
Zeiger auf das [CPropExchange-Objekt](../../mfc/reference/cpropexchange-class.md) (in `DoPropExchange`der Regel als Parameter an übergeben).

*pszPropName*<br/>
Der Name der ausgetauschten Eigenschaft.

*strValue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Membervariable Ihrer Klasse).

*strDefault*<br/>
Standardwert für die Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Austausch erfolgreich war; 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird aus der Variablen gelesen oder in die Variable geschrieben, auf die von *strValue*verwiesen wird. Wenn *strDefault* angegeben ist, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn aus irgendeinem Grund der Serialisierungsprozess des Steuerelements fehlschlägt.

## <a name="px_vbxfontconvert"></a><a name="px_vbxfontconvert"></a>PX_VBXFontConvert

Rufen Sie diese Funktion `DoPropExchange` innerhalb der Memberfunktion ihres Steuerelements auf, um eine Schriftarteigenschaft zu initialisieren, indem Sie die schriftartbezogenen Eigenschaften eines VBX-Steuerelements konvertieren.

```cpp
BOOL PX_VBXFontConvert(
    CPropExchange* pPX,
    CFontHolder& font);
```

### <a name="parameters"></a>Parameter

*Ppx*<br/>
Zeiger auf das [CPropExchange-Objekt](../../mfc/reference/cpropexchange-class.md) (in `DoPropExchange`der Regel als Parameter an übergeben).

*Schriftart*<br/>
Die font-Eigenschaft des OLE-Steuerelements, das die konvertierten VBX-Schriftarteigenschaften enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Austausch erfolgreich war; 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte nur von einem OLE-Steuerelement verwendet werden, das als direkter Ersatz für ein VBX-Steuerelement konzipiert ist. Wenn die Visual Basic-Entwicklungsumgebung ein Formular konvertiert, das ein VBX-Steuerelement enthält, `IDataObject::SetData` um das entsprechende Ersatz-OLE-Steuerelement zu verwenden, ruft sie die Funktion des Steuerelements auf und übergibt einen Eigenschaftensatz, der die Eigenschaftendaten des VBX-Steuerelements enthält. Dieser Vorgang bewirkt wiederum, dass `DoPropExchange` die Funktion des Steuerelements aufgerufen wird. `DoPropExchange`kann `PX_VBXFontConvert` aufrufen, um die schriftartbezogenen Eigenschaften des VBX-Steuerelements (z. B. "FontName", "FontSize" usw.) in die entsprechenden Komponenten der Schriftarteigenschaft des OLE-Steuerelements zu konvertieren.

`PX_VBXFontConvert`sollte nur aufgerufen werden, wenn das Steuerelement tatsächlich aus einer VBX-Formularanwendung konvertiert wird. Zum Beispiel:

[!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
