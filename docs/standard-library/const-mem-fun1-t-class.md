---
title: const_mem_fun1_t-Klasse
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_t
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
ms.openlocfilehash: 93d0e7a116c7c7ba7a2ed1cb46fd88585a99120d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228322"
---
# <a name="const_mem_fun1_t-class"></a>const_mem_fun1_t-Klasse

Eine Adapter Klasse, die es ermöglicht, **`const`** dass eine Member-Funktion, die ein einzelnes Argument annimmt, als binäres Funktions Objekt aufgerufen wird, wenn Sie mit einem Zeigerargument initialisiert wird. In c++ 11 veraltet, entfernt in c++ 17.

## <a name="syntax"></a>Syntax

```cpp
template <class Result, class Type, class Arg>
class const_mem_fun1_t : public binary_function<const Type *, Arg, Result>
{
    explicit const_mem_fun1_t(Result (Type::* member_ptr)(Arg) const);
    Result operator()(const Type* left, Arg right) const;
};
```

### <a name="parameters"></a>Parameter

*member_ptr*\
Ein Zeiger auf die Memberfunktion der Klasse `Type`, die in ein Funktionsobjekt konvertiert werden soll.

*linken*\
Das- **`const`** Objekt, für das die *member_ptr* Member-Funktion aufgerufen wird.

*Richting*\
Das Argument, das *member_ptr*angegeben wird.

## <a name="return-value"></a>Rückgabewert

Eine anpassungsfähige binäre Funktion.

## <a name="remarks"></a>Bemerkungen

In der-Klassen Vorlage wird eine Kopie von *member_ptr*gespeichert, die ein Zeiger auf eine Member-Funktion der-Klasse `Type` in einem privaten Member-Objekt sein muss. Die Member-Funktion wird `operator()` als zurückgegeben definiert `(left->member_ptr)(right) const` .

## <a name="example"></a>Beispiel

Der Konstruktor von `const_mem_fun1_t` wird nur selten direkt verwendet. `mem_fn`wird verwendet, um Member-Funktionen anzupassen. Ein Beispiel für die Verwendung von Membern für Member-Funktionen finden Sie unter [mem_fn](../standard-library/functional-functions.md#mem_fn) .
