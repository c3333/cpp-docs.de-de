---
title: Compilerwarnung (Stufe 1) C4010
ms.date: 11/04/2016
f1_keywords:
- C4010
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
ms.openlocfilehash: 6045d49ee34f837ad9f22bac5b2b43b75a998f7c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164689"
---
# <a name="compiler-warning-level-1-c4010"></a>Compilerwarnung (Stufe 1) C4010

einzeiligen Kommentar enthält Zeilen Fortsetzungs Zeichen

Ein einzeiligen Kommentar, der durch//eingeführt wird, enthält einen umgekehrten Schrägstrich (\\), der als Zeilen Fortsetzungs Zeichen fungiert. Der Compiler betrachtet die nächste Zeile als Fortsetzung und behandelt Sie als Kommentar.

Einige von der Syntax gesteuerte Editoren geben nicht die Zeile an, die dem Fortsetzungs Zeichen als Kommentar folgt. Ignorieren Sie Syntax Farben für alle Zeilen, die diese Warnung auslösen.

Im folgenden Beispiel wird C4010 generiert:

```cpp
// C4010.cpp
// compile with: /WX
int main() {
   // the next line is also a comment because of the backslash \
   int a = 3; // C4010
   a++;
}
```
