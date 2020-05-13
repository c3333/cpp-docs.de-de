---
title: CPictureHolder-Klasse
ms.date: 11/04/2016
f1_keywords:
- CPictureHolder
- AFXCTL/CPictureHolder
- AFXCTL/CPictureHolder::CPictureHolder
- AFXCTL/CPictureHolder::CreateEmpty
- AFXCTL/CPictureHolder::CreateFromBitmap
- AFXCTL/CPictureHolder::CreateFromIcon
- AFXCTL/CPictureHolder::CreateFromMetafile
- AFXCTL/CPictureHolder::GetDisplayString
- AFXCTL/CPictureHolder::GetPictureDispatch
- AFXCTL/CPictureHolder::GetType
- AFXCTL/CPictureHolder::Render
- AFXCTL/CPictureHolder::SetPictureDispatch
- AFXCTL/CPictureHolder::m_pPict
helpviewer_keywords:
- CPictureHolder [MFC], CPictureHolder
- CPictureHolder [MFC], CreateEmpty
- CPictureHolder [MFC], CreateFromBitmap
- CPictureHolder [MFC], CreateFromIcon
- CPictureHolder [MFC], CreateFromMetafile
- CPictureHolder [MFC], GetDisplayString
- CPictureHolder [MFC], GetPictureDispatch
- CPictureHolder [MFC], GetType
- CPictureHolder [MFC], Render
- CPictureHolder [MFC], SetPictureDispatch
- CPictureHolder [MFC], m_pPict
ms.assetid: a4f59775-704a-41dd-b5bd-2e531c95127a
ms.openlocfilehash: edb93b05c1187d2c78f4c1120ee76282167c9b49
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753597"
---
# <a name="cpictureholder-class"></a>CPictureHolder-Klasse

Implementiert eine Picture-Eigenschaft, mit der der Benutzer ein Bild in Ihrem Steuerelement anzeigen kann.

## <a name="syntax"></a>Syntax

```
class CPictureHolder
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPictureHolder::CPictureHolder](#cpictureholder)|Erstellt ein `CPictureHolder`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPictureHolder::CreateEmpty](#createempty)|Erstellt ein leeres `CPictureHolder`-Objekt.|
|[CPictureHolder::CreateFromBitmap](#createfrombitmap)|Erstellt `CPictureHolder` ein Objekt aus einer Bitmap.|
|[CPictureHolder::CreateFromIcon](#createfromicon)|Erstellt `CPictureHolder` ein Objekt aus einem Symbol.|
|[CPictureHolder::CreateFromMetafile](#createfrommetafile)|Erstellt `CPictureHolder` ein Objekt aus einer Metadatei.|
|[CPictureHolder::GetDisplayString](#getdisplaystring)|Ruft die Zeichenfolge ab, die im Eigenschaftenbrowser eines Steuerelementcontainers angezeigt wird.|
|[CPictureHolder::GetPictureDispatch](#getpicturedispatch)|Gibt `CPictureHolder` die Schnittstelle `IDispatch` des Objekts zurück.|
|[CPictureHolder::GetType](#gettype)|Gibt an, ob es sich bei dem `CPictureHolder` Objekt um eine Bitmap, eine Metadatei oder ein Symbol handelt.|
|[CPictureHolder::Render](#render)|Rendert das Bild.|
|[CPictureHolder::SetPictureDispatch](#setpicturedispatch)|Legt `CPictureHolder` die Schnittstelle `IDispatch` des Objekts fest.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPictureHolder::m_pPict](#m_ppict)|Ein Zeiger auf ein Bildobjekt.|

## <a name="remarks"></a>Bemerkungen

`CPictureHolder`hat keine Basisklasse.

Mit der Stock Picture-Eigenschaft kann der Entwickler eine Bitmap, ein Symbol oder eine Metadatei für die Anzeige angeben.

Informationen zum Erstellen benutzerdefinierter Bildeigenschaften finden Sie im Artikel [MFC ActiveX Controls: Using Pictures in a ActiveX Control](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CPictureHolder`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxctl.h

