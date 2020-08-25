---
title: '&lt;strstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <strstream>
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
ms.openlocfilehash: 13eea1101abca0f79f0d7c15405ceb3118707b67
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845652"
---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;

Definiert mehrere Klassen, die Iostreams-Vorgänge für Sequenzen unterstützen, die in einem zugewiesenen Array von-Objekten gespeichert sind **`char`** . Solche Sequenzen sind leicht in und aus C-Zeichenfolgen zu konvertieren.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<strstream>

**Namespace:** std

## <a name="remarks"></a>Bemerkungen

Objekte des Typs `strstream` funktionieren mit **`char`** *, die C-Zeichen folgen sind. Verwenden [\<sstream>](../standard-library/sstream.md) Sie, um mit Objekten vom Typ [basic_string](../standard-library/basic-string-class.md)zu arbeiten.

> [!NOTE]
> Die Klassen in \<strstream> sind veraltet. Verwenden Sie stattdessen die Klassen in \<sstream>.

## <a name="members"></a>Member

### <a name="classes"></a>Klassen

|name|Beschreibung|
|-|-|
|[Klasse "straustreambuf"](../standard-library/strstreambuf-class.md)|Die Klasse beschreibt einen Streampuffer, der die Übertragung von Elementen in eine und aus einer Sequenz von Elementen steuert, die in einem- **`char`** Array Objekt gespeichert sind.|
|[istrinstream-Klasse](../standard-library/istrstream-class.md)|Die Klasse beschreibt ein Objekt, das die Extraktion von Elementen und codierten Objekten aus einem Streampuffer der Klasse [strstreambuf](../standard-library/strstreambuf-class.md) steuert.|
|[Ostrstream-Klasse](../standard-library/ostrstream-class.md)|Die Klasse beschreibt ein Objekt, das die Einfügung von Elementen und codierten Objekten in einen Streampuffer der Klasse [strstreambuf](../standard-library/strstreambuf-class.md) steuert.|
|[Klasse "straustream"](../standard-library/strstream-class.md)|Die Klasse beschreibt ein Objekt, das die Einfügung und Extraktion von Elementen und codierten Objekten mit einem Streampuffer der Klasse [strstreambuf](../standard-library/strstreambuf-class.md) steuert.|

### <a name="functions"></a>Functions

```cpp
void freeze(bool freezefl = true);
char* str();
int pcount();
```

## <a name="see-also"></a>Weitere Informationen

[\<strstream>](../standard-library/strstream.md)\
[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[Iostreams-Konventionen](../standard-library/iostreams-conventions.md)
