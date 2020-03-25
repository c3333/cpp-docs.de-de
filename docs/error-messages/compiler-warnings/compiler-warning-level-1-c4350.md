---
title: Compilerwarnung (Stufe 1) C4350
ms.date: 11/04/2016
f1_keywords:
- C4350
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
ms.openlocfilehash: 890ecd4fcec1212fa04a58b0eaab8c2eb4206763
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187218"
---
# <a name="compiler-warning-level-1-c4350"></a>Compilerwarnung (Stufe 1) C4350

Verhaltensänderung: 'Member1' wird anstelle von 'Member2' aufgerufen

Ein rvalue-Wert kann nicht an einen nicht konstanten Verweis gebunden werden. In Visual C++ Studio-Versionen vor Visual Studio 2003 war es möglich, einen Rvalue-Wert in einer direkten Initialisierung an einen nicht konstanten Verweis zu binden. Dieser Code gibt nun eine Warnung aus.

Aus Gründen der Abwärtskompatibilität ist es weiterhin möglich, Rvalues an nicht konstante Verweise zu binden, aber Standard Konvertierungen werden nach Möglichkeit bevorzugt.

Diese Warnung stellt eine Änderung des Verhaltens vom Visual C++ .NET 2002-Compiler dar. Wenn diese Option aktiviert ist, kann diese Warnung möglicherweise für korrekten Code angegeben werden. Dies kann z. b. bei Verwendung der **Std:: auto_ptr** -Klassen Vorlage angegeben werden.

Wenn Sie diese Warnung erhalten, überprüfen Sie den Code, um festzustellen, ob er von der Bindung von Rvalues an nicht konstante Verweise abhängt. Das Hinzufügen eines Konstanten zum Verweis oder das Bereitstellen einer zusätzlichen konstanten Verweis Überladung kann das Problem lösen.

Diese Warnung ist standardmäßig deaktiviert. Weitere Informationen finden Sie unter [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

Im folgenden Beispiel wird C4350 generiert:

```cpp
// C4350.cpp
// compile with: /W1
#pragma warning (default : 4350)
class A {};

class B
{
public:
   B(B&){}
   // try the following instead:
   // B(const B&){}

   B(A){}
   operator A(){ return A();}
};

B source() { return A(); }

int main()
{
   B ap(source());   // C4350
}
```
