---
title: Platform::Type-Klasse
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Type::GetTypeCode
- VCCORLIB/Platform::Type::FullName
helpviewer_keywords:
- Platform::Type Class
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
ms.openlocfilehash: 7463a2518e6ec5cc84f59db05cfaf60e43eb9fde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322096"
---
# <a name="platformtype-class"></a>Platform::Type-Klasse

Enthält Laufzeitinformationen über einen Typ, insbesondere einen Zeichenfolgennamen und einen Typecode. Wird durch Aufrufen von [Object::GetType](../cppcx/platform-object-class.md#gettype) für ein beliebiges Objekt oder mithilfe des [typeid-Operators](../extensions/typeid-cpp-component-extensions.md) für einen Klassen- oder Strukturnamen abgerufen.

## <a name="syntax"></a>Syntax

```cpp
public ref class Platform::Type :
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable
```

### <a name="remarks"></a>Bemerkungen

Die `Type` -Klasse ist in Anwendungen nützlich, in denen die Verarbeitung über eine `if` - oder `switch` -Anweisung erfolgt, die sich je nach Laufzeittyp eines Objekts verzweigt. Der Typcode, der die Kategorie eines Typs beschreibt, wird mithilfe der [Memberfunktion Type::GetTypeCode](#gettypecode) abgerufen.

## <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|[Type::GetTypeCode-Methode](#gettypecode)|Gibt einen [Platform::TypeCode-Enumeration](../cppcx/platform-typecode-enumeration.md) -Wert für das Objekt zurück.|
|[Typ::ToString-Methode](#tostring)|Gibt den Namen des Typs zurück, wie in seinen Metadaten angegeben.|

## <a name="public-properties"></a>Öffentliche Eigenschaften

|||
|-|-|
|[Typ::FullName](#fullname)|Gibt eine [Platform::String-Klasse](../cppcx/platform-string-class.md)^ zurück, die den vollqualifizierten Namen des Typs darstellt, und verwendet . (Punkt) als Trennzeichen, nicht :: (Doppelpunkt) `MyNamespace.MyClass`– z. B. .|

## <a name="conversion-operators"></a>Konvertierungsoperatoren

|||
|-|-|
|[Operator Typ](../cppcx/operator-type-hat.md)|Ermöglicht die Konvertierung von `Windows::UI::Xaml::Interop::TypeName` in `Platform::Type`.|
|[Operator Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)|Ermöglicht die Konvertierung von `Platform::Type` in `Windows::UI::Xaml::Interop::TypeName`.|

### <a name="requirements"></a>Anforderungen

**Mindestens unterstützter Client:** Windows 8

**Minimal unterstützter Server:** Windows Server 2012

**Namespace:** Platform

**Metadaten:** platform.winmd

## <a name="typefullname-property"></a><a name="fullname"></a>Typ::FullName-Eigenschaft

Ruft den vollqualifizierten Namen des aktuellen Typs im Formular `Namespace.Type`ab.

### <a name="syntax"></a>Syntax

```cpp
String^ FullName();
```

### <a name="return-value"></a>Rückgabewert

Der Name des Typs.

### <a name="example"></a>Beispiel

```cpp
//  namespace is TestApp
MainPage::MainPage()
{
    InitializeComponent();
    Type^ t = this->GetType();
    auto s = t->FullName; // returns "TestApp.MainPage"
    auto s2 = t->ToString(); //also returns "TestApp.MainPage"
}
```

## <a name="typegettypecode-method"></a><a name="gettypecode"></a>Typ::GetTypeCode-Methode

Ruft einen der eingebauten Typen aus der Kategorie der numerischen Typen ab.

### <a name="syntax"></a>Syntax

```cpp
Platform::TypeCode GetTypeCode();
```

### <a name="return-value"></a>Rückgabewert

Einer der Platform::TypeCode-Enumierationswerte.

### <a name="remarks"></a>Bemerkungen

Das Äquivalent der GetTypeCode()-Membermethode ist die `typeid`-Eigenschaft.

## <a name="typetostring-method"></a><a name="tostring"></a>Typ::ToString-Methode

Ruft den Namen des Typs ab.

### <a name="syntax"></a>Syntax

```cpp
Platform::String^ ToString();
```

### <a name="return-value"></a>Rückgabewert

Ein Name des Typs, wie in seinen Metadaten angegeben.

## <a name="see-also"></a>Siehe auch

[Plattformnamespace](../cppcx/platform-namespace-c-cx.md)
