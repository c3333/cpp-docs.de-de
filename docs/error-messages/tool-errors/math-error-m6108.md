---
title: Mathematischer Fehler M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: 68e6ae823613d87eb01c443b564b46746259cd7b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173724"
---
# <a name="math-error-m6108"></a>Mathematischer Fehler M6108

Quadratwurzel

Der Operand in einem Quadratwurzel Vorgang war negativ.

Das Programm endet mit dem Exitcode 136.

> [!NOTE]
>  Dieser Fehler wird nicht von der `sqrt`-Funktion in der C-Lauf Zeit Bibliothek und der systeminternen FORTRAN-Funktion **sqrt** generiert. Die C-`sqrt` Funktion überprüft das-Argument, bevor der Vorgang durchgeführt wird, und gibt einen Fehlerwert zurück, wenn der Operand negativ ist. Die Fortran **sqrt** -Funktion generiert den Domänen Fehler [M6201](../../error-messages/tool-errors/math-error-m6201.md) anstelle dieses Fehlers.
