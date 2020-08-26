---
title: filesystem_error-Klasse
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
ms.openlocfilehash: 1d142057859f1ca173f8953b34c07bbb3803ecba
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835869"
---
# <a name="filesystem_error-class"></a>filesystem_error-Klasse

Eine Basisklasse für alle Ausnahmen, die ausgelöst werden, um einen Systemüberlauf auf niedriger Ebene zu melden.

## <a name="syntax"></a>Syntax

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>Bemerkungen

Die-Klasse fungiert als Basisklasse für alle Ausnahmen, die ausgelöst werden, um einen Fehler in Functions zu melden \<filesystem> . Sie speichert ein Objekt vom Typ `string` , `mymesg` das hier zur Veranschaulichung aufgerufen wird. Außerdem werden zwei Objekte vom Typ gespeichert `path` , die `mypval1` als und bezeichnet werden `mypval2` .

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|Name|Beschreibung|
|-|-|
|[filesystem_error](#filesystem_error)|Erstellt eine `filesystem_error` Meldung.|

### <a name="functions"></a>Functions

|Name|Beschreibung|
|-|-|
|[path1](#path1)|Gibt `mypval1` zurück.|
|[path2](#path2)|Gibt `mypval2` zurück.|
|[worüber](#what)|Gibt einen Zeiger auf ein `NTBS` zurück.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<filesystem>

**Namespace:** std::experimental::filesystem

## <a name="filesystem_error"></a><a name="filesystem_error"></a> filesystem_error

Der erste Konstruktor erstellt seine Nachricht aus *what_arg* und *EC*. Der zweite Konstruktor erstellt auch seine Nachricht aus *"pval1"*, die in gespeichert wird `mypval1` . Der dritte Konstruktor erstellt seine Nachricht auch aus *"pval1"*, die er in speichert `mypval1` , und aus *"pval2"*, die er in speichert `mypval2` .

```cpp
filesystem_error(const string& what_arg,
    error_code ec);

filesystem_error(const string& what_arg,
    const path& pval1,
    error_code ec);

filesystem_error(const string& what_arg,
    const path& pval1,
    const path& pval2,
    error_code ec);
```

### <a name="parameters"></a>Parameter

*what_arg*\
Angegebene Meldung.

*EC*\
Der angegebene Fehlercode.

*"mypval1"*\
Weiterer angegebener Nachrichten Parameter.

*"mypval2"*\
Weiterer angegebener Nachrichten Parameter.

## <a name="path1"></a><a name="path1"></a> path1

Die Memberfunktion gibt `mypval1` zurück.

```cpp
const path& path1() const noexcept;
```

## <a name="path2"></a><a name="path2"></a> path2

Die Memberfunktion gibt `mypval2` zurück.

```cpp
const path& path2() const noexcept;
```

## <a name="what"></a><a name="what"></a> worüber

Die Member-Funktion gibt einen Zeiger auf einen zurück `NTBS` , der vorzugsweise aus `runtime_error::what()` , `system_error::what()` , `mymesg` , `mypval1.native_string()` und besteht `mypval2.native_string()` .

```cpp
const char *what() const noexcept;
```
