---
title: '&lt;ios&gt;-Typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ios
- iosfwd/std::streamoff
- iosfwd/std::streampos
- iosfwd/std::streamsize
- iosfwd/std::wios
- iosfwd/std::wstreampos
ms.assetid: 0b962632-3439-44de-bf26-20c67a7f0ff3
ms.openlocfilehash: 0f63f65fb4c10fbe2ad538852222e6468b9061d0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375400"
---
# <a name="ltiosgt-typedefs"></a>&lt;ios&gt;-Typedefs

## <a name="ios"></a><a name="ios"></a>Ios

Unterstützt die ios-Klasse aus der alten iostream-Bibliothek.

```cpp
typedef basic_ios<char, char_traits<char>> ios;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassenvorlage [basic_ios](../standard-library/basic-ios-class.md), spezialisiert auf Elemente vom Typ **char** mit Standardzeichenmerkmalen.

## <a name="streamoff"></a><a name="streamoff"></a>Streamoff

Unterstützt interne Vorgänge.

```cpp
#ifdef _WIN64
    typedef __int64 streamoff;
#else
    typedef long streamoff;
#endif
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist eine Ganzzahl mit Vorzeichen, die ein Objekt beschreibt, das einen Byte-Offset speichern kann, der an verschiedenen Streampositionierungsvorgängen beteiligt ist. Seine Repräsentation hat mindestens 32 Wertbits. Er ist nicht unbedingt groß genug, um eine willkürliche Byte-Position innerhalb eines Streams repräsentieren zu können. Der `streamoff(-1)` Wert gibt im Allgemeinen einen fehlerhaften Offset an.

## <a name="streampos"></a><a name="streampos"></a>streampos

Enthält die aktuelle Position des Pufferzeigers oder Dateizeigers.

```cpp
typedef fpos<mbstate_t> streampos;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für [fpos](../standard-library/fpos-class.md) <  `mbstate_t`>.

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
   cout << y << endl;
}
```

```Output
7
```

## <a name="streamsize"></a><a name="streamsize"></a>Streamgröße

Bezeichnet die Größe des Streams.

```cpp
#ifdef _WIN64
    typedef __int64 streamsize;
#else
    typedef int streamsize;
#endif
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist eine Ganzzahl mit Vorzeichen, die ein Objekt beschreibt, das die Anzahl von Objekten speichern kann, die an verschiedenen Streamvorgängen beteiligt sind. Seine Repräsentation verfügt über mindestens 16 Bits. Er ist nicht unbedingt groß genug, um eine willkürliche Byte-Position innerhalb eines Streams repräsentieren zu können.

### <a name="example"></a>Beispiel

Nachdem Sie folgendes Programm kompiliert und ausgeführt haben, öffnen Sie die Datei test.txt,, um den Effekt der Einstellung `streamsize` zu überprüfen.

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

## <a name="wios"></a><a name="wios"></a>wios

Unterstützt die wios-Klasse aus der alten iostream-Bibliothek.

```cpp
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassenvorlage [basic_ios](../standard-library/basic-ios-class.md), spezialisiert auf Elemente vom Typ **wchar_t** mit Standardzeichenmerkmalen.

## <a name="wstreampos"></a><a name="wstreampos"></a>wstreampos

Enthält die aktuelle Position des Pufferzeigers oder Dateizeigers.

```cpp
typedef fpos<mbstate_t> wstreampos;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für [fpos](../standard-library/fpos-class.md) <  `mbstate_t`>.

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
