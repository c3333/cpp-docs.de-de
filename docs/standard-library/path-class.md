---
title: path-Klasse
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: fb56afbc1d29f1d321b394342382f89b06768720
ms.sourcegitcommit: b5854134553db1d99a5761bec131841c374a3098
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2020
ms.locfileid: "91958658"
---
# <a name="path-class"></a>path-Klasse

Die **path** -Klasse speichert ein Objekt vom Typ `string_type` , `myname` das hier zur Veranschaulichung aufgerufen wird und als Pfadname verwendet werden kann. `string_type` ist ein Synonym für `basic_string<value_type>` , wobei `value_type` ein Synonym für **`wchar_t`** unter Windows oder **`char`** POSIX ist.

Weitere Informationen und Codebeispiele finden Sie unter [Datei System Navigation (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntax

```cpp
class path;
```

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[path](#path)|Erstellt ein Objekt vom Typ `path`.|

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[const_iterator](#const_iterator)|Ein Synonym für `iterator`.|
|[Iterator](#iterator)|Ein bidirektionaler konstanter Iterator, der die `path` Komponenten von festlegt `myname` .|
|[string_type](#string_type)|Der Typ ist ein Synonym für `basic_string<value_type>`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[append](#append)|Fügt die angegebene Sequenz an `mypath` , konvertiert und fügt bei Bedarf eine preferred_separator ein.|
|[assign](#assign)|Ersetzt `mypath` durch die angegebene Sequenz, konvertiert nach Bedarf.|
|[beginnen](#begin)|Gibt einen-Wert zurück `path::iterator` , der das erste Pfad Element im Pfadnamen angibt, falls vorhanden.|
|[c_str](#c_str)|Gibt einen Zeiger auf das erste Zeichen in zurück `mypath` .|
|[Löschen](#clear)|Führt aus `mypath.clear()` .|
|[vergleichbar](#compare)|Gibt Vergleichswerte zurück.|
|[concat](#compare)|Fügt die angegebene Sequenz nach `mypath` Bedarf an, konvertiert (aber kein Trennzeichen) an.|
|[empty](#empty)|Gibt `mypath.empty()`zurück.|
|[end](#end)|Gibt einen Sequenz Ende-Iterator vom Typ zurück `iterator` .|
|[extension](#extension)|Gibt das Suffix von zurück `filename()` .|
|[filename](#filename)|Gibt die Stammverzeichniskomponente von „myname“ zurück, insbesondere `empty() ? path() : *--end()`. Die Komponente kann leer sein.|
|[generic_string](#generic_string)|Gibt `this->string<Elem, Traits, Alloc>(al)` zurück, wobei jeder umgekehrte Schrägstrich in einen Schrägstrich konvertiert wird (unter Windows).|
|[generic_u16string](#generic_u16string)|Gibt `u16string()` zurück, wobei jeder umgekehrte Schrägstrich in einen Schrägstrich konvertiert wird (unter Windows).|
|[generic_u32string](#generic_u32string)|Gibt `u32string()` zurück, wobei jeder umgekehrte Schrägstrich in einen Schrägstrich konvertiert wird (unter Windows).|
|[generic_u8string](#generic_u8string)|Gibt `u8string()` zurück, wobei jeder umgekehrte Schrägstrich in einen Schrägstrich konvertiert wird (unter Windows).|
|[generic_wstring](#generic_wstring)|Gibt `wstring()` zurück, wobei jeder umgekehrte Schrägstrich in einen Schrägstrich konvertiert wird (unter Windows).|
|[has_extension](#has_extension)|Gibt `!extension().empty()`zurück.|
|[has_filename](#has_filename)|Gibt `!filename().empty()`zurück.|
|[has_parent_path](#has_parent_path)|Gibt `!parent_path().empty()`zurück.|
|[has_relative_path](#has_relative_path)|Gibt `!relative_path().empty()`zurück.|
|[has_root_directory](#has_root_directory)|Gibt `!root_directory().empty()`zurück.|
|[has_root_name](#has_root_name)|Gibt `!root_name().empty()`zurück.|
|[has_root_path](#has_root_path)|Gibt `!root_path().empty()`zurück.|
|[has_stem](#has_stem)|Gibt `!stem().empty()`zurück.|
|[is_absolute](#is_absolute)|Für Windows gibt die Funktion zurück `has_root_name() && has_root_directory()` . Für POSIX gibt die Funktion zurück `has_root_directory()` .|
|[is_relative](#is_relative)|Gibt `!is_absolute()`zurück.|
|[make_preferred](#make_preferred)|Konvertiert jedes Trennzeichen nach Bedarf in einen preferred_separator.|
|[native](#native)|Gibt `myname`zurück.|
|[parent_path](#parent_path)|Gibt die übergeordnete Pfadkomponente von zurück `myname` .|
|[preferred_separator](#preferred_separator)|Das konstante Objekt gibt je nach Betriebssystem des Hosts das bevorzugte Zeichen zum Trennen von Pfadkomponenten zurück. |
|[relative_path](#relative_path)|Gibt die relative Pfadkomponente von zurück `myname` . |
|[remove_filename](#remove_filename)|Entfernt den Dateinamen.|
|[replace_extension](#replace_extension)|Ersetzt die Erweiterung von `myname` . |
|[replace_filename](#replace_filename)|Ersetzt den Dateinamen.|
|[root_directory](#root_directory)|Gibt die Stammverzeichnis Komponente von zurück `myname` . |
|[root_name](#root_name)|Gibt die Stamm Namen Komponente von zurück `myname` . |
|[root_path](#root_path)|Gibt die Stamm Pfadkomponente von zurück `myname` .|
|[stem](#stem)|Gibt die `stem` Komponente von zurück `myname` .|
|[string](#string)|Konvertiert die in gespeicherte Sequenz `mypath` .|
|[swap](#swap)|Führt aus `swap(mypath, right.mypath)` .|
|[u16string](#u16string)|Konvertiert die in gespeicherte Sequenz in `mypath` UTF-16 und gibt Sie in einem Objekt vom Typ zurück `u16string` .|
|[u32string](#u32string)|Konvertiert die in gespeicherte Sequenz in `mypath` UTF-32 und gibt Sie in einem Objekt vom Typ zurück `u32string` .|
|["u8string"](#u8string)|Konvertiert die in gespeicherte Sequenz in `mypath` UTF-8 und gibt Sie in einem Objekt vom Typ zurück `u8string` .|
|[value_type](#value_type)|Der Typ beschreibt die Pfadelemente, die vom Hostbetriebssystem bevorzugt werden.|
|[wstring](#wstring)|Konvertiert die in gespeicherte Sequenz in `mypath` die Codierung, die vom Host System für eine Sequenz bevorzugt wird, **`wchar_t`** und gibt diese in einem Objekt vom Typ gespeicherten zurück `wstring` .|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator =](#op_as)|Ersetzt die Elemente des Pfads durch eine Kopie eines anderen Pfades.|
|[Operator + =](#op_add)|Verschiedene `concat` Ausdrücke.|
|[Operator/=](#op_divide)|Verschiedene `append` Ausdrücke.|
|[Operator string_type](#op_string)|Gibt `myname`zurück.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<filesystem>

**Namespace:** std::experimental::filesystem

## <a name="pathappend"></a><a name="append"></a> Path:: Append

Fügt die angegebene Sequenz an `mypath` , konvertiert und fügt bei Bedarf ein ein `preferred_separator` .

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>Parameter

*Ausgangs*\
Angegebene Sequenz.

*erstes*\
Beginn der angegebenen Sequenz.

*letzten*\
Ende der angegebenen Sequenz.

## <a name="pathassign"></a><a name="assign"></a> Path:: Assign

Ersetzt `mypath` durch die angegebene Sequenz, konvertiert nach Bedarf.

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>Parameter

*Ausgangs*\
Angegebene Sequenz.

*erstes*\
Beginn der angegebenen Sequenz.

*letzten*\
Ende der angegebenen Sequenz.

## <a name="pathbegin"></a><a name="begin"></a> Path:: begin

Gibt einen-Wert zurück `path::iterator` , der das erste Pfad Element im Pfadnamen angibt, falls vorhanden.

```cpp
iterator begin() const;
```

## <a name="pathc_str"></a><a name="c_str"></a> Pfad:: c_str

Gibt einen Zeiger auf das erste Zeichen in zurück `mypath` .

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="pathclear"></a><a name="clear"></a> Path:: Clear

Führt aus `mypath.clear()` .

```cpp
void clear() noexcept;
```

## <a name="pathcompare"></a><a name="compare"></a> Path:: Compare

Diese erste Funktion gibt `mypath.compare(pval.native())` zurück. Die zweite Funktion gibt `mypath.compare(str)` zurück. Die dritte Funktion gibt zurück `mypath.compare(ptr)` .

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Parameter

*PVAL*\
Der zu vergleichende Pfad.

*SRT*\
Zu vergleichende Zeichenfolge.

*PTR*\
Der zu vergleichende Zeiger.

## <a name="pathconcat"></a><a name="concat"></a> Pfad:: Concat

Fügt die angegebene Sequenz nach `mypath` Bedarf an, konvertiert (aber kein Trennzeichen) an.

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>Parameter

*Ausgangs*\
Angegebene Sequenz.

*erstes*\
Beginn der angegebenen Sequenz.

*letzten*\
Ende der angegebenen Sequenz.

## <a name="pathconst_iterator"></a><a name="const_iterator"></a> Pfad:: const_iterator

Ein Synonym für `iterator`.

```cpp
typedef iterator const_iterator;
```

## <a name="pathempty"></a><a name="empty"></a> Path:: Empty

Gibt `mypath.empty()`zurück.

```cpp
bool empty() const noexcept;
```

## <a name="pathend"></a><a name="end"></a> Path:: End

Gibt einen Sequenz Ende-Iterator vom Typ zurück `iterator` .

```cpp
iterator end() const;
```

## <a name="pathextension"></a><a name="extension"></a> Path:: Extension

Gibt das Suffix von zurück `filename()` .

```cpp
path extension() const;
```

### <a name="remarks"></a>Bemerkungen

Gibt das Suffix der folgenden zurück `filename() X` :

Wenn `X == path(".") || X == path("..")` oder wenn `X` keinen Punkt enthält, ist das Suffix leer.

Andernfalls beginnt das Suffix mit dem rechten Punkt (und umfasst diesen).

## <a name="pathfilename"></a><a name="filename"></a> Path:: filename

Gibt die Stammverzeichniskomponente von „myname“ zurück, insbesondere `empty() path() : *--end()`. Die Komponente kann leer sein.

```cpp
path filename() const;
```

## <a name="pathgeneric_string"></a><a name="generic_string"></a> Pfad:: generic_string

Gibt `this->string<Elem, Traits, Alloc>(al)` zurück, wobei jeder umgekehrte Schrägstrich in einen Schrägstrich konvertiert wird (unter Windows).

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="pathgeneric_u16string"></a><a name="generic_u16string"></a> Pfad:: generic_u16string

Gibt `u16string()` zurück, wobei jeder umgekehrte Schrägstrich in einen Schrägstrich konvertiert wird (unter Windows).

```cpp
u16string generic_u16string() const;
```

## <a name="pathgeneric_u32string"></a><a name="generic_u32string"></a> Pfad:: generic_u32string

Gibt `u32string()` zurück, wobei jeder umgekehrte Schrägstrich in einen Schrägstrich konvertiert wird (unter Windows).

```cpp
u32string generic_u32string() const;
```

## <a name="pathgeneric_u8string"></a><a name="generic_u8string"></a> Pfad:: generic_u8string

Gibt `u8string()` zurück, wobei jeder umgekehrte Schrägstrich in einen Schrägstrich konvertiert wird (unter Windows).

```cpp
string generic_u8string() const;
```

## <a name="pathgeneric_wstring"></a><a name="generic_wstring"></a> Pfad:: generic_wstring

Gibt `wstring()` zurück, wobei jeder umgekehrte Schrägstrich in einen Schrägstrich konvertiert wird (unter Windows).

```cpp
wstring generic_wstring() const;
```

## <a name="pathhas_extension"></a><a name="has_extension"></a> Pfad:: has_extension

Gibt `!extension().empty()`zurück.

```cpp
bool has_extension() const;
```

## <a name="pathhas_filename"></a><a name="has_filename"></a> Pfad:: has_filename

Gibt `!filename().empty()`zurück.

```cpp
bool has_filename() const;
```

## <a name="pathhas_parent_path"></a><a name="has_parent_path"></a> Pfad:: has_parent_path

Gibt `!parent_path().empty()`zurück.

```cpp
bool has_parent_path() const;
```

## <a name="pathhas_relative_path"></a><a name="has_relative_path"></a> Pfad:: has_relative_path

Gibt `!relative_path().empty()`zurück.

```cpp
bool has_relative_path() const;
```

## <a name="pathhas_root_directory"></a><a name="has_root_directory"></a> Pfad:: has_root_directory

Gibt `!root_directory().empty()`zurück.

```cpp
bool has_root_directory() const;
```

## <a name="pathhas_root_name"></a><a name="has_root_name"></a> Pfad:: has_root_name

Gibt `!root_name().empty()`zurück.

```cpp
bool has_root_name() const;
```

## <a name="pathhas_root_path"></a><a name="has_root_path"></a> Pfad:: has_root_path

Gibt `!root_path().empty()`zurück.

```cpp
bool has_root_path() const;
```

## <a name="pathhas_stem"></a><a name="has_stem"></a> Pfad:: has_stem

Gibt `!stem().empty()`zurück.

```cpp
bool has_stem() const;
```

## <a name="pathis_absolute"></a><a name="is_absolute"></a> Pfad:: is_absolute

Für Windows gibt die Funktion zurück `has_root_name() && has_root_directory()` . Für POSIX gibt die Funktion zurück `has_root_directory()` .

```cpp
bool is_absolute() const;
```

## <a name="pathis_relative"></a><a name="is_relative"></a> Pfad:: is_relative

Gibt `!is_absolute()`zurück.

```cpp
bool is_relative() const;
```

## <a name="pathiterator"></a><a name="iterator"></a> Path:: Iterator

Ein bidirektionaler konstanter Iterator, der die Pfad Komponenten von festlegt `myname` .

```cpp
class iterator
   {
   // bidirectional iterator for path
   typedef bidirectional_iterator_tag iterator_category;
   typedef path_type value_type;
   typedef ptrdiff_t difference_type;
   typedef const value_type *pointer;
   typedef const value_type& reference;
   // ...
   };
```

### <a name="remarks"></a>Bemerkungen

Die Klasse beschreibt einen bidirektionalen Konstanten Iterator, der die `path` Komponenten von `myname` in der Sequenz festlegt:

1. den Stammnamen, falls vorhanden

1. das Stammverzeichnis, falls vorhanden

1. die übrigen Verzeichnis Elemente des übergeordneten Elements (sofern vorhanden), die `path` mit dem Dateinamen enden, falls vorhanden.

Für `pval` ein Objekt vom Typ `path` :

1. `path::iterator X = pval.begin()` legt das erste `path` Element im Pfadnamen fest, falls vorhanden.

1. `X == pval.end()` ist true, wenn auf `X` das Ende der Komponenten Sequenz verweist.

1. `*X` gibt eine Zeichenfolge zurück, die der aktuellen Komponente entspricht.

1. `++X` legt die nächste Komponente in der Sequenz fest, falls vorhanden.

1. `--X` legt die vorhergehende Komponente in der Sequenz fest, falls vorhanden.

1. Durch die Änderung werden `myname` alle Iteratoren ungültig, die Elemente in festlegen `myname` .

## <a name="pathmake_preferred"></a><a name="make_preferred"></a> Pfad:: make_preferred

Konvertiert jedes Trennzeichen nach `preferred_separator` Bedarf in eine.

```cpp
path& make_preferred();
```

## <a name="pathnative"></a><a name="native"></a> Path:: Native

Gibt `myname`zurück.

```cpp
const string_type& native() const noexcept;
```

## <a name="pathoperator"></a><a name="op_as"></a> Path:: Operator =

Ersetzt die Elemente des Pfads durch eine Kopie eines anderen Pfades.

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>Parameter

*Richting*\
Der [Pfad](../standard-library/path-class.md) , der in die kopiert wird `path` .

*Ausgangs*\
Der Quellpfad.

### <a name="remarks"></a>Bemerkungen

Der erste Member-Operator kopiert `right.myname` in `myname` . Der zweite Member-Operator wechselt `right.myname` zu `myname` . Der dritte Member-Operator verhält sich wie `*this = path(source)` .

## <a name="pathoperator"></a><a name="op_add"></a> Path:: Operator + =

Verschiedene `concat` Ausdrücke.

```cpp
path& operator+=(const path& right);
path& operator+=(const string_type& str);
path& operator+=(const value_type *ptr);
path& operator+=(value_type elem);

template <class Source>
path& operator+=(const Source& source);

template <class Elem>
path& operator+=(Elem elem);
```

### <a name="parameters"></a>Parameter

*Richting*\
Der hinzugefügte Pfad.

*SRT*\
Die hinzugefügte Zeichenfolge.

*PTR*\
Der hinzugefügte Zeiger.

*Elem*\
Der hinzugefügte `value_type` oder `Elem` .

*Ausgangs*\
Die hinzugefügte Quelle.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktionen verhalten sich wie die folgenden entsprechenden Ausdrücke:

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string<Elem>(1, elem)));`

## <a name="pathoperator"></a><a name="op_divide"></a> Path:: Operator/=

Verschiedene `append` Ausdrücke.

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>Parameter

*Richting*\
Der hinzugefügte Pfad.

*Ausgangs*\
Die hinzugefügte Quelle.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktionen verhalten sich wie die folgenden entsprechenden Ausdrücke:

1. `append(right);`

1. `append(source);`

## <a name="pathoperator-string_type"></a><a name="op_string"></a> Path:: Operator string_type

Gibt `myname`zurück.

```cpp
operator string_type() const;
```

## <a name="pathparent_path"></a><a name="parent_path"></a> Pfad::p arent_path

Gibt die übergeordnete Pfadkomponente von zurück `myname` .

```cpp
path parent_path() const;
```

### <a name="remarks"></a>Bemerkungen

Gibt die übergeordnete Pfadkomponente von zurück `myname` , insbesondere das Präfix von `myname` nach dem Entfernen `filename().native()` und alle unmittelbar vorangehenden Verzeichnis Trennzeichen. (Auch wenn `begin() != end()` , ist dies die Kombination aller Elemente im Bereich, `[begin(), --end())` indem Sie nacheinander anwenden `operator/=` .) Die Komponente ist möglicherweise leer.

## <a name="pathpath"></a><a name="path"></a> Pfad::p ATH

Erstellt eine `path` auf verschiedene Weise.

```cpp
path();

path(const path& right);
path(path&& right) noexcept;

template <class Source>
path(const Source& source);

template <class Source>
path(const Source& source, const locale& loc);

template <class InIt>
path(InIt first, InIt last);

template <class InIt>
path(InIt first, InIt last, const locale& loc);
```

### <a name="parameters"></a>Parameter

*Richting*\
Der Pfad, in dem der konstruierte Pfad eine Kopie sein soll.

*Ausgangs*\
Die Quelle, deren Kopie der erstellte Pfad sein soll.

*a.a.o.*\
Das angegebene Gebiets Schema.

*erstes*\
Die Position des ersten zu kopierenden Elements.

*letzten*\
Die Position des letzten Elements, das kopiert werden soll.

### <a name="remarks"></a>Bemerkungen

Die Konstruktoren werden `myname` auf unterschiedliche Weise konstruiert:

Dies `path()` ist `myname()` .

Für `path(const path& right` ) ist der Wert `myname(right.myname)` .

Dies `path(path&& right)` ist `myname(right.myname)` .

Dies `template<class Source> path(const Source& source)` ist `myname(source)` .

`template<class Source> path(const Source& source, const locale& loc)`Dies ist der Fall, wenn Sie `myname(source)` alle benötigten Codecvt-Facetten von erhalten `loc` .

Dies `template<class InIt> path(InIt first, InIt last)` ist `myname(first, last)` .

`template<class InIt> path(InIt first, InIt last, const locale& loc)`Dies ist der Fall, wenn Sie `myname(first, last)` alle benötigten Codecvt-Facetten von erhalten `loc` .

## <a name="pathpreferred_separator"></a><a name="preferred_separator"></a> Pfad::p referred_separator

Das konstante Objekt gibt je nach Betriebssystem des Hosts das bevorzugte Zeichen zum Trennen von Pfadkomponenten zurück.

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume POSIX
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass es in den meisten Kontexten unter Windows gleichermaßen zulässig ist, an dieser Stelle „L'/'“ zu verwenden.

## <a name="pathrelative_path"></a><a name="relative_path"></a> Pfad:: RELATIVE_PATH

Gibt die relative Pfadkomponente von zurück `myname` .

```cpp
path relative_path() const;
```

### <a name="remarks"></a>Bemerkungen

Gibt die relative Pfadkomponente von zurück `myname` , insbesondere das Suffix von `myname` nach dem Entfernen und die `root_path().native()` unmittelbar nachfolgenden redundante Verzeichnis Trennzeichen. Die Komponente kann leer sein.

## <a name="pathremove_filename"></a><a name="remove_filename"></a> Pfad:: remove_filename

Entfernt den Dateinamen.

```cpp
path& remove_filename();
```

## <a name="pathreplace_extension"></a><a name="replace_extension"></a> Pfad:: replace_extension

Ersetzt die Erweiterung von `myname` .

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>Parameter

*NewExt*\
Die neue Erweiterung.

### <a name="remarks"></a>Bemerkungen

Entfernt zuerst das Suffix `extension().native()` aus `myname` . Wenn `!newext.empty() && newext[0] != dot` (wobei `dot` ist `*path(".").c_str()` ), dann `dot` wird an `myname` angefügt. Anschließend wird " *netwext* " an angefügt `myname` .

## <a name="pathreplace_filename"></a><a name="replace_filename"></a> Pfad:: replace_filename

Ersetzt den Dateinamen.

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>Parameter

*PVAL*\
Der Pfad des Datei namens.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion führt Folgendes aus:

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="pathroot_directory"></a><a name="root_directory"></a> Pfad:: root_directory

Gibt die Stammverzeichnis Komponente von zurück `myname` .

```cpp
path root_directory() const;
```

### <a name="remarks"></a>Bemerkungen

Die Komponente kann leer sein.

## <a name="pathroot_name"></a><a name="root_name"></a> Pfad:: root_name

Gibt die Stamm Namen Komponente von zurück `myname` .

```cpp
path root_name() const;
```

### <a name="remarks"></a>Bemerkungen

Die Komponente kann leer sein.

## <a name="pathroot_path"></a><a name="root_path"></a> Pfad:: root_path

Gibt die Stamm Pfadkomponente von zurück `myname` .

```cpp
path root_path() const;
```

### <a name="remarks"></a>Bemerkungen

Gibt die Stamm Pfadkomponente von zurück `myname` , insbesondere `root_name()`  /  `root_directory` . Die Komponente kann leer sein.

## <a name="pathstem"></a><a name="stem"></a> Path:: stem

Gibt die `stem` Komponente von zurück `myname` .

```cpp
path stem() const;
```

### <a name="remarks"></a>Bemerkungen

Gibt die `stem` Komponente von zurück `myname` , insbesondere `filename().native()` mit allen nachfolgenden `extension().native()` entfernten. Die Komponente kann leer sein.

## <a name="pathstring"></a><a name="string"></a> Path:: String

Konvertiert die in gespeicherte Sequenz `mypath` .

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>Bemerkungen

Die erste Member-Funktion (Template) konvertiert die gespeicherte Sequenz auf `mypath` die gleiche Weise wie die folgende:

1. `string()` für `string<char, Traits, Alloc>()`

1. `wstring()` für `string<wchar_t, Traits, Alloc>()`

1. `u16string()` für `string<char16_t, Traits, Alloc>()`

1. `u32string()` für `string<char32_t, Traits, Alloc>()`

Die zweite Member-Funktion konvertiert die in gespeicherte Sequenz in `mypath` die Codierung, die vom Host System für eine Sequenz bevorzugt wird, **`char`** und gibt diese in einem Objekt vom Typ gespeicherten zurück `string` .

## <a name="pathstring_type"></a><a name="string_type"></a> Pfad:: string_type

Der Typ ist ein Synonym für `basic_string<value_type>`.

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="pathswap"></a><a name="swap"></a> Path:: Swap

Führt aus `swap(mypath, right.mypath)` .

```cpp
void swap(path& right) noexcept;
```

## <a name="pathu16string"></a><a name="u16string"></a> Pfad:: u16string

Konvertiert die in gespeicherte Sequenz in `mypath` UTF-16 und gibt Sie in einem Objekt vom Typ zurück `u16string` .

```cpp
u16string u16string() const;
```

## <a name="pathu32string"></a><a name="u32string"></a> Pfad:: u32string

Konvertiert die in gespeicherte Sequenz in `mypath` UTF-32 und gibt Sie in einem Objekt vom Typ zurück `u32string` .

```cpp
u32string u32string() const;
```

## <a name="pathu8string"></a><a name="u8string"></a> Pfad:: "u8string"

Konvertiert die in gespeicherte Sequenz in `mypath` UTF-8 und gibt Sie in einem Objekt vom Typ zurück `u8string` .

```cpp
string u8string() const;
```

## <a name="pathvalue_type"></a><a name="value_type"></a> Pfad:: value_type

Der Typ beschreibt die `path` Elemente, die vom Host Betriebssystem bevorzugt werden.

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume POSIX
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="pathwstring"></a><a name="wstring"></a> Path:: wstring

Konvertiert die in gespeicherte Sequenz in `mypath` die Codierung, die vom Host System für eine Sequenz bevorzugt wird, **`wchar_t`** und gibt diese in einem Objekt vom Typ gespeicherten zurück `wstring` .

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>Weitere Informationen

[Headerdateienreferenz](../standard-library/cpp-standard-library-header-files.md)
