---
title: Compilerfehler C2555
ms.date: 11/04/2016
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: ebf3e4a3aff48311edd5fb95b01a7b2d23990231
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202423"
---
# <a name="compiler-error-c2555"></a>Compilerfehler C2555

' Class1:: Funktion1 ': der Rückgabetyp der virtuellen Funktion wird unterschiedlich und ist nicht kovariant von ' Klasse2:: Funktion2 '.

Eine virtuelle Funktion und eine abgeleitete Überschreibungs Funktion verfügen über identische Parameterlisten, aber unterschiedliche Rückgabe Typen. Eine über schreibende Funktion in einer abgeleiteten Klasse kann sich nur durch ihren Rückgabetyp von einer virtuellen Funktion in einer Basisklasse unterscheiden.

Umwandeln Sie den Rückgabewert, nachdem die virtuelle Funktion aufgerufen wurde, um diesen Fehler zu beheben.

Dieser Fehler wird möglicherweise auch angezeigt, wenn Sie mit/CLR. kompilieren.   Beispielsweise entspricht die Visualisierung C++ der folgenden C# Deklaration:

```
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

stimmt

```
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

Im folgenden Beispiel wird C2555 generiert:

```cpp
// C2555.cpp
// compile with: /c
struct X {
   virtual void func();
};
struct Y : X {
   char func();  // C2555
   void func2();   // OK
};
```
