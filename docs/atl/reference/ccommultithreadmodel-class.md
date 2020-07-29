---
title: CComMultiThreadModel-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModel::CriticalSection
- ATLBASE/ATL::CComMultiThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModel::Decrement
- ATLBASE/ATL::CComMultiThreadModel::Increment
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModel class
- threading [ATL]
ms.assetid: db8f1662-2f7a-44b3-b341-ffbfb6e422a3
ms.openlocfilehash: 38ed43e77492484b7c8d8cb06cad71e695d41c4a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224278"
---
# <a name="ccommultithreadmodel-class"></a>CComMultiThreadModel-Klasse

`CComMultiThreadModel`stellt Thread sichere Methoden zum Inkrementieren und Dekrementieren des Werts einer Variablen bereit.

## <a name="syntax"></a>Syntax

```
class CComMultiThreadModel
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|Beschreibung|
|----------|-----------------|
|[CComMultiThreadModel:: autocriticalsection](#autocriticalsection)|Verweist auf die Klasse [ccomautocriticalsection](../../atl/reference/ccomautocriticalsection-class.md).|
|[CComMultiThreadModel:: CriticalSection](#criticalsection)|References-Klasse [ccomcriticalsection](../../atl/reference/ccomcriticalsection-class.md).|
|[CComMultiThreadModel:: threadmodelnocs](#threadmodelnocs)|Verweist auf die Klasse [ccommultithreadmodelnocs](../../atl/reference/ccommultithreadmodelnocs-class.md).|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CComMultiThreadModel::D ecrement](#decrement)|Kum Dekremente den Wert der angegebenen Variablen auf Thread sichere Weise.|
|[CComMultiThreadModel:: Increment](#increment)|Kum Erhöht den Wert der angegebenen Variablen auf Thread sichere Weise.|

## <a name="remarks"></a>Bemerkungen

In der Regel verwenden Sie `CComMultiThreadModel` einen von zwei **`typedef`** Namen, entweder [ccomobjectthreadmodel] (ATL-Typedefs. MD # ccomobjectthreadmodel oder [ccomglobalsthlmodel] (ATL-Typedefs. MD # ccomglobalsthlmodel). Die Klasse, auf die jeweils verwiesen wird **`typedef`** , hängt vom verwendeten Threading Modell ab, wie in der folgenden Tabelle dargestellt:

|Typedef|Single Threading|Apartment Threading|Kostenloses Threading|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|E|E|M|
|`CComGlobalsThreadModel`|E|M|M|

S = `CComSingleThreadModel` ; M =`CComMultiThreadModel`

`CComMultiThreadModel`selbst definiert drei **`typedef`** Namen. `AutoCriticalSection`und `CriticalSection` Verweis Klassen, die Methoden zum Abrufen und Freigeben des Besitzes eines kritischen Abschnitts bereitstellen. `ThreadModelNoCS`References-Klasse [ccommultithreadmodelnocs (ccommultithreadmodelnocs-Class.MD).

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="ccommultithreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CComMultiThreadModel:: autocriticalsection

Bei Verwendung `CComMultiThreadModel` **`typedef`** `AutoCriticalSection` von verweist der Name auf die Klasse [ccomautocriticalsection](ccomautocriticalsection-class.md), die Methoden zum Abrufen und Freigeben des Besitzes eines kritischen Abschnitts Objekts bereitstellt.

```
typedef CComAutoCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Bemerkungen

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) und [ccommultithreadmodelnocs](ccommultithreadmodelnocs-class.md) enthalten auch Definitionen für `AutoCriticalSection` . In der folgenden Tabelle wird die Beziehung zwischen der Threading Modell Klasse und der Critical-Abschnitts Klasse gezeigt, auf die von verwiesen wird `AutoCriticalSection` :

|In definierte Klasse|Referenzierte Klasse|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Zusätzlich zu `AutoCriticalSection` können Sie den **`typedef`** Namen [CriticalSection](#criticalsection)verwenden. Sie sollten nicht `AutoCriticalSection` in globalen Objekten oder statischen Klassenmembern angeben, wenn Sie den CRT-Startcode entfernen möchten.

### <a name="example"></a>Beispiel

Der folgende Code wird nach [CComObjectRootEx](ccomobjectrootex-class.md)modelliert und veranschaulicht, wie `AutoCriticalSection` er in einer Threading Umgebung verwendet wird.

```cpp
template<class ThreadModel>
class CMyAutoCritClass
{
public:
   typedef ThreadModel _ThreadModel;
   typedef typename _ThreadModel::AutoCriticalSection _CritSec;

   CMyAutoCritClass() : m_dwRef(0) {}

   ULONG InternalAddRef()
   {
      return _ThreadModel::Increment(&m_dwRef);
   }
   ULONG InternalRelease()
   {
      return _ThreadModel::Decrement(&m_dwRef);
   }
   void Lock() { m_critsec.Lock( ); }
   void Unlock() { m_critsec.Unlock(); }

private:
   _CritSec m_critsec;
   LONG m_dwRef;
```

In den folgenden Tabellen sind die Ergebnisse der `InternalAddRef` -Methode und der- `Lock` Methode aufgeführt, abhängig vom `ThreadModel` Vorlagen Parameter und dem Threading Modell, das von der Anwendung verwendet wird:

### <a name="threadmodel--ccomobjectthreadmodel"></a>Thread Model = ccomobjectthreadmodel

|Methode|Threading mit einem oder einem Apartment|Kostenloses Threading|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|Das Inkrement ist nicht Thread sicher.|Das Inkrement ist Thread sicher.|
|`Lock`|Führt keine Aktion aus. Es ist kein kritischer Abschnitt zum Sperren vorhanden.|Der kritische Abschnitt ist gesperrt.|

### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>Thread Model = ccomobjectthreadmodel:: threadmodelnocs

|Methode|Threading mit einem oder einem Apartment|Kostenloses Threading|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|Das Inkrement ist nicht Thread sicher.|Das Inkrement ist Thread sicher.|
|`Lock`|Führt keine Aktion aus. Es ist kein kritischer Abschnitt zum Sperren vorhanden.|Führt keine Aktion aus. Es ist kein kritischer Abschnitt zum Sperren vorhanden.|

## <a name="ccommultithreadmodelcriticalsection"></a><a name="criticalsection"></a>CComMultiThreadModel:: CriticalSection

Bei Verwendung `CComMultiThreadModel` **`typedef`** `CriticalSection` von verweist der Name auf die Klasse [ccomcriticalsection](ccomcriticalsection-class.md), die Methoden zum Abrufen und Freigeben des Besitzes eines kritischen Abschnitts Objekts bereitstellt.

```
typedef CComCriticalSection CriticalSection;
```

### <a name="remarks"></a>Bemerkungen

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) und [ccommultithreadmodelnocs](ccommultithreadmodelnocs-class.md) enthalten auch Definitionen für `CriticalSection` . In der folgenden Tabelle wird die Beziehung zwischen der Threading Modell Klasse und der Critical-Abschnitts Klasse gezeigt, auf die von verwiesen wird `CriticalSection` :

