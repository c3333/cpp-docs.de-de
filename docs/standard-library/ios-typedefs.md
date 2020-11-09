---
title: typedef `<ios>`
description: Beschreibt die C++-Standardvorlagen Bibliothek (STL)- `<ios>` Typedefs, die die- `ios` Klasse aus der alten Bibliothek unterstützen `iostream` .
ms.date: 11/06/2020
f1_keywords:
- iosfwd/std::ios
- iosfwd/std::streamoff
- iosfwd/std::streampos
- iosfwd/std::streamsize
- iosfwd/std::wios
- iosfwd/std::wstreampos
ms.openlocfilehash: 4af9636ab3317e7b81eb73dc74aef065b1287e21
ms.sourcegitcommit: 3f0c1dcdcce25865d1a1022bcc5b9eec79f69025
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2020
ms.locfileid: "94381635"
---
# <a name="ios-typedefs"></a>typedef `<ios>`

## `ios`

Unterstützt die- `ios` Klasse aus der alten `iostream` Bibliothek.

```cpp
typedef basic_ios<char, char_traits<char>> ios;
```

### <a name="remarks"></a>Hinweise

Der Typ ist ein Synonym für eine Klassen Vorlage [`basic_ios`](../standard-library/basic-ios-class.md) , die auf Elemente des Typs **`char`** mit Standard Zeichen Merkmalen spezialisiert ist.

## `streamoff`

Unterstützt interne Vorgänge.

```cpp
#ifdef _WIN64
    typedef __int64 streamoff;
#else
    typedef long streamoff;
#endif
```

### <a name="remarks"></a>Hinweise

Der Typ ist eine Ganzzahl mit Vorzeichen. Es beschreibt ein Objekt, das einen Byte Offset in streampositionierungsvorgängen speichern kann. Seine Repräsentation hat mindestens 32 Wertbits. Es ist nicht notwendigerweise groß genug, um eine beliebige Byte Position innerhalb eines Streams darzustellen. Der Wert `streamoff(-1)` weist im Allgemeinen auf einen fehlerhaften Offset hin.

## `streampos`

Enthält die aktuelle Position des Pufferzeigers oder Dateizeigers.

```cpp
typedef fpos<mbstate_t> streampos;
```

### <a name="remarks"></a>Hinweise

Der Typ ist ein Synonym für [`fpos`](../standard-library/fpos-class.md) <  `mbstate_t`>.

### <a name="example"></a>Beispiel

```cpp
// ios_streampos.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   ofstream x( "iostream.txt" );
   x << "testing";
   streampos y = x.tellp( );
   cout << streamoff(y) << '\n';
}
```

```Output
7
```

## `streamsize`

Bezeichnet die Größe des Streams.

```cpp
#ifdef _WIN64
    typedef __int64 streamsize;
#else
    typedef int streamsize;
#endif
```

### <a name="remarks"></a>Hinweise

Der Typ ist eine Ganzzahl mit Vorzeichen, die ein Objekt beschreibt, das die Anzahl von Objekten speichern kann, die an verschiedenen Streamvorgängen beteiligt sind. Seine Repräsentation verfügt über mindestens 16 Bits. Es ist nicht notwendigerweise groß genug, um eine beliebige Byte Position innerhalb eines Streams darzustellen.

### <a name="example"></a>Beispiel

Nach dem Kompilieren und Ausführen des folgenden Programms sehen Sie sich die Datei `test.txt` an, um die Auswirkung der Einstellung anzuzeigen `streamsize` .

```cpp
// ios_streamsize.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   char a[16] = "any such text";
   ofstream x( "test.txt" );
   streamsize y = 6;
   x.write( a, y );
}
```

## `wios`

Unterstützt die- `wios` Klasse aus der alten `iostream` Bibliothek.

```cpp
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;
```

### <a name="remarks"></a>Hinweise

Der Typ ist ein Synonym für eine Klassen Vorlage [`basic_ios`](../standard-library/basic-ios-class.md) , die auf Elemente des Typs **`wchar_t`** mit Standard Zeichen Merkmalen spezialisiert ist.

## `wstreampos`

Enthält die aktuelle Position des Pufferzeigers oder Dateizeigers.

```cpp
typedef fpos<mbstate_t> wstreampos;
```

### <a name="remarks"></a>Hinweise

Der Typ ist ein Synonym für [`fpos`](../standard-library/fpos-class.md) <  `mbstate_t`>.

### <a name="example"></a>Beispiel

```cpp
// ios_wstreampos.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   wofstream xw( "wiostream.txt" );
   xw << L"testing";
   wstreampos y = xw.tellp( );
   cout << y << endl;
}
```

```Output
7
```
