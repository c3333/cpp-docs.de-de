---
title: Basierte Zeiger (C++)
ms.date: 10/09/2018
f1_keywords:
- __based
- _based
- __based_cpp
helpviewer_keywords:
- __based keyword [C++]
- based pointers
- pointers, based
ms.assetid: 1e5f2e96-c52e-4738-8e14-87278681205e
ms.openlocfilehash: 24c3a7f85c4ea05c38f3ab1d3f637ea0ab24d4c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363748"
---
# <a name="based-pointers-c"></a>Basierte Zeiger (C++)

Mit **dem Schlüsselwort __based** können Sie Zeiger basierend auf Zeigern (Zeiger, die Offsets von vorhandenen Zeigern sind) deklarieren. Das **__based** Schlüsselwort ist Microsoft-spezifisch.

## <a name="syntax"></a>Syntax

```
type __based( base ) declarator
```

## <a name="remarks"></a>Bemerkungen

Zeiger, die auf Zeigeradressen basieren, sind die einzige Form des **schlüsselworts __based,** das in 32-Bit- oder 64-Bit-Kompilierungen gültig ist. Für den 32-Bit-C/C++Compiler von Microsoft ist ein basierter Zeiger ein 32-Bit-Offset von einer 32-Bit-Zeigerbasis. Eine ähnliche Einschränkung besteht für 64-Bit-Umgebungen, in denen ein basierter Zeiger ein 64-Bit-Offset von der 64-Bit-Basis ist.

Eine Verwendung von Zeigern, die auf Zeigern basieren, ist für dauerhafte Bezeichner, die Zeiger enthalten. Eine verknüpfte Liste, die aus Zeigern auf Grundlage eines Zeigers besteht, kann auf Datenträger gespeichert werden, dann an eine andere Stelle im Arbeitsspeicher neu geladen werden, wobei die Zeiger weiterhin gültig bleiben. Beispiel:

```cpp
// based_pointers1.cpp
// compile with: /c
void *vpBuffer;
struct llist_t {
   void __based( vpBuffer ) *vpData;
   struct llist_t __based( vpBuffer ) *llNext;
};
```

Dem Zeiger `vpBuffer` wird die Adresse des später im Programm zugewiesenen Arbeitsspeichers zugeteilt. Die verknüpfte Liste wird relativ zum Wert von `vpBuffer` verschoben.

> [!NOTE]
> Persistente Bezeichner, die Zeiger enthalten, können auch mithilfe von [Speicherzuordnungsdateien](/windows/win32/Memory/file-mapping)erreicht werden.

Beim Dereferenzieren eines basierten Zeigers muss die Basis explizit angegeben werden oder implizit durch die Deklaration bekannt sein.

Aus Kompatibilität mit früheren Versionen ist **_based** ein Synonym für **__based,** es sei denn, die Compileroption [ \(/Za Disable language extensions)](../build/reference/za-ze-disable-language-extensions.md) wird angegeben.

## <a name="example"></a>Beispiel

Im folgenden Code wird gezeigt, wie ein Basiszeiger verändert wird, indem seine Basis geändert wird.

```cpp
// based_pointers2.cpp
// compile with: /EHsc
#include <iostream>

int a1[] = { 1,2,3 };
int a2[] = { 10,11,12 };
int *pBased;

typedef int __based(pBased) * pBasedPtr;

using namespace std;
int main() {
   pBased = &a1[0];
   pBasedPtr pb = 0;

   cout << *pb << endl;
   cout << *(pb+1) << endl;

   pBased = &a2[0];

   cout << *pb << endl;
   cout << *(pb+1) << endl;
}
```

```Output
1
2
10
11
```

## <a name="see-also"></a>Siehe auch

[Keywords](../cpp/keywords-cpp.md)<br/>
[alloc_text](../preprocessor/alloc-text.md)
