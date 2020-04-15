---
title: EventTargetArray-Klasse
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::AddTail
- event/Microsoft::WRL::Details::EventTargetArray::Begin
- event/Microsoft::WRL::Details::EventTargetArray::End
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::Length
- event/Microsoft::WRL::Details::EventTargetArray::~EventTargetArray
helpviewer_keywords:
- Microsoft::WRL::Details::EventTargetArray class
- Microsoft::WRL::Details::EventTargetArray::AddTail method
- Microsoft::WRL::Details::EventTargetArray::Begin method
- Microsoft::WRL::Details::EventTargetArray::End method
- Microsoft::WRL::Details::EventTargetArray::EventTargetArray, constructor
- Microsoft::WRL::Details::EventTargetArray::Length method
- Microsoft::WRL::Details::EventTargetArray::~EventTargetArray, destructor
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
ms.openlocfilehash: 9ea8800aa22a6b5cae0b3342cf337786fb53fc76
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371497"
---
# <a name="eventtargetarray-class"></a>EventTargetArray-Klasse

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
class EventTargetArray :
    public Microsoft::WRL::RuntimeClass<
        Microsoft::WRL::RuntimeClassFlags<ClassicCom>,
        IUnknown
    >;
```

## <a name="remarks"></a>Bemerkungen

Stellt ein Array von Ereignishandlern dar.

Die Ereignishandler, die einem [EventSource-Objekt](eventsource-class.md) zugeordnet `EventTargetArray` sind, werden in einem geschützten Datenmember gespeichert.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                                           | BESCHREIBUNG
-------------------------------------------------------------- | -----------------------------------------------------------
[EventTargetArray::EventTargetArray](#eventtargetarray)        | Initialisiert eine neue Instanz der Klasse `EventTargetArray`.
[EventTargetArray::-EventTargetArray](#tilde-eventtargetarray) | Deinitialisiert die `EventTargetArray` aktuelle Klasse.

### <a name="public-methods"></a>Öffentliche Methoden

Name                                  | BESCHREIBUNG
------------------------------------- | ---------------------------------------------------------------------------------------
[EventTargetArray::AddTail](#addtail) | Fügt den angegebenen Ereignishandler an das Ende des internen Arrays von Ereignishandlern an.
[EventTargetArray::Begin](#begin)     | Ruft die Adresse des ersten Elements im internen Array von Ereignishandlern ab.
[EventTargetArray::Ende](#end)         | Ruft die Adresse des letzten Elements im internen Array von Ereignishandlern ab.
[EventTargetArray::Länge](#length)   | Ruft die aktuelle Anzahl von Elementen im internen Array von Ereignishandlern ab.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`EventTargetArray`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** event.h

**Namespace:** Microsoft::WRL::Details

## <a name="eventtargetarrayeventtargetarray"></a><a name="tilde-eventtargetarray"></a>EventTargetArray::-EventTargetArray

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
~EventTargetArray();
```

### <a name="remarks"></a>Bemerkungen

Deinitialisiert die `EventTargetArray` aktuelle Klasse.

## <a name="eventtargetarrayaddtail"></a><a name="addtail"></a>EventTargetArray::AddTail

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>Parameter

*Element*<br/>
Zeiger auf den anzuhängenden Ereignishandler.

### <a name="remarks"></a>Bemerkungen

Fügt den angegebenen Ereignishandler an das Ende des internen Arrays von Ereignishandlern an.

`AddTail()`ist dazu bestimmt, intern `EventSource` nur von der Klasse verwendet zu werden.

## <a name="eventtargetarraybegin"></a><a name="begin"></a>EventTargetArray::Begin

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
ComPtr<IUnknown>* Begin();
```

### <a name="return-value"></a>Rückgabewert

Die Adresse des ersten Elements im internen Array von Ereignishandlern.

### <a name="remarks"></a>Bemerkungen

Ruft die Adresse des ersten Elements im internen Array von Ereignishandlern ab.

## <a name="eventtargetarrayend"></a><a name="end"></a>EventTargetArray::Ende

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
ComPtr<IUnknown>* End();
```

### <a name="return-value"></a>Rückgabewert

Die Adresse des letzten Elements im internen Array von Ereignishandlern.

### <a name="remarks"></a>Bemerkungen

Ruft die Adresse des letzten Elements im internen Array von Ereignishandlern ab.

## <a name="eventtargetarrayeventtargetarray"></a><a name="eventtargetarray"></a>EventTargetArray::EventTargetArray

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
EventTargetArray(
   _Out_ HRESULT* hr,
   size_t items
);
```

### <a name="parameters"></a>Parameter

*Hr*<br/>
Nach diesen Konstruktoroperationen gibt der Parameter *hr* an, ob die Zuweisung des Arrays erfolgreich war oder fehlgeschlagen ist. Die folgende Liste zeigt die möglichen Werte für *hr*.

- S_OK<br/>
  Der Vorgang wurde erfolgreich ausgeführt.

- E_OUTOFMEMORY<br/>
  Speicher konnte für das Array nicht zugewiesen werden.

- S_FALSE<br/>
  *Parameterelemente* sind kleiner oder gleich Null.

*items*<br/>
Die Anzahl der zuzuweisenden Arrayelemente.

### <a name="remarks"></a>Bemerkungen

Initialisiert eine neue Instanz der Klasse `EventTargetArray`.

`EventTargetArray`wird verwendet, um ein Array von `EventSource` Ereignishandlern in einem Objekt zu beaufbewahren.

## <a name="eventtargetarraylength"></a><a name="length"></a>EventTargetArray::Länge

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
size_t Length();
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Anzahl von Elementen im internen Array von Ereignishandlern.

### <a name="remarks"></a>Bemerkungen

Ruft die aktuelle Anzahl von Elementen im internen Array von Ereignishandlern ab.
