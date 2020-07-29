---
title: directory_iterator-Klasse.
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::directory_iterator
- filesystem/std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator::directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator::increment
- filesystem/std::experimental::filesystem::directory_iterator::operator=
- filesystem/std::experimental::filesystem::directory_iterator::operator==
- filesystem/std::experimental::filesystem::directory_iterator::operator!=
- filesystem/std::experimental::filesystem::directory_iterator::operator*
- filesystem/std::experimental::filesystem::directory_iterator::operator-&gt;
- filesystem/std::experimental::filesystem::directory_iterator::operator++
ms.assetid: dca2ecf8-3e69-4644-a83d-705061e10cc8
helpviewer_keywords:
- std::experimental::filesystem::directory_iterator
- std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- std::experimental::filesystem::directory_iterator
- std::experimental::filesystem::directory_iterator::directory_iterator
- std::experimental::filesystem::directory_iterator::increment
- std::experimental::filesystem::directory_iterator::operator=
- std::experimental::filesystem::directory_iterator::operator==
- std::experimental::filesystem::directory_iterator::operator!=
- std::experimental::filesystem::directory_iterator::operator*
- std::experimental::filesystem::directory_iterator::operator-&gt;
- std::experimental::filesystem::directory_iterator::operator++
ms.openlocfilehash: a7ccc2a941da079e14092af5b81dc537db4a48c0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215776"
---
# <a name="directory_iterator-class"></a>directory_iterator-Klasse.

Beschreibt einen Eingabeiterator, der alle Dateinamen in einem Verzeichnis durchläuft. Bei einem Iterator `X` wertet der Ausdruck `*X` zu einem Objekt der Klasse aus, `directory_entry` das den Dateinamen umschließt, und alles, was über den Status bekannt ist.

Die Klasse speichert ein Objekt vom Typ `path` , das `mydir` hier zur Veranschaulichung aufgerufen wird, das den Namen des Verzeichnisses darstellt, das sequenziert werden soll, und ein Objekt vom Typ, `directory_entry` `myentry` das hier aufgerufen wird, das den aktuellen Dateinamen in der Verzeichnis Sequenz darstellt. Ein konstruiertes Standard Objekt vom Typ `directory_entry` weist einen leeren `mydir` Pfadnamen auf und stellt den Sequenz Ende-Iterator dar.

Wenn z. b. das Verzeichnis `abc` mit Einträgen `def` und `ghi` ist, lautet der folgende Code:

`for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`

Ruft `visit` mit den Argumenten `path("abc/def")` und auf `path("abc/ghi")` .

