---
title: CStockPropImpl-Klasse
ms.date: 05/06/2019
f1_keywords:
- CStockPropImpl
- ATLCTL/ATL::CStockPropImpl
- ATLCTL/ATL::get_Appearance
- ATLCTL/ATL::get_AutoSize
- ATLCTL/ATL::get_BackColor
- ATLCTL/ATL::get_BackStyle
- ATLCTL/ATL::get_BorderColor
- ATLCTL/ATL::get_BorderStyle
- ATLCTL/ATL::get_BorderVisible
- ATLCTL/ATL::get_BorderWidth
- ATLCTL/ATL::get_Caption
- ATLCTL/ATL::get_DrawMode
- ATLCTL/ATL::get_DrawStyle
- ATLCTL/ATL::get_DrawWidth
- ATLCTL/ATL::get_Enabled
- ATLCTL/ATL::get_FillColor
- ATLCTL/ATL::get_FillStyle
- ATLCTL/ATL::get_Font
- ATLCTL/ATL::get_ForeColor
- ATLCTL/ATL::get_HWND
- ATLCTL/ATL::get_MouseIcon
- ATLCTL/ATL::get_MousePointer
- ATLCTL/ATL::get_Picture
- ATLCTL/ATL::get_ReadyState
- ATLCTL/ATL::get_TabStop
- ATLCTL/ATL::get_Text
- ATLCTL/ATL::getvalid
- ATLCTL/ATL::get_Window
- ATLCTL/ATL::put_Appearance
- ATLCTL/ATL::put_AutoSize
- ATLCTL/ATL::put_BackColor
- ATLCTL/ATL::put_BackStyle
- ATLCTL/ATL::put_BorderColor
- ATLCTL/ATL::put_BorderStyle
- ATLCTL/ATL::put_BorderVisible
- ATLCTL/ATL::put_BorderWidth
- ATLCTL/ATL::put_Caption
- ATLCTL/ATL::put_DrawMode
- ATLCTL/ATL::put_DrawStyle
- ATLCTL/ATL::put_DrawWidth
- ATLCTL/ATL::put_Enabled
- ATLCTL/ATL::put_FillColor
- ATLCTL/ATL::put_FillStyle
- ATLCTL/ATL::put_Font
- ATLCTL/ATL::put_ForeColor
- ATLCTL/ATL::put_HWND
- ATLCTL/ATL::put_MouseIcon
- ATLCTL/ATL::put_MousePointer
- ATLCTL/ATL::put_Picture
- ATLCTL/ATL::put_ReadyState
- ATLCTL/ATL::put_TabStop
- ATLCTL/ATL::put_Text
- ATLCTL/ATL::putvalid
- ATLCTL/ATL::put_Window
- ATLCTL/ATL::putref_Font
- ATLCTL/ATL::putref_MouseIcon
- ATLCTL/ATL::putref_Picture
helpviewer_keywords:
- CStockPropImpl class
- controls [ATL], stock properties
- stock properties, ATL controls
ms.assetid: 45f11d7d-6580-4a0e-872d-3bc8b836cfda
ms.openlocfilehash: 0aaeb1b6de0febfd5fc0d41cbcc7bad41c607af4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330670"
---
# <a name="cstockpropimpl-class"></a>CStockPropImpl-Klasse

Diese Klasse stellt Methoden zum Unterstützen von Bestandseigenschaftswerten bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <
    class T,
    class InterfaceName,
    const IID* piid = &_ATL_IIDOF(InterfaceName),
    const GUID* plibid = &CComModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0,
    class tihclass = CcomTypeInfoHolder>
class ATL_NO_VTABLE CStockPropImpl :
    public IDispatchImpl<InterfaceName, piid, plibid, wMajor, wMinor, tihclass>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Die Klasse, die das Steuerelement `CStockPropImpl`implementiert und von ableitet.

*InterfaceName*<br/>
Eine duale Schnittstelle, die die Bestandseigenschaften freilegt.

*piid*<br/>
Ein Zeiger auf die `InterfaceName`IID von .

*plibid*<br/>
Ein Zeiger auf die LIBID der Typbibliothek, die die Definition von `InterfaceName`enthält.

*wMajor*<br/>
Die Hauptversion der Typbibliothek Der Standardwert ist 1.

*wMinor*<br/>
Die Nebenversion der Typbibliothek Der Standardwert ist 0.

