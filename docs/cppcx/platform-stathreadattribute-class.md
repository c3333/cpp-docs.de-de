---
title: Platform::STAThreadAttribute-Klasse
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Platform
- COLLECTION/Platform::Platform::STAThreadAttribute constructor 1
- COLLECTION/Platform::Platform::STAThreadAttribute::Equals
- COLLECTION/Platform::Platform::STAThreadAttribute::GetHashCode
- COLLECTION/Platform::Platform::STAThreadAttribute::ToString
helpviewer_keywords:
- Platform::STAThreadAttribute Class
ms.assetid: f97960fc-e673-4d9e-910a-54c8415411c4
ms.openlocfilehash: 6a8220d8cddca29e621b21fc56966efdb42cb32e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213020"
---
# <a name="platformstathreadattribute-class"></a>Platform::STAThreadAttribute-Klasse

Legt Singlethreaded Apartment (STA) als Threadingmodell für Anwendungen fest.

## <a name="syntax"></a>Syntax

```
public ref class STAThreadAttribute sealed : Attribute
```

### <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|BESCHREIBUNG|
|----------|-----------------|
|[STAThreadAttribute-Konstruktor 1](#ctor)|Initialisiert eine neue Instanz der Klasse.|

### <a name="public-methods"></a>Öffentliche Methoden

Das STAThreadAttribute-Attribut erbt von der [Platform:: Object-Klasse](../cppcx/platform-object-class.md). „STAThreadAttribute“ wird zudem überladen oder weist die folgenden Member auf:

|Name|BESCHREIBUNG|
|----------|-----------------|
|[STAThreadAttribute::Equals](#equals)|Bestimmt, ob das angegebene Objekt gleich dem aktuellen Objekt ist.|
|[STAThreadAttribute::GetHashCode](#gethashcode)|Gibt den Hashcode für diese Instanz zurück.|
|[STAThreadAttribute::ToString](#tostring)|Gibt eine Zeichenfolge zurück, die das aktuelle Objekt darstellt.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Platform`

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** collection.h

**Namespace:** Platform

## <a name="stathreadattribute-constructor"></a><a name="ctor"></a> STAThreadAttribute constructor

Initialisiert eine neue Instanz der STAThreadAttribute-Klasse.

### <a name="syntax"></a>Syntax

```cpp
public:STAThreadAttribute();
```

## <a name="stathreadattributeequals"></a><a name="equals"></a>STAThreadAttribute:: ist Gleichheits

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

## <a name="stathreadattributegethashcode"></a><a name="gethashcode"></a>STAThreadAttribute:: GetHashCode

Gibt den Hashcode für diese Instanz zurück.

### <a name="syntax"></a>Syntax

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Rückgabewert

Der Hashcode für diese Instanz.

## <a name="stathreadattributetostring"></a><a name="tostring"></a>STAThreadAttribute::-Zeichenfolge

Gibt eine Zeichenfolge zurück, die das aktuelle Objekt darstellt.

### <a name="syntax"></a>Syntax

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>Rückgabewert

Eine Zeichenfolge, die das aktuelle Objekt darstellt.

## <a name="see-also"></a>Weitere Informationen

[Platform-Namespace](platform-namespace-c-cx.md)
