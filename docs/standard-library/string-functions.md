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
ms.openlocfilehash: 350a66481c7061322f08a768ec1628598f4af68e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843182"
---
# <a name="ltstringgt-functions"></a>&lt;string&gt;-Funktionen

[getline](#getline)\
[Stod](#stod)\
[Stof](#stof)\
[Stoi](#stoi)\
[OLS](#stol)\
[stold](#stold)\
[Stoll](#stoll)\
[Stoul](#stoul)\
[stoull](#stoull)\
[Wechsel](#swap)\
[to_string](#to_string)\
[to_wstring](#to_wstring)

## <a name="getline"></a><a name="getline"></a> getline

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

*SRT*\
Die Zeichenfolge, in die die Zeichen aus dem Eingabestream gelesen werden.

*Trennzeichen*\
Das Zeilentrennzeichen.

### <a name="return-value"></a>Rückgabewert

Der Eingabestream *in_stream*.

### <a name="remarks"></a>Bemerkungen

Das mit markierte Funktions Signatur Paar `(1)` extrahiert Zeichen aus *in_stream* , bis das *Trenn* Zeichen gefunden wurde, und speichert Sie in *Str*.

Das mit markierte Funktions Signatur Paar `(2)` verwendet "Zeilenumbruch" als Standardzeilen Trennzeichen und verhält sich als `getline(in_stream, str, in_stream. widen('\n'))` .

Die zweite Funktion jedes Paars ist analog zur ersten, um [rvalue-Verweise](../cpp/lvalues-and-rvalues-visual-cpp.md) zu unterstützen.

Die Extraktion wird beendet, sobald eines der folgenden Ereignisse eintritt:

- Am Ende der Datei. in diesem Fall wird das interne Statusflag von *in_stream* auf festgelegt `ios_base::eofbit` .

- Nachdem die Funktion ein Element extrahiert hat, das mit dem *Trenn*Zeichen identisch ist. Das Element wird nicht zurückgestellt oder an die gesteuerte Sequenz angefügt.

- Nachdem die Funktion `str.` [max_size](../standard-library/basic-string-class.md#max_size) Elemente extrahiert hat. Das interne Statusflag von *in_stream* ist auf festgelegt `ios_base::failbit` .

- Ein anderer anderer Fehler als der zuvor aufgeführte. das interne Statusflag von *in_stream* ist auf festgelegt `ios_base::badbit` .

Informationen zu internen Statusflags finden Sie unter [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

Wenn die Funktion keine Elemente extrahiert, wird das interne Statusflag von *in_stream* auf festgelegt `ios_base::failbit` . In jedem Fall `getline` gibt *in_stream*zurück.

Wenn eine Ausnahme ausgelöst wird, bleiben *in_stream* und *Str* in einem gültigen Zustand.

### <a name="example"></a>Beispiel

Der folgende Code zeigt `getline()` in zwei Modi: zuerst mit dem Standardtrennzeichen (newline) und dann mit einem Leerzeichen als Trennzeichen. Mit dem Dateiendezeichen (STRG-Z auf der Tastatur) wird die Beendigung der while-Schleifen gesteuert. Mit diesem Wert wird das interne Statusflag von auf festgelegt `cin` `eofbit` , das mit [basic_ios:: Clear ()](../standard-library/basic-ios-class.md#clear) gelöscht werden muss, bevor die zweite while-Schleife ordnungsgemäß funktioniert.

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

## <a name="stod"></a><a name="stod"></a> Stod

Konvertiert eine Zeichenfolge in eine **`double`** .

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

*SRT*\
Die zu konvertierende Zeichenfolge.

*idx*\
Der Indexwert des ersten Zeichens ohne Konvertierung.

### <a name="return-value"></a>Rückgabewert

Der- **`double`** Wert.

### <a name="remarks"></a>Bemerkungen

Die-Funktion konvertiert die Sequenz von Elementen in *Str* in einen Wert vom Typ **`double`** , so als ob durch Aufrufen von `strtod( str.c_str(), _Eptr)` , wobei `_Eptr` ein internes Objekt für die Funktion ist. Wenn `str.c_str() == *_Eptr` , wird ein Objekt vom Typ ausgelöst `invalid_argument` . Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls speichert die *idx* Funktion `*_Eptr -  str.c_str()` in `*idx` und gibt den Wert zurück, wenn IDX kein NULL-Zeiger ist.

## <a name="stof"></a><a name="stof"></a> Stof

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

*SRT*\
Die zu konvertierende Zeichenfolge.

*idx*\
Der Indexwert des ersten Zeichens ohne Konvertierung.

### <a name="return-value"></a>Rückgabewert

Der- **`float`** Wert.

### <a name="remarks"></a>Bemerkungen

Die-Funktion konvertiert die Sequenz von Elementen in *Str* in einen Wert vom Typ **`float`** , so als ob durch Aufrufen von `strtof( str.c_str(), _Eptr)` , wobei `_Eptr` ein internes Objekt für die Funktion ist. Wenn `str.c_str() == *_Eptr` , wird ein Objekt vom Typ ausgelöst `invalid_argument` . Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls speichert die *idx* Funktion `*_Eptr -  str.c_str()` in `*idx` und gibt den Wert zurück, wenn IDX kein NULL-Zeiger ist.

## <a name="stoi"></a><a name="stoi"></a> Stoi

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

*SRT*\
Die zu konvertierende Zeichenfolge.

*idx*\
Der Indexwert des ersten Zeichens ohne Konvertierung.

*sock*\
Die zu verwendende Zahlenbasis.

### <a name="remarks"></a>Bemerkungen

Die `stoi` -Funktion konvertiert die Zeichenfolge in *Str* in einen Wert des Typs **`int`** und gibt den Wert zurück. Wenn beispielsweise die Zeichenfolge "10" übergeben wurde, ist der durch `stoi` zurückgegebene Wert die Ganzzahl 10.

`stoi` verhält sich ähnlich wie die-Funktion `strtol` für Einzel Byte Zeichen, wenn Sie in der Weise aufgerufen `strtol( str.c_str(), _Eptr, idx)` wird, wobei `_Eptr` ein internes Objekt der Funktion ist, oder bei `wcstol` breit Zeichen, wenn Sie auf ähnliche Weise aufgerufen wird `wcstol(Str.c_str(), _Eptr, idx)` . Weitere Informationen finden Sie unter [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md).

Wenn `str.c_str() == *_Eptr` , wird `stoi` ein Objekt vom Typ ausgelöst `invalid_argument` . Wenn ein solcher-Befehl festgelegt `errno` wird oder der zurückgegebene Wert nicht als ein Objekt vom Typ dargestellt werden kann **`int`** , wird ein Objekt vom Typ ausgelöst `out_of_range` . Andernfalls speichert die Funktion in, wenn *IDX* kein NULL-Zeiger `*_Eptr - str.c_str()` ist `*idx` .

## <a name="stol"></a><a name="stol"></a> OLS

Konvertiert eine Zeichenfolge in eine **`long`** .

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

*SRT*\
Die zu konvertierende Zeichenfolge.

*idx*\
Der Indexwert des ersten Zeichens ohne Konvertierung.

*sock*\
Die zu verwendende Zahlenbasis.

### <a name="return-value"></a>Rückgabewert

Der lange ganzzahlige Wert.

### <a name="remarks"></a>Bemerkungen

Die-Funktion konvertiert die Sequenz von Elementen in *Str* in einen Wert vom Typ **`long`** , so als ob durch Aufrufen von `strtol( str.c_str(), _Eptr, idx)` , wobei `_Eptr` ein internes Objekt für die Funktion ist. Wenn `str.c_str() == *_Eptr` , wird ein Objekt vom Typ ausgelöst `invalid_argument` . Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls speichert die *idx* Funktion `*_Eptr -  str.c_str()` in `*idx` und gibt den Wert zurück, wenn IDX kein NULL-Zeiger ist.

## <a name="stold"></a><a name="stold"></a> stold

Konvertiert eine Zeichenfolge in eine **`long double`** .

```cpp
double stold(
    const string& str,
    size_t* idx = 0);

double stold(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>Parameter

*SRT*\
Die zu konvertierende Zeichenfolge.

*idx*\
Der Indexwert des ersten Zeichens ohne Konvertierung.

### <a name="return-value"></a>Rückgabewert

Der- **`long double`** Wert.

### <a name="remarks"></a>Bemerkungen

Die-Funktion konvertiert die Sequenz von Elementen in *Str* in einen Wert vom Typ **`long double`** , so als ob durch Aufrufen von `strtold( str.c_str(), _Eptr)` , wobei `_Eptr` ein internes Objekt für die Funktion ist. Wenn `str.c_str() == *_Eptr` , wird ein Objekt vom Typ ausgelöst `invalid_argument` . Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls speichert die *idx* Funktion `*_Eptr -  str.c_str()` in `*idx` und gibt den Wert zurück, wenn IDX kein NULL-Zeiger ist.

## <a name="stoll"></a><a name="stoll"></a> Stoll

Konvertiert eine Zeichenfolge in eine **`long long`** .

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

*SRT*\
Die zu konvertierende Zeichenfolge.

*idx*\
Der Indexwert des ersten Zeichens ohne Konvertierung.

*sock*\
Die zu verwendende Zahlenbasis.

### <a name="return-value"></a>Rückgabewert

Der- **`long long`** Wert.

### <a name="remarks"></a>Bemerkungen

Die-Funktion konvertiert die Sequenz von Elementen in *Str* in einen Wert vom Typ **`long long`** , so als ob durch Aufrufen von `strtoll( str.c_str(), _Eptr, idx)` , wobei `_Eptr` ein internes Objekt für die Funktion ist. Wenn `str.c_str() == *_Eptr` , wird ein Objekt vom Typ ausgelöst `invalid_argument` . Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls speichert die *idx* Funktion `*_Eptr -  str.c_str()` in `*idx` und gibt den Wert zurück, wenn IDX kein NULL-Zeiger ist.

## <a name="stoul"></a><a name="stoul"></a> Stoul

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

*SRT*\
Die zu konvertierende Zeichenfolge.

*idx*\
Der Indexwert des ersten Zeichens ohne Konvertierung.

*sock*\
Die zu verwendende Zahlenbasis.

### <a name="return-value"></a>Rückgabewert

Der lange ganzzahlige Wert ohne Vorzeichen.

### <a name="remarks"></a>Bemerkungen

Die-Funktion konvertiert die Sequenz von Elementen in *Str* in einen Wert vom Typ **`unsigned long`** , so als ob durch Aufrufen von `strtoul( str.c_str(), _Eptr, idx)` , wobei `_Eptr` ein internes Objekt für die Funktion ist. Wenn `str.c_str() == *_Eptr` , wird ein Objekt vom Typ ausgelöst `invalid_argument` . Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls speichert die *idx* Funktion `*_Eptr -  str.c_str()` in `*idx` und gibt den Wert zurück, wenn IDX kein NULL-Zeiger ist.

## <a name="stoull"></a><a name="stoull"></a> stoull

Konvertiert eine Zeichenfolge in eine **`unsigned long long`** .

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

*SRT*\
Die zu konvertierende Zeichenfolge.

*idx*\
Der Indexwert des ersten Zeichens ohne Konvertierung.

*sock*\
Die zu verwendende Zahlenbasis.

### <a name="return-value"></a>Rückgabewert

Der- **`unsigned long long`** Wert.

### <a name="remarks"></a>Bemerkungen

Die-Funktion konvertiert die Sequenz von Elementen in *Str* in einen Wert vom Typ **`unsigned long long`** , so als ob durch Aufrufen von `strtoull( str.c_str(), _Eptr, idx)` , wobei `_Eptr` ein internes Objekt für die Funktion ist. Wenn `str.c_str() == *_Eptr` , wird ein Objekt vom Typ ausgelöst `invalid_argument` . Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls speichert die *idx* Funktion `*_Eptr -  str.c_str()` in `*idx` und gibt den Wert zurück, wenn IDX kein NULL-Zeiger ist.

## <a name="swap"></a><a name="swap"></a> Wechsel

Tauscht die Arrays von Zeichen für zwei Zeichenfolgen aus.

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Eine Zeichenfolge, deren Elemente mit den Elementen einer anderen Zeichenfolge ausgetauscht werden sollen.

*Richting*\
Die andere Zeichenfolge, deren Elemente mit der ersten Zeichenfolge ausgetauscht werden sollen.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion führt die spezialisierte Member-Funktion auf der *linken Seite*aus. [Swap](../standard-library/basic-string-class.md#swap)(*right*) für Zeichen folgen, die eine Konstante Komplexität gewährleisten.

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

## <a name="to_string"></a><a name="to_string"></a> to_string

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

Die-Funktion konvertiert *value* in eine Sequenz von Elementen, die in einem internen Array Objekt in `Buf` der Funktion gespeichert `sprintf(Buf, Fmt, value)` ist, als wäre durch den Aufruf von. `Fmt`

- `"%d"` Wenn *value* vom Typ ist **`int`**

- `"%u"` Wenn *value* vom Typ ist **`unsigned int`**

- `"%ld"` Wenn *value* vom Typ ist **`long`**

- `"%lu"` Wenn *value* vom Typ ist **`unsigned long`**

- `"%lld"` Wenn *value* vom Typ ist **`long long`**

- `"%llu"` Wenn *value* vom Typ ist **`unsigned long long`**

- `"%f"` Wenn *value* vom Typ **`float`** oder ist **`double`**

- `"%Lf"` Wenn *value* vom Typ ist **`long double`**

Die Funktion gibt `string(Buf)` zurück.

## <a name="to_wstring"></a><a name="to_wstring"></a> to_wstring

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

Die-Funktion konvertiert *value* in eine Sequenz von Elementen, die in einem internen Array Objekt in `Buf` der Funktion gespeichert `swprintf(Buf, Len, Fmt, value)` ist, als wäre durch den Aufruf von. `Fmt`

- `L"%d"` Wenn *value* vom Typ ist **`int`**

- `L"%u"` Wenn *value* vom Typ ist **`unsigned int`**

- `L"%ld"` Wenn *value* vom Typ ist **`long`**

- `L"%lu"` Wenn *value* vom Typ ist **`unsigned long`**

- `L"%lld"` Wenn *value* vom Typ ist **`long long`**

- `L"%llu"` Wenn *value* vom Typ ist **`unsigned long long`**

- `L"%f"` Wenn *value* vom Typ **`float`** oder ist **`double`**

- `L"%Lf"` Wenn *value* vom Typ ist **`long double`**

Die Funktion gibt `wstring(Buf)` zurück.

## <a name="see-also"></a>Weitere Informationen

[\<string>](../standard-library/string.md)
