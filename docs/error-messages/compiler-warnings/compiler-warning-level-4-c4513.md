---
title: Compilerwarnung (Stufe 4) C4513
ms.date: 11/04/2016
f1_keywords:
- C4513
helpviewer_keywords:
- C4513
ms.assetid: 6877334a-f30a-4184-9483-dac3348737a4
ms.openlocfilehash: f5f25465beb04c6f91d290d4c119d07d75dd8f54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185216"
---
# <a name="compiler-warning-level-4-c4513"></a>Compilerwarnung (Stufe 4) C4513

"Klasse": Dekonstruktor konnte nicht generiert werden.

Der Compiler kann keinen standarddekonstruktor für die angegebene Klasse generieren. Es wurde kein Dekonstruktor erstellt. Der Dekonstruktor befindet sich in einer Basisklasse, auf die die abgeleitete Klasse nicht zugreifen kann. Wenn die Basisklasse über einen privaten Dekonstruktor verfügt, machen Sie sie öffentlich oder geschützt.
