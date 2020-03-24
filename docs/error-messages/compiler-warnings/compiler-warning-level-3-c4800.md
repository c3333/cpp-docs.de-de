---
title: Compilerwarnung (Stufe 4) C4800
ms.date: 03/14/2019
f1_keywords:
- C4800
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
ms.openlocfilehash: 828b38aeb184741af284f2d7722017b24f6255a3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198587"
---
# <a name="compiler-warning-level-4-c4800"></a>Compilerwarnung (Stufe 4) C4800

::: moniker range=">= vs-2019"
Visual Studio 2019 und höher:
> Implizite Konvertierung von '*Type*' in bool. Möglicher Informationsverlust
::: moniker-end

C4800 ist eine Warnung der Stufe 3 in Visual Studio 2015 und früher:
> '*Type*': Wert für bool ' true ' oder ' false ' erzwingen (Leistungs Warnung)

Diese Warnung wird generiert, wenn ein Wert implizit in den Typ `bool`konvertiert wird. Diese Meldung wird in der Regel durch Zuweisen von `int` Variablen zu `bool` Variablen verursacht, wobei die `int` Variable nur die Werte **true** und **false**enthält und als Typ `bool`neu deklariert werden kann. Wenn Sie den Ausdruck nicht so umschreiben können, dass der Typ `bool`verwendet wird, können Sie dem Ausdruck "`!=0`" hinzufügen, wodurch der Ausdruckstyp `bool`wird. Wenn Sie den Ausdruck in den Typ umwandeln `bool` wird die Warnung nicht deaktiviert, was beabsichtigt ist.

::: moniker range=">= vs-2017"
Diese Warnung wird nicht in Visual Studio 2017 ausgegeben.
::: moniker-end

::: moniker range=">= vs-2019"
Diese Warnung ist standardmäßig deaktiviert, beginnend mit Visual Studio 2019. Verwenden Sie __/w__*n*__4800__ , um C4800 als Warnung der Ebene *n* zu aktivieren, oder [/Wall](../../build/reference/compiler-option-warning-level.md) , um alle Warnungen zu aktivieren, die standardmäßig deaktiviert sind. Weitere Informationen finden Sie unter [standardmäßig](../../preprocessor/compiler-warnings-that-are-off-by-default.md)deaktivierte Compilerwarnungen.
::: moniker-end

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4800 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C4800.cpp
// compile with: /W4 /w44800
int main() {
   int i = 0;

   // To fix, instead try:
   // bool i = 0;

   bool j = i;   // C4800
   j++;
}
```
