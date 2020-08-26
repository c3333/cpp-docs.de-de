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
ms.openlocfilehash: 3b950192e098815739c30b732f1caee755c69f26
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835713"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; typedefs (<fstream>-Typdefinitionen)

[filebuf](#filebuf)\
[FStream](#fstream)\
[ifstream](#ifstream)\
[ofstream](#ofstream)\
[wfilebuf](#wfilebuf)\
[wfstream](#wfstream)\
[wifstream](#wifstream)\
[wofstream](#wofstream)

## <a name="filebuf"></a><a name="filebuf"></a> filebuf

Ein Typ, `basic_filebuf` der auf **`char`** Vorlagen Parameter spezialisiert ist.

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassen Vorlagen [Basic_filebuf](../standard-library/basic-filebuf-class.md), das auf Elemente des Typs **`char`** mit Standard Zeichen Merkmalen spezialisiert ist.

## <a name="fstream"></a><a name="fstream"></a> FStream

Ein Typ, `basic_fstream` der auf **`char`** Vorlagen Parameter spezialisiert ist.

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassen Vorlagen [Basic_fstream](../standard-library/basic-fstream-class.md), das auf Elemente des Typs **`char`** mit Standard Zeichen Merkmalen spezialisiert ist.

## <a name="ifstream"></a><a name="ifstream"></a> ifstream

Definiert einen Stream, der für das serielle Lesen von Einzelbyte-Zeichendaten aus einer Datei verwendet werden soll. `ifstream` ist eine typedef, die die Klassen Vorlage `basic_ifstream` für spezialisiert **`char`** .

Außerdem gibt es `wifstream` eine typedef, die `basic_ifstream` auf das Lesen von **`wchar_t`** doppelten Zeichen spezialisiert ist. Weitere Informationen finden Sie unter [wifstream](../standard-library/fstream-typedefs.md#wifstream).

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassen Vorlagen [basic_ifstream](../standard-library/basic-ifstream-class.md), die auf Elemente vom Typ "char" mit Standard Zeichen Merkmalen spezialisiert ist. Ein Beispiel ist

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a><a name="ofstream"></a> ofstream

Ein Typ, `basic_ofstream` der auf **`char`** Vorlagen Parameter spezialisiert ist.

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassen Vorlagen [basic_ofstream](../standard-library/basic-ofstream-class.md), das auf Elemente des Typs **`char`** mit Standard Zeichen Merkmalen spezialisiert ist.

## <a name="wfstream"></a><a name="wfstream"></a> wfstream

Ein Typ, `basic_fstream` der auf **`wchar_t`** Vorlagen Parameter spezialisiert ist.

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassen Vorlagen [Basic_fstream](../standard-library/basic-fstream-class.md), das auf Elemente des Typs **`wchar_t`** mit Standard Zeichen Merkmalen spezialisiert ist.

## <a name="wifstream"></a><a name="wifstream"></a> wifstream

Ein Typ, `basic_ifstream` der auf **`wchar_t`** Vorlagen Parameter spezialisiert ist.

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassen Vorlagen [basic_ifstream](../standard-library/basic-ifstream-class.md), das auf Elemente des Typs **`wchar_t`** mit Standard Zeichen Merkmalen spezialisiert ist.

## <a name="wofstream"></a><a name="wofstream"></a> wofstream

Ein Typ, `basic_ofstream` der auf **`wchar_t`** Vorlagen Parameter spezialisiert ist.

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassen Vorlagen [basic_ofstream](../standard-library/basic-ofstream-class.md), das auf Elemente des Typs **`wchar_t`** mit Standard Zeichen Merkmalen spezialisiert ist.

## <a name="wfilebuf"></a><a name="wfilebuf"></a> wfilebuf

Ein Typ, `basic_filebuf` der auf **`wchar_t`** Vorlagen Parameter spezialisiert ist.

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassen Vorlagen [Basic_filebuf](../standard-library/basic-filebuf-class.md), das auf Elemente des Typs **`wchar_t`** mit Standard Zeichen Merkmalen spezialisiert ist.

## <a name="see-also"></a>Weitere Informationen

[\<fstream>](../standard-library/fstream.md)
