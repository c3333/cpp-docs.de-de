---
title: const- und volatile-Zeiger
ms.date: 11/19/2019
helpviewer_keywords:
- volatile keyword [C++], and pointers
- pointers, and const
- pointers, and volatile
- const keyword [C++], volatile pointers
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
ms.openlocfilehash: a8fd25777d1169ba281fbee173c1c8f5673c8b56
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227568"
---
# <a name="const-and-volatile-pointers"></a>const- und volatile-Zeiger

Die Schlüsselwörter " [Konstanten](const-cpp.md) " und " [volatile](volatile-cpp.md) " ändern, wie Zeiger behandelt werden. Das **`const`** Schlüsselwort gibt an, dass der Zeiger nach der Initialisierung nicht geändert werden kann. der Zeiger ist anschließend vor Änderungen geschützt.

Das **`volatile`** Schlüsselwort gibt an, dass der Wert, der mit dem folgenden Namen verknüpft ist, durch andere Aktionen als in der Benutzeranwendung geändert werden kann. Daher ist das- **`volatile`** Schlüsselwort zum Deklarieren von Objekten im gemeinsam genutzten Speicher nützlich, auf die von mehreren Prozessen oder globalen Daten Bereichen zugegriffen werden kann, die für die Kommunikation mit Interruptroutinen verwendet werden.

Wenn ein Name als deklariert wird **`volatile`** , lädt der Compiler den Wert immer wieder aus dem Arbeitsspeicher, wenn er vom Programm aufgerufen wird. Dies reduziert die mögliche Optimierung erheblich. Wenn sich der Zustand eines Objekts unerwartet ändern kann, ist dies jedoch die einzige Möglichkeit, vorhersagbare Programmleistung sicherzustellen.

Um das Objekt, auf das der Zeiger verweist, als oder zu deklarieren **`const`** **`volatile`** , verwenden Sie eine Deklaration der folgenden Form:

```cpp
const char *cpch;
volatile char *vpch;
```

Um den Wert des Zeigers zu deklarieren, d. –. die tatsächliche Adresse, die im Zeiger gespeichert ist – als **`const`** oder **`volatile`** , verwenden Sie eine Deklaration der folgenden Form:

```cpp
char * const pchc;
char * volatile pchv;
```

Die Programmiersprache C++ verhindert Zuweisungen, die die Änderung eines Objekts oder Zeigers ermöglichen, die als deklariert wurden **`const`** . Diese Zuweisungen würden die Informationen entfernen, mit denen das Objekt oder der Zeiger deklariert wurde, und dadurch den Zweck der ursprünglichen Deklaration entfremden. Betrachten Sie hierzu die folgenden Deklarationen:

```cpp
const char cch = 'A';
char ch = 'B';
```

Bei den vorangehenden Deklarationen von zwei Objekten ( `cch` , vom Typ " **Konstanten char**" und `ch` vom Typ " **char")** sind die folgenden Deklarationen/Initialisierungen gültig:

```cpp
const char *pch1 = &cch;
const char *const pch4 = &cch;
const char *pch5 = &ch;
char *pch6 = &ch;
char *const pch7 = &ch;
const char *const pch8 = &ch;
```

Die folgende Deklaration/folgenden Initialisierungen sind fehlerhaft.

```cpp
char *pch2 = &cch;   // Error
char *const pch3 = &cch;   // Error
```

Die Deklaration von `pch2` deklariert einen Zeiger, mit dem ein konstantes Objekt möglicherweise geändert wird, und ist daher nicht zulässig. Die Deklaration von `pch3` gibt an, dass der Zeiger konstant ist, nicht das-Objekt. die Deklaration ist aus demselben Grund nicht zulässig, da die `pch2` Deklaration nicht zulässig ist.

Die folgenden acht Zuweisungen zeigen die Zuweisung durch einen Zeiger und die Änderung des Zeigerwerts für die vorhergehenden Deklarationen. Gehen Sie vorerst davon aus, dass die Initialisierung für `pch1` durch `pch8` korrekt war.

```cpp
*pch1 = 'A';  // Error: object declared const
pch1 = &ch;   // OK: pointer not declared const
*pch2 = 'A';  // OK: normal pointer
pch2 = &ch;   // OK: normal pointer
*pch3 = 'A';  // OK: object not declared const
pch3 = &ch;   // Error: pointer declared const
*pch4 = 'A';  // Error: object declared const
pch4 = &ch;   // Error: pointer declared const
```

Zeiger **`volatile`** , die als deklariert wurden, oder als eine Mischung aus **`const`** und **`volatile`** befolgen dieselben Regeln.

Zeiger auf **`const`** Objekte werden häufig wie folgt in Funktions Deklarationen verwendet:

```cpp
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );
```

Die vorherige Anweisung deklariert eine Funktion [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md), bei der zwei der drei Argumente vom Typ "Zeiger auf" sind **`char`** . Da die Argumente als Verweis und nicht als Wert übermittelt werden, kann die-Funktion sowohl als auch ändern, `strDestination` `strSource` Wenn `strSource` nicht als deklariert wurde **`const`** . Die Deklaration von `strSource` als **`const`** gewährleistet den `strSource` Aufrufer, der von der aufgerufenen Funktion nicht geändert werden kann.

> [!NOTE]
> Da es eine Standard Konvertierung von *tykame* <strong>\*</strong> in **`const`** *tykame* gibt <strong>\*</strong> , ist es zulässig, ein Argument vom Typ `char *` an [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)zu übergeben. Umgekehrt ist dies jedoch nicht der Fall. Es ist keine implizite Konvertierung vorhanden, um das **`const`** Attribut aus einem Objekt oder einem Zeiger zu entfernen.

Ein **`const`** Zeiger eines bestimmten Typs kann einem Zeiger desselben Typs zugewiesen werden. Ein Zeiger, der nicht **`const`** einem Zeiger zugewiesen werden kann, ist jedoch nicht möglich **`const`** . Der folgende Code zeigt korrekte und inkorrekte Zuweisungen:

```cpp
// const_pointer.cpp
int *const cpObject = 0;
int *pObject;

int main() {
pObject = cpObject;
cpObject = pObject;   // C3892
}
```

Das folgende Beispiel zeigt, wie ein Objekt als Konstante deklariert wird, wenn ein Zeiger auf einen Zeiger auf ein Objekt vorhanden ist.

```cpp
// const_pointer2.cpp
struct X {
   X(int i) : m_i(i) { }
   int m_i;
};

int main() {
   // correct
   const X cx(10);
   const X * pcx = &cx;
   const X ** ppcx = &pcx;

   // also correct
   X const cx2(20);
   X const * pcx2 = &cx2;
   X const ** ppcx2 = &pcx2;
}
```

## <a name="see-also"></a>Siehe auch

[Zeiger](pointers-cpp.md) 
 Unformatierte [Zeiger](raw-pointers.md)
