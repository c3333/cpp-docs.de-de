---
title: Compilerwarnung (Stufe 2) C4275
ms.date: 02/08/2019
f1_keywords:
- C4275
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
ms.openlocfilehash: ad12c1c27006a57c8339e9dad82e4d8e1a239a6e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161996"
---
# <a name="compiler-warning-level-2-c4275"></a>Compilerwarnung (Stufe 2) C4275

> die nicht-dll-Schnittstellen Klasse "*class_1*" wird als Basis für die DLL-Schnittstellen Klasse "*class_2*" verwendet.

Eine exportierte Klasse wurde von einer Klasse abgeleitet, die nicht exportiert wurde.

Stellen Sie Folgendes sicher, um die Möglichkeit einer Daten Beschädigung beim Exportieren einer Klasse mit [__declspec (dllexport)](../../cpp/dllexport-dllimport.md)zu minimieren:

- Der Zugriff auf alle statischen Daten erfolgt über Funktionen, die aus der dll exportiert werden.

- Keine Inline Methoden ihrer Klasse können statische Daten ändern.

- Keine Inline Methoden ihrer Klasse verwenden CRT-Funktionen oder andere Bibliotheksfunktionen, die statische Daten verwenden.

- Keine Inline Klassen Funktionen verwenden CRT-Funktionen oder andere Bibliotheksfunktionen, bei denen Sie auf statische Daten zugreifen.

- Keine Methoden ihrer Klasse (unabhängig vom Inlining) können Typen verwenden, bei denen die Instanziierung in der exe-und dll-Datei Unterschiede aufweisen.

Sie können den Export von Klassen vermeiden, indem Sie eine DLL definieren, die eine Klasse mit virtuellen Funktionen definiert, und Funktionen, die Sie zum Instanziieren und Löschen von Objekten des Typs aufzurufen können.  Sie können dann einfach virtuelle Funktionen für den Typ aufzurufen.

C4275 kann in Visual C++ ignoriert werden, wenn Sie von einem Typ in der C++ Standard Bibliothek ableiten, eine Debugversion kompilieren ( **/MTD**) und die Compilerfehlermeldung auf `_Container_base`verweist.

```cpp
// C4275.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275
```
