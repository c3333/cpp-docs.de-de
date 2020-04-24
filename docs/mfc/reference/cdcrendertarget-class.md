---
title: CDCRenderTarget-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::Attach
- AFXRENDERTARGET/CDCRenderTarget::BindDC
- AFXRENDERTARGET/CDCRenderTarget::Create
- AFXRENDERTARGET/CDCRenderTarget::Detach
- AFXRENDERTARGET/CDCRenderTarget::GetDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::m_pDCRenderTarget
helpviewer_keywords:
- CDCRenderTarget [MFC], CDCRenderTarget
- CDCRenderTarget [MFC], Attach
- CDCRenderTarget [MFC], BindDC
- CDCRenderTarget [MFC], Create
- CDCRenderTarget [MFC], Detach
- CDCRenderTarget [MFC], GetDCRenderTarget
- CDCRenderTarget [MFC], m_pDCRenderTarget
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
ms.openlocfilehash: 8c07962c017d160cb3ce5841a75f1ae8a8761641
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753395"
---
# <a name="cdcrendertarget-class"></a>CDCRenderTarget-Klasse

Ein Wrapper für ID2D1DCRenderTarget.

## <a name="syntax"></a>Syntax

```
class CDCRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDCRenderTarget::CDCRenderTarget](#cdcrendertarget)|Erstellt ein CDCRenderTarget-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDCRenderTarget::Anfügen](#attach)|Fügt vorhandene Renderzielschnittstelle an das Objekt an|
|[CDCRenderTarget::BindDC](#binddc)|Bindet das Renderziel an den Gerätekontext, an den es Zeichnungsbefehle ausgibt|
|[CDCRenderTarget::Erstellen](#create)|Erstellt ein CDCRenderTarget.|
|[CDCRenderTarget::Detach](#detach)|Trennt die Renderzielschnittstelle vom Objekt|
|[CDCRenderTarget::GetDCRenderTarget](#getdcrendertarget)|Gibt ID2D1DCRenderTarget-Schnittstelle zurück|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDCRenderTarget::operator ID2D1DCRenderTarget*](#operator_id2d1dcrendertarget_star)|Gibt ID2D1DCRenderTarget-Schnittstelle zurück|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDCRenderTarget::m_pDCRenderTarget](#m_pdcrendertarget)|Ein Zeiger auf ein ID2D1DCRenderTarget-Objekt.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[CDCRenderTarget](../../mfc/reference/cdcrendertarget-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxrendertarget.h

## <a name="cdcrendertargetattach"></a><a name="attach"></a>CDCRenderTarget::Anfügen

Fügt vorhandene Renderzielschnittstelle an das Objekt an

```cpp
void Attach(ID2D1DCRenderTarget* pTarget);
```

### <a name="parameters"></a>Parameter

*pTarget*<br/>
Vorhandene Renderzielschnittstelle. Kann nicht NULL sein

## <a name="cdcrendertargetbinddc"></a><a name="binddc"></a>CDCRenderTarget::BindDC

Bindet das Renderziel an den Gerätekontext, an den es Zeichnungsbefehle ausgibt

```
BOOL BindDC(
    const CDC& dc,
    const CRect& rect);
```

### <a name="parameters"></a>Parameter

*Dc*<br/>
Der Gerätekontext, in den das Renderziel Zeichnungsbefehle ausgibt

*Rect*<br/>
Die Abmessungen des Handles an einen Gerätekontext (HDC), an den das Renderziel gebunden ist

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="cdcrendertargetcdcrendertarget"></a><a name="cdcrendertarget"></a>CDCRenderTarget::CDCRenderTarget

Erstellt ein CDCRenderTarget-Objekt.

```
CDCRenderTarget();
```

## <a name="cdcrendertargetcreate"></a><a name="create"></a>CDCRenderTarget::Erstellen

Erstellt ein CDCRenderTarget.

```
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```

### <a name="parameters"></a>Parameter

*Props*<br/>
Der Rendering-Modus, das Pixelformat, die Remote-Optionen, dPI-Informationen und die minimale DirectX-Unterstützung, die für das Hardware-Rendering erforderlich ist.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="cdcrendertargetdetach"></a><a name="detach"></a>CDCRenderTarget::Detach

Trennt die Renderzielschnittstelle vom Objekt

```
ID2D1DCRenderTarget* Detach();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf die getrennte Renderzielschnittstelle.

## <a name="cdcrendertargetgetdcrendertarget"></a><a name="getdcrendertarget"></a>CDCRenderTarget::GetDCRenderTarget

Gibt ID2D1DCRenderTarget-Schnittstelle zurück

```
ID2D1DCRenderTarget* GetDCRenderTarget();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1DCRenderTarget-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cdcrendertargetm_pdcrendertarget"></a><a name="m_pdcrendertarget"></a>CDCRenderTarget::m_pDCRenderTarget

Ein Zeiger auf ein ID2D1DCRenderTarget-Objekt.

```
ID2D1DCRenderTarget* m_pDCRenderTarget;
```

## <a name="cdcrendertargetoperator-id2d1dcrendertarget"></a><a name="operator_id2d1dcrendertarget_star"></a>CDCRenderTarget::operator ID2D1DCRenderTarget*

Gibt ID2D1DCRenderTarget-Schnittstelle zurück

```
operator ID2D1DCRenderTarget*();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1DCRenderTarget-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)
