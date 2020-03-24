---
title: Compilerfehler C2989
ms.date: 11/04/2016
f1_keywords:
- C2989
helpviewer_keywords:
- C2989
ms.assetid: 936303d8-eb3b-4746-82ec-2f18020a6f64
ms.openlocfilehash: 585823c2114befa3e6d432e3cf8100fa14ed1a7d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176727"
---
# <a name="compiler-error-c2989"></a>Compilerfehler C2989

"Class": Klassentyp wurde bereits als nicht Klassen-Typ deklariert.

Die generische Klasse oder die generische Klasse definiert eine nicht-Vorlage oder eine nicht generische Klasse neu. Überprüfen Sie die Header Dateien auf Konflikte.

Im folgenden Beispiel wird C2989 generiert:

```cpp
// C2989.cpp
// compile with: /c
class C{};

template <class T>
class C{};  // C2989
class C2{};
```

C2989 kann auch auftreten, wenn Generika verwendet werden:

```cpp
// C2989b.cpp
// compile with: /clr /c
ref class GC1;

generic <typename T> ref class GC1;   // C2989
template <typename T> ref class GC2;

generic <typename T> ref class GC2;   // C2989
generic <typename T> ref class GCb;
template <typename T> ref class GC2;
generic <typename T> ref class GCc;
```
