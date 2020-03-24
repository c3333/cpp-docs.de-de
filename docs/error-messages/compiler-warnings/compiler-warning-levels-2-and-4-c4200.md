---
title: Compilerwarnung (Stufen 2 und 4) C4200
ms.date: 11/04/2016
f1_keywords:
- C4200
helpviewer_keywords:
- C4200
ms.assetid: e44d6073-937f-42b7-acc1-65e802b475c6
ms.openlocfilehash: 4b0750fe50e18214e0841eff6b3459438e9a6aec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197950"
---
# <a name="compiler-warning-levels-2-and-4-c4200"></a>Compilerwarnung (Stufen 2 und 4) C4200

nicht dem Standard entsprechende Erweiterung: Null-Array in Struktur/Union

Gibt an, dass eine Struktur oder Union ein Array mit Größe Null enthält.

Die Deklaration eines Arrays der Größe 0 (null) ist eine Microsoft-Erweiterung. Dadurch wird eine Warnung der Stufe 2 bei der Kompilierung einer C++-Datei und eine Warnung der Stufe 4 kompiliert, wenn C-Datei kompiliert wird. C++die Kompilierung gibt auch folgende Warnung aus: "der Kopier-oder Kopier Zuweisungs Operator kann nicht generiert werden, wenn UDT ein Array der Größen NULL enthält". In diesem Beispiel wird die Warnung C4200 generiert:

```cpp
// C4200.cpp
// compile by using: cl /W4 c4200.cpp
struct A {
    int a[0];  // C4200
};
int main() {
}
```

Diese nicht standardisierte Erweiterung wird häufig zum Verknüpfen von Code mit externen Datenstrukturen verwendet, die eine variable Länge haben. Wenn dieses Szenario für Ihren Code gilt, können Sie die Warnung deaktivieren:

## <a name="example"></a>Beispiel

```cpp
// C4200b.cpp
// compile by using: cl /W4 c4200a.cpp
#pragma warning(disable : 4200)
struct A {
    int a[0];
};
int main() {
}
```
