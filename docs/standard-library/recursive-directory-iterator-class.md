---
title: recursive_directory_iterator-Klasse
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
ms.openlocfilehash: 0f9bdc3edd7f5798afaa8d170adc35708a6aafa2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217622"
---
# <a name="recursive_directory_iterator-class"></a>recursive_directory_iterator-Klasse

Beschreibt einen eingabeiterator, der die Dateinamen in einem Verzeichnis durchläuft und möglicherweise rekursiv in Unterverzeichnisse absteigend ist. Bei einem Iterator `X` wertet der Ausdruck `*X` zu einem Objekt der Klasse aus, `directory_entry` das den Dateinamen umschließt, und alles, was über den Status bekannt ist.

Weitere Informationen und Codebeispiele finden Sie unter [Dateisystemnavigation (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntax

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>Bemerkungen

Die Klassen Vorlage speichert Folgendes:

1. ein Objekt vom Typ `stack<pair<directory_iterator, path>>` , das `mystack` hier zum Zweck der Darstellung aufgerufen wird, das den Schachteln der Verzeichnisse darstellt, die sequenziert werden sollen.

1. ein Objekt vom Typ `directory_entry` `myentry` , das hier aufgerufen wird, das den aktuellen Dateinamen in der Verzeichnis Sequenz darstellt.

1. ein Objekt vom Typ **`bool`** , `no_push` das hier aufgerufen wird, das aufzeichnet, ob der rekursive Abstieg in die Unterverzeichnisse deaktiviert ist.

1. ein Objekt vom Typ `directory_options` , `myoptions` das hier aufgerufen wird und die bei der Konstruktion festgelegte Optionen aufzeichnet.

Ein konstruiertes Standard Objekt vom Typ `recursive_directory_entry` verfügt über einen Sequenz Ende-Iterator bei `mystack.top().first` und stellt den Sequenz Ende-Iterator dar. Wenn das Verzeichnis z. b. `abc` Einträge `def` (ein Verzeichnis), `def/ghi` und ist `jkl` , lautet der folgende Code:

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

Ruft "Visit" mit den Argumenten `path("abc/def/ghi")` und auf `path("abc/jkl")` . Sie können die Sequenzierung über eine Verzeichnis Unterstruktur auf zwei Arten qualifizieren:

1. Ein Verzeichnis Symlink wird nur überprüft, wenn Sie einen `recursive_directory_iterator` mit einem- `directory_options` Argument erstellen, dessen Wert ist `directory_options::follow_directory_symlink` .

1. Wenn Sie anrufen, `disable_recursion_pending` wird ein nachfolgendes Verzeichnis, das während eines Inkrements gefunden wurde, nicht rekursiv gescannt.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[recursive_directory_iterator](#recursive_directory_iterator)|Erstellt ein Objekt vom Typ `recursive_directory_iterator`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Eingeh](#depth)|Gibt zurück `mystack.size() - 1` , und `pval` ist daher in Tiefe Null.|
|[disable_recursion_pending](#disable_recursion_pending)|Speichert **`true`** in `no_push` .|
|[increment](#increment)|Wechselt zum nächsten Dateinamen in der Sequenz.|
|[options](#options)|Gibt `myoptions`zurück.|
|[Chor](#pop)|Gibt das nächste-Objekt zurück.|
|[recursion_pending](#recursion_pending)|Gibt `!no_push`zurück.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator! =](#op_neq)|Gibt `!(*this == right)`zurück.|
|[Operator =](#op_as)|Die als Standard (default) festgelegten Memberzuweisungsoperatoren verhalten sich wie erwartet.|
|[Operator = =](#op_eq)|Gibt **`true`** nur dann zurück, wenn sowohl **`*this`** als auch *right* Sequenz Ende-Iteratoren sind oder beide keine Sequenz-Iteratoren sind.|
|[KOM](#op_multiply)|Gibt `myentry`zurück.|
|[Operator->](#op_cast)|Gibt `&**this`zurück.|
|[Operator + +](#op_increment)|Inkremente `recursive_directory_iterator` .|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<filesystem>

**Namespace:** std::tr2::sys

## <a name="recursive_directory_iteratordepth"></a><a name="depth"></a>recursive_directory_iterator::d epth

Gibt zurück `mystack.size() - 1` , und `pval` ist daher in Tiefe Null.

```cpp
int depth() const;
```

## <a name="recursive_directory_iteratordisable_recursion_pending"></a><a name="disable_recursion_pending"></a>recursive_directory_iterator::d isable_recursion_pending

Speichert **`true`** in `no_push` .

```cpp
void disable_recursion_pending();
```

## <a name="recursive_directory_iteratorincrement"></a><a name="increment"></a>recursive_directory_iterator:: Inkrement

Wechselt zum nächsten Dateinamen in der Sequenz.

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

### <a name="parameters"></a>Parameter

*EC*\
Der angegebene Fehlercode.

### <a name="remarks"></a>Bemerkungen

Die Funktion versucht, zum nächsten Dateinamen in der geschachtelten Sequenz zu gelangen. Bei erfolgreicher Ausführung speichert Sie diesen Dateinamen in `myentry` ; andernfalls erzeugt Sie einen Sequenz Ende-Iterator.

## <a name="recursive_directory_iteratoroperator"></a><a name="op_neq"></a>recursive_directory_iterator:: Operator! =

Gibt `!(*this == right)`zurück.

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Parameter

*Richting*\
Der [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) für den Vergleich.

## <a name="recursive_directory_iteratoroperator"></a><a name="op_as"></a>recursive_directory_iterator:: Operator =

Die als Standard (default) festgelegten Memberzuweisungsoperatoren verhalten sich wie erwartet.

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parameter

*recursive_directory_iterator*\
Die [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) , die in die kopiert werden `recursive_directory_iterator` .

## <a name="recursive_directory_iteratoroperator"></a><a name="op_eq"></a>recursive_directory_iterator:: Operator = =

Gibt **`true`** nur dann zurück, wenn sowohl **`*this`** als auch *right* Sequenz Ende-Iteratoren sind oder beide keine Sequenz-Iteratoren sind.

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Parameter

*Richting*\
Der [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) für den Vergleich.

## <a name="recursive_directory_iteratoroperator"></a><a name="op_multiply"></a>recursive_directory_iterator:: Operator *

Gibt `myentry`zurück.

```cpp
const directory_entry& operator*() const;
```

## <a name="recursive_directory_iteratoroperator-"></a><a name="op_cast"></a>recursive_directory_iterator:: Operator->

Gibt `&**this`zurück.

```cpp
const directory_entry * operator->() const;
```

## <a name="recursive_directory_iteratoroperator"></a><a name="op_increment"></a>recursive_directory_iterator:: Operator + +

Inkremente `recursive_directory_iterator` .

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

### <a name="parameters"></a>Parameter

*wartenden*\
Das angegebene Inkrement.

### <a name="remarks"></a>Bemerkungen

Die erste Member-Funktion Ruft auf `increment()` und gibt dann zurück **`*this`** . Die zweite Member-Funktion erstellt eine Kopie des-Objekts, ruft auf `increment()` und gibt dann die Kopie zurück.

## <a name="recursive_directory_iteratoroptions"></a><a name="options"></a>recursive_directory_iterator:: Options

Gibt `myoptions`zurück.

```cpp
directory_options options() const;
```

## <a name="recursive_directory_iteratorpop"></a><a name="pop"></a>recursive_directory_iterator::p op

Gibt das nächste-Objekt zurück.

```cpp
void pop();
```

### <a name="remarks"></a>Bemerkungen

, Wenn `depth() == 0` das Objekt ein Sequenz Ende-Iterator wird. Andernfalls beendet die Memberfunktion das Durchsuchen des aktuellen (tiefsten) Verzeichnisses und setzt das Durchsuchen auf der nächstniedrigeren Tiefe fort.

## <a name="recursive_directory_iteratorrecursion_pending"></a><a name="recursion_pending"></a>recursive_directory_iterator:: recursion_pending

Gibt `!no_push`zurück.

```cpp
bool recursion_pending() const;
```

## <a name="recursive_directory_iteratorrecursive_directory_iterator"></a><a name="recursive_directory_iterator"></a>recursive_directory_iterator:: recursive_directory_iterator

Erstellt ein Objekt vom Typ `recursive_directory_iterator`.

```cpp
recursive_directory_iterator() noexcept;
explicit recursive_directory_iterator(const path& pval);

recursive_directory_iterator(const path& pval,
    error_code& ec) noexcept;
recursive_directory_iterator(const path& pval,
    directory_options opts);

recursive_directory_iterator(const path& pval,
    directory_options opts,
    error_code& ec) noexcept;
recursive_directory_iterator(const recursive_directory_iterator&) = default;
recursive_directory_iterator(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parameter

*PVAL*\
Der angegebene Pfad.

*error_code*\
Der angegebene Fehlercode.

*OPTS*\
Die angegebenen Verzeichnis Optionen.

*recursive_directory_iterator*\
Das `recursive_directory_iterator`-Element, von dem das erstellte `recursive_directory_iterator`-Element eine Kopie sein soll.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor erzeugt einen Sequenzende-Iterator. Mit dem zweiten und dritten Konstruktoren **`false`** `no_push` wird in und `directory_options::none` in gespeichert `myoptions` . Anschließend wird versucht, *PVal* als Verzeichnis zu öffnen und zu lesen. Bei erfolgreicher Initialisierung initialisieren `mystack` und `myentry` , um den ersten nicht-Verzeichnis Dateinamen in der geschachtelte Sequence-Sequenz festzulegen. andernfalls wird ein Sequenz Ende-Iterator erzeugt.

Der vierte und fünfte Konstruktoren Verhalten sich identisch mit dem zweiten und dritten, mit dem Unterschied, dass Sie zuerst *OPTS* in speichern `myoptions` . Die als Standard festgelegten Konstruktoren verhalten sich wie erwartet.

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[Dateisystemnavigation (C++)](../standard-library/file-system-navigation.md)
