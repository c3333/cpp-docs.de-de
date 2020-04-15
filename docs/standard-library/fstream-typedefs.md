---
title: '&lt;fstream&gt; typedefs (<fstream>-Typdefinitionen)'
ms.date: 11/04/2016
f1_keywords:
- fstream/std::filebuf
- fstream/std::fstream
- fstream/std::ifstream
- fstream/std::ofstream
- fstream/std::wfilebuf
- fstream/std::wfstream
- fstream/std::wifstream
- fstream/std::wofstream
ms.assetid: 8dddef2d-7f17-42a6-ba08-6f6f20597d23
ms.openlocfilehash: 57e481c131a6e4a1111b1ed88217b891d6fc96a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317190"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; typedefs (<fstream>-Typdefinitionen)

||||
|-|-|-|
|[filebuf](#filebuf)|[Fstream](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a><a name="filebuf"></a>filebuf

Ein `basic_filebuf` Typ, der auf **char-Vorlagenparameter** spezialisiert ist.

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassenvorlage [basic_filebuf](../standard-library/basic-filebuf-class.md), spezialisiert auf Elemente vom Typ **char** mit Standardzeichenmerkmalen.

## <a name="fstream"></a><a name="fstream"></a>Fstream

Ein `basic_fstream` Typ, der auf **char-Vorlagenparameter** spezialisiert ist.

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassenvorlage [basic_fstream](../standard-library/basic-fstream-class.md), spezialisiert auf Elemente vom Typ **char** mit Standardzeichenmerkmalen.

## <a name="ifstream"></a><a name="ifstream"></a>Ifstream

Definiert einen Stream, der für das serielle Lesen von Einzelbyte-Zeichendaten aus einer Datei verwendet werden soll. `ifstream`ist ein typedef, der die `basic_ifstream` Klassenvorlage für **char**spezialisiert.

Es gibt `wifstream`auch , eine typedef, die sich `basic_ifstream` darauf spezialisiert hat, **wchar_t** doppelt breiten Zeichen zu lesen. Weitere Informationen finden Sie unter [wifstream](../standard-library/fstream-typedefs.md#wifstream).

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassenvorlage [basic_ifstream](../standard-library/basic-ifstream-class.md), spezialisiert auf Elemente vom Typ char mit Standardzeichenmerkmalen. Ein Beispiel ist

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a><a name="ofstream"></a>ofstream

Ein `basic_ofstream` Typ, der auf **char-Vorlagenparameter** spezialisiert ist.

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassenvorlage [basic_ofstream](../standard-library/basic-ofstream-class.md), spezialisiert auf Elemente vom Typ **char** mit Standardzeichenmerkmalen.

## <a name="wfstream"></a><a name="wfstream"></a>wfstream

Ein `basic_fstream` Typ, der auf **wchar_t** Vorlagenparametern spezialisiert ist.

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassenvorlage [basic_fstream](../standard-library/basic-fstream-class.md), spezialisiert auf Elemente vom Typ **wchar_t** mit Standardzeichenmerkmalen.

## <a name="wifstream"></a><a name="wifstream"></a>wifstream

Ein `basic_ifstream` Typ, der auf **wchar_t** Vorlagenparametern spezialisiert ist.

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassenvorlage [basic_ifstream](../standard-library/basic-ifstream-class.md), spezialisiert auf Elemente vom Typ **wchar_t** mit Standardzeichenmerkmalen.

## <a name="wofstream"></a><a name="wofstream"></a>wofstream

Ein `basic_ofstream` Typ, der auf **wchar_t** Vorlagenparametern spezialisiert ist.

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassenvorlage [basic_ofstream](../standard-library/basic-ofstream-class.md), spezialisiert auf Elemente vom Typ **wchar_t** mit Standardzeichenmerkmalen.

## <a name="wfilebuf"></a><a name="wfilebuf"></a>wfilebuf

Ein `basic_filebuf` Typ, der auf **wchar_t** Vorlagenparametern spezialisiert ist.

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassenvorlage [basic_filebuf](../standard-library/basic-filebuf-class.md), spezialisiert auf Elemente vom Typ **wchar_t** mit Standardzeichenmerkmalen.

## <a name="see-also"></a>Siehe auch

[\<fstream>](../standard-library/fstream.md)
