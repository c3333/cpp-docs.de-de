---
title: CD2DTextLayout-Klasse
ms.date: 03/27/2019
f1_keywords:
- CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::Create
- AFXRENDERTARGET/CD2DTextLayout::Destroy
- AFXRENDERTARGET/CD2DTextLayout::Get
- AFXRENDERTARGET/CD2DTextLayout::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::GetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::IsValid
- AFXRENDERTARGET/CD2DTextLayout::ReCreate
- AFXRENDERTARGET/CD2DTextLayout::SetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::SetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::m_pTextLayout
helpviewer_keywords:
- CD2DTextLayout [MFC], CD2DTextLayout
- CD2DTextLayout [MFC], Create
- CD2DTextLayout [MFC], Destroy
- CD2DTextLayout [MFC], Get
- CD2DTextLayout [MFC], GetFontFamilyName
- CD2DTextLayout [MFC], GetLocaleName
- CD2DTextLayout [MFC], IsValid
- CD2DTextLayout [MFC], ReCreate
- CD2DTextLayout [MFC], SetFontFamilyName
- CD2DTextLayout [MFC], SetLocaleName
- CD2DTextLayout [MFC], m_pTextLayout
ms.assetid: 724bd13c-f2ef-4e55-a775-8cb04b7b7908
ms.openlocfilehash: 9be4c1134e2f82ceb3af31cbeb1a7d55f4071777
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369027"
---
# <a name="cd2dtextlayout-class"></a>CD2DTextLayout-Klasse

Ein Wrapper für IDWriteTextLayout.

## <a name="syntax"></a>Syntax

