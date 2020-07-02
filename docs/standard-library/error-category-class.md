---
title: error_category-Klasse
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_category
- system_error/std::error_category::value_type
- system_error/std::error_category::default_error_condition
- system_error/std::error_category::equivalent
- system_error/std::error_category::message
- system_error/std::error_category::name
helpviewer_keywords:
- std::error_category
- std::error_category::value_type
- std::error_category::default_error_condition
- std::error_category::equivalent
- std::error_category::message
- std::error_category::name
ms.assetid: e0a71e14-852d-4905-acd6-5f8ed426706d
ms.openlocfilehash: 136320ba3be36ec20fc08e0d83b1ce3274ed08ff
ms.sourcegitcommit: 8fd49f8ac20457710ceb5403ca46fc73cb3f95f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85737560"
---
# <a name="error_category-class"></a>error_category-Klasse

Stellt die abstrakte, allgemeine Basis für Objekte dar, die eine Fehlercodekategorie beschreibt.

## <a name="syntax"></a>Syntax

```cpp
class error_category;

constexpr error_category() noexcept;
virtual ~error_category();
error_category(const error_category&) = delete
```

## <a name="remarks"></a>Hinweise

`error_category` wird von zwei vordefinierten Objekten implementiert: [generic_category](../standard-library/system-error-functions.md#generic_category) und [system_category](../standard-library/system-error-functions.md#system_category).

## <a name="members"></a>Member

### <a name="typedefs"></a>TypeDefs

|||
|-|-|
|[value_type](#value_type)|Ein Typ, der den gespeicherten Fehlercodewert darstellt.|

### <a name="functions"></a>Functions

|||
|-|-|
|[default_error_condition](#default_error_condition)|Speichert den Fehlercodewert für ein Fehlerbedingungsobjekt.|
|[entsprechen](#equivalent)|Gibt einen Wert zurück, der angibt, ob Fehlerobjekte gleichwertig sind.|
|[generic_category](#generic)||
|[Nachricht](#message)|Gibt den Namen des angegebenen Fehlercodes zurück.|
|[name](#name)|Gibt den Namen der Kategorie zurück.|
|[system_category](#system)||

### <a name="operators"></a>Operatoren

|||
|-|-|
|[Operator =](#op_as)||
|[Operator = =](#op_eq_eq)|Prüft auf Gleichheit zwischen `error_category`-Objekten.|
|[Operator! =](#op_neq)|Prüft auf Ungleichheit zwischen `error_category`-Objekten.|
|[Operator<](#op_lt)|Testet, ob das [error_category](../standard-library/error-category-class.md)-Objekt kleiner ist als das `error_category`-Objekt, das für den Vergleich übergeben wurde.|

## <a name="default_error_condition"></a><a name="default_error_condition"></a>default_error_condition

Speichert den Fehlercodewert für ein Fehlerbedingungsobjekt.

```cpp
virtual error_condition default_error_condition(int _Errval) const;
```

### <a name="parameters"></a>Parameter

`_Errval`\
Der Fehlercodewert, der in [error_condition](../standard-library/error-condition-class.md) gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt `error_condition(_Errval, *this)` zurück.

### <a name="remarks"></a>Hinweise

### <a name="equivalent"></a>Äquivalent in <a name="equivalent"></a>

Gibt einen Wert zurück, der angibt, ob Fehlerobjekte gleichwertig sind.

```cpp
virtual bool equivalent(value_type _Errval,
    const error_condition& _Cond) const;

virtual bool equivalent(const error_code& _Code,
    value_type _Errval) const;
```

#### <a name="parameters"></a>Parameter

*_Errval*\
Der zu vergleichende Fehlercodewert.

*_Cond*\
Das zu vergleichende [error_condition](../standard-library/error-condition-class.md)-Objekt.

*_Code*\
Das zu vergleichende [error_code](../standard-library/error-code-class.md)-Objekt.

#### <a name="return-value"></a>Rückgabewert

**true** , wenn Kategorie und Wert gleich sind. andernfalls **false**.

#### <a name="remarks"></a>Hinweise

Die erste Memberfunktion gibt `*this == _Cond.category() && _Cond.value() == _Errval` zurück.

Die zweite Memberfunktion gibt `*this == _Code.category() && _Code.value() == _Errval` zurück.

### <a name="generic_category"></a><a name="generic"></a>generic_category

```cpp
const error_category& generic_category();
```

### <a name="message"></a><a name="message"></a>Nachricht

Gibt den Namen des angegebenen Fehlercodes zurück.

```cpp
virtual string message(error_code::value_type val) const = 0;
```

#### <a name="parameters"></a>Parameter

*ster*\
Der zu beschreibende Fehlercodewert.

#### <a name="return-value"></a>Rückgabewert

Gibt einen beschreibenden Namen des Fehlercodes *Val* für die Kategorie zurück. Wenn der Fehlercode nicht erkannt wird, wird zurückgegeben `"unknown error"` .

#### <a name="remarks"></a>Hinweise

### <a name="name"></a><a name="name"></a>-Name

Gibt den Namen der Kategorie zurück.

```cpp
virtual const char *name() const = 0;
```

#### <a name="return-value"></a>Rückgabewert

Gibt den Namen der Kategorie als Bytezeichenfolge zurück, die mit null endet.

### <a name="operator"></a><a name="op_as"></a>Operator =

```cpp
error_category& operator=(const error_category&) = delete;
```

### <a name="operator"></a><a name="op_eq_eq"></a>Operator = =

Prüft auf Gleichheit zwischen `error_category`-Objekten.

```cpp
bool operator==(const error_category& right) const;
```

#### <a name="parameters"></a>Parameter

*Richting*\
Das Objekt, das auf Gleichheit getestet werden soll.

#### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Objekte gleich sind; **FALSE**, wenn die Objekte nicht gleich sind.

#### <a name="remarks"></a>Hinweise

Dieser Memberoperator gibt `this == &right` zurück.

### <a name="operator"></a><a name="op_neq"></a>Operator! =

Prüft auf Ungleichheit zwischen `error_category`-Objekten.

```cpp
bool operator!=(const error_category& right) const;
```

#### <a name="parameters"></a>Parameter

*Richting*\
Das Objekt, das auf Ungleichheit geprüft werden soll.

#### <a name="return-value"></a>Rückgabewert

**true** , wenn das `error_category` Objekt nicht gleich dem-Objekt ist, das `error_category` *Rechts*übermittelt wird; andernfalls **false**.

#### <a name="remarks"></a>Hinweise

Der Memberoperator gibt `(!*this == right)`zurück.

### <a name="operatorlt"></a><a name="op_lt"></a>KOM&lt;

Testet, ob das [error_category](../standard-library/error-category-class.md)-Objekt kleiner ist als das `error_category`-Objekt, das für den Vergleich übergeben wurde.

```cpp
bool operator<(const error_category& right) const;
```

#### <a name="parameters"></a>Parameter

*Richting*\
Das zu vergleichende `error_category`-Objekt.

#### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn das Objekt, das an `error_category` übergeben wird, kleiner ist als das an `error_category` übergebene Objekt; andernfalls **FALSE**.

#### <a name="remarks"></a>Hinweise

Der Memberoperator gibt `this < &right`zurück.

### <a name="system_category"></a><a name="system"></a>system_category

```cpp
const error_category& system_category();
```

### <a name="value_type"></a><a name="value_type"></a>value_type

Ein Typ, der den gespeicherten Fehlercodewert darstellt.

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>Hinweise

Diese Typdefinition ist ein Synonym für **int**.
