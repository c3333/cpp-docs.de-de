---
title: WeakReference-Klasse
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::Resolve
- implements/Microsoft::WRL::Details::WeakReference::SetUnknown
- implements/Microsoft::WRL::Details::WeakReference::~WeakReference
- implements/Microsoft::WRL::Details::WeakReference::WeakReference
helpviewer_keywords:
- Microsoft::WRL::Details::WeakReference class
- Microsoft::WRL::Details::WeakReference::DecrementStrongReference method
- Microsoft::WRL::Details::WeakReference::IncrementStrongReference method
- Microsoft::WRL::Details::WeakReference::Resolve method
- Microsoft::WRL::Details::WeakReference::SetUnknown method
- Microsoft::WRL::Details::WeakReference::~WeakReference, destructor
- Microsoft::WRL::Details::WeakReference::WeakReference, constructor
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
ms.openlocfilehash: 9a367a61a029abe1be599b1e262e279402149ccd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220456"
---
# <a name="weakreference-class"></a>WeakReference-Klasse

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
class WeakReference;
```

## <a name="remarks"></a>Bemerkungen

Stellt einen *schwachen Verweis* dar, der mit dem Windows-Runtime oder dem klassischen com verwendet werden kann. Ein schwacher Verweis repräsentiert ein Objekt, auf das möglicherweise zugegriffen werden kann.

Ein `WeakReference` -Objekt verwaltet einen *starken Verweis*, bei dem es sich um einen Zeiger auf ein-Objekt handelt, und einen *starken Verweis Zähler*, bei dem es sich um die Anzahl der Kopien des starken Verweises handelt, die von der-Methode verteilt wurden `Resolve()` . Obwohl der starke Verweis Zähler ungleich NULL ist, ist der starke Verweis gültig, und auf das Objekt kann zugegriffen werden. Wenn der starke Verweis Zähler 0 (null) ist, ist der starke Verweis ungültig, und auf das Objekt kann nicht zugegriffen werden.

Ein- `WeakReference` Objekt wird normalerweise verwendet, um ein Objekt darzustellen, dessen vorhanden sein durch einen externen Thread oder eine externe Anwendung gesteuert wird. Erstellen Sie z. b `WeakReference` . ein-Objekt aus einem Verweis auf ein Datei Objekt. Solange die Datei geöffnet ist, ist der starke Verweis gültig. Wenn die Datei aber geschlossen wird, wird der starke Verweis ungültig.

Die `WeakReference` Methoden sind Thread sicher.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                                  | BESCHREIBUNG
----------------------------------------------------- | ---------------------------------------------------------------------------
[WeakReference:: WeakReference](#weakreference)        | Initialisiert eine neue Instanz der `WeakReference`-Klasse.
[WeakReference:: ~ WeakReference](#tilde-weakreference) | Deinitialisiert (zerstört) die aktuelle Instanz der- `WeakReference` Klasse.

### <a name="public-methods"></a>Öffentliche Methoden

name                                                                 | BESCHREIBUNG
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[WeakReference::D ecrementstrongreferenzierung](#decrementstrongreference) | Verringert den starken Verweis Zähler des aktuellen- `WeakReference` Objekts.
[WeakReference:: incrementstrongreferenzierung](#incrementstrongreference) | Erhöht den starken Verweis Zähler des aktuellen- `WeakReference` Objekts.
[WeakReference:: Resolve](#resolve)                                   | Legt den angegebenen Zeiger auf den aktuellen starken Verweis Wert fest, wenn der starke Verweis Zähler ungleich 0 (null) ist.
[WeakReference:: stunknown](#setunknown)                             | Legt den starken Verweis des aktuellen- `WeakReference` Objekts auf den angegebenen Schnittstellen Zeiger fest.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`WeakReference`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** implementiert. h

**Namespace:** Microsoft:: WRL::D etails

## <a name="weakreferenceweakreference"></a><a name="tilde-weakreference"></a>WeakReference:: ~ WeakReference

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Deinitialisiert die aktuelle Instanz der- `WeakReference` Klasse.

## <a name="weakreferencedecrementstrongreference"></a><a name="decrementstrongreference"></a>WeakReference::D ecrementstrongreferenzierung

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>Bemerkungen

Verringert den starken Verweis Zähler des aktuellen- `WeakReference` Objekts.

Wenn der starke Verweis Zähler Null ist, wird der starke Verweis auf festgelegt **`nullptr`** .

### <a name="return-value"></a>Rückgabewert

Der dekrementierte starke Verweis Zähler.

## <a name="weakreferenceincrementstrongreference"></a><a name="incrementstrongreference"></a>WeakReference:: incrementstrongreferenzierung

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>Rückgabewert

Der inkrementierte starke Verweis Zähler.

### <a name="remarks"></a>Bemerkungen

Erhöht den starken Verweis Zähler des aktuellen- `WeakReference` Objekts.

## <a name="weakreferenceresolve"></a><a name="resolve"></a>WeakReference:: Resolve

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
STDMETHOD(Resolve)
   (REFIID riid,
   _Deref_out_opt_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>Parameter

*riid*<br/>
Eine Schnittstellen-ID.

*ppvObject*<br/>
Wenn dieser Vorgang abgeschlossen ist, eine Kopie des aktuellen starken Verweises, wenn der starke Verweis Zähler ungleich 0 (null) ist.

### <a name="return-value"></a>Rückgabewert

- S_OK, wenn dieser Vorgang erfolgreich ist und der starke Verweis Zähler 0 (null) ist. Der *ppvobject* -Parameter ist auf festgelegt **`nullptr`** .

- S_OK, wenn dieser Vorgang erfolgreich ist und der starke Verweis Zähler ungleich 0 (null) ist. Der *ppvobject* -Parameter wird auf den starken Verweis festgelegt.

- Andernfalls ein HRESULT, das den Grund für den fehlgeschlagenen Vorgang angibt.

### <a name="remarks"></a>Bemerkungen

Legt den angegebenen Zeiger auf den aktuellen starken Verweis Wert fest, wenn der starke Verweis Zähler ungleich 0 (null) ist.

## <a name="weakreferencesetunknown"></a><a name="setunknown"></a>WeakReference:: stunknown

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>Parameter

*ttenes*<br/>
Ein Zeiger auf die- `IUnknown` Schnittstelle eines Objekts.

### <a name="remarks"></a>Bemerkungen

Legt den starken Verweis des aktuellen- `WeakReference` Objekts auf den angegebenen Schnittstellen Zeiger fest.

## <a name="weakreferenceweakreference"></a><a name="weakreference"></a>WeakReference:: WeakReference

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
WeakReference();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert eine neue Instanz der `WeakReference`-Klasse.

Der starke Verweis Zeiger für das- `WeakReference` Objekt wird mit initialisiert **`nullptr`** , und der starke Verweis Zähler wird auf 1 initialisiert.
