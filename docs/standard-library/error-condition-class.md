---
title: error_condition-Klasse
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_condition
- system_error/std::error_condition::value_type
- system_error/std::error_condition::assign
- system_error/std::error_condition::category
- system_error/std::error_condition::clear
- system_error/std::error_condition::message
- system_error/std::error_condition::operator bool
helpviewer_keywords:
- std::error_condition
- std::error_condition::value_type
- std::error_condition::assign
- std::error_condition::category
- std::error_condition::clear
- std::error_condition::message
ms.assetid: 6690f481-97c9-4554-a0ff-851dc96b7a06
ms.openlocfilehash: c63676e7bdf5ce1547b4feae16c7899ace545ad2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203363"
---
# <a name="error_condition-class"></a>error_condition-Klasse

Stellt benutzerdefinierte Fehlercodes dar.

## <a name="syntax"></a>Syntax

```cpp
class error_condition;
```

## <a name="remarks"></a>Bemerkungen

Ein Objekt vom Typ `error_condition` enthält einen Fehlercodewert und einen Zeiger auf ein Objekt, das eine [category (Kategorie)](../standard-library/error-category-class.md) von Fehlercodes darstellt, die für berichtete benutzerdefinierte Fehlercodes verwendet werden.

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|||
|-|-|
|[error_condition](#error_condition)|Konstruiert ein Objekt vom Typ `error_condition`.|

### <a name="typedefs"></a>TypeDefs

|||
|-|-|
|[value_type](#value_type)|Ein Typ, der den gespeicherten Fehlercodewert darstellt.|

### <a name="functions"></a>Functions

|||
|-|-|
|[assign](#assign)|Weist einen Fehlercodewert und die Kategorie an eine Fehlerbedingung zurück.|
|[category](#category)|Gibt die Fehlerkategorie zurück.|
|[Löschen](#clear)|Löscht den Fehlercodewert und die Kategorie.|
|[Nachricht](#message)|Gibt den Namen des Fehlercodes zurück.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[Operator = =](#op_eq_eq)|Prüft auf Gleichheit zwischen `error_condition`-Objekten.|
|[Operator! =](#op_neq)|Prüft auf Ungleichheit zwischen `error_condition`-Objekten.|
|[Operator<](#op_lt)|Testet, ob das `error_condition`-Objekt kleiner ist als das `error_code`-Objekt, das für den Vergleich übergeben wurde.|
|[Operator =](#op_eq)|Weist dem `error_condition`-Objekt einen neuen Enumerationswert zu.|
|[Operator bool](#op_bool)|Wandelt eine Variable vom Typ `error_condition` um.|

### <a name="assign"></a><a name="assign"></a>einräumen

Weist einen Fehlercodewert und die Kategorie an eine Fehlerbedingung zurück.

```cpp
void assign(value_type val, const error_category& _Cat);
```

#### <a name="parameters"></a>Parameter

*ster*\
Der Fehlercodewert, der in `error_code` gespeichert werden soll.

*_Cat*\
Die Fehlerkategorie, die in `error_code` gespeichert werden soll.

#### <a name="remarks"></a>Bemerkungen

Die Member-Funktion speichert *Val* als Fehler Codewert und einen Zeiger auf *_Cat*.

### <a name="category"></a><a name="category"></a>Kategorie

Gibt die Fehlerkategorie zurück.

```cpp
const error_category& category() const;
```

#### <a name="return-value"></a>Rückgabewert

Ein Verweis auf die gespeicherte Fehlerkategorie.

#### <a name="remarks"></a>Bemerkungen

### <a name="clear"></a><a name="clear"></a>Klartext

Löscht den Fehlercodewert und die Kategorie.

```cpp
clear();
```

#### <a name="remarks"></a>Bemerkungen

Die Memberfunktion speichert einen Fehlercodewert „Null“ und einen Zeiger auf das Objekt [generic_category](../standard-library/system-error-functions.md#generic_category).

### <a name="error_condition"></a><a name="error_condition"></a>error_condition

Konstruiert ein Objekt vom Typ `error_condition`.

```cpp
error_condition();

error_condition(value_type val, const error_category& _Cat);

template <class _Enum>
error_condition(_Enum _Errcode,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_code>::type* = 0);
```

#### <a name="parameters"></a>Parameter

*ster*\
Der Fehlercodewert, der in `error_condition` gespeichert werden soll.

*_Cat*\
Die Fehlerkategorie, die in `error_condition` gespeichert werden soll.

*_Errcode*\
Der Enumerationswert, der in `error_condition` gespeichert werden soll.

#### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor speichert einen Fehlercodewert „Null“ und einen Zeiger auf [generic_category](../standard-library/system-error-functions.md#generic_category).

Der zweite Konstruktor speichert *Val* als Fehler Codewert und einen Zeiger auf [Error_category](../standard-library/error-category-class.md).

Im dritten Konstruktor wird `(value_type)_Errcode` als Fehlercodewert und ein Zeiger auf [generic_category](../standard-library/system-error-functions.md#generic_category) gespeichert.

### <a name="message"></a><a name="message"></a>Nachricht

Gibt den Namen des Fehlercodes zurück.

```cpp
string message() const;
```

#### <a name="return-value"></a>Rückgabewert

Ein `string`, der den Namen des Fehlercodes darstellt.

#### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion gibt `category().message(value())` zurück.

### <a name="operator"></a><a name="op_eq_eq"></a>Operator = =

Prüft auf Gleichheit zwischen `error_condition`-Objekten.

```cpp
bool operator==(const error_condition& right) const;
```

#### <a name="parameters"></a>Parameter

*Richting*\
Die Objekte, die auf Gleichheit getestet werden sollen.

#### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Objekte gleich sind. , **`false`** Wenn Objekte nicht gleich sind.

#### <a name="remarks"></a>Bemerkungen

Der Memberoperator gibt `category() == right.category() && value == right.value()`zurück.

### <a name="operator"></a><a name="op_neq"></a>Operator! =

Prüft auf Ungleichheit zwischen `error_condition`-Objekten.

```cpp
bool operator!=(const error_condition& right) const;
```

#### <a name="parameters"></a>Parameter

*Richting*\
Das Objekt, das auf Ungleichheit geprüft werden soll.

#### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das `error_condition` Objekt nicht gleich dem-Objekt ist, das `error_condition` *Rechts*übermittelt wird; andernfalls **`false`** .

#### <a name="remarks"></a>Bemerkungen

Der Memberoperator gibt `!(*this == right)`zurück.

### <a name="operatorlt"></a><a name="op_lt"></a>KOM&lt;

Testet, ob das `error_condition`-Objekt kleiner ist als das `error_code`-Objekt, das für den Vergleich übergeben wurde.

```cpp
bool operator<(const error_condition& right) const;
```

#### <a name="parameters"></a>Parameter

*Richting*\
Das zu vergleichende `error_condition`-Objekt.

#### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das- `error_condition` Objekt kleiner als das `error_condition` für den Vergleich übergebenen Objekt ist. Andernfalls **`false`** .

#### <a name="remarks"></a>Bemerkungen

Der Memberoperator gibt `category() < right.category() || category() == right.category() && value < right.value()`zurück.

### <a name="operator"></a><a name="op_eq"></a>Operator =

Weist dem `error_condition`-Objekt einen neuen Enumerationswert zu.

```cpp
template <class _Enum>
error_condition(_Enum error,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_condition>::type&
    operator=(Enum _Errcode);
```

#### <a name="parameters"></a>Parameter

*_Errcode*\
Der Enumerationswert, der dem `error_condition`-Objekt zugewiesen wird.

#### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das `error_condition`-Objekt, dem der neue Enumerationswert durch die Memberfunktion zugewiesen wird.

#### <a name="remarks"></a>Bemerkungen

Der Memberoperator speichert `(value_type)error` als Fehlercodewert und einen Zeiger auf [generic_category](../standard-library/system-error-functions.md#generic_category). Er gibt zurück **`*this`** .

### <a name="operator-bool"></a><a name="op_bool"></a>Operator bool

Wandelt eine Variable vom Typ `error_condition` um.

```cpp
explicit operator bool() const;
```

#### <a name="return-value"></a>Rückgabewert

Der boolesche Wert des Objekts `error_condition`.

#### <a name="remarks"></a>Bemerkungen

Der Operator gibt einen Wert zurück, der nur in konvertierbar **`true`** ist, wenn [value](#value) ungleich 0 (null) ist. Der Rückgabetyp kann nur in konvertiert **`bool`** werden, nicht zu `void *` oder anderen bekannten skalaren Typen.

### <a name="value"></a><a name="value"></a>-Wert

Gibt den gespeicherten Fehlercodewert zurück.

```cpp
value_type value() const;
```

#### <a name="return-value"></a>Rückgabewert

Der gespeicherte Fehlercodewert vom Typ [value_type](#value_type).

#### <a name="remarks"></a>Bemerkungen

### <a name="value_type"></a><a name="value_type"></a>value_type

Ein Typ, der den gespeicherten Fehlercodewert darstellt.

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>Bemerkungen

Die Typdefinition ist ein Synonym für **`int`** .
