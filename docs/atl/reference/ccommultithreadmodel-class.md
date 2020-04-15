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
ms.openlocfilehash: 7ef803439d2d683633e8f9c00810542dd787541e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327673"
---
# <a name="ccommultithreadmodel-class"></a>CComMultiThreadModel-Klasse

`CComMultiThreadModel`bietet threadsichere Methoden zum Erhöhen und Dekrementieren des Werts einer Variablen.

## <a name="syntax"></a>Syntax

```
class CComMultiThreadModel
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|Referenzen Klasse [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md).|
|[CComMultiThreadModel::CriticalSection](#criticalsection)|Referenzen Klasse [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).|
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|Referenzen Klasse [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComMultiThreadModel::DEkrementierung](#decrement)|(Statisch) Dekrementiert den Wert der angegebenen Variablen auf threadsichere Weise.|
|[CComMultiThreadModel::Inkrement](#increment)|(Statisch) Erhöht den Wert der angegebenen Variablen auf threadsichere Weise.|

## <a name="remarks"></a>Bemerkungen

In der `CComMultiThreadModel` Regel verwenden Sie über zwei **typedef-Namen,** entweder [CComObjectThreadModel](atl-typedefs.md-ccomobjectthreadmodel oder [CComGlobalsThreadModel](atl-typedefs.md-ccomglobalsthreadmodel). Die Klasse, auf die von jedem **typedef** verwiesen wird, hängt vom verwendeten Threadingmodell ab, wie in der folgenden Tabelle dargestellt:

|Typedef|Einzelnes Gewinden|Apartment-Threading|Kostenloses Einfädeln|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|E|E|M|
|`CComGlobalsThreadModel`|E|M|M|

S= `CComSingleThreadModel`; M=`CComMultiThreadModel`

`CComMultiThreadModel`definiert selbst drei **typedef-Namen.** `AutoCriticalSection`und `CriticalSection` Referenzklassen, die Methoden zum Abrufen und Freigeben des Besitzes eines kritischen Abschnitts bereitstellen. `ThreadModelNoCS`Referenzen Klasse [CComMultiThreadModelNoCS(ccommultithreadmodelnocs-class.md).

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="ccommultithreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CComMultiThreadModel::AutoCriticalSection

Bei `CComMultiThreadModel`verwendung verweist die `AutoCriticalSection` **typedef-Namensreferenzklasse** [CComAutoCriticalSection](ccomautocriticalsection-class.md)auf Methoden zum Abrufen und Freigeben des Besitzes eines kritischen Abschnittsobjekts.

```
typedef CComAutoCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Bemerkungen

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) und [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) enthalten `AutoCriticalSection`auch Definitionen für . Die folgende Tabelle zeigt die Beziehung zwischen der Threadingmodellklasse `AutoCriticalSection`und der kritischen Schnittklasse, auf die verwiesen wird:

|Klasse definiert in|Klasse referenziert|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Zusätzlich zu `AutoCriticalSection`können Sie den **typedef-Namen** [CriticalSection](#criticalsection)verwenden. Sie sollten `AutoCriticalSection` nicht in globalen Objekten oder statischen Klassenmembern angeben, wenn Sie den CRT-Startcode entfernen möchten.

### <a name="example"></a>Beispiel

Der folgende Code wird nach [CComObjectRootEx](ccomobjectrootex-class.md)modelliert und veranschaulicht `AutoCriticalSection` die Verwendung in einer Threadingumgebung.

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

Die folgenden Tabellen zeigen `InternalAddRef` die `Lock` Ergebnisse der `ThreadModel` und Methoden, abhängig vom Vorlagenparameter und dem threading modell, das von der Anwendung verwendet wird:

### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel

|Methode|Single- oder Apartment-Threading|Free Threading|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|Das Inkrement ist nicht threadsicher.|Das Inkrement ist threadsicher.|
|`Lock`|Tut nichts; Es gibt keinen kritischen Abschnitt, der gesperrt werden muss.|Der kritische Abschnitt ist gesperrt.|

### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel::ThreadModelNoCS

|Methode|Single- oder Apartment-Threading|Free Threading|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|Das Inkrement ist nicht threadsicher.|Das Inkrement ist threadsicher.|
|`Lock`|Tut nichts; Es gibt keinen kritischen Abschnitt, der gesperrt werden muss.|Tut nichts; Es gibt keinen kritischen Abschnitt, der gesperrt werden muss.|

## <a name="ccommultithreadmodelcriticalsection"></a><a name="criticalsection"></a>CComMultiThreadModel::CriticalSection

Bei `CComMultiThreadModel`verwendung verweist die `CriticalSection` **typedef-Namensreferenzklasse** [CComCriticalSection](ccomcriticalsection-class.md)auf Methoden zum Abrufen und Freigeben des Besitzes eines kritischen Abschnittsobjekts.

```
typedef CComCriticalSection CriticalSection;
```

### <a name="remarks"></a>Bemerkungen

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) und [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) enthalten `CriticalSection`auch Definitionen für . Die folgende Tabelle zeigt die Beziehung zwischen der Threadingmodellklasse `CriticalSection`und der kritischen Schnittklasse, auf die verwiesen wird:

