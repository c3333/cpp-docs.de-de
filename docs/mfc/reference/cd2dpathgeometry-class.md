---
title: CD2DPathGeometry-Klasse
ms.date: 11/04/2016
f1_keywords:
- CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::Attach
- AFXRENDERTARGET/CD2DPathGeometry::Create
- AFXRENDERTARGET/CD2DPathGeometry::Destroy
- AFXRENDERTARGET/CD2DPathGeometry::Detach
- AFXRENDERTARGET/CD2DPathGeometry::GetFigureCount
- AFXRENDERTARGET/CD2DPathGeometry::GetSegmentCount
- AFXRENDERTARGET/CD2DPathGeometry::Open
- AFXRENDERTARGET/CD2DPathGeometry::Stream
- AFXRENDERTARGET/CD2DPathGeometry::m_pPathGeometry
helpviewer_keywords:
- CD2DPathGeometry [MFC], CD2DPathGeometry
- CD2DPathGeometry [MFC], Attach
- CD2DPathGeometry [MFC], Create
- CD2DPathGeometry [MFC], Destroy
- CD2DPathGeometry [MFC], Detach
- CD2DPathGeometry [MFC], GetFigureCount
- CD2DPathGeometry [MFC], GetSegmentCount
- CD2DPathGeometry [MFC], Open
- CD2DPathGeometry [MFC], Stream
- CD2DPathGeometry [MFC], m_pPathGeometry
ms.assetid: 686216eb-5080-4242-ace5-8fa1ce96307c
ms.openlocfilehash: 91460e3435130530ecc57bdcc09d1c7301333a3b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753074"
---
# <a name="cd2dpathgeometry-class"></a>CD2DPathGeometry-Klasse

Ein Wrapper für ID2D1PathGeometry.

## <a name="syntax"></a>Syntax

```
class CD2DPathGeometry : public CD2DGeometry;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DPathGeometry::CD2DPathGeometry](#cd2dpathgeometry)|Erstellt ein CD2DPathGeometry-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DPathGeometry::Anfügen](#attach)|Fügt vorhandene Ressourcenschnittstelle an das Objekt an|
|[CD2DPathGeometry::Erstellen](#create)|Erstellt eine CD2DPathGeometry. (Überschreibt [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DPathGeometry::Destroy](#destroy)|Zerstört ein CD2DPathGeometry-Objekt. (Überschreibt [CD2DGeometry::Destroy](../../mfc/reference/cd2dgeometry-class.md#destroy).)|
|[CD2DPathGeometry::Detach](#detach)|Trennen der Ressourcenschnittstelle vom Objekt|
|[CD2DPathGeometry::GetFigureCount](#getfigurecount)|Ruft die Anzahl der Figuren in der Pfadgeometrie ab.|
|[CD2DPathGeometry::GetSegmentCount](#getsegmentcount)|Ruft die Anzahl der Segmente in der Pfadgeometrie ab.|
|[CD2DPathGeometry::Öffnen](#open)|Ruft die Geometriesenke ab, die zum Auffüllen der Pfadgeometrie mit Figuren und Segmenten verwendet wird.|
|[CD2DPathGeometry::Stream](#stream)|Kopiert den Inhalt der Pfadgeometrie in die angegebene ID2D1GeometrySink.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DPathGeometry::m_pPathGeometry](#m_ppathgeometry)|Ein Zeiger auf eine ID2D1PathGeometry.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DGeometry](../../mfc/reference/cd2dgeometry-class.md)

`CD2DPathGeometry`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxrendertarget.h

## <a name="cd2dpathgeometryattach"></a><a name="attach"></a>CD2DPathGeometry::Anfügen

Fügt vorhandene Ressourcenschnittstelle an das Objekt an

```cpp
void Attach(ID2D1PathGeometry* pResource);
```

### <a name="parameters"></a>Parameter

*pResource*<br/>
Vorhandene Ressourcenschnittstelle. Kann nicht NULL sein

## <a name="cd2dpathgeometrycd2dpathgeometry"></a><a name="cd2dpathgeometry"></a>CD2DPathGeometry::CD2DPathGeometry

Erstellt ein CD2DPathGeometry-Objekt.

```
CD2DPathGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parameter

*pParentTarget*<br/>
Ein Zeiger auf das Renderziel.

*bAutoDestroy*<br/>
Gibt an, dass das Objekt vom Besitzer (pParentTarget) zerstört wird.

## <a name="cd2dpathgeometrycreate"></a><a name="create"></a>CD2DPathGeometry::Erstellen

Erstellt eine CD2DPathGeometry.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parameter

*pRenderTarget*<br/>
Ein Zeiger auf das Renderziel.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT-Fehlercode zurückgegeben.

## <a name="cd2dpathgeometrydestroy"></a><a name="destroy"></a>CD2DPathGeometry::Destroy

Zerstört ein CD2DPathGeometry-Objekt.

```
virtual void Destroy();
```

## <a name="cd2dpathgeometrydetach"></a><a name="detach"></a>CD2DPathGeometry::Detach

Trennen der Ressourcenschnittstelle vom Objekt

```
ID2D1PathGeometry* Detach();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine getrennte Ressourcenschnittstelle.

## <a name="cd2dpathgeometrygetfigurecount"></a><a name="getfigurecount"></a>CD2DPathGeometry::GetFigureCount

Ruft die Anzahl der Figuren in der Pfadgeometrie ab.

```
int GetFigureCount() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Figuren in der Pfadgeometrie zurück.

## <a name="cd2dpathgeometrygetsegmentcount"></a><a name="getsegmentcount"></a>CD2DPathGeometry::GetSegmentCount

Ruft die Anzahl der Segmente in der Pfadgeometrie ab.

```
int GetSegmentCount() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Segmente in der Pfadgeometrie zurück.

## <a name="cd2dpathgeometrym_ppathgeometry"></a><a name="m_ppathgeometry"></a>CD2DPathGeometry::m_pPathGeometry

Ein Zeiger auf eine ID2D1PathGeometry.

```
ID2D1PathGeometry* m_pPathGeometry;
```

## <a name="cd2dpathgeometryopen"></a><a name="open"></a>CD2DPathGeometry::Öffnen

Ruft die Geometriesenke ab, die zum Auffüllen der Pfadgeometrie mit Figuren und Segmenten verwendet wird.

```
ID2D1GeometrySink* Open();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die ID2D1GeometrySink, die zum Auffüllen der Pfadgeometrie mit Figuren und Segmenten verwendet wird.

## <a name="cd2dpathgeometrystream"></a><a name="stream"></a>CD2DPathGeometry::Stream

Kopiert den Inhalt der Pfadgeometrie in die angegebene ID2D1GeometrySink.

```
BOOL Stream(ID2D1GeometrySink* geometrySink);
```

### <a name="parameters"></a>Parameter

*geometrySink*<br/>
Die Senke, in die der Inhalt der Pfadgeometrie kopiert wird. Durch das Ändern dieser Senke wird der Inhalt dieser Pfadgeometrie nicht geändert.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)