Weitere Informationen und Codebeispiele finden Sie unter [Dateisystemnavigation (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntax

```cpp
class directory_iterator;
```

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[directory_iterator](#directory_iterator)|Erstellt einen eingabeiterator, der die Dateinamen in einem Verzeichnis durchläuft.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[increment](#increment)|Versucht, mit dem nächsten Dateinamen im Verzeichnis fortzufahren.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator! =](#op_neq)|Gibt `!(*this == right)`zurück.|
|[Operator =](#op_as)|Die als Standard (default) festgelegten Memberzuweisungsoperatoren verhalten sich wie erwartet.|
|[Operator = =](#op_eq)|Gibt **`true`** nur dann zurück, wenn sowohl **`*this`** als auch *right* Sequenz Ende-Iteratoren sind oder beide keine Sequenz-Iteratoren sind.|
|[KOM](#op_star)|Gibt `myentry`zurück.|
|[Operator->](#op_cast)|Gibt `&**this`zurück.|
|[Operator + +](#op_increment)|Ruft `increment()` auf, gibt dann zurück **`*this`** oder erstellt eine Kopie des-Objekts, ruft auf und `increment()` gibt dann die Kopie zurück.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<experimental/filesystem>

**Namespace:** std::experimental::filesystem

## <a name="directory_iteratordirectory_iterator"></a><a name="directory_iterator"></a>directory_iterator::d irectory_iterator

Der erste Konstruktor erzeugt einen Sequenzende-Iterator. Mit dem zweiten und dritten Konstruktoren wird *PVal* in gespeichert `mydir` . Anschließend wird versucht, das Verzeichnis zu öffnen und `mydir` als Verzeichnis zu lesen. Bei erfolgreicher Ausführung speichern Sie den ersten Dateinamen im Verzeichnis in `myentry` ; andernfalls wird ein Sequenz Ende-Iterator erzeugt.

Die als Standard festgelegten Konstruktoren verhalten sich wie erwartet.

```cpp
directory_iterator() noexcept;
explicit directory_iterator(const path& pval);

directory_iterator(const path& pval, error_code& ec) noexcept;
directory_iterator(const directory_iterator&) = default;
directory_iterator(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parameter

*PVAL*\
Der gespeicherte Dateiname-Pfad.

*EC*\
Der Status Fehlercode.

*directory_iterator*\
Das gespeicherte-Objekt.

## <a name="directory_iteratorincrement"></a><a name="increment"></a>directory_iterator:: Inkrement

Die Funktion versucht, zum nächsten Dateinamen im Verzeichnis zu gelangen. Bei erfolgreicher Ausführung speichert Sie diesen Dateinamen in `myentry` ; andernfalls erzeugt Sie einen Sequenz Ende-Iterator.

```cpp
directory_iterator& increment(error_code& ec) noexcept;
```

## <a name="directory_iteratoroperator"></a><a name="op_neq"></a>directory_iterator:: Operator! =

Der Memberoperator gibt `!(*this == right)`zurück.

```cpp
bool operator!=(const directory_iterator& right) const;
```

### <a name="parameters"></a>Parameter

*Richting*\
Die [directory_iterator](../standard-library/directory-iterator-class.md) mit der verglichen werden `directory_iterator` .

## <a name="directory_iteratoroperator"></a><a name="op_as"></a>directory_iterator:: Operator =

Die als Standard (default) festgelegten Memberzuweisungsoperatoren verhalten sich wie erwartet.

```cpp
directory_iterator& operator=(const directory_iterator&) = default;
directory_iterator& operator=(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parameter

*Richting*\
Die [directory_iterator](../standard-library/directory-iterator-class.md) , die in die kopiert werden `directory_iterator` .

## <a name="directory_iteratoroperator"></a><a name="op_eq"></a>directory_iterator:: Operator = =

Der Member-Operator gibt **`true`** nur dann zurück, wenn sowohl **`*this`** als auch *right* Sequenz Ende-Iteratoren sind oder beide keine Sequenz Sequenz-Iteratoren sind.

```cpp
bool operator==(const directory_iterator& right) const;
```

### <a name="parameters"></a>Parameter

*Richting*\
Die [directory_iterator](../standard-library/directory-iterator-class.md) mit der verglichen werden `directory_iterator` .

## <a name="directory_iteratoroperator"></a><a name="op_star"></a>directory_iterator:: Operator *

Der Memberoperator gibt `myentry`zurück.

```cpp
const directory_entry& operator*() const;
```

## <a name="directory_iteratoroperator-"></a><a name="op_cast"></a>directory_iterator:: Operator->

Die Memberfunktion gibt `&**this` zurück.

```cpp
const directory_entry * operator->() const;
```

## <a name="directory_iteratoroperator"></a><a name="op_increment"></a>directory_iterator:: Operator + +

Die erste Member-Funktion Ruft auf `increment()` und gibt dann zurück **`*this`** . Die zweite Member-Funktion erstellt eine Kopie des-Objekts, ruft auf `increment()` und gibt dann die Kopie zurück.

```cpp
directory_iterator& operator++();
directory_iterator& operator++(int);
```

### <a name="parameters"></a>Parameter

*wartenden*\
Die Anzahl der Inkremente.

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[Dateisystemnavigation (C++)](../standard-library/file-system-navigation.md)
