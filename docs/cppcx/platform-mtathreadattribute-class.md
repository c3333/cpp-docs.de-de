---
title: Platform::MTAThreadAttribute-Klasse
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::MTAThreadAttribute::Equals
- VCCORLIB/Platform::MTAThreadAttribute::GetHashCode
- VCCORLIB/Platform::MTAThreadAttribute::ToString
helpviewer_keywords:
- Platform::MTAThreadAttribute Class
ms.assetid: bfc546a7-4333-4407-85b4-4721565e1f44
ms.openlocfilehash: 700eeae226be48c1f6659d621f2f5c0ed397bb7f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213046"
---
# <a name="platformmtathreadattribute-class"></a>Platform::MTAThreadAttribute-Klasse

Legt Multithreaded Apartment (MTA) als Threadingmodell für Anwendungen fest.

## <a name="syntax"></a>Syntax

```
public ref class MTAThreadAttribute sealed : Attribute
```

### <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|BESCHREIBUNG|
|----------|-----------------|
|[Mtathleattributkonstruktor 1](#ctor) -Konstruktor|Initialisiert eine neue Instanz der Klasse.|

### <a name="public-methods"></a>Öffentliche Methoden

Das mtathlesattribute-Attribut erbt von der [Platform:: Object-Klasse](../cppcx/platform-object-class.md). „MTAThreadAttribute“ wird zudem überladen oder weist die folgenden Member auf:

|Name|BESCHREIBUNG|
|----------|-----------------|
|[MTAThreadAttribute::Equals](#equals)|Bestimmt, ob das angegebene Objekt gleich dem aktuellen Objekt ist.|
|[MTAThreadAttribute::GetHashCode](#gethashcode)|Gibt den Hashcode für diese Instanz zurück.|
|[MTAThreadAttribute::ToString](#tostring)|Gibt eine Zeichenfolge zurück, die das aktuelle Objekt darstellt.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Platform`

### <a name="requirements"></a>Requirements (Anforderungen)

**Metadaten:** Platform. winmd

**Namespace:** Platform

## <a name="mtathreadattribute-constructor"></a><a name="ctor"></a>Mtathleattribute-Konstruktor

Initialisiert eine neue Instanz der MTAThreadAttribute-Klasse.

### <a name="syntax"></a>Syntax

```cpp
public:MTAThreadAttribute();
```

## <a name="mtathreadattributeequals"></a><a name="equals"></a>Mtathlesattribute:: ist Gleichheits

Bestimmt, ob das angegebene Objekt gleich dem aktuellen Objekt ist.

### <a name="syntax"></a>Syntax

```cpp
public:virtual override bool Equals( Object^ obj );
```

### <a name="parameters"></a>Parameter

*obj*<br/>
Das zu vergleichende Objekt.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Objekte gleich sind. andernfalls **`false`** .

## <a name="mtathreadattributegethashcode"></a><a name="gethashcode"></a>Mtathlesattribute:: GetHashCode

Gibt den Hashcode für diese Instanz zurück.

### <a name="syntax"></a>Syntax

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Rückgabewert

Der Hashcode für diese Instanz.

## <a name="mtathreadattributetostring"></a><a name="tostring"></a>Mtathlesattribute::-Zeichenfolge

Gibt eine Zeichenfolge zurück, die das aktuelle Objekt darstellt.

### <a name="syntax"></a>Syntax

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>Rückgabewert

Eine Zeichenfolge, die das aktuelle Objekt darstellt.

## <a name="see-also"></a>Weitere Informationen

[Platform-Namespace](platform-namespace-c-cx.md)
