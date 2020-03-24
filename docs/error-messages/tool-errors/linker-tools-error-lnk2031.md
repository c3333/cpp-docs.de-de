---
title: Linkertoolfehler LNK2031
ms.date: 11/04/2016
f1_keywords:
- LNK2031
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
ms.openlocfilehash: 096ccb7ff443d24e0d53e73a5950faa1e85aeae6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194563"
---
# <a name="linker-tools-error-lnk2031"></a>Linkertoolfehler LNK2031

> p/Aufruf für "*Function_declaration*" *decorated_name*kann nicht generiert werden. die Aufruf Konvention fehlt in den Metadaten.

## <a name="remarks"></a>Bemerkungen

Wenn Sie versuchen, eine native Funktion in ein reines Image zu importieren, denken Sie daran, dass sich die impliziten Aufruf Konventionen zwischen nativen und reinen Kompilierungen unterscheiden. Weitere Informationen zu reinen Bildern finden Sie unter [reiner und überprüfbarerC++Code (/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Die **/clr: pure** -Compileroption ist in Visual Studio 2015 veraltet und wird in Visual Studio 2017 nicht unterstützt.

## <a name="example"></a>Beispiel

In diesem Codebeispiel wird eine Komponente mit einer exportierten, systemeigenen Funktion generiert, deren Aufruf Konvention implizit [__cdecl](../../cpp/cdecl.md)ist.

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein reiner Client erstellt, der die native Funktion nutzt. Die Aufruf Konvention unter **/clr: pure** ist jedoch [__clrcall](../../cpp/clrcall.md). Im folgenden Beispiel wird Linkertoolfehler LNK2031 generiert.

```cpp
// LNK2031_b.cpp
// compile with: /clr:pure LNK2031.lib
// LNK2031 expected
extern "C" int func();

int main() {
   return func();
}
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie die native Funktion aus einem reinen Image verwendet wird. Beachten Sie den expliziten **__cdecl** Aufruf Konvention-Spezifizierer.

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```
