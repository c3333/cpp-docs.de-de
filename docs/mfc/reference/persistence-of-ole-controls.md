---
title: Persistenz der OLE-Steuerelemente
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
ms.openlocfilehash: 42e70f9e48339eddb2a5af4fa288400cce01f490
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426642"
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
|[PX_DataPath](#px_datapath)|Tauscht eine Steuerelement Eigenschaft vom Typ `CDataPathProperty`aus.|
|[PX_Double](#px_double)|Tauscht eine Steuerelement Eigenschaft vom Typ **Double**aus.|
|[PX_Font](#px_font)|Tauscht eine Schriftart Eigenschaft eines-Steuer Elements aus.|
|[PX_Float](#px_float)|Tauscht eine Steuerelement Eigenschaft vom Typ **float**aus.|
|[PX_IUnknown](#px_iunknown)|Tauscht eine Steuerelement Eigenschaft von undefiniertem Typ aus.|
|[PX_Long](#px_long)|Tauscht eine Steuerelement Eigenschaft vom Typ **Long**aus.|
|[PX_Picture](#px_picture)|Tauscht eine Bild Eigenschaft eines-Steuer Elements aus.|
|[PX_Short](#px_short)|Tauscht eine Steuerelement Eigenschaft vom Typ **Short**aus.|
|[PX_ULong](#px_ulong)|Tauscht eine Steuerelement Eigenschaft vom Typ **ulong**aus.|
|[PX_UShort](#px_ushort)|Tauscht eine Steuerelement Eigenschaft vom Typ " **UShort**" aus.|
|[Pxstring](#px_string)|Tauscht eine Zeichen folgen-Steuerelement Eigenschaft aus.|
|[PX_VBXFontConvert](#px_vbxfontconvert)|Tauscht die Schriftart bezogenen Eigenschaften eines VBX-Steuer Elements in eine Schriftart Eigenschaft des OLE-Steuer Elements aus.|

Außerdem wird die `AfxOleTypeMatchGuid` globale Funktion bereitgestellt, um eine Entsprechung zwischen einer TYPEDESC und einer angegebenen GUID zu testen.

##  <a name="px_blob"></a>PX_Blob

Sie können diese Funktion innerhalb der `DoPropExchange` Member-Funktion des Steuer Elements zum Serialisieren oder Initialisieren einer Eigenschaft, die Binary Large Object-Daten (BLOB) speichert, abrufen.

```
BOOL PX_Blob(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    HGLOBAL& hBlob,
    HGLOBAL hBlobDefault = NULL);
```

### <a name="parameters"></a>Parameter

*PPX*<br/>
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an `DoPropExchange`übergeben).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*hblob*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*hblobdefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Hinweise

Der Wert der Eigenschaft wird von der Variablen, auf die von *hblob*verwiesen wird, gelesen oder in diese geschrieben. Diese Variable sollte mit NULL initialisiert werden, bevor zunächst `PX_Blob` zum ersten Mal aufgerufen wird (in der Regel kann dies im Konstruktor des Steuer Elements erfolgen). Wenn *hblobdefault* angegeben wird, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Initialisierungs-oder Serialisierungsprozess des-Steuer Elements aus irgendeinem Grund fehlschlägt.

Die Handles *hblob* und *hblobdefault* verweisen auf einen Speicherblock, der Folgendes enthält:

- Ein DWORD, das die Länge der folgenden Binärdaten (in Bytes) enthält, gefolgt von

- Ein Speicherblock, der die eigentlichen Binärdaten enthält.

Beachten Sie, dass `PX_Blob` beim Laden von BLOB-Typeigenschaften mithilfe der Windows [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) -API Arbeitsspeicher zuweist. Sie sind dafür verantwortlich, diesen Arbeitsspeicher freizugeben. Daher sollte der Dekonstruktor des Steuer Elements [Global Free](/windows/win32/api/winbase/nf-winbase-globalfree) für alle Eigenschaften Handles des BLOB-Typs aufgerufen werden, um den Arbeitsspeicher freizugeben, der dem Steuerelement zugeordnet ist.

##  <a name="px_bool"></a>PX_Bool

Diese Funktion wird in der `DoPropExchange` Member-Funktion des Steuer Elements aufgerufen, um eine Eigenschaft des Typs "bool" zu serialisieren oder zu initialisieren.

```
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
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an `DoPropExchange`übergeben).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*bValue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*bdefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Hinweise

Der Wert der Eigenschaft wird nach Bedarf aus der Variablen gelesen oder in diese geschrieben, auf die von *bvalue*verwiesen wird. Wenn *bdefault* angegeben wird, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

##  <a name="px_color"></a>PX_Color

Diese Funktion wird in der `DoPropExchange` Member-Funktion des Steuer Elements aufgerufen, um eine Eigenschaft des Typs OLE_COLOR zu serialisieren oder zu initialisieren.

```
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
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an `DoPropExchange`übergeben).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*clrvalue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*clrdefault*<br/>
Der Standardwert für die Eigenschaft, wie vom Steuerelement Entwickler definiert.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Hinweise

Der Wert der Eigenschaft *wird nach Bedarf*aus der Variablen gelesen oder in diese geschrieben. Wenn *clrdefault* angegeben wird, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

##  <a name="px_currency"></a>PX_Currency

Diese Funktion wird in der `DoPropExchange` Member-Funktion des Steuer Elements aufgerufen, um eine Eigenschaft vom Typ **Currency**zu serialisieren oder zu initialisieren.

```
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
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an `DoPropExchange`übergeben).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*cyvalue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*cydefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Hinweise

Der Wert der Eigenschaft wird in der Variablen, auf die von *cyvalue*verwiesen wird, gelesen oder in diese geschrieben. Wenn *cydefault* angegeben wird, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

##  <a name="px_datapath"></a>PX_DataPath

Verwenden Sie diese Funktion innerhalb der `DoPropExchange` Member-Funktion des Steuer Elements, um eine Daten Pfadeigenschaft des Typs " [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)" zu serialisieren oder zu initialisieren.

```
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
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an `DoPropExchange`übergeben).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*datapathproperty*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Hinweise

Daten Pfad Eigenschaften implementieren asynchrone Steuerelement Eigenschaften. Der Wert der Eigenschaft wird von der Variablen, auf die von *datapathproperty*verwiesen wird, gelesen oder in diese geschrieben.

##  <a name="px_double"></a>PX_Double

Diese Funktion wird in der `DoPropExchange` Member-Funktion des Steuer Elements aufgerufen, um eine Eigenschaft vom Typ " **Double**" zu serialisieren oder zu initialisieren.

```
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
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an `DoPropExchange`übergeben).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*Double-Wert*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*doubledefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Hinweise

Der Wert der Eigenschaft wird in der Variablen, auf die von *Double value*verwiesen wird, gelesen oder in diese geschrieben. Wenn *Double default* angegeben wird, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

##  <a name="px_font"></a>PX_Font

Diese Funktion wird in der `DoPropExchange` Member-Funktion des Steuer Elements aufgerufen, um eine Eigenschaft des Typs "Font" zu serialisieren oder zu initialisieren.

```
BOOL PX_Font(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC FAR* pFontDesc = NULL,
    LPFONTDISP pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Parameter

*PPX*<br/>
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an `DoPropExchange`übergeben).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*Raster*<br/>
Ein Verweis auf ein `CFontHolder` Objekt, das die Eigenschaft Schriftart enthält.

*pfontde*<br/>
Ein Zeiger auf eine `FONTDESC`-Struktur, die die Werte enthält, die beim Initialisieren des Standardstatus der Schriftart Eigenschaft verwendet werden sollen, falls *pfontdispambient* NULL ist.

*pfontdispambient*<br/>
Ein Zeiger auf die `IFontDisp`-Schnittstelle einer Schriftart, die beim Initialisieren des Standardstatus der Schriftart Eigenschaft verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Hinweise

Der Wert der Eigenschaft wird in `font`gelesen oder geschrieben, ein `CFontHolder` Verweis, wenn dies angebracht ist. Wenn *pfontde SC* und *pfontdispambient* angegeben werden, werden Sie bei Bedarf zum Initialisieren des Standardwerts der Eigenschaft verwendet. Diese Werte werden verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt. In der Regel übergeben Sie NULL für *pfontbesc* und den Ambient-Wert, der von `COleControl::AmbientFont` für *pfontdispambient*zurückgegeben wurde. Beachten Sie, dass das von `COleControl::AmbientFont` zurückgegebene Schriftart Objekt durch einen aufzurufenden `IFontDisp::Release` Member-Funktion freigegeben werden muss.

##  <a name="px_float"></a>PX_Float

Diese Funktion wird in der `DoPropExchange` Member-Funktion des Steuer Elements aufgerufen, um eine Eigenschaft vom Typ **float**zu serialisieren oder zu initialisieren.

```
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
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an `DoPropExchange`übergeben).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*floatvalue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*floatdefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Hinweise

Der Wert der Eigenschaft wird in der Variablen, auf die von *floatvalue*verwiesen wird, gelesen oder in diese geschrieben. Wenn *floatdefault* angegeben wird, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

##  <a name="px_iunknown"></a>PX_IUnknown

Aufrufen Sie diese Funktion innerhalb der `DoPropExchange` Member-Funktion des Steuer Elements, um eine Eigenschaft zu serialisieren oder zu initialisieren, die von einem Objekt dargestellt wird, das eine `IUnknown`abgeleitete Schnittstelle

```
BOOL PX_IUnknown(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    LPUNKNOWN& pUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault = NULL);
```

### <a name="parameters"></a>Parameter

*PPX*<br/>
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an `DoPropExchange`übergeben).

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

### <a name="remarks"></a>Hinweise

Der Wert der Eigenschaft wird in der Variablen, auf die von *Punk*verwiesen wird, gelesen oder in diese geschrieben. Wenn " *punkdefault* " angegeben ist, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

##  <a name="px_long"></a>PX_Long

Diese Funktion wird in der `DoPropExchange` Member-Funktion des Steuer Elements aufgerufen, um eine Eigenschaft vom Typ **Long**zu serialisieren oder zu initialisieren.

```
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
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an `DoPropExchange`übergeben).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*lValue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*ldefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Hinweise

Der Wert der Eigenschaft *wird nach Bedarf*aus der Variablen gelesen oder in diese geschrieben. Wenn " *ldefault* " angegeben ist, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

##  <a name="px_picture"></a>PX_Picture

Diese Funktion wird in der `DoPropExchange` Member-Funktion des Steuer Elements aufgerufen, um eine Bild Eigenschaft des Steuer Elements zu serialisieren oder zu initialisieren.

```
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
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an `DoPropExchange`übergeben).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*PICT*<br/>
Verweis auf ein [CPictureHolder](../../mfc/reference/cpictureholder-class.md) -Objekt, in dem die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*pictdefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Hinweise

Der Wert der Eigenschaft *wird nach Bedarf*aus der Variablen gelesen oder in diese geschrieben. Wenn *pictdefault* angegeben wird, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

##  <a name="px_short"></a>PX_Short

Diese Funktion wird in der `DoPropExchange` Member-Funktion des Steuer Elements aufgerufen, um eine Eigenschaft vom Typ **Short**zu serialisieren oder zu initialisieren.

```
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
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an `DoPropExchange`übergeben).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*sValue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*sdefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Hinweise

Der Wert der Eigenschaft wird in der Variablen, auf die von *sValue*verwiesen wird, gelesen oder in diese geschrieben. Wenn *sdefault* angegeben wird, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

##  <a name="px_ulong"></a>PX_ULong

Diese Funktion wird in der `DoPropExchange` Member-Funktion des Steuer Elements aufgerufen, um eine Eigenschaft des Typs **ulong**zu serialisieren oder zu initialisieren.

```
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
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an `DoPropExchange`übergeben).

*pszPropName*<br/>
Der Name der auszutauschenden Eigenschaft.

*ULValue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*uldefault*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Hinweise

Der Wert der Eigenschaft wird in der Variablen, auf die von *ULValue*verwiesen wird, gelesen oder in diese geschrieben. Wenn *uldefault* angegeben wird, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

##  <a name="px_ushort"></a>PX_UShort

Diese Funktion wird in der `DoPropExchange` Member-Funktion des Steuer Elements aufgerufen, um eine Eigenschaft vom Typ **Ganzzahl ohne Vorzeichen Short**zu serialisieren oder zu initialisieren.

```
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
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an `DoPropExchange`übergeben).

*pszPropName*<br/>
Der Name der auszutauschenden Eigenschaft.

*Startwert*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*Standardwert*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Hinweise

Der Wert der Eigenschaft *wird nach Bedarf*aus der Variablen gelesen oder in diese geschrieben. Wenn " *Standard* Wert" angegeben wird, wird er als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

##  <a name="px_string"></a>Pxstring

Diese Funktion wird in der `DoPropExchange` Member-Funktion des Steuer Elements aufgerufen, um eine Zeichen folgen Eigenschaft zu serialisieren oder zu initialisieren.

```
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
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an `DoPropExchange`übergeben).

*pszPropName*<br/>
Der Name der Eigenschaft, die ausgetauscht wird.

*strValue*<br/>
Verweis auf die Variable, in der die Eigenschaft gespeichert ist (in der Regel eine Member-Variable ihrer Klasse).

*der Standardwert*<br/>
Der Standardwert für die-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Hinweise

Der Wert der Eigenschaft *wird nach Bedarf*aus der Variablen gelesen oder in diese geschrieben. Wenn "- *Standard* " angegeben ist, wird es als Standardwert der Eigenschaft verwendet. Dieser Wert wird verwendet, wenn der Serialisierungsprozess des Steuer Elements aus irgendeinem Grund fehlschlägt.

##  <a name="px_vbxfontconvert"></a>PX_VBXFontConvert

Diese Funktion wird in der `DoPropExchange` Member-Funktion des Steuer Elements aufgerufen, um eine Schriftart Eigenschaft zu initialisieren, indem die Schriftart bezogenen Eigenschaften eines VBX-Steuer Elements umgerechnet werden.

```
BOOL PX_VBXFontConvert(
    CPropExchange* pPX,
    CFontHolder& font);
```

### <a name="parameters"></a>Parameter

*PPX*<br/>
Zeiger auf das [CPropExchange](../../mfc/reference/cpropexchange-class.md) -Objekt (in der Regel als Parameter an `DoPropExchange`übergeben).

*Raster*<br/>
Die Font-Eigenschaft des OLE-Steuer Elements, die die konvertierten VBX-Schriftart bezogenen Eigenschaften enthalten soll.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Austausch erfolgreich war. 0, wenn nicht erfolgreich.

### <a name="remarks"></a>Hinweise

Diese Funktion sollte nur von einem OLE-Steuerelement verwendet werden, das als direkter Ersatz für ein VBX-Steuerelement konzipiert ist. Wenn in der Visual Basic Entwicklungsumgebung ein Formular mit einem VBX-Steuerelement konvertiert wird, um das entsprechende Replace OLE-Steuerelement zu verwenden, wird die `IDataObject::SetData`-Funktion des Steuer Elements aufgerufen und ein Eigenschaften Satz übergeben, der die Eigenschaften Daten des VBX-Steuer Elements enthält. Dieser Vorgang bewirkt wiederum, dass die `DoPropExchange` Funktion des Steuer Elements aufgerufen wird. `DoPropExchange` können `PX_VBXFontConvert` zum Konvertieren der Schriftart bezogenen Eigenschaften des VBX-Steuer Elements (z. b. "FontName", "FontSize" usw.) in die entsprechenden Komponenten der Schriftart Eigenschaft des OLE-Steuer Elements aufzurufen.

`PX_VBXFontConvert` sollten nur aufgerufen werden, wenn das Steuerelement tatsächlich von einer VBX-Formular Anwendung konvertiert wird. Beispiel:

[!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]

## <a name="see-also"></a>Siehe auch

[Makros und Globals](../../mfc/reference/mfc-macros-and-globals.md)
