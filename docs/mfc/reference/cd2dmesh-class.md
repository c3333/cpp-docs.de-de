---
title: CD2DMesh-Klasse
ms.date: 11/04/2016
f1_keywords:
- CD2DMesh
- AFXRENDERTARGET/CD2DMesh
- AFXRENDERTARGET/CD2DMesh::CD2DMesh
- AFXRENDERTARGET/CD2DMesh::Attach
- AFXRENDERTARGET/CD2DMesh::Create
- AFXRENDERTARGET/CD2DMesh::Destroy
- AFXRENDERTARGET/CD2DMesh::Detach
- AFXRENDERTARGET/CD2DMesh::Get
- AFXRENDERTARGET/CD2DMesh::IsValid
- AFXRENDERTARGET/CD2DMesh::Open
- AFXRENDERTARGET/CD2DMesh::m_pMesh
helpviewer_keywords:
- CD2DMesh [MFC], CD2DMesh
- CD2DMesh [MFC], Attach
- CD2DMesh [MFC], Create
- CD2DMesh [MFC], Destroy
- CD2DMesh [MFC], Detach
- CD2DMesh [MFC], Get
- CD2DMesh [MFC], IsValid
- CD2DMesh [MFC], Open
- CD2DMesh [MFC], m_pMesh
ms.assetid: 11a2c78a-1367-40e8-a34f-44aa0509a4c9
ms.openlocfilehash: 64f5dd7b40853a86dc7f964ecd3701f132a94e16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369185"
---
# <a name="cd2dmesh-class"></a>CD2DMesh-Klasse

Ein Wrapper für ID2D1Mesh.

## <a name="syntax"></a>Syntax

```
class CD2DMesh : public CD2DResource;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DMesh::CD2DMesh](#cd2dmesh)|Erstellt ein CD2DMesh-Objekt.|
|[CD2DMesh::-CD2DMesh](#_dtorcd2dmesh)|Der Destruktor. Wird aufgerufen, wenn ein D2D-Netzobjekt zerstört wird.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DMesh::Anfügen](#attach)|Fügt vorhandene Ressourcenschnittstelle an das Objekt an|
|[CD2DMesh::Erstellen](#create)|Erstellt ein CD2DMesh. (Überschreibt [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DMesh::Destroy](#destroy)|Zerstört ein CD2DMesh-Objekt. (Überschreibt [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DMesh::Detach](#detach)|Trennen der Ressourcenschnittstelle vom Objekt|
|[CD2DMesh::Get](#get)|Gibt ID2D1Mesh-Schnittstelle zurück|
|[CD2DMesh::IsValid](#isvalid)|Überprüft die Ressourcengültigkeit (Überschreibt [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DMesh::Öffnen](#open)|Öffnet das Netz für die Grundgesamtheit.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DMesh::operator ID2D1Mesh*](#operator_id2d1mesh_star)|Gibt ID2D1Mesh-Schnittstelle zurück|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DMesh::m_pMesh](#m_pmesh)|Ein Zeiger auf ein ID2D1Mesh.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DMesh`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxrendertarget.h

## <a name="cd2dmeshcd2dmesh"></a><a name="_dtorcd2dmesh"></a>CD2DMesh::-CD2DMesh

Der Destruktor. Wird aufgerufen, wenn ein D2D-Netzobjekt zerstört wird.

```
virtual ~CD2DMesh();
```

## <a name="cd2dmeshattach"></a><a name="attach"></a>CD2DMesh::Anfügen

Fügt vorhandene Ressourcenschnittstelle an das Objekt an

```
void Attach(ID2D1Mesh* pResource);
```

### <a name="parameters"></a>Parameter

*pResource*<br/>
Vorhandene Ressourcenschnittstelle. Kann nicht NULL sein

## <a name="cd2dmeshcd2dmesh"></a><a name="cd2dmesh"></a>CD2DMesh::CD2DMesh

Erstellt ein CD2DMesh-Objekt.

```
CD2DMesh(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parameter

*pParentTarget*<br/>
Ein Zeiger auf das Renderziel.

*bAutoDestroy*<br/>
Gibt an, dass das Objekt vom Besitzer (pParentTarget) zerstört wird.

## <a name="cd2dmeshcreate"></a><a name="create"></a>CD2DMesh::Erstellen

Erstellt ein CD2DMesh.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parameter

*pRenderTarget*<br/>
Ein Zeiger auf das Renderziel.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT-Fehlercode zurückgegeben.

## <a name="cd2dmeshdestroy"></a><a name="destroy"></a>CD2DMesh::Destroy

Zerstört ein CD2DMesh-Objekt.

```
virtual void Destroy();
```

## <a name="cd2dmeshdetach"></a><a name="detach"></a>CD2DMesh::Detach

Trennen der Ressourcenschnittstelle vom Objekt

```
ID2D1Mesh* Detach();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine getrennte Ressourcenschnittstelle.

## <a name="cd2dmeshget"></a><a name="get"></a>CD2DMesh::Get

Gibt ID2D1Mesh-Schnittstelle zurück

```
ID2D1Mesh* Get();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1Mesh-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dmeshisvalid"></a><a name="isvalid"></a>CD2DMesh::IsValid

Überprüft die Gültigkeit der Ressource

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Ressource gültig ist; andernfalls FALSE.

## <a name="cd2dmeshm_pmesh"></a><a name="m_pmesh"></a>CD2DMesh::m_pMesh

Ein Zeiger auf ein ID2D1Mesh.

```
ID2D1Mesh* m_pMesh;
```

## <a name="cd2dmeshopen"></a><a name="open"></a>CD2DMesh::Öffnen

Öffnet das Netz für die Grundgesamtheit.

```
ID2D1TessellationSink* Open();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine ID2D1TessellationSink, die zum Auffüllen des Netzes verwendet wird.

## <a name="cd2dmeshoperator-id2d1mesh"></a><a name="operator_id2d1mesh_star"></a>CD2DMesh::operator ID2D1Mesh*

Gibt ID2D1Mesh-Schnittstelle zurück

```
operator ID2D1Mesh*();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1Mesh-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)
