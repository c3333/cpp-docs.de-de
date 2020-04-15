---
title: ComPtrRef-Klasse
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef
- client/Microsoft::WRL::Details::ComPtrRef::ComPtrRef
- client/Microsoft::WRL::Details::ComPtrRef::GetAddressOf
- client/Microsoft::WRL::Details::ComPtrRef::operator==
- client/Microsoft::WRL::Details::ComPtrRef::operator!=
- client/Microsoft::WRL::Details::ComPtrRef::operator InterfaceType**
- client/Microsoft::WRL::Details::ComPtrRef::operator*
- client/Microsoft::WRL::Details::ComPtrRef::operator T*
- client/Microsoft::WRL::Details::ComPtrRef::operator void**
- client/Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf
helpviewer_keywords:
- Microsoft::WRL::Details::ComPtrRef class
- Microsoft::WRL::Details::ComPtrRef::ComPtrRef, constructor
- Microsoft::WRL::Details::ComPtrRef::GetAddressOf method
- Microsoft::WRL::Details::ComPtrRef::operator== operator
- Microsoft::WRL::Details::ComPtrRef::operator!= operator
- Microsoft::WRL::Details::ComPtrRef::operator InterfaceType** operator
- Microsoft::WRL::Details::ComPtrRef::operator* operator
- Microsoft::WRL::Details::ComPtrRef::operator T* operator
- Microsoft::WRL::Details::ComPtrRef::operator void** operator
- Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf method
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
ms.openlocfilehash: df9ded817227547493c04035e0abc3d948e24495
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372634"
---
# <a name="comptrref-class"></a>ComPtrRef-Klasse

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template <typename T>
class ComPtrRef : public ComPtrRefBase<T>;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein [ComPtr\<T>](comptr-class.md) Typ oder ein daraus abgeleiteter Typ, nicht nur die Schnittstelle, die durch die dargestellt wird. `ComPtr`

## <a name="remarks"></a>Bemerkungen

