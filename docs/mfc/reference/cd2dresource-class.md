---
title: CD2DResource-Klasse
ms.date: 03/27/2019
f1_keywords:
- CD2DResource
- AFXRENDERTARGET/CD2DResource
- AFXRENDERTARGET/CD2DResource::CD2DResource
- AFXRENDERTARGET/CD2DResource::Create
- AFXRENDERTARGET/CD2DResource::Destroy
- AFXRENDERTARGET/CD2DResource::IsValid
- AFXRENDERTARGET/CD2DResource::IsAutoDestroy
- AFXRENDERTARGET/CD2DResource::ReCreate
- AFXRENDERTARGET/CD2DResource::m_bIsAutoDestroy
- AFXRENDERTARGET/CD2DResource::m_pParentTarget
helpviewer_keywords:
- CD2DResource [MFC], CD2DResource
- CD2DResource [MFC], Create
- CD2DResource [MFC], Destroy
- CD2DResource [MFC], IsValid
- CD2DResource [MFC], IsAutoDestroy
- CD2DResource [MFC], ReCreate
- CD2DResource [MFC], m_bIsAutoDestroy
- CD2DResource [MFC], m_pParentTarget
ms.assetid: 34e3ee18-aab6-4c39-9294-de869e1f7820
ms.openlocfilehash: 5e747eda42e625d0f4cf65859e471933bbb043ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369094"
---
# <a name="cd2dresource-class"></a>CD2DResource-Klasse

Eine abstrakte Klasse, die eine Schnittstelle zum Erstellen und Verwalten von D2D-Ressourcen wie Pinsel, Ebenen und Texten bereitstellt.

## <a name="syntax"></a>Syntax

```
class CD2DResource : public CObject;
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DResource::CD2DResource](#cd2dresource)|Erstellt ein CD2DResource-Objekt.|
|[CD2DResource::-CD2DResource](#_dtorcd2dresource)|Der Destruktor. Wird aufgerufen, wenn ein D2D-Ressourcenobjekt zerstört wird.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DResource::Erstellen](#create)|Erstellt eine CD2DResource.|
|[CD2DResource::Destroy](#destroy)|Zerstört ein CD2DResource-Objekt.|
|[CD2DResource::IsValid](#isvalid)|Überprüft die Gültigkeit der Ressource|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DResource::IsAutoDestroy](#isautodestroy)|Überprüfen Sie die automatische Zerstörungsflagge.|
|[CD2DResource::ReCreate](#recreate)|Erstellt eine CD2DResource neu.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DResource::m_bIsAutoDestroy](#m_bisautodestroy)|Ressource wird vom Besitzer zerstört (CRenderTarget)|
|[CD2DResource::m_pParentTarget](#m_pparenttarget)|Zeiger auf das übergeordnete CRenderTarget)|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CD2DResource`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxrendertarget.h

## <a name="cd2dresourcecd2dresource"></a><a name="_dtorcd2dresource"></a>CD2DResource::-CD2DResource

Der Destruktor. Wird aufgerufen, wenn ein D2D-Ressourcenobjekt zerstört wird.

```
virtual ~CD2DResource();
```

## <a name="cd2dresourcecd2dresource"></a><a name="cd2dresource"></a>CD2DResource::CD2DResource

Erstellt ein CD2DResource-Objekt.

```
CD2DResource(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy);
```

### <a name="parameters"></a>Parameter

*pParentTarget*<br/>
Ein Zeiger auf das Renderziel.

*bAutoDestroy*<br/>
Gibt an, dass das Objekt vom Besitzer (pParentTarget) zerstört wird.

## <a name="cd2dresourcecreate"></a><a name="create"></a>CD2DResource::Erstellen

Erstellt eine CD2DResource.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget) = 0;
```

### <a name="parameters"></a>Parameter

*pRenderTarget*<br/>
Ein Zeiger auf das Renderziel.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT-Fehlercode zurückgegeben.

## <a name="cd2dresourcedestroy"></a><a name="destroy"></a>CD2DResource::Destroy

Zerstört ein CD2DResource-Objekt.

```
virtual void Destroy() = 0;
```

## <a name="cd2dresourceisautodestroy"></a><a name="isautodestroy"></a>CD2DResource::IsAutoDestroy

Überprüfen Sie die automatische Zerstörungsflagge.

```
BOOL IsAutoDestroy() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Objekt von seinem Besitzer zerstört wird; andernfalls FALSE.

## <a name="cd2dresourceisvalid"></a><a name="isvalid"></a>CD2DResource::IsValid

Überprüft die Gültigkeit der Ressource

```
virtual BOOL IsValid() const = 0;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Ressource gültig ist; andernfalls FALSE.

## <a name="cd2dresourcem_bisautodestroy"></a><a name="m_bisautodestroy"></a>CD2DResource::m_bIsAutoDestroy

Ressource wird vom Besitzer zerstört (CRenderTarget)

```
BOOL m_bIsAutoDestroy;
```

## <a name="cd2dresourcem_pparenttarget"></a><a name="m_pparenttarget"></a>CD2DResource::m_pParentTarget

Zeiger auf das übergeordnete CRenderTarget)

```
CRenderTarget* m_pParentTarget;
```

## <a name="cd2dresourcerecreate"></a><a name="recreate"></a>CD2DResource::ReCreate

Erstellt eine CD2DResource neu.

```
virtual HRESULT ReCreate(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parameter

*pRenderTarget*<br/>
Ein Zeiger auf das Renderziel.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT-Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)
