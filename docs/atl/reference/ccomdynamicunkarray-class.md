---
title: CComDynamicUnkArray-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::Add
- ATLCOM/ATL::CComDynamicUnkArray::begin
- ATLCOM/ATL::CComDynamicUnkArray::clear
- ATLCOM/ATL::CComDynamicUnkArray::end
- ATLCOM/ATL::CComDynamicUnkArray::GetAt
- ATLCOM/ATL::CComDynamicUnkArray::GetCookie
- ATLCOM/ATL::CComDynamicUnkArray::GetSize
- ATLCOM/ATL::CComDynamicUnkArray::GetUnknown
- ATLCOM/ATL::CComDynamicUnkArray::Remove
helpviewer_keywords:
- connection points [C++], managing
- CComDynamicUnkArray class
ms.assetid: 202470d7-9a1b-498f-b96d-659d681acd65
ms.openlocfilehash: 51b1d7e81c98bd5dbcf957b1705e7a717bfb9ab0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747981"
---
# <a name="ccomdynamicunkarray-class"></a>CComDynamicUnkArray-Klasse

Diese Klasse speichert `IUnknown` ein Array von Zeigern.

## <a name="syntax"></a>Syntax

```
class CComDynamicUnkArray
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|Konstruktor. Initialisiert die Auflistungswerte auf NULL und die Auflistungsgröße auf Null.|
|[CComDynamicUnkArray::'CComDynamicUnkArray](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComDynamicUnkArray::Hinzufügen](#add)|Rufen Sie diese `IUnknown` Methode auf, um dem Array einen Zeiger hinzuzufügen.|
|[CComDynamicUnkArray::begin](#begin)|Gibt einen Zeiger auf `IUnknown` den ersten Zeiger in der Auflistung zurück.|
|[CComDynamicUnkArray::clear](#clear)|Leert das Array.|
|[CComDynamicUnkArray::end](#end)|Gibt einen Zeiger auf einen `IUnknown` Zeiger hinter dem letzten Zeiger in der Auflistung zurück.|
|[CComDynamicUnkArray::Getat](#getat)|Entfernt das Element am angegebenen Index.|
|[CComDynamicUnkArray::GetCookie](#getcookie)|Rufen Sie diese Methode auf, `IUnknown` um das Cookie abzurufen, das einem bestimmten Zeiger zugeordnet ist.|
|[CComDynamicUnkArray::GetSize](#getsize)|Gibt die Länge eines Arrays zurück.|
|[CComDynamicUnkArray::GetUnknown](#getunknown)|Rufen Sie diese `IUnknown` Methode auf, um den Zeiger abzurufen, der einem bestimmten Cookie zugeordnet ist.|
|[CComDynamicUnkArray::Entfernen](#remove)|Rufen Sie diese `IUnknown` Methode auf, um einen Zeiger aus dem Array zu entfernen.|

## <a name="remarks"></a>Bemerkungen

`CComDynamicUnkArray`enthält ein dynamisch `IUnknown` zugewiesenes Array von Zeigern, jeweils eine Schnittstelle auf einem Verbindungspunkt. `CComDynamicUnkArray`kann als Parameter für die [IConnectionPointImpl-Vorlagenklasse](../../atl/reference/iconnectionpointimpl-class.md) verwendet werden.

Die `CComDynamicUnkArray` Methoden [begin](#begin) and [end](#end) können verwendet werden, um alle Verbindungspunkte zu durchlaufen (z. B. wenn ein Ereignis ausgelöst wird).

Weitere Informationen zum Automatisieren der Erstellung von Verbindungspunktproxys finden Sie unter [Hinzufügen von Verbindungspunkten zu einem Objekt.](../../atl/adding-connection-points-to-an-object.md)

> [!NOTE]
> **Hinweis** Die `CComDynamicUnkArray` Klasse wird vom Assistenten zum Hinzufügen von **Klassen** verwendet, wenn ein Steuerelement mit Verbindungspunkten erstellt wird. Wenn Sie die Anzahl der Verbindungspunkte manuell angeben `CComDynamicUnkArray` möchten, ändern Sie den Verweis von `CComUnkArray<` *n* `>`, wobei *n* die Anzahl der erforderlichen Verbindungspunkte ist.

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlcom.h

## <a name="ccomdynamicunkarrayadd"></a><a name="add"></a>CComDynamicUnkArray::Hinzufügen

Rufen Sie diese `IUnknown` Methode auf, um dem Array einen Zeiger hinzuzufügen.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Parameter

*Punk*<br/>
Der `IUnknown` Zeiger, der dem Array hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt das Cookie zurück, das dem neu hinzugefügten Zeiger zugeordnet ist.

## <a name="ccomdynamicunkarraybegin"></a><a name="begin"></a>CComDynamicUnkArray::begin

Gibt einen Zeiger auf den Anfang `IUnknown` der Auflistung von Schnittstellenzeigern zurück.

```
IUnknown**
    begin();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `IUnknown` einen Schnittstellenzeiger.

