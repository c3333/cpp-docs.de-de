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
ms.openlocfilehash: 05ef787764045ec7e17f5cdfdb0d4611cb2ac900
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229973"
---
# <a name="ccomsinglethreadmodel-class"></a>CComSingleThreadModel-Klasse

Diese Klasse stellt Methoden zum Inkrementieren und Dekrementieren des Werts einer Variablen bereit.

## <a name="syntax"></a>Syntax

```
class CComSingleThreadModel
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComSingleThreadModel:: autocriticalsection](#autocriticalsection)|Verweist auf die Klasse [ccomfakecriticalsection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComSingleThreadModel:: CriticalSection](#criticalsection)|References-Klasse `CComFakeCriticalSection` .|
|[CComSingleThreadModel:: threadmodelnocs](#threadmodelnocs)|Verweise `CComSingleThreadModel` .|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CComSingleThreadModel::D ecrement](#decrement)|Dekremente den Wert der angegebenen Variablen. Diese Implementierung ist nicht Thread sicher.|
|[CComSingleThreadModel:: Increment](#increment)|Erhöht den Wert der angegebenen Variablen. Diese Implementierung ist nicht Thread sicher.|

## <a name="remarks"></a>Bemerkungen

`CComSingleThreadModel`stellt Methoden zum Inkrementieren und Dekrementieren des Werts einer Variablen bereit. Anders als [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) und [ccommultithreadmodelnocs](../../atl/reference/ccommultithreadmodelnocs-class.md)sind diese Methoden nicht Thread sicher.

In der Regel verwenden Sie `CComSingleThreadModel` einen von zwei **`typedef`** Namen, entweder [ccomobjectthreadmodel](atl-typedefs.md#ccomobjectthreadmodel) oder [ccomglobalsthread Model](atl-typedefs.md#ccomglobalsthreadmodel). Die Klasse, auf die jeweils verwiesen wird **`typedef`** , hängt vom verwendeten Threading Modell ab, wie in der folgenden Tabelle dargestellt:

|Typedef|Einzelnes Threading Modell|Apartment Threading Modell|Kostenloses Threading Modell|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|E|E|M|
|`CComGlobalsThreadModel`|E|M|M|

S = `CComSingleThreadModel` ; M =`CComMultiThreadModel`

`CComSingleThreadModel`selbst definiert drei **`typedef`** Namen. `ThreadModelNoCS`Verweise `CComSingleThreadModel` . `AutoCriticalSection`und `CriticalSection` die Verweis Klasse [ccomfakecriticalsection](../../atl/reference/ccomfakecriticalsection-class.md), die leere Methoden bereitstellt, die dem Abrufen und Freigeben des Besitzes eines kritischen Abschnitts zugeordnet sind.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="ccomsinglethreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CComSingleThreadModel:: autocriticalsection

Wenn verwendet `CComSingleThreadModel` wird, **`typedef`** verweist der Name auf die `AutoCriticalSection` Klasse [ccomfakecriticalsection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Bemerkungen

Da keinen `CComFakeCriticalSection` kritischen Abschnitt bereitstellt, machen seine Methoden nichts.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) und [ccommultithreadmodelnocs](../../atl/reference/ccommultithreadmodelnocs-class.md) enthalten Definitionen für `AutoCriticalSection` . In der folgenden Tabelle wird die Beziehung zwischen der Threading Modell Klasse und der Critical-Abschnitts Klasse gezeigt, auf die von verwiesen wird `AutoCriticalSection` :

|In definierte Klasse|Referenzierte Klasse|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Zusätzlich zu `AutoCriticalSection` können Sie den **`typedef`** Namen [CriticalSection](#criticalsection)verwenden. Sie sollten nicht `AutoCriticalSection` in globalen Objekten oder statischen Klassenmembern angeben, wenn Sie den CRT-Startcode entfernen möchten.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [CComMultiThreadModel:: autocriticalsection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccomsinglethreadmodelcriticalsection"></a><a name="criticalsection"></a>CComSingleThreadModel:: CriticalSection

Wenn verwendet `CComSingleThreadModel` wird, **`typedef`** verweist der Name auf die `CriticalSection` Klasse [ccomfakecriticalsection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Bemerkungen

Da keinen `CComFakeCriticalSection` kritischen Abschnitt bereitstellt, machen seine Methoden nichts.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) und [ccommultithreadmodelnocs](../../atl/reference/ccommultithreadmodelnocs-class.md) enthalten Definitionen für `CriticalSection` . In der folgenden Tabelle wird die Beziehung zwischen der Threading Modell Klasse und der Critical-Abschnitts Klasse gezeigt, auf die von verwiesen wird `CriticalSection` :

|In definierte Klasse|Referenzierte Klasse|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Zusätzlich zu `CriticalSection` können Sie den **`typedef`** Namen [autocriticalsection](#autocriticalsection)verwenden. Sie sollten nicht `AutoCriticalSection` in globalen Objekten oder statischen Klassenmembern angeben, wenn Sie den CRT-Startcode entfernen möchten.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [CComMultiThreadModel:: autocriticalsection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccomsinglethreadmodeldecrement"></a><a name="decrement"></a>CComSingleThreadModel::D ecrement

Diese statische Funktion Dekremente den Wert der Variablen, auf die von *p*verwiesen wird.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parameter

*cker*<br/>
in Ein Zeiger auf die Variable, die dekrementiert werden soll.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis der Dekrement.

## <a name="ccomsinglethreadmodelincrement"></a><a name="increment"></a>CComSingleThreadModel:: Increment

Diese statische Funktion erhöht den Wert der Variablen, auf die von *p*verwiesen wird.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parameter

*cker*<br/>
in Ein Zeiger auf die Variable, die inkrementiert werden soll.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des Inkrements.

## <a name="ccomsinglethreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComSingleThreadModel:: threadmodelnocs

Wenn Sie verwenden `CComSingleThreadModel` , **`typedef`** verweist der Name `ThreadModelNoCS` einfach auf `CComSingleThreadModel` .

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>Bemerkungen

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) und [ccommultithreadmodelnocs](../../atl/reference/ccommultithreadmodelnocs-class.md) enthalten Definitionen für `ThreadModelNoCS` . In der folgenden Tabelle wird die Beziehung zwischen der Thread Modell Klasse und der-Klasse, auf die von verwiesen wird, gezeigt `ThreadModelNoCS` :

|In definierte Klasse|Referenzierte Klasse|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [CComMultiThreadModel:: autocriticalsection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Weitere Informationen

[Klassenübersicht](../../atl/atl-class-overview.md)
