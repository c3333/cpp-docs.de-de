---
title: STACKSIZE
ms.date: 11/04/2016
f1_keywords:
- STACKSIZE
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
ms.openlocfilehash: 2d27b4fd596098f4abc5bb0d804d87bd08f70a60
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318354"
---
# <a name="stacksize"></a>STACKSIZE

Legt die Stapelgröße in Bytes fest.

```
STACKSIZE reserve[,commit]
```

## <a name="remarks"></a>Hinweise

Alternativ können Sie den Stapel festgelegt ist, mit der [Stapelreservierungen](stack-stack-allocations.md) (/ STACK) Option. Finden Sie in der Dokumentation auf diese Option, Weitere Informationen zu den *reservieren* und `commit` Argumente.

Diese Option wirkt sich nicht für DLLs aus.

## <a name="see-also"></a>Siehe auch

[Regeln für Moduldefinitionsanweisungen](rules-for-module-definition-statements.md)
