---
title: Benutzerdefinierte Literale (C++)
description: Beschreibt den Zweck und die Verwendung von benutzerdefinierten Literalen in Standard C++.
ms.date: 02/10/2020
ms.assetid: ff4a5bec-f795-4705-a2c0-53788fd57609
ms.openlocfilehash: a6636be414fa4dc199ce10fca1b33f092492575f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/11/2020
ms.locfileid: "79090560"
---
# <a name="user-defined-literals"></a>Benutzerdefinierte Literale

Es gibt sechs Hauptkategorien von Literalen in C++: Ganzzahl, Zeichen, Gleit Komma, Zeichenfolge, boolescher Wert und Zeiger. Ab C++ 11 können Sie Ihre eigenen Literale basierend auf diesen Kategorien definieren, um syntaktische Verknüpfungen für allgemeine Idiome bereitzustellen und die Typsicherheit zu erhöhen. Angenommen, Sie verfügen über eine `Distance`-Klasse. Sie können einen Literalwert für Kilometer und einen anderen für Meilen definieren und den Benutzer auffordern, sich explizit über die Maßeinheiten zu freuen, indem Sie Folgendes schreiben: `auto d = 42.0_km` oder `auto d = 42.0_mi`. Es gibt keinen Leistungsvorteil und keinen Nachteil für benutzerdefinierte Literale. Sie sind in erster Linie für die einfache oder für die Typableitung der Kompilierzeit vorgesehen. Die Standard Bibliothek verfügt über benutzerdefinierte Literale für `std::string`, für `std::complex`und für Einheiten in Zeit-und Dauer Vorgängen im \<Chrono-> Header:

```cpp
Distance d = 36.0_mi + 42.0_km;         // Custom UDL (see below)
std::string str = "hello"s + "World"s;  // Standard Library <string> UDL
complex<double> num =
   (2.0 + 3.01i) * (5.0 + 4.3i);        // Standard Library <complex> UDL
auto duration = 15ms + 42h;             // Standard Library <chrono> UDLs
```

## <a name="user-defined-literal-operator-signatures"></a>Benutzerdefinierte Literaloperatorsignaturen

Sie implementieren ein benutzerdefiniertes Literale, indem Sie einen **Operator ""** im Namespace Bereich mit einer der folgenden Formen definieren:

```cpp
ReturnType operator "" _a(unsigned long long int);   // Literal operator for user-defined INTEGRAL literal
ReturnType operator "" _b(long double);              // Literal operator for user-defined FLOATING literal
ReturnType operator "" _c(char);                     // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _d(wchar_t);                  // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _e(char16_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _f(char32_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _g(const char*, size_t);      // Literal operator for user-defined STRING literal
ReturnType operator "" _h(const wchar_t*, size_t);   // Literal operator for user-defined STRING literal
ReturnType operator "" _i(const char16_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _g(const char32_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

Die Operatornamen im vorherigen Beispiel sind Platzhalter für die von Ihnen bereitgestellten Namen. Der führende Unterstrich ist jedoch erforderlich. (Nur die Standard Bibliothek darf Literale ohne Unterstrich definieren.) Der Rückgabetyp ist der Speicherort, an dem die Konvertierung oder andere Vorgänge angepasst werden, die vom Literal Alle diese Operatoren können auch `constexpr` definiert werden.

## <a name="cooked-literals"></a>Verarbeitete Literale

Im Quellcode ist jede Literale, unabhängig davon, ob Benutzer definiert oder nicht, eine Folge von alphanumerischen Zeichen, wie z. b. `101`oder `54.7`, oder `"hello"` oder `true`. Der Compiler interpretiert die Sequenz als Integer-, float-, Konstante char-\* Zeichenfolge usw. Ein benutzerdefiniertes Literale, das den Typ akzeptiert, den der Compiler dem literalen Wert zugewiesen hat, wird informell als *gekochtes Literalwert*bezeichnet. Alle ober aufgeführten Operatoren außer `_r` und `_t` sind verarbeitete Literale. Beispielsweise würde ein Literal `42.0_km` an einen Operator mit dem Namen _km gebunden, der eine Signatur ähnlich _b hat, und das Literal `42_km` an einen Operator mit einer Signatur ähnlich _a gebunden.

Das folgende Beispiel zeigt, wie benutzerdefinierte Literale Aufrufer zu einer expliziten Eingabe auffordern können. Zum Erstellen der `Distance` muss der Benutzer explizit Kilometer oder Meilen mit den entsprechenden benutzerdefinierten Literalzeichen angeben. Sie können dasselbe Ergebnis auf andere Weise erreichen, aber benutzerdefinierte Literale sind weniger ausführlich als die Alternativen.

```cpp
// UDL_Distance.cpp

