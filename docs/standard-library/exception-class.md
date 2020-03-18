---
title: exception-Klasse
ms.date: 11/04/2016
f1_keywords:
- exception/std::exception
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
ms.openlocfilehash: 5bef8190889ae00298760ea395fb524f557c2be2
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446831"
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

Diese Basisklasse bildet den Stamm der Standard Ausnahmeklassen, die in [\<stdexcept>](../standard-library/stdexcept.md) definiert sind. Der Wert der C-Zeichenfolge, der durch `what` zurückgegeben wird, wird vom Standardkonstruktor nicht angegeben, kann aber von den Konstruktoren für bestimmte abgeleitete Klassen als durch die Implementierung definierte C-Zeichenfolge angegeben werden. Keine der Memberfunktionen löst irgendeine Ausnahme aus.

Mit dem **int** -Parameter können Sie angeben, dass kein Arbeitsspeicher zugewiesen werden soll. Der Wert des **int** -Werts wird ignoriert.

> [!NOTE]
> Die Konstruktoren `exception(const char* const &message)` und `exception(const char* const &message, int)` sind Microsoft-Erweiterungen der C++-Standardbibliothek.

## <a name="example"></a>Beispiel

Beispiele für die Verwendung von Standard Ausnahmeklassen, die von der `exception`-Klasse erben, finden Sie in allen unter [\<stdexcept >](../standard-library/stdexcept.md) definierten Klassen.
