---
title: MakeAllocator-Klasse
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
- implements/Microsoft::WRL::Details::MakeAllocator::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::~MakeAllocator
helpviewer_keywords:
- Microsoft::WRL::Details::MakeAllocator class
- Microsoft::WRL::Details::MakeAllocator::Allocate method
- Microsoft::WRL::Details::MakeAllocator::Detach method
- Microsoft::WRL::Details::MakeAllocator::MakeAllocator, constructor
- Microsoft::WRL::Details::MakeAllocator::~MakeAllocator, destructor
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
ms.openlocfilehash: dc0d83f2550646572a4eff2bec7850037c6dbf6a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371333"
---
# <a name="makeallocator-class"></a>MakeAllocator-Klasse

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template<
    typename T,
    bool hasWeakReferenceSupport =
          !__is_base_of(RuntimeClassFlags<InhibitWeakReference>,
                        T)
>
class MakeAllocator;

template<typename T>
class MakeAllocator<T, false>;

template<typename T>
class MakeAllocator<T, true>;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein Typname.

*hasWeakReferenceSupport*<br/>
**true,** um Speicher für ein Objekt zuzuweisen, das schwache Verweise unterstützt; **false,** um Speicher für ein Objekt zuzuweisen, das keine schwachen Verweise unterstützt.

## <a name="remarks"></a>Bemerkungen

Reserviert Speicher für eine aktivierbare Klasse mit oder ohne schwache Verweisunterstützung.

Überschreiben `MakeAllocator` Sie die Klasse, um ein benutzerdefiniertes Speicherzuweisungsmodell zu implementieren.

`MakeAllocator`wird in der Regel verwendet, um Speicherverluste zu verhindern, wenn ein Objekt während der Konstruktion ausgelöst wird.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                                  | BESCHREIBUNG
----------------------------------------------------- | ----------------------------------------------------------------
[MakeAllocator::MakeAllocator](#makeallocator)        | Initialisiert eine neue Instanz der Klasse `MakeAllocator`.
[MakeAllocator::'MakeAllocator](#tilde-makeallocator) | Deinitialisiert die aktuelle Instanz `MakeAllocator` der Klasse.

### <a name="public-methods"></a>Öffentliche Methoden

Name                                 | BESCHREIBUNG
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[MakeAllocator::Allocate](#allocate) | Ordnet Speicher zu und ordnet `MakeAllocator` ihn dem aktuellen Objekt zu.
[MakeAllocator::Detach](#detach)     | Trennt den von der [Allocate-Methode](#allocate) zugewiesenen Speicher vom aktuellen `MakeAllocator` Objekt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`MakeAllocator`

## <a name="requirements"></a>Anforderungen

**Header:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="makeallocatorallocate"></a><a name="allocate"></a>MakeAllocator::Allocate

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
__forceinline void* Allocate();
```

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, ein Zeiger auf den zugewiesenen Speicher; andernfalls `nullptr`.

### <a name="remarks"></a>Bemerkungen

Ordnet Speicher zu und ordnet `MakeAllocator` ihn dem aktuellen Objekt zu.

Die Größe des zugewiesenen Speichers entspricht der `MakeAllocator` Größe des Typs, der durch den aktuellen Vorlagenparameter angegeben wird.

Ein Entwickler muss nur `Allocate()` die Methode überschreiben, um ein anderes Speicherzuweisungsmodell zu implementieren.

## <a name="makeallocatordetach"></a><a name="detach"></a>MakeAllocator::Detach

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>Bemerkungen

Trennt den von der [Allocate-Methode](#allocate) zugewiesenen Speicher vom aktuellen `MakeAllocator` Objekt.

Wenn Sie `Detach()`aufrufen, sind Sie für das `Allocate` Löschen des von der Methode bereitgestellten Speichers verantwortlich.

## <a name="makeallocatormakeallocator"></a><a name="makeallocator"></a>MakeAllocator::MakeAllocator

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
MakeAllocator();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert eine neue Instanz der Klasse `MakeAllocator`.

## <a name="makeallocatormakeallocator"></a><a name="tilde-makeallocator"></a>MakeAllocator::'MakeAllocator

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>Bemerkungen

Deinitialisiert die aktuelle Instanz `MakeAllocator` der Klasse.

Dieser Destruktor löscht bei Bedarf auch den zugrunde liegenden zugewiesenen Speicher.
