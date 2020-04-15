---
title: CFontHolder-Klasse
ms.date: 11/04/2016
f1_keywords:
- CFontHolder
- AFXCTL/CFontHolder
- AFXCTL/CFontHolder::CFontHolder
- AFXCTL/CFontHolder::GetDisplayString
- AFXCTL/CFontHolder::GetFontDispatch
- AFXCTL/CFontHolder::GetFontHandle
- AFXCTL/CFontHolder::InitializeFont
- AFXCTL/CFontHolder::QueryTextMetrics
- AFXCTL/CFontHolder::ReleaseFont
- AFXCTL/CFontHolder::Select
- AFXCTL/CFontHolder::SetFont
- AFXCTL/CFontHolder::m_pFont
helpviewer_keywords:
- CFontHolder [MFC], CFontHolder
- CFontHolder [MFC], GetDisplayString
- CFontHolder [MFC], GetFontDispatch
- CFontHolder [MFC], GetFontHandle
- CFontHolder [MFC], InitializeFont
- CFontHolder [MFC], QueryTextMetrics
- CFontHolder [MFC], ReleaseFont
- CFontHolder [MFC], Select
- CFontHolder [MFC], SetFont
- CFontHolder [MFC], m_pFont
ms.assetid: 728ab472-0c97-440d-889f-1324c6e1b6b8
ms.openlocfilehash: 6a053f127123a9ca21853189b9458738b217ee2b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373818"
---
# <a name="cfontholder-class"></a>CFontHolder-Klasse

Implementiert die vordefinierte Schriftarteigenschaft und kapselt die Funktionalität eines Windows-Schriftartobjekts und der `IFont` -Schnittstelle.

## <a name="syntax"></a>Syntax

```
class CFontHolder
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFontHolder::CFontHolder](#cfontholder)|Erstellt ein `CFontHolder`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFontHolder::GetDisplayString](#getdisplaystring)|Ruft die Zeichenfolge ab, die im Eigenschaftenbrowser eines Containers angezeigt wird.|
|[CFontHolder::GetFontDispatch](#getfontdispatch)|Gibt die `IDispatch` Benutzeroberfläche der Schriftart zurück.|
|[CFontHolder::GetFontHandle](#getfonthandle)|Gibt ein Handle an eine Windows-Schriftart zurück.|
|[CFontHolder::InitializeFont](#initializefont)|Initialisiert ein `CFontHolder`-Objekt.|
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|Ruft Informationen für die zugehörige Schriftart ab.|
|[CFontHolder::ReleaseFont](#releasefont)|Trennt das `CFontHolder` Objekt `IFont` von `IFontNotification` der und Schnittstellen.|
|[CFontHolder::Auswählen](#select)|Wählt eine Schriftartressource in einem Gerätekontext aus.|
|[CFontHolder::SetFont](#setfont)|Verbindet `CFontHolder` das Objekt `IFont` mit einer Schnittstelle.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFontHolder::m_pFont](#m_pfont)|Ein Zeiger auf `CFontHolder` die `IFont` Schnittstelle des Objekts.|

## <a name="remarks"></a>Bemerkungen

`CFontHolder`hat keine Basisklasse.

Verwenden Sie diese Klasse, um benutzerdefinierte Schriftarteigenschaften für das Steuerelement zu implementieren. Informationen zum Erstellen solcher Eigenschaften finden Sie im Artikel [ActiveX-Steuerelemente: Verwenden von Schriftarten](../../mfc/mfc-activex-controls-using-fonts.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CFontHolder`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxctl.h

## <a name="cfontholdercfontholder"></a><a name="cfontholder"></a>CFontHolder::CFontHolder

Erstellt ein `CFontHolder`-Objekt.

```
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```

### <a name="parameters"></a>Parameter

*pNotify*<br/>
Zeiger auf die `IPropertyNotifySink` Schriftartoberfläche.

### <a name="remarks"></a>Bemerkungen

Sie müssen `InitializeFont` aufrufen, um das resultierende Objekt zu initialisieren, bevor Sie es verwenden.

## <a name="cfontholdergetdisplaystring"></a><a name="getdisplaystring"></a>CFontHolder::GetDisplayString

Ruft eine Zeichenfolge ab, die im Eigenschaftenbrowser eines Containers angezeigt werden kann.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>Parameter

*strValue*<br/>
Verweis auf den [CString,](../../atl-mfc-shared/reference/cstringt-class.md) der die Anzeigezeichenfolge enthalten soll.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Zeichenfolge erfolgreich abgerufen wurde; andernfalls 0.

## <a name="cfontholdergetfontdispatch"></a><a name="getfontdispatch"></a>CFontHolder::GetFontDispatch

Rufen Sie diese Funktion auf, um einen Zeiger auf die Dispatch-Schnittstelle der Schriftart abzurufen.

