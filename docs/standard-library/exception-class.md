---
title: exception-Klasse
ms.date: 11/04/2016
f1_keywords:
- exception/std::exception
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
ms.openlocfilehash: fd3fb3c48e9501b7aaf90bca14ea98530b245ec0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228270"
---
# <a name="exception-class"></a>exception-Klasse

Die Klasse dient als Basisklasse für alle Ausnahmen, die durch spezifische Ausdrücke und die C++-Standardbibliothek ausgelöst werden.

## <a name="syntax"></a>Syntax

```cpp
class exception {
   public:
   exception();
   exception(const char* const &message);
   exception(const char* const &message, int);
   exception(const exception &right);
   exception& operator=(const exception &right);
   virtual ~exception();
   virtual const char *what() const;
};
```

## <a name="remarks"></a>Bemerkungen

Dabei handelt es sich um den Stamm der Standard Ausnahme Klassen, die in definiert sind [\<stdexcept>](../standard-library/stdexcept.md) . Der Wert der C-Zeichenfolge, der durch `what` zurückgegeben wird, wird vom Standardkonstruktor nicht angegeben, kann aber von den Konstruktoren für bestimmte abgeleitete Klassen als durch die Implementierung definierte C-Zeichenfolge angegeben werden. Keine der Memberfunktionen löst irgendeine Ausnahme aus.

Mit dem- **`int`** Parameter können Sie angeben, dass kein Arbeitsspeicher zugewiesen werden soll. Der Wert von **`int`** wird ignoriert.

> [!NOTE]
> Die Konstruktoren `exception(const char* const &message)` und `exception(const char* const &message, int)` sind Microsoft-Erweiterungen der C++-Standardbibliothek.

## <a name="example"></a>Beispiel

Beispiele für die Verwendung der Standard Ausnahme Klassen, die von der- `exception` Klasse erben, finden Sie unter einer der Klassen, die in definiert sind [\<stdexcept>](../standard-library/stdexcept.md) .
