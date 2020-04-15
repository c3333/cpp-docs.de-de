---
title: CD2DTextFormat-Klasse
ms.date: 03/27/2019
f1_keywords:
- CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::Create
- AFXRENDERTARGET/CD2DTextFormat::Destroy
- AFXRENDERTARGET/CD2DTextFormat::Get
- AFXRENDERTARGET/CD2DTextFormat::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextFormat::GetLocaleName
- AFXRENDERTARGET/CD2DTextFormat::IsValid
- AFXRENDERTARGET/CD2DTextFormat::ReCreate
- AFXRENDERTARGET/CD2DTextFormat::m_pTextFormat
helpviewer_keywords:
- CD2DTextFormat [MFC], CD2DTextFormat
- CD2DTextFormat [MFC], Create
- CD2DTextFormat [MFC], Destroy
- CD2DTextFormat [MFC], Get
- CD2DTextFormat [MFC], GetFontFamilyName
- CD2DTextFormat [MFC], GetLocaleName
- CD2DTextFormat [MFC], IsValid
- CD2DTextFormat [MFC], ReCreate
- CD2DTextFormat [MFC], m_pTextFormat
ms.assetid: db194cec-9dae-4644-ab84-7c43b7164117
ms.openlocfilehash: f7310fd3ca2ac34df7cc1a99cd5527ea8ba709c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369046"
---
# <a name="cd2dtextformat-class"></a>CD2DTextFormat-Klasse

Ein Wrapper für IDWriteTextFormat.

## <a name="syntax"></a>Syntax

