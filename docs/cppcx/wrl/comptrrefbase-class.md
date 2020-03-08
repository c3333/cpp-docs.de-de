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
ms.openlocfilehash: df4e2aa1ce650fd5b1f04baf2f7c4cd2fb4cff93
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865820"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase-Klasse

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template <typename T>
class ComPtrRefBase;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein [comptr-\<t >](comptr-class.md) Typ oder ein von ihm abgeleiteter Typ, nicht nur die Schnittstelle, die vom `ComPtr`dargestellt wird.

## <a name="remarks"></a>Bemerkungen

Stellt die Basisklasse für die [comptrref](comptrref-class.md) -Klasse dar.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Öffentliche Typedefs

Name            | BESCHREIBUNG
--------------- | -------------------------------------------------
`InterfaceType` | Ein Synonym für den Typ des Vorlagen Parameters *T*.

### <a name="public-operators"></a>Öffentliche Operatoren

Name                                                                       | BESCHREIBUNG
-------------------------------------------------------------------------- | -----------------------------------------------------------------------------------------------------
[Comptrrefbase:: Operator iinspectable * *](#operator-iinspectable-star-star) | Wandelt das aktuelle [ptr_](#ptr) Datenmember in einen Zeiger auf einen Zeiger auf die `IInspectable` Schnittstelle um.
[Comptrref Base:: Operator IUnknown * *](#operator-iunknown-star-star)         | Wandelt das aktuelle [ptr_](#ptr) Datenmember in einen Zeiger auf einen Zeiger auf die `IUnknown` Schnittstelle um.

### <a name="protected-data-members"></a>Geschützte Datenelemente

Name                        | BESCHREIBUNG
--------------------------- | ----------------------------------------------------------------
[Comptrref Base::p tr_](#ptr) | Ein Zeiger auf den Typ, der durch den aktuellen Vorlagen Parameter angegeben wird.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ComPtrRefBase`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** client.h

**Namespace:** Microsoft:: WRL::D etails

## <a name="operator-iinspectable-star-star"></a>Comptrrefbase:: Operator iinspectable\*\*-Operator

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
operator IInspectable**() const;
```

### <a name="remarks"></a>Bemerkungen

Wandelt das aktuelle [ptr_](#ptr) Datenmember in einen Zeiger auf einen Zeiger auf die `IInspectable` Schnittstelle um.

Wenn die aktuelle `ComPtrRefBase` nicht von `IInspectable`abgeleitet ist, wird ein Fehler ausgegeben.

Diese Umwandlung ist nur verfügbar, wenn `__WRL_CLASSIC_COM__` definiert ist.

## <a name="operator-iunknown-star-star"></a>Comptrref Base:: Operator IUnknown * *-Operator

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
operator IUnknown**() const;
```

### <a name="remarks"></a>Bemerkungen

Wandelt das aktuelle [ptr_](#ptr) Datenmember in einen Zeiger auf einen Zeiger auf die `IUnknown` Schnittstelle um.

Wenn die aktuelle `ComPtrRefBase` nicht von `IUnknown`abgeleitet ist, wird ein Fehler ausgegeben.

## <a name="ptr"></a>Comptrref Base::p tr_

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
T* ptr_;
```

### <a name="remarks"></a>Bemerkungen

Ein Zeiger auf den Typ, der durch den aktuellen Vorlagen Parameter angegeben wird. `ptr_` ist das geschützte Datenmember.
