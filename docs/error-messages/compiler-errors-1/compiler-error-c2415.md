---
title: Compilerfehler C2415
ms.date: 11/04/2016
f1_keywords:
- C2415
helpviewer_keywords:
- C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
ms.openlocfilehash: a0cdd528eca8ea267c62e6d44752d29ae16830c4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205620"
---
# <a name="compiler-error-c2415"></a>Compilerfehler C2415

Ungültiger Operandentyp

Der Opcode verwendet keine Operanden dieses Typs.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Der Opcode unterstützt die Anzahl der verwendeten Operanden nicht. Lesen Sie in einem Assemblerreferenzhandbuch nach, wie viele Operanden zulässig sind.

1. Neuere Prozessoren unterstützen die Anweisung durch zusätzliche Typen. Passen Sie die Option [/arch (minimale CPU-Architektur)](../../build/reference/arch-minimum-cpu-architecture.md) an, um den späteren Prozessor zu verwenden.
