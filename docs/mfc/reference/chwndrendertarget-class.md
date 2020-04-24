---
title: CHwndRenderTarget-Klasse
ms.date: 11/04/2016
f1_keywords:
- CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::Attach
- AFXRENDERTARGET/CHwndRenderTarget::CheckWindowState
- AFXRENDERTARGET/CHwndRenderTarget::Create
- AFXRENDERTARGET/CHwndRenderTarget::Detach
- AFXRENDERTARGET/CHwndRenderTarget::GetHwnd
- AFXRENDERTARGET/CHwndRenderTarget::GetHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::ReCreate
- AFXRENDERTARGET/CHwndRenderTarget::Resize
- AFXRENDERTARGET/CHwndRenderTarget::m_pHwndRenderTarget
helpviewer_keywords:
- CHwndRenderTarget [MFC], CHwndRenderTarget
- CHwndRenderTarget [MFC], Attach
- CHwndRenderTarget [MFC], CheckWindowState
- CHwndRenderTarget [MFC], Create
- CHwndRenderTarget [MFC], Detach
- CHwndRenderTarget [MFC], GetHwnd
- CHwndRenderTarget [MFC], GetHwndRenderTarget
- CHwndRenderTarget [MFC], ReCreate
- CHwndRenderTarget [MFC], Resize
- CHwndRenderTarget [MFC], m_pHwndRenderTarget
ms.assetid: aa65b69f-7202-46ea-af81-ef325da0b840
ms.openlocfilehash: d1669d89183cd971e1afe0f05a1bad040f6b07df
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752701"
---
# <a name="chwndrendertarget-class"></a>CHwndRenderTarget-Klasse

Ein Wrapper für ID2D1HwndRenderTarget.

## <a name="syntax"></a>Syntax

```
class CHwndRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHwndRenderTarget::CHwndRenderTarget](#chwndrendertarget)|Erstellt ein CHwndRenderTarget-Objekt aus HWND.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHwndRenderTarget::Anfügen](#attach)|Fügt vorhandene Renderzielschnittstelle an das Objekt an|
|[CHwndRenderTarget::CheckWindowState](#checkwindowstate)|Gibt an, ob die diesem Renderziel zugeordnete HWND ausfällt.|
|[CHwndRenderTarget::Erstellen](#create)|Erstellt ein Renderziel, das dem Fenster zugeordnet ist|
|[CHwndRenderTarget::Detach](#detach)|Trennt die Renderzielschnittstelle vom Objekt|
|[CHwndRenderTarget::GetHwnd](#gethwnd)|Gibt die HWND zurück, die diesem Renderziel zugeordnet ist.|
|[CHwndRenderTarget::GetHwndRenderTarget](#gethwndrendertarget)|Gibt die ID2D1HwndRenderTarget-Schnittstelle zurück.|
|[CHwndRenderTarget::ReCreate](#recreate)|Erstellt ein Renderziel, das dem Fenster zugeordnet ist|
|[CHwndRenderTarget::Größe ändern](#resize)|Ändert die Größe des Renderziels auf die angegebene Pixelgröße|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHwndRenderTarget::operator ID2D1HwndRenderTarget*](#operator_id2d1hwndrendertarget_star)|Gibt die ID2D1HwndRenderTarget-Schnittstelle zurück.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHwndRenderTarget::m_pHwndRenderTarget](#m_phwndrendertarget)|Ein Zeiger auf ein ID2D1HwndRenderTarget-Objekt.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[CHwndRenderTarget](../../mfc/reference/chwndrendertarget-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxrendertarget.h

## <a name="chwndrendertargetattach"></a><a name="attach"></a>CHwndRenderTarget::Anfügen

Fügt vorhandene Renderzielschnittstelle an das Objekt an

```cpp
void Attach(ID2D1HwndRenderTarget* pTarget);
```

### <a name="parameters"></a>Parameter

*pTarget*<br/>
Vorhandene Renderzielschnittstelle. Kann nicht NULL sein

## <a name="chwndrendertargetcheckwindowstate"></a><a name="checkwindowstate"></a>CHwndRenderTarget::CheckWindowState

Gibt an, ob die diesem Renderziel zugeordnete HWND ausfällt.

```
D2D1_WINDOW_STATE CheckWindowState() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der angibt, ob die diesem Renderziel zugeordnete HWND ausgemacht ist.

## <a name="chwndrendertargetchwndrendertarget"></a><a name="chwndrendertarget"></a>CHwndRenderTarget::CHwndRenderTarget

Erstellt ein CHwndRenderTarget-Objekt aus HWND.

```
CHwndRenderTarget(HWND hwnd = NULL);
```

### <a name="parameters"></a>Parameter

*Hwnd*<br/>
Der HWND, der diesem Renderziel zugeordnet ist

## <a name="chwndrendertargetcreate"></a><a name="create"></a>CHwndRenderTarget::Erstellen

Erstellt ein Renderziel, das dem Fenster zugeordnet ist

```
BOOL Create(HWND hWnd);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
Der HWND, der diesem Renderziel zugeordnet ist

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="chwndrendertargetdetach"></a><a name="detach"></a>CHwndRenderTarget::Detach

Trennt die Renderzielschnittstelle vom Objekt

```
ID2D1HwndRenderTarget* Detach();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf die getrennte Renderzielschnittstelle.

## <a name="chwndrendertargetgethwnd"></a><a name="gethwnd"></a>CHwndRenderTarget::GetHwnd

Gibt die HWND zurück, die diesem Renderziel zugeordnet ist.

```
HWND GetHwnd() const;
```

### <a name="return-value"></a>Rückgabewert

Die DIESEM Renderziel zugeordnete HWND.

## <a name="chwndrendertargetgethwndrendertarget"></a><a name="gethwndrendertarget"></a>CHwndRenderTarget::GetHwndRenderTarget

Gibt die ID2D1HwndRenderTarget-Schnittstelle zurück.

```
ID2D1HwndRenderTarget* GetHwndRenderTarget();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1HwndRenderTarget-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="chwndrendertargetm_phwndrendertarget"></a><a name="m_phwndrendertarget"></a>CHwndRenderTarget::m_pHwndRenderTarget

Ein Zeiger auf ein ID2D1HwndRenderTarget-Objekt.

```
ID2D1HwndRenderTarget* m_pHwndRenderTarget;
```

## <a name="chwndrendertargetoperator-id2d1hwndrendertarget"></a><a name="operator_id2d1hwndrendertarget_star"></a>CHwndRenderTarget::operator ID2D1HwndRenderTarget*

Gibt die ID2D1HwndRenderTarget-Schnittstelle zurück.

```
operator ID2D1HwndRenderTarget*();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1HwndRenderTarget-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="chwndrendertargetrecreate"></a><a name="recreate"></a>CHwndRenderTarget::ReCreate

Erstellt ein Renderziel, das dem Fenster zugeordnet ist

```
BOOL ReCreate(HWND hWnd);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
Der HWND, der diesem Renderziel zugeordnet ist

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="chwndrendertargetresize"></a><a name="resize"></a>CHwndRenderTarget::Größe ändern

Ändert die Größe des Renderziels auf die angegebene Pixelgröße

```
BOOL Resize(const CD2DSizeU& size);
```

### <a name="parameters"></a>Parameter

*size*<br/>
Die neue Größe des Renderziels in Gerätepixeln

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)
