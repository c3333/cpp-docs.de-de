---
title: Compilerwarnung (Stufe 1) C4251
ms.date: 04/21/2020
f1_keywords:
- C4251
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
ms.openlocfilehash: 9f261d3deb7f1cac8cd5c60b920e0be49bc8b7a6
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032329"
---
# <a name="compiler-warning-level-1-c4251"></a>Compilerwarnung (Stufe 1) C4251

> '*Typ*' : Klasse '*Typ1*' muss dll-interface haben, um von Clients der Klasse '*typ2*' verwendet zu werden

## <a name="remarks"></a>Bemerkungen

Um die Möglichkeit einer Datenbeschädigung beim Exportieren einer als [__declspec(dllexport)](../../cpp/dllexport-dllimport.md)deklarierten Klasse zu minimieren, stellen Sie sicher, dass:

- Auf alle statischen Daten wird über Funktionen zugegriffen, die aus der DLL exportiert werden.

- Keine inline Methoden Ihrer Klasse können statische Daten ändern.

- Keine inline Methoden Ihrer Klasse verwenden CRT-Funktionen oder andere Bibliotheksfunktionen, die statische Daten verwenden. Weitere Informationen finden Sie unter [Potenzielle Fehler beim Übergeben von CRT-Objekten über DLL-Grenzen](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)hinweg .

- Keine Methoden Ihrer Klasse (ob inline oder nicht) können Typen verwenden, bei denen die Instanziierung in EXE und DLL statische Datenunterschiede aufweisen.

Sie können Probleme beim Exportieren einer Klasse aus einer DLL vermeiden: Definieren Sie Ihre Klasse, um virtuelle Funktionen und Funktionen zum Instanziieren und Löschen von Objekten des Typs zu verwenden. Sie können dann einfach virtuelle Funktionen für den Typ aufrufen.

C4251 kann ignoriert werden, wenn Ihre Klasse von einem Typ in der C++-Standardbibliothek abgeleitet wird, Sie eine Debugversion `_Container_base`(**/MTd )** kompilieren und die Compilerfehlermeldung auf verweist.

## <a name="example"></a>Beispiel

In diesem Beispiel `VecWrapper` wird `std::vector`eine spezielle Klasse exportiert, die von abgeleitet wurde.

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllexport) VecWrapper : vector<Node *> {};   // C4251
```
