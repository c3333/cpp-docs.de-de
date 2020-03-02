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
ms.openlocfilehash: 9b111e06ba475a5077ba36b2235e8bd530302189
ms.sourcegitcommit: ab8d7b47b63b62892a1256a09b1324a9a136eccf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2020
ms.locfileid: "78215462"
---
# <a name="ccomsinglethreadmodel-class"></a>CComSingleThreadModel-Klasse

Diese Klasse stellt Methoden zum Inkrementieren und Dekrementieren des Werts einer Variablen bereit.

## <a name="syntax"></a>Syntax

```
class CComSingleThreadModel
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|Beschreibung|
|----------|-----------------|
|[CComSingleThreadModel:: autocriticalsection](#autocriticalsection)|Verweist auf die Klasse [ccomfakecriticalsection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComSingleThreadModel:: CriticalSection](#criticalsection)|Verweist auf die Klasse `CComFakeCriticalSection`.|
|[CComSingleThreadModel:: threadmodelnocs](#threadmodelnocs)|Verweist auf `CComSingleThreadModel`.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CComSingleThreadModel::D ecrement](#decrement)|Dekremente den Wert der angegebenen Variablen. Diese Implementierung ist nicht Thread sicher.|
|[CComSingleThreadModel:: Increment](#increment)|Erhöht den Wert der angegebenen Variablen. Diese Implementierung ist nicht Thread sicher.|

## <a name="remarks"></a>Hinweise

`CComSingleThreadModel` stellt Methoden zum Inkrementieren und Dekrementieren des Werts einer Variablen bereit. Anders als [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) und [ccommultithreadmodelnocs](../../atl/reference/ccommultithreadmodelnocs-class.md)sind diese Methoden nicht Thread sicher.

In der Regel verwenden Sie `CComSingleThreadModel` über einen von zwei **typedef** -Namen (entweder [ccomobjectthreadmodel](atl-typedefs.md#ccomobjectthreadmodel) oder [ccomglobalsthread Model](atl-typedefs.md#ccomglobalsthreadmodel)). Die Klasse, auf die jede **typedef** verweist, hängt vom verwendeten Threading Modell ab, wie in der folgenden Tabelle gezeigt:

|Typedef|Einzelnes Threading Modell|Apartment Threading Modell|Kostenloses Threading Modell|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M = `CComMultiThreadModel`

`CComSingleThreadModel` selbst definiert drei **typedef** -Namen. `ThreadModelNoCS` Verweise `CComSingleThreadModel`. `AutoCriticalSection` und `CriticalSection` Verweis Klasse [ccomfakecriticalsection](../../atl/reference/ccomfakecriticalsection-class.md), die leere Methoden bereitstellt, die dem Abrufen und Freigeben des Besitzes eines kritischen Abschnitts zugeordnet sind.

## <a name="requirements"></a>Voraussetzungen

**Header:** atlbase. h

##  <a name="autocriticalsection"></a>CComSingleThreadModel:: autocriticalsection

Wenn Sie `CComSingleThreadModel`verwenden, ist der **typedef** -Name `AutoCriticalSection` Verweis Klasse [ccomfakecriticalsection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Hinweise

Da `CComFakeCriticalSection` keinen kritischen Abschnitt bereitstellt, machen seine Methoden nichts.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) und [ccommultithreadmodelnocs](../../atl/reference/ccommultithreadmodelnocs-class.md) enthalten Definitionen für `AutoCriticalSection`. In der folgenden Tabelle wird die Beziehung zwischen der Threading Modell Klasse und der Critical-Abschnitts Klasse gezeigt, auf die von `AutoCriticalSection`verwiesen wird:

|In definierte Klasse|Referenzierte Klasse|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Zusätzlich zu `AutoCriticalSection`können Sie den **typedef** -Namen [CriticalSection](#criticalsection)verwenden. Sie sollten `AutoCriticalSection` nicht in globalen Objekten oder statischen Klassenmembern angeben, wenn Sie den CRT-Startcode entfernen möchten.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [CComMultiThreadModel:: autocriticalsection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="criticalsection"></a>CComSingleThreadModel:: CriticalSection

Wenn Sie `CComSingleThreadModel`verwenden, ist der **typedef** -Name `CriticalSection` Verweis Klasse [ccomfakecriticalsection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Hinweise

Da `CComFakeCriticalSection` keinen kritischen Abschnitt bereitstellt, machen seine Methoden nichts.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) und [ccommultithreadmodelnocs](../../atl/reference/ccommultithreadmodelnocs-class.md) enthalten Definitionen für `CriticalSection`. In der folgenden Tabelle wird die Beziehung zwischen der Threading Modell Klasse und der Critical-Abschnitts Klasse gezeigt, auf die von `CriticalSection`verwiesen wird:

|In definierte Klasse|Referenzierte Klasse|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Zusätzlich zu `CriticalSection`können Sie den **typedef** -Namen [autocriticalsection](#autocriticalsection)verwenden. Sie sollten `AutoCriticalSection` nicht in globalen Objekten oder statischen Klassenmembern angeben, wenn Sie den CRT-Startcode entfernen möchten.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [CComMultiThreadModel:: autocriticalsection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="decrement"></a>CComSingleThreadModel::D ecrement

Diese statische Funktion Dekremente den Wert der Variablen, auf die von *p*verwiesen wird.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parameter

*p*<br/>
in Ein Zeiger auf die Variable, die dekrementiert werden soll.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis der Dekrement.

##  <a name="increment"></a>CComSingleThreadModel:: Increment

Diese statische Funktion erhöht den Wert der Variablen, auf die von *p*verwiesen wird.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parameter

*p*<br/>
in Ein Zeiger auf die Variable, die inkrementiert werden soll.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des Inkrements.

##  <a name="threadmodelnocs"></a>CComSingleThreadModel:: threadmodelnocs

Wenn Sie `CComSingleThreadModel`verwenden, verweist der **typedef** -Name `ThreadModelNoCS` einfach auf `CComSingleThreadModel`.

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>Hinweise

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) und [ccommultithreadmodelnocs](../../atl/reference/ccommultithreadmodelnocs-class.md) enthalten Definitionen für `ThreadModelNoCS`. In der folgenden Tabelle wird die Beziehung zwischen der Threading Modell Klasse und der-Klasse, auf die von `ThreadModelNoCS`verwiesen wird, veranschaulicht:

|In definierte Klasse|Referenzierte Klasse|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [CComMultiThreadModel:: autocriticalsection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Siehe auch

[Klassen Übersicht](../../atl/atl-class-overview.md)
