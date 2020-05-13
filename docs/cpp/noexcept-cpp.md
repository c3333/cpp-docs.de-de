---
title: noexcept (C++)
ms.date: 11/19/2019
f1_keywords:
- noexcept_cpp
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
ms.openlocfilehash: efb5ad272c8857e7a0dbd2c75885b826f2b8b9f8
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825363"
---
# <a name="noexcept-c"></a>noexcept (C++)

**C++ 11:** Gibt an, ob eine Funktion Ausnahmen auslösen kann.

## <a name="syntax"></a>Syntax

> *noaußer-Ausdruck*: \
> &nbsp;&nbsp;&nbsp;&nbsp;**noexcept**\
> &nbsp;&nbsp;&nbsp;&nbsp;**noaußer (** *Constant-Expression* **)**

### <a name="parameters"></a>Parameter

*Constant-Expression*<br/>
Ein konstanter Ausdruck vom Typ **bool** , der angibt, ob der Satz potenzieller Ausnahme Typen leer ist. Die bedingungslose Version entspricht `noexcept(true)`.

## <a name="remarks"></a>Bemerkungen

Ein *noaußer-Ausdruck* ist eine Art von *Ausnahme Spezifikation*, ein Suffix für eine Funktionsdeklaration, die einen Satz von Typen darstellt, die möglicherweise von einem Ausnahmehandler für jede Ausnahme, die eine Funktion beendet, abgeglichen werden. Unärer Bedingter Operator `noexcept(` *constant_expression* `)` , bei dem *constant_expression* **true**ergibt, und das Bedingungs bedingte Synonym " **noaußer**" gibt an, dass der Satz potenzieller Ausnahme Typen, die eine Funktion beenden können, leer ist. Das heißt, die Funktion löst nie eine Ausnahme aus und lässt niemals zu, dass eine Ausnahme außerhalb des Gültigkeits Bereichs weitergegeben wird. Der Operator `noexcept(` *constant_expression* `)` , in dem *constant_expression* **false**ergibt, oder das Fehlen einer Ausnahme Spezifikation (außer für einen Dekonstruktor oder eine Funktion zum Aufheben der Zuordnung) gibt an, dass der Satz möglicher Ausnahmen, die die Funktion beenden können, der Satz aller Typen ist.

Markieren Sie eine Funktion als " **noaußer** " nur, wenn alle Funktionen, die Sie direkt oder indirekt aufruft, auch " **noaußer** " oder " **konstant**" sind. Der Compiler überprüft nicht unbedingt jeden Codepfad auf Ausnahmen, die möglicherweise zu einer " **noaußer** "-Funktion hochskalieren. Wenn eine Ausnahme den äußeren Gültigkeitsbereich einer markierten `noexcept`Funktion beendet, wird " [Std::](../standard-library/exception-functions.md#terminate) End" sofort aufgerufen, und es gibt keine Garantie dafür, dass Dekonstruktoren von im Gültigkeitsbereich befindlichen Objekten aufgerufen werden. Verwenden Sie **noaußer** anstelle des dynamischen ausnahmebezeichers `throw()`, der jetzt im Standard veraltet ist. Es wird empfohlen, `noexcept` dass Sie auf jede Funktion anwenden, die keine Ausnahme zulässt, um die aufzurufende Stapel aufzurufen. Wenn eine Funktion als " **noaußer**" deklariert wird, ermöglicht Sie dem Compiler, effizienteren Code in verschiedenen Kontexten zu generieren. Weitere Informationen finden Sie unter [Ausnahme Spezifikationen](exception-specifications-throw-cpp.md).

## <a name="example"></a>Beispiel

Eine Vorlagen Funktion, die ihr Argument kopiert, kann als " **No"** deklariert werden, außer für die Bedingung, dass das kopierte Objekt ein Plain Old Data Type (Pod) ist. Eine solche Funktion kann wie folgt deklariert werden:

```cpp
#include <type_traits>

template <typename T>
T copy_object(const T& obj) noexcept(std::is_pod<T>)
{
   // ...
}
```

## <a name="see-also"></a>Weitere Informationen

[Modern C++ bewährte Methoden für Ausnahmen und Fehlerbehandlung](errors-and-exception-handling-modern-cpp.md)<br/>
[Ausnahme Spezifikationen (throw, noaußer)](exception-specifications-throw-cpp.md)
