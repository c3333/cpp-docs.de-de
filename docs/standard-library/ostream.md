---
title: '&lt;ostream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ostream>
- ostream/std::<ostream>
- std::<ostream>
helpviewer_keywords:
- ostream header
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
ms.openlocfilehash: 37642cbcbe57fba54f071a8fc94af53c97684a36
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228140"
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;

Definiert die Klassen Vorlagen [basic_ostream](../standard-library/basic-ostream-class.md), die Einfügungen für die Iostreams vermittelt. Der Header definiert auch mehrere verwandte Manipulatoren. Dieser Header wird in der Regel von einem der anderen iostreams-Header für Sie eingefügt. Sie müssen ihn nur selten direkt einfügen.)

## <a name="syntax"></a>Syntax

```cpp
#include <ostream>
```

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|Erstellt einen Typ aus `basic_ostream` , der spezialisiert ist **`char`** und auf `char_traits` spezialisiert ist **`char`** .|
|[wostream](../standard-library/ostream-typedefs.md#wostream)|Erstellt einen Typ aus `basic_ostream` , der spezialisiert ist **`wchar_t`** und auf `char_traits` spezialisiert ist **`wchar_t`** .|

### <a name="manipulators"></a>Manipulatoren

|||
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|Beendet eine Zeile und leert den Puffer.|
|[Runden](../standard-library/ostream-functions.md#ends)|Beendet eine Zeichenfolge.|
|[Flächen](../standard-library/ostream-functions.md#flush)|Leert den Puffer.|
|[swap](../standard-library/ostream-functions.md#swap)|Tauscht die Werte des linken `basic_ostream`-Objektparameters gegen diejenigen des rechten `basic_ostream`-Objektparameters aus.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator<<](../standard-library/ostream-operators.md#op_lt_lt)|Schreibt verschiedene Typen in den Stream.|

### <a name="classes"></a>Klassen

|Klasse|BESCHREIBUNG|
|-|-|
|[basic_ostream](../standard-library/basic-ostream-class.md)|Die Klassen Vorlage beschreibt ein Objekt, das das Einfügen von Elementen und codierten Objekten in einen Streampuffer steuert.|

## <a name="see-also"></a>Siehe auch

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[Iostreams-Konventionen](../standard-library/iostreams-conventions.md)