```
class CD2DTextLayout : public CD2DResource;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DTextLayout::CD2DTextLayout](#cd2dtextlayout)|Erstellt ein CD2DTextLayout-Objekt.|
|[CD2DTextLayout::-CD2DTextLayout](#_dtorcd2dtextlayout)|Der Destruktor. Wird aufgerufen, wenn ein D2D-Textlayoutobjekt zerstört wird.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DTextLayout::Erstellen](#create)|Erstellt ein CD2DTextLayout. (Überschreibt [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DTextLayout::Destroy](#destroy)|Zerstört ein CD2DTextLayout-Objekt. (Überschreibt [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DTextLayout::Get](#get)|Gibt IDWriteTextLayout-Schnittstelle zurück|
|[CD2DTextLayout::GetFontFamilyName](#getfontfamilyname)|Kopiert den Schriftfamiliennamen des Textes an der angegebenen Position.|
|[CD2DTextLayout::GetLocaleName](#getlocalename)|Ruft den Gebietsschemanamen des Textes an der angegebenen Position ab.|
|[CD2DTextLayout::IsValid](#isvalid)|Überprüft die Ressourcengültigkeit (Überschreibt [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DTextLayout::ReCreate](#recreate)|Erstellt ein CD2DTextLayout neu. (Überschreibt [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|
|[CD2DTextLayout::SetFontFamilyName](#setfontfamilyname)|Legt den Familiennamen für null-terminierte Schriftarten für Text innerhalb eines angegebenen Textbereichs fest.|
|[CD2DTextLayout::SetLocaleName](#setlocalename)|Legt den Gebietsschemanamen für Text innerhalb eines angegebenen Textbereichs fest|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DTextLayout::operator IDWriteTextLayout*](#operator_idwritetextlayout_star)|Gibt IDWriteTextLayout-Schnittstelle zurück|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DTextLayout::m_pTextLayout](#m_ptextlayout)|Ein Zeiger auf ein IDWriteTextLayout.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DTextLayout](../../mfc/reference/cd2dtextlayout-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxrendertarget.h

## <a name="cd2dtextlayoutcd2dtextlayout"></a><a name="_dtorcd2dtextlayout"></a>CD2DTextLayout::-CD2DTextLayout

Der Destruktor. Wird aufgerufen, wenn ein D2D-Textlayoutobjekt zerstört wird.

```
virtual ~CD2DTextLayout();
```

## <a name="cd2dtextlayoutcd2dtextlayout"></a><a name="cd2dtextlayout"></a>CD2DTextLayout::CD2DTextLayout

Erstellt ein CD2DTextLayout-Objekt.

```
CD2DTextLayout(
    CRenderTarget* pParentTarget,
    const CString& strText,
    CD2DTextFormat& textFormat,
    const CD2DSizeF& sizeMax,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parameter

*pParentTarget*<br/>
Ein Zeiger auf das Renderziel.

*strText*<br/>
Ein CString-Objekt, das die Zeichenfolge zum Erstellen eines neuen CD2DTextLayout-Objekts enthält.

*textFormat*<br/>
Ein CString-Objekt, das das Format enthält, das auf die Zeichenfolge angewendet werden soll.

*sizeMax*<br/>
Die Größe des Layoutfelds.

*bAutoDestroy*<br/>
Gibt an, dass das Objekt vom Besitzer (pParentTarget) zerstört wird.

## <a name="cd2dtextlayoutcreate"></a><a name="create"></a>CD2DTextLayout::Erstellen

Erstellt ein CD2DTextLayout.

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT-Fehlercode zurückgegeben.

## <a name="cd2dtextlayoutdestroy"></a><a name="destroy"></a>CD2DTextLayout::Destroy

Zerstört ein CD2DTextLayout-Objekt.

```
virtual void Destroy();
```

## <a name="cd2dtextlayoutget"></a><a name="get"></a>CD2DTextLayout::Get

Gibt IDWriteTextLayout-Schnittstelle zurück

```
IDWriteTextLayout* Get();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine IDWriteTextLayout-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dtextlayoutgetfontfamilyname"></a><a name="getfontfamilyname"></a>CD2DTextLayout::GetFontFamilyName

Kopiert den Schriftfamiliennamen des Textes an der angegebenen Position.

```
CString GetFontFamilyName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>Parameter

*currentPosition*<br/>
Die Position des zu untersuchenden Textes.

*Textrange*<br/>
Der Textbereich, der die gleiche Formatierung wie der Text an der von currentPosition angegebenen Position aufweist. Dies bedeutet, dass die Ausführung die exakte Formatierung als angegebene Position aufweist, einschließlich, aber nicht beschränkt auf den Familiennamen der Schriftart.

### <a name="return-value"></a>Rückgabewert

CString-Objekt, das den aktuellen Schriftfamiliennamen enthält.

## <a name="cd2dtextlayoutgetlocalename"></a><a name="getlocalename"></a>CD2DTextLayout::GetLocaleName

Ruft den Gebietsschemanamen des Textes an der angegebenen Position ab.

```
CString GetLocaleName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>Parameter

*currentPosition*<br/>
Die Position des zu überprüfenden Textes.

*Textrange*<br/>
Der Textbereich, der die gleiche Formatierung wie der Text an der von currentPosition angegebenen Position aufweist. Dies bedeutet, dass die Ausführung die exakte Formatierung als angegebene Position aufweist, einschließlich, aber nicht beschränkt auf den Gebietsschemanamen.

### <a name="return-value"></a>Rückgabewert

CString-Objekt, das den aktuellen Gebietsschemanamen enthält.

## <a name="cd2dtextlayoutisvalid"></a><a name="isvalid"></a>CD2DTextLayout::IsValid

Überprüft die Gültigkeit der Ressource

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Ressource gültig ist; andernfalls FALSE.

## <a name="cd2dtextlayoutm_ptextlayout"></a><a name="m_ptextlayout"></a>CD2DTextLayout::m_pTextLayout

Ein Zeiger auf ein IDWriteTextLayout.

```
IDWriteTextLayout* m_pTextLayout;
```

## <a name="cd2dtextlayoutoperator-idwritetextlayout"></a><a name="operator_idwritetextlayout_star"></a>CD2DTextLayout::operator IDWriteTextLayout*

Gibt IDWriteTextLayout-Schnittstelle zurück

```
operator IDWriteTextLayout*();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine IDWriteTextLayout-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dtextlayoutrecreate"></a><a name="recreate"></a>CD2DTextLayout::ReCreate

Erstellt ein CD2DTextLayout neu.

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT-Fehlercode zurückgegeben.

## <a name="cd2dtextlayoutsetfontfamilyname"></a><a name="setfontfamilyname"></a>CD2DTextLayout::SetFontFamilyName

Legt den Familiennamen für null-terminierte Schriftarten für Text innerhalb eines angegebenen Textbereichs fest.

```
BOOL SetFontFamilyName(
    LPCWSTR pwzFontFamilyName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>Parameter

*pwzFontFamilyName*<br/>
Der Schriftfamilienname, der für die gesamte Textzeichenfolge innerhalb des von textRange angegebenen Bereichs gilt.

*Textrange*<br/>
Textbereich, auf den diese Änderung angewendet wird

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="cd2dtextlayoutsetlocalename"></a><a name="setlocalename"></a>CD2DTextLayout::SetLocaleName

Legt den Gebietsschemanamen für Text innerhalb eines angegebenen Textbereichs fest

```
BOOL SetLocaleName(
    LPCWSTR pwzLocaleName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>Parameter

*pwzLocaleName*<br/>
Eine null-terminierte Gebietsschemanamenszeichenfolge

*Textrange*<br/>
Textbereich, auf den diese Änderung angewendet wird

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)
