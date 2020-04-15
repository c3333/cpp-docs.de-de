---
title: path-Klasse
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: 669dfd2c8cd8576ebfb6684bab7cf63cdd51babc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372107"
---
# <a name="path-class"></a>path-Klasse

Die **Pfadklasse** speichert ein `string_type`Objekt `myname` vom Typ , das hier für die Zwecke der Exposition aufgerufen wird und für die Verwendung als Pfadname geeignet ist. `string_type`ist ein `basic_string<value_type>`Synonym `value_type` für , wobei ein Synonym für **wchar_t** unter Windows oder **char** auf POSIX ist.

Weitere Informationen und Codebeispiele finden Sie unter [Dateisystemnavigation (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntax

```cpp
class path;
```

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[path](#path)|Erstellt ein Objekt vom Typ `path`.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[const_iterator](#const_iterator)|Ein Synonym für `iterator`.|
|[Iterator](#iterator)|Ein bidirektionaler konstanter Iterator, der die `path` Komponenten von `myname`bezeichnet.|
|[string_type](#string_type)|Der Typ ist ein Synonym für `basic_string<value_type>`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Anfügen](#append)|Fügt die angegebene `mypath`Sequenz an an , konvertiert und fügt bei Bedarf eine preferred_separator ein.|
|[Zuweisen](#assign)|Ersetzt `mypath` durch die angegebene Sequenz, die bei Bedarf konvertiert wird.|
|[Beginnen](#begin)|Gibt `path::iterator` ein Element zurück, das das erste Pfadelement im Pfadnamen angibt, sofern vorhanden.|
|[c_str](#c_str)|Gibt einen Zeiger auf das `mypath`erste Zeichen in zurück.|
|[Klar](#clear)|Führt `mypath.clear()`.|
|[Vergleichen](#compare)|Gibt Vergleichswerte zurück.|
|[concat](#compare)|Fügt die angegebene `mypath`Sequenz nach Bedarf an , konvertiert (aber nicht ein Trennzeichen einfügen).|
|[empty](#empty)|Gibt `mypath.empty()` zurück.|
|[Ende](#end)|Gibt einen End-of-Sequence-Iterator vom Typ zurück. `iterator`|
|[Erweiterung](#extension)|Gibt das Suffix von `filename()`zurück.|
|[Dateiname](#filename)|Gibt die Stammverzeichniskomponente von „myname“ zurück, insbesondere `empty() path() : *--end()`. Die Komponente kann leer sein.|
|[generic_string](#generic_string)|Gibt `this->string<Elem, Traits, Alloc>(al)` zurück, wobei jeder umgekehrte Schrägstrich in einen Schrägstrich konvertiert wird (unter Windows).|
|[generic_u16string](#generic_u16string)|Gibt `u16string()` zurück, wobei jeder umgekehrte Schrägstrich in einen Schrägstrich konvertiert wird (unter Windows).|
|[generic_u32string](#generic_u32string)|Gibt `u32string()` zurück, wobei jeder umgekehrte Schrägstrich in einen Schrägstrich konvertiert wird (unter Windows).|
|[generic_u8string](#generic_u8string)|Gibt `u8string()` zurück, wobei jeder umgekehrte Schrägstrich in einen Schrägstrich konvertiert wird (unter Windows).|
|[generic_wstring](#generic_wstring)|Gibt `wstring()` zurück, wobei jeder umgekehrte Schrägstrich in einen Schrägstrich konvertiert wird (unter Windows).|
|[has_extension](#has_extension)|Gibt `!extension().empty()` zurück.|
|[has_filename](#has_filename)|Gibt `!filename().empty()` zurück.|
|[has_parent_path](#has_parent_path)|Gibt `!parent_path().empty()` zurück.|
|[has_relative_path](#has_relative_path)|Gibt `!relative_path().empty()` zurück.|
|[has_root_directory](#has_root_directory)|Gibt `!root_directory().empty()` zurück.|
|[has_root_name](#has_root_name)|Gibt `!root_name().empty()` zurück.|
|[has_root_path](#has_root_path)|Gibt `!root_path().empty()` zurück.|
|[has_stem](#has_stem)|Gibt `!stem().empty()` zurück.|
|[is_absolute](#is_absolute)|Für Windows gibt `has_root_name() && has_root_directory()`die Funktion zurück. Für POSIX gibt `has_root_directory()`die Funktion zurück.|
|[is_relative](#is_relative)|Gibt `!is_absolute()` zurück.|
|[make_preferred](#make_preferred)|Konvertiert jedes Trennzeichen nach Bedarf in einen preferred_separator.|
|[ursprünglich](#native)|Gibt `myname` zurück.|
|[parent_path](#parent_path)|Gibt die übergeordnete `myname`Pfadkomponente von zurück.|
|[preferred_separator](#preferred_separator)|Das konstante Objekt gibt je nach Betriebssystem des Hosts das bevorzugte Zeichen zum Trennen von Pfadkomponenten zurück. |
|[relative_path](#relative_path)|Gibt die relative `myname`Pfadkomponente von zurück. |
|[remove_filename](#remove_filename)|Entfernt den Dateinamen.|
|[replace_extension](#replace_extension)|Ersetzt die Erweiterung `myname`von . |
|[replace_filename](#replace_filename)|RReplacet den Dateinamen.|
|[root_directory](#root_directory)|Gibt die Stammverzeichniskomponente von `myname`zurück. |
|[root_name](#root_name)|Gibt die Stammnamenkomponente von `myname`zurück. |
|[root_path](#root_path)|Gibt die Stammpfadkomponente von `myname`zurück.|
|[stem](#stem)|Gibt `stem` die `myname`Komponente von zurück.|
|[string](#string)|Konvertiert die in `mypath`gespeicherte Sequenz.|
|[swap](#swap)|Führt `swap(mypath, right.mypath)`.|
|[u16string](#u16string)|Konvertiert die in `mypath` UTF-16 gespeicherte Sequenz und gibt `u16string`sie in einem Objekt vom Typ zurück.|
|[u32string](#u32string)|Konvertiert die in `mypath` UTF-32 gespeicherte Sequenz und gibt `u32string`sie in einem Objekt vom Typ zurück.|
|[u8string](#u8string)|Konvertiert die in `mypath` UTF-8 gespeicherte Sequenz und gibt `u8string`sie in einem Objekt vom Typ zurück.|
|[Value_type](#value_type)|Der Typ beschreibt die Pfadelemente, die vom Hostbetriebssystem bevorzugt werden.|
|[wstring](#wstring)|Konvertiert die in `mypath` der vom Hostsystem bevorzugte Sequenz in `wchar_t` die Codierung für eine Sequenz `wstring`und gibt sie in einem Objekt vom Typ zurück.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator=](#op_as)|Ersetzt die Elemente des Pfads durch eine Kopie eines anderen Pfads.|
|[Operator+=](#op_add)|Verschiedene `concat` Ausdrücke.|
|[Operator/=](#op_divide)|Verschiedene `append` Ausdrücke.|
|[Betreiber string_type](#op_string)|Gibt `myname` zurück.|

## <a name="requirements"></a>Anforderungen

**Header:** \<Dateisystem>

**Namespace:** std::experimental::filesystem

## <a name="pathappend"></a><a name="append"></a>Pfad::Anfügen

Fügt die angegebene `mypath`Sequenz an an `preferred_separator` , konvertiert und fügt bei Bedarf ein.

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>Parameter

*Quelle*\
Angegebene Sequenz.

*Ersten*\
Beginn der angegebenen Sequenz.

*letzte*\
Ende der angegebenen Sequenz.

## <a name="pathassign"></a><a name="assign"></a>Pfad::zuweisen

Ersetzt `mypath` durch die angegebene Sequenz, die bei Bedarf konvertiert wird.

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>Parameter

*Quelle*\
Angegebene Sequenz.

*Ersten*\
Beginn der angegebenen Sequenz.

*letzte*\
Ende der angegebenen Sequenz.

## <a name="pathbegin"></a><a name="begin"></a>Pfad::begin

Gibt `path::iterator` ein Element zurück, das das erste Pfadelement im Pfadnamen angibt, sofern vorhanden.

```cpp
iterator begin() const;
```

## <a name="pathc_str"></a><a name="c_str"></a>Pfad::c_str

Gibt einen Zeiger auf das `mypath`erste Zeichen in zurück.

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="pathclear"></a><a name="clear"></a>Weg::klar

Führt `mypath.clear()`.

```cpp
void clear() noexcept;
```

## <a name="pathcompare"></a><a name="compare"></a>Pfad::vergleichen

Diese erste Funktion gibt `mypath.compare(pval.native())` zurück. Die zweite Funktion gibt `mypath.compare(str)` zurück. Die dritte `mypath.compare(ptr)`Funktion gibt zurück.

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Parameter

*pval*\
Pfad zum Vergleichen.

*Str*\
Zeichenfolge zum Vergleichen.

*Ptr*\
Zeiger zum Vergleichen.

## <a name="pathconcat"></a><a name="concat"></a>Pfad::konat

Fügt die angegebene `mypath`Sequenz nach Bedarf an , konvertiert (aber nicht ein Trennzeichen einfügen).

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>Parameter

*Quelle*\
Angegebene Sequenz.

*Ersten*\
Beginn der angegebenen Sequenz.

*letzte*\
Ende der angegebenen Sequenz.

## <a name="pathconst_iterator"></a><a name="const_iterator"></a>Pfad::const_iterator

Ein Synonym für `iterator`.

```cpp
typedef iterator const_iterator;
```

## <a name="pathempty"></a><a name="empty"></a>Pfad::leer

Gibt `mypath.empty()` zurück.

```cpp
bool empty() const noexcept;
```

## <a name="pathend"></a><a name="end"></a>Pfad::ende

Gibt einen End-of-Sequence-Iterator vom Typ zurück. `iterator`

```cpp
iterator end() const;
```

## <a name="pathextension"></a><a name="extension"></a>Pfad::Erweiterung

Gibt das Suffix von `filename()`zurück.

```cpp
path extension() const;
```

### <a name="remarks"></a>Bemerkungen

Gibt das Suffix `filename() X` solcher:

Wenn `X == path(".") || X == path("..")` oder `X` ob kein Punkt enthält, ist das Suffix leer.

Andernfalls beginnt das Suffix mit dem rechten Punkt (und umfasst diesen).

## <a name="pathfilename"></a><a name="filename"></a>Pfad::Dateiname

Gibt die Stammverzeichniskomponente von „myname“ zurück, insbesondere `empty() path() : *--end()`. Die Komponente kann leer sein.

```cpp
path filename() const;
```

## <a name="pathgeneric_string"></a><a name="generic_string"></a>Weg::generic_string

Gibt `this->string<Elem, Traits, Alloc>(al)` zurück, wobei jeder umgekehrte Schrägstrich in einen Schrägstrich konvertiert wird (unter Windows).

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="pathgeneric_u16string"></a><a name="generic_u16string"></a>Pfad::generic_u16string

Gibt `u16string()` zurück, wobei jeder umgekehrte Schrägstrich in einen Schrägstrich konvertiert wird (unter Windows).

```cpp
u16string generic_u16string() const;
```

## <a name="pathgeneric_u32string"></a><a name="generic_u32string"></a>Pfad::generic_u32string

Gibt `u32string()` zurück, wobei jeder umgekehrte Schrägstrich in einen Schrägstrich konvertiert wird (unter Windows).

```cpp
u32string generic_u32string() const;
```

## <a name="pathgeneric_u8string"></a><a name="generic_u8string"></a>Pfad::generic_u8string

Gibt `u8string()` zurück, wobei jeder umgekehrte Schrägstrich in einen Schrägstrich konvertiert wird (unter Windows).

```cpp
string generic_u8string() const;
```

## <a name="pathgeneric_wstring"></a><a name="generic_wstring"></a>Weg::generic_wstring

Gibt `wstring()` zurück, wobei jeder umgekehrte Schrägstrich in einen Schrägstrich konvertiert wird (unter Windows).

```cpp
wstring generic_wstring() const;
```

## <a name="pathhas_extension"></a><a name="has_extension"></a>Pfad::has_extension

Gibt `!extension().empty()` zurück.

```cpp
bool has_extension() const;
```

## <a name="pathhas_filename"></a><a name="has_filename"></a>Pfad::has_filename

Gibt `!filename().empty()` zurück.

```cpp
bool has_filename() const;
```

## <a name="pathhas_parent_path"></a><a name="has_parent_path"></a>Pfad::has_parent_path

Gibt `!parent_path().empty()` zurück.

```cpp
bool has_parent_path() const;
```

## <a name="pathhas_relative_path"></a><a name="has_relative_path"></a>Pfad::has_relative_path

Gibt `!relative_path().empty()` zurück.

```cpp
bool has_relative_path() const;
```

## <a name="pathhas_root_directory"></a><a name="has_root_directory"></a>Weg::has_root_directory

Gibt `!root_directory().empty()` zurück.

```cpp
bool has_root_directory() const;
```

## <a name="pathhas_root_name"></a><a name="has_root_name"></a>Pfad::has_root_name

Gibt `!root_name().empty()` zurück.

```cpp
bool has_root_name() const;
```

## <a name="pathhas_root_path"></a><a name="has_root_path"></a>Pfad::has_root_path

Gibt `!root_path().empty()` zurück.

```cpp
bool has_root_path() const;
```

## <a name="pathhas_stem"></a><a name="has_stem"></a>Pfad::has_stem

Gibt `!stem().empty()` zurück.

```cpp
bool has_stem() const;
```

## <a name="pathis_absolute"></a><a name="is_absolute"></a>Weg::is_absolute

Für Windows gibt `has_root_name() && has_root_directory()`die Funktion zurück. Für POSIX gibt `has_root_directory()`die Funktion zurück.

```cpp
bool is_absolute() const;
```

## <a name="pathis_relative"></a><a name="is_relative"></a>Pfad::is_relative

Gibt `!is_absolute()` zurück.

```cpp
bool is_relative() const;
```

## <a name="pathiterator"></a><a name="iterator"></a>Weg::iterator

Ein bidirektionaler konstanter Iterator, `myname`der die Pfadkomponenten von bezeichnet.

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

Die Klasse beschreibt einen bidirektionalen Konstanteniterator, der die `path` Komponenten von `myname` in der Sequenz bezeichnet:

1. den Stammnamen, falls vorhanden

1. das Stammverzeichnis, falls vorhanden

1. die übrigen Verzeichniselemente `path`des übergeordneten , falls vorhanden, und endend mit dem Dateinamen, falls vorhanden

Für `pval` ein Objekt `path`vom Typ :

1. `path::iterator X = pval.begin()`bezeichnet das `path` erste Element im Pfadnamen, falls vorhanden.

1. `X == pval.end()`ist wahr, wenn `X` Punkte kurz hinter dem Ende der Sequenz von Komponenten liegen.

1. `*X`Gibt eine Zeichenfolge zurück, die mit der aktuellen Komponente übereinstimmt

1. `++X` legt die nächste Komponente in der Sequenz fest, falls vorhanden.

1. `--X` legt die vorhergehende Komponente in der Sequenz fest, falls vorhanden.

1. Durch `myname` ändern werden alle Iteratoren ungültig, die Elemente in `myname`bezeichnen.

## <a name="pathmake_preferred"></a><a name="make_preferred"></a>Pfad::make_preferred

Konvertiert jedes Trennzeichen `preferred_separator` nach Bedarf in ein.

```cpp
path& make_preferred();
```

## <a name="pathnative"></a><a name="native"></a>Pfad::native

Gibt `myname` zurück.

```cpp
const string_type& native() const noexcept;
```

## <a name="pathoperator"></a><a name="op_as"></a>Pfad::operator=

Ersetzt die Elemente des Pfads durch eine Kopie eines anderen Pfads.

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>Parameter

*Richting*\
Der [Pfad,](../standard-library/path-class.md) der `path`in die kopiert wird.

*Quelle*\
Der Quellpfad.

### <a name="remarks"></a>Bemerkungen

Der erste Memberoperator kopiert `right.myname` in `myname`. Der zweite Memberoperator wechselt `right.myname` zu `myname`. Der dritte Memberoperator verhält `*this = path(source)`sich wie .

## <a name="pathoperator"></a><a name="op_add"></a>Pfad::operator+=

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

*Str*\
Die hinzugefügte Zeichenfolge.

*Ptr*\
Der hinzugefügte Zeiger.

*Elem*\
Die `value_type` hinzugefügte oder `Elem`.

*Quelle*\
Die hinzugefügte Quelle.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktionen verhalten sich wie die folgenden entsprechenden Ausdrücke:

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string<Elem>(1, elem)));`

## <a name="pathoperator"></a><a name="op_divide"></a>Pfad::operator/=

Verschiedene `append` Ausdrücke.

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>Parameter

*Richting*\
Der hinzugefügte Pfad.

*Quelle*\
Die hinzugefügte Quelle.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktionen verhalten sich wie die folgenden entsprechenden Ausdrücke:

1. `append(right);`

1. `append(source);`

## <a name="pathoperator-string_type"></a><a name="op_string"></a>Pfad::Operator string_type

Gibt `myname` zurück.

```cpp
operator string_type() const;
```

## <a name="pathparent_path"></a><a name="parent_path"></a>pfad::parent_path

Gibt die übergeordnete `myname`Pfadkomponente von zurück.

```cpp
path parent_path() const;
```

### <a name="remarks"></a>Bemerkungen

Gibt die übergeordnete `myname`Pfadkomponente von zurück, insbesondere das Präfix nach dem `myname` Entfernen `filename().native()` und alle unmittelbar vorhergehenden Verzeichnistrennzeichen. (Gleich, `begin() != end()`wenn , ist es die Kombination `[begin(), --end())` aller Elemente `operator/=`im Bereich durch sukzessive Anwendung .) Die Komponente ist möglicherweise leer.

## <a name="pathpath"></a><a name="path"></a>Pfad::path

Konstruiert eine `path` auf verschiedene Weise.

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
Der Pfad, von dem der erstellte Pfad eine Kopie sein soll.

*Quelle*\
Die Quelle, von der der erstellte Pfad eine Kopie sein soll.

*Loc*\
Das angegebene Gebietsschema.

*Ersten*\
Die Position des ersten zu kopierenden Elements.

*letzte*\
Die Position des letzten zu kopierenden Elements.

### <a name="remarks"></a>Bemerkungen

Die Konstruktoren `myname` konstruieren alle auf verschiedene Weise:

Denn `path()` es `myname()`ist .

Für `path(const path& right`) `myname(right.myname)`ist es .

Denn `path(path&& right)` es `myname(right.myname)`ist .

Denn `template<class Source> path(const Source& source)` es `myname(source)`ist .

Denn `template<class Source> path(const Source& source, const locale& loc)` es `myname(source)`ist , alle benötigten Codecvt `loc`Facetten von zu erhalten.

Denn `template<class InIt> path(InIt first, InIt last)` es `myname(first, last)`ist .

Denn `template<class InIt> path(InIt first, InIt last, const locale& loc)` es `myname(first, last)`ist , alle benötigten Codecvt `loc`Facetten von zu erhalten.

## <a name="pathpreferred_separator"></a><a name="preferred_separator"></a>pfad::preferred_separator

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

## <a name="pathrelative_path"></a><a name="relative_path"></a>Pfad::relative_path

Gibt die relative `myname`Pfadkomponente von zurück.

```cpp
path relative_path() const;
```

### <a name="remarks"></a>Bemerkungen

Gibt die relative `myname`Pfadkomponente von zurück, `myname` insbesondere `root_path().native()` das Suffix nach dem Entfernen und alle unmittelbar nachfolgenden redundanten Verzeichnistrennzeichen. Die Komponente kann leer sein.

## <a name="pathremove_filename"></a><a name="remove_filename"></a>Pfad::remove_filename

Entfernt den Dateinamen.

```cpp
path& remove_filename();
```

## <a name="pathreplace_extension"></a><a name="replace_extension"></a>Pfad::replace_extension

Ersetzt die Erweiterung `myname`von .

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>Parameter

*newext*\
Die neue Erweiterung.

### <a name="remarks"></a>Bemerkungen

Entfernt zuerst das Suffix `extension().native()` aus `myname`. Wenn `!newext.empty() && newext[0] != dot` (wo `dot` `*path(".").c_str()`ist `dot` ), dann `myname`an an angehängt wird. Then *newext* is appended to `myname`.

## <a name="pathreplace_filename"></a><a name="replace_filename"></a>Pfad::replace_filename

Ersetzt den Dateinamen.

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>Parameter

*pval*\
Der Pfad des Dateinamens.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion führt Folgendes aus:

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="pathroot_directory"></a><a name="root_directory"></a>Pfad::root_directory

Gibt die Stammverzeichniskomponente von `myname`zurück.

```cpp
path root_directory() const;
```

### <a name="remarks"></a>Bemerkungen

Die Komponente kann leer sein.

## <a name="pathroot_name"></a><a name="root_name"></a>Weg::root_name

Gibt die Stammnamenkomponente von `myname`zurück.

```cpp
path root_name() const;
```

### <a name="remarks"></a>Bemerkungen

Die Komponente kann leer sein.

## <a name="pathroot_path"></a><a name="root_path"></a>Weg::root_path

Gibt die Stammpfadkomponente von `myname`zurück.

```cpp
path root_path() const;
```

### <a name="remarks"></a>Bemerkungen

Gibt die `myname`Stammpfadkomponente `root_name()`  /  `root_directory`von zurück, insbesondere . Die Komponente kann leer sein.

## <a name="pathstem"></a><a name="stem"></a>Pfad::Stamm

Gibt `stem` die `myname`Komponente von zurück.

```cpp
path stem() const;
```

### <a name="remarks"></a>Bemerkungen

Gibt `stem` die `myname`Komponente `filename().native()` von zurück, `extension().native()` insbesondere mit entferntem Trailing. Die Komponente kann leer sein.

## <a name="pathstring"></a><a name="string"></a>Pfad::string

Konvertiert die in `mypath`gespeicherte Sequenz.

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>Bemerkungen

Die erste (Vorlagen-)Memberfunktion konvertiert `mypath` die sequenz, die auf die gleiche Weise gespeichert wird wie:

1. `string()` für `string<char, Traits, Alloc>()`

1. `wstring()` für `string<wchar_t, Traits, Alloc>()`

1. `u16string()` für `string<char16_t, Traits, Alloc>()`

1. `u32string()` für `string<char32_t, Traits, Alloc>()`

Die zweite Memberfunktion konvertiert die `mypath` in der vom Hostsystem bevorzugte Sequenz in die Codierung für eine `string` **char-Sequenz** und gibt sie in einem Objekt vom Typ zurück.

## <a name="pathstring_type"></a><a name="string_type"></a>Pfad::string_type

Der Typ ist ein Synonym für `basic_string<value_type>`.

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="pathswap"></a><a name="swap"></a>Pfad::swap

Führt `swap(mypath, right.mypath)`.

```cpp
void swap(path& right) noexcept;
```

## <a name="pathu16string"></a><a name="u16string"></a>Pfad::u16string

Konvertiert die in `mypath` UTF-16 gespeicherte Sequenz und gibt `u16string`sie in einem Objekt vom Typ zurück.

```cpp
u16string u16string() const;
```

## <a name="pathu32string"></a><a name="u32string"></a>Pfad::u32string

Konvertiert die in `mypath` UTF-32 gespeicherte Sequenz und gibt `u32string`sie in einem Objekt vom Typ zurück.

```cpp
u32string u32string() const;
```

## <a name="pathu8string"></a><a name="u8string"></a>Pfad::u8string

Konvertiert die in `mypath` UTF-8 gespeicherte Sequenz und gibt `u8string`sie in einem Objekt vom Typ zurück.

```cpp
string u8string() const;
```

## <a name="pathvalue_type"></a><a name="value_type"></a>Weg::value_type

Der Typ `path` beschreibt die vom Hostbetriebssystem bevorzugten Elemente.

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume POSIX
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="pathwstring"></a><a name="wstring"></a>pfad::wstring

Konvertiert die in `mypath` der vom Hostsystem bevorzugte Sequenz in die Codierung für eine **wchar_t** `wstring`Sequenz und gibt sie in einem Objekt vom Typ zurück.

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>Siehe auch

[Headerdateienreferenz](../standard-library/cpp-standard-library-header-files.md)
