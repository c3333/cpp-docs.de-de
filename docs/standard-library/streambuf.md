---
title: '&lt;streambuf&gt;'
ms.date: 11/04/2016
f1_keywords:
- <streambuf>
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
ms.openlocfilehash: 1121bd4e782fca57588d05fb29b5b9b6cdec18e9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215607"
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;

Fügen Sie den Iostreams-Standard Header ein, \<streambuf> um die Klassen Vorlage [basic_streambuf](../standard-library/basic-streambuf-class.md)zu definieren, die für den Betrieb der iostreams-Klassen grundlegend ist. Dieser Header wird in der Regel von einem der anderen iostreams-Header für Sie eingefügt. Sie müssen ihn nur selten direkt einfügen.

## <a name="syntax"></a>Syntax

```cpp
#include <streambuf>
```

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|Eine Spezialisierung von `basic_streambuf` , die **`char`** als Vorlagen Parameter verwendet.|
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|Eine Spezialisierung von `basic_streambuf` , die **`wchar_t`** als Vorlagen Parameter verwendet.|

### <a name="classes"></a>Klassen

|Klasse|BESCHREIBUNG|
|-|-|
|[basic_streambuf-Klasse](basic-streambuf-class.md)|Die Klassen Vorlage beschreibt eine abstrakte Basisklasse für die Ableitung eines Streampuffers, der die Übertragung von Elementen in eine und aus einer bestimmten Darstellung eines Streams steuert.|

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[Iostreams-Konventionen](../standard-library/iostreams-conventions.md)
