---
title: Platform::Object-Klasse
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Object::Object
- VCCORLIB/Platform::Object::Equals
- VCCORLIB/Platform::Object::GetHashCode
- VCCORLIB/Platform::Object::ReferenceEquals
- VCCORLIB/Platform::ToString
- VCCORLIB/Platform::GetType
helpviewer_keywords:
- Object class
ms.assetid: 709e84a8-0bff-471b-bc14-63e424080b5a
ms.openlocfilehash: 77313f8c4dcc87fa9de852afe2d60e614f8fc3a3
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423669"
---
# <a name="platformobject-class"></a>Platform::Object-Klasse

Stellt ein häufiges Verhalten für Verweis Klassen und Verweis Strukturen in Windows-Runtime-apps bereit. Alle Verweisklassen- und Referenzstruktur-Instanzen sind implizit konvertierbar in Platform::Object^ und können seine virtuelle ToString-Methode überschreiben.

## <a name="syntax"></a>Syntax

```cpp
public ref class Object : Object
```

### <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[Object:: Object](#ctor)|Initialisiert eine neue Instanz der Objektklasse.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[Object:: ist Gleichheits](#equals)|Ermittelt, ob das angegebene Objekt und das aktuelle Objekt gleich sind.|
|[Object:: GetHashCode](#gethashcode)|Gibt den Hashcode für diese Instanz zurück.|
|[Object:: referenceist](#referenceequals)|Stellt fest, ob die angegebenen Objekt-Instanzen dieselbe Instanz sind.|
|[ToString](#tostring)|Gibt eine Zeichenfolge zurück, die das aktuelle Objekt darstellt. Kann überschrieben werden.|
|[GetType](#gettype)|Ruft einen [Platform::Type](../cppcx/platform-type-class.md) ab, der die aktuelle Instanz beschreibt.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Object`

`Object`

### <a name="requirements"></a>Voraussetzungen

**Header:** vccorlib.h

**Namespace:** Platform

## <a name="equals"></a>Object:: Gleichheits Methode

Ermittelt, ob das angegebene Objekt und das aktuelle Objekt gleich sind.

### <a name="syntax"></a>Syntax

```cpp
bool Equals(
    Object^ obj
)
```

### <a name="parameters"></a>Parameter

*obj*<br/>
Das zu vergleichende Objekt.

### <a name="return-value"></a>Rückgabewert

**true** , wenn die Objekte gleich sind, andernfalls **false**.

## <a name="gethashcode"></a>Object:: GetHashCode-Methode

Gibt den `IUnknown`*-Identitätswert für diese Instanz zurück, wenn es sich um ein COM-Objekt handelt, bzw. einen berechneten Hashwert, wenn es kein COM-Objekt ist.

### <a name="syntax"></a>Syntax

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Rückgabewert

Ein numerischer Wert, der das Objekt eindeutig identifiziert.

### <a name="remarks"></a>Hinweise

Sie können GetHashCode zum Erstellen von Schlüsseln für Objekte in Zuordnungen verwenden. Sie können Hashcodes mithilfe von [Object:: gleich](#equals)vergleichen. Wenn der Codepfad äußerst wichtig ist und `GetHashCode` sowie `Equals` nicht schnell genug sind, können Sie auf die zugrunde liegende COM-Ebene herunter wechseln und systemeigene `IUnknown`-Zeigervergleiche ausführen.

## <a name="gettype"></a>Object:: GetType-Methode

Gibt ein [Platform:: Type](../cppcx/platform-type-class.md) -Objekt zurück, das den Lauf Zeittyp eines Objekts beschreibt.

### <a name="syntax"></a>Syntax

```cpp
Object::GetType();
```

### <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert

Ein [Platform:: Type](../cppcx/platform-type-class.md) -Objekt, das den Lauf Zeittyp des Objekts beschreibt.

### <a name="remarks"></a>Hinweise

Der statische [Typ:: gettypep](../cppcx/platform-type-class.md#gettypecode) kann verwendet werden, um einen [Platform:: TypeCode-Enumerationswert](../cppcx/platform-typecode-enumeration.md) zu erhalten, der den aktuellen Typ darstellt. Dies ist besonders für integrierte Typen hilfreich. Der Typcode für eine beliebige Verweis Klasse neben [Platform:: String](../cppcx/platform-string-class.md) ist Object (1).

Die [Windows:: UI:: XAML:: Interop:: tykame](/uwp/api/windows.ui.xaml.interop.typename) -Klasse wird in den Windows-APIs als sprachunabhängige Methode für die Übergabe von Typinformationen zwischen Windows-Komponenten und-Apps verwendet. Die T[Platform:: Type-Klasse](../cppcx/platform-type-class.md) verfügt über Operatoren zum Wechseln zwischen `Type` und `TypeName`.

Verwenden Sie den [typeid](../extensions/typeid-cpp-component-extensions.md) -Operator, um ein `Platform::Type` Objekt für einen Klassennamen zurückzugeben, z. b. beim Navigieren zwischen XAML-Seiten:

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

## <a name="ctor"></a>Object:: Object-Konstruktor

Initialisiert eine neue Instanz der Objektklasse.

### <a name="syntax"></a>Syntax

```cpp
public:Object();
```

## <a name="referenceequals"></a>Object:: referencegleichsmethode

Stellt fest, ob die angegebenen Objekt-Instanzen dieselbe Instanz sind.

### <a name="syntax"></a>Syntax

```cpp
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2);
```

### <a name="parameters"></a>Parameter

*obj1*<br/>
Das erste zu vergleichende Objekt.

*obj2*<br/>
Das zweite zu vergleichende Objekt.

### <a name="return-value"></a>Rückgabewert

**true** , wenn die beiden Objekte identisch sind. andernfalls **false**.

## <a name="tostring"></a>Object:: destring-MethodeC++(/CX)

Gibt eine Zeichenfolge zurück, die das aktuelle Objekt darstellt.

### <a name="syntax"></a>Syntax

```cpp
public:
virtual String^ ToString();
```

### <a name="return-value"></a>Rückgabewert

Eine Zeichenfolge, die das aktuelle Objekt darstellt. Sie können diese Methode überschreiben, um eine benutzerdefinierte Zeichenfolgenmeldung in der Verweisklasse oder Struktur bereitzustellen:

```cpp
public ref class Tree sealed
{
public:
    Tree(){}
    virtual Platform::String^ ToString() override
    {
      return "I’m a Tree";
    };
};
```

## <a name="see-also"></a>Siehe auch

[Platform-Namespace](platform-namespace-c-cx.md)<br/>
[Platform::Type-Klasse](platform-type-class.md)<br/>
[Typsystem](type-system-c-cx.md)
