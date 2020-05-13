---
title: CComUnkArray-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComUnkArray
- ATLCOM/ATL::CComUnkArray
- ATLCOM/ATL::CComUnkArray::CComUnkArray
- ATLCOM/ATL::CComUnkArray::Add
- ATLCOM/ATL::CComUnkArray::begin
- ATLCOM/ATL::CComUnkArray::end
- ATLCOM/ATL::CComUnkArray::GetCookie
- ATLCOM/ATL::CComUnkArray::GetUnknown
- ATLCOM/ATL::CComUnkArray::Remove
helpviewer_keywords:
- connection points [C++], managing
- CComUnkArray class
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
ms.openlocfilehash: c1d2f0296394d3979ef4f152e3f902c89adf5b45
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327306"
---
# <a name="ccomunkarray-class"></a>CComUnkArray-Klasse

Diese Klasse `IUnknown` speichert Zeiger und ist für die Verwendung als Parameter für die [IConnectionPointImpl-Vorlagenklasse](../../atl/reference/iconnectionpointimpl-class.md) konzipiert.

## <a name="syntax"></a>Syntax

```
template<unsigned int nMaxSize>
class CComUnkArray
```

#### <a name="parameters"></a>Parameter

*nMaxSize*<br/>
Die maximale `IUnknown` Anzahl von Zeigern, die im statischen Array gehalten werden können.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComUnkArray::CComUnkArray](#ccomunkarray)|Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComUnkArray::Hinzufügen](#add)|Rufen Sie diese `IUnknown` Methode auf, um dem Array einen Zeiger hinzuzufügen.|
|[CComUnkArray::begin](#begin)|Gibt einen Zeiger auf `IUnknown` den ersten Zeiger in der Auflistung zurück.|
|[CComUnkArray::ende](#end)|Gibt einen Zeiger auf einen `IUnknown` Zeiger hinter dem letzten Zeiger in der Auflistung zurück.|
|[CComUnkArray::GetCookie](#getcookie)|Rufen Sie diese Methode auf, `IUnknown` um das Cookie abzurufen, das einem bestimmten Zeiger zugeordnet ist.|
|[CComUnkArray::GetUnknown](#getunknown)|Rufen Sie diese `IUnknown` Methode auf, um den Zeiger abzurufen, der einem bestimmten Cookie zugeordnet ist.|
|[CComUnkArray::Entfernen](#remove)|Rufen Sie diese `IUnknown` Methode auf, um einen Zeiger aus dem Array zu entfernen.|

## <a name="remarks"></a>Bemerkungen

`CComUnkArray`enthält eine feste `IUnknown` Anzahl von Zeigern, jeweils eine Schnittstelle auf einem Verbindungspunkt. `CComUnkArray`kann als Parameter für die [IConnectionPointImpl-Vorlagenklasse](../../atl/reference/iconnectionpointimpl-class.md) verwendet werden. `CComUnkArray<1>`ist eine Vorlagenspezialisierung, die `CComUnkArray` für einen Verbindungspunkt optimiert wurde.

Die `CComUnkArray` Methoden [begin](#begin) and [end](#end) können verwendet werden, um alle Verbindungspunkte zu durchlaufen (z. B. wenn ein Ereignis ausgelöst wird).

Weitere Informationen zum Automatisieren der Erstellung von Verbindungspunktproxys finden Sie unter [Hinzufügen von Verbindungspunkten zu einem Objekt.](../../atl/adding-connection-points-to-an-object.md)

> [!NOTE]
> **Hinweis** Die Klasse [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md) wird vom Assistenten zum Hinzufügen von **Klassen** verwendet, wenn ein Steuerelement mit Verbindungspunkten erstellt wird. Wenn Sie die Anzahl der Verbindungspunkte manuell angeben `CComDynamicUnkArray` möchten, ändern Sie den Verweis von `CComUnkArray<` *n* `>`, wobei *n* die Anzahl der erforderlichen Verbindungspunkte ist.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="ccomunkarrayadd"></a><a name="add"></a>CComUnkArray::Hinzufügen

Rufen Sie diese `IUnknown` Methode auf, um dem Array einen Zeiger hinzuzufügen.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Parameter

*Punk*<br/>
Rufen Sie diese `IUnknown` Methode auf, um dem Array einen Zeiger hinzuzufügen.

### <a name="return-value"></a>Rückgabewert

Gibt das Cookie zurück, das dem neu hinzugefügten Zeiger zugeordnet ist, oder 0, wenn das Array nicht groß genug ist, um den neuen Zeiger zu enthalten.

## <a name="ccomunkarraybegin"></a><a name="begin"></a>CComUnkArray::begin

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

## <a name="ccomunkarrayccomunkarray"></a><a name="ccomunkarray"></a>CComUnkArray::CComUnkArray

Der Konstruktor.

```
CComUnkArray();
```

### <a name="remarks"></a>Bemerkungen

Legt die Auflistung `nMaxSize` `IUnknown` für Zeiger fest und initialisiert die Zeiger auf NULL.

## <a name="ccomunkarrayend"></a><a name="end"></a>CComUnkArray::ende

Gibt einen Zeiger auf einen `IUnknown` Zeiger hinter dem letzten Zeiger in der Auflistung zurück.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `IUnknown` einen Schnittstellenzeiger.

### <a name="remarks"></a>Bemerkungen

Die `CComUnkArray` `begin` Methoden `end` und können verwendet werden, um alle Verbindungspunkte zu durchlaufen, z. B. wenn ein Ereignis ausgelöst wird.

[!code-cpp[NVC_ATL_COM#44](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]

## <a name="ccomunkarraygetcookie"></a><a name="getcookie"></a>CComUnkArray::GetCookie

Rufen Sie diese Methode auf, `IUnknown` um das Cookie abzurufen, das einem bestimmten Zeiger zugeordnet ist.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Parameter

*ppFind*<br/>
Der `IUnknown` Zeiger, für den das zugehörige Cookie erforderlich ist.

### <a name="return-value"></a>Rückgabewert

Gibt das dem `IUnknown` Zeiger zugeordnete Cookie oder `IUnknown` 0 zurück, wenn kein übereinstimmender Zeiger gefunden wird.

### <a name="remarks"></a>Bemerkungen

Wenn mehr als eine Instanz `IUnknown` desselben Zeigers vorhanden ist, gibt diese Funktion das Cookie für die erste zurück.

## <a name="ccomunkarraygetunknown"></a><a name="getunknown"></a>CComUnkArray::GetUnknown

Rufen Sie diese `IUnknown` Methode auf, um den Zeiger abzurufen, der einem bestimmten Cookie zugeordnet ist.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Parameter

*dwCookie*<br/>
Das Cookie, für `IUnknown` das der zugehörige Zeiger erforderlich ist.

### <a name="return-value"></a>Rückgabewert

Gibt `IUnknown` den Zeiger oder NULL zurück, wenn kein übereinstimmendes Cookie gefunden wurde.

## <a name="ccomunkarrayremove"></a><a name="remove"></a>CComUnkArray::Entfernen

Rufen Sie diese `IUnknown` Methode auf, um einen Zeiger aus dem Array zu entfernen.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Parameter

*dwCookie*<br/>
Das Cookie, das `IUnknown` auf den Zeiger verweist, der aus dem Array entfernt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn der Zeiger entfernt wird, andernfalls FALSE.

## <a name="see-also"></a>Siehe auch

[CComDynamicUnkArray-Klasse](../../atl/reference/ccomdynamicunkarray-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
