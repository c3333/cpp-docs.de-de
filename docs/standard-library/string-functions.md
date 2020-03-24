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
ms.openlocfilehash: 459e46f6aa144c591173a159c282658b120b1af3
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150602"
---
# <a name="ltstringgt-functions"></a>&lt;string&gt;-Funktionen

||||
|-|-|-|
|[getline](#getline)|[stod](#stod)|[stof](#stof)|
|[stoi](#stoi)|[stol](#stol)|[stold](#stold)|
|[stoll](#stoll)|[stoul](#stoul)|[stoull](#stoull)|
|[swap](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

## <a name="getline"></a><a name="getline"></a> getline

Extrahiert Zeichenfolgen zeilenweise aus dem Eingabestream.

```cpp
// (1) delimiter as parameter
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& is,
    basic_string<CharType, Traits, Allocator>& str,
    CharType delim);

template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>&& is,
    basic_string<CharType, Traits, Allocator>& str,
    const CharType delim);

// (2) default delimiter used
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& is,
    basic_string<CharType, Traits, Allocator>& str);

template <class Allocator, class Traits, class Allocator>
basic_istream<Allocator, Traits>& getline(
    basic_istream<Allocator, Traits>&& is,
    basic_string<Allocator, Traits, Allocator>& str);
```

### <a name="parameters"></a>Parameter

*ist gleich*\
Der Eingabestream, aus dem eine Zeichenfolge extrahiert werden soll.

*Str*\
Die Zeichenfolge, in die die Zeichen aus dem Eingabestream gelesen werden.

*Delta* -\
Das Zeilentrennzeichen.

### <a name="return-value"></a>Rückgabewert

Der Eingabestream *ist*.

### <a name="remarks"></a>Bemerkungen

Das Funktions Signatur Paar, das als `(1)` extrahiert werden soll, *ist* , bis *Delta* gefunden wird, das in *Str*gespeichert wird.

Das mit markierte Funktions Signatur Paar wird als Standardzeilen Trennzeichen als Zeilen Trenn`(2)` Zeichen verwendet und verhält sich wie **getline**(`is`, `str``is`. `widen`(' `\n`')).

Die zweite Funktion jedes Paars ist analog zur ersten, um [rvalue-Verweise](../cpp/lvalues-and-rvalues-visual-cpp.md) zu unterstützen.

Die Extraktion wird beendet, sobald eines der folgenden Ereignisse eintritt:

- Am Ende der Datei. in diesem *Fall wird das* interne Statusflag von auf `ios_base::eofbit`festgelegt.

- Nachdem die Funktion ein Element extrahiert hat, das `delim` entspricht; in diesem Fall wird das Element weder zurückgestellt noch an die kontrollierte Sequenz angefügt.

- Nachdem die Funktion `str.`[max_size](../standard-library/basic-string-class.md#max_size) Elemente extrahiert hat *, wird das* interne Statusflag von auf `ios_base::failbit`festgelegt.

- Ein anderer anderer Fehler als der zuvor aufgeführte. in diesem *Fall wird das* interne Statusflag von auf festgelegt `ios_base::badbit`

Informationen zu internen Statusflags finden Sie unter [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

Wenn die Funktion keine Elemente extrahiert *, wird das* interne Statusflag von auf `ios_base::failbit`festgelegt. In jedem Fall *wird*`getline` zurückgegeben.

Wenn eine Ausnahme ausgelöst *wird, bleiben* und *Str* in einem gültigen Zustand.

### <a name="example"></a>Beispiel

Der folgende Code zeigt `getline()` in zwei Modi: zuerst mit dem Standardtrennzeichen (newline) und dann mit einem Leerzeichen als Trennzeichen. Mit dem Dateiendezeichen (STRG-Z auf der Tastatur) wird die Beendigung der while-Schleifen gesteuert. Dadurch wird das interne Statusflag von `cin` auf `eofbit` festgelegt; dies muss mit [basic_ios::clear()](../standard-library/basic-ios-class.md#clear) gelöscht werden, damit die zweite while-Schleife ordnungsgemäß ausgeführt werden kann.

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

## <a name="stod"></a><a name="stod"></a> stod

Konvertiert eine Zeichen Sequenz in einen **Double**-Typ.

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

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*str*|Die zu konvertierende Zeichenfolge.|
|*idx*|Der Indexwert des ersten Zeichens ohne Konvertierung.|

### <a name="return-value"></a>Rückgabewert

Der **Double** -Wert.

### <a name="remarks"></a>Bemerkungen

Die-Funktion konvertiert die Sequenz von Elementen in *Str* in einen Wert `val` vom Typ **Double** , als ob durch Aufrufen von `strtod( str.c_str(), _Eptr)`, wobei `_Eptr` ein internes Objekt für die Funktion ist. Bei `str.c_str() == *_Eptr` wird ein Objekt vom Typ `invalid_argument` ausgegeben. Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls speichert die Funktion `*_Eptr -  str.c_str()` in `*idx` und gibt `val`zurück, wenn *IDX* kein NULL-Zeiger ist.

## <a name="stof"></a><a name="stof"></a> stof

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

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*str*|Die zu konvertierende Zeichenfolge.|
|*idx*|Der Indexwert des ersten Zeichens ohne Konvertierung.|

### <a name="return-value"></a>Rückgabewert

Der Float-Wert.

### <a name="remarks"></a>Bemerkungen

Die-Funktion konvertiert die Sequenz von Elementen in *Str* in einen Wert `val` vom Typ **float** , als ob durch Aufrufen von `strtof( str.c_str(), _Eptr)`, wobei `_Eptr` ein internes Objekt für die Funktion ist. Bei `str.c_str() == *_Eptr` wird ein Objekt vom Typ `invalid_argument` ausgegeben. Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls speichert die Funktion `*_Eptr -  str.c_str()` in `*idx` und gibt `val`zurück, wenn *IDX* kein NULL-Zeiger ist.

## <a name="stoi"></a><a name="stoi"></a> stoi

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

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*str*|Die zu konvertierende Zeichenfolge.|
|*idx*|Enthält den Index des ersten Zeichens ohne Konvertierung bei der Rückgabe.|
|*base*|Die zu verwendende Zahlenbasis.|

### <a name="remarks"></a>Bemerkungen

Die-Funktion `stoi` konvertiert die Zeichenfolge in *Str* in einen Wert vom Typ **int** und gibt den Wert zurück. Wenn beispielsweise die Zeichenfolge "10" übergeben wurde, ist der durch `stoi` zurückgegebene Wert die Ganzzahl 10.

`stoi` ähnelt der Funktion `strtol` bei Einzelbyte-Zeichen, wenn der Aufruf über `strtol( str.c_str(), _Eptr, idx)` erfolgt, wobei `_Eptr` ein internes Objekt der Funktion ist, oder `wcstol` bei Breitzeichen, wenn der Aufruf ähnlich über `wcstol(Str.c_str(), _Eptr, idx)` erfolgt. Weitere Informationen finden Sie unter [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md).

Wenn `str.c_str() == *_Eptr`, löst `stoi` ein Objekt vom Typ `invalid_argument`aus. Wenn ein solcher-Befehl `errno`festgelegt oder der zurückgegebene Wert nicht als ein Objekt vom Typ " **int**" dargestellt werden kann, wird ein Objekt vom Typ "`out_of_range`" ausgelöst. Andernfalls speichert die Funktion `*_Eptr - str.c_str()` in `*idx`, wenn *IDX* kein NULL-Zeiger ist.

## <a name="stol"></a><a name="stol"></a> stol

Konvertiert eine Zeichen Sequenz in eine **lange**.

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

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*str*|Die zu konvertierende Zeichenfolge.|
|*idx*|Der Indexwert des ersten Zeichens ohne Konvertierung.|
|*base*|Die zu verwendende Zahlenbasis.|

### <a name="return-value"></a>Rückgabewert

Der lange ganzzahlige Wert.

### <a name="remarks"></a>Bemerkungen

Die-Funktion konvertiert die Sequenz von Elementen in *Str* in einen Wert `val` vom Typ **Long** , als ob durch Aufrufen von `strtol( str.c_str(), _Eptr, idx)`, wobei `_Eptr` ein internes Objekt für die Funktion ist. Bei `str.c_str() == *_Eptr` wird ein Objekt vom Typ `invalid_argument` ausgegeben. Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls speichert die Funktion `*_Eptr -  str.c_str()` in `*idx` und gibt `val`zurück, wenn *IDX* kein NULL-Zeiger ist.

## <a name="stold"></a><a name="stold"></a> stold

Konvertiert eine Zeichen Sequenz in einen **long Double**-Typ.

```cpp
double stold(
    const string& str,
    size_t* idx = 0);

double stold(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*str*|Die zu konvertierende Zeichenfolge.|
|*idx*|Der Indexwert des ersten Zeichens ohne Konvertierung.|

### <a name="return-value"></a>Rückgabewert

Der **long Double** -Wert.

### <a name="remarks"></a>Bemerkungen

Die-Funktion konvertiert die Sequenz von Elementen in *Str* in einen Wert `val` vom Typ **long Double** , als ob durch Aufrufen von `strtold( str.c_str(), _Eptr)`, wobei `_Eptr` ein internes Objekt für die Funktion ist. Bei `str.c_str() == *_Eptr` wird ein Objekt vom Typ `invalid_argument` ausgegeben. Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls speichert die Funktion `*_Eptr -  str.c_str()` in `*idx` und gibt `val`zurück, wenn *IDX* kein NULL-Zeiger ist.

## <a name="stoll"></a><a name="stoll"></a> stoll

Konvertiert eine Zeichenfolge in eine **lange Länge**.

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

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*str*|Die zu konvertierende Zeichenfolge.|
|*idx*|Der Indexwert des ersten Zeichens ohne Konvertierung.|
|*base*|Die zu verwendende Zahlenbasis.|

### <a name="return-value"></a>Rückgabewert

Der **Long Long** -Wert.

### <a name="remarks"></a>Bemerkungen

Die-Funktion konvertiert die Sequenz von Elementen in *Str* in einen Wert `val` vom Typ **Long Long** , als ob durch Aufrufen von `strtoll( str.c_str(), _Eptr, idx)`, wobei `_Eptr` ein internes Objekt für die Funktion ist. Bei `str.c_str() == *_Eptr` wird ein Objekt vom Typ `invalid_argument` ausgegeben. Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls speichert die Funktion `*_Eptr -  str.c_str()` in `*idx` und gibt `val`zurück, wenn *IDX* kein NULL-Zeiger ist.

## <a name="stoul"></a><a name="stoul"></a> stoul

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

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*str*|Die zu konvertierende Zeichenfolge.|
|*idx*|Der Indexwert des ersten Zeichens ohne Konvertierung.|
|*base*|Die zu verwendende Zahlenbasis.|

### <a name="return-value"></a>Rückgabewert

Der lange ganzzahlige Wert ohne Vorzeichen.

### <a name="remarks"></a>Bemerkungen

Die-Funktion konvertiert die Sequenz von Elementen in *Str* in einen Wert `val` vom Typ **Ganzzahl ohne Vorzeichen long** As If by Call `strtoul( str.c_str(), _Eptr, idx)`, wobei `_Eptr` ein internes Objekt für die Funktion ist. Bei `str.c_str() == *_Eptr` wird ein Objekt vom Typ `invalid_argument` ausgegeben. Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls speichert die Funktion `*_Eptr -  str.c_str()` in `*idx` und gibt `val`zurück, wenn *IDX* kein NULL-Zeiger ist.

## <a name="stoull"></a><a name="stoull"></a> stoull

Konvertiert eine Zeichen Sequenz in eine **unsignierte lange Länge**.

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

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*str*|Die zu konvertierende Zeichenfolge.|
|*idx*|Der Indexwert des ersten Zeichens ohne Konvertierung.|
|*base*|Die zu verwendende Zahlenbasis.|

### <a name="return-value"></a>Rückgabewert

Der **lange lange Wert ohne** Vorzeichen.

### <a name="remarks"></a>Bemerkungen

Die-Funktion konvertiert die Sequenz von Elementen in *Str* in einen Wert `val` vom Typ **Ganzzahl ohne Vorzeichen long long** As If by Call `strtoull( str.c_str(), _Eptr, idx)`, wobei `_Eptr` ein internes Objekt für die Funktion ist. Bei `str.c_str() == *_Eptr` wird ein Objekt vom Typ `invalid_argument` ausgegeben. Wenn solch ein Aufruf `errno` festlegt, wird ein Objekt vom Typ `out_of_range` ausgegeben. Andernfalls speichert die Funktion `*_Eptr -  str.c_str()` in `*idx` und gibt `val`zurück, wenn *IDX* kein NULL-Zeiger ist.

## <a name="swap"></a><a name="swap"></a> swap

Tauscht die Arrays von Zeichen für zwei Zeichenfolgen aus.

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Eine Zeichenfolge, deren Elemente mit denen einer anderen Zeichenfolge ausgetauscht werden sollen.

*Rechte*\
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
string to_string(int Val);
string to_string(unsigned int Val);
string to_string(long Val);
string to_string(unsigned long Val);
string to_string(long long Val);
string to_string(unsigned long long Val);
string to_string(float Val);
string to_string(double Val);
string to_string(long double Val);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Ster*|Der zu konvertierende Wert.|

### <a name="return-value"></a>Rückgabewert

Das `string`, das den Wert darstellt.

### <a name="remarks"></a>Bemerkungen

Die-Funktion konvertiert *Val* in eine Sequenz von Elementen, die in einem Array Objekt gespeichert sind, `Buf` intern für die Funktion, als ob durch Aufrufen von `sprintf(Buf, Fmt, Val)`, wobei `Fmt`

- `"%d"`, wenn `Val` den Typ " **int** " aufweist

- `"%u"`, wenn `Val` den Typ " **Ganzzahl ohne Vorzeichen int** " aufweist

- `"%ld"`, wenn `Val` den Typ **Long** aufweist.

- `"%lu"`, wenn `Val` den Typ **Ganzzahl ohne Vorzeichen long** aufweist

- `"%lld"`, wenn `Val` den Typ " **Long Long** " aufweist.

- `"%llu"`, wenn `Val` den Typ " **Long Long" nicht signiert** hat.

- `"%f"`, wenn `Val` vom Typ **float** oder **Double** ist.

- `"%Lf"`, wenn `Val` den Typ **long Double** hat.

Die Funktion gibt `string(Buf)`zurück.

## <a name="to_wstring"></a><a name="to_wstring"></a> to_wstring

Konvertiert einen Wert in eine breite Zeichenfolge.

```cpp
wstring to_wstring(int Val);
wstring to_wstring(unsigned int Val);
wstring to_wstring(long Val);
wstring to_wstring(unsigned long Val);
wstring to_wstring(long long Val);
wstring to_wstring(unsigned long long Val);
wstring to_wstring(float Val);
wstring to_wstring(double Val);
wstring to_wstring(long double Val);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|`Val`|Der zu konvertierende Wert.|

### <a name="return-value"></a>Rückgabewert

Die breite Zeichenfolge, die den Wert darstellt.

### <a name="remarks"></a>Bemerkungen

Mit der Funktion wird `Val` in eine Sequenz von Elementen konvertiert, die in einem für die Funktion internen `Buf`-Arrayobjekt gespeichert werden, als würde `swprintf(Buf, Len, Fmt, Val)` aufgerufen, wobei `Fmt` Folgendem entspricht:

- `L"%d"`, wenn `Val` den Typ " **int** " aufweist

- `L"%u"`, wenn `Val` den Typ " **Ganzzahl ohne Vorzeichen int** " aufweist

- `L"%ld"`, wenn `Val` den Typ **Long** aufweist.

- `L"%lu"`, wenn `Val` den Typ **Ganzzahl ohne Vorzeichen long** aufweist

- `L"%lld"`, wenn `Val` den Typ " **Long Long** " aufweist.

- `L"%llu"`, wenn `Val` den Typ " **Long Long" nicht signiert** hat.

- `L"%f"`, wenn `Val` vom Typ **float** oder **Double** ist.

- `L"%Lf"`, wenn `Val` den Typ **long Double** hat.

Die Funktion gibt `wstring(Buf)`zurück.

## <a name="see-also"></a>Weitere Informationen

[\<string>](../standard-library/string.md)