|Klasse definiert in|Klasse referenziert|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Zusätzlich zu `CriticalSection`können Sie den **typedef-Namen** [AutoCriticalSection](#autocriticalsection)verwenden. Sie sollten `AutoCriticalSection` nicht in globalen Objekten oder statischen Klassenmembern angeben, wenn Sie den CRT-Startcode entfernen möchten.

### <a name="example"></a>Beispiel

Siehe [CcomMultithreadModel::AutoCriticalSection](#autocriticalsection).

## <a name="ccommultithreadmodeldecrement"></a><a name="decrement"></a>CComMultiThreadModel::DEkrementierung

Diese statische Funktion ruft die Win32-Funktion [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement)auf, die den Wert der Variablen, auf die *p*zeigt, dekrementiert.

```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```

### <a name="parameters"></a>Parameter

*P*<br/>
[in] Zeiger auf die zu dekrementierte Variable.

### <a name="return-value"></a>Rückgabewert

Wenn das Ergebnis der Dekrementierung `Decrement` 0 ist, gibt er 0 zurück. Wenn das Ergebnis der Dekrementierung ungleich Null ist, ist der Rückgabewert ebenfalls ungleich Null, entspricht jedoch möglicherweise nicht dem Ergebnis der Dekrementierung.

### <a name="remarks"></a>Bemerkungen

`InterlockedDecrement`verhindert, dass mehrere Threads gleichzeitig diese Variable verwenden.

## <a name="ccommultithreadmodelincrement"></a><a name="increment"></a>CComMultiThreadModel::Inkrement

Diese statische Funktion ruft die Win32-Funktion [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement)auf, die den Wert der Variablen, auf die *p*zeigt, erhöht.

```
static ULONG WINAPI Increment(LPLONG p) throw ();
```

### <a name="parameters"></a>Parameter

*P*<br/>
[in] Zeiger auf die zu erhöhende Variable.

### <a name="return-value"></a>Rückgabewert

Wenn das Ergebnis des Inkrements 0 ist, gibt `Increment` er 0 zurück. Wenn das Ergebnis des Inkrements ungleich Null ist, ist der Rückgabewert ebenfalls ungleich Null, entspricht jedoch möglicherweise nicht dem Ergebnis des Inkrements.

### <a name="remarks"></a>Bemerkungen

`InterlockedIncrement`verhindert, dass mehrere Threads gleichzeitig diese Variable verwenden.

## <a name="ccommultithreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComMultiThreadModel::ThreadModelNoCS

Bei `CComMultiThreadModel`Verwendung verweist der `ThreadModelNoCS` **typedef-Name** auf die Klasse [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md).

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Bemerkungen

`CComMultiThreadModelNoCS`bietet threadsichere Methoden zum Erhöhen und Dekrementieren einer Variablen; Es enthält jedoch keinen kritischen Abschnitt.

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) `CComMultiThreadModelNoCS` und enthalten auch `ThreadModelNoCS`Definitionen für . Die folgende Tabelle zeigt die Beziehung zwischen der Threadingmodellklasse und der Klasse, auf die verwiesen wird: `ThreadModelNoCS`

|Klasse definiert in|Klasse referenziert|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Beispiel

Siehe [CcomMultithreadModel::AutoCriticalSection](#autocriticalsection).

## <a name="see-also"></a>Siehe auch

[CComSingleThreadModel-Klasse](ccomsinglethreadmodel-class.md)<br/>
[CComAutoCriticalSection-Klasse](ccomautocriticalsection-class.md)<br/>
[CComCriticalSection-Klasse](ccomcriticalsection-class.md)<br/>
[Klassenübersicht](../atl-class-overview.md)
