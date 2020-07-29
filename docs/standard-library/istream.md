---
title: '&lt;istream&gt;'
ms.date: 11/04/2016
f1_keywords:
- istream/std::<istream>
- <istream>
- std::<istream>
helpviewer_keywords:
- istream header
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
ms.openlocfilehash: 37399bb50f195c683b52eea4c8fadf8679d62852
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233092"
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

Definiert die Klassen Vorlagen Basic_istream, die Extraktionen für die Iostreams vermittelt, und die Klassen Vorlage Basic_iostream, die sowohl Einfügungen-als auch Extraktionen vermittelt. Der Header definiert auch einen verknüpften Manipulator. Diese Headerdatei wird in der Regel von einem anderen Iostreams-Header eingeschlossen. Sie müssen sie nur selten direkt einschließen.

## <a name="syntax"></a>Syntax

```cpp
#include <istream>
```

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[iostream](../standard-library/istream-typedefs.md#iostream)|Ein Typ, `basic_iostream` der auf spezialisiert ist **`char`** .|
|[istream](../standard-library/istream-typedefs.md#istream)|Ein Typ, `basic_istream` der auf spezialisiert ist **`char`** .|
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|Ein `basic_iostream`-Typ, der auf **wchar** spezialisiert ist.|
|[wistream](../standard-library/istream-typedefs.md#wistream)|Ein `basic_istream`-Typ, der auf **wchar** spezialisiert ist.|

### <a name="manipulators"></a>Manipulatoren

|||
|-|-|
|[Gefangener](../standard-library/istream-functions.md#ws)|Überspringt Leerraum im Datenstrom.|
|[swap](../standard-library/istream-functions.md#istream_swap)|Tauscht zwei Streamobjekte.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator>>](../standard-library/istream-operators.md#op_gt_gt)|Extrahiert von Zeichenfolgen und Zeichen aus dem Stream.|

### <a name="classes"></a>Klassen

|Klasse|BESCHREIBUNG|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|Eine Streamklasse für Ein- und Ausgabe.|
|[basic_istream](../standard-library/basic-istream-class.md)|Die Klassen Vorlage beschreibt ein Objekt, das das Extrahieren von Elementen und codierten Objekten aus einem Streampuffer mit Elementen des Typs steuert `Elem` , der auch als " [char_type](../standard-library/basic-ios-class.md#char_type)" bezeichnet wird, dessen Zeichen Merkmale von der Klasse bestimmt werden `Tr` , die auch als [Traits_type](../standard-library/basic-ios-class.md#traits_type)bezeichnet wird.|

## <a name="see-also"></a>Siehe auch

[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[Iostreams-Konventionen](../standard-library/iostreams-conventions.md)