## <a name="cpictureholdercpictureholder"></a><a name="cpictureholder"></a>CPictureHolder::CPictureHolder

Erstellt ein `CPictureHolder`-Objekt.

```
CPictureHolder();
```

## <a name="cpictureholdercreateempty"></a><a name="createempty"></a>CPictureHolder::CreateEmpty

Erstellt ein `CPictureHolder` leeres Objekt `IPicture` und verbindet es mit einer Schnittstelle.

```
BOOL CreateEmpty();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Objekt erfolgreich erstellt wurde; andernfalls 0.

## <a name="cpictureholdercreatefrombitmap"></a><a name="createfrombitmap"></a>CPictureHolder::CreateFromBitmap

Verwendet eine Bitmap, um das `CPictureHolder`Bildobjekt in einer zu initialisieren.

```
BOOL CreateFromBitmap(
    UINT idResource);

BOOL CreateFromBitmap(
    CBitmap* pBitmap,
    CPalette* pPal = NULL,
    BOOL bTransferOwnership = TRUE);

BOOL CreateFromBitmap(
    HBITMAP hbm,
    HPALETTE hpal = NULL,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Parameter

*idResource*<br/>
Ressourcen-ID einer Bitmapressource.

*pBitmap*<br/>
Zeiger auf ein [CBitmap-Objekt.](../../mfc/reference/cbitmap-class.md)

*pPal*<br/>
Zeiger auf ein [CPalette-Objekt.](../../mfc/reference/cpalette-class.md)

*bTransferOwnership*<br/>
Gibt an, ob das Bildobjekt den Besitz der Bitmap- und Palettenobjekte übernimmt.

*Hbm*<br/>
Handle für die Bitmap, aus der das `CPictureHolder` Objekt erstellt wird.

*hpal*<br/>
Handle für die Palette, die zum Rendern der Bitmap verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Objekt erfolgreich erstellt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn *bTransferOwnership* TRUE ist, sollte der Aufrufer das Bitmap- oder Palettenobjekt nach der Rückgabe dieses Aufrufs in keiner Weise verwenden. Wenn *bTransferOwnership* FALSE ist, ist der Aufrufer dafür verantwortlich, sicherzustellen, dass die Bitmap- und Palettenobjekte für die Lebensdauer des Bildobjekts gültig bleiben.

## <a name="cpictureholdercreatefromicon"></a><a name="createfromicon"></a>CPictureHolder::CreateFromIcon

Verwendet ein Symbol, um das `CPictureHolder`Bildobjekt in einem zu initialisieren.

```
BOOL CreateFromIcon(
    UINT idResource);

BOOL CreateFromIcon(
    HICON hIcon,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Parameter

*idResource*<br/>
Ressourcen-ID einer Bitmapressource.

*hIcon*<br/>
Behandeln Sie das Symbol, aus dem das `CPictureHolder` Objekt erstellt wird.

*bTransferOwnership*<br/>
Gibt an, ob das Bildobjekt den Besitz des Symbolobjekts übernimmt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Objekt erfolgreich erstellt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn *bTransferOwnership* TRUE ist, sollte der Aufrufer das Symbolobjekt nach der Rückgabe dieses Aufrufs in keiner Weise verwenden. Wenn *bTransferOwnership* FALSE ist, ist der Aufrufer dafür verantwortlich, sicherzustellen, dass das Symbolobjekt für die Lebensdauer des bild-Objekts gültig bleibt.

## <a name="cpictureholdercreatefrommetafile"></a><a name="createfrommetafile"></a>CPictureHolder::CreateFromMetafile

Verwendet eine Metadatei, um das `CPictureHolder`Bildobjekt in einer zu initialisieren.

```
BOOL CreateFromMetafile(
    HMETAFILE hmf,
    int xExt,
    int yExt,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Parameter

*hmf*<br/>
Handle für die Metadatei, `CPictureHolder` die zum Erstellen des Objekts verwendet wird.

*xExt*<br/>
X Ausdehnung des Bildes.

*yExt*<br/>
Y Ausdehnung des Bildes.

*bTransferOwnership*<br/>
Gibt an, ob das picture-Objekt den Besitz des Metadateiobjekts übernimmt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Objekt erfolgreich erstellt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn *bTransferOwnership* TRUE ist, sollte der Aufrufer das Metadateiobjekt nach der Rückgabe dieses Aufrufs in keiner Weise verwenden. Wenn *bTransferOwnership* FALSE ist, ist der Aufrufer dafür verantwortlich, sicherzustellen, dass das Metadateiobjekt für die Lebensdauer des Bildobjekts gültig bleibt.

## <a name="cpictureholdergetdisplaystring"></a><a name="getdisplaystring"></a>CPictureHolder::GetDisplayString

Ruft die Zeichenfolge ab, die im Eigenschaftenbrowser eines Containers angezeigt wird.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>Parameter

*strValue*<br/>
Verweis auf den [CString,](../../atl-mfc-shared/reference/cstringt-class.md) der die Anzeigezeichenfolge enthalten soll.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Zeichenfolge erfolgreich abgerufen wurde; andernfalls 0.

## <a name="cpictureholdergetpicturedispatch"></a><a name="getpicturedispatch"></a>CPictureHolder::GetPictureDispatch

Diese Funktion gibt einen `CPictureHolder` Zeiger auf `IPictureDisp` die Schnittstelle des Objekts zurück.

```
LPPICTUREDISP GetPictureDispatch();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CPictureHolder` die `IPictureDisp` Schnittstelle des Objekts.

### <a name="remarks"></a>Bemerkungen

Der Anrufer `Release` muss diesen Zeiger aufrufen, wenn er damit fertig ist.

## <a name="cpictureholdergettype"></a><a name="gettype"></a>CPictureHolder::GetType

Gibt an, ob es sich bei dem Bild um eine Bitmap, eine Metadatei oder ein Symbol handelt.

```
short GetType();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der den Typ des Bildes angibt. Mögliche Werte und ihre Bedeutung sind wie folgt:

|Wert|Bedeutung|
|-----------|-------------|
|PICTYPE_UNINITIALIZED|`CPictureHolder`Objekt unititialisiert ist.|
|PICTYPE_NONE|`CPictureHolder`Objekt ist leer.|
|PICTYPE_BITMAP|Bild ist eine Bitmap.|
|PICTYPE_METAFILE|Bild ist eine Metadatei.|
|PICTYPE_ICON|Bild ist ein Symbol.|

## <a name="cpictureholderm_ppict"></a><a name="m_ppict"></a>CPictureHolder::m_pPict

Ein Zeiger auf `CPictureHolder` die `IPicture` Schnittstelle des Objekts.

```
LPPICTURE m_pPict;
```

## <a name="cpictureholderrender"></a><a name="render"></a>CPictureHolder::Render

Rendert das Bild im Rechteck, auf das *rcRender*verweist.

```cpp
void Render(
    CDC* pDC,
    const CRect& rcRender,
    const CRect& rcWBounds);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Zeiger auf den Anzeigekontext, in dem das Bild gerendert werden soll.

*rcRender*<br/>
Rechteck, in dem das Bild gerendert werden soll.

*rcWBounds*<br/>
Ein Rechteck, das das umgrenzende Rechteck des Objekts darstellt, das das Bild rendert. Für ein Steuerelement ist dieses Rechteck der *rcBounds-Parameter,* der an eine Außerkraftsetzung von [COleControl::OnDraw](../../mfc/reference/colecontrol-class.md#ondraw)übergeben wird.

## <a name="cpictureholdersetpicturedispatch"></a><a name="setpicturedispatch"></a>CPictureHolder::SetPictureDispatch

Verbindet `CPictureHolder` das Objekt `IPictureDisp` mit einer Schnittstelle.

```cpp
void SetPictureDispatch(LPPICTUREDISP pDisp);
```

### <a name="parameters"></a>Parameter

*pDisp*<br/>
Zeiger auf die `IPictureDisp` neue Schnittstelle.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CFontHolder-Klasse](../../mfc/reference/cfontholder-class.md)
