---
title: Compilerwarnung (Stufe 1) C4165
ms.date: 11/04/2016
f1_keywords:
- C4165
helpviewer_keywords:
- C4165
ms.assetid: f5bed515-2290-4f88-8dab-b45d95fe26ef
ms.openlocfilehash: bb036f7672a074e859d3e19083e256bd80c93578
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176097"
---
# <a name="compiler-warning-level-1-c4165"></a>Compilerwarnung (Stufe 1) C4165

"HRESULT" wird in "bool" konvertiert. sind Sie sicher, was Sie möchten?

Wenn ein HRESULT in einer [if](../../cpp/if-else-statement-cpp.md) -Anweisung verwendet wird, wird das HRESULT in einen [booleschen](../../cpp/bool-cpp.md) Typ konvertiert, es sei denn, Sie testen explizit die Variable als HRESULT. Diese Warnung ist standardmäßig deaktiviert.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4165 generiert.

```cpp
// C4165.cpp
// compile with: /W1
#include <windows.h>
#pragma warning(1:4165)

extern HRESULT hr;
int main() {
   if (hr) {
   // try either of the following ...
   // if (FAILED(hr)) { // C4165 expected
   // if (hr != S_OK) {
   }
}
```
