---
title: Compilerwarnung C4355
ms.date: 11/04/2016
f1_keywords:
- C4355
helpviewer_keywords:
- C4355
ms.assetid: b819ecab-8a07-42d7-8fa4-1180d51626c0
ms.openlocfilehash: 2725db0e37f8e60f37ec1b534306f516fe10be33
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223342"
---
# <a name="compiler-warning-c4355"></a>Compilerwarnung C4355

"this": Wird in der Basisliste für den Memberinitialisierer verwendet

Der **`this`** Zeiger ist nur in nicht statischen Element Funktionen gültig. Sie kann nicht in der Initialisiererliste für eine Basisklasse verwendet werden.

Die Basisklassenkonstruktoren und Klassenmember-Konstruktoren werden vor dem **`this`** Konstruktor aufgerufen. Tatsächlich haben Sie einen Zeiger auf ein nicht konstruiertes Objekt an einen anderen Konstruktor übergeben. Wenn diese anderen Konstruktoren auf Member zugreifen oder Element Funktionen aufrufen, ist das Ergebnis nicht definiert. Sie sollten den-Zeiger erst verwenden, wenn **`this`** alle Konstruktionen abgeschlossen sind.

Diese Warnung ist standardmäßig deaktiviert. Weitere Informationen finden Sie unter [Standardmäßig deaktivierte Compilerwarnungen](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Im folgenden Beispiel wird C4355 generiert:

```cpp
// C4355.cpp
// compile with: /w14355 /c
#include <tchar.h>

class CDerived;
class CBase {
public:
   CBase(CDerived *derived): m_pDerived(derived) {};
   ~CBase();
   virtual void function() = 0;

   CDerived * m_pDerived;
};

class CDerived : public CBase {
public:
   CDerived() : CBase(this) {};   // C4355 "this" used in derived c'tor
   virtual void function() {};
};

CBase::~CBase() {
   m_pDerived -> function();
}

int main() {
   CDerived myDerived;
}
```
