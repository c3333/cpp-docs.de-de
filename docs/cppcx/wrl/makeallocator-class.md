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
ms.openlocfilehash: 19d3ab294df8adc059424c97e5733ae9ebb75c9c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218376"
---
# <a name="makeallocator-class"></a>MakeAllocator-Klasse

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

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

*hasweakreferencesupport*<br/>
**`true`** So weisen Sie Speicher für ein Objekt zu, das schwache Verweise unterstützt **`false`**, um Speicher für ein Objekt zuzuweisen, das keine schwachen Verweise unterstützt.

## <a name="remarks"></a>Bemerkungen

Ordnet Speicher für eine aktivierbare Klasse mit oder ohne Unterstützung für schwache Verweise zu.

Überschreiben `MakeAllocator` Sie die-Klasse, um ein benutzerdefiniertes Speicher Belegungs Modell zu implementieren.

`MakeAllocator`wird normalerweise verwendet, um Speicher Verluste zu verhindern, wenn ein Objekt während der Erstellung auslöst.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                                  | BESCHREIBUNG
----------------------------------------------------- | ----------------------------------------------------------------
[Makezuweisung:: makezuweisung](#makeallocator)        | Initialisiert eine neue Instanz der `MakeAllocator`-Klasse.
[Makezuweisung:: ~ makezuweisung](#tilde-makeallocator) | Deinitialisiert die aktuelle Instanz der- `MakeAllocator` Klasse.

### <a name="public-methods"></a>Öffentliche Methoden

name                                 | BESCHREIBUNG
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[Makeallocator:: zuordnen](#allocate) | Ordnet Speicher zu und ordnet ihn dem aktuellen- `MakeAllocator` Objekt zu.
[Makezuweisung::D Etach](#detach)     | Trennt den von der Zuordnungs [Methode](#allocate) zugeordneten Arbeitsspeicher aus dem aktuellen- `MakeAllocator` Objekt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`MakeAllocator`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** implementiert. h

**Namespace:** Microsoft:: WRL::D etails

## <a name="makeallocatorallocate"></a><a name="allocate"></a>Makeallocator:: zuordnen

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
__forceinline void* Allocate();
```

### <a name="return-value"></a>Rückgabewert

Bei Erfolg ein Zeiger auf den zugeordneten Speicher. andernfalls **`nullptr`** .

### <a name="remarks"></a>Bemerkungen

Ordnet Speicher zu und ordnet ihn dem aktuellen- `MakeAllocator` Objekt zu.

Die Größe des zugeordneten Arbeitsspeichers entspricht der Größe des Typs, der durch den aktuellen `MakeAllocator` Vorlagen Parameter angegeben wird.

Ein Entwickler muss nur die- `Allocate()` Methode überschreiben, um ein anderes Speicher Belegungs Modell zu implementieren.

## <a name="makeallocatordetach"></a><a name="detach"></a>Makezuweisung::D Etach

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>Bemerkungen

Trennt den von der Zuordnungs [Methode](#allocate) zugeordneten Arbeitsspeicher aus dem aktuellen- `MakeAllocator` Objekt.

Wenn Sie anrufen `Detach()` , sind Sie dafür verantwortlich, den von der-Methode bereitgestellten Arbeitsspeicher zu löschen `Allocate` .

## <a name="makeallocatormakeallocator"></a><a name="makeallocator"></a>Makezuweisung:: makezuweisung

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
MakeAllocator();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert eine neue Instanz der `MakeAllocator`-Klasse.

## <a name="makeallocatormakeallocator"></a><a name="tilde-makeallocator"></a>Makezuweisung:: ~ makezuweisung

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>Bemerkungen

Deinitialisiert die aktuelle Instanz der- `MakeAllocator` Klasse.

Dieser Dekonstruktor löscht bei Bedarf auch den zugrunde liegenden zugeordneten Arbeitsspeicher.
