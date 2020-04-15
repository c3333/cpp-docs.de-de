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
ms.openlocfilehash: a80c0ec14da2a955a95ac84dd3975212ef20ae04
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374222"
---
# <a name="weakreference-class"></a>WeakReference-Klasse

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
class WeakReference;
```

## <a name="remarks"></a>Bemerkungen

Stellt einen *schwachen Verweis* dar, der mit der Windows-Runtime oder der klassischen COM verwendet werden kann. Ein schwacher Verweis repräsentiert ein Objekt, auf das möglicherweise zugegriffen werden kann.

Ein `WeakReference` Objekt verwaltet einen *starken Verweis*, der ein Zeiger auf ein Objekt ist, und eine *starke Verweisanzahl* `Resolve()` , d. h. die Anzahl der Kopien des starken Verweises, die von der Methode verteilt wurden. Während die starke Verweisanzahl ungleich Null ist, ist der starke Verweis gültig, und auf das Objekt kann zugegriffen werden. Wenn die starke Verweisanzahl Null wird, ist der starke Verweis ungültig, und auf das Objekt kann nicht zugegriffen werden.

Ein `WeakReference` Objekt wird in der Regel verwendet, um ein Objekt darzustellen, dessen Vorhandensein von einem externen Thread oder einer anwendung gesteuert wird. Erstellen Sie beispielsweise `WeakReference` ein Objekt aus einem Verweis auf ein Dateiobjekt. Solange die Datei geöffnet ist, ist der starke Verweis gültig. Wenn die Datei aber geschlossen wird, wird der starke Verweis ungültig.

Die `WeakReference` Methoden sind threadsicher.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                                  | BESCHREIBUNG
----------------------------------------------------- | ---------------------------------------------------------------------------
[WeakReference::WeakReference](#weakreference)        | Initialisiert eine neue Instanz der Klasse `WeakReference`.
[WeakReference::-Schwachreferenz](#tilde-weakreference) | Deinitialisiert (zerstört) die aktuelle Instanz `WeakReference` der Klasse.

### <a name="public-methods"></a>Öffentliche Methoden

Name                                                                 | BESCHREIBUNG
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[SchwachReferenz::DecrementStrongReference](#decrementstrongreference) | Dekrementiert die starke Referenzanzahl des aktuellen `WeakReference` Objekts.
[WeakReference::IncrementStrongReference](#incrementstrongreference) | Erhöht die starke Referenzanzahl `WeakReference` des aktuellen Objekts.
[WeakReference::Auflösen](#resolve)                                   | Legt den angegebenen Zeiger auf den aktuellen starken Referenzwert fest, wenn die starke Referenzanzahl ungleich Null ist.
[WeakReference::SetUnknown](#setunknown)                             | Legt den starken Verweis `WeakReference` des aktuellen Objekts auf den angegebenen Schnittstellenzeiger fest.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`WeakReference`

## <a name="requirements"></a>Anforderungen

**Header:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="weakreferenceweakreference"></a><a name="tilde-weakreference"></a>WeakReference::-Schwachreferenz

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Deinitialisiert die aktuelle Instanz `WeakReference` der Klasse.

## <a name="weakreferencedecrementstrongreference"></a><a name="decrementstrongreference"></a>SchwachReferenz::DecrementStrongReference

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>Bemerkungen

Dekrementiert die starke Referenzanzahl des aktuellen `WeakReference` Objekts.

Wenn die starke Referenzanzahl Null wird, `nullptr`wird der starke Verweis auf festgelegt.

### <a name="return-value"></a>Rückgabewert

Die dekrementierte starke Referenzanzahl.

## <a name="weakreferenceincrementstrongreference"></a><a name="incrementstrongreference"></a>WeakReference::IncrementStrongReference

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>Rückgabewert

Die inkrementierte starke Referenzanzahl.

### <a name="remarks"></a>Bemerkungen

Erhöht die starke Referenzanzahl `WeakReference` des aktuellen Objekts.

## <a name="weakreferenceresolve"></a><a name="resolve"></a>WeakReference::Auflösen

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

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
Wenn dieser Vorgang abgeschlossen ist, wird eine Kopie des aktuellen starken Verweises kopiert, wenn die starke Referenzanzahl ungleich Null ist.

### <a name="return-value"></a>Rückgabewert

- S_OK, wenn dieser Vorgang erfolgreich ist und die starke Referenzanzahl Null ist. Der Parameter *ppvObject* `nullptr`ist auf festgelegt.

- S_OK, wenn dieser Vorgang erfolgreich ist und die starke Referenzanzahl ungleich Null ist. Der *parameter ppvObject* wird auf den starken Verweis gesetzt.

- Andernfalls ein HRESULT, das den Grund für den Fehler in diesem Vorgang angibt.

### <a name="remarks"></a>Bemerkungen

Legt den angegebenen Zeiger auf den aktuellen starken Referenzwert fest, wenn die starke Referenzanzahl ungleich Null ist.

## <a name="weakreferencesetunknown"></a><a name="setunknown"></a>WeakReference::SetUnknown

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>Parameter

*Unk*<br/>
Ein Zeiger auf `IUnknown` die Schnittstelle eines Objekts.

### <a name="remarks"></a>Bemerkungen

Legt den starken Verweis `WeakReference` des aktuellen Objekts auf den angegebenen Schnittstellenzeiger fest.

## <a name="weakreferenceweakreference"></a><a name="weakreference"></a>WeakReference::WeakReference

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
WeakReference();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert eine neue Instanz der Klasse `WeakReference`.

Der starke Referenzzeiger `WeakReference` für das Objekt `nullptr`wird initialisiert auf , und die starke Verweisanzahl wird auf 1 initialisiert.
