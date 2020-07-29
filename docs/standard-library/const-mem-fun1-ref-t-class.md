---
title: const_mem_fun1_ref_t-Klasse
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_ref_t
helpviewer_keywords:
- const_mem_fun1_ref_t class
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
ms.openlocfilehash: f9f426b7280872846695e204f2c9843d2622fe19
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228335"
---
# <a name="const_mem_fun1_ref_t-class"></a>const_mem_fun1_ref_t-Klasse

Eine Adapter Klasse, die es ermöglicht, **`const`** dass eine Member-Funktion, die ein einzelnes Argument annimmt, als binäres Funktions Objekt aufgerufen wird, wenn Sie mit einem Verweis Argument initialisiert wird. In c++ 11 veraltet, entfernt in c++ 17.

## <a name="syntax"></a>Syntax

```cpp
template <class Result, class Type, class Arg>
    class const_mem_fun1_ref_t
        : public binary_function<Type, Arg, Result>
{
    explicit const_mem_fun1_ref_t(Result (Type::* Pm)(Arg) const);
    Result operator()(const Type& left, Arg right) const;
};
```

### <a name="parameters"></a>Parameter

*14:*\
Ein Zeiger auf die Memberfunktion der Klasse `Type`, die in ein Funktionsobjekt konvertiert werden soll.

*linken*\
Das- **`const`** Objekt, für das die *pm* -Mitglieds Funktion aufgerufen wird.

*Richting*\
Das Argument, das *pm*zugewiesen wird.

## <a name="return-value"></a>Rückgabewert

Eine anpassungsfähige binäre Funktion.

## <a name="remarks"></a>Bemerkungen

In der-Klassen Vorlage wird eine Kopie von *pm*gespeichert, die ein Zeiger auf eine Member-Funktion der-Klasse `Type` in einem privaten Member-Objekt sein muss. Er definiert seine Member-Funktion `operator()` als Rückgabe ( `left` . \* *pm*) ( `right` ) **`const`** .

## <a name="example"></a>Beispiel

Der Konstruktor von `const_mem_fun1_ref_t` wird in der Regel nicht direkt verwendet; die Hilfsfunktion `mem_fun_ref` wird verwendet, um Memberfunktionen anzupassen. Weitere Beispiele für die Verwendung von Memberfunktionsadaptern finden Sie unter [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref).