Stellt einen Verweis auf `ComPtr<T>`ein Objekt vom Typ dar.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                               | BESCHREIBUNG
---------------------------------- | -------------------------------------------------------------------------------------------------------------
[ComPtrRef::ComPtrRef](#comptrref) | Initialisiert eine neue Instanz `ComPtrRef` der Klasse vom angegebenen `ComPtrRef` Zeiger auf ein anderes Objekt.

### <a name="public-methods"></a>Öffentliche Methoden

Name                                                         | BESCHREIBUNG
------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef::GetAddressOf](#getaddressof)                     | Ruft die Adresse eines Zeigers auf die `ComPtrRef` Schnittstelle ab, die durch das aktuelle Objekt dargestellt wird.
[ComPtrRef::ReleaseAndGetAddressOf](#releaseandgetaddressof) | Löscht das `ComPtrRef` aktuelle Objekt und gibt einen Zeiger auf einen Zeiger auf die `ComPtrRef` Schnittstelle zurück, die durch das Objekt dargestellt wurde.

### <a name="public-operators"></a>Öffentliche Operatoren

Name                                                                     | BESCHREIBUNG
------------------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef::operator InterfaceType**](#operator-interfacetype-star-star) | Löscht das `ComPtrRef` aktuelle Objekt und gibt einen Zeiger auf einen Zeiger auf die `ComPtrRef` Schnittstelle zurück, die durch das Objekt dargestellt wurde.
[ComPtrRef::operator T*](#operator-t-star)                               | Gibt den Wert des [ptr_](comptrrefbase-class.md#ptr) Datenmembers des aktuellen ComPtrRef-Objekts zurück.
[ComPtrRef::operator void**](#operator-void-star-star)                   | Löscht das `ComPtrRef` aktuelle Objekt, wirft den Zeiger auf die `ComPtrRef` Schnittstelle um, die vom Objekt als `void`Zeiger auf Zeiger auf zeiger-zu dargestellt dargestellt wurde, und gibt dann den Umwandlungszeiger zurück.
[ComPtrRef::Operator*](#operator-star)                                   | Ruft den Zeiger auf die Schnittstelle `ComPtrRef` ab, die durch das aktuelle Objekt dargestellt wird.
[ComPtrRef::operator==](#operator-equality)                              | Gibt an, ob zwei `ComPtrRef`-Objekte gleich sind.
[ComPtrRef::operator!=](#operator-inequality)                            | Gibt an, ob zwei `ComPtrRef`-Objekte ungleich sind.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>Anforderungen

**Header:** client.h

**Namespace:** Microsoft::WRL::Details

## <a name="comptrrefcomptrref"></a><a name="comptrref"></a>ComPtrRef::ComPtrRef

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>Parameter

*Ptr*<br/>
Der zugrunde liegende `ComPtrRef` Wert eines anderen Objekts.

### <a name="remarks"></a>Bemerkungen

Initialisiert eine neue Instanz `ComPtrRef` der Klasse vom angegebenen `ComPtrRef` Zeiger auf ein anderes Objekt.

## <a name="comptrrefgetaddressof"></a><a name="getaddressof"></a>ComPtrRef::GetAddressOf

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
InterfaceType* const * GetAddressOf() const;
```

### <a name="return-value"></a>Rückgabewert

Adresse eines Zeigers auf die Schnittstelle, die durch das aktuelle `ComPtrRef` Objekt dargestellt wird.

### <a name="remarks"></a>Bemerkungen

Ruft die Adresse eines Zeigers auf die `ComPtrRef` Schnittstelle ab, die durch das aktuelle Objekt dargestellt wird.

## <a name="comptrrefoperator"></a><a name="operator-equality"></a>ComPtrRef::operator==

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);

bool operator==(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator==(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>Parameter

*Eine*<br/>
Ein Verweis auf ein `ComPtrRef`-Objekt.

*B*<br/>
Ein Verweis `ComPtrRef` auf ein anderes Objekt oder ein`void*`Zeiger auf einen anonymen Typ ( ).

### <a name="return-value"></a>Rückgabewert

Der erste Operator gibt **true** ab, wenn Objekt *a* gleich Objekt *b*ist; andernfalls **false**.

Der zweite und dritte Operator ergeben **true,** wenn Objekt *a* gleich **nullptr**ist; andernfalls **false**.

Der vierte und fünfte Operator ergeben **true,** wenn Objekt *a* gleich Objekt *b*ist; andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Gibt an, ob zwei `ComPtrRef`-Objekte gleich sind.

## <a name="comptrrefoperator"></a><a name="operator-inequality"></a>ComPtrRef::operator!=

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);

bool operator!=(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator!=(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>Parameter

*Eine*<br/>
Ein Verweis auf ein `ComPtrRef`-Objekt.

*B*<br/>
Ein Verweis `ComPtrRef` auf ein anderes Objekt oder ein`void*`Zeiger auf ein anonymes Objekt ( ).

### <a name="return-value"></a>Rückgabewert

Der erste Operator gibt **true** ab, wenn Objekt *a* nicht gleich Objekt *b*ist; andernfalls **false**.

Der zweite und dritte Operator ergeben **true,** wenn Objekt *a* nicht gleich **nullptr**ist; andernfalls **false**.

Der vierte und fünfte Operator ergeben **true,** wenn Objekt *a* nicht gleich Objekt *b*ist; andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Gibt an, ob zwei `ComPtrRef`-Objekte ungleich sind.

## <a name="comptrrefoperator-interfacetype"></a><a name="operator-interfacetype-star-star"></a>ComPtrRef::operator InterfaceType**

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
operator InterfaceType**();
```

### <a name="remarks"></a>Bemerkungen

Löscht das `ComPtrRef` aktuelle Objekt und gibt einen Zeiger auf einen Zeiger auf die `ComPtrRef` Schnittstelle zurück, die durch das Objekt dargestellt wurde.

## <a name="comptrrefoperator"></a><a name="operator-star"></a>ComPtrRef::Operator*

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
InterfaceType* operator *();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf die Schnittstelle, `ComPtrRef` die durch das aktuelle Objekt dargestellt wird.

### <a name="remarks"></a>Bemerkungen

Ruft den Zeiger auf die Schnittstelle `ComPtrRef` ab, die durch das aktuelle Objekt dargestellt wird.

## <a name="comptrrefoperator-t"></a><a name="operator-t-star"></a>ComPtrRef::operator T*

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
operator T*();
```

### <a name="remarks"></a>Bemerkungen

Gibt den Wert des [ptr_](comptrrefbase-class.md#ptr) Datenmember des aktuellen `ComPtrRef` Objekts zurück.

## <a name="comptrrefoperator-void"></a><a name="operator-void-star-star"></a>ComPtrRef::operator void\*\*

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
operator void**() const;
```

### <a name="remarks"></a>Bemerkungen

Löscht das `ComPtrRef` aktuelle Objekt, wirft den Zeiger auf die `ComPtrRef` Schnittstelle um, die vom Objekt als `void`Zeiger auf Zeiger auf zeiger-zu dargestellt dargestellt wurde, und gibt dann den Umwandlungszeiger zurück.

## <a name="comptrrefreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>ComPtrRef::ReleaseAndGetAddressOf

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf die Schnittstelle, die `ComPtrRef` durch das gelöschte Objekt dargestellt wurde.

### <a name="remarks"></a>Bemerkungen

Löscht das `ComPtrRef` aktuelle Objekt und gibt einen Zeiger auf einen Zeiger auf die `ComPtrRef` Schnittstelle zurück, die durch das Objekt dargestellt wurde.