```
LPFONTDISP GetFontDispatch();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CFontHolder` die `IFontDisp` Schnittstelle des Objekts. Beachten Sie, dass `GetFontDispatch` die `IUnknown::Release` Funktion, die Aufrufe aufrufen, diesen Schnittstellenzeiger aufrufen muss, wenn sie damit abgeschlossen ist.

### <a name="remarks"></a>Bemerkungen

Rufen `InitializeFont` Sie `GetFontDispatch`an, bevor Sie anrufen .

## <a name="cfontholdergetfonthandle"></a><a name="getfonthandle"></a>CFontHolder::GetFontHandle

Rufen Sie diese Funktion auf, um ein Handle für eine Windows-Schriftart abzurufen.

```
HFONT GetFontHandle();

HFONT GetFontHandle(
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>Parameter

*cyLogical*<br/>
Höhe des Rechtecks, in dem das Steuerelement gezeichnet wird, in logischen Einheiten.

*cyHimetric*<br/>
Höhe, in MM_HIMETRIC Einheiten, des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Ein Handle für das Font-Objekt; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Das Verhältnis von *cyLogical* und *cyHimetric* wird verwendet, um die richtige Anzeigegröße in logischen Einheiten für die Punktgröße der Schriftart zu berechnen, ausgedrückt in MM_HIMETRIC Einheiten:

Displaygröße = ( *cyLogical* / *cyHimetric*) X Schriftgröße

Die Version ohne Parameter gibt ein Handle an eine Schriftart zurück, die für den Bildschirm korrekt ist.

## <a name="cfontholderinitializefont"></a><a name="initializefont"></a>CFontHolder::InitializeFont

Initialisiert ein `CFontHolder`-Objekt.

```
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,
    LPDISPATCH pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Parameter

*pFontDesc*<br/>
Zeiger auf eine Schriftartbeschreibungsstruktur ( [FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc)), die die Eigenschaften der Schriftart angibt.

*pFontDispAmbient*<br/>
Zeigen Sie mit dem Zeiger auf die Ambient Font-Eigenschaft des Containers.

### <a name="remarks"></a>Bemerkungen

Wenn *pFontDispAmbient* nicht NULL `CFontHolder` ist, wird das `IFont` Objekt mit einem Klon der Schnittstelle verbunden, die von der Ambient Font-Eigenschaft des Containers verwendet wird.

Wenn *pFontDispAmbient* NULL ist, wird ein neues Font-Objekt entweder aus der Schriftartbeschreibung erstellt, auf die *pFontDesc* zeigt, oder, wenn *pFontDesc* NULL ist, aus einer Standardbeschreibung.

Rufen Sie diese `CFontHolder` Funktion auf, nachdem Sie ein Objekt erstellt haben.

## <a name="cfontholderm_pfont"></a><a name="m_pfont"></a>CFontHolder::m_pFont

Ein Zeiger auf `CFontHolder` die `IFont` Schnittstelle des Objekts.

```
LPFONT m_pFont;
```

## <a name="cfontholderquerytextmetrics"></a><a name="querytextmetrics"></a>CFontHolder::QueryTextMetrics

Ruft Informationen zur physischen Schriftart `CFontHolder` ab, die vom Objekt dargestellt wird.

```
void QueryTextMetrics(LPTEXTMETRIC lptm);
```

### <a name="parameters"></a>Parameter

*lptm*<br/>
Ein Zeiger auf eine [TEXTMETRIC-Struktur,](/windows/win32/api/wingdi/ns-wingdi-textmetricw) die die Informationen empfängt.

## <a name="cfontholderreleasefont"></a><a name="releasefont"></a>CFontHolder::ReleaseFont

Diese Funktion trennt `CFontHolder` das `IFont` Objekt von seiner Schnittstelle.

```
void ReleaseFont();
```

## <a name="cfontholderselect"></a><a name="select"></a>CFontHolder::Auswählen

Rufen Sie diese Funktion auf, um die Schriftart Des Steuerelements im angegebenen Gerätekontext auszuwählen.

```
CFont* Select(
    CDC* pDC,
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Gerätekontext, in dem die Schriftart ausgewählt ist.

*cyLogical*<br/>
Höhe des Rechtecks, in dem das Steuerelement gezeichnet wird, in logischen Einheiten.

*cyHimetric*<br/>
Höhe, in MM_HIMETRIC Einheiten, des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die Schriftart, die ersetzt wird.

### <a name="remarks"></a>Bemerkungen

Eine Erläuterung der *cyLogical-* und *cyHimetric-Parameter* finden Sie unter [GetFontHandle.](#getfonthandle)

## <a name="cfontholdersetfont"></a><a name="setfont"></a>CFontHolder::SetFont

Gibt jede vorhandene Schriftart frei und verbindet das `CFontHolder` Objekt mit einer `IFont` Schnittstelle.

```
void SetFont(LPFONT pNewFont);
```

### <a name="parameters"></a>Parameter

*pNewFont*<br/>
Zeiger auf die `IFont` neue Schnittstelle.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CPropExchange-Klasse](../../mfc/reference/cpropexchange-class.md)
