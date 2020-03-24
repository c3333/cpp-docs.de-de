---
title: Compilerwarnung (Stufe 1) C4691
ms.date: 11/04/2016
f1_keywords:
- C4691
helpviewer_keywords:
- C4691
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
ms.openlocfilehash: 8065129e20b627eb387421455527f6aaec3fdc2f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175375"
---
# <a name="compiler-warning-level-1-c4691"></a>Compilerwarnung (Stufe 1) C4691

"Typ": der Typ, auf den verwiesen wird, wurde in einer nicht referenzierten Assembly "file" erwartet, die in der aktuellen Übersetzungseinheit definiert ist.

Es wird nicht auf die Metadatendatei verwiesen, die die ursprüngliche Typdefinition enthält, und der Compiler verwendet eine lokale Typdefinition.

Wenn Sie die *Datei*neu erstellen, kann C4691 mit der Pragma- [Warnung](../../preprocessor/warning.md)ignoriert oder deaktiviert werden.  Das heißt, wenn die Datei, die Sie aufbauen, mit der Datei identisch ist, in der der Compiler die Typdefinition finden soll, können Sie C4691 ignorieren.

Es kann jedoch ein unerwartetes Verhalten auftreten, wenn der Compiler eine Definition verwendet, die nicht aus derselben Assembly gehört, auf die in den Metadaten verwiesen wird. CLR-Typen werden nicht nur durch den Namen des Typs, sondern auch durch die Assembly typisiert.  Das heißt, ein Typ z von der Assembly z. dll unterscheidet sich von dem Typ z von der Assembly y. dll.

## <a name="example"></a>Beispiel

Dieses Beispiel enthält die ursprüngliche Typdefinition.

```cpp
// C4691_a.cpp
// compile with: /clr /LD /W1
public ref class Original_Type {};
```

## <a name="example"></a>Beispiel

In diesem Beispiel wird auf C4691_a. dll verwiesen und ein Feld vom Typ Original_Type deklariert.

```cpp
// C4691_b.cpp
// compile with: /clr /LD
#using "C4691_a.dll"
public ref class Client {
public:
   Original_Type^ ot;
};
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4691 generiert.  Beachten Sie, dass dieses Beispiel eine Definition für Original_Type enthält und nicht auf C4691a. dll verweist.

Um dies aufzulösen, verweisen Sie auf die Metadatendatei, die die ursprüngliche Typdefinition enthält, und entfernen Sie die lokale Deklaration und Definition.

```cpp
// C4691_c.cpp
// compile with: /clr /LD /W1
// C4691 expected

// Uncomment the following line to resolve.
// #using "C4691_a.dll"
#using "C4691_b.dll"

// Delete the following line to resolve.
ref class Original_Type;

public ref class MyClass : Client {};
```
