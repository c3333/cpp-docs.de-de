---
title: CD2DLayer-Klasse
ms.date: 11/04/2016
f1_keywords:
- CD2DLayer
- AFXRENDERTARGET/CD2DLayer
- AFXRENDERTARGET/CD2DLayer::CD2DLayer
- AFXRENDERTARGET/CD2DLayer::Attach
- AFXRENDERTARGET/CD2DLayer::Create
- AFXRENDERTARGET/CD2DLayer::Destroy
- AFXRENDERTARGET/CD2DLayer::Detach
- AFXRENDERTARGET/CD2DLayer::Get
- AFXRENDERTARGET/CD2DLayer::GetSize
- AFXRENDERTARGET/CD2DLayer::IsValid
- AFXRENDERTARGET/CD2DLayer::m_pLayer
helpviewer_keywords:
- CD2DLayer [MFC], CD2DLayer
- CD2DLayer [MFC], Attach
- CD2DLayer [MFC], Create
- CD2DLayer [MFC], Destroy
- CD2DLayer [MFC], Detach
- CD2DLayer [MFC], Get
- CD2DLayer [MFC], GetSize
- CD2DLayer [MFC], IsValid
- CD2DLayer [MFC], m_pLayer
ms.assetid: 2f96378e-66bb-40d1-9661-6afe324de3c1
ms.openlocfilehash: aa6fb313bfcc2983f167936e5ad4f78be1e17a44
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369216"
---
# <a name="cd2dlayer-class"></a>CD2DLayer-Klasse

Ein Wrapper für ID2D1Layer.

## <a name="syntax"></a>Syntax

```
class CD2DLayer : public CD2DResource;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DLayer::CD2DLayer](#cd2dlayer)|Erstellt ein CD2DLayer-Objekt.|
|[CD2DLayer::-CD2DLayer](#_dtorcd2dlayer)|Der Destruktor. Wird aufgerufen, wenn ein D2D-Layerobjekt zerstört wird.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DLayer::Anfügen](#attach)|Fügt vorhandene Ressourcenschnittstelle an das Objekt an|
|[CD2DLayer::Erstellen](#create)|Erstellt einen CD2DLayer. (Überschreibt [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DLayer::Destroy](#destroy)|Zerstört ein CD2DLayer-Objekt. (Überschreibt [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DLayer::Detach](#detach)|Trennen der Ressourcenschnittstelle vom Objekt|
|[CD2DLayer::Get](#get)|Gibt ID2D1Layer-Schnittstelle zurück|
|[CD2DLayer::GetSize](#getsize)|Gibt die Größe des Renderziels in geräteunabhängigen Pixeln zurück|
|[CD2DLayer::IsValid](#isvalid)|Überprüft die Ressourcengültigkeit (Überschreibt [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DLayer::operator ID2D1Layer*](#operator_id2d1layer_star)|Gibt ID2D1Layer-Schnittstelle zurück|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DLayer::m_pLayer](#m_player)|Speichert einen Zeiger auf ein ID2D1Layer-Objekt.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DLayer`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxrendertarget.h

## <a name="cd2dlayercd2dlayer"></a><a name="_dtorcd2dlayer"></a>CD2DLayer::-CD2DLayer

Der Destruktor. Wird aufgerufen, wenn ein D2D-Layerobjekt zerstört wird.

```
virtual ~CD2DLayer();
```

## <a name="cd2dlayerattach"></a><a name="attach"></a>CD2DLayer::Anfügen

Fügt vorhandene Ressourcenschnittstelle an das Objekt an

```
void Attach(ID2D1Layer* pResource);
```

### <a name="parameters"></a>Parameter

*pResource*<br/>
Vorhandene Ressourcenschnittstelle. Kann nicht NULL sein

## <a name="cd2dlayercd2dlayer"></a><a name="cd2dlayer"></a>CD2DLayer::CD2DLayer

Erstellt ein CD2DLayer-Objekt.

```
CD2DLayer(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parameter

*pParentTarget*<br/>
Ein Zeiger auf das Renderziel.

*bAutoDestroy*<br/>
Gibt an, dass das Objekt vom Besitzer (pParentTarget) zerstört wird.

## <a name="cd2dlayercreate"></a><a name="create"></a>CD2DLayer::Erstellen

Erstellt einen CD2DLayer.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parameter

*pRenderTarget*<br/>
Ein Zeiger auf das Renderziel.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT-Fehlercode zurückgegeben.

## <a name="cd2dlayerdestroy"></a><a name="destroy"></a>CD2DLayer::Destroy

Zerstört ein CD2DLayer-Objekt.

```
virtual void Destroy();
```

## <a name="cd2dlayerdetach"></a><a name="detach"></a>CD2DLayer::Detach

Trennen der Ressourcenschnittstelle vom Objekt

```
ID2D1Layer* Detach();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine getrennte Ressourcenschnittstelle.

## <a name="cd2dlayerget"></a><a name="get"></a>CD2DLayer::Get

Gibt ID2D1Layer-Schnittstelle zurück

```
ID2D1Layer* Get();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1Layer-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dlayergetsize"></a><a name="getsize"></a>CD2DLayer::GetSize

Gibt die Größe des Renderziels in geräteunabhängigen Pixeln zurück

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Größe des Renderziels in geräteunabhängigen Pixeln

## <a name="cd2dlayerisvalid"></a><a name="isvalid"></a>CD2DLayer::IsValid

Überprüft die Gültigkeit der Ressource

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Ressource gültig ist; andernfalls FALSE.

## <a name="cd2dlayerm_player"></a><a name="m_player"></a>CD2DLayer::m_pLayer

Speichert einen Zeiger auf ein ID2D1Layer-Objekt.

```
ID2D1Layer* m_pLayer;
```

## <a name="cd2dlayeroperator-id2d1layer"></a><a name="operator_id2d1layer_star"></a>CD2DLayer::operator ID2D1Layer*

Gibt ID2D1Layer-Schnittstelle zurück

```
operator ID2D1Layer* ();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1Layer-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)