```
class CD2DTextFormat : public CD2DResource;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DTextFormat::CD2DTextFormat](#cd2dtextformat)|Erstellt ein CD2DTextFormat-Objekt.|
|[CD2DTextFormat::-CD2DTextFormat](#_dtorcd2dtextformat)|Der Destruktor. Wird aufgerufen, wenn ein D2D-Textformatobjekt zerstört wird.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DTextFormat::Erstellen](#create)|Erstellt ein CD2DTextFormat. (Überschreibt [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DTextFormat::Destroy](#destroy)|Zerstört ein CD2DTextFormat-Objekt. (Überschreibt [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DTextFormat::Get](#get)|Gibt IDWriteTextFormat-Schnittstelle zurück|
|[CD2DTextFormat::GetFontFamilyName](#getfontfamilyname)|Ruft eine Kopie des Schriftfamiliennamens ab.|
|[CD2DTextFormat::GetLocaleName](#getlocalename)|Ruft eine Kopie des Gebietsschemanamens ab.|
|[CD2DTextFormat::IsValid](#isvalid)|Überprüft die Ressourcengültigkeit (Überschreibt [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DTextFormat::ReCreate](#recreate)|Erstellt ein CD2DTextFormat neu. (Überschreibt [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DTextFormat::operator IDWriteTextFormat*](#operator_idwritetextformat_star)|Gibt IDWriteTextFormat-Schnittstelle zurück|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DTextFormat::m_pTextFormat](#m_ptextformat)|Ein Zeiger auf ein IDWriteTextFormat.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DTextFormat](../../mfc/reference/cd2dtextformat-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxrendertarget.h

## <a name="cd2dtextformatcd2dtextformat"></a><a name="_dtorcd2dtextformat"></a>CD2DTextFormat::-CD2DTextFormat

Der Destruktor. Wird aufgerufen, wenn ein D2D-Textformatobjekt zerstört wird.

```
virtual ~CD2DTextFormat();
```

## <a name="cd2dtextformatcd2dtextformat"></a><a name="cd2dtextformat"></a>CD2DTextFormat::CD2DTextFormat

Erstellt ein CD2DTextFormat-Objekt.

```
CD2DTextFormat(
    CRenderTarget* pParentTarget,
    const CString& strFontFamilyName,
    FLOAT fontSize,
    DWRITE_FONT_WEIGHT fontWeight = DWRITE_FONT_WEIGHT_NORMAL,
    DWRITE_FONT_STYLE fontStyle = DWRITE_FONT_STYLE_NORMAL,
    DWRITE_FONT_STRETCH fontStretch = DWRITE_FONT_STRETCH_NORMAL,
    const CString& strFontLocale = _T(""),
    IDWriteFontCollection* pFontCollection = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parameter

*pParentTarget*<br/>
Ein Zeiger auf das Renderziel.

*strFontFamilyName*<br/>
Ein CString-Objekt, das den Namen der Schriftfamilie enthält.

*Fontsize*<br/>
Die logische Größe der Schriftart in DIP-Einheiten ("geräteunabhängiges Pixel"). Ein DIP entspricht 1/96 Zoll.

*Fontweight*<br/>
Ein Wert, der die Schriftgröße für das Textobjekt angibt.

*Fontstyle*<br/>
Ein Wert, der die Schriftart für das Textobjekt angibt.

*Fontstretch*<br/>
Ein Wert, der die Schriftartdehnung für das Textobjekt angibt.

*strFontLocale*<br/>
Ein CString-Objekt, das den Gebietsschemanamen enthält.

*pFontCollection*<br/>
Ein Zeiger auf ein Font-Auflistungsobjekt. Wenn dies NULL ist, gibt die Systemschriftartsammlung an.

*bAutoDestroy*<br/>
Gibt an, dass das Objekt vom Besitzer (pParentTarget) zerstört wird.

## <a name="cd2dtextformatcreate"></a><a name="create"></a>CD2DTextFormat::Erstellen

Erstellt ein CD2DTextFormat.

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT-Fehlercode zurückgegeben.

## <a name="cd2dtextformatdestroy"></a><a name="destroy"></a>CD2DTextFormat::Destroy

Zerstört ein CD2DTextFormat-Objekt.

```
virtual void Destroy();
```

## <a name="cd2dtextformatget"></a><a name="get"></a>CD2DTextFormat::Get

Gibt IDWriteTextFormat-Schnittstelle zurück

```
IDWriteTextFormat* Get();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine IDWriteTextFormat-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dtextformatgetfontfamilyname"></a><a name="getfontfamilyname"></a>CD2DTextFormat::GetFontFamilyName

Ruft eine Kopie des Schriftfamiliennamens ab.

```
CString GetFontFamilyName() const;
```

### <a name="return-value"></a>Rückgabewert

CString-Objekt, das den aktuellen Schriftfamiliennamen enthält.

## <a name="cd2dtextformatgetlocalename"></a><a name="getlocalename"></a>CD2DTextFormat::GetLocaleName

Ruft eine Kopie des Gebietsschemanamens ab.

```
CString GetLocaleName() const;
```

### <a name="return-value"></a>Rückgabewert

CString-Objekt, das den aktuellen Gebietsschemanamen enthält.

## <a name="cd2dtextformatisvalid"></a><a name="isvalid"></a>CD2DTextFormat::IsValid

Überprüft die Gültigkeit der Ressource

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Ressource gültig ist; andernfalls FALSE.

## <a name="cd2dtextformatm_ptextformat"></a><a name="m_ptextformat"></a>CD2DTextFormat::m_pTextFormat

Ein Zeiger auf ein IDWriteTextFormat.

```
IDWriteTextFormat* m_pTextFormat;
```

## <a name="cd2dtextformatoperator-idwritetextformat"></a><a name="operator_idwritetextformat_star"></a>CD2DTextFormat::operator IDWriteTextFormat*

Gibt IDWriteTextFormat-Schnittstelle zurück

```
operator IDWriteTextFormat*();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine IDWriteTextFormat-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dtextformatrecreate"></a><a name="recreate"></a>CD2DTextFormat::ReCreate

Erstellt ein CD2DTextFormat neu.

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT-Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)
