---
title: CComQIPtr-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
ms.openlocfilehash: 2b1d8b92fbc5e95a5061956bafc4922d249a6f18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327418"
---
# <a name="ccomqiptr-class"></a>CComQIPtr-Klasse

Eine intelligente Zeigerklasse zum Verwalten von COM-Schnittstellenzeigern.

## <a name="syntax"></a>Syntax

```
template<class T, const IID* piid= &__uuidof(T)>
class CComQIPtr: public CComPtr<T>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Eine COM-Schnittstelle, die den Typ des zu speichernden Zeigers angibt.

*piid*<br/>
Ein Zeiger auf die IID von *T*.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComQIPtr::CComQIPtr](#ccomqiptr)|Konstruktor.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComQIPtr::Operator =](#operator_eq)|Weist dem Elementzeiger einen Zeiger zu.|

## <a name="remarks"></a>Bemerkungen

ATL `CComQIPtr` verwendet und [CComPtr,](../../atl/reference/ccomptr-class.md) um COM-Schnittstellenzeiger zu verwalten, die beide von [CComPtrBase](../../atl/reference/ccomptrbase-class.md)stammen. Beide Klassen führen eine automatische `AddRef` `Release`Verweiszählung durch Aufrufe von und durch. Überladene Operatoren verarbeiten Zeigervorgänge.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

[CComPtr](../../atl/reference/ccomptr-class.md)

`CComQIPtr`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcomcli.h

## <a name="ccomqiptrccomqiptr"></a><a name="ccomqiptr"></a>CComQIPtr::CComQIPtr

Der Konstruktor.

```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```

### <a name="parameters"></a>Parameter

*Lp*<br/>
Wird verwendet, um den Schnittstellenzeiger zu initialisieren.

*T*<br/>
Eine COM-Schnittstelle.

*piid*<br/>
Ein Zeiger auf die IID von *T*.

## <a name="ccomqiptroperator-"></a><a name="operator_eq"></a>CComQIPtr::Operator =

Der Zuweisungsoperator.

```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```

### <a name="parameters"></a>Parameter

*Lp*<br/>
Wird verwendet, um den Schnittstellenzeiger zu initialisieren.

*T*<br/>
Eine COM-Schnittstelle.

*piid*<br/>
Ein Zeiger auf die IID von *T*.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf `CComQIPtr` das aktualisierte Objekt zurück.

## <a name="see-also"></a>Siehe auch

[CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)<br/>
[CComQIPtr::CComQIPtr](#ccomqiptr)<br/>
[CComPtrBase-Klasse](../../atl/reference/ccomptrbase-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[CComQIPtrElementTraits-Klasse](../../atl/reference/ccomqiptrelementtraits-class.md)
