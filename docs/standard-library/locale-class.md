---
title: locale-Klasse
ms.date: 03/19/2019
f1_keywords:
- xlocale/std::locale
- xlocale/std::locale::category
- xlocale/std::locale::combine
- xlocale/std::locale::name
- xlocale/std::locale::classic
- xlocale/std::locale::global
- xlocale/std::locale::operator( )
- xlocale/std::locale::facet
- xlocale/std::locale::id
helpviewer_keywords:
- std::locale [C++]
- std::locale [C++], category
- std::locale [C++], combine
- std::locale [C++], name
- std::locale [C++], classic
- std::locale [C++], global
- std::locale [C++], facet
- std::locale [C++], id
ms.assetid: 7dd6d271-472d-4750-8fb5-ea8f55fbef62
ms.openlocfilehash: 2581c5cdacc9e542f5d911860128dcf5526621ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367319"
---
# <a name="locale-class"></a>locale-Klasse

Die Klasse, die ein Gebietsschemaobjekt beschreibt, das kulturspezifische Informationen als einen Satz von Facets kapselt, die zusammen eine bestimmte lokalisierte Umgebung definieren.

## <a name="syntax"></a>Syntax

```cpp
class locale;
```

## <a name="remarks"></a>Bemerkungen

Ein Facet ist ein Zeiger auf ein Objekt einer Klasse, die von der [facet](#facet_class)-Klasse abgeleitet wird. Diese verfügt über ein öffentliches Objekt in folgendem Format:

```cpp
static locale::id id;
```

Sie können einen offenen Satz dieser Facets definieren. Sie können auch ein Gebietsschemaobjekt erstellen, das eine beliebige Anzahl von Facets festgelegt.

Vordefinierte Gruppen dieser Facets stellen die [locale-Kategorien](#category) dar, die normalerweise in der Standard-C-Bibliothek von der Funktion `setlocale` verwaltet werden.

Kategorie `collate` (LC_COLLATE) umfasst die Facetten:

```cpp
collate<char>
collate<wchar_t>
```

Kategorie `ctype` (LC_CTYPE) umfasst die Facetten:

```cpp
ctype<char>
ctype<wchar_t>
codecvt<char, char, mbstate_t>
codecvt<wchar_t, char, mbstate_t>
codecvt<char16_t, char, mbstate_t>
codecvt<char32_t, char, mbstate_t>
```

Kategorie `monetary` (LC_MONETARY) umfasst die Facetten:

```cpp
moneypunct<char, false>
moneypunct<wchar_t, false>
moneypunct<char, true>
moneypunct<wchar_t, true>
money_get<char, istreambuf_iterator<char>>
money_get<wchar_t, istreambuf_iterator<wchar_t>>
money_put<char, ostreambuf_iterator<char>>
money_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

Kategorie `numeric` (LC_NUMERIC) umfasst die Facetten:

```cpp
num_get<char, istreambuf_iterator<char>>
num_get<wchar_t, istreambuf_iterator<wchar_t>>
num_put<char, ostreambuf_iterator<char>>
num_put<wchar_t, ostreambuf_iterator<wchar_t>>
numpunct<char>
numpunct<wchar_t>
```

Kategorie `time` (LC_TIME) umfasst die Facetten:

```cpp
time_get<char, istreambuf_iterator<char>>
time_get<wchar_t, istreambuf_iterator<wchar_t>>
time_put<char, ostreambuf_iterator<char>>
time_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

Kategorie `messages` (LC_MESSAGES) umfasst die Facetten:

```cpp
messages<char>
messages<wchar_t>
```

(Die letzte Kategorie wird von POSIX benötigt, nicht jedoch der C-Standard.)

Einige dieser vordefinierten Facetten werden von `iostream` den Klassen verwendet, um die Konvertierung numerischer Werte in und aus Textsequenzen zu steuern.

Ein Objekt der locale-Klasse speichert einen Gebietsschemanamen als Objekt der Klasse [string](../standard-library/string-typedefs.md#string). Durch Verwenden eines ungültigen Gebietsschemanamens zur Erstellung eines Gebietsschemafacets oder eines Gebietsschemaobjekts wird ein Objekt der Klasse [runtime_error](../standard-library/runtime-error-class.md) ausgelöst. Der gespeicherte Gebietsschemaname ist, `"*"` wenn das Gebietsschemaobjekt nicht sicher sein kann, dass ein Gebietsschema im C-Stil genau dem durch das Objekt dargestellten entspricht. Andernfalls können Sie ein übereinstimmendes Gebietsschema innerhalb der `locale_object`Standard-C-Bibliothek `setlocale(LC_ALL , locale_object.`für ein Gebietsschemaobjekt einrichten, indem Sie [den Namen](#name)`().c_str())`aufrufen.

In dieser Implementierung können Sie außerdem die statische Memberfunktion aufrufen:

```cpp
static locale empty();
```

zur Erstellung eines Gebietsschemaobjekts, das keine Facets hat. Es ist auch ein transparentes Gebietsschema. Wenn die Vorlage [has_facet](../standard-library/locale-functions.md#has_facet) funktioniert und [use_facet](../standard-library/locale-functions.md#use_facet) die angeforderte Facette nicht in einem transparenten Gebietsschema finden kann, konsultieren sie zuerst das globale Gebietsschema und dann, wenn dies transparent ist, das klassische Gebietsschema. Sie können also schreiben:

```cpp
cout.imbue(locale::empty());
```

Nachfolgende Einfügungen, die [`cout`](../standard-library/iostream.md#cout) durch den aktuellen Status des globalen Gebietsschemas vermittelt werden. Sie können sogar Folgendes schreiben:

```cpp
locale loc(locale::empty(),
    locale::classic(),
    locale::numeric);

cout.imbue(loc);
```

Numerische Formatierungsregeln für nachfolgende Einfügungen in `cout` bleiben gleich wie im C-Gebietsschema, auch wenn das globale Gebietsschema Änderungsregeln für das Einfügen von Datumsangaben und Währungswerten bietet.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[locale](#locale)|Erstellt ein Gebietsschema, eine Kopie eines Gebietsschemas oder eine Kopie des Gebietsschemas, in dem ein Facet oder eine Kategorie durch ein Facet oder eine Kategorie eines anderen Gebietsschemas ersetzt wurde.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[category](#category)|Ein ganzzahliger Typ, der Bitmaskenwerte bereitstellt, um Standardfacetfamilien anzugeben.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Kombinieren](#combine)|Fügt ein Facet eines angegebenen Gebietsschemas in ein Zielgebietsschema ein.|
|[name](#name)|Gibt den gespeicherten Gebietsschemanamen zurück.|

### <a name="static-functions"></a>Statische Funktionen

|||
|-|-|
|[Klassisch](#classic)|Die statische Memberfunktion gibt ein Gebietsschemaobjekt zurück, das das klassische C-Gebietsschema darstellt.|
|[Globalen](#global)|Setzt das Standardgebietsschema für das Programm zurück.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator=](#op_eq)|Weist ein Gebietsschema zu.|
|[Operator!=](#op_neq)|Prüft zwei Gebietsschemen auf Ungleichheit.|
|[Operator( )](#op_call)|Vergleicht zwei `basic_string`-Objekte.|
|[Betreiber== Einzelnachweise ==](#op_eq_eq)|Prüft zwei Gebietsschemen auf Gleichheit.|

### <a name="classes"></a>Klassen

|Klasse|BESCHREIBUNG|
|-|-|
|[Facet](#facet_class)|Eine Klasse, die als Basisklasse für alle Gebietsschemafacets dient.|
|[`id`](#id_class)|Die Memberklasse stellt eine einzigartige Facetidentifikation bereit, die als Index zum Suchen von Facets in einem Gebietsschema verwendet wird.|

## <a name="requirements"></a>Anforderungen

**Header:** \<locale>

**Namespace:** std

## <a name="localecategory"></a><a name="category"></a>Gebietsschema::Kategorie

Ein ganzzahliger Typ, der Bitmaskenwerte bereitstellt, um Standardfacetfamilien anzugeben.

```cpp
typedef int category;
static const int collate = LC_COLLATE;
static const int ctype = LC_CTYPE;
static const int monetary = LC_MONETARY;
static const int numeric = LC_NUMERIC;
static const int time = LC_TIME;
static const int messages = LC_MESSAGES;
static const int all = LC_ALL;
static const int none = 0;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für einen **int-Typ,** der eine Gruppe von unterschiedlichen Elementen eines Bitmaskentyps darstellen kann, die lokal zu Klassengebietsschema sind, oder verwendet werden kann, um eine der entsprechenden C-Gebietsschemakategorien darzustellen. Die Elemente sind:

- `collate`, entspricht der C-Kategorie LC_COLLATE

- `ctype`, entsprechend der C-Kategorie LC_CTYPE

- `monetary`, entspricht der C-Kategorie LC_MONETARY

- `numeric`, entspricht der C-Kategorie LC_NUMERIC

- `time`, entspricht der Klasse C LC_TIME

- `messages`, entspricht der POSIX-Kategorie LC_MESSAGES

Zwei weitere nützliche Werte sind:

- `none`, entspricht keiner der C-Kategorien

- `all`, entsprechend der C-Union aller Kategorien LC_ALL

Sie können eine beliebige Gruppe `OR` von Kategorien darstellen, `monetary` indem `time`Sie mit diesen Konstanten verwenden, wie in &#124; .

## <a name="localeclassic"></a><a name="classic"></a>Gebietsschema::klassisch

Die statische Memberfunktion gibt ein Gebietsschemaobjekt zurück, das das klassische C-Gebietsschema darstellt.

```cpp
static const locale& classic();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das C-Gebietsschema.

### <a name="remarks"></a>Bemerkungen

Das klassische C-Gebietsschema ist das US-englische ASCII-Gebietsschema in der Standard C-Bibliothek. Es ist das Gebietsschema, das implizit in Programmen verwendet wird, die nicht internationalisiert werden.

### <a name="example"></a>Beispiel

```cpp
// locale_classic.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "german" );
   locale loc2 = locale::global( loc1 );
   cout << "The name of the previous locale is: " << loc2.name( )
        << "." << endl;
   cout << "The name of the current locale is: " << loc1.name( )
        << "." << endl;

   if (loc2 == locale::classic( ) )
      cout << "The previous locale was classic." << endl;
   else
      cout << "The previous locale was not classic." << endl;

   if (loc1 == locale::classic( ) )
      cout << "The current locale is classic." << endl;
   else
      cout << "The current locale is not classic." << endl;
}
```

```Output
The name of the previous locale is: C.
The name of the current locale is: German_Germany.1252.
The previous locale was classic.
The current locale is not classic.
```

## <a name="localecombine"></a><a name="combine"></a>Gebietsschema::kombinieren

Fügt ein Facet eines angegebenen Gebietsschemas in ein Zielgebietsschema ein.

```cpp
template <class Facet>
locale combine(const locale& source_locale) const;
```

### <a name="parameters"></a>Parameter

*source_locale*\
Das Gebietsschema enthält das Facet, das in das Zielgebietsschema eingefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Die Memberfunktion gibt ein Gebietsschemaobjekt zurück, das die `Facet` in *source_locale*aufgeführte Facette ersetzt oder ** \*dazu** hinzufügt.

### <a name="example"></a>Beispiel

```cpp
// locale_combine.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main() {
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s; it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc ) << result1 << endl;

   locale loc2 ( "C" );
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc2 )  << result2 << endl;

   locale loc3 = loc2.combine<collate<_TCHAR> > (loc);
   int result3 = use_facet<collate<_TCHAR> > ( loc3 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc3 ) << result3 << endl;
}
```

## <a name="facet-class"></a><a name="facet_class"></a>Facette Klasse

Eine Klasse, die als Basisklasse für alle Gebietsschemafacets dient.

```cpp
class facet {
protected:
    explicit facet(size_t references = 0);
    virtual ~facet();
private:
    facet(const facet&) // not defined
    void operator=(const facet&) // not defined
};
```

### <a name="remarks"></a>Bemerkungen

Sie können kein Objekt der Klasse `facet`kopieren oder zuweisen. Sie können Objekte, die von der Klasse `locale::facet` abgeleitet wurden, erstellen oder zerstören, aber nicht die Objekte der richtigen Basisklasse. In der Regel `_Myfac` erstellen `facet` Sie ein `locale`Objekt, das beim Erstellen eines abgeleitet ist, wie in`locale loc(locale::classic(), new _Myfac);`

In solchen Fällen sollte der Konstruktor für die Basisklasse `facet` über ein Argument für *Nullverweise* verfügen. Wenn das Objekt nicht mehr benötigt wird, wird es gelöscht, sodass Sie ein Argument für *Verweise* ungleich Null nur in den seltenen Fällen angeben, in denen Sie die Verantwortung für die Lebensdauer des Objekts übernehmen.

## <a name="localeglobal"></a><a name="global"></a>gebietsschema::global

Setzt das Standardgebietsschema für das Programm zurück. Dieser Aufruf wirkt sich auf das globale Gebietsschema für C und C++ aus.

```cpp
static locale global(const locale& new_default_locale);
```

### <a name="parameters"></a>Parameter

*new_default_locale*\
Das Gebietsschema, das als Standardgebietsschema vom Programm verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Das vorherige Gebietsschema, bevor das Standardgebietsschema zurückgesetzt wurde.

### <a name="remarks"></a>Bemerkungen

Bei Programmstart ist das globale Gebietsschema gleich dem klassischen Gebietsschema. Die `global()`-Funktion ruft `setlocale( LC_ALL, loc.name. c_str())` auf, um ein entsprechendes Gebietsschema in der Standard-C-Bibliothek festzulegen.

### <a name="example"></a>Beispiel

```cpp
// locale_global.cpp
// compile by using: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_germany" );
   locale loc1;
   cout << "The initial locale is: " << loc1.name( ) << endl;
   locale loc2 = locale::global ( loc );
   locale loc3;
   cout << "The current locale is: " << loc3.name( ) << endl;
   cout << "The previous locale was: " << loc2.name( ) << endl;
}
```

```Output
The initial locale is: C
The current locale is: German_Germany.1252
The previous locale was: C
```

## <a name="id-class"></a><a name="id_class"></a>id-Klasse

Die Memberklasse stellt eine einzigartige Facetidentifikation bereit, die als Index zum Suchen von Facets in einem Gebietsschema verwendet wird.

```cpp
class id
{
   protected:    id();
   private:      id(const id&)
   void operator=(const id&)  // not defined
};
```

### <a name="remarks"></a>Bemerkungen

Die Memberklasse beschreibt das statische Memberobjekt, das von jedem Gebietsschemafacet benötigt wird. Sie können kein Objekt der Klasse `id`kopieren oder zuweisen.

## <a name="localelocale"></a><a name="locale"></a>Gebietsschema::locale

Erstellt ein Gebietsschema, eine Kopie eines Gebietsschemas oder eine Kopie des Gebietsschemas, in dem ein Facet oder eine Kategorie durch ein Facet oder eine Kategorie eines anderen Gebietsschemas ersetzt wurde. Enthält auch einen Destruktor.

```cpp
locale();

explicit locale(const char* locale_name, category new_category = all);
explicit locale(const string& locale_name);
locale(const locale& from_locale);
locale(const locale& from_locale, const locale& Other, category new_category);
locale(const locale& from_locale, const char* locale_name, category new_category);

template <class Facet>
locale(const locale& from_locale, const Facet* new_facet);

~locale();
```

### <a name="parameters"></a>Parameter

*locale_name*\
Der Name eines Gebietsschemas.

*from_locale*\
Ein Gebietsschema, das zum Erstellen des neuen Gebietsschemas kopiert werden soll.

*Andere*\
Ein Gebietsschema für die Auswahl einer Kategorie.

*new_category*\
Die Kategorie, die im erstellten Gebietsschema ersetzt werden soll.

*new_facet*\
Das Facet, das im erstellten Gebietsschema ersetzt werden soll.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert das Objekt, um mit dem globalen Gebietsschema übereinzustimmen. Der zweite und dritte Konstruktor initialisieren alle Gebietsschemakategorien, um ein Verhalten zu haben, das mit dem Gebietsschemanamen *locale_name*übereinstimmt. Die übrigen Konstruktoren kopieren *from_locale*mit den ausnahmen:

`locale(const locale& from_locale, const locale& Other, category new_category);`

ersetzt von *Anderen* die Facetten, die einer Kategorie C entsprechen, für die C & *new_category* ungleich Null ist.

`locale(const locale& from_locale, const char* locale_name, category new_category);`

`locale(const locale& from_locale, const string& locale_name, category new_category);`

ersetzt aus `locale(locale_name, all)` den Facetten, die einer Kategorie `replace_category & new_category` entsprechen *replace_category* für die ungleich Null ist.

`template<class Facet> locale(const locale& from_locale, Facet* new_facet);`

ersetzt (oder fügt) *from_locale* der Facette *new_facet*, wenn *new_facet* kein Nullzeiger ist.

Wenn Gebietsschemaname *locale_name* ein NULL-Zeiger oder anderweitig ungültig ist, löst die Funktion [runtime_error](../standard-library/runtime-error-class.md)aus.

### <a name="example"></a>Beispiel

```cpp
// locale_locale.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( ) {

   // Second constructor
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s, it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc ) << result1 << endl;

   // The first (default) constructor
   locale loc2;
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc2 )  << result2 << endl;

   // Third constructor
   locale loc3 (loc2,loc, _M_COLLATE );
   int result3 = use_facet<collate<_TCHAR> > ( loc3 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc3 ) << result3 << endl;

   // Fourth constructor
   locale loc4 (loc2, "German_Germany", _M_COLLATE );
   int result4 = use_facet<collate<_TCHAR> > ( loc4 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc4 ) << result4 << endl;
}
```

## <a name="localename"></a><a name="name"></a>Gebietsschema::Name

Gibt den gespeicherten Gebietsschemanamen zurück.

```cpp
string name() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Zeichenfolge, die den Namen des Gebietsschemas angibt.

### <a name="example"></a>Beispiel

```cpp
// locale_name.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "german" );
   locale loc2 = locale::global( loc1 );
   cout << "The name of the previous locale is: "
        << loc2.name( ) << "." << endl;
   cout << "The name of the current locale is: "
        << loc1.name( ) << "." << endl;
}
```

```Output
The name of the previous locale is: C.
The name of the current locale is: German_Germany.1252.
```

## <a name="localeoperator"></a><a name="op_eq"></a>Gebietsschema::operator=

Weist ein Gebietsschema zu.

```cpp
const locale& operator=(const locale& other) noexcept;
```

## <a name="localeoperator"></a><a name="op_neq"></a>gebietsschema::operator!=

Prüft zwei Gebietsschemen auf Ungleichheit.

```cpp
bool operator!=(const locale& right) const;
```

### <a name="parameters"></a>Parameter

*Richting*\
Eines der Gebietsschemas, die auf Ungleichheit geprüft werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein boolescher Wert, der **wahr** ist, wenn die Gebietsschemas keine Kopien desselben Gebietsschemas sind. Es ist **falsch,** wenn die Gebietsschemas Kopien desselben Gebietsschemas sind.

### <a name="remarks"></a>Bemerkungen

Zwei Gebietsschemas sind gleich, wenn sie dasselbe Gebietsschema sind, wenn es sich um eine Kopie des anderen Gebietsschemas handelt oder wenn sie identische Namen haben.

### <a name="example"></a>Beispiel

```cpp
// locale_op_ne.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "German_Germany" );
   locale loc2( "German_Germany" );
   locale loc3( "English" );

   if ( loc1 != loc2 )
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc2 (" << loc2.name( ) << ") are not equal." << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc2 (" << loc2.name( ) << ") are equal." << endl;

   if ( loc1 != loc3 )
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc3 (" << loc3.name( ) << ") are not equal." << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc3 (" << loc3.name( ) << ") are equal." << endl;
}
```

```Output
locales loc1 (German_Germany.1252) and
loc2 (German_Germany.1252) are equal.
locales loc1 (German_Germany.1252) and
loc3 (English_United States.1252) are not equal.
```

## <a name="localeoperator"></a><a name="op_call"></a>Gebietsschema::operator()

Vergleicht zwei `basic_string`-Objekte.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator()(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right) const;
```

### <a name="parameters"></a>Parameter

*Links*\
Die linke Zeichenfolge.

*Richting*\
Die rechte Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Die Memberfunktion gibt Folgendes zurück:

- -1, wenn die erste Sequenz im Vergleich kleiner ist als die zweite Sequenz.

- +1, wenn die zweite Sequenz kleiner als die erste Sequenz ist.

- 0, wenn die Sequenzen gleichwertig sind.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion führt Folgendes aus:

```cpp
const collate<CharType>& fac = use_fac<collate<CharType>>(*this);

return (fac.compare(left.begin(), left.end(), right.begin(), right.end()) < 0);
```

Das bedeutet, dass Sie ein Gebietsschemaobjekt als Funktionsobjekt verwenden können.

### <a name="example"></a>Beispiel

```cpp
// locale_op_compare.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

int main( )
{
   using namespace std;
   wchar_t *sa = L"ztesting";
   wchar_t *sb = L"\0x00DFtesting";
   basic_string<wchar_t> a( sa );
   basic_string<wchar_t> b( sb );

   locale loc( "German_Germany" );
   cout << loc( a,b ) << endl;

   const collate<wchar_t>& fac = use_facet<collate<wchar_t> >( loc );
   cout << ( fac.compare( sa, sa + a.length( ),
       sb, sb + b.length( ) ) < 0) << endl;
}
```

```Output
0
0
```

## <a name="localeoperator"></a><a name="op_eq_eq"></a>gebietsschema::operator==

Prüft zwei Gebietsschemen auf Gleichheit.

```cpp
bool operator==(const locale& right) const;
```

### <a name="parameters"></a>Parameter

*Richting*\
Eines der Gebietsschemas, die auf Gleichheit geprüft werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein boolescher Wert, der **wahr** ist, wenn es sich bei den Gebietsschemas um Kopien desselben Gebietsschemas handelt. Es ist **falsch,** wenn die Gebietsschemas keine Kopien desselben Gebietsschemas sind.

### <a name="remarks"></a>Bemerkungen

Zwei Gebietsschemas sind gleich, wenn sie dasselbe Gebietsschema sind, wenn es sich um eine Kopie des anderen Gebietsschemas handelt oder wenn sie identische Namen haben.

### <a name="example"></a>Beispiel

```cpp
// locale_op_eq.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "German_Germany" );
   locale loc2( "German_Germany" );
   locale loc3( "English" );

   if ( loc1 == loc2 )
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc2 (" << loc2.name( ) << ") are equal."
      << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc2 (" << loc2.name( ) << ") are not equal."
      << endl;

   if ( loc1 == loc3 )
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc3 (" << loc3.name( ) << ") are equal."
      << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc3 (" << loc3.name( ) << ") are not equal."
      << endl;
}
```

```Output
locales loc1 (German_Germany.1252)
and loc2 (German_Germany.1252) are equal.
locales loc1 (German_Germany.1252)
and loc3 (English_United States.1252) are not equal.
```

## <a name="see-also"></a>Siehe auch

[\<Gebietsschema>](../standard-library/locale.md)\
[Codepages](../c-runtime-library/code-pages.md)\
[Gebietsschemanamen, Sprachen und Länder-/Regionszeichenfolgen](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
