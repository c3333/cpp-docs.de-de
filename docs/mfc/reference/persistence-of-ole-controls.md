---
title: Persistenz der OLE-Steuerelemente
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
ms.openlocfilehash: a99757854e23708f86822906c7ef9023701ea06b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214060"
---
# <a name="persistence-of-ole-controls"></a>Persistenz der OLE-Steuerelemente

Eine Funktion von OLE-Steuerelementen ist die Eigenschafts Persistenz (oder Serialisierung), die es dem OLE-Steuerelement ermöglicht, Eigenschaftswerte in eine Datei oder einen Stream zu lesen oder zu schreiben. Eine Containeranwendung kann die Serialisierung verwenden, um die Eigenschaftswerte eines Steuer Elements zu speichern, auch nachdem die Anwendung das Steuerelement zerstört hat. Die Eigenschaftswerte des OLE-Steuer Elements können dann aus der Datei oder dem Datenstrom gelesen werden, wenn eine neue Instanz des Steuer Elements zu einem späteren Zeitpunkt erstellt wird.

### <a name="persistence-of-ole-controls"></a>Persistenz der OLE-Steuerelemente

|||
|-|-|
|[PX_Blob](#px_blob)|Tauscht eine Steuerelement Eigenschaft aus, die Binary Large Object (BLOB)-Daten speichert.|
|[PX_Bool](#px_bool)|Tauscht eine Steuerelement Eigenschaft vom Typ **bool**aus.|
|[PX_Color](#px_color)|Tauscht eine Farb Eigenschaft eines-Steuer Elements aus.|
|[PX_Currency](#px_currency)|Tauscht eine Steuerelement Eigenschaft des Typs **CY**aus.|
|[PX_DataPath](#px_datapath)|Tauscht eine Steuerelement Eigenschaft vom Typ aus `CDataPathProperty` .|
|[PX_Double](#px_double)|Tauscht eine Steuerelement Eigenschaft vom Typ aus **`double`** .|
|[PX_Font](#px_font)|Tauscht eine Schriftart Eigenschaft eines-Steuer Elements aus.|
|[PX_Float](#px_float)|Tauscht eine Steuerelement Eigenschaft vom Typ aus **`float`** .|
|[PX_IUnknown](#px_iunknown)|Tauscht eine Steuerelement Eigenschaft von undefiniertem Typ aus.|
|[PX_Long](#px_long)|Tauscht eine Steuerelement Eigenschaft vom Typ aus **`long`** .|
|[PX_Picture](#px_picture)|Tauscht eine Bild Eigenschaft eines-Steuer Elements aus.|
|[PX_Short](#px_short)|Tauscht eine Steuerelement Eigenschaft vom Typ aus **`short`** .|
|[PX_ULong](#px_ulong)|Tauscht eine Steuerelement Eigenschaft vom Typ **ulong**aus.|
|[PX_UShort](#px_ushort)|Tauscht eine Steuerelement Eigenschaft vom Typ " **UShort**" aus.|
|[Pxstring](#px_string)|Tauscht eine Zeichen folgen-Steuerelement Eigenschaft aus.|
|[PX_VBXFontConvert](#px_vbxfontconvert)|Tauscht die Schriftart bezogenen Eigenschaften eines VBX-Steuer Elements in eine Schriftart Eigenschaft des OLE-Steuer Elements aus.|

Außerdem `AfxOleTypeMatchGuid` wird die globale Funktion bereitgestellt, um eine Entsprechung zwischen einer TYPEDESC und einer angegebenen GUID zu testen.

## <a name="px_blob"></a><a name="px_blob"></a>PX_Blob

Sie können diese Funktion innerhalb der Member-Funktion des Steuer Elements `DoPropExchange` zum Serialisieren oder Initialisieren einer Eigenschaft, die Binary Large Object (BLOB)-Daten speichert, abrufen.

```cpp
BOOL PX_Blob(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    HGLOBAL& hBlob,
    HGLOBAL hBlobDefault = NULL);
```

### <a name="parameters"></a>Parameter

*PPX*<br/>
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an übergeben `DoPropExchange` ).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*hblob*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*hblobdefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird von der Variablen, auf die von *hblob*verwiesen wird, gelesen oder in diese geschrieben. Diese Variable sollte mit NULL initialisiert werden, bevor Sie `PX_Blob` zum ersten Mal aufgerufen wird (in der Regel kann dies im Konstruktor des Steuer Elements erfolgen). Wenn *hblobdefault* angegeben wird, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Initialisierungs-oder Serialisierungsprozess des-Steuer Elements aus irgendeinem Grund fehlschlägt.

Die Handles *hblob* und *hblobdefault* verweisen auf einen Speicherblock, der Folgendes enthält:

- Ein DWORD, das die Länge der folgenden Binärdaten (in Bytes) enthält, gefolgt von

- Ein Speicherblock, der die eigentlichen Binärdaten enthält.

Beachten Sie, dass `PX_Blob` beim Laden von BLOB-Typeigenschaften mithilfe der Windows [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) -API Arbeitsspeicher belegt. Sie sind dafür verantwortlich, diesen Arbeitsspeicher freizugeben. Daher sollte der Dekonstruktor des Steuer Elements [Global Free](/windows/win32/api/winbase/nf-winbase-globalfree) für alle Eigenschaften Handles des BLOB-Typs aufgerufen werden, um den Arbeitsspeicher freizugeben, der dem Steuerelement zugeordnet ist.

## <a name="px_bool"></a><a name="px_bool"></a>PX_Bool

Mit dieser Funktion innerhalb der Member- `DoPropExchange` Funktion des Steuer Elements können Sie eine Eigenschaft des Typs bool Serialisieren oder initialisieren.

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

*PPX*<br/>
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an übergeben `DoPropExchange` ).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*bValue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*bdefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird nach Bedarf aus der Variablen gelesen oder in diese geschrieben, auf die von *bvalue*verwiesen wird. Wenn *bdefault* angegeben wird, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

## <a name="px_color"></a><a name="px_color"></a>PX_Color

Mit dieser Funktion können Sie innerhalb der `DoPropExchange` Member-Funktion des Steuer Elements eine Eigenschaft vom Typ OLE_COLOR Serialisieren oder initialisieren.

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

*PPX*<br/>
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an übergeben `DoPropExchange` ).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*clrvalue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*clrdefault*<br/>
Der Standardwert für die Eigenschaft, wie vom Steuerelement Entwickler definiert.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft *wird nach Bedarf*aus der Variablen gelesen oder in diese geschrieben. Wenn *clrdefault* angegeben wird, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

## <a name="px_currency"></a><a name="px_currency"></a>PX_Currency

Mit dieser Funktion innerhalb der Member- `DoPropExchange` Funktion des Steuer Elements können Sie eine Eigenschaft vom Typ **Currency**Serialisieren oder initialisieren.

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

*PPX*<br/>
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an übergeben `DoPropExchange` ).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*cyvalue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*cydefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird in der Variablen, auf die von *cyvalue*verwiesen wird, gelesen oder in diese geschrieben. Wenn *cydefault* angegeben wird, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

## <a name="px_datapath"></a><a name="px_datapath"></a>PX_DataPath

Verwenden Sie diese Funktion innerhalb der `DoPropExchange` Member-Funktion des Steuer Elements, um eine Daten Pfadeigenschaft des Typs " [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)" zu serialisieren oder zu initialisieren.

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

*PPX*<br/>
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an übergeben `DoPropExchange` ).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*datapathproperty*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Daten Pfad Eigenschaften implementieren asynchrone Steuerelement Eigenschaften. Der Wert der Eigenschaft wird von der Variablen, auf die von *datapathproperty*verwiesen wird, gelesen oder in diese geschrieben.

## <a name="px_double"></a><a name="px_double"></a>PX_Double

Sie können diese Funktion innerhalb der `DoPropExchange` Member-Funktion des Steuer Elements zum Serialisieren oder Initialisieren einer Eigenschaft vom Typ aufruft **`double`** .

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

*PPX*<br/>
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an übergeben `DoPropExchange` ).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*Double-Wert*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*doubledefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird in der Variablen, auf die von *Double value*verwiesen wird, gelesen oder in diese geschrieben. Wenn *Double default* angegeben wird, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

## <a name="px_font"></a><a name="px_font"></a>PX_Font

Sie können diese Funktion innerhalb der `DoPropExchange` Member-Funktion des Steuer Elements zum Serialisieren oder Initialisieren einer Eigenschaft vom Typ Schriftart abrufen.

```cpp
BOOL PX_Font(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC FAR* pFontDesc = NULL,
    LPFONTDISP pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Parameter

*PPX*<br/>
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an übergeben `DoPropExchange` ).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*Raster*<br/>
Ein Verweis auf ein- `CFontHolder` Objekt, das die Font-Eigenschaft enthält.

*pfontde*<br/>
Ein Zeiger auf eine- `FONTDESC` Struktur, die die Werte enthält, die beim Initialisieren des Standardstatus der Schriftart Eigenschaft verwendet werden sollen, falls *pfontdispambient* NULL ist.

*pfontdispambient*<br/>
Ein Zeiger auf die- `IFontDisp` Schnittstelle einer Schriftart, die beim Initialisieren des Standardstatus der Schriftart Eigenschaft verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird `font` bei Bedarf aus einem Verweis gelesen oder geschrieben `CFontHolder` . Wenn *pfontde SC* und *pfontdispambient* angegeben werden, werden Sie bei Bedarf zum Initialisieren des Standardwerts der Eigenschaft verwendet. Diese Werte werden verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt. In der Regel übergeben Sie NULL für *pfontbesc* und den von zurückgegebenen Ambient-Wert `COleControl::AmbientFont` für *pfontdispambient*. Beachten Sie, dass das von zurückgegebene Schriftart Objekt `COleControl::AmbientFont` durch einen-Rückruf der Member-Funktion freigegeben werden muss `IFontDisp::Release` .

## <a name="px_float"></a><a name="px_float"></a>PX_Float

Sie können diese Funktion innerhalb der `DoPropExchange` Member-Funktion des Steuer Elements zum Serialisieren oder Initialisieren einer Eigenschaft vom Typ aufruft **`float`** .

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

*PPX*<br/>
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an übergeben `DoPropExchange` ).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*floatvalue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*floatdefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird in der Variablen, auf die von *floatvalue*verwiesen wird, gelesen oder in diese geschrieben. Wenn *floatdefault* angegeben wird, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

## <a name="px_iunknown"></a><a name="px_iunknown"></a>PX_IUnknown

Aufrufen Sie diese Funktion innerhalb der Member-Funktion des Steuer Elements `DoPropExchange` , um eine Eigenschaft zu serialisieren oder zu initialisieren, die von einem-Objekt mit einer von `IUnknown` abgeleiteten Schnittstelle

```cpp
BOOL PX_IUnknown(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    LPUNKNOWN& pUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault = NULL);
```

### <a name="parameters"></a>Parameter

*PPX*<br/>
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an übergeben `DoPropExchange` ).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*Kro*<br/>
Verweis auf eine Variable, die die-Schnittstelle des-Objekts enthält, das den Wert der-Eigenschaft darstellt.

*IID*<br/>
Eine Schnittstellen-ID, die angibt, welche Schnittstelle des Eigenschafts Objekts vom Steuerelement verwendet wird.

*punkdefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird in der Variablen, auf die von *Punk*verwiesen wird, gelesen oder in diese geschrieben. Wenn " *punkdefault* " angegeben ist, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

## <a name="px_long"></a><a name="px_long"></a>PX_Long

Sie können diese Funktion innerhalb der `DoPropExchange` Member-Funktion des Steuer Elements zum Serialisieren oder Initialisieren einer Eigenschaft vom Typ aufruft **`long`** .

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

*PPX*<br/>
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an übergeben `DoPropExchange` ).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*lValue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*ldefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft *wird nach Bedarf*aus der Variablen gelesen oder in diese geschrieben. Wenn " *ldefault* " angegeben ist, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

## <a name="px_picture"></a><a name="px_picture"></a>PX_Picture

Mit dieser Funktion innerhalb der Member-Funktion des Steuer Elements können Sie `DoPropExchange` eine Bild Eigenschaft des Steuer Elements Serialisieren oder initialisieren.

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

*PPX*<br/>
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an übergeben `DoPropExchange` ).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*PICT*<br/>
Verweis auf ein [CPictureHolder](../../mfc/reference/cpictureholder-class.md) -Objekt, in dem die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*pictdefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft *wird nach Bedarf*aus der Variablen gelesen oder in diese geschrieben. Wenn *pictdefault* angegeben wird, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

## <a name="px_short"></a><a name="px_short"></a>PX_Short

Sie können diese Funktion innerhalb der `DoPropExchange` Member-Funktion des Steuer Elements zum Serialisieren oder Initialisieren einer Eigenschaft vom Typ aufruft **`short`** .

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

*PPX*<br/>
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an übergeben `DoPropExchange` ).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*sValue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*sdefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird in der Variablen, auf die von *sValue*verwiesen wird, gelesen oder in diese geschrieben. Wenn *sdefault* angegeben wird, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

## <a name="px_ulong"></a><a name="px_ulong"></a>PX_ULong

Mit dieser Funktion innerhalb der Member- `DoPropExchange` Funktion des Steuer Elements können Sie eine Eigenschaft des Typs **ulong**Serialisieren oder initialisieren.

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

*PPX*<br/>
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an übergeben `DoPropExchange` ).

*pszPropName*<br/>
Der Name der auszutauschenden Eigenschaft.

*ULValue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*uldefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft wird in der Variablen, auf die von *ULValue*verwiesen wird, gelesen oder in diese geschrieben. Wenn *uldefault* angegeben wird, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

## <a name="px_ushort"></a><a name="px_ushort"></a>PX_UShort

Sie können diese Funktion innerhalb der `DoPropExchange` Member-Funktion des Steuer Elements zum Serialisieren oder Initialisieren einer Eigenschaft vom Typ aufruft **`unsigned short`** .

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

*PPX*<br/>
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an übergeben `DoPropExchange` ).

*pszPropName*<br/>
Der Name der auszutauschenden Eigenschaft.

*Startwert*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*Standardwert*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft *wird nach Bedarf*aus der Variablen gelesen oder in diese geschrieben. Wenn " *Standard* Wert" angegeben wird, wird er als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

## <a name="pxstring"></a><a name="px_string"></a>Pxstring

Mit dieser Funktion können Sie in der Member-Funktion des Steuer Elements `DoPropExchange` eine Zeichen folgen Eigenschaft serialisieren oder initialisieren.

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

*PPX*<br/>
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an übergeben `DoPropExchange` ).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*strValue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*der Standardwert*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Wert der Eigenschaft *wird nach Bedarf*aus der Variablen gelesen oder in diese geschrieben. Wenn "- *Standard* " angegeben ist, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

## <a name="px_vbxfontconvert"></a><a name="px_vbxfontconvert"></a>PX_VBXFontConvert

Mit dieser Funktion können Sie in der Member-Funktion des Steuer Elements `DoPropExchange` eine Schriftart Eigenschaft initialisieren, indem Sie die Schriftart bezogenen Eigenschaften eines VBX-Steuer Elements umrechnen.

```cpp
BOOL PX_VBXFontConvert(
    CPropExchange* pPX,
    CFontHolder& font);
```

### <a name="parameters"></a>Parameter

*PPX*<br/>
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an übergeben `DoPropExchange` ).

*Raster*<br/>
Die Font-Eigenschaft des OLE-Steuer Elements, die die konvertierten VBX-Schriftart bezogenen Eigenschaften enthalten soll.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte nur von einem OLE-Steuerelement verwendet werden, das als direkter Ersatz für ein VBX-Steuerelement konzipiert ist. Wenn in der Visual Basic Entwicklungsumgebung ein Formular mit einem VBX-Steuerelement konvertiert wird, um das entsprechende Replace OLE-Steuerelement zu verwenden, wird die-Funktion des Steuer Elements aufgerufen `IDataObject::SetData` und ein Eigenschaften Satz übergeben, der die Eigenschaften Daten des VBX-Steuer Elements enthält. Dieser Vorgang bewirkt wiederum, dass die Funktion des Steuer Elements `DoPropExchange` aufgerufen wird. `DoPropExchange`kann aufgerufen werden `PX_VBXFontConvert` , um die Schriftart bezogenen Eigenschaften des VBX-Steuer Elements (z. b. FontName, "FontSize" usw.) in die entsprechenden Komponenten der Schriftart Eigenschaft des OLE-Steuer Elements zu konvertieren.

`PX_VBXFontConvert`sollte nur aufgerufen werden, wenn das Steuerelement tatsächlich von einer VBX-Formular Anwendung konvertiert wird. Beispiel:

[!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
