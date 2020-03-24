---
title: Compilerfehler C2414
ms.date: 11/04/2016
f1_keywords:
- C2414
helpviewer_keywords:
- C2414
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
ms.openlocfilehash: fbe627a57e5defc499a4bc5d463e0bf33494acba
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205659"
---
# <a name="compiler-error-c2414"></a>Compilerfehler C2414

Ungültige Operandenanzahl

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Der Opcode unterstützt die Anzahl der verwendeten Operanden nicht. Lesen Sie in einem Assemblerreferenzhandbuch nach, wie viele Operanden zulässig sind.

1. Neuere Prozessoren unterstützen die Anweisung mit einer unterschiedlichen Anzahl von Operanden. Passen Sie die Option [/arch (minimale CPU-Architektur)](../../build/reference/arch-minimum-cpu-architecture.md) an, um den späteren Prozessor zu verwenden.
