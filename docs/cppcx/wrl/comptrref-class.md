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
ms.openlocfilehash: f92a3e14018cf8c02dec40b664b72a0956f6220e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220534"
---
# <a name="comptrref-class"></a>ComPtrRef-Klasse

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template <typename T>
class ComPtrRef : public ComPtrRefBase<T>;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein [comptr \<T> ](comptr-class.md) -Typ oder ein von ihm abgeleiteter Typ, nicht nur die Schnittstelle, die durch dargestellt wird `ComPtr` .

## <a name="remarks"></a>Bemerkungen

Stellt einen Verweis auf ein Objekt vom Typ dar `ComPtr<T>` .

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                               | BESCHREIBUNG
---------------------------------- | -------------------------------------------------------------------------------------------------------------
[Comptrref:: comptrref](#comptrref) | Initialisiert eine neue Instanz der- `ComPtrRef` Klasse aus dem angegebenen Zeiger auf ein anderes- `ComPtrRef` Objekt.

### <a name="public-methods"></a>Öffentliche Methoden

name                                                         | BESCHREIBUNG
------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------
[Comptrref:: getaddressof](#getaddressof)                     | Ruft die Adresse eines Zeigers auf die-Schnittstelle ab, die durch das aktuelle-Objekt dargestellt wird `ComPtrRef` .
[Comptrref:: releaseandgetaddressof](#releaseandgetaddressof) | Löscht das aktuelle `ComPtrRef` -Objekt und gibt einen Zeiger auf einen Zeiger auf die-Schnittstelle zurück, die durch das-Objekt dargestellt wurde `ComPtrRef` .

### <a name="public-operators"></a>Öffentliche Operatoren

Name                                                                     | BESCHREIBUNG
------------------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[Comptrref:: Operator interfaketype * *](#operator-interfacetype-star-star) | Löscht das aktuelle `ComPtrRef` -Objekt und gibt einen Zeiger auf einen Zeiger auf die-Schnittstelle zurück, die durch das-Objekt dargestellt wurde `ComPtrRef` .
[Comptrref:: Operator T *](#operator-t-star)                               | Gibt den Wert des [ptr_](comptrrefbase-class.md#ptr) Datenmembers des aktuellen comptrref-Objekts zurück.
[Comptrref:: Operator void * *](#operator-void-star-star)                   | Löscht das aktuelle- `ComPtrRef` Objekt, wandelt den Zeiger auf die Schnittstelle um, die durch das `ComPtrRef` -Objekt als Zeiger auf Zeiger auf dargestellt wurde **`void`** , und gibt dann den Umwandlungs Zeiger zurück.
[Comptrref:: Operator *](#operator-star)                                   | Ruft den Zeiger auf die-Schnittstelle ab, die durch das aktuelle-Objekt dargestellt wird `ComPtrRef` .
[Comptrref:: Operator = =](#operator-equality)                              | Gibt an, ob zwei `ComPtrRef`-Objekte gleich sind.
[Comptrref:: Operator! =](#operator-inequality)                            | Gibt an, ob zwei `ComPtrRef`-Objekte ungleich sind.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** client.h

**Namespace:** Microsoft:: WRL::D etails

## <a name="comptrrefcomptrref"></a><a name="comptrref"></a>Comptrref:: comptrref

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>Parameter

*ptr*<br/>
Der zugrunde liegende Wert eines anderen- `ComPtrRef` Objekts.

### <a name="remarks"></a>Bemerkungen

Initialisiert eine neue Instanz der- `ComPtrRef` Klasse aus dem angegebenen Zeiger auf ein anderes- `ComPtrRef` Objekt.

## <a name="comptrrefgetaddressof"></a><a name="getaddressof"></a>Comptrref:: getaddressof

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
InterfaceType* const * GetAddressOf() const;
```

### <a name="return-value"></a>Rückgabewert

Adresse eines Zeigers auf die-Schnittstelle, die durch das aktuelle-Objekt dargestellt wird `ComPtrRef` .

### <a name="remarks"></a>Bemerkungen

Ruft die Adresse eines Zeigers auf die-Schnittstelle ab, die durch das aktuelle-Objekt dargestellt wird `ComPtrRef` .

## <a name="comptrrefoperator"></a><a name="operator-equality"></a>Comptrref:: Operator = =

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

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

*ein*<br/>
Ein Verweis auf ein `ComPtrRef`-Objekt.

*b*<br/>
Ein Verweis auf ein anderes `ComPtrRef` Objekt oder ein Zeiger auf einen anonymen Typ ( **`void*`** ).

### <a name="return-value"></a>Rückgabewert

Der erste Operator ergibt **`true`** , wenn Objekt *a* und Objekt *b*gleich sind, andernfalls **`false`** .

Der zweite und der dritte Operator ergeben sich, **`true`** Wenn Objekt *a* gleich ist, **`nullptr`** andernfalls **`false`** .

Der vierte und fünfte Operator ergeben, **`true`** Wenn Objekt *a* gleich Objekt *b*ist, und andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Gibt an, ob zwei `ComPtrRef`-Objekte gleich sind.

## <a name="comptrrefoperator"></a><a name="operator-inequality"></a>Comptrref:: Operator! =

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

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

*ein*<br/>
Ein Verweis auf ein `ComPtrRef`-Objekt.

*b*<br/>
Ein Verweis auf ein anderes `ComPtrRef` Objekt oder ein Zeiger auf ein anonymes Objekt ( **`void*`** ).

### <a name="return-value"></a>Rückgabewert

Der erste Operator ergibt **`true`** , wenn Objekt *a* nicht gleich Objekt *b*ist; andernfalls **`false`** .

Der zweite und der dritte Operator ergeben sich **`true`** , wenn Objekt *a* nicht gleich ist, **`nullptr`** andernfalls **`false`** .

Der vierte und fünfte Operator ergeben **`true`** , wenn Objekt *a* nicht gleich Objekt *b*ist, und andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Gibt an, ob zwei `ComPtrRef`-Objekte ungleich sind.

## <a name="comptrrefoperator-interfacetype"></a><a name="operator-interfacetype-star-star"></a>Comptrref:: Operator interfaketype\*\*

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
operator InterfaceType**();
```

### <a name="remarks"></a>Bemerkungen

Löscht das aktuelle `ComPtrRef` -Objekt und gibt einen Zeiger auf einen Zeiger auf die-Schnittstelle zurück, die durch das-Objekt dargestellt wurde `ComPtrRef` .

## <a name="comptrrefoperator"></a><a name="operator-star"></a>Comptrref:: Operator *

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
InterfaceType* operator *();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf die-Schnittstelle, die vom aktuellen-Objekt dargestellt wird `ComPtrRef` .

### <a name="remarks"></a>Bemerkungen

Ruft den Zeiger auf die-Schnittstelle ab, die durch das aktuelle-Objekt dargestellt wird `ComPtrRef` .

## <a name="comptrrefoperator-t"></a><a name="operator-t-star"></a>Comptrref:: Operator T *

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
operator T*();
```

### <a name="remarks"></a>Bemerkungen

Gibt den Wert des [ptr_](comptrrefbase-class.md#ptr) Datenmembers des aktuellen- `ComPtrRef` Objekts zurück.

## <a name="comptrrefoperator-void"></a><a name="operator-void-star-star"></a>Comptrref:: Operator void\*\*

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
operator void**() const;
```

### <a name="remarks"></a>Bemerkungen

Löscht das aktuelle- `ComPtrRef` Objekt, wandelt den Zeiger auf die Schnittstelle um, die durch das `ComPtrRef` -Objekt als Zeiger auf Zeiger auf dargestellt wurde **`void`** , und gibt dann den Umwandlungs Zeiger zurück.

## <a name="comptrrefreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>Comptrref:: releaseandgetaddressof

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die-Schnittstelle, die durch das gelöschte Objekt dargestellt wurde `ComPtrRef` .

### <a name="remarks"></a>Bemerkungen

Löscht das aktuelle `ComPtrRef` -Objekt und gibt einen Zeiger auf einen Zeiger auf die-Schnittstelle zurück, die durch das-Objekt dargestellt wurde `ComPtrRef` .
