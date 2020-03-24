---
title: Compilerfehler C3808
ms.date: 11/04/2016
f1_keywords:
- C3808
helpviewer_keywords:
- C3808
ms.assetid: 2ee8ac97-3ea4-417a-8710-be73a7f98cf4
ms.openlocfilehash: e854764dc3f8d3ede79965302b62055b91df0a4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165625"
---
# <a name="compiler-error-c3808"></a>Compilerfehler C3808

> "*Typ*": eine Klasse mit dem ComImport-Attribut kann Member "*Member*" nicht definieren, es sind nur abstrakte Funktionen oder DllImport-Funktionen zulässig.

## <a name="remarks"></a>Bemerkungen

Ein Typ, der von <xref:System.Runtime.InteropServices.ComImportAttribute> abgeleitet ist, kann *Member*nicht definieren.

Die Compileroptionen **/clr: pure** und **/clr: Safe** sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3808 generiert.

```cpp
// C3808.cpp
// compile with: /c /clr:pure user32.lib
using namespace System::Runtime::InteropServices;

[System::Runtime::InteropServices::ComImportAttribute()]
ref struct S1 {
   int f() {}   // C3808
   virtual int g() abstract;   // OK

   [DllImport("msvcrt.dll")]
   int printf(System::String ^, int i);   // OK
};
```
