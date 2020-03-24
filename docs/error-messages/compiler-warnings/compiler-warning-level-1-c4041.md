---
title: Compilerwarnung (Stufe 1) C4041
ms.date: 11/04/2016
f1_keywords:
- C4041
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
ms.openlocfilehash: 14ea6d9cae3b490107b656153bb68815026971e1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164234"
---
# <a name="compiler-warning-level-1-c4041"></a>Compilerwarnung (Stufe 1) C4041

Compilerlimit : Browserausgabe wird abgebrochen

Die Browserinformationen haben das Compilerlimit überschritten.

Diese Warnung kann durch die Kompilierung mit [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (Browserinformationen einschließlich lokaler Variablen) verursacht werden.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>So beheben Sie den Fehler (unterschiedliche Lösungsmöglichkeiten)

1. Kompilieren Sie mit /Fr (Browserinformationen ohne lokale Variablen).

1. Deaktivieren Sie die Browserausgabe (Kompilieren ohne/fr oder/FR).
