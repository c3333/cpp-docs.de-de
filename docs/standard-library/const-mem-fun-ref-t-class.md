---
title: const_mem_fun_ref_t-Klasse
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun_ref_t
helpviewer_keywords:
- const_mem_fun_ref_t class
ms.assetid: 316ddbaa-9f46-4931-8eba-ea4ca66360ef
ms.openlocfilehash: 09d8569253dbeb1a873f4fc7b64b55658511d18e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228361"
---
# <a name="const_mem_fun_ref_t-class"></a>const_mem_fun_ref_t-Klasse

Eine Adapter Klasse, die es ermöglicht, **`const`** dass eine Member-Funktion, die keine Argumente annimmt, als unäres Funktions Objekt aufgerufen wird, wenn Sie mit einem Verweis Argument initialisiert wird. In c++ 11 veraltet, entfernt in c++ 17.

## <a name="syntax"></a>Syntax

```cpp
template <class Result, class Type>
    class const_mem_fun_ref_t
: public unary_function<Type, Result>
{
    explicit const_mem_fun_t(Result (Type::* Pm)() const);
    Result operator()(const Type& left) const;
};
```

### <a name="parameters"></a>Parameter

*14:*\
Ein Zeiger auf die Memberfunktion der Klasse `Type`, die in ein Funktionsobjekt konvertiert werden soll.

*linken*\
Das-Objekt, für das die *pm* -Mitglieds Funktion aufgerufen wird.

## <a name="return-value"></a>Rückgabewert

Eine anpassungsfähige unäre Funktion.

## <a name="remarks"></a>Bemerkungen

In der-Klassen Vorlage wird eine Kopie von *pm*gespeichert, die ein Zeiger auf eine Member-Funktion der-Klasse `Type` in einem privaten Member-Objekt sein muss. Er definiert seine Member-Funktion `operator()` als Rückgabe (**Links** \* `Pm` ). () **`const`**.

## <a name="example"></a>Beispiel

Der Konstruktor von `const_mem_fun_ref_t` wird in der Regel nicht direkt verwendet; die Hilfsfunktion `mem_fun_ref` wird verwendet, um Memberfunktionen anzupassen. Weitere Beispiele für die Verwendung von Memberfunktionsadaptern finden Sie unter [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref).
