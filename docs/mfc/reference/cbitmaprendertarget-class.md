---
title: CBitmapRenderTarget-Klasse
ms.date: 11/04/2016
f1_keywords:
- CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::Attach
- AFXRENDERTARGET/CBitmapRenderTarget::Detach
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmap
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::m_pBitmapRenderTarget
helpviewer_keywords:
- CBitmapRenderTarget [MFC], CBitmapRenderTarget
- CBitmapRenderTarget [MFC], Attach
- CBitmapRenderTarget [MFC], Detach
- CBitmapRenderTarget [MFC], GetBitmap
- CBitmapRenderTarget [MFC], GetBitmapRenderTarget
- CBitmapRenderTarget [MFC], m_pBitmapRenderTarget
ms.assetid: c89a4437-812e-4943-acb2-b429a04cc4d2
ms.openlocfilehash: 6249c121f7bcca0675a8138baef0e2cdc9e632d8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352603"
---
# <a name="cbitmaprendertarget-class"></a>CBitmapRenderTarget-Klasse

Ein Wrapper für ID2D1BitmapRenderTarget.

## <a name="syntax"></a>Syntax

```
class CBitmapRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBitmapRenderTarget::CBitmapRenderTarget](#cbitmaprendertarget)|Erstellt ein CBitmapRenderTarget-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBitmapRenderTarget::Anfügen](#attach)|Fügt vorhandene Renderzielschnittstelle an das Objekt an|
|[CBitmapRenderTarget::Detach](#detach)|Trennt die Renderzielschnittstelle vom Objekt|
|[CBitmapRenderTarget::GetBitmap](#getbitmap)|Ruft die Bitmap für dieses Renderziel ab. Die zurückgegebene Bitmap kann für Zeichnungsvorgänge verwendet werden.|
|[CBitmapRenderTarget::GetBitmapRenderTarget](#getbitmaprendertarget)|Gibt ID2D1BitmapRenderTarget-Schnittstelle zurück|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBitmapRenderTarget::operator ID2D1BitmapRenderTarget*](#operator_id2d1bitmaprendertarget_star)|Gibt ID2D1BitmapRenderTarget-Schnittstelle zurück|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBitmapRenderTarget::m_pBitmapRenderTarget](#m_pbitmaprendertarget)|Ein Zeiger auf ein ID2D1BitmapRenderTarget-Objekt.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

`CBitmapRenderTarget`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxrendertarget.h

## <a name="cbitmaprendertargetattach"></a><a name="attach"></a>CBitmapRenderTarget::Anfügen

Fügt vorhandene Renderzielschnittstelle an das Objekt an

```
void Attach(ID2D1BitmapRenderTarget* pTarget);
```

### <a name="parameters"></a>Parameter

*pTarget*<br/>
Vorhandene Renderzielschnittstelle. Kann nicht NULL sein

## <a name="cbitmaprendertargetcbitmaprendertarget"></a><a name="cbitmaprendertarget"></a>CBitmapRenderTarget::CBitmapRenderTarget

Erstellt ein CBitmapRenderTarget-Objekt.

```
CBitmapRenderTarget();
```

## <a name="cbitmaprendertargetdetach"></a><a name="detach"></a>CBitmapRenderTarget::Detach

Trennt die Renderzielschnittstelle vom Objekt

```
ID2D1BitmapRenderTarget* Detach();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf die getrennte Renderzielschnittstelle.

## <a name="cbitmaprendertargetgetbitmap"></a><a name="getbitmap"></a>CBitmapRenderTarget::GetBitmap

Ruft die Bitmap für dieses Renderziel ab. Die zurückgegebene Bitmap kann für Zeichnungsvorgänge verwendet werden.

```
BOOL GetBitmap(CD2DBitmap& bitmap);
```

### <a name="parameters"></a>Parameter

*Bitmap*<br/>
Wenn diese Methode zurückgegeben wird, enthält die gültige Bitmap für dieses Renderziel. Diese Bitmap kann für Zeichnungsvorgänge verwendet werden.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="cbitmaprendertargetgetbitmaprendertarget"></a><a name="getbitmaprendertarget"></a>CBitmapRenderTarget::GetBitmapRenderTarget

Gibt ID2D1BitmapRenderTarget-Schnittstelle zurück

```
ID2D1BitmapRenderTarget* GetBitmapRenderTarget();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1BitmapRenderTarget-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cbitmaprendertargetm_pbitmaprendertarget"></a><a name="m_pbitmaprendertarget"></a>CBitmapRenderTarget::m_pBitmapRenderTarget

Ein Zeiger auf ein ID2D1BitmapRenderTarget-Objekt.

```
ID2D1BitmapRenderTarget* m_pBitmapRenderTarget;
```

## <a name="cbitmaprendertargetoperator-id2d1bitmaprendertarget"></a><a name="operator_id2d1bitmaprendertarget_star"></a>CBitmapRenderTarget::operator ID2D1BitmapRenderTarget*

Gibt ID2D1BitmapRenderTarget-Schnittstelle zurück

```
operator ID2D1BitmapRenderTarget*();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1BitmapRenderTarget-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)
