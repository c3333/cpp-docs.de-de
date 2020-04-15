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
ms.openlocfilehash: 8300ec484bdb58919ce8e450b706dd07c275ceee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363688"
---
# <a name="platformobject-class"></a>Platform::Object-Klasse

Stellt allgemeines Verhalten für Verweisklassen und Verweisstrukturen in Windows-Runtime-Apps bereit. Alle Verweisklassen- und Referenzstruktur-Instanzen sind implizit konvertierbar in Platform::Object^ und können seine virtuelle ToString-Methode überschreiben.

## <a name="syntax"></a>Syntax

```cpp
public ref class Object : Object
```

### <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Object::Object](#ctor)|Initialisiert eine neue Instanz der Objektklasse.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Object::Equals](#equals)|Bestimmt, ob das angegebene Objekt gleich dem aktuellen Objekt ist.|
|[Object::GetHashCode](#gethashcode)|Gibt den Hashcode für diese Instanz zurück.|
|[Object::ReferenceEquals](#referenceequals)|Stellt fest, ob die angegebenen Objekt-Instanzen dieselbe Instanz sind.|
|[ToString](#tostring)|Gibt eine Zeichenfolge zurück, die das aktuelle Objekt darstellt. Kann überschrieben werden.|
|[GetType](#gettype)|Ruft einen [Platform::Type](../cppcx/platform-type-class.md) ab, der die aktuelle Instanz beschreibt.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Object`

`Object`

### <a name="requirements"></a>Anforderungen

**Header:** vccorlib.h

**Namespace:** Platform

## <a name="objectequals-method"></a><a name="equals"></a>Object::Equals-Methode

Bestimmt, ob das angegebene Objekt gleich dem aktuellen Objekt ist.

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

**true,** wenn die Objekte gleich sind, andernfalls **false**.

## <a name="objectgethashcode-method"></a><a name="gethashcode"></a>Object::GetHashCode-Methode

Gibt den `IUnknown`*-Identitätswert für diese Instanz zurück, wenn es sich um ein COM-Objekt handelt, bzw. einen berechneten Hashwert, wenn es kein COM-Objekt ist.

### <a name="syntax"></a>Syntax

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Rückgabewert

Ein numerischer Wert, der das Objekt eindeutig identifiziert.

### <a name="remarks"></a>Bemerkungen

Sie können GetHashCode zum Erstellen von Schlüsseln für Objekte in Zuordnungen verwenden. Sie können Hashcodes mit [Object::Equals](#equals)vergleichen. Wenn der Codepfad äußerst wichtig ist und `GetHashCode` sowie `Equals` nicht schnell genug sind, können Sie auf die zugrunde liegende COM-Ebene herunter wechseln und systemeigene `IUnknown`-Zeigervergleiche ausführen.

## <a name="objectgettype-method"></a><a name="gettype"></a>Object::GetType-Methode

Gibt ein [Platform::Type-Objekt](../cppcx/platform-type-class.md) zurück, das den Laufzeittyp eines Objekts beschreibt.

### <a name="syntax"></a>Syntax

```cpp
Object::GetType();
```

### <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert

Ein [Platform::Type-Objekt,](../cppcx/platform-type-class.md) das den Laufzeittyp des Objekts beschreibt.

### <a name="remarks"></a>Bemerkungen

Der statische [Type::GetTypeCode](../cppcx/platform-type-class.md#gettypecode) kann verwendet werden, um einen [Platform::TypeCode Enumeration-Wert](../cppcx/platform-typecode-enumeration.md) abzuerhalten, der den aktuellen Typ darstellt. Dies ist besonders für integrierte Typen hilfreich. Der Typcode für jede Ref-Klasse außer [Platform::String](../cppcx/platform-string-class.md) ist Objekt (1).

Die [Windows::UI::Xaml::Interop::TypeName-Klasse](/uwp/api/windows.ui.xaml.interop.typename) wird in den Windows-APIs als sprachunabhängige Möglichkeit zum Übergeben von Typinformationen zwischen Windows-Komponenten und -Apps verwendet. Die[T-Plattform::Type-Klasse](../cppcx/platform-type-class.md) verfügt `Type` über `TypeName`Operatoren zum Konvertieren zwischen und .

Verwenden Sie den [typeid-Operator,](../extensions/typeid-cpp-component-extensions.md) um ein `Platform::Type` Objekt für einen Klassennamen zurückzugeben, z. B. beim Navigieren zwischen XAML-Seiten:

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

## <a name="objectobject-constructor"></a><a name="ctor"></a>Objekt::Objektkonstruktor

Initialisiert eine neue Instanz der Objektklasse.

### <a name="syntax"></a>Syntax

```cpp
public:Object();
```

## <a name="objectreferenceequals-method"></a><a name="referenceequals"></a>Object::ReferenceEquals-Methode

Stellt fest, ob die angegebenen Objekt-Instanzen dieselbe Instanz sind.

### <a name="syntax"></a>Syntax

```cpp
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2);
```

### <a name="parameters"></a>Parameter

*obj1*<br/>
Das erste der zu vergleichenden Objekte.

*obj2*<br/>
Das zweite der zu vergleichenden Objekte.

### <a name="return-value"></a>Rückgabewert

**true,** wenn die beiden Objekte identisch sind; andernfalls **false**.

## <a name="objecttostring-method-ccx"></a><a name="tostring"></a>Objekt::ToString-Methode (C++/CX)

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

[Plattform-Namespace](platform-namespace-c-cx.md)<br/>
[Plattform::Typklasse](platform-type-class.md)<br/>
[Typensystem](type-system-c-cx.md)