|In definierte Klasse|Referenzierte Klasse|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Zusätzlich zu `CriticalSection` können Sie den **`typedef`** Namen [autocriticalsection](#autocriticalsection)verwenden. Sie sollten nicht `AutoCriticalSection` in globalen Objekten oder statischen Klassenmembern angeben, wenn Sie den CRT-Startcode entfernen möchten.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [CComMultiThreadModel:: autocriticalsection](#autocriticalsection).

## <a name="ccommultithreadmodeldecrement"></a><a name="decrement"></a>CComMultiThreadModel::D ecrement

Diese statische Funktion Ruft die Win32-Funktion " [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement)" auf, die den Wert der Variablen Dekremente, auf die *p*zeigt.

```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```

### <a name="parameters"></a>Parameter

*cker*<br/>
in Ein Zeiger auf die Variable, die dekrementiert werden soll.

### <a name="return-value"></a>Rückgabewert

Wenn das Ergebnis des dekrements 0 ist, wird `Decrement` 0 zurückgegeben. Wenn das Ergebnis des dekrements ungleich 0 (null) ist, ist der Rückgabewert auch ungleich 0 (null), ist aber möglicherweise nicht mit dem Ergebnis des dekrements identisch.

### <a name="remarks"></a>Bemerkungen

`InterlockedDecrement`verhindert, dass mehr als ein Thread gleichzeitig diese Variable verwendet.

## <a name="ccommultithreadmodelincrement"></a><a name="increment"></a>CComMultiThreadModel:: Increment

Diese statische Funktion Ruft die Win32-Funktion [interlockedinkrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement)auf, mit der der Wert der Variablen erhöht wird, auf die von *p*verwiesen wird.

```
static ULONG WINAPI Increment(LPLONG p) throw ();
```

### <a name="parameters"></a>Parameter

*cker*<br/>
in Ein Zeiger auf die Variable, die inkrementiert werden soll.

### <a name="return-value"></a>Rückgabewert

Wenn das Ergebnis des Inkrements 0 ist, wird `Increment` 0 zurückgegeben. Wenn das Ergebnis des Inkrements ungleich 0 (null) ist, ist der Rückgabewert auch ungleich 0 (null), kann aber nicht dem Ergebnis des Inkrements entsprechen.

### <a name="remarks"></a>Bemerkungen

`InterlockedIncrement`verhindert, dass mehr als ein Thread gleichzeitig diese Variable verwendet.

## <a name="ccommultithreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComMultiThreadModel:: threadmodelnocs

Wenn verwendet `CComMultiThreadModel` wird, **`typedef`** verweist der Name auf die `ThreadModelNoCS` Klasse [ccommultithreadmodelnocs](ccommultithreadmodelnocs-class.md).

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Bemerkungen

`CComMultiThreadModelNoCS`stellt Thread sichere Methoden zum Inkrementieren und Dekrementieren einer Variablen bereit. Es wird jedoch kein kritischer Abschnitt bereitgestellt.

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) und `CComMultiThreadModelNoCS` enthalten auch Definitionen für `ThreadModelNoCS` . In der folgenden Tabelle wird die Beziehung zwischen der Thread Modell Klasse und der-Klasse, auf die von verwiesen wird, gezeigt `ThreadModelNoCS` :

|In definierte Klasse|Referenzierte Klasse|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [CComMultiThreadModel:: autocriticalsection](#autocriticalsection).

## <a name="see-also"></a>Siehe auch

[CComSingleThreadModel-Klasse](ccomsinglethreadmodel-class.md)<br/>
[Ccomautocriticalsection-Klasse](ccomautocriticalsection-class.md)<br/>
[Ccomcriticalsection-Klasse](ccomcriticalsection-class.md)<br/>
[Klassenübersicht](../atl-class-overview.md)
