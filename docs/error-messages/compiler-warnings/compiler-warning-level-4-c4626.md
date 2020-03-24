---
title: Compilerwarnung (Stufe 4) C4626
ms.date: 11/04/2016
f1_keywords:
- C4626
helpviewer_keywords:
- C4626
ms.assetid: 7f822ff4-a4a3-4f17-b45b-e8b7b4659a14
ms.openlocfilehash: 665a21d9f0221b2cf3db111142576669a3b5d728
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198263"
---
# <a name="compiler-warning-level-4-c4626"></a>Compilerwarnung (Stufe 4) C4626

„Abgeleitete Klasse“: Der Zuweisungsoperator wurde implizit als gelöscht definiert, da auf einen Basisklassen-Zuweisungsoperator nicht zugegriffen werden kann oder dieser gelöscht wurde.

Ein Zuweisungsoperator wurde gelöscht, oder es kann nicht auf diesen in einer Basisklasse zugegriffen werden. Daher wurde er nicht für eine abgeleitete Klasse generiert. Bei jedem Versuch, Objekte dieses Typs zuzuweisen, wird ein Compilerfehler generiert.

Diese Warnung ist standardmäßig deaktiviert. Weitere Informationen finden Sie unter [Standardmäßig deaktivierte Compilerwarnungen](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Im folgenden Beispiel wird C4626 generiert und gezeigt, wie Sie diesen Fehler beheben:

```
// C4626
// compile with: /W4
#pragma warning(default : 4626)
class B
{
// public:
   B& operator = (const B&)
   {
      return *this;
   }
};

class D : public B
{

}; // C4626 - to fix, make B's copy constructor public

int main()
{
   D m;
   D n;
   // m = n;   // this line will cause an error
}
```