#include <iostream>
#include <string>

struct Distance
{
private:
    explicit Distance(long double val) : kilometers(val)
    {}

    friend Distance operator"" _km(long double val);
    friend Distance operator"" _mi(long double val);

    long double kilometers{ 0 };
public:
    const static long double km_per_mile;
    long double get_kilometers() { return kilometers; }

    Distance operator+(Distance other)
    {
        return Distance(get_kilometers() + other.get_kilometers());
    }
};

const long double Distance::km_per_mile = 1.609344L;

Distance operator"" _km(long double val)
{
    return Distance(val);
}

Distance operator"" _mi(long double val)
{
    return Distance(val * Distance::km_per_mile);
}

int main()
{
    // Must have a decimal point to bind to the operator we defined!
    Distance d{ 402.0_km }; // construct using kilometers
    std::cout << "Kilometers in d: " << d.get_kilometers() << std::endl; // 402

    Distance d2{ 402.0_mi }; // construct using miles
    std::cout << "Kilometers in d2: " << d2.get_kilometers() << std::endl;  //646.956

    // add distances constructed with different units
    Distance d3 = 36.0_mi + 42.0_km;
    std::cout << "d3 value = " << d3.get_kilometers() << std::endl; // 99.9364

    // Distance d4(90.0); // error constructor not accessible

    std::string s;
    std::getline(std::cin, s);
    return 0;
}
```

Die Literalzahl muss ein Dezimaltrennzeichen verwenden. Andernfalls würde die Zahl als ganze Zahl interpretiert werden, und der Typ wäre nicht mit dem Operator kompatibel. Für Gleit Komma Eingaben muss der Typ **long Double**und für ganzzahlige **Typen lang sein.**

## <a name="raw-literals"></a>Unformatierte Literale

In einem unformatierten benutzerdefinierten Literalformat akzeptiert der Operator, den Sie definieren, das Literale als Sequenz von Char-Werten. Es liegt an Ihnen, diese Sequenz als Zahl, Zeichenfolge oder einen anderen Typ zu interpretieren. Aus der zuvor auf dieser Seite aufgeführten Liste von Operatoren können `_r` und `_t` zum Definieren von unformatierten Literalen verwendet werden:

```cpp
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

Sie können unformatierte Literale verwenden, um eine benutzerdefinierte Interpretation einer Eingabe Sequenz bereitzustellen, die sich vom normalen Verhalten des Compilers unterscheidet. Sie könnten beispielsweise ein Literal definieren, das die Sequenz `4.75987` in einen benutzerdefinierten Dezimaltyp anstatt in einen IEEE 754-Gleitkommatyp konvertiert. Unformatierte Literale, wie z. b. gekochte Literale, können auch zur Kompilierzeit Validierung von Eingabe Sequenzen verwendet werden.

### <a name="example-limitations-of-raw-literals"></a>Beispiel: Einschränkungen von unformatierten literalen

Der unformatierte Literaloperator und die Vorlage für den Literaloperator funktionieren nur für Ganzzahl- und Gleitkommatypen benutzerdefinierter Literale, wie im folgenden Beispiel gezeigt:

