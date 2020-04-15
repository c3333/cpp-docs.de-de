---
title: '&lt;string&gt;-Funktionen'
ms.date: 11/04/2016
f1_keywords:
- string/std::getline
- string/std::stod
- string/std::stof
- string/std::stoi
- string/std::stol
- string/std::stold
- string/std::stoll
- string/std::stoul
- string/std::stoull
- string/std::swap
- string/std::to_string
- string/std::to_wstring
ms.assetid: 1a4ffd11-dce5-4cc6-a043-b95de034c7c4
helpviewer_keywords:
- std::getline [C++]
- std::stod [C++]
- std::stof [C++]
- std::stoi [C++]
- std::stol [C++]
- std::stold [C++]
- std::stoll [C++]
- std::stoul [C++]
- std::stoull [C++]
- std::swap [C++]
- std::to_string [C++]
- std::to_wstring [C++]
ms.openlocfilehash: 3f1dca71a6bb9d5461150378191b9373f907ecd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376664"
---
# <a name="ltstringgt-functions"></a>&lt;string&gt;-Funktionen

||||
|-|-|-|
|[Getline](#getline)|[stod](#stod)|[stof](#stof)|
|[Stoi](#stoi)|[stol](#stol)|[stold](#stold)|
|[stoll](#stoll)|[stoul](#stoul)|[stoull](#stoull)|
|[swap](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

## <a name="getline"></a><a name="getline"></a>Getline

Extrahiert Zeichenfolgen zeilenweise aus dem Eingabestream.

```cpp
// (1) delimiter as parameter
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& in_stream,
    basic_string<CharType, Traits, Allocator>& str,
    CharType delimiter);

template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>&& in_stream,
    basic_string<CharType, Traits, Allocator>& str,
    const CharType delimiter);

// (2) default delimiter used
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& in_stream,
    basic_string<CharType, Traits, Allocator>& str);

template <class Allocator, class Traits, class Allocator>
basic_istream<Allocator, Traits>& getline(
    basic_istream<Allocator, Traits>&& in_stream,
    basic_string<Allocator, Traits, Allocator>& str);
```

### <a name="parameters"></a>Parameter

*in_stream*\
Der Eingabestream, aus dem eine Zeichenfolge extrahiert werden soll.

*Str*\
Die Zeichenfolge, in die die Zeichen aus dem Eingabestream gelesen werden.

*Trennzeichen*\
Das Zeilentrennzeichen.

### <a name="return-value"></a>Rückgabewert

Der Eingabestream *in_stream*.

### <a name="remarks"></a>Bemerkungen

Das Paar von `(1)` Funktionssignaturen, die als Extraktzeichen markiert *sind, aus in_stream* bis das *Trennzeichen* gefunden wird, wird in *str*gespeichert.

Das Paar der `(2)` markierten Funktionssignaturen verwendet newline als `getline(in_stream, str, in_stream. widen('\n'))`Standardzeilentrennzeichen und verhält sich als .

Die zweite Funktion jedes Paars ist analog zur ersten, um [rvalue-Verweise](../cpp/lvalues-and-rvalues-visual-cpp.md) zu unterstützen.

Die Extraktion wird beendet, sobald eines der folgenden Ereignisse eintritt:

- Am Ende der Datei, in diesem *in_stream* Fall wird `ios_base::eofbit`die interne Statusflagge von in_stream auf gesetzt.

- Nachdem die Funktion ein Element extrahiert hat, das gleich dem *Trennzeichen*vergleicht. Das Element wird nicht zurückgesetzt oder an die gesteuerte Sequenz angehängt.

- Nachdem die Funktion `str.` [max_size](../standard-library/basic-string-class.md#max_size) Elemente extrahiert. Die interne Statusflagge von `ios_base::failbit` *in_stream* ist auf festgelegt.

- Ein anderer Fehler als der zuvor aufgeführte; die interne Statusflagge von `ios_base::badbit` *in_stream* auf .

Informationen zu internen Statusflags finden Sie unter [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

Wenn die Funktion keine Elemente extrahiert, *in_stream* wird das `ios_base::failbit`interne Zustandsflag von in_stream auf festgelegt. In jedem `getline` Fall gibt *in_stream*zurück.

Wenn eine Ausnahme ausgelöst wird, bleiben *in_stream* und *str* in einem gültigen Zustand.

### <a name="example"></a>Beispiel

Der folgende Code zeigt `getline()` in zwei Modi: zuerst mit dem Standardtrennzeichen (newline) und dann mit einem Leerzeichen als Trennzeichen. Mit dem Dateiendezeichen (STRG-Z auf der Tastatur) wird die Beendigung der while-Schleifen gesteuert. Dieser Wert legt das `cin` interne `eofbit`Zustandsflag von fest, das mit [basic_ios::clear()](../standard-library/basic-ios-class.md#clear) gelöscht werden muss, bevor die zweite while-Schleife ordnungsgemäß funktioniert.

```cpp
// compile with: /EHsc /W4
#include <string>
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    string str;
    vector<string> v1;
    cout << "Enter a sentence, press ENTER between sentences. (Ctrl-Z to stop): " << endl;
    // Loop until end-of-file (Ctrl-Z) is input, store each sentence in a vector.
    // Default delimiter is the newline character.
    while (getline(cin, str)) {
        v1.push_back(str);
    }

    cout << "The following input was stored with newline delimiter:" << endl;
    for (const auto& p : v1) {
        cout << p << endl;
    }

    cin.clear();

    vector<string> v2;
    // Now try it with a whitespace delimiter
    while (getline(cin, str, ' ')) {
        v2.push_back(str);
    }

    cout << "The following input was stored with whitespace as delimiter:" << endl;
    for (const auto& p : v2) {
        cout << p << endl;
    }
}
```

## <a name="stod"></a><a name="stod"></a>stod

Konvertiert eine Zeichensequenz **`double`** in eine .

```cpp
double stod(
    const string& str,
    size_t* idx = 0);

double stod(
    const wstring& str,
    size_t* idx = 0
;
```

### <a name="parameters"></a>Parameter

*Str*\
Die zu konvertierende Zeichenfolge.

*Idx*\
Der Indexwert des ersten Zeichens ohne Konvertierung.

### <a name="return-value"></a>Rückgabewert

Der **`double`** Wert.

### <a name="remarks"></a>Bemerkungen

Die Funktion konvertiert die Sequenz *str* von Elementen in **`double`** str in `strtod( str.c_str(), _Eptr)`einen Wert vom Typ, als ob durch Aufrufen , wobei `_Eptr` es sich um ein internes Objekt für die Funktion handelt. Wenn `str.c_str() == *_Eptr`, wird ein `invalid_argument`Objekt vom Typ ausgelöst. Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls, wenn *idx* kein Nullzeiger ist, speichert `*_Eptr -  str.c_str()` `*idx` die Funktion den Wert und gibt ihn zurück.

## <a name="stof"></a><a name="stof"></a>stof

Konvertiert eine Zeichenfolge in eine Float-Zahl.

```cpp
float stof(
    const string& str,
    size_t* idx = 0);

float stof(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>Parameter

*Str*\
Die zu konvertierende Zeichenfolge.

*Idx*\
Der Indexwert des ersten Zeichens ohne Konvertierung.

### <a name="return-value"></a>Rückgabewert

Der **`float`** Wert.

### <a name="remarks"></a>Bemerkungen

Die Funktion konvertiert die Sequenz *str* von Elementen in **`float`** str in `strtof( str.c_str(), _Eptr)`einen Wert vom Typ, als ob durch Aufrufen , wobei `_Eptr` es sich um ein internes Objekt für die Funktion handelt. Wenn `str.c_str() == *_Eptr`, wird ein `invalid_argument`Objekt vom Typ ausgelöst. Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls, wenn *idx* kein Nullzeiger ist, speichert `*_Eptr -  str.c_str()` `*idx` die Funktion den Wert und gibt ihn zurück.

## <a name="stoi"></a><a name="stoi"></a>Stoi

Konvertiert eine Zeichenfolge in eine Ganzzahl.

```cpp
int stoi(
    const string& str,
    size_t* idx = 0,
    int base = 10);

int stoi(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="return-value"></a>Rückgabewert

Der Ganzzahlwert.

### <a name="parameters"></a>Parameter

*Str*\
Die zu konvertierende Zeichenfolge.

*Idx*\
Der Indexwert des ersten Zeichens ohne Konvertierung.

*Basis*\
Die zu verwendende Zahlenbasis.

### <a name="remarks"></a>Bemerkungen

Die `stoi` Funktion konvertiert die Zeichenfolge in *str* in **`int`** einen Wert des Typs und gibt den Wert zurück. Wenn beispielsweise die Zeichenfolge "10" übergeben wurde, ist der durch `stoi` zurückgegebene Wert die Ganzzahl 10.

`stoi`verhält sich ähnlich `strtol` wie die Funktion für Einbytezeichen, `strtol( str.c_str(), _Eptr, idx)`wenn `_Eptr` sie in der Art und Weise aufgerufen wird, wobei es sich um ein Objekt handelt, das intern in der Funktion ist. oder `wcstol` für weite Zeichen, wenn es in `wcstol(Str.c_str(), _Eptr, idx)`ähnlicher Weise aufgerufen wird, . Weitere Informationen finden Sie unter [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md).

Wenn `str.c_str() == *_Eptr` `stoi` , ein Objekt `invalid_argument`vom Typ auslöst. Wenn ein solcher `errno`Aufruf festgelegt würde oder wenn der zurückgegebene Wert **`int`** nicht als Objekt `out_of_range`vom Typ dargestellt werden kann, wird ein Objekt vom Typ ausgelöst. Andernfalls wird die Funktion `*_Eptr - str.c_str()` in `*idx`gespeichert, wenn *idx* kein Nullzeiger ist.

## <a name="stol"></a><a name="stol"></a>Stol

Konvertiert eine Zeichensequenz **`long`** in eine .

```cpp
long stol(
    const string& str,
    size_t* idx = 0,
    int base = 10);

long stol(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>Parameter

*Str*\
Die zu konvertierende Zeichenfolge.

*Idx*\
Der Indexwert des ersten Zeichens ohne Konvertierung.

*Basis*\
Die zu verwendende Zahlenbasis.

### <a name="return-value"></a>Rückgabewert

Der lange ganzzahlige Wert.

### <a name="remarks"></a>Bemerkungen

Die Funktion konvertiert die Sequenz *str* von Elementen in **`long`** str in `strtol( str.c_str(), _Eptr, idx)`einen Wert vom Typ, als ob durch Aufrufen , wobei `_Eptr` es sich um ein internes Objekt für die Funktion handelt. Wenn `str.c_str() == *_Eptr`, wird ein `invalid_argument`Objekt vom Typ ausgelöst. Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls, wenn *idx* kein Nullzeiger ist, speichert `*_Eptr -  str.c_str()` `*idx` die Funktion den Wert und gibt ihn zurück.

## <a name="stold"></a><a name="stold"></a>stold

Konvertiert eine Zeichensequenz **`long double`** in eine .

```cpp
double stold(
    const string& str,
    size_t* idx = 0);

double stold(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>Parameter

*Str*\
Die zu konvertierende Zeichenfolge.

*Idx*\
Der Indexwert des ersten Zeichens ohne Konvertierung.

### <a name="return-value"></a>Rückgabewert

Der **`long double`** Wert.

### <a name="remarks"></a>Bemerkungen

Die Funktion konvertiert die Sequenz *str* von Elementen in **`long double`** str in `strtold( str.c_str(), _Eptr)`einen Wert vom Typ, als ob durch Aufrufen , wobei `_Eptr` es sich um ein internes Objekt für die Funktion handelt. Wenn `str.c_str() == *_Eptr`, wird ein `invalid_argument`Objekt vom Typ ausgelöst. Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls, wenn *idx* kein Nullzeiger ist, speichert `*_Eptr -  str.c_str()` `*idx` die Funktion den Wert und gibt ihn zurück.

## <a name="stoll"></a><a name="stoll"></a>Stoll

Konvertiert eine Zeichensequenz **`long long`** in eine .

```cpp
long long stoll(
    const string& str,
    size_t* idx = 0,
    int base = 10);

long long stoll(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>Parameter

*Str*\
Die zu konvertierende Zeichenfolge.

*Idx*\
Der Indexwert des ersten Zeichens ohne Konvertierung.

*Basis*\
Die zu verwendende Zahlenbasis.

### <a name="return-value"></a>Rückgabewert

Der **`long long`** Wert.

### <a name="remarks"></a>Bemerkungen

Die Funktion konvertiert die Sequenz *str* von Elementen in **`long long`** str in `strtoll( str.c_str(), _Eptr, idx)`einen Wert vom Typ, als ob durch Aufrufen , wobei `_Eptr` es sich um ein internes Objekt für die Funktion handelt. Wenn `str.c_str() == *_Eptr`, wird ein `invalid_argument`Objekt vom Typ ausgelöst. Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls, wenn *idx* kein Nullzeiger ist, speichert `*_Eptr -  str.c_str()` `*idx` die Funktion den Wert und gibt ihn zurück.

## <a name="stoul"></a><a name="stoul"></a>stoul

Konvertiert eine Zeichenfolge in einen langen Wert ohne Vorzeichen.

```cpp
unsigned long stoul(
    const string& str,
    size_t* idx = 0,
    int base = 10);

unsigned long stoul(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>Parameter

*Str*\
Die zu konvertierende Zeichenfolge.

*Idx*\
Der Indexwert des ersten Zeichens ohne Konvertierung.

*Basis*\
Die zu verwendende Zahlenbasis.

### <a name="return-value"></a>Rückgabewert

Der lange ganzzahlige Wert ohne Vorzeichen.

### <a name="remarks"></a>Bemerkungen

Die Funktion konvertiert die Sequenz *str* von Elementen in **`unsigned long`** str in `strtoul( str.c_str(), _Eptr, idx)`einen Wert vom Typ, als ob durch Aufrufen , wobei `_Eptr` es sich um ein internes Objekt für die Funktion handelt. Wenn `str.c_str() == *_Eptr`, wird ein `invalid_argument`Objekt vom Typ ausgelöst. Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls, wenn *idx* kein Nullzeiger ist, speichert `*_Eptr -  str.c_str()` `*idx` die Funktion den Wert und gibt ihn zurück.

## <a name="stoull"></a><a name="stoull"></a>stoull

Konvertiert eine Zeichensequenz **`unsigned long long`** in eine .

```cpp
unsigned long long stoull(
    const string& str,
    size_t* idx = 0,
    int base = 10);

unsigned long long stoull(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>Parameter

*Str*\
Die zu konvertierende Zeichenfolge.

*Idx*\
Der Indexwert des ersten Zeichens ohne Konvertierung.

*Basis*\
Die zu verwendende Zahlenbasis.

### <a name="return-value"></a>Rückgabewert

Der **`unsigned long long`** Wert.

### <a name="remarks"></a>Bemerkungen

Die Funktion konvertiert die Sequenz *str* von Elementen in **`unsigned long long`** str in `strtoull( str.c_str(), _Eptr, idx)`einen Wert vom Typ, als ob durch Aufrufen , wobei `_Eptr` es sich um ein internes Objekt für die Funktion handelt. Wenn `str.c_str() == *_Eptr`, wird ein `invalid_argument`Objekt vom Typ ausgelöst. Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls, wenn *idx* kein Nullzeiger ist, speichert `*_Eptr -  str.c_str()` `*idx` die Funktion den Wert und gibt ihn zurück.

## <a name="swap"></a><a name="swap"></a>Swap

Tauscht die Arrays von Zeichen für zwei Zeichenfolgen aus.

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Links*\
Eine Zeichenfolge, deren Elemente mit den Elementen einer anderen Zeichenfolge ausgetauscht werden sollen.

*Richting*\
Die andere Zeichenfolge, deren Elemente mit der ersten Zeichenfolge ausgetauscht werden sollen.

### <a name="remarks"></a>Bemerkungen

Die Vorlagenfunktion führt die spezialisierte Memberfunktion *left aus.* [Swap](../standard-library/basic-string-class.md#swap)(*rechts*) für Strings, was eine konstante Komplexität garantiert.

### <a name="example"></a>Beispiel

```cpp
// string_swap.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // Declaring an object of type basic_string<char>
   string s1 ( "Tweedledee" );
   string s2 ( "Tweedledum" );
   cout << "Before swapping string s1 and s2:" << endl;
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   swap ( s1 , s2 );
   cout << "\nAfter swapping string s1 and s2:" << endl;
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;
}
```

```Output
Before swapping string s1 and s2:
The basic_string s1 = Tweedledee.
The basic_string s2 = Tweedledum.

After swapping string s1 and s2:
The basic_string s1 = Tweedledum.
The basic_string s2 = Tweedledee.
```

## <a name="to_string"></a><a name="to_string"></a>to_string

Konvertiert einen Wert in einen `string`-Wert.

```cpp
string to_string(int value);
string to_string(unsigned int value);
string to_string(long value);
string to_string(unsigned long value);
string to_string(long long value);
string to_string(unsigned long long value);
string to_string(float value);
string to_string(double value);
string to_string(long double value);
```

### <a name="parameters"></a>Parameter

*Wert*\
Der zu konvertierende Wert.

### <a name="return-value"></a>Rückgabewert

Das `string`, das den Wert darstellt.

### <a name="remarks"></a>Bemerkungen

Die Funktion konvertiert *den Wert* in eine Sequenz `Buf` von Elementen, die `sprintf(Buf, Fmt, value)`in `Fmt` einem Arrayobjekt intern in die Funktion gespeichert sind, als ob durch Aufrufen

- `"%d"`Wenn *der Wert* vom Typ ist**`int`**

- `"%u"`Wenn *der Wert* vom Typ ist**`unsigned int`**

- `"%ld"`Wenn *der Wert* vom Typ ist**`long`**

- `"%lu"`Wenn *der Wert* vom Typ ist**`unsigned long`**

- `"%lld"`Wenn *der Wert* vom Typ ist**`long long`**

- `"%llu"`Wenn *der Wert* vom Typ ist**`unsigned long long`**

- `"%f"`wenn *der* Wert **`float`** vom Typ oder**`double`**

- `"%Lf"`Wenn *der Wert* vom Typ ist**`long double`**

Die Funktion gibt `string(Buf)` zurück.

## <a name="to_wstring"></a><a name="to_wstring"></a>to_wstring

Konvertiert einen Wert in eine breite Zeichenfolge.

```cpp
wstring to_wstring(int value);
wstring to_wstring(unsigned int value);
wstring to_wstring(long value);
wstring to_wstring(unsigned long value);
wstring to_wstring(long long value);
wstring to_wstring(unsigned long long value);
wstring to_wstring(float value);
wstring to_wstring(double value);
wstring to_wstring(long double value);
```

### <a name="parameters"></a>Parameter

*Wert*\
Der zu konvertierende Wert.

### <a name="return-value"></a>Rückgabewert

Die breite Zeichenfolge, die den Wert darstellt.

### <a name="remarks"></a>Bemerkungen

Die Funktion konvertiert *den Wert* in eine Sequenz `Buf` von Elementen, die `swprintf(Buf, Len, Fmt, value)`in `Fmt` einem Arrayobjekt intern in die Funktion gespeichert sind, als ob durch Aufrufen

- `L"%d"`Wenn *der Wert* vom Typ ist**`int`**

- `L"%u"`Wenn *der Wert* vom Typ ist**`unsigned int`**

- `L"%ld"`Wenn *der Wert* vom Typ ist**`long`**

- `L"%lu"`Wenn *der Wert* vom Typ ist**`unsigned long`**

- `L"%lld"`Wenn *der Wert* vom Typ ist**`long long`**

- `L"%llu"`Wenn *der Wert* vom Typ ist**`unsigned long long`**

- `L"%f"`wenn *der* Wert **`float`** vom Typ oder**`double`**

- `L"%Lf"`Wenn *der Wert* vom Typ ist**`long double`**

Die Funktion gibt `wstring(Buf)` zurück.

## <a name="see-also"></a>Siehe auch

[\<>](../standard-library/string.md)
