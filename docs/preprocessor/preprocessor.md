---
title: Präprozessor
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
ms.openlocfilehash: 7188d7a6803c9eec109a59906cf0c016a460819d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337514"
---
# <a name="preprocessor"></a>Präprozessor

Der Präprozessor ist ein Textprozessor, der den Text einer Quelldatei im Rahmen der ersten Übersetzungsphase bearbeitet. Der Präprozessor analysiert den Quelltext nicht, aber er unterteilt ihn in Token, um Makroaufrufe zu finden. Obwohl der Compiler den Präprozessor normalerweise im ersten Durchlauf aufruft, kann der Präprozessor auch separat aufgerufen werden, um Text ohne Kompilierung zu verarbeiten.

Das Referenzmaterial zum Präprozessor enthält die folgenden Abschnitte:

- [Präprozessordirektiven](../preprocessor/preprocessor-directives.md)

- [Präprozessoroperatoren](../preprocessor/preprocessor-operators.md)

- [Vordefinierte Makros](../preprocessor/predefined-macros.md)

- [Pragmas](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

**Microsoft Specific**

Sie können eine Auflistung Ihres Quellcodes nach der Vorverarbeitung mithilfe der Compileroption [/E](../build/reference/e-preprocess-to-stdout.md) oder [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) abrufen. Beide Optionen rufen den Präprozessor auf und senden den resultierenden Text an das Standardausgabegerät, das in den meisten Fällen die Konsole ist. Der Unterschied zwischen den `/E` beiden `#line` Optionen `/EP` besteht darin, dass richtlinien enthalten sind, und diese Richtlinien werden entfernt.

**END Microsoft Spezifisch**

## <a name="special-terminology"></a><a name="_predir_special_terminology"></a>Spezielle Terminologie

In der Präprozessordokumentation bezieht sich der Begriff "Argument" auf die Entität, die an eine Funktion übergeben wird. In einigen Fällen wird sie durch "tatsächlich" oder "formal" geändert, was den im Funktionsaufruf angegebenen Argumentausdruck und die in der Funktionsdefinition angegebene Argumentdeklaration beschreibt.

Der Begriff "Variable" bezeichnet ein einfaches C-Datenobjekt. Der Begriff "Objekt" bezieht sich sowohl auf C++-Objekte als auch auf Variablen. es ist ein inklusiver Begriff.

## <a name="see-also"></a>Siehe auch

[C/C++-Präprozessorreferenz](../preprocessor/c-cpp-preprocessor-reference.md)\
[Phasen der Übersetzung](../preprocessor/phases-of-translation.md)
