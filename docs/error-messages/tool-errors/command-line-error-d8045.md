---
title: Befehlszeilenfehler D8045
ms.date: 11/04/2016
f1_keywords:
- D8045
helpviewer_keywords:
- D8045
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
ms.openlocfilehash: 05a2d3851e58062e1e326781a223e2f4b0346620
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196845"
---
# <a name="command-line-error-d8045"></a>Befehlszeilenfehler D8045

die C-Datei ' file ' kann nicht mit der Option/CLR kompiliert werden.

An C++ eine Kompilierung, die **/CLR**verwendet, können nur Quell Code Dateien übermittelt werden.  Verwenden Sie **/tp** , um eine c-Datei als cpp-Datei zu kompilieren. Weitere Informationen finden Sie unter [/TC,/TP,/TC,/TP (Quell Dateityp angeben)](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) .

Weitere Informationen finden Sie unter [/clr (Common Language Runtime-Kompilierung)](../../build/reference/clr-common-language-runtime-compilation.md).

D8045 kann auch auftreten, wenn Sie eine ATL-Anwendung mithilfe C++von Visual kompilieren. Weitere Informationen finden [Sie unter Gewusst wie: Migrieren zu/CLR](../../dotnet/how-to-migrate-to-clr.md) .
