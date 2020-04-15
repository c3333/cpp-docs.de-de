---
title: ComPtrRefBase-Klasse
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown**
- client/Microsoft::WRL::Details::ComPtrRefBase::ptr_
helpviewer_keywords:
- Microsoft::WRL::Details::ComPtrRefBase class
- Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable** operator
- Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown** operator
- Microsoft::WRL::Details::ComPtrRefBase::ptr_ data member
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
ms.openlocfilehash: 4f6dd6449cf8135ad14486d64cea95d8329e0014
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372622"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase-Klasse

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template <typename T>
class ComPtrRefBase;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein [ComPtr\<T>](comptr-class.md) Typ oder ein daraus abgeleiteter Typ, nicht nur die Schnittstelle, die durch die dargestellt wird. `ComPtr`

## <a name="remarks"></a>Bemerkungen

Stellt die Basisklasse für die [ComPtrRef-Klasse](comptrref-class.md) dar.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

Name            | BESCHREIBUNG
--------------- | -------------------------------------------------
`InterfaceType` | Ein Synonym für den Typ des Vorlagenparameters *T*.

### <a name="public-operators"></a>Öffentliche Operatoren

Name                                                                       | BESCHREIBUNG
-------------------------------------------------------------------------- | -----------------------------------------------------------------------------------------------------
[ComPtrRefBase::operator IInspectable**](#operator-iinspectable-star-star) | Gibt das aktuelle [ptr_](#ptr) Datenmember in einen Zeiger auf einen `IInspectable` Zeiger auf die Schnittstelle um.
[ComPtrRefBase::operator IUnknown**](#operator-iunknown-star-star)         | Gibt das aktuelle [ptr_](#ptr) Datenmember in einen Zeiger auf einen `IUnknown` Zeiger auf die Schnittstelle um.

### <a name="protected-data-members"></a>Geschützte Datenmember

Name                        | BESCHREIBUNG
--------------------------- | ----------------------------------------------------------------
[ComPtrRefBase::ptr_](#ptr) | Zeiger auf den Typ, der durch den aktuellen Vorlagenparameter angegeben wird.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ComPtrRefBase`

## <a name="requirements"></a>Anforderungen

**Header:** client.h

**Namespace:** Microsoft::WRL::Details

## <a name="comptrrefbaseoperator-iinspectable-operator"></a><a name="operator-iinspectable-star-star"></a>ComPtrRefBase::operator IInspectable\* \* Operator

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
operator IInspectable**() const;
```

### <a name="remarks"></a>Bemerkungen

Gibt das aktuelle [ptr_](#ptr) Datenmember in einen Zeiger auf einen `IInspectable` Zeiger auf die Schnittstelle um.

Ein Fehler wird angezeigt, `ComPtrRefBase` wenn der Strom `IInspectable`nicht von ableitet.

Diese Umwandlung ist `__WRL_CLASSIC_COM__` nur verfügbar, wenn definiert ist.

## <a name="comptrrefbaseoperator-iunknown-operator"></a><a name="operator-iunknown-star-star"></a>ComPtrRefBase::operator IUnknown** Operator

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
operator IUnknown**() const;
```

### <a name="remarks"></a>Bemerkungen

Gibt das aktuelle [ptr_](#ptr) Datenmember in einen Zeiger auf einen `IUnknown` Zeiger auf die Schnittstelle um.

Ein Fehler wird angezeigt, `ComPtrRefBase` wenn der Strom `IUnknown`nicht von ableitet.

## <a name="comptrrefbaseptr_"></a><a name="ptr"></a>ComPtrRefBase::ptr_

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
T* ptr_;
```

### <a name="remarks"></a>Bemerkungen

Zeiger auf den Typ, der durch den aktuellen Vorlagenparameter angegeben wird. `ptr_`ist das geschützte Datenmitglied.
