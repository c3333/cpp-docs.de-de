---
title: CComSingleThreadModel-Klasse
ms.date: 2/29/2020
f1_keywords:
- CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComSingleThreadModel::CriticalSection
- ATLBASE/ATL::CComSingleThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComSingleThreadModel::Decrement
- ATLBASE/ATL::CComSingleThreadModel::Increment
helpviewer_keywords:
- single-threaded applications
- CComSingleThreadModel class
- single-threaded applications, ATL
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
ms.openlocfilehash: 3d8169c999ba96049bc711033f7ba2ef53989663
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327334"
---
# <a name="ccomsinglethreadmodel-class"></a>CComSingleThreadModel-Klasse

Diese Klasse stellt Methoden zum Erhöhen und Dekrementieren des Werts einer Variablen bereit.

## <a name="syntax"></a>Syntax

```
class CComSingleThreadModel
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|Referenzen Klasse [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComSingleThreadModel::CriticalSection](#criticalsection)|Referenzklasse `CComFakeCriticalSection`.|
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|Referenzen `CComSingleThreadModel`.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComSingleThreadModel::DEkrementierung](#decrement)|Dekrementiert den Wert der angegebenen Variablen. Diese Implementierung ist nicht threadsicher.|
|[CComSingleThreadModel::Inkrement](#increment)|Inkrementiert den Wert der angegebenen Variablen. Diese Implementierung ist nicht threadsicher.|

## <a name="remarks"></a>Bemerkungen

`CComSingleThreadModel`bietet Methoden zum Erhöhen und Dekrementieren des Werts einer Variablen. Im Gegensatz zu [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) und [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)sind diese Methoden nicht threadsicher.

In der `CComSingleThreadModel` Regel verwenden Sie über einen von zwei **typedef-Namen,** entweder [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) oder [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel). Die Klasse, auf die von jedem **typedef** verwiesen wird, hängt vom verwendeten Threadingmodell ab, wie in der folgenden Tabelle dargestellt:

|Typedef|Single-Threading-Modell|Wohnung Threading Modell|Kostenloses Gewindemodell|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|E|E|M|
|`CComGlobalsThreadModel`|E|M|M|

S= `CComSingleThreadModel`; M=`CComMultiThreadModel`

`CComSingleThreadModel`definiert selbst drei **typedef-Namen.** `ThreadModelNoCS`Referenzen `CComSingleThreadModel`. `AutoCriticalSection`und `CriticalSection` referenzklasse [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), die leere Methoden bereitstellt, die mit dem Abrufen und Freigeben des Besitzes eines kritischen Abschnitts verknüpft sind.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="ccomsinglethreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CComSingleThreadModel::AutoCriticalSection

Bei `CComSingleThreadModel`Verwendung verweist der `AutoCriticalSection` **typedef-Name** auf die Klasse [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Bemerkungen

Da `CComFakeCriticalSection` kein kritischer Abschnitt vorhanden ist, tun seine Methoden nichts.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) und [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) enthalten `AutoCriticalSection`Definitionen für . Die folgende Tabelle zeigt die Beziehung zwischen der Threadingmodellklasse `AutoCriticalSection`und der kritischen Schnittklasse, auf die verwiesen wird:

|Klasse definiert in|Klasse referenziert|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Zusätzlich zu `AutoCriticalSection`können Sie den **typedef-Namen** [CriticalSection](#criticalsection)verwenden. Sie sollten `AutoCriticalSection` nicht in globalen Objekten oder statischen Klassenmembern angeben, wenn Sie den CRT-Startcode entfernen möchten.

### <a name="example"></a>Beispiel

Siehe [CcomMultithreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccomsinglethreadmodelcriticalsection"></a><a name="criticalsection"></a>CComSingleThreadModel::CriticalSection

Bei `CComSingleThreadModel`Verwendung verweist der `CriticalSection` **typedef-Name** auf die Klasse [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Bemerkungen

Da `CComFakeCriticalSection` kein kritischer Abschnitt vorhanden ist, tun seine Methoden nichts.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) und [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) enthalten `CriticalSection`Definitionen für . Die folgende Tabelle zeigt die Beziehung zwischen der Threadingmodellklasse `CriticalSection`und der kritischen Schnittklasse, auf die verwiesen wird:

|Klasse definiert in|Klasse referenziert|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Zusätzlich zu `CriticalSection`können Sie den **typedef-Namen** [AutoCriticalSection](#autocriticalsection)verwenden. Sie sollten `AutoCriticalSection` nicht in globalen Objekten oder statischen Klassenmembern angeben, wenn Sie den CRT-Startcode entfernen möchten.

### <a name="example"></a>Beispiel

Siehe [CcomMultithreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccomsinglethreadmodeldecrement"></a><a name="decrement"></a>CComSingleThreadModel::DEkrementierung

Diese statische Funktion dekrementiert den Wert der Variablen, auf die *p*zeigt.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
[in] Zeiger auf die zu dekrementierte Variable.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des Abbaus.

## <a name="ccomsinglethreadmodelincrement"></a><a name="increment"></a>CComSingleThreadModel::Inkrement

Diese statische Funktion erhöht den Wert der Variablen, auf die *p*zeigt.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
[in] Zeiger auf die zu erhöhende Variable.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des Inkrements.

## <a name="ccomsinglethreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComSingleThreadModel::ThreadModelNoCS

Bei `CComSingleThreadModel`Verwendung verweist der `ThreadModelNoCS` `CComSingleThreadModel` **typedef-Name** einfach auf .

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>Bemerkungen

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) und [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) enthalten `ThreadModelNoCS`Definitionen für . Die folgende Tabelle zeigt die Beziehung zwischen der Threadingmodellklasse und der Klasse, auf die verwiesen wird: `ThreadModelNoCS`

|Klasse definiert in|Klasse referenziert|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Beispiel

Siehe [CcomMultithreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
