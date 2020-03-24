---
title: Compilerfehler C3268
ms.date: 11/04/2016
f1_keywords:
- C3268
helpviewer_keywords:
- C3268
ms.assetid: d74a630c-daea-4e29-9759-83efef7fb184
ms.openlocfilehash: 191456a1e290b568897ba76cd5bdccb8f83c310b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201460"
---
# <a name="compiler-error-c3268"></a>Compilerfehler C3268

> "*Function*": eine generische Funktion oder eine Member-Funktion einer generischen Klasse darf keine Variablen Parameterliste aufweisen.

## <a name="remarks"></a>Bemerkungen

Die Compileroptionen **/clr: pure** und **/clr: Safe** sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

Weitere Informationen finden Sie unter [Generika](../../extensions/generics-cpp-component-extensions.md) .

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3268 generiert:

```cpp
// C3268.cpp
// compile with: /clr:pure /c
generic <class ItemType>
void Test(ItemType item, ...) {}   // C3268
// try the following line instead
// void Test(ItemType item) {}

generic <class ItemType2>
ref struct MyStruct { void Test(...){} };   // C3268
// try the following line instead
// ref struct MyStruct { void Test2(){} };   // OK
```
