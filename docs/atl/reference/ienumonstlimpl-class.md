---
title: IEnumonSTLImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl::Clone
- ATLCOM/ATL::IEnumOnSTLImpl::Init
- ATLCOM/ATL::IEnumOnSTLImpl::Next
- ATLCOM/ATL::IEnumOnSTLImpl::Reset
- ATLCOM/ATL::IEnumOnSTLImpl::Skip
- ATLCOM/ATL::IEnumOnSTLImpl::m_iter
- ATLCOM/ATL::IEnumOnSTLImpl::m_pcollection
- ATLCOM/ATL::IEnumOnSTLImpl::m_spUnk
helpviewer_keywords:
- IEnumOnSTLImpl class
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
ms.openlocfilehash: 2fbe6ccfbea2836c42a054da7ea9ebeac4e1555d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329709"
---
# <a name="ienumonstlimpl-class"></a>IEnumonSTLImpl-Klasse

Diese Klasse definiert eine Enumeratorschnittstelle basierend auf einer C++-Standardbibliotheksauflistung.

## <a name="syntax"></a>Syntax

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```

#### <a name="parameters"></a>Parameter

*Basis*<br/>
Ein COM-Enumerator. Ein Beispiel finden Sie unter [IEnumString.](/windows/win32/api/objidl/nn-objidl-ienumstring)

*piid*<br/>
Ein Zeiger auf die Schnittstellen-ID der Enumeratorschnittstelle.

*T*<br/>
Der Typ des Elements, das von der Enumeratorschnittstelle verfügbar gemacht wird.

*Kopieren*<br/>
Eine [Kopierrichtlinienklasse](../../atl/atl-copy-policy-classes.md).

*CollType*<br/>
Eine C++-Standardbibliothekscontainerklasse.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IEnumonSTLImpl::Klonen](#clone)|Die Implementierung von **Clone**.|
|[IEnumonSTLImpl::Init](#init)|Initialisiert den Enumerator.|
|[IEnumonSTLImpl::Weiter](#next)|Die Implementierung von **Next**.|
|[IEnumonSTLImpl::Reset](#reset)|Die Implementierung von **Reset**.|
|[IEnumonSTLImpl::Überspringen](#skip)|Die Implementierung von **Skip**.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IEnumonsTLImpl::m_iter](#m_iter)|Der Iterator, der die aktuelle Position des Enumerators innerhalb der Auflistung darstellt.|
|[IEnumonSTLImpl::m_pcollection](#m_pcollection)|Ein Zeiger auf den C++-Standardbibliothekscontainer, in dem die aufzuzählenden Elemente enthalten sind.|
|[IEnumonSTLImpl::m_spUnk](#m_spunk)|Der `IUnknown` Zeiger des Objekts, das die Auflistung liefert.|

## <a name="remarks"></a>Bemerkungen

`IEnumOnSTLImpl`stellt die Implementierung für eine COM-Enumeratorschnittstelle bereit, in der die aufgezählten Elemente in einem C++-Standardbibliotheks-kompatiblen Container gespeichert werden. Diese Klasse entspricht der [CComEnumImpl-Klasse,](../../atl/reference/ccomenumimpl-class.md) die eine Implementierung für eine Enumeratorschnittstelle auf basisarraybasiert bereitstellt.

> [!NOTE]
> Weitere [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init) Informationen zu weiteren Unterschieden zwischen `CComEnumImpl` und `IEnumOnSTLImpl`.

In der Regel müssen Sie *keine* eigene Enumeratorklasse erstellen, indem Sie von dieser Schnittstellenimplementierung ableiten. Wenn Sie einen von ATL bereitgestellten Enumerator basierend auf einem C++-Standardbibliothekscontainer verwenden möchten, ist es üblicher, eine Instanz von [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)zu erstellen oder eine Auflistungsklasse zu erstellen, die einen Enumerator zurückgibt, indem von [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)ableitung.

Wenn Sie jedoch einen benutzerdefinierten Enumerator bereitstellen müssen (z. B. einen, der Schnittstellen zusätzlich zur Enumeratorschnittstelle verfügbar macht), können Sie von dieser Klasse ableiten. In diesem Fall müssen Sie wahrscheinlich die [Clone-Methode](#clone) überschreiben, um Eine eigene Implementierung bereitzustellen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Base`

`IEnumOnSTLImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="ienumonstlimplinit"></a><a name="init"></a>IEnumonSTLImpl::Init

Initialisiert den Enumerator.

```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```

### <a name="parameters"></a>Parameter

*pUnkForRelease*<br/>
[in] Der `IUnknown` Zeiger eines Objekts, das während der Lebensdauer des Enumerators am Leben gehalten werden muss. Übergeben Sie NULL, wenn kein solches Objekt vorhanden ist.

*collection*<br/>
Ein Verweis auf den C++-Standardbibliothekscontainer, in dem die aufzuzählenden Elemente enthalten sind.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Wenn Sie `Init` einen Verweis auf eine Auflistung übergeben, die in einem anderen Objekt enthalten ist, können Sie den Parameter *pUnkForRelease* verwenden, um sicherzustellen, dass das Objekt und die darin enthaltene Auflistung so lange verfügbar ist, wie der Enumerator es benötigt.

Sie müssen diese Methode aufrufen, bevor Sie einen Zeiger an die Enumeratorschnittstelle an beliebige Clients zurückgeben.

## <a name="ienumonstlimplclone"></a><a name="clone"></a>IEnumonSTLImpl::Klonen

Diese Methode stellt die Implementierung der **Clone-Methode** bereit, indem ein Objekt vom Typ `CComEnumOnSTL`erstellt, es mit derselben Auflistung und demselben Iterator initialisiert wird, die vom aktuellen Objekt verwendet wird, und die Schnittstelle für das neu erstellte Objekt zurückgibt.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Parameter

*ppEnum*<br/>
[out] Die Enumeratorschnittstelle für ein neu erstelltes Objekt, das vom aktuellen Enumerator geklont wurde.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="ienumonstlimplm_spunk"></a><a name="m_spunk"></a>IEnumonSTLImpl::m_spUnk

Der `IUnknown` Zeiger des Objekts, das die Auflistung liefert.

```
CComPtr<IUnknown> m_spUnk;
```

### <a name="remarks"></a>Bemerkungen

Dieser intelligente Zeiger verwaltet einen Verweis auf das Anier [an IEnumOnSTLImpl::Init übergebene](#init)Objekt, um sicherzustellen, dass es während der Lebensdauer des Enumerators erhalten bleibt.

## <a name="ienumonstlimplm_pcollection"></a><a name="m_pcollection"></a>IEnumonSTLImpl::m_pcollection

Dieser Member verweist auf die Auflistung, die die Daten bereitstellt, die die Implementierung der Enumeratorschnittstelle antreiben.

```
CollType* m_pcollection;
```

### <a name="remarks"></a>Bemerkungen

Dieses Element wird durch einen Aufruf von [IEnumOnSTLImpl::Init](#init)initialisiert.

## <a name="ienumonstlimplm_iter"></a><a name="m_iter"></a>IEnumonsTLImpl::m_iter

Dieses Element enthält den Iterator, der verwendet wird, um die aktuelle Position innerhalb der Auflistung zu markieren und zu nachfolgenden Elementen zu navigieren.

```
CollType::iterator m_iter;
```

## <a name="ienumonstlimplnext"></a><a name="next"></a>IEnumonSTLImpl::Weiter

Diese Methode stellt die Implementierung der **Next-Methode** bereit.

```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```

### <a name="parameters"></a>Parameter

*celt*<br/>
[in] Die Anzahl der angeforderten Elemente.

*rgelt*<br/>
[out] Das Array, das mit den Elementen ausgefüllt werden soll.

*pceltFetched*<br/>
[out] Die Anzahl der Tatsächlich zurückgegebenen Elemente in *rgelt*. Dies kann kleiner als *celt* sein, wenn weniger als *celt-Elemente* in der Liste verbleiben.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="ienumonstlimplreset"></a><a name="reset"></a>IEnumonSTLImpl::Reset

Diese Methode stellt die Implementierung der **Reset-Methode** bereit.

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="ienumonstlimplskip"></a><a name="skip"></a>IEnumonSTLImpl::Überspringen

Diese Methode stellt die Implementierung der **Skip-Methode** bereit.

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Parameter

*celt*<br/>
[in] Die Anzahl der zu überspringenden Elemente.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
