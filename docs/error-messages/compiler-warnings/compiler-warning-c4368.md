---
title: Compilerwarnung C4368
ms.date: 11/04/2016
f1_keywords:
- C4368
helpviewer_keywords:
- C4368
ms.assetid: cb85bcee-fd3d-4aa5-b626-2324f07a4f1b
ms.openlocfilehash: d96ae14bc427568dcf7ba7bc6e5d53f3d28883ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165301"
---
# <a name="compiler-warning-c4368"></a>Compilerwarnung C4368

'Member' kann nicht als Member des verwalteten 'Typs' definiert werden: Gemischte Typen werden nicht unterstützt

Sie können keinen systemeigenen Datenmember in einen CLR-Typ einbetten.

Sie können jedoch einen Zeiger auf einen systemeigenen Typ deklarieren und dessen Lebensdauer im Konstruktor, Destruktor und Finalizer der verwalteten Klasse steuern. Weitere Informationen finden Sie unter [debugtoren und Finalizer](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

Diese Warnmeldung wird immer als Fehler ausgegeben. Verwenden Sie das [Warning](../../preprocessor/warning.md) -Pragma, um C4368 zu deaktivieren.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4368 generiert.

```cpp
// C4368.cpp
// compile with: /clr /c
struct N {};
ref struct O {};
ref struct R {
    R() : m_p( new N ) {}
    ~R() { delete m_p; }

   property N prop;   // C4368
   int i[10];   // C4368

   property O ^ prop2;   // OK
   N * m_p;   // OK
};
```
