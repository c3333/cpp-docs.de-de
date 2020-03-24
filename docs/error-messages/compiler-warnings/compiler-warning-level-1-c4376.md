---
title: Compilerwarnung (Stufe 1) C4376
ms.date: 11/04/2016
f1_keywords:
- C4376
helpviewer_keywords:
- C4376
ms.assetid: 5f202c74-9489-48fe-b36f-19cd882b1589
ms.openlocfilehash: 8009d2e5d09ad173f6150ebe9a907be9f4947cd7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162855"
---
# <a name="compiler-warning-level-1-c4376"></a>Compilerwarnung (Stufe 1) C4376

Zugriffsspezifizierer 'old_specifier:' wird nicht mehr unterstützt: Verwenden Sie stattdessen 'new_specifier:'

Weitere Informationen zum Angeben des Typs und der Member-Barrierefreiheit in den Metadaten finden Sie unter [Typsichtbarkeit](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) und Element [Sichtbarkeit](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility) in Gewusst [wie: definieren undC++verarbeiten von Klassen und Strukturen (/CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4376 generiert.

```cpp
// C4376.cpp
// compile with: /clr /W1 /c
public ref class G {
public public:   // C4376
   void m2();
};

public ref class H {
public:   // OK
   void m2();
};
```
