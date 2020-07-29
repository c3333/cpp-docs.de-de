---
title: Ccomsumimpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComEnumImpl
- ATLCOM/ATL::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::Clone
- ATLCOM/ATL::CComEnumImpl::Init
- ATLCOM/ATL::CComEnumImpl::Next
- ATLCOM/ATL::CComEnumImpl::Reset
- ATLCOM/ATL::CComEnumImpl::Skip
- ATLCOM/ATL::CComEnumImpl::m_begin
- ATLCOM/ATL::CComEnumImpl::m_dwFlags
- ATLCOM/ATL::CComEnumImpl::m_end
- ATLCOM/ATL::CComEnumImpl::m_iter
- ATLCOM/ATL::CComEnumImpl::m_spUnk
helpviewer_keywords:
- CComEnumImpl class
ms.assetid: cc0d8e76-e608-46db-87cd-4c7161fe32d2
ms.openlocfilehash: 517a4e90ca21e22dcf161aefcff61a40437eabe0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226606"
---
# <a name="ccomenumimpl-class"></a>Ccomsumimpl-Klasse

Diese Klasse stellt die Implementierung für eine com-Enumeratorschnittstelle bereit, bei der die aufzuzählenden Elemente in einem Array gespeichert werden.

## <a name="syntax"></a>Syntax

```
template <class Base,
    const IID* piid, class T, class Copy>
class ATL_NO_VTABLE CComEnumImpl : public Base
```

#### <a name="parameters"></a>Parameter

*Sock*<br/>
Eine com-Enumeratorschnittstelle. Ein Beispiel finden Sie unter " [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) ".

*piid*<br/>
Ein Zeiger auf die Schnittstellen-ID der Enumeratorschnittstelle.

*T*<br/>
Der Typ des Elements, das von der Enumeratorschnittstelle verfügbar gemacht wird.