### <a name="remarks"></a>Bemerkungen

Die Auflistung enthält Zeiger auf Schnittstellen, `IUnknown`die lokal als gespeichert sind. Sie werfen `IUnknown` jede Schnittstelle in den echten Schnittstellentyp um und rufen sie dann durch. Sie müssen die Schnittstelle nicht zuerst abfragen.

Bevor Sie `IUnknown` die Schnittstelle verwenden, sollten Sie überprüfen, ob es sich nicht um NULL handelt.

## <a name="ccomdynamicunkarrayclear"></a><a name="clear"></a>CComDynamicUnkArray::clear

Leert das Array.

```cpp
void clear();
```

## <a name="ccomdynamicunkarrayccomdynamicunkarray"></a><a name="ccomdynamicunkarray"></a>CComDynamicUnkArray::CComDynamicUnkArray

Der Konstruktor.

```
CComDynamicUnkArray();
```

### <a name="remarks"></a>Bemerkungen

Legt die Auflistungsgröße auf Null fest und initialisiert die Werte auf NULL. Der Destruktor befreit die Sammlung, falls erforderlich.

## <a name="ccomdynamicunkarrayccomdynamicunkarray"></a><a name="dtor"></a>CComDynamicUnkArray::'CComDynamicUnkArray

Der Destruktor.

```
~CComDynamicUnkArray();
```

### <a name="remarks"></a>Bemerkungen

Gibt Ressourcen frei, die vom Klassenkonstruktor zugewiesen wurden.

## <a name="ccomdynamicunkarrayend"></a><a name="end"></a>CComDynamicUnkArray::end

Gibt einen Zeiger auf einen `IUnknown` Zeiger hinter dem letzten Zeiger in der Auflistung zurück.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `IUnknown` einen Schnittstellenzeiger.

## <a name="ccomdynamicunkarraygetat"></a><a name="getat"></a>CComDynamicUnkArray::Getat

Entfernt das Element am angegebenen Index.

```
IUnknown* GetAt(int nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der Index des abzurufenden Elements.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine [IUnknown-Schnittstelle.](/windows/win32/api/unknwn/nn-unknwn-iunknown)

## <a name="ccomdynamicunkarraygetcookie"></a><a name="getcookie"></a>CComDynamicUnkArray::GetCookie

Rufen Sie diese Methode auf, `IUnknown` um das Cookie abzurufen, das einem bestimmten Zeiger zugeordnet ist.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Parameter

*ppFind*<br/>
Der `IUnknown` Zeiger, für den das zugehörige Cookie erforderlich ist.

### <a name="return-value"></a>Rückgabewert

Gibt das dem `IUnknown` Zeiger zugeordnete Cookie oder `IUnknown` Null zurück, wenn kein übereinstimmender Zeiger gefunden wird.

### <a name="remarks"></a>Bemerkungen

Wenn mehr als eine Instanz `IUnknown` desselben Zeigers vorhanden ist, gibt diese Funktion das Cookie für die erste zurück.

## <a name="ccomdynamicunkarraygetsize"></a><a name="getsize"></a>CComDynamicUnkArray::GetSize

Gibt die Länge eines Arrays zurück.

```
int GetSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Länge des Arrays.

## <a name="ccomdynamicunkarraygetunknown"></a><a name="getunknown"></a>CComDynamicUnkArray::GetUnknown

Rufen Sie diese `IUnknown` Methode auf, um den Zeiger abzurufen, der einem bestimmten Cookie zugeordnet ist.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Parameter

*dwCookie*<br/>
Das Cookie, für `IUnknown` das der zugehörige Zeiger erforderlich ist.

### <a name="return-value"></a>Rückgabewert

Gibt `IUnknown` den Zeiger oder NULL zurück, wenn kein übereinstimmendes Cookie gefunden wurde.

## <a name="ccomdynamicunkarrayremove"></a><a name="remove"></a>CComDynamicUnkArray::Entfernen

Rufen Sie diese `IUnknown` Methode auf, um einen Zeiger aus dem Array zu entfernen.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Parameter

*dwCookie*<br/>
Das Cookie, das `IUnknown` auf den Zeiger verweist, der aus dem Array entfernt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn der Zeiger entfernt wird. andernfalls FALSE.

## <a name="see-also"></a>Weitere Informationen

[CComUnkArray-Klasse](../../atl/reference/ccomunkarray-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
