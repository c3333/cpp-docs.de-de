---
title: Compilerfehler C3771
ms.date: 11/04/2016
f1_keywords:
- C3771
helpviewer_keywords:
- C3771
ms.assetid: 68c23b25-7f21-4eaa-8f7e-38fda1130a69
ms.openlocfilehash: 6c29ad6007d33c43ae1e4758ae05caa9109053e3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165729"
---
# <a name="compiler-error-c3771"></a>Compilerfehler C3771

"Bezeichner": Die Friend-Deklaration kann im nächsten Namespacebereich nicht gefunden werden.

Die Klassenvorlagendeklaration für den angegebenen *Bezeichner* der Vorlage wurde im aktuellen Namespace nicht gefunden.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Stellen Sie sicher, dass die Klassenvorlagendeklaration für den Vorlagenbezeichner im aktuellen Namespace definiert ist oder dass der Vorlagenbezeichner ein voll qualifizierter Name ist.

## <a name="example"></a>Beispiel

Im folgenden Codebeispiel werden eine Klassenvorlage und Funktion im Namespace `NA`deklariert, allerdings wird versucht, eine Friend-Funktionsvorlage im Namespace `NB`zu deklarieren.

```cpp
// C3771.cpp
// compile with: /c

namespace NA {
template<class T> class A {
    void aFunction(T t) {};
    };
}
// using namespace NA;
namespace NB {
    class X {
        template<class T> friend void A<T>::aFunction(T); // C3771
// try the following line instead
//      template<class T> friend void NA::A<T>::aFunction(T);
// or try "using namespace NA;" instead.
    };
}
```

## <a name="see-also"></a>Weitere Informationen

[Vorlagen](../../cpp/templates-cpp.md)