*Kopieren*<br/>
Eine homogene [Kopier Richtlinien Klasse](../../atl/atl-copy-policy-classes.md).

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[Ccomeinumimpl:: ccomeinumimpl](#ccomenumimpl)|Der Konstruktor.|
|[Ccomeinumimpl:: ~ ccomendumimpl](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[Ccomendumimpl:: Clone](#clone)|Die Implementierung der Methode für die **Klon** Enumeration-Schnittstelle.|
|[Ccomumumimpl:: init](#init)|Initialisiert den Enumerator.|
|[Ccomeinumimpl:: Next](#next)|Die Implementierung von **Next**.|
|[Ccomeinumimpl:: Reset](#reset)|Die Implementierung der **zurück**Setzung.|
|[Ccomendumimpl:: Skip](#skip)|Die Implementierung von **Skip**.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|Beschreibung|
|----------|-----------------|
|[Ccomumumimpl:: m_begin](#m_begin)|Ein Zeiger auf das erste Element im Array.|
|[Ccomumumimpl:: m_dwFlags](#m_dwflags)|Kopierflags wurden durchlaufen `Init` .|
|[Ccomumumimpl:: m_end](#m_end)|Ein Zeiger auf die Position direkt hinter dem letzten Element im Array.|
|[Ccomumumimpl:: m_iter](#m_iter)|Ein Zeiger auf das aktuelle Element im Array.|
|[Ccomumumimpl:: m_spUnk](#m_spunk)|Der `IUnknown` Zeiger des-Objekts, das die aufgelistete Auflistung bereitstellt.|

## <a name="remarks"></a>Bemerkungen

Ein Beispiel für Methoden Implementierungen finden Sie unter [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) . `CComEnumImpl`stellt die Implementierung für eine com-Enumeratorschnittstelle bereit, bei der die aufzuzählenden Elemente in einem Array gespeichert werden. Diese Klasse entspricht der- `IEnumOnSTLImpl` Klasse, die eine Implementierung einer Enumeratorschnittstelle bereitstellt, die auf einem C++-Standard Bibliotheks Container basiert.

> [!NOTE]
> Ausführliche Informationen zu weiteren Unterschieden zwischen `CComEnumImpl` und finden Sie unter `IEnumOnSTLImpl` [ccomsumimpl:: init](#init).

In der Regel müssen Sie *keine* eigene Enumeratorklasse erstellen, indem Sie von dieser Schnittstellen Implementierung ableiten. Wenn Sie einen von ATL bereitgestellten Enumerator verwenden möchten, der auf einem Array basiert, ist es häufiger, eine Instanz von [CComEnum](../../atl/reference/ccomenum-class.md)zu erstellen.

Wenn Sie jedoch einen benutzerdefinierten Enumerator angeben müssen (z. b. einen, der Schnittstellen zusätzlich zur Enumeratorschnittstelle verfügbar macht), können Sie von dieser Klasse ableiten. In dieser Situation ist es wahrscheinlich, dass Sie die [ccomsumimpl:: Clone](#clone) -Methode außer Kraft setzen müssen, um eine eigene Implementierung bereitzustellen.

Weitere Informationen finden Sie unter [ATL-Auflistungen und-Enumeratoren](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Base`

`CComEnumImpl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Atlcom. h

## <a name="ccomenumimplccomenumimpl"></a><a name="ccomenumimpl"></a>Ccomeinumimpl:: ccomeinumimpl

Der Konstruktor.

```
CComEnumImpl();
```

## <a name="ccomenumimplccomenumimpl"></a><a name="dtor"></a>Ccomeinumimpl:: ~ ccomendumimpl

Der Destruktor.

```
~CComEnumImpl();
```

## <a name="ccomenumimplinit"></a><a name="init"></a>Ccomumumimpl:: init

Sie müssen diese Methode vor dem Übergeben eines Zeigers an die Enumeratorschnittstelle zurück an alle Clients ausführen.

```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```

### <a name="parameters"></a>Parameter

*beginnen*<br/>
Ein Zeiger auf das erste Element des Arrays, das die aufzuzählenden Elemente enthält.

*end*<br/>
Ein Zeiger auf die Position direkt hinter dem letzten Element des Arrays, das die aufzuzählenden Elemente enthält.

*Kro*<br/>
in Der `IUnknown` Zeiger eines Objekts, das während der Lebensdauer des Enumerators aufrechterhalten werden muss. Übergeben Sie NULL, wenn kein solches Objekt vorhanden ist.

*flags*<br/>
Flags, die angeben, ob der Enumerator den Besitz des Arrays übernehmen oder eine Kopie davon erstellen soll. Mögliche Werte sind unten beschrieben.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Bemerkungen

Diese Methode nur einmal aufzurufen – initialisieren Sie den Enumerator, verwenden Sie ihn, und lösen Sie ihn aus.

Wenn Sie Zeiger an Elemente in einem Array übergeben, das in einem anderen Objekt gespeichert ist (und Sie den Enumerator nicht zum Kopieren der Daten auffordern), können Sie den *Punk* -Parameter verwenden, um sicherzustellen, dass das Objekt und das enthaltene Array so lange verfügbar sind, wie der Enumerator Sie benötigt. Der Enumerator enthält einfach einen com-Verweis auf das-Objekt, um ihn aktiv zu halten. Der com-Verweis wird automatisch freigegeben, wenn der Enumerator zerstört wird.

Mit dem *Flags* -Parameter können Sie angeben, wie der Enumerator die an ihn übergebenen Array Elemente behandeln soll. *Flags* können einen der Werte aus der `CComEnumFlags` unten gezeigten Enumeration entnehmen:

```
enum CComEnumFlags
   {
   AtlFlagNoCopy = 0,
   AtlFlagTakeOwnership = 2, // BitOwn
   AtlFlagCopy = 3           // BitOwn | BitCopy
   };
```

`AtlFlagNoCopy`bedeutet, dass die Lebensdauer des Arrays nicht durch den Enumerator gesteuert wird. In diesem Fall ist entweder das Array statisch, oder das von *Punk* identifizierte Objekt ist für das Freigeben des Arrays zuständig, wenn es nicht mehr benötigt wird.

`AtlFlagTakeOwnership`bedeutet, dass die Zerstörung des Arrays durch den Enumerator gesteuert werden soll. In diesem Fall muss das Array dynamisch mithilfe von zugeordnet werden **`new`** . Der Enumerator löscht das Array in seinem Dekonstruktor. In der Regel würden Sie NULL für *Punk*übergeben, obwohl Sie immer noch einen gültigen Zeiger übergeben können, wenn Sie über die Zerstörung des Enumerators aus irgendeinem Grund benachrichtigt werden müssen.

`AtlFlagCopy`bedeutet, dass ein neues Array erstellt werden soll, indem das an über gegebene Array kopiert wird `Init` . Die Lebensdauer des neuen Arrays soll durch den Enumerator gesteuert werden. Der Enumerator löscht das Array in seinem Dekonstruktor. In der Regel würden Sie NULL für *Punk*übergeben, obwohl Sie immer noch einen gültigen Zeiger übergeben können, wenn Sie über die Zerstörung des Enumerators aus irgendeinem Grund benachrichtigt werden müssen.

> [!NOTE]
> Der Prototyp dieser Methode gibt die Array Elemente als Typ an `T` , wobei `T` als Vorlagen Parameter für die Klasse definiert wurde. Dabei handelt es sich um denselben Typ, der über die COM-Schnittstellen Methode [ccomsumimpl:: Next](#next)verfügbar gemacht wird. Dies impliziert, dass diese Klasse im Gegensatz zu [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)keine unterschiedlichen Speicher-und Datentypen unterstützt. Der Datentyp der Elemente im Array muss mit dem Datentyp übereinstimmen, der über die COM-Schnittstelle verfügbar gemacht wird.

## <a name="ccomenumimplclone"></a><a name="clone"></a>Ccomendumimpl:: Clone

Diese Methode bietet die Implementierung der **Clone** -Methode, indem ein Objekt vom Typ erstellt `CComEnum` wird, das mit demselben Array und Iterator initialisiert wird, das vom aktuellen-Objekt verwendet wird, und die-Schnittstelle für das neu erstellte-Objekt zurückgegeben wird.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Parameter

*ppEnum*<br/>
vorgenommen Die Enumeratorschnittstelle für ein neu erstelltes Objekt, das vom aktuellen Enumerator geklont wurde.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass geklonte Enumeratoren nie ihren eigenen Kopiervorgang (oder Besitz Besitz) der vom ursprünglichen Enumerator verwendeten Daten erstellen. Bei Bedarf behalten geklonte Enumeratoren den ursprünglichen Enumerator (mithilfe eines COM-Verweises) bei, um sicherzustellen, dass die Daten so lange verfügbar sind, wie Sie benötigt werden.

## <a name="ccomenumimplm_spunk"></a><a name="m_spunk"></a>Ccomumumimpl:: m_spUnk

Dieser intelligente Zeiger behält einen Verweis auf das an [CComEnumImpl:: init](#init)übergebenen Objekt bei und stellt sicher, dass es während der Lebensdauer des Enumerators aktiv bleibt.

```
CComPtr<IUnknown> m_spUnk;
```

## <a name="ccomenumimplm_begin"></a><a name="m_begin"></a>Ccomumumimpl:: m_begin

Ein Zeiger auf die Position direkt hinter dem letzten Element des Arrays, das die aufzuzählenden Elemente enthält.

```
T* m_begin;
```

## <a name="ccomenumimplm_end"></a><a name="m_end"></a>Ccomumumimpl:: m_end

Ein Zeiger auf das erste Element des Arrays, das die aufzuzählenden Elemente enthält.

```
T* m_end;
```

## <a name="ccomenumimplm_iter"></a><a name="m_iter"></a>Ccomumumimpl:: m_iter

Ein Zeiger auf das aktuelle Element des Arrays, das die aufzuzählenden Elemente enthält.

```
T* m_iter;
```

## <a name="ccomenumimplm_dwflags"></a><a name="m_dwflags"></a>Ccomumumimpl:: m_dwFlags

Die an [CComEnumImpl:: init](#init)übergebenen Flags.

```
DWORD m_dwFlags;
```

## <a name="ccomenumimplnext"></a><a name="next"></a>Ccomeinumimpl:: Next

Diese Methode bietet die Implementierung der **nächsten** Methode.

```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```

### <a name="parameters"></a>Parameter

*celt*<br/>
in Die Anzahl der angeforderten Elemente.

*rgelt*<br/>
vorgenommen Das Array, das mit den Elementen aufgefüllt werden soll.

*pceltFetched*<br/>
vorgenommen Die Anzahl der Elemente, die tatsächlich in *rgelt*zurückgegeben werden. Dies kann kleiner als der *celt* sein, wenn weniger als *celt* -Elemente in der Liste enthalten sind.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

## <a name="ccomenumimplreset"></a><a name="reset"></a>Ccomeinumimpl:: Reset

Diese Methode stellt die Implementierung der **Reset** -Methode bereit.

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

## <a name="ccomenumimplskip"></a><a name="skip"></a>Ccomendumimpl:: Skip

Diese Methode stellt die Implementierung der **Skip** -Methode bereit.

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Parameter

*celt*<br/>
in Die Anzahl der zu über springenden Elemente.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Bemerkungen

Gibt E_INVALIDARG zurück, wenn *celt* NULL ist, gibt S_FALSE zurück, wenn weniger als *celt* -Elemente zurückgegeben werden, andernfalls S_OK.

## <a name="see-also"></a>Siehe auch

[IEnumOnSTLImpl-Klasse](../../atl/reference/ienumonstlimpl-class.md)<br/>
[Ccomenumerationsklasse](../../atl/reference/ccomenum-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
