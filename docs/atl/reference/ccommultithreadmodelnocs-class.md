---
title: CComMultiThreadModelNoCS-Klasse
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
ms.openlocfilehash: 4d41ffcfccbd7ef65ed86df79bffec1209a88cd3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327653"
---
# <a name="ccommultithreadmodelnocs-class"></a>CComMultiThreadModelNoCS-Klasse

`CComMultiThreadModelNoCS`bietet threadsichere Methoden zum Erhöhen und Dekrementieren des Werts einer Variablen, ohne kritische Abschnittssperr- oder Entsperrfunktionen.

## <a name="syntax"></a>Syntax

```
class CComMultiThreadModelNoCS
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|Referenzen Klasse [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComMultiThreadModelNoCS::CriticalSection](#criticalsection)|Referenzklasse `CComFakeCriticalSection`.|
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|Referenzklasse `CComMultiThreadModelNoCS`.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComMultiThreadModelNoCS::DEkrement](#decrement)|(Statisch) Dekrementiert den Wert der angegebenen Variablen auf threadsichere Weise.|
|[CComMultiThreadModelNoCS::Inkrement](#increment)|(Statisch) Erhöht den Wert der angegebenen Variablen auf threadsichere Weise.|

## <a name="remarks"></a>Bemerkungen

`CComMultiThreadModelNoCS`[cComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) ähnelt, da es threadsichere Methoden zum Inkrementieren und Dekrementieren einer Variablen bereitstellt. Wenn Sie jedoch auf eine `CComMultiThreadModelNoCS`kritische Abschnittsklasse durch verweisen, werden Methoden wie `Lock` und `Unlock` werden nichts tun.

In der `CComMultiThreadModelNoCS` Regel `ThreadModelNoCS` verwenden Sie den **Typedef-Namen.** Dieser **typedef** ist `CComMultiThreadModelNoCS` `CComMultiThreadModel`in , und [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)definiert.

> [!NOTE]
> Die globalen **typedef-Namen** [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) und [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel) verweisen nicht auf `CComMultiThreadModelNoCS`.

Zusätzlich zu `ThreadModelNoCS` `CComMultiThreadModelNoCS` definiert `AutoCriticalSection` und `CriticalSection`. Diese beiden letztgenannten **typedef-Namen** verweisen auf [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), das leere Methoden bereitstellt, die mit dem Abrufen und Freigeben eines kritischen Abschnitts verknüpft sind.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="ccommultithreadmodelnocsautocriticalsection"></a><a name="autocriticalsection"></a>CComMultiThreadModelNoCS::AutoCriticalSection

Bei `CComMultiThreadModelNoCS`Verwendung verweist der `AutoCriticalSection` **typedef-Name** auf die Klasse [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Bemerkungen

Da `CComFakeCriticalSection` kein kritischer Abschnitt vorhanden ist, tun seine Methoden nichts.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) und [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) enthalten `AutoCriticalSection`auch Definitionen für . Die folgende Tabelle zeigt die Beziehung zwischen der Threadingmodellklasse `AutoCriticalSection`und der kritischen Schnittklasse, auf die verwiesen wird:

|Klasse definiert in|Klasse referenziert|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Zusätzlich zu `AutoCriticalSection`können Sie den **typedef-Namen** [CriticalSection](#criticalsection)verwenden. Sie sollten `AutoCriticalSection` nicht in globalen Objekten oder statischen Klassenmembern angeben, wenn Sie den CRT-Startcode entfernen möchten.

### <a name="example"></a>Beispiel

Siehe [CcomMultithreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccommultithreadmodelnocscriticalsection"></a><a name="criticalsection"></a>CComMultiThreadModelNoCS::CriticalSection

Bei `CComMultiThreadModelNoCS`Verwendung verweist der `CriticalSection` **typedef-Name** auf die Klasse [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Bemerkungen

Da `CComFakeCriticalSection` kein kritischer Abschnitt vorhanden ist, tun seine Methoden nichts.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) und [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) enthalten `CriticalSection`auch Definitionen für . Die folgende Tabelle zeigt die Beziehung zwischen der Threadingmodellklasse `CriticalSection`und der kritischen Schnittklasse, auf die verwiesen wird:

|Klasse definiert in|Klasse referenziert|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Zusätzlich zu `CriticalSection`können Sie den **typedef-Namen** `AutoCriticalSection`verwenden. Sie sollten `AutoCriticalSection` nicht in globalen Objekten oder statischen Klassenmembern angeben, wenn Sie den CRT-Startcode entfernen möchten.

### <a name="example"></a>Beispiel

Siehe [CcomMultithreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccommultithreadmodelnocsdecrement"></a><a name="decrement"></a>CComMultiThreadModelNoCS::DEkrement

Diese statische Funktion ruft die Win32-Funktion [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement)auf, die den Wert der Variablen, auf die *p*zeigt, dekrementiert.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
[in] Zeiger auf die zu dekrementierte Variable.

### <a name="return-value"></a>Rückgabewert

Wenn das Ergebnis der Dekrementierung `Decrement` 0 ist, gibt er 0 zurück. Wenn das Ergebnis der Dekrementierung ungleich Null ist, ist der Rückgabewert ebenfalls ungleich Null, entspricht jedoch möglicherweise nicht dem Ergebnis der Dekrementierung.

### <a name="remarks"></a>Bemerkungen

**InterlockedDecrement** verhindert, dass mehrere Threads gleichzeitig diese Variable verwenden.

## <a name="ccommultithreadmodelnocsincrement"></a><a name="increment"></a>CComMultiThreadModelNoCS::Inkrement

Diese statische Funktion ruft die Win32-Funktion [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement)auf, die den Wert der Variablen, auf die *p*zeigt, erhöht.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
[in] Zeiger auf die zu erhöhende Variable.

### <a name="return-value"></a>Rückgabewert

Wenn das Ergebnis des Inkrements 0 ist, gibt **Increment** 0 zurück. Wenn das Ergebnis des Inkrements ungleich Null ist, ist der Rückgabewert ebenfalls ungleich Null, entspricht jedoch möglicherweise nicht dem Ergebnis des Inkrements.

### <a name="remarks"></a>Bemerkungen

**InterlockedIncrement** verhindert, dass mehrere Threads gleichzeitig diese Variable verwenden.

## <a name="ccommultithreadmodelnocsthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComMultiThreadModelNoCS::ThreadModelNoCS

Bei `CComMultiThreadModelNoCS`Verwendung verweist der `ThreadModelNoCS` `CComMultiThreadModelNoCS` **typedef-Name** einfach auf .

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Bemerkungen

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) und [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) enthalten `ThreadModelNoCS`auch Definitionen für . Die folgende Tabelle zeigt die Beziehung zwischen der Threadingmodellklasse und der Klasse, auf die verwiesen wird: `ThreadModelNoCS`

|Klasse definiert in|Klasse referenziert|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

Beachten Sie, `ThreadModelNoCS` dass `CComMultiThreadModelNoCS` die Definition `CComMultiThreadModel` `CComSingleThreadModel`von in Symmetrie mit und bietet. Angenommen, der Beispielcode `CComMultiThreadModel::AutoCriticalSection` in deklariert den folgenden **typdef:**

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

Unabhängig von der `ThreadModel` für (z. B.) `CComMultiThreadModelNoCS` `_ThreadModel` angegebenen Klasse wird entsprechend aufgelöst.

### <a name="example"></a>Beispiel

Siehe [CcomMultithreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
