---
title: Compilerwarnung (Stufe 1) C4251
ms.date: 11/04/2016
f1_keywords:
- C4251
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
ms.openlocfilehash: 8a723b7ce7fc79fb6be9c9dd2b500631098622b0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163218"
---
# <a name="compiler-warning-level-1-c4251"></a>Compilerwarnung (Stufe 1) C4251

"Bezeichner": die Klasse "Type" muss über eine DLL-Schnittstelle verfügen, die von Clients der Klasse "Typ2" verwendet werden darf.

Stellen Sie Folgendes sicher, um die Möglichkeit einer Daten Beschädigung beim Exportieren einer Klasse mit [__declspec (dllexport)](../../cpp/dllexport-dllimport.md)zu minimieren:

- Alle statischen Daten sind über Funktionen zugänglich, die aus der dll exportiert werden.

- Keine Inline Methoden ihrer Klasse können statische Daten ändern.

- Keine Inline Methoden ihrer Klasse verwenden CRT-Funktionen, oder andere Bibliotheksfunktionen verwenden statische Daten (Weitere Informationen finden Sie unter [potenzielle Fehler bei der Übergabe von CRT-Objekten über dll-Grenzen](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md) hinweg).

- Keine Methoden ihrer Klasse (unabhängig vom Inlining) können Typen verwenden, bei denen die Instanziierung in der exe-und dll-Datei Unterschiede aufweisen.

Sie können den Export von Klassen vermeiden, indem Sie eine DLL definieren, die eine Klasse mit virtuellen Funktionen definiert, und Funktionen, die Sie zum Instanziieren und Löschen von Objekten des Typs aufzurufen können.  Sie können dann einfach virtuelle Funktionen für den Typ aufzurufen.

C4251 kann ignoriert werden, wenn Sie von einem Typ in der C++ Standard Bibliothek ableiten, eine Debugversion ( **/MTD**) kompilieren und die Compilerfehlermeldung auf _Container_base verweist.

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251
```
