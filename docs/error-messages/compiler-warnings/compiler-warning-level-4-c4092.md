---
title: Compilerwarnung (Stufe 4) C4092
ms.date: 11/04/2016
f1_keywords:
- C4092
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
ms.openlocfilehash: 675e6ccbc516734a405620aa74eaa04ff2f75087
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219988"
---
# <a name="compiler-warning-level-4-c4092"></a>Compilerwarnung (Stufe 4) C4092

> sizeof gibt "unsigned long" zurück

Der Operand des **`sizeof`** Operators war sehr groß, daher wurde **`sizeof`** eine zurückgegeben **`unsigned long`** . Diese Warnung tritt unter den Microsoft-Erweiterungen ( [`/Ze`](../../build/reference/za-ze-disable-language-extensions.md) ) auf. Unter ANSI Compatibility ( **`/Za`** ) wird das Ergebnis stattdessen abgeschnitten.
