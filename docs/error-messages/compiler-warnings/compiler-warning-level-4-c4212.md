---
title: Compilerwarnung (Stufe 4) C4212
ms.date: 11/04/2016
f1_keywords:
- C4212
helpviewer_keywords:
- C4212
ms.assetid: df781ea1-182d-4f9f-9a31-55b6ce80c711
ms.openlocfilehash: d33e5c60bac657060ffef2a43686a5f737eb11cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161307"
---
# <a name="compiler-warning-level-4-c4212"></a>Compilerwarnung (Stufe 4) C4212

nicht dem Standard entsprechende Erweiterung: die Funktionsdeklaration hat Ellipsen verwendet.

Der Funktionsprototyp weist eine Variable Anzahl von Argumenten auf. Die Funktionsdefinition ist nicht.

Im folgenden Beispiel wird C4212 generiert:

```c
// C4212.c
// compile with: /W4 /Ze /c
void f(int , ...);
void f(int i, int j) {}
```
