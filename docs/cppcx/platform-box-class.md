---
title: Platform::Box-Klasse
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
ms.openlocfilehash: 7484bcda3f05a8a9e56a33222d0630d4597e1219
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354757"
---
# <a name="platformbox-class"></a>Platform::Box-Klasse

Aktiviert einen Werttyp wie `Windows::Foundation::DateTime` oder einen skalaren Typ wie `int` , der in einem `Platform::Object` -Typ gespeichert wird. Es ist normalerweise nicht erforderlich, `Box` explizit zu verwenden, da das Boxing implizit geschieht, wenn Sie einen Werttyp in `Object^`umwandeln.

### <a name="syntax"></a>Syntax

```cpp
ref class Box abstract;
```

### <a name="requirements"></a>Anforderungen

**Header:** vccorlib.h

**Namespace:** Platform

### <a name="members"></a>Member

|Member|BESCHREIBUNG|
|------------|-----------------|
|[Feld](#ctor) | Erstellt eine `Box`, die einen Wert vom angegebenen Typ kapseln kann. |
|[Operator&lt;Box const T&gt;^](#box-const-t) | Ermöglicht Boxingkonvertierungen von einer `const`-Wertklasse `T` oder `enum`-Klasse `T` in `Box<T>`. |
|[Operator&lt;Box const volatile T&gt;^](#box-const-volatile-t) | Ermöglicht Boxingkonvertierungen von einer `const volatile`-Wertklasse `T` oder einem `enum`-Typ `T` in `Box<T>`. |
|[Operator&lt;Box T&gt;^](#box-t) | Ermöglicht Boxingkonvertierungen von einer `T`-Wertklasse in `Box<T>`. |
|[Operator&lt;Box volatile T&gt;^](#box-volatile-t) | Ermöglicht Boxingkonvertierungen von einer `volatile`-Wertklasse `T` oder einem `enum`-Typ `T` in `Box<T>`. |
|[Box::operator T](#t) | Ermöglicht Boxingkonvertierungen von einer `T`-Wertklasse oder `enum`-Klasse `T` in `Box<T>`. |
|[Value-Eigenschaft](#value) | Gibt den im `Box`-Objekt gekapselten Wert zurück. |

## <a name="boxbox-constructor"></a><a name="ctor"></a>Box::Box-Konstruktor

Erstellt eine `Box`, die einen Wert vom angegebenen Typ kapseln kann.

### <a name="syntax"></a>Syntax

```cpp
Box(T valueArg);
```

### <a name="parameters"></a>Parameter

*valueArg*<br/>
Der Typ des Werts, für den eine Boxingkonvertierung ausgeführt werden soll – beispielsweise `int`, `bool`, `float64`, `DateTime`.

## <a name="boxoperator-boxltconst-tgt-operator"></a><a name="box-const-t"></a>Box::operator&lt;Box&gt;const T - Operator

Ermöglicht Boxingkonvertierungen von einer `const`-Wertklasse `T` oder `enum`-Klasse `T` in `Box<T>`.

### <a name="syntax"></a>Syntax

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Eine Wertklasse, eine Wertstruktur oder ein Enumerationstyp. Schließt die integrierten Typen in den [Standardnamespace](../cppcx/default-namespace.md)ein.

### <a name="return-value"></a>Rückgabewert

Eine `Platform::Box<T>^` Instanz, die den ursprünglichen Wert darstellt, der in einer Verweisklasse geschachtelt wurde.

## <a name="boxoperator-boxltconst-volatile-tgt-operator"></a><a name="box-const-volatile-t"></a>Box::operator&lt;Box const&gt;volatile T - Operator

Ermöglicht Boxingkonvertierungen von einer `const volatile`-Wertklasse `T` oder einem `enum`-Typ `T` in `Box<T>`.

### <a name="syntax"></a>Syntax

```cpp
operator Box<const volatile T>^(const volatile T valueType);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein Enumerationstyp, eine Wertklasse oder eine Wertstruktur. Schließt die integrierten Typen in den [Standardnamespace](../cppcx/default-namespace.md)ein.

### <a name="return-value"></a>Rückgabewert

Eine `Platform::Box<T>^` Instanz, die den ursprünglichen Wert darstellt, der in einer Verweisklasse geschachtelt wurde.

## <a name="boxoperator-boxlttgt-operator"></a><a name="box-t"></a>Box::operator&lt;Box&gt;T - Operator

Ermöglicht Boxingkonvertierungen von einer `T`-Wertklasse in `Box<T>`.

### <a name="syntax"></a>Syntax

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein Enumerationstyp, eine Wertklasse oder eine Wertstruktur. Schließt die integrierten Typen in den [Standardnamespace](../cppcx/default-namespace.md)ein.

### <a name="return-value"></a>Rückgabewert

Eine `Platform::Box<T>^` Instanz, die den ursprünglichen Wert darstellt, der in einer Verweisklasse geschachtelt wurde.

## <a name="boxoperator-boxltvolatile-tgt-operator"></a><a name="box-volatile-t"></a>Box::operator&lt;Box&gt;volatile T - Operator

Ermöglicht Boxingkonvertierungen von einer `volatile`-Wertklasse `T` oder einem `enum`-Typ `T` in `Box<T>`.

### <a name="syntax"></a>Syntax

```cpp
operator Box<volatile T>^(volatile T valueType);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein Enumerationstyp, eine Wertklasse oder eine Wertstruktur. Schließt die integrierten Typen in den [Standardnamespace](../cppcx/default-namespace.md)ein.

### <a name="return-value"></a>Rückgabewert

Eine `Platform::Box<T>^` Instanz, die den ursprünglichen Wert darstellt, der in einer Verweisklasse geschachtelt wurde.

## <a name="boxoperator-t-operator"></a><a name="t"></a>Box::operator T Operator

Ermöglicht Boxingkonvertierungen von einer `T`-Wertklasse oder `enum`-Klasse `T` in `Box<T>`.

### <a name="syntax"></a>Syntax

```cpp
operator Box<T>^(T valueType);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein Enumerationstyp, eine Wertklasse oder eine Wertstruktur. Schließt die integrierten Typen in den [Standardnamespace](../cppcx/default-namespace.md)ein.

### <a name="return-value"></a>Rückgabewert

Eine `Platform::Box<T>^` Instanz, die den ursprünglichen Wert darstellt, der in einer Verweisklasse geschachtelt wurde.

## <a name="boxvalue-property"></a><a name="value"></a>Box::Value-Eigenschaft

Gibt den im `Box`-Objekt gekapselten Wert zurück.

### <a name="syntax"></a>Syntax

```cpp
virtual property T Value{
   T get();
}
```

### <a name="return-value"></a>Rückgabewert

Gibt den durch Boxing konvertierten Wert in dem Typ zurück, den er vor dem Boxing besaß.

## <a name="see-also"></a>Siehe auch

[Plattformnamespace](../cppcx/platform-namespace-c-cx.md)<br/>
[Boxing](../cppcx/boxing-c-cx.md)
