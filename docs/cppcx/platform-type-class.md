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
ms.openlocfilehash: 2c73967d287ade86e2657af70592845d2cc2085e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87185033"
---
# <a name="platformtype-class"></a>Platform::Type-Klasse

Enthält Laufzeitinformationen über einen Typ, insbesondere einen Zeichenfolgennamen und einen Typecode. Wird durch Aufrufen von [Object:: GetType](../cppcx/platform-object-class.md#gettype) für ein beliebiges Objekt oder mithilfe des [typeid](../extensions/typeid-cpp-component-extensions.md) -Operators für einen Klassen-oder Struktur Namen abgerufen.

## <a name="syntax"></a>Syntax

```cpp
public ref class Platform::Type :
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable
```

### <a name="remarks"></a>Bemerkungen

Die- `Type` Klasse ist in Anwendungen nützlich, die die Verarbeitung mithilfe einer-oder-Anweisung leiten müssen **`if`** **`switch`** , die basierend auf dem Lauf Zeittyp eines Objekts verzweigt. Der Typcode, der die Kategorie eines Typs beschreibt, wird mithilfe der Member-Funktion [Type:: gettypeer Code](#gettypecode) abgerufen.

## <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|[Type::GetTypeCode-Methode](#gettypecode)|Gibt einen [Platform::TypeCode-Enumeration](../cppcx/platform-typecode-enumeration.md) -Wert für das Objekt zurück.|
|[Type:: destring-Methode](#tostring)|Gibt den Namen des Typs zurück, wie er in den Metadaten angegeben ist.|

## <a name="public-properties"></a>Öffentliche Eigenschaften

|||
|-|-|
|[Type:: FullName](#fullname)|Gibt eine [Platform::String-Klasse](../cppcx/platform-string-class.md)^ zurück, die den vollqualifizierten Namen des Typs darstellt, und verwendet . (Punkt) als Trennzeichen, nicht:: (Double-Doppelpunkt) – z `MyNamespace.MyClass` . b..|

## <a name="conversion-operators"></a>Konvertierungsoperatoren

|||
|-|-|
|[Operator Type ^](../cppcx/operator-type-hat.md)|Ermöglicht die Konvertierung von `Windows::UI::Xaml::Interop::TypeName` in `Platform::Type`.|
|[Operator Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)|Ermöglicht die Konvertierung von `Platform::Type` in `Windows::UI::Xaml::Interop::TypeName`.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Mindestens unterstützter Client:** Windows 8

**Mindestens unterstützter Server:** Windows Server 2012

**Namespace:** Platform

**Metadaten:** Platform. winmd

## <a name="typefullname-property"></a><a name="fullname"></a>Type:: FullName-Eigenschaft

Ruft den voll qualifizierten Namen des aktuellen Typs im Formular ab `Namespace.Type` .

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

## <a name="typegettypecode-method"></a><a name="gettypecode"></a>Type:: gettypeer Code-Methode

Ruft einen der eingebauten Typen aus der Kategorie der numerischen Typen ab.

### <a name="syntax"></a>Syntax

```cpp
Platform::TypeCode GetTypeCode();
```

### <a name="return-value"></a>Rückgabewert

Einer der Platform::TypeCode-Enumierationswerte.

### <a name="remarks"></a>Bemerkungen

Die Entsprechung der gettypeer Code ()-Member-Methode ist die- **`typeid`** Eigenschaft.

## <a name="typetostring-method"></a><a name="tostring"></a>Type:: destring-Methode

Ruft den Namen des Typs ab.

### <a name="syntax"></a>Syntax

```cpp
Platform::String^ ToString();
```

### <a name="return-value"></a>Rückgabewert

Ein Name des Typs, wie in den Metadaten angegeben.

## <a name="see-also"></a>Weitere Informationen

[Plattformnamespace](../cppcx/platform-namespace-c-cx.md)
