---
title: CComPtr-Klasse
description: Referenzhandbuch zur Microsoft C++ Active Template Library (ATL)-Klasse CComPtr.
ms.date: 02/07/2020
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
ms.openlocfilehash: 855466225db2672755658dcbbc9a266d09e0e7be
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327528"
---
# <a name="ccomptr-class"></a>CComPtr-Klasse

Eine intelligente Zeigerklasse zum Verwalten von COM-Schnittstellenzeigern.

## <a name="syntax"></a>Syntax

```cpp
template<class T>
class CComPtr
```

### <a name="parameters"></a>Parameter

*T*<br/>
Eine COM-Schnittstelle, die den Typ des zu speichernden Zeigers angibt.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComPtr::CComPtr](#ccomptr)|Der Konstruktor.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComPtr::operator =](#operator_eq)|Weist dem Elementzeiger einen Zeiger zu.|

## <a name="remarks"></a>Bemerkungen

ATL `CComPtr` verwendet und [CComQIPtr,](../../atl/reference/ccomqiptr-class.md) um COM-Schnittstellenzeiger zu verwalten. Beide sind von [CComPtrBase](../../atl/reference/ccomptrbase-class.md)abgeleitet und beide machen automatische Referenzzählung.

Die `CComPtr` und [CComQIPtr-Klassen](../../atl/reference/ccomqiptr-class.md) können durch automatische Referenzzählung dazu beitragen, Speicherverluste zu beseitigen.  Die folgenden Funktionen ausführen die gleichen logischen Vorgänge. Die zweite Version ist jedoch möglicherweise weniger fehleranfällig, da sie die `CComPtr` Klasse verwendet:

[!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]

[!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]

In Debugbuilds wird der Link atlsd.lib für die Codeablaufverfolgung verwendet.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

`CComPtr`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="ccomptrccomptr"></a><a name="ccomptr"></a>CComPtr::CComPtr

Der Konstruktor.

```cpp
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```

### <a name="parameters"></a>Parameter

*Lp*<br/>
Wird verwendet, um den Schnittstellenzeiger zu initialisieren.

*T*<br/>
Eine COM-Schnittstelle.

### <a name="remarks"></a>Bemerkungen

Die Konstruktoren, die `AddRef` ein Argument *aufrufen,* rufen lp auf, wenn es sich nicht um einen Nullzeiger handelt. Ein Objekt, das nicht `Release` im Besitz von NULL ist, ruft die Zerstörung des CComPtr-Objekts auf oder wenn dem CComPtr-Objekt ein neues Objekt zugewiesen wird.

## <a name="ccomptroperator-"></a><a name="operator_eq"></a>CComPtr::operator =

Zuweisungsoperator.

```cpp
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf `CComPtr` das aktualisierte Objekt zurück

### <a name="remarks"></a>Bemerkungen

Mit diesem Vorgang AddRefs das neue Objekt und gibt das vorhandene Objekt frei, sofern vorhanden.

## <a name="see-also"></a>Siehe auch

[CComPtr::CComPtr](#ccomptr)<br/>
[CComQIPtr::CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
