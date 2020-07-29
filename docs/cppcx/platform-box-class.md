---
title: Platform::Box-Klasse
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
ms.openlocfilehash: 6afc12dbc3f6980bb7fd42d7f0a8fdc9e6d0e284
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232169"
---
# <a name="platformbox-class"></a>Platform::Box-Klasse

Aktiviert einen Werttyp wie `Windows::Foundation::DateTime` oder einen skalaren Typ wie **`int`** , der in einem-Typ gespeichert werden soll `Platform::Object` . Es ist normalerweise nicht erforderlich, `Box` explizit zu verwenden, da das Boxing implizit geschieht, wenn Sie einen Werttyp in `Object^`umwandeln.

### <a name="syntax"></a>Syntax

```cpp
ref class Box abstract;
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** vccorlib.h

**Namespace:** Platform

### <a name="members"></a>Member

|Member|Beschreibung|
|------------|-----------------|
|[Feld](#ctor) | Erstellt eine `Box`, die einen Wert vom angegebenen Typ kapseln kann. |
|[Operator Feldkonstante &lt; T&gt;^](#box-const-t) | Ermöglicht Boxingkonvertierungen von einer **`const`** Wert Klasse `T` oder- **`enum`** Klasse `T` in `Box<T>` . |
|[Operator Box Konstante " &lt; volatile"&gt;^](#box-const-volatile-t) | Aktiviert Boxingkonvertierungen von einer **`const volatile`** Wert Klasse `T` oder einem **`enum`** Typ `T` in `Box<T>` . |
|[Operator Box &lt; T&gt;^](#box-t) | Ermöglicht Boxingkonvertierungen von einer `T`-Wertklasse in `Box<T>`. |
|[Operator Box &lt; volatile T&gt;^](#box-volatile-t) | Aktiviert Boxingkonvertierungen von einer **`volatile`** Wert Klasse `T` oder einem **`enum`** Typ `T` in `Box<T>` . |
|[Box:: Operator T](#t) | Ermöglicht Boxingkonvertierungen von einer Wert Klasse `T` oder- **`enum`** Klasse `T` in `Box<T>` . |
|[Value-Eigenschaft](#value) | Gibt den im `Box`-Objekt gekapselten Wert zurück. |

## <a name="boxbox-constructor"></a><a name="ctor"></a>Box:: Box-Konstruktor

Erstellt eine `Box`, die einen Wert vom angegebenen Typ kapseln kann.

### <a name="syntax"></a>Syntax

```cpp
Box(T valueArg);
```

### <a name="parameters"></a>Parameter

*valuearg*<br/>
Der Typ des Werts, der gekapselt werden soll, z. –.,, **`int`** **`bool`** `float64` , `DateTime` .

## <a name="boxoperator-boxltconst-tgt-operator"></a><a name="box-const-t"></a>Box:: Operator Box-Operator (Operator) &lt; &gt;

Ermöglicht Boxingkonvertierungen von einer **`const`** Wert Klasse `T` oder- **`enum`** Klasse `T` in `Box<T>` .

### <a name="syntax"></a>Syntax

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Eine Wertklasse, eine Wertstruktur oder ein Enumerationstyp. Schließt die integrierten Typen in den [Standard Namespace](../cppcx/default-namespace.md)ein.

### <a name="return-value"></a>Rückgabewert

Eine- `Platform::Box<T>^` Instanz, die den ursprünglichen Wert darstellt, der in einer Verweis Klasse gekapselt ist.

## <a name="boxoperator-boxltconst-volatile-tgt-operator"></a><a name="box-const-volatile-t"></a>Box:: Operator Box-Operator (Operator) &lt; Konstanten Operator (Operator) &gt;

Aktiviert Boxingkonvertierungen von einer **`const volatile`** Wert Klasse `T` oder einem **`enum`** Typ `T` in `Box<T>` .

### <a name="syntax"></a>Syntax

```cpp
operator Box<const volatile T>^(const volatile T valueType);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein Enumerationstyp, eine Wertklasse oder eine Wertstruktur. Schließt die integrierten Typen in den [Standard Namespace](../cppcx/default-namespace.md)ein.

### <a name="return-value"></a>Rückgabewert

Eine- `Platform::Box<T>^` Instanz, die den ursprünglichen Wert darstellt, der in einer Verweis Klasse gekapselt ist.

## <a name="boxoperator-boxlttgt-operator"></a><a name="box-t"></a>Box:: Operator Box &lt; T &gt; ^-Operator

Ermöglicht Boxingkonvertierungen von einer `T`-Wertklasse in `Box<T>`.

### <a name="syntax"></a>Syntax

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein Enumerationstyp, eine Wertklasse oder eine Wertstruktur. Schließt die integrierten Typen in den [Standard Namespace](../cppcx/default-namespace.md)ein.

### <a name="return-value"></a>Rückgabewert

Eine- `Platform::Box<T>^` Instanz, die den ursprünglichen Wert darstellt, der in einer Verweis Klasse gekapselt ist.

## <a name="boxoperator-boxltvolatile-tgt-operator"></a><a name="box-volatile-t"></a>Box:: Operator Box &lt; volatile T &gt; ^-Operator

Aktiviert Boxingkonvertierungen von einer **`volatile`** Wert Klasse `T` oder einem **`enum`** Typ `T` in `Box<T>` .

### <a name="syntax"></a>Syntax

```cpp
operator Box<volatile T>^(volatile T valueType);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein Enumerationstyp, eine Wertklasse oder eine Wertstruktur. Schließt die integrierten Typen in den [Standard Namespace](../cppcx/default-namespace.md)ein.

### <a name="return-value"></a>Rückgabewert

Eine- `Platform::Box<T>^` Instanz, die den ursprünglichen Wert darstellt, der in einer Verweis Klasse gekapselt ist.

## <a name="boxoperator-t-operator"></a><a name="t"></a>Box:: Operator T-Operator

Ermöglicht Boxingkonvertierungen von einer Wert Klasse `T` oder- **`enum`** Klasse `T` in `Box<T>` .

### <a name="syntax"></a>Syntax

```cpp
operator Box<T>^(T valueType);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein Enumerationstyp, eine Wertklasse oder eine Wertstruktur. Schließt die integrierten Typen in den [Standard Namespace](../cppcx/default-namespace.md)ein.

### <a name="return-value"></a>Rückgabewert

Eine- `Platform::Box<T>^` Instanz, die den ursprünglichen Wert darstellt, der in einer Verweis Klasse gekapselt ist.

## <a name="boxvalue-property"></a><a name="value"></a>Box:: Value-Eigenschaft

Gibt den im `Box`-Objekt gekapselten Wert zurück.

### <a name="syntax"></a>Syntax

```cpp
virtual property T Value{
   T get();
}
```

### <a name="return-value"></a>Rückgabewert

Gibt den durch Boxing konvertierten Wert in dem Typ zurück, den er vor dem Boxing besaß.

## <a name="see-also"></a>Weitere Informationen

[Plattformnamespace](../cppcx/platform-namespace-c-cx.md)<br/>
[Boxing](../cppcx/boxing-c-cx.md)
