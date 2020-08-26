---
title: error_code-Klasse
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_code
- system_error/std::error_code::value_type
- system_error/std::error_code::assign
- system_error/std::error_code::category
- system_error/std::error_code::clear
- system_error/std::error_code::default_error_condition
- system_error/std::error_code::message
- system_error/std::error_code::operator bool
helpviewer_keywords:
- std::error_code
- std::error_code::value_type
- std::error_code::assign
- std::error_code::category
- std::error_code::clear
- std::error_code::default_error_condition
- std::error_code::message
ms.assetid: c09b4a96-cb14-4281-a319-63543f9b2b4a
ms.openlocfilehash: 5bbd67d2967a1a6d070ece54ea464a2a5a2deac9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844456"
---
# <a name="error_code-class"></a>error_code-Klasse

Stellt Low-Level-Systemfehler dar, die von der Implementierung abhängen.

## <a name="syntax"></a>Syntax

```cpp
class error_code;
```

## <a name="remarks"></a>Bemerkungen

Ein Objekt vom Typ `error_code`-Klasse enthält einen Fehlercodewert und einen Zeiger auf ein Objekt, das eine [Kategorie](../standard-library/error-category-class.md) von Fehlercodes darstellt, die gemeldete Systemfehler auf niedriger Ebene beschreiben.

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|Name|BESCHREIBUNG|
|-|-|
|[error_code](#error_code)|Konstruiert ein Objekt vom Typ `error_code`.|

### <a name="typedefs"></a>TypeDefs

|Name|BESCHREIBUNG|
|-|-|
|[value_type](#value_type)|Ein Typ, der den gespeicherten Fehlercodewert darstellt.|

### <a name="functions"></a>Functions

|Name|BESCHREIBUNG|
|-|-|
|[assign](#assign)|Weist einen Fehlercodewert und die Kategorie an einen Fehlercode zu.|
|[category](#category)|Gibt die Fehlerkategorie zurück.|
|[Löschen](#clear)|Löscht den Fehlercodewert und die Kategorie.|
|[default_error_condition](#default_error_condition)|Gibt die Standardfehlerbedingung zurück.|
|[Nachricht](#message)|Gibt den Namen des Fehlercodes zurück.|

### <a name="operators"></a>Operatoren

|Name|BESCHREIBUNG|
|-|-|
|[Operator = =](#op_eq_eq)|Prüft auf Gleichheit zwischen `error_code`-Objekten.|
|[Operator! =](#op_neq)|Prüft auf Ungleichheit zwischen `error_code`-Objekten.|
|[Operator<](#op_lt)|Testet, ob das `error_code`-Objekt kleiner ist als das `error_code`-Objekt, das für den Vergleich übergeben wurde.|
|[Operator =](#op_eq)|Weist dem `error_code`-Objekt einen neuen Enumerationswert zu.|
|[Operator bool](#op_bool)|Wandelt eine Variable vom Typ `error_code` um.|

### <a name="assign"></a><a name="assign"></a> einräumen

Weist einen Fehlercodewert und die Kategorie an einen Fehlercode zu.

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

### <a name="category"></a><a name="category"></a> Kategorie

Gibt die Fehlerkategorie zurück.

```cpp
const error_category& category() const;
```

#### <a name="remarks"></a>Bemerkungen

### <a name="clear"></a><a name="clear"></a> Klartext

Löscht den Fehlercodewert und die Kategorie.

```cpp
clear();
```

#### <a name="remarks"></a>Bemerkungen

Die Memberfunktion speichert einen Fehlercodewert „Null“ und einen Zeiger auf das Objekt [generic_category](../standard-library/system-error-functions.md#generic_category).

### <a name="default_error_condition"></a><a name="default_error_condition"></a> default_error_condition

Gibt die Standardfehlerbedingung zurück.

```cpp
error_condition default_error_condition() const;
```

#### <a name="return-value"></a>Rückgabewert

Die von [default_error_condition](../standard-library/error-category-class.md#default_error_condition) angegebene Funktion [error_condition](../standard-library/error-condition-class.md).

#### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion gibt `category().default_error_condition(value())` zurück.

### <a name="error_code"></a><a name="error_code"></a> error_code

Konstruiert ein Objekt vom Typ `error_code`.

```cpp
error_code();

error_code(value_type val, const error_category& _Cat);

template <class _Enum>
error_code(_Enum _Errcode,
    typename enable_if<is_error_code_enum<_Enum>::value,
    error_code>::type* = 0);
```

#### <a name="parameters"></a>Parameter

*ster*\
Der Fehlercodewert, der in `error_code` gespeichert werden soll.

*_Cat*\
Die Fehlerkategorie, die in `error_code` gespeichert werden soll.

*_Errcode*\
Der Enumerationswert, der in `error_code` gespeichert werden soll.

#### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor speichert einen Fehlercodewert „Null“ und einen Zeiger auf [generic_category](../standard-library/system-error-functions.md#generic_category).

Der zweite Konstruktor speichert *Val* als Fehler Codewert und einen Zeiger auf [Error_category](../standard-library/error-category-class.md).

Im dritten Konstruktor wird `(value_type)_Errcode` als Fehlercodewert und ein Zeiger auf [generic_category](../standard-library/system-error-functions.md#generic_category) gespeichert.

### <a name="message"></a><a name="message"></a> Nachricht

Gibt den Namen des Fehlercodes zurück.

```cpp
string message() const;
```

#### <a name="return-value"></a>Rückgabewert

Ein `string`, der den Namen des Fehlercodes darstellt.

#### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion gibt `category().message(value())` zurück.

### <a name="operator"></a><a name="op_eq_eq"></a> Operator = =

Prüft auf Gleichheit zwischen `error_code`-Objekten.

```cpp
bool operator==(const error_code& right) const;
```

#### <a name="parameters"></a>Parameter

*Richting*\
Das Objekt, das auf Gleichheit getestet werden soll.

#### <a name="return-value"></a>Rückgabewert

**`true`** , wenn die Objekte gleich sind. , **`false`** Wenn Objekte nicht gleich sind.

#### <a name="remarks"></a>Bemerkungen

Der Memberoperator gibt `category() == right.category() && value == right.value()`zurück.

### <a name="operator"></a><a name="op_neq"></a> Operator! =

Prüft auf Ungleichheit zwischen `error_code`-Objekten.

```cpp
bool operator!=(const error_code& right) const;
```

#### <a name="parameters"></a>Parameter

*Richting*\
Das Objekt, das auf Ungleichheit geprüft werden soll.

#### <a name="return-value"></a>Rückgabewert

**`true`** , wenn das `error_code` Objekt nicht gleich dem-Objekt ist, das `error_code` *Rechts*übermittelt wird; andernfalls **`false`** .

#### <a name="remarks"></a>Bemerkungen

Der Memberoperator gibt `!(*this == right)`zurück.

### <a name="operatorlt"></a><a name="op_lt"></a> KOM&lt;

Testet, ob das `error_code`-Objekt kleiner ist als das `error_code`-Objekt, das für den Vergleich übergeben wurde.

```cpp
bool operator<(const error_code& right) const;
```

#### <a name="parameters"></a>Parameter

*Richting*\
Das zu vergleichende error_code-Objekt.

#### <a name="return-value"></a>Rückgabewert

**`true`** , wenn das- `error_code` Objekt kleiner als das `error_code` für den Vergleich übergebenen Objekt ist. Andernfalls **`false`** .

#### <a name="remarks"></a>Bemerkungen

Der Memberoperator gibt `category() < right.category() || category() == right.category() && value < right.value()`zurück.

### <a name="operator"></a><a name="op_eq"></a> Operator =

Weist dem `error_code`-Objekt einen neuen Enumerationswert zu.

```cpp
template <class _Enum>
typename enable_if<is_error_code_enum<_Enum>::value, error_code>::type&
    operator=(_Enum _Errcode);
```

#### <a name="parameters"></a>Parameter

*_Errcode*\
Der Enumerationswert, der dem `error_code`-Objekt zugewiesen wird.

#### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das `error_code`-Objekt, dem der neue Enumerationswert durch die Memberfunktion zugewiesen wird.

#### <a name="remarks"></a>Bemerkungen

Der Memberoperator speichert `(value_type)_Errcode` als Fehlercodewert und einen Zeiger auf [generic_category](../standard-library/system-error-functions.md#generic_category). Er gibt zurück **`*this`** .

### <a name="operator-bool"></a><a name="op_bool"></a> Operator bool

Wandelt eine Variable vom Typ `error_code` um.

```cpp
explicit operator bool() const;
```

#### <a name="return-value"></a>Rückgabewert

Der boolesche Wert des Objekts `error_code`.

#### <a name="remarks"></a>Bemerkungen

Der Operator gibt einen Wert zurück, der nur in konvertierbar **`true`** ist, wenn [value](#value) ungleich 0 (null) ist. Der Rückgabetyp kann nur in konvertiert **`bool`** werden, nicht zu `void *` oder anderen bekannten skalaren Typen.

### <a name="value"></a>Wert vom Typ <a name="value"></a>

Gibt den gespeicherten Fehlercodewert zurück.

```cpp
value_type value() const;
```

### <a name="return-value"></a>Rückgabewert

Der gespeicherte Fehlercodewert vom Typ [value_type](#value_type).

### <a name="value_type"></a><a name="value_type"></a> value_type

Ein Typ, der den gespeicherten Fehlercodewert darstellt.

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>Bemerkungen

Diese Typdefinition ist ein Synonym für **`int`** .
