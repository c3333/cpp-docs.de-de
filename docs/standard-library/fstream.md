---
title: '&lt;fstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: 46f65f746179740f2d67dd1ada2f96ab3fb6aaf6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203233"
---
# <a name="ltfstreamgt"></a>&lt;fstream&gt;

Definiert mehrere Klassen, die iostreams-Vorgänge für Sequenzen unterstützen, die in externen Dateien gespeichert sind.

## <a name="syntax"></a>Syntax

```cpp
#include <fstream>
```

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|Ein Typ, `basic_filebuf` der auf **`char`** Vorlagen Parameter spezialisiert ist.|
|[FStream](../standard-library/fstream-typedefs.md#fstream)|Ein Typ, `basic_fstream` der auf **`char`** Vorlagen Parameter spezialisiert ist.|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|Ein Typ, `basic_ifstream` der auf **`char`** Vorlagen Parameter spezialisiert ist.|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|Ein Typ, `basic_ofstream` der auf **`char`** Vorlagen Parameter spezialisiert ist.|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|Ein Typ, `basic_fstream` der auf **`wchar_t`** Vorlagen Parameter spezialisiert ist.|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|Ein Typ, `basic_ifstream` der auf **`wchar_t`** Vorlagen Parameter spezialisiert ist.|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|Ein Typ, `basic_ofstream` der auf **`wchar_t`** Vorlagen Parameter spezialisiert ist.|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|Ein Typ, `basic_filebuf` der auf **`wchar_t`** Vorlagen Parameter spezialisiert ist.|

### <a name="classes"></a>Klassen

|Klasse|BESCHREIBUNG|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|Die Klassen Vorlage beschreibt einen Streampuffer, der die Übertragung von Elementen des Typs steuert `Elem` , dessen Zeichen Merkmale von der Klasse bestimmt werden `Tr` , in eine und aus einer Sequenz von Elementen, die in einer externen Datei gespeichert sind.|
|[basic_fstream](../standard-library/basic-fstream-class.md)|In der Klassen Vorlage wird ein Objekt beschrieben, das das Einfügen und Extrahieren von Elementen und codierten Objekten mit einem Streampuffer der Klasse [Basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **Tr**> mit Elementen des Typs steuert `Elem` , dessen Zeichen Merkmale von der Klasse bestimmt werden `Tr` .|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|Die Klassen Vorlage beschreibt ein Objekt, das das Extrahieren von Elementen und codierten Objekten aus einem Streampuffer der Klasse [Basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **Tr**> mit Elementen des Typs steuert `Elem` , dessen Zeichen Merkmale von der Klasse bestimmt werden `Tr` .|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|In der Klassen Vorlage wird ein Objekt beschrieben, das das Einfügen von Elementen und codierten Objekten in einen Streampuffer der Klasse [Basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **Tr**> mit Elementen des Typs steuert `Elem` , dessen Zeichen Merkmale von der Klasse bestimmt werden `Tr` .|

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[Iostreams-Konventionen](../standard-library/iostreams-conventions.md)
