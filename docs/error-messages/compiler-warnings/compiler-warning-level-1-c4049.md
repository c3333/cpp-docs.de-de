---
title: Compilerwarnung (Stufe 1) C4049
ms.date: 11/04/2016
f1_keywords:
- C4049
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
ms.openlocfilehash: 214ccae5d9835bc4a3b66bbbe1cd5ded4bc651cb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164143"
---
# <a name="compiler-warning-level-1-c4049"></a>Compilerwarnung (Stufe 1) C4049

Compilerlimit: Ausgabe der Zeilennummer wird beendet.

Die Datei enthält mehr als 16.777.215 (2<sup>24</sup>-1) Quellzeilen. Der Compiler beendet die Nummerierung bei 16.777.215.

Für Code nach Zeile 16.777.215:

- Das Bild enthält keine Debuginformationen für Zeilennummern.

- Einige Diagnosen werden möglicherweise mit falschen Zeilennummern gemeldet.

- asm-Auflistungen (/FAS) weisen möglicherweise falsche Zeilennummern auf.
