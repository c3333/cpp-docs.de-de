---
title: Linkertoolfehler LNK2028
ms.date: 11/04/2016
f1_keywords:
- LNK2028
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
ms.openlocfilehash: ef9e3eae655a4fbee1c3da74f6036e5fb22434b1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194615"
---
# <a name="linker-tools-error-lnk2028"></a>Linkertoolfehler LNK2028

auf "*Exported_function*" (*decorated_name*) wird in der Funktion "*function_containing_function_call*" (*decorated_name*) verwiesen.

## <a name="remarks"></a>Bemerkungen

Wenn Sie versuchen, eine native Funktion in ein reines Image zu importieren, denken Sie daran, dass sich die impliziten Aufruf Konventionen zwischen nativen und reinen Kompilierungen unterscheiden.

Die **/clr: pure** -Compileroption ist in Visual Studio 2015 veraltet und wird in Visual Studio 2017 nicht unterstützt.

## <a name="example"></a>Beispiel

In diesem Codebeispiel wird eine Komponente mit einer exportierten, systemeigenen Funktion generiert, deren Aufruf Konvention implizit [__cdecl](../../cpp/cdecl.md)ist.

```cpp
// LNK2028.cpp
// compile with: /LD
__declspec(dllexport) int func() {
   return 3;
}
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein reiner Client erstellt, der die native Funktion nutzt. Die Aufruf Konvention unter **/clr: pure** ist jedoch [__clrcall](../../cpp/clrcall.md). Im folgenden Beispiel wird Linkertoolfehler LNK2028 generiert.

```cpp
// LNK2028_b.cpp
// compile with: /clr:pure lnk2028.lib
// LNK2028 expected
int func();

int main() {
   return func();
}
```
