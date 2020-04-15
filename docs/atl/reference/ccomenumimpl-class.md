---
title: CComEnumImpl-Klasse
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
ms.openlocfilehash: 965e0a8bf6c890882754b60e2785832933d1c52c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327861"
---
# <a name="ccomenumimpl-class"></a>CComEnumImpl-Klasse

Diese Klasse stellt die Implementierung für eine COM-Enumeratorschnittstelle bereit, in der die aufgezählten Elemente in einem Array gespeichert werden.

## <a name="syntax"></a>Syntax

```
template <class Base,
    const IID* piid, class T, class Copy>
class ATL_NO_VTABLE CComEnumImpl : public Base
```

#### <a name="parameters"></a>Parameter

*Basis*<br/>
Eine COM-Enumeratorschnittstelle. Ein Beispiel finden Sie unter [IEnumString.](/windows/win32/api/objidl/nn-objidl-ienumstring)

*piid*<br/>
Ein Zeiger auf die Schnittstellen-ID der Enumeratorschnittstelle.

*T*<br/>
Der Typ des Elements, das von der Enumeratorschnittstelle verfügbar gemacht wird.

*Kopieren*<br/>
Eine homogene [Kopierrichtlinienklasse](../../atl/atl-copy-policy-classes.md).

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|Der Konstruktor.|
|[CComEnumImpl::'CComEnumImpl](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComEnumImpl::Klonen](#clone)|Die Implementierung **Clone** der Clone-Enumerationsschnittstellenmethode.|
|[CComEnumImpl::Init](#init)|Initialisiert den Enumerator.|
|[CComEnumImpl::Weiter](#next)|Die Implementierung von **Next**.|
|[CComEnumImpl::Reset](#reset)|Die Implementierung von **Reset**.|
|[CComEnumImpl::Überspringen](#skip)|Die Implementierung von **Skip**.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComEnumImpl::m_begin](#m_begin)|Ein Zeiger auf das erste Element im Array.|
|[CComEnumImpl::m_dwFlags](#m_dwflags)|Kopieren von `Init`Flags, die durch übergeben wurden.|
|[CComEnumImpl::m_end](#m_end)|Ein Zeiger auf die Position direkt hinter dem letzten Element im Array.|
|[CComEnumImpl::m_iter](#m_iter)|Ein Zeiger auf das aktuelle Element im Array.|
|[CComEnumImpl::m_spUnk](#m_spunk)|Der `IUnknown` Zeiger des Objekts, das die Auflistung liefert, die aufgezählt wird.|

## <a name="remarks"></a>Bemerkungen

Ein Beispiel für Methodenimplementierungen finden Sie unter [IEnumString.](/windows/win32/api/objidl/nn-objidl-ienumstring) `CComEnumImpl`stellt die Implementierung für eine COM-Enumeratorschnittstelle bereit, in der die aufgezählten Elemente in einem Array gespeichert werden. Diese Klasse entspricht der `IEnumOnSTLImpl` Klasse, die eine Implementierung einer Enumeratorschnittstelle basierend auf einem C++-Standardbibliothekscontainer bereitstellt.

> [!NOTE]
> Weitere Informationen zu `CComEnumImpl` weiteren `IEnumOnSTLImpl`Unterschieden zwischen und finden Sie unter [CComEnumImpl::Init](#init).

In der Regel müssen Sie *keine* eigene Enumeratorklasse erstellen, indem Sie von dieser Schnittstellenimplementierung ableiten. Wenn Sie einen von ATL bereitgestellten Enumerator basierend auf einem Array verwenden möchten, ist es üblicher, eine Instanz von [CComEnum](../../atl/reference/ccomenum-class.md)zu erstellen.

Wenn Sie jedoch einen benutzerdefinierten Enumerator bereitstellen müssen (z. B. einen, der Schnittstellen zusätzlich zur Enumeratorschnittstelle verfügbar macht), können Sie von dieser Klasse ableiten. In diesem Fall müssen Sie wahrscheinlich die [CComEnumImpl::Clone-Methode](#clone) überschreiben, um Eine eigene Implementierung bereitzustellen.

Weitere Informationen finden Sie unter [ATL-Sammlungen und -Enumeratoren](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Base`

`CComEnumImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="ccomenumimplccomenumimpl"></a><a name="ccomenumimpl"></a>CComEnumImpl::CComEnumImpl

Der Konstruktor.

```
CComEnumImpl();
```

## <a name="ccomenumimplccomenumimpl"></a><a name="dtor"></a>CComEnumImpl::'CComEnumImpl

Der Destruktor.

```
~CComEnumImpl();
```

## <a name="ccomenumimplinit"></a><a name="init"></a>CComEnumImpl::Init

Sie müssen diese Methode aufrufen, bevor Sie einen Zeiger an die Enumeratorschnittstelle an beliebige Clients zurückgeben.

```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```

### <a name="parameters"></a>Parameter

*Beginnen*<br/>
Ein Zeiger auf das erste Element des Arrays, das die aufzuzählenden Elemente enthält.

*Ende*<br/>
Ein Zeiger auf die Position direkt hinter dem letzten Element des Arrays, das die aufzuzählenden Elemente enthält.

*Punk*<br/>
[in] Der `IUnknown` Zeiger eines Objekts, das während der Lebensdauer des Enumerators am Leben gehalten werden muss. Übergeben Sie NULL, wenn kein solches Objekt vorhanden ist.

*Flaggen*<br/>
Flags, die angeben, ob der Enumerator den Besitz des Arrays übernehmen oder eine Kopie davon erstellen soll. Mögliche Werte werden unten beschrieben.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode nur einmal auf – initialisieren Sie den Enumerator, verwenden Sie ihn, und werfen Sie ihn dann weg.

Wenn Sie Zeiger auf Elemente in einem Array übergeben, die in einem anderen Objekt enthalten sind (und Sie den Enumerator nicht bitten, die Daten zu kopieren), können Sie den *pUnk-Parameter* verwenden, um sicherzustellen, dass das Objekt und das darin enthaltene Array so lange verfügbar sind, wie der Enumerator sie benötigt. Der Enumerator hält einfach einen COM-Verweis auf das Objekt, um es am Leben zu erhalten. Die COM-Referenz wird automatisch freigegeben, wenn der Enumerator zerstört wird.

Mit dem *Parameter flags* können Sie angeben, wie der Enumerator die an ihn übergebenen Arrayelemente behandeln soll. *Flags* können einen der Werte `CComEnumFlags` aus der unten gezeigten Enumeration übernehmen:

```
enum CComEnumFlags
   {
   AtlFlagNoCopy = 0,
   AtlFlagTakeOwnership = 2, // BitOwn
   AtlFlagCopy = 3           // BitOwn | BitCopy
   };
```

`AtlFlagNoCopy`bedeutet, dass die Lebensdauer des Arrays nicht vom Enumerator gesteuert wird. In diesem Fall ist entweder das Array statisch, oder das von *pUnk* identifizierte Objekt ist dafür verantwortlich, das Array freizugeben, wenn es nicht mehr benötigt wird.

`AtlFlagTakeOwnership`bedeutet, dass die Zerstörung des Arrays vom Enumerator gesteuert werden soll. In diesem Fall muss das Array dynamisch mit **neuen**zugewiesen worden sein. Der Enumerator löscht das Array in seinem Destruktor. In der Regel würden Sie NULL für *pUnk*übergeben, obwohl Sie immer noch einen gültigen Zeiger übergeben können, wenn Sie aus irgendeinem Grund über die Zerstörung des Enumerators benachrichtigt werden müssen.

`AtlFlagCopy`bedeutet, dass ein neues Array durch Kopieren `Init`des Arrays erstellt werden soll, das an übergeben wird. Die Lebensdauer des neuen Arrays wird vom Enumerator gesteuert. Der Enumerator löscht das Array in seinem Destruktor. In der Regel würden Sie NULL für *pUnk*übergeben, obwohl Sie immer noch einen gültigen Zeiger übergeben können, wenn Sie aus irgendeinem Grund über die Zerstörung des Enumerators benachrichtigt werden müssen.

> [!NOTE]
> Der Prototyp dieser Methode gibt die Arrayelemente `T`als `T` vom Typ an, wobei als Vorlagenparameter für die Klasse definiert wurde. Dies ist derselbe Typ, der mit der COM-Schnittstellenmethode [CComEnumImpl::Next](#next)verfügbar gemacht wird. Dies hat zur Folge, dass diese Klasse im Gegensatz zu [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)keine unterschiedlichen Speicher- und verfügbar gemachten Datentypen unterstützt. Der Datentyp der Elemente im Array muss mit dem Datentyp identisch sein, der über die COM-Schnittstelle verfügbar gemacht wird.

## <a name="ccomenumimplclone"></a><a name="clone"></a>CComEnumImpl::Klonen

Diese Methode stellt die Implementierung der **Clone-Methode** bereit, indem ein Objekt vom Typ `CComEnum`erstellt, es mit demselben Array und Iterator initialisiert wird, das vom aktuellen Objekt verwendet wird, und die Schnittstelle für das neu erstellte Objekt zurückgibt.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Parameter

*ppEnum*<br/>
[out] Die Enumeratorschnittstelle für ein neu erstelltes Objekt, das vom aktuellen Enumerator geklont wurde.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass geklonte Enumeratoren niemals ihre eigene Kopie (oder Übernahme des Besitzes) der vom ursprünglichen Enumerator verwendeten Daten erstellen. Bei Bedarf halten geklonte Enumeratoren den ursprünglichen Enumerator am Leben (unter Verwendung einer COM-Referenz), um sicherzustellen, dass die Daten so lange verfügbar sind, wie sie sie benötigen.

## <a name="ccomenumimplm_spunk"></a><a name="m_spunk"></a>CComEnumImpl::m_spUnk

Dieser intelligente Zeiger verwaltet einen Verweis auf das an [CComEnumImpl::Init übergebene](#init)Objekt, um sicherzustellen, dass es während der Lebensdauer des Enumerators erhalten bleibt.

```
CComPtr<IUnknown> m_spUnk;
```

## <a name="ccomenumimplm_begin"></a><a name="m_begin"></a>CComEnumImpl::m_begin

Ein Zeiger auf die Position direkt hinter dem letzten Element des Arrays, das die aufzuzählenden Elemente enthält.

```
T* m_begin;
```

## <a name="ccomenumimplm_end"></a><a name="m_end"></a>CComEnumImpl::m_end

Ein Zeiger auf das erste Element des Arrays, das die aufzuzählenden Elemente enthält.

```
T* m_end;
```

## <a name="ccomenumimplm_iter"></a><a name="m_iter"></a>CComEnumImpl::m_iter

Ein Zeiger auf das aktuelle Element des Arrays, das die aufzuzählenden Elemente enthält.

```
T* m_iter;
```

## <a name="ccomenumimplm_dwflags"></a><a name="m_dwflags"></a>CComEnumImpl::m_dwFlags

Die Flags wurden an [CComEnumImpl::Init](#init)übergeben.

```
DWORD m_dwFlags;
```

## <a name="ccomenumimplnext"></a><a name="next"></a>CComEnumImpl::Weiter

Diese Methode stellt die Implementierung der **Next-Methode** bereit.

```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```

### <a name="parameters"></a>Parameter

*celt*<br/>
[in] Die Anzahl der angeforderten Elemente.

*rgelt*<br/>
[out] Das Array, das mit den Elementen gefüllt werden soll.

*pceltFetched*<br/>
[out] Die Anzahl der Tatsächlich zurückgegebenen Elemente in *rgelt*. Dies kann kleiner als *celt* sein, wenn weniger als *Celt-Elemente* in der Liste verbleiben.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="ccomenumimplreset"></a><a name="reset"></a>CComEnumImpl::Reset

Diese Methode stellt die Implementierung der **Reset-Methode** bereit.

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="ccomenumimplskip"></a><a name="skip"></a>CComEnumImpl::Überspringen

Diese Methode stellt die Implementierung der **Skip-Methode** bereit.

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Parameter

*celt*<br/>
[in] Die Anzahl der zu überspringenden Elemente.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Gibt E_INVALIDARG wenn *celt* Null ist, gibt S_FALSE zurück, wenn weniger als *celt-Elemente* zurückgegeben werden, gibt S_OK andernfalls zurück.

## <a name="see-also"></a>Siehe auch

[IEnumonSTLImpl-Klasse](../../atl/reference/ienumonstlimpl-class.md)<br/>
[CComEnum-Klasse](../../atl/reference/ccomenum-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