```cpp
#include <cstddef>
#include <cstdio>

// Literal operator for user-defined INTEGRAL literal
void operator "" _dump(unsigned long long int lit)
{
    printf("operator \"\" _dump(unsigned long long int) : ===>%llu<===\n", lit);
};

// Literal operator for user-defined FLOATING literal
void operator "" _dump(long double lit)
{
    printf("operator \"\" _dump(long double)            : ===>%Lf<===\n",  lit);
};

// Literal operator for user-defined CHARACTER literal
void operator "" _dump(char lit)
{
    printf("operator \"\" _dump(char)                   : ===>%c<===\n",   lit);
};

void operator "" _dump(wchar_t lit)
{
    printf("operator \"\" _dump(wchar_t)                : ===>%d<===\n",   lit);
};

void operator "" _dump(char16_t lit)
{
    printf("operator \"\" _dump(char16_t)               : ===>%d<===\n",   lit);
};

void operator "" _dump(char32_t lit)
{
    printf("operator \"\" _dump(char32_t)               : ===>%d<===\n",   lit);
};

// Literal operator for user-defined STRING literal
void operator "" _dump(const     char* lit, size_t)
{
    printf("operator \"\" _dump(const     char*, size_t): ===>%s<===\n",   lit);
};

void operator "" _dump(const  wchar_t* lit, size_t)
{
    printf("operator \"\" _dump(const  wchar_t*, size_t): ===>%ls<===\n",  lit);
};

void operator "" _dump(const char16_t* lit, size_t)
{
    printf("operator \"\" _dump(const char16_t*, size_t):\n"                  );
};

void operator "" _dump(const char32_t* lit, size_t)
{
    printf("operator \"\" _dump(const char32_t*, size_t):\n"                  );
};

// Raw literal operator
void operator "" _dump_raw(const char* lit)
{
    printf("operator \"\" _dump_raw(const char*)        : ===>%s<===\n",   lit);
};

template<char...> void operator "" _dump_template();       // Literal operator template

int main(int argc, const char* argv[])
{
    42_dump;
    3.1415926_dump;
    3.14e+25_dump;
     'A'_dump;
    L'B'_dump;
    u'C'_dump;
    U'D'_dump;
      "Hello World"_dump;
     L"Wide String"_dump;
    u8"UTF-8 String"_dump;
     u"UTF-16 String"_dump;
     U"UTF-32 String"_dump;
    42_dump_raw;
    3.1415926_dump_raw;
    3.14e+25_dump_raw;

    // There is no raw literal operator or literal operator template support on these types:
    //  'A'_dump_raw;
    // L'B'_dump_raw;
    // u'C'_dump_raw;
    // U'D'_dump_raw;
    //   "Hello World"_dump_raw;
    //  L"Wide String"_dump_raw;
    // u8"UTF-8 String"_dump_raw;
    //  u"UTF-16 String"_dump_raw;
    //  U"UTF-32 String"_dump_raw;
}
```

```Output
operator "" _dump(unsigned long long int) : ===>42<===
operator "" _dump(long double)            : ===>3.141593<===
operator "" _dump(long double)            : ===>31399999999999998506827776.000000<===
operator "" _dump(char)                   : ===>A<===
operator "" _dump(wchar_t)                : ===>66<===
operator "" _dump(char16_t)               : ===>67<===
operator "" _dump(char32_t)               : ===>68<===
operator "" _dump(const     char*, size_t): ===>Hello World<===
operator "" _dump(const  wchar_t*, size_t): ===>Wide String<===
operator "" _dump(const     char*, size_t): ===>UTF-8 String<===
operator "" _dump(const char16_t*, size_t):
operator "" _dump(const char32_t*, size_t):
operator "" _dump_raw(const char*)        : ===>42<===
operator "" _dump_raw(const char*)        : ===>3.1415926<===
operator "" _dump_raw(const char*)        : ===>3.14e+25<===
```