*tihclass*<br/>
Die Klasse, die zum Verwalten der Typinformationen für *T*verwendet wird. Der Standardwert `CComTypeInfoHolder`ist .

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|[get_Appearance](#get_appearance)|Rufen Sie diese Methode auf, um den Malstil abzurufen, der vom Steuerelement verwendet wird, z. B. flach oder 3D.|
|[get_AutoSize](#get_autosize)|Rufen Sie diese Methode auf, um den Status des Flags abzurufen, das angibt, ob das Steuerelement keine andere Größe haben kann.|
|[get_BackColor](#get_backcolor)|Rufen Sie diese Methode auf, um die Hintergrundfarbe des Steuerelements abzurufen.|
|[get_BackStyle](#get_backstyle)|Rufen Sie diese Methode auf, um den Hintergrundstil des Steuerelements zu erhalten, entweder transparent oder undurchsichtig.|
|[get_BorderColor](#get_bordercolor)|Rufen Sie diese Methode auf, um die Rahmenfarbe des Steuerelements abzurufen.|
|[get_BorderStyle](#get_borderstyle)|Rufen Sie diese Methode auf, um den Rahmenstil des Steuerelements abzurufen.|
|[get_BorderVisible](#get_bordervisible)|Rufen Sie diese Methode auf, um den Status des Flags abzurufen, das angibt, ob der Rahmen des Steuerelements sichtbar ist oder nicht.|
|[get_BorderWidth](#get_borderwidth)|Rufen Sie diese Methode auf, um die Breite (in Pixel) des Rahmens des Steuerelements abzurufen.|
|[get_Caption](#get_caption)|Rufen Sie diese Methode auf, um den in der Beschriftung eines Objekts angegebenen Text abzurufen.|
|[get_DrawMode](#get_drawmode)|Rufen Sie diese Methode auf, um den Zeichnungsmodus des Steuerelements abzurufen, z. B. XOR-Stift oder Invert Colors.|
|[get_DrawStyle](#get_drawstyle)|Rufen Sie diese Methode auf, um den Zeichnungsstil des Steuerelements abzurufen, z. B. Volumenkörper, Gestrichelt oder gepunktet.|
|[get_DrawWidth](#get_drawwidth)|Rufen Sie diese Methode auf, um die Zeichnungsbreite (in Pixel) abzurufen, die von den Zeichnungsmethoden des Steuerelements verwendet wird.|
|[get_Enabled](#get_enabled)|Rufen Sie diese Methode auf, um den Status des Flags abzurufen, das angibt, ob das Steuerelement aktiviert ist.|
|[get_FillColor](#get_fillcolor)|Rufen Sie diese Methode auf, um die Füllfarbe des Steuerelements abzurufen.|
|[get_FillStyle](#get_fillstyle)|Rufen Sie diese Methode auf, um den Füllstil des Steuerelements abzurufen, z. B. fest, transparent oder kreuzgeschlüpft.|
|[get_Font](#get_font)|Rufen Sie diese Methode auf, um einen Zeiger auf die Schriftarteigenschaften des Steuerelements abzurufen.|
|[get_ForeColor](#get_forecolor)|Rufen Sie diese Methode auf, um die Vordergrundfarbe des Steuerelements abzurufen.|
|[get_HWND](#get_hwnd)|Rufen Sie diese Methode auf, um das Fensterhandle abzurufen, das dem Steuerelement zugeordnet ist.|
|[get_MouseIcon](#get_mouseicon)|Rufen Sie diese Methode auf, um die Bildeigenschaften der Grafik (Symbol, Bitmap oder Metadatei) anzuzeigen, wenn sich die Maus über dem Steuerelement befindet.|
|[get_MousePointer](#get_mousepointer)|Rufen Sie diese Methode auf, um den Typ des Mauszeigers anzuzeigen, wenn sich die Maus über dem Steuerelement befindet, z. B. Pfeil, Kreuz oder Sanduhr.|
|[get_Picture](#get_picture)|Rufen Sie diese Methode auf, um einen Zeiger auf die Bildeigenschaften einer Grafik (Symbol, Bitmap oder Metadatei) anzuzeigen.|
|[get_ReadyState](#get_readystate)|Rufen Sie diese Methode auf, um den bereiten Status des Steuerelements abzurufen, z. B. laden oder laden.|
|[get_TabStop](#get_tabstop)|Rufen Sie diese Methode auf, um das Flag abzurufen, das angibt, ob es sich bei dem Steuerelement um einen Tabstopp handelt oder nicht.|
|[get_Text](#get_text)|Rufen Sie diese Methode auf, um den Text abzurufen, der mit dem Steuerelement angezeigt wird.|
|[getvalid](#get_valid)|Rufen Sie diese Methode auf, um den Status des Flags abzurufen, das angibt, ob das Steuerelement gültig ist oder nicht.|
|[get_Window](#get_window)|Rufen Sie diese Methode auf, um das Fensterhandle abzurufen, das dem Steuerelement zugeordnet ist. Identisch mit [CStockPropImpl::get_HWND](#get_hwnd).|
|[put_Appearance](#put_appearance)|Rufen Sie diese Methode auf, um den vom Steuerelement verwendeten Farbstil festzulegen, z. B. flach oder 3D.|
|[put_AutoSize](#put_autosize)|Rufen Sie diese Methode auf, um den Wert des Flags festzulegen, das angibt, ob das Steuerelement keine andere Größe haben kann.|
|[put_BackColor](#put_backcolor)|Rufen Sie diese Methode auf, um die Hintergrundfarbe des Steuerelements festzulegen.|
|[put_BackStyle](#put_backstyle)|Rufen Sie diese Methode auf, um den Hintergrundstil des Steuerelements festzulegen.|
|[put_BorderColor](#put_bordercolor)|Rufen Sie diese Methode auf, um die Rahmenfarbe des Steuerelements festzulegen.|
|[put_BorderStyle](#put_borderstyle)|Rufen Sie diese Methode auf, um den Rahmenstil des Steuerelements festzulegen.|
|[put_BorderVisible](#put_bordervisible)|Rufen Sie diese Methode auf, um den Wert des Flags festzulegen, das angibt, ob der Rahmen des Steuerelements sichtbar ist oder nicht.|
|[put_BorderWidth](#put_borderwidth)|Rufen Sie diese Methode auf, um die Breite des Rahmens des Steuerelements festzulegen.|
|[put_Caption](#put_caption)|Rufen Sie diese Methode auf, um den Text festzulegen, der mit dem Steuerelement angezeigt werden soll.|
|[put_DrawMode](#put_drawmode)|Rufen Sie diese Methode auf, um den Zeichnungsmodus des Steuerelements festzulegen, z. B. XOR-Stift oder Invert Colors.|
|[put_DrawStyle](#put_drawstyle)|Rufen Sie diese Methode auf, um den Zeichnungsstil des Steuerelements festzulegen, z. B. Volumenkörper, Gestrichelt oder gepunktet.|
|[put_DrawWidth](#put_drawwidth)|Rufen Sie diese Methode auf, um die Breite (in Pixel) festzulegen, die von den Zeichenmethoden des Steuerelements verwendet wird.|
|[put_Enabled](#put_enabled)|Rufen Sie diese Methode auf, um das Flag festzulegen, das angibt, ob das Steuerelement aktiviert ist.|
|[put_FillColor](#put_fillcolor)|Rufen Sie diese Methode auf, um die Füllfarbe des Steuerelements festzulegen.|
|[put_FillStyle](#put_fillstyle)|Rufen Sie diese Methode auf, um den Füllstil des Steuerelements festzulegen, z. B. durch fest, transparent oder kreuzgeschlüpft.|
|[put_Font](#put_font)|Rufen Sie diese Methode auf, um die Schriftarteigenschaften des Steuerelements festzulegen.|
|[put_ForeColor](#put_forecolor)|Rufen Sie diese Methode auf, um die Vordergrundfarbe des Steuerelements festzulegen.|
|[put_HWND](#put_hwnd)|Diese Methode gibt E_FAIL zurück.|
|[put_MouseIcon](#put_mouseicon)|Rufen Sie diese Methode auf, um die Bildeigenschaften der Grafik (Symbol, Bitmap oder Metadatei) festzulegen, die angezeigt werden sollen, wenn sich die Maus über dem Steuerelement befindet.|
|[put_MousePointer](#put_mousepointer)|Rufen Sie diese Methode auf, um den Typ des Mauszeigers festzulegen, der angezeigt wird, wenn sich die Maus über dem Steuerelement befindet, z. B. Pfeil, Kreuz oder Sanduhr.|
|[put_Picture](#put_picture)|Rufen Sie diese Methode auf, um die Bildeigenschaften einer Grafik (Symbol, Bitmap oder Metadatei) festzulegen, die angezeigt werden soll.|
|[put_ReadyState](#put_readystate)|Rufen Sie diese Methode auf, um den bereiten Zustand des Steuerelements festzulegen, z. B. Laden oder Laden.|
|[put_TabStop](#put_tabstop)|Rufen Sie diese Methode auf, um den Wert des Flags festzulegen, das angibt, ob es sich bei dem Steuerelement um einen Tabstopp handelt oder nicht.|
|[put_Text](#put_text)|Rufen Sie diese Methode auf, um den Text festzulegen, der mit dem Steuerelement angezeigt wird.|
|[putvalid](#put_valid)|Rufen Sie diese Methode auf, um das Flag festzulegen, das angibt, ob das Steuerelement gültig ist oder nicht.|
|[put_Window](#put_window)|Diese Methode ruft [CStockPropImpl::put_HWND](#put_hwnd)auf, das E_FAIL zurückgibt.|
|[putref_Font](#putref_font)|Rufen Sie diese Methode auf, um die Schriftarteigenschaften des Steuerelements mit einer Verweisanzahl festzulegen.|
|[putref_MouseIcon](#putref_mouseicon)|Rufen Sie diese Methode auf, um die Bildeigenschaften der Grafik (Symbol, Bitmap oder Metadatei) festzulegen, die angezeigt werden sollen, wenn sich die Maus über dem Steuerelement befindet, mit einer Referenzanzahl.|
|[putref_Picture](#putref_picture)|Rufen Sie diese Methode auf, um die Bildeigenschaften einer Grafik (Symbol, Bitmap oder Metadatei) festzulegen, die mit einer Referenzanzahl angezeigt werden soll.|

## <a name="remarks"></a>Bemerkungen

`CStockPropImpl`bietet **Put-and-Get-Methoden** für jede Bestandsimmobilie. **put** Diese Methoden stellen den Code bereit, der zum Festlegen oder Abrufen des Datenmembers erforderlich ist, das jeder Eigenschaft zugeordnet ist, und zum Benachrichtigen und Synchronisieren mit dem Container, wenn sich die Eigenschaft ändert.

Visual Studio bietet Unterstützung für Bestandseigenschaften über seine Assistenten. Weitere Informationen zum Hinzufügen von Bestandseigenschaften zu einem Steuerelement finden Sie im [ATL-Tutorial](../../atl/active-template-library-atl-tutorial.md).

Aus Gründen der `CStockPropImpl` Abwärtskompatibilität `get_Window` `put_Window` werden auch `get_HWND` Verfügbarmachen und Methoden verfügbar gemacht, die einfach bzw. `put_HWND`aufrufen. Die Standardimplementierung `put_HWND` von Rückgaben E_FAIL da HWND eine schreibgeschützte Eigenschaft sein sollte.

Die folgenden Eigenschaften verfügen auch über eine **putref-Implementierung:**

- Schriftart

- MouseIcon

- Bild

Dieselben drei Bestandseigenschaften erfordern, dass ihr `CComPtr` entsprechender Datenmember vom Typ oder einer anderen Klasse ist, die über den Zuweisungsoperator eine korrekte Schnittstellenreferenzzählung bereitstellt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`T`

[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)

`CStockPropImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlctl.h

## <a name="cstockpropimplget_appearance"></a><a name="get_appearance"></a>CStockPropImpl::get_Appearance

Rufen Sie diese Methode auf, um den Malstil abzurufen, der vom Steuerelement verwendet wird, z. B. flach oder 3D.

```
HRESULT STDMETHODCALLTYPE get_Appearance(SHORT pnAppearance);
```

### <a name="parameters"></a>Parameter

*pnErscheinung*<br/>
Variable, die den Farbstil des Steuerelements empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_autosize"></a><a name="get_autosize"></a>CStockPropImpl::get_AutoSize

Rufen Sie diese Methode auf, um den Status des Flags abzurufen, das angibt, ob das Steuerelement keine andere Größe haben kann.

```
HRESULT STDMETHODCALLTYPE get_Autosize(VARIANT_BOOL* pbAutoSize);
```

### <a name="parameters"></a>Parameter

*pbAutoSize*<br/>
Variable, die den Flag-Status empfängt. TRUE gibt an, dass das Steuerelement keine andere Größe haben kann.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_backcolor"></a><a name="get_backcolor"></a>CStockPropImpl::get_BackColor

Rufen Sie diese Methode auf, um die Hintergrundfarbe des Steuerelements abzurufen.

```
HRESULT STDMETHODCALLTYPE get_BackColor(OLE_COLOR* pclrBackColor);
```

### <a name="parameters"></a>Parameter

*pclrBackColor*<br/>
Variable, die die Hintergrundfarbe des Steuerelements empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_backstyle"></a><a name="get_backstyle"></a>CStockPropImpl::get_BackStyle

Rufen Sie diese Methode auf, um den Hintergrundstil des Steuerelements zu erhalten, entweder transparent oder undurchsichtig.

```
HRESULT STDMETHODCALLTYPE get_BackStyle(LONG* pnBackStyle);
```

### <a name="parameters"></a>Parameter

*pnBackStyle*<br/>
Variable, die den Hintergrundstil des Steuerelements empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_bordercolor"></a><a name="get_bordercolor"></a>CStockPropImpl::get_BorderColor

Rufen Sie diese Methode auf, um die Rahmenfarbe des Steuerelements abzurufen.

```
HRESULT STDMETHODCALLTYPE get_BorderColor(OLE_COLOR* pclrBorderColor);
```

### <a name="parameters"></a>Parameter

*pclrBorderColor*<br/>
Variable, die die Rahmenfarbe des Steuerelements empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_borderstyle"></a><a name="get_borderstyle"></a>CStockPropImpl::get_BorderStyle

Rufen Sie diese Methode auf, um den Rahmenstil des Steuerelements abzurufen.

```
HRESULT STDMETHODCALLTYPE get_BorderStyle(LONG* pnBorderStyle);
```

### <a name="parameters"></a>Parameter

*pnBorderStyle*<br/>
Variable, die den Rahmenstil des Steuerelements empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_bordervisible"></a><a name="get_bordervisible"></a>CStockPropImpl::get_BorderVisible

Rufen Sie diese Methode auf, um den Status des Flags abzurufen, das angibt, ob der Rahmen des Steuerelements sichtbar ist oder nicht.

```
HRESULT STDMETHODCALLTYPE get_BorderVisible(VARIANT_BOOL* pbBorderVisible);
```

### <a name="parameters"></a>Parameter

*pbBorderVisible*<br/>
Variable, die den Flag-Status empfängt. TRUE gibt an, dass der Rahmen des Steuerelements sichtbar ist.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_borderwidth"></a><a name="get_borderwidth"></a>CStockPropImpl::get_BorderWidth

Rufen Sie diese Methode auf, um die Breite des Rahmens des Steuerelements abzurufen.

```
HRESULT STDMETHODCALLTYPE get_BorderWidth(LONG* pnBorderWidth);
```

### <a name="parameters"></a>Parameter

*pnBorderWidth*<br/>
Variable, die die Rahmenbreite des Steuerelements empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_caption"></a><a name="get_caption"></a>CStockPropImpl::get_Caption

Rufen Sie diese Methode auf, um den in der Beschriftung eines Objekts angegebenen Text abzurufen.

```
HRESULT STDMETHODCALLTYPE get_Caption(BSTR* pbstrCaption);
```

### <a name="parameters"></a>Parameter

*pbstrCaption*<br/>
Der Text, der mit dem Steuerelement angezeigt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_drawmode"></a><a name="get_drawmode"></a>CStockPropImpl::get_DrawMode

Rufen Sie diese Methode auf, um den Zeichnungsmodus des Steuerelements abzurufen, z. B. XOR-Stift oder Invert Colors.

```
HRESULT STDMETHODCALLTYPE get_DrawMode(LONG* pnDrawMode);
```

### <a name="parameters"></a>Parameter

*pnDrawMode*<br/>
Variable, die den Zeichnungsmodus des Steuerelements empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_drawstyle"></a><a name="get_drawstyle"></a>CStockPropImpl::get_DrawStyle

Rufen Sie diese Methode auf, um den Zeichnungsstil des Steuerelements abzurufen, z. B. Volumenkörper, Gestrichelt oder gepunktet.

```
HRESULT STDMETHODCALLTYPE get_DrawStyle(LONG* pnDrawStyle);
```

### <a name="parameters"></a>Parameter

*pnDrawStyle*<br/>
Variable, die den Zeichnungsstil des Steuerelements empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_drawwidth"></a><a name="get_drawwidth"></a>CStockPropImpl::get_DrawWidth

Rufen Sie diese Methode auf, um die Zeichnungsbreite (in Pixel) abzurufen, die von den Zeichnungsmethoden des Steuerelements verwendet wird.

```
HRESULT STDMETHODCALLTYPE get_DrawWidth(LONG* pnDrawWidth);
```

### <a name="parameters"></a>Parameter

*pnDrawWidth*<br/>
Variable, die den Breitenwert des Steuerelements in Pixel empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_enabled"></a><a name="get_enabled"></a>CStockPropImpl::get_Enabled

Rufen Sie diese Methode auf, um den Status des Flags abzurufen, das angibt, ob das Steuerelement aktiviert ist.

```
HRESULT STDMETHODCALLTYPE get_Enabled(VARIANT_BOOL* pbEnabled);
```

### <a name="parameters"></a>Parameter

*pbEnabled*<br/>
Variable, die den Flag-Status empfängt. TRUE gibt an, dass das Steuerelement aktiviert ist.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_fillcolor"></a><a name="get_fillcolor"></a>CStockPropImpl::get_FillColor

Rufen Sie diese Methode auf, um die Füllfarbe des Steuerelements abzurufen.

```
HRESULT STDMETHODCALLTYPE get_FillColor(OLE_COLOR* pclrFillColor);
```

### <a name="parameters"></a>Parameter

*pclrFillColor*<br/>
Variable, die die Füllfarbe des Steuerelements empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_fillstyle"></a><a name="get_fillstyle"></a>CStockPropImpl::get_FillStyle

Rufen Sie diese Methode auf, um den Füllstil des Steuerelements abzurufen, z. B. fest, transparent oder kreuzgerafft.

```
HRESULT STDMETHODCALLTYPE get_FillStyle(LONG* pnFillStyle);
```

### <a name="parameters"></a>Parameter

*pnFillStyle*<br/>
Variable, die den Füllstil des Steuerelements empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_font"></a><a name="get_font"></a>CStockPropImpl::get_Font

Rufen Sie diese Methode auf, um einen Zeiger auf die Schriftarteigenschaften des Steuerelements abzurufen.

```
HRESULT STDMETHODCALLTYPE get_Font(IFontDisp** ppFont);
```

### <a name="parameters"></a>Parameter

*ppFont*<br/>
Variable, die einen Zeiger auf die Schriftarteigenschaften des Steuerelements empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_forecolor"></a><a name="get_forecolor"></a>CStockPropImpl::get_ForeColor

Rufen Sie diese Methode auf, um die Vordergrundfarbe des Steuerelements abzurufen.

```
HRESULT STDMETHODCALLTYPE get_ForeColor(OLE_COLOR* pclrForeColor);
```

### <a name="parameters"></a>Parameter

*pclrForeColor*<br/>
Variable, die die Vordergrundfarbe der Steuerelemente empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_hwnd"></a><a name="get_hwnd"></a>CStockPropImpl::get_HWND

Rufen Sie diese Methode auf, um das Fensterhandle abzurufen, das dem Steuerelement zugeordnet ist.

```
HRESULT STDMETHODCALLTYPE get_HWND(LONG_PTR* phWnd);
```

### <a name="parameters"></a>Parameter

*phWnd*<br/>
Das Fensterhandle, das dem Steuerelement zugeordnet ist.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_mouseicon"></a><a name="get_mouseicon"></a>CStockPropImpl::get_MouseIcon

Rufen Sie diese Methode auf, um die Bildeigenschaften der Grafik (Symbol, Bitmap oder Metadatei) anzuzeigen, wenn sich die Maus über dem Steuerelement befindet.

```
HRESULT STDMETHODCALLTYPE get_MouseIcon(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>Parameter

*ppPicture*<br/>
Variable, die einen Zeiger auf die Bildeigenschaften der Grafik empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_mousepointer"></a><a name="get_mousepointer"></a>CStockPropImpl::get_MousePointer

Rufen Sie diese Methode auf, um den Typ des Mauszeigers anzuzeigen, wenn sich die Maus über dem Steuerelement befindet, z. B. Pfeil, Kreuz oder Sanduhr.

```
HRESULT STDMETHODCALLTYPE get_MousePointer(LONG* pnMousePointer);
```

### <a name="parameters"></a>Parameter

*pnMousePointer*<br/>
Variable, die den Typ des Mauszeigers empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_picture"></a><a name="get_picture"></a>CStockPropImpl::get_Picture

Rufen Sie diese Methode auf, um einen Zeiger auf die Bildeigenschaften einer Grafik (Symbol, Bitmap oder Metadatei) anzuzeigen.

```
HRESULT STDMETHODCALLTYPE get_Picture(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>Parameter

*ppPicture*<br/>
Variable, die einen Zeiger auf die Eigenschaften des Bildes empfängt. Weitere Informationen finden Sie unter [IPictureDisp.](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp)

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_readystate"></a><a name="get_readystate"></a>CStockPropImpl::get_ReadyState

Rufen Sie diese Methode auf, um den bereiten Status des Steuerelements abzurufen, z. B. laden oder laden.

```
HRESULT STDMETHODCALLTYPE get_ReadyState(LONG* pnReadyState);
```

### <a name="parameters"></a>Parameter

*pnReadyState*<br/>
Variable, die den bereiten Status des Steuerelements empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_tabstop"></a><a name="get_tabstop"></a>CStockPropImpl::get_TabStop

Rufen Sie diese Methode auf, um den Status des Flags abzurufen, das angibt, ob es sich bei dem Steuerelement um einen Tabstopp handelt oder nicht.

```
HRESULT STDMETHODCALLTYPE get_TabStop(VARIANT_BOOL* pbTabStop);
```

### <a name="parameters"></a>Parameter

*pbTabStop*<br/>
Variable, die den Flag-Status empfängt. TRUE gibt an, dass es sich bei dem Steuerelement um einen Tabstopp handelt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_text"></a><a name="get_text"></a>CStockPropImpl::get_Text

Rufen Sie diese Methode auf, um den Text abzurufen, der mit dem Steuerelement angezeigt wird.

```
HRESULT STDMETHODCALLTYPE get_Text(BSTR* pbstrText);
```

### <a name="parameters"></a>Parameter

*pbstrText*<br/>
Der Text, der mit dem Steuerelement angezeigt wird.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplgetvalid"></a><a name="get_valid"></a>CStockPropImpl::getvalid

Rufen Sie diese Methode auf, um den Status des Flags abzurufen, das angibt, ob das Steuerelement gültig ist oder nicht.

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL* pbValid);
```

### <a name="parameters"></a>Parameter

*pbGültig*<br/>
Variable, die den Flag-Status empfängt. TRUE gibt an, dass das Steuerelement gültig ist.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplget_window"></a><a name="get_window"></a>CStockPropImpl::get_Window

Rufen Sie diese Methode auf, um das Fensterhandle abzurufen, das dem Steuerelement zugeordnet ist. Identisch mit [CStockPropImpl::get_HWND](#get_hwnd).

```
HRESULT STDMETHODCALLTYPE get_Window(LONG_PTR* phWnd);
```

### <a name="parameters"></a>Parameter

*phWnd*<br/>
Das Fensterhandle, das dem Steuerelement zugeordnet ist.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_appearance"></a><a name="put_appearance"></a>CStockPropImpl::put_Erscheinung

Rufen Sie diese Methode auf, um den vom Steuerelement verwendeten Farbstil festzulegen, z. B. flach oder 3D.

```
HRESULT STDMETHODCALLTYPE put_Appearance(SHORT nAppearance);
```

### <a name="parameters"></a>Parameter

*nErscheinung*<br/>
Der neue Farbstil, der vom Steuerelement verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_autosize"></a><a name="put_autosize"></a>CStockPropImpl::put_AutoSize

Rufen Sie diese Methode auf, um den Wert des Flags festzulegen, das angibt, ob das Steuerelement keine andere Größe haben kann.

```
HRESULT STDMETHODCALLTYPE put_AutoSize(VARIANT_BOOL bAutoSize,);
```

### <a name="parameters"></a>Parameter

*bAutoSize*<br/>
TRUE, wenn das Steuerelement keine andere Größe haben kann.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_backcolor"></a><a name="put_backcolor"></a>CStockPropImpl::put_BackColor

Rufen Sie diese Methode auf, um die Hintergrundfarbe des Steuerelements festzulegen.

```
HRESULT STDMETHODCALLTYPE put_BackColor(OLE_COLOR clrBackColor);
```

### <a name="parameters"></a>Parameter

*clrBackColor*<br/>
Die neue Steuerelementhintergrundfarbe.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_backstyle"></a><a name="put_backstyle"></a>CStockPropImpl::put_BackStyle

Rufen Sie diese Methode auf, um den Hintergrundstil des Steuerelements festzulegen.

```
HRESULT STDMETHODCALLTYPE put_BackStyle(LONG nBackStyle);
```

### <a name="parameters"></a>Parameter

*nBackStyle*<br/>
Der neue Steuerelementhintergrundstil.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_bordercolor"></a><a name="put_bordercolor"></a>CStockPropImpl::put_BorderColor

Rufen Sie diese Methode auf, um die Rahmenfarbe des Steuerelements festzulegen.

```
HRESULT STDMETHODCALLTYPE put_BorderColor(OLE_COLOR clrBorderColor);
```

### <a name="parameters"></a>Parameter

*clrBorderColor*<br/>
Die neue Rahmenfarbe. Der OLE_COLOR Datentyp wird intern als 32-Bit-Ganze dargestellt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_borderstyle"></a><a name="put_borderstyle"></a>CStockPropImpl::put_BorderStyle

Rufen Sie diese Methode auf, um den Rahmenstil des Steuerelements festzulegen.

```
HRESULT STDMETHODCALLTYPE put_BorderStyle(LONG nBorderStyle);
```

### <a name="parameters"></a>Parameter

*nBorderStyle*<br/>
Der neue Rahmenstil.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_bordervisible"></a><a name="put_bordervisible"></a>CStockPropImpl::put_BorderVisible

Rufen Sie diese Methode auf, um den Wert des Flags festzulegen, das angibt, ob der Rahmen des Steuerelements sichtbar ist oder nicht.

```
HRESULT STDMETHODCALLTYPE put_BorderVisible(VARIANT_BOOL bBorderVisible);
```

### <a name="parameters"></a>Parameter

*bBorderVisible*<br/>
TRUE, wenn der Rahmen sichtbar sein soll.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_borderwidth"></a><a name="put_borderwidth"></a>CStockPropImpl::put_BorderWidth

Rufen Sie diese Methode auf, um die Breite des Rahmens des Steuerelements festzulegen.

```
HRESULT STDMETHODCALLTYPE put_BorderWidth(LONG nBorderWidth);
```

### <a name="parameters"></a>Parameter

*nBorderWidth*<br/>
Die neue Breite des Rahmens des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_caption"></a><a name="put_caption"></a>CStockPropImpl::put_Caption

Rufen Sie diese Methode auf, um den Text festzulegen, der mit dem Steuerelement angezeigt werden soll.

```
HRESULT STDMETHODCALLTYPE put_Caption(BSTR bstrCaption);
```

### <a name="parameters"></a>Parameter

*bstrCaption*<br/>
Der Text, der mit dem Steuerelement angezeigt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_drawmode"></a><a name="put_drawmode"></a>CStockPropImpl::put_DrawMode

Rufen Sie diese Methode auf, um den Zeichnungsmodus des Steuerelements festzulegen, z. B. XOR-Stift oder Invert Colors.

```
HRESULT STDMETHODCALLTYPE put_DrawMode(LONG nDrawMode);
```

### <a name="parameters"></a>Parameter

*nDrawMode*<br/>
Der neue Zeichnungsmodus für das Steuerelement.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_drawstyle"></a><a name="put_drawstyle"></a>CStockPropImpl::put_DrawStyle

Rufen Sie diese Methode auf, um den Zeichnungsstil des Steuerelements festzulegen, z. B. Volumenkörper, Gestrichelt oder gepunktet.

```
HRESULT STDMETHODCALLTYPE put_DrawStyle(LONG pnDrawStyle);
```

### <a name="parameters"></a>Parameter

*nDrawStyle*<br/>
Der neue Zeichnungsstil für das Steuerelement.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_drawwidth"></a><a name="put_drawwidth"></a>CStockPropImpl::put_DrawWidth

Rufen Sie diese Methode auf, um die Breite (in Pixel) festzulegen, die von den Zeichenmethoden des Steuerelements verwendet wird.

```
HRESULT STDMETHODCALLTYPE put_DrawWidth(LONG nDrawWidth);
```

### <a name="parameters"></a>Parameter

*nDrawWidth*<br/>
Die neue Breite, die von den Zeichnungsmethoden des Steuerelements verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_enabled"></a><a name="put_enabled"></a>CStockPropImpl::put_Enabled

Rufen Sie diese Methode auf, um den Wert des Flags festzulegen, das angibt, ob das Steuerelement aktiviert ist.

```
HRESULT STDMETHODCALLTYPE put_Enabled(VARIANT_BOOL bEnabled);
```

### <a name="parameters"></a>Parameter

*bAktiviert*<br/>
TRUE, wenn das Steuerelement aktiviert ist.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_fillcolor"></a><a name="put_fillcolor"></a>CStockPropImpl::put_FillColor

Rufen Sie diese Methode auf, um die Füllfarbe des Steuerelements festzulegen.

```
HRESULT STDMETHODCALLTYPE put_FillColor(OLE_COLOR clrFillColor);
```

### <a name="parameters"></a>Parameter

*clrFillColor*<br/>
Die neue Füllfarbe für das Steuerelement.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_fillstyle"></a><a name="put_fillstyle"></a>CStockPropImpl::put_FillStyle

Rufen Sie diese Methode auf, um den Füllstil des Steuerelements festzulegen, z. B. durch fest, transparent oder kreuzgeschlüpft.

```
HRESULT STDMETHODCALLTYPE put_FillStyle(LONG nFillStyle);
```

### <a name="parameters"></a>Parameter

*nFillStyle*<br/>
Der neue Füllstil für das Steuerelement.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_font"></a><a name="put_font"></a>CStockPropImpl::put_Font

Rufen Sie diese Methode auf, um die Schriftarteigenschaften des Steuerelements festzulegen.

```
HRESULT STDMETHODCALLTYPE put_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>Parameter

*pFont*<br/>
Ein Zeiger auf die Schriftarteigenschaften des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_forecolor"></a><a name="put_forecolor"></a>CStockPropImpl::put_ForeColor

Rufen Sie diese Methode auf, um die Vordergrundfarbe des Steuerelements festzulegen.

```
HRESULT STDMETHODCALLTYPE put_ForeColor(OLE_COLOR clrForeColor);
```

### <a name="parameters"></a>Parameter

*clrForeColor*<br/>
Die neue Vordergrundfarbe des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_hwnd"></a><a name="put_hwnd"></a>CStockPropImpl::put_HWND

Diese Methode gibt E_FAIL zurück.

```
HRESULT STDMETHODCALLTYPE put_HWND(LONG_PTR /* hWnd */);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
Reserviert.

### <a name="return-value"></a>Rückgabewert

Gibt E_FAIL zurück.

### <a name="remarks"></a>Bemerkungen

Das Fensterhandle ist ein schreibgeschützter Wert.

## <a name="cstockpropimplput_mouseicon"></a><a name="put_mouseicon"></a>CStockPropImpl::put_MouseIcon

Rufen Sie diese Methode auf, um die Bildeigenschaften der Grafik (Symbol, Bitmap oder Metadatei) festzulegen, die angezeigt werden sollen, wenn sich die Maus über dem Steuerelement befindet.

```
HRESULT STDMETHODCALLTYPE put_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parameter

*pPicture*<br/>
Ein Zeiger auf die Bildeigenschaften der Grafik.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_mousepointer"></a><a name="put_mousepointer"></a>CStockPropImpl::put_MousePointer

Rufen Sie diese Methode auf, um den Typ des Mauszeigers festzulegen, der angezeigt wird, wenn sich die Maus über dem Steuerelement befindet, z. B. Pfeil, Kreuz oder Sanduhr.

```
HRESULT STDMETHODCALLTYPE put_MousePointer(LONG nMousePointer);
```

### <a name="parameters"></a>Parameter

*nMousePointer*<br/>
Der Typ des Mauszeigers.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_picture"></a><a name="put_picture"></a>CStockPropImpl::put_Bild

Rufen Sie diese Methode auf, um die Bildeigenschaften einer Grafik (Symbol, Bitmap oder Metadatei) festzulegen, die angezeigt werden soll.

```
HRESULT STDMETHODCALLTYPE put_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parameter

*pPicture*<br/>
Ein Zeiger auf die Eigenschaften des Bildes. Weitere Informationen finden Sie unter [IPictureDisp.](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp)

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_readystate"></a><a name="put_readystate"></a>CStockPropImpl::put_ReadyState

Rufen Sie diese Methode auf, um den bereiten Zustand des Steuerelements festzulegen, z. B. Laden oder Laden.

```
HRESULT STDMETHODCALLTYPE put_ReadyState(LONG nReadyState);
```

### <a name="parameters"></a>Parameter

*nReadyState*<br/>
Der bereite Status des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_tabstop"></a><a name="put_tabstop"></a>CStockPropImpl::put_TabStop

Rufen Sie diese Methode auf, um das Flag festzulegen, das angibt, ob es sich bei dem Steuerelement um einen Tabstopp handelt oder nicht.

```
HRESULT STDMETHODCALLTYPE put_TabStop(VARIANT_BOOL bTabStop);
```

### <a name="parameters"></a>Parameter

*bTabStop*<br/>
TRUE, wenn es sich bei dem Steuerelement um einen Tabstopp handelt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_text"></a><a name="put_text"></a>CStockPropImpl::put_Text

Rufen Sie diese Methode auf, um den Text festzulegen, der mit dem Steuerelement angezeigt wird.

```
HRESULT STDMETHODCALLTYPE put_Text(BSTR bstrText);
```

### <a name="parameters"></a>Parameter

*bstrText*<br/>
Der Text, der mit dem Steuerelement angezeigt wird.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplputvalid"></a><a name="put_valid"></a>CStockPropImpl::putvalid

Rufen Sie diese Methode auf, um das Flag festzulegen, das angibt, ob das Steuerelement gültig ist oder nicht.

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL bValid);
```

### <a name="parameters"></a>Parameter

*bGültig*<br/>
TRUE, wenn das Steuerelement gültig ist.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cstockpropimplput_window"></a><a name="put_window"></a>CStockPropImpl::put_Window

Diese Methode ruft [CStockPropImpl::put_HWND](#put_hwnd)auf, das E_FAIL zurückgibt.

```
HRESULT STDMETHODCALLTYPE put_Window(LONG_PTR hWnd);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
Das Fensterhandle.

### <a name="return-value"></a>Rückgabewert

Gibt E_FAIL zurück.

### <a name="remarks"></a>Bemerkungen

Das Fensterhandle ist ein schreibgeschützter Wert.

## <a name="cstockpropimplputref_font"></a><a name="putref_font"></a>CStockPropImpl::putref_Font

Rufen Sie diese Methode auf, um die Schriftarteigenschaften des Steuerelements mit einer Verweisanzahl festzulegen.

```
HRESULT STDMETHODCALLTYPE putref_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>Parameter

*pFont*<br/>
Ein Zeiger auf die Schriftarteigenschaften des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Das gleiche wie [CStockPropImpl::put_Font](#put_font), aber mit einer Verweisanzahl.

## <a name="cstockpropimplputref_mouseicon"></a><a name="putref_mouseicon"></a>CStockPropImpl::putref_MouseIcon

Rufen Sie diese Methode auf, um die Bildeigenschaften der Grafik (Symbol, Bitmap oder Metadatei) festzulegen, die angezeigt werden sollen, wenn sich die Maus über dem Steuerelement befindet, mit einer Referenzanzahl.

```
HRESULT STDMETHODCALLTYPE putref_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parameter

*pPicture*<br/>
Ein Zeiger auf die Bildeigenschaften der Grafik.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Das gleiche wie [CStockPropImpl::put_MouseIcon](#put_mouseicon), aber mit einer Verweisanzahl.

## <a name="cstockpropimplputref_picture"></a><a name="putref_picture"></a>CStockPropImpl::putref_Bild

Rufen Sie diese Methode auf, um die Bildeigenschaften einer Grafik (Symbol, Bitmap oder Metadatei) festzulegen, die mit einer Referenzanzahl angezeigt werden soll.

```
HRESULT STDMETHODCALLTYPE putref_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parameter

*pPicture*<br/>
Ein Zeiger auf die Eigenschaften des Bildes. Weitere Informationen finden Sie unter [IPictureDisp.](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp)

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Das gleiche wie [CStockPropImpl::put_Picture](#put_picture), aber mit einer Verweisanzahl.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[IDispatchImpl-Klasse](../../atl/reference/idispatchimpl-class.md)
