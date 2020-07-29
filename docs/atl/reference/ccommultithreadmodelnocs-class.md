---
title: Ccommultithreadmodelnocs-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::CriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::Decrement
- ATLBASE/ATL::CComMultiThreadModelNoCS::Increment
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModelNoCS class
- threading [ATL]
ms.assetid: 2b3f7a45-fd72-452c-aaf3-ccdaa621c821
ms.openlocfilehash: beb5cd1e13de1a10546f28d4a7eb98e45b6e9af1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224265"
---
# <a name="ccommultithreadmodelnocs-class"></a>Ccommultithreadmodelnocs-Klasse

`CComMultiThreadModelNoCS`stellt Thread sichere Methoden zum Inkrementieren und Dekrementieren des Werts einer Variablen bereit, ohne dass eine kritische Abschnitts Sperr-oder entsperrungs Funktionalität besteht.

## <a name="syntax"></a>Syntax

```
class CComMultiThreadModelNoCS
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|Beschreibung|
|----------|-----------------|
|[Ccommultithreadmodelnocs:: autocriticalsection](#autocriticalsection)|Verweist auf die Klasse [ccomfakecriticalsection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[Ccommultithreadmodelnocs:: CriticalSection](#criticalsection)|References-Klasse `CComFakeCriticalSection` .|
|[Ccommultithreadmodelnocs:: threadmodelnocs](#threadmodelnocs)|References-Klasse `CComMultiThreadModelNoCS` .|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[Ccommultithreadmodelnocs::D ecrement](#decrement)|Kum Dekremente den Wert der angegebenen Variablen auf Thread sichere Weise.|
|[Ccommultithreadmodelnocs:: Increment](#increment)|Kum Erhöht den Wert der angegebenen Variablen auf Thread sichere Weise.|

## <a name="remarks"></a>Bemerkungen

`CComMultiThreadModelNoCS`ähnelt [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) , da es Thread sichere Methoden zum Inkrementieren und Dekrementieren einer Variablen bereitstellt. Wenn Sie jedoch auf eine kritische Abschnitts Klasse durch verweisen `CComMultiThreadModelNoCS` , werden Methoden wie `Lock` und `Unlock` keine Aktion ausführen.

In der Regel verwenden Sie `CComMultiThreadModelNoCS` den `ThreadModelNoCS` **`typedef`** Namen. Dies **`typedef`** wird in `CComMultiThreadModelNoCS` , `CComMultiThreadModel` und [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)definiert.

> [!NOTE]
> Die globalen **`typedef`** Namen " [ccomobjectthreadmodel](atl-typedefs.md#ccomobjectthreadmodel) " und " [ccomglobalsthlock Model](atl-typedefs.md#ccomglobalsthreadmodel) " verweisen nicht `CComMultiThreadModelNoCS` .

Zusätzlich zu `ThreadModelNoCS` `CComMultiThreadModelNoCS` definiert `AutoCriticalSection` und `CriticalSection` . Diese beiden letzteren **`typedef`** Namen verweisen auf [ccomfakecriticalsection](../../atl/reference/ccomfakecriticalsection-class.md), das leere Methoden bereitstellt, die mit dem Abrufen und Freigeben eines kritischen Abschnitts verknüpft sind.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="ccommultithreadmodelnocsautocriticalsection"></a><a name="autocriticalsection"></a>Ccommultithreadmodelnocs:: autocriticalsection

Wenn verwendet `CComMultiThreadModelNoCS` wird, **`typedef`** verweist der Name auf die `AutoCriticalSection` Klasse [ccomfakecriticalsection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Bemerkungen

Da keinen `CComFakeCriticalSection` kritischen Abschnitt bereitstellt, machen seine Methoden nichts.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) und [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) enthalten auch Definitionen für `AutoCriticalSection` . In der folgenden Tabelle wird die Beziehung zwischen der Threading Modell Klasse und der Critical-Abschnitts Klasse gezeigt, auf die von verwiesen wird `AutoCriticalSection` :

|In definierte Klasse|Referenzierte Klasse|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Zusätzlich zu `AutoCriticalSection` können Sie den **`typedef`** Namen [CriticalSection](#criticalsection)verwenden. Sie sollten nicht `AutoCriticalSection` in globalen Objekten oder statischen Klassenmembern angeben, wenn Sie den CRT-Startcode entfernen möchten.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [CComMultiThreadModel:: autocriticalsection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccommultithreadmodelnocscriticalsection"></a><a name="criticalsection"></a>Ccommultithreadmodelnocs:: CriticalSection

Wenn verwendet `CComMultiThreadModelNoCS` wird, **`typedef`** verweist der Name auf die `CriticalSection` Klasse [ccomfakecriticalsection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Bemerkungen

Da keinen `CComFakeCriticalSection` kritischen Abschnitt bereitstellt, machen seine Methoden nichts.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) und [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) enthalten auch Definitionen für `CriticalSection` . In der folgenden Tabelle wird die Beziehung zwischen der Threading Modell Klasse und der Critical-Abschnitts Klasse gezeigt, auf die von verwiesen wird `CriticalSection` :

|In definierte Klasse|Referenzierte Klasse|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Zusätzlich zu `CriticalSection` können Sie den **`typedef`** Namen verwenden `AutoCriticalSection` . Sie sollten nicht `AutoCriticalSection` in globalen Objekten oder statischen Klassenmembern angeben, wenn Sie den CRT-Startcode entfernen möchten.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [CComMultiThreadModel:: autocriticalsection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccommultithreadmodelnocsdecrement"></a><a name="decrement"></a>Ccommultithreadmodelnocs::D ecrement

Diese statische Funktion Ruft die Win32-Funktion " [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement)" auf, die den Wert der Variablen Dekremente, auf die *p*zeigt.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parameter

*cker*<br/>
in Ein Zeiger auf die Variable, die dekrementiert werden soll.

### <a name="return-value"></a>Rückgabewert

Wenn das Ergebnis des dekrements 0 ist, wird `Decrement` 0 zurückgegeben. Wenn das Ergebnis des dekrements ungleich 0 (null) ist, ist der Rückgabewert auch ungleich 0 (null), ist aber möglicherweise nicht mit dem Ergebnis des dekrements identisch.

### <a name="remarks"></a>Bemerkungen

Mit **InterlockedDecrement** wird verhindert, dass mehr als ein Thread gleichzeitig diese Variable verwendet.

## <a name="ccommultithreadmodelnocsincrement"></a><a name="increment"></a>Ccommultithreadmodelnocs:: Increment

Diese statische Funktion Ruft die Win32-Funktion [interlockedinkrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement)auf, mit der der Wert der Variablen erhöht wird, auf die von *p*verwiesen wird.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parameter

*cker*<br/>
in Ein Zeiger auf die Variable, die inkrementiert werden soll.

### <a name="return-value"></a>Rückgabewert

Wenn das Ergebnis des Inkrements 0 ist, gibt **Inkrement** 0 zurück. Wenn das Ergebnis des Inkrements ungleich 0 (null) ist, ist der Rückgabewert auch ungleich 0 (null), kann aber nicht dem Ergebnis des Inkrements entsprechen.

### <a name="remarks"></a>Bemerkungen

Mit **interlockedinkrement** wird verhindert, dass mehr als ein Thread gleichzeitig diese Variable verwendet.

## <a name="ccommultithreadmodelnocsthreadmodelnocs"></a><a name="threadmodelnocs"></a>Ccommultithreadmodelnocs:: threadmodelnocs

Wenn Sie verwenden `CComMultiThreadModelNoCS` , **`typedef`** verweist der Name `ThreadModelNoCS` einfach auf `CComMultiThreadModelNoCS` .

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Bemerkungen

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) und [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) enthalten auch Definitionen für `ThreadModelNoCS` . In der folgenden Tabelle wird die Beziehung zwischen der Thread Modell Klasse und der-Klasse, auf die von verwiesen wird, gezeigt `ThreadModelNoCS` :

|In definierte Klasse|Referenzierte Klasse|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

Beachten Sie, dass die Definition von `ThreadModelNoCS` in die `CComMultiThreadModelNoCS` Symmetrie mit und bereitstellt `CComMultiThreadModel` `CComSingleThreadModel` . Angenommen, der Beispielcode in hat `CComMultiThreadModel::AutoCriticalSection` Folgendes deklariert **`typedef`** :

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

Unabhängig von der Klasse, die für angegeben `ThreadModel` wurde (z `CComMultiThreadModelNoCS` . b.), wird `_ThreadModel` entsprechend aufgelöst.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [CComMultiThreadModel:: autocriticalsection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
