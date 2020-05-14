---
title: C-Operatoren (additiv)
ms.date: 10/18/2018
helpviewer_keywords:
- usual arithmetic conversions
- operators [C], addition
- + operator, additive operators
- additive operators
- arithmetic operators [C++], additive operators
ms.assetid: bb8ac205-b061-41fc-8dd4-dab87c8b900c
ms.openlocfilehash: 29bea87e56aa90a8deab7ad7280b3fbdfb45c82b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326900"
---
# <a name="c-additive-operators"></a>C-Operatoren (additiv)

Die additiven Operatoren führen Additionen ( **+** ) und Subtraktionen ( **-** ) aus.

## <a name="syntax"></a>Syntax

*additive-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additiver-Ausdruck* **+** *multiplikativer-Ausdruck*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additiver-Ausdruck* **-** *multiplikativer-Ausdruck*

> [!NOTE]
> Obwohl die Syntax für *additive-expression* auch *multiplicative-expression* enthält, heißt das nicht, dass Ausdrücke erforderlich sind, die Multiplikation verwenden. In der [Zusammenfassung der C-Sprachsyntax](../c-language/c-language-syntax-summary.md) finden Sie weitere Informationen über die Syntax für *multiplicative-expression*, *cast-expression* und *unary-expression*.

Die Operanden können Ganzzahl- oder Gleitkommawerte sein. Einige Additionsvorgänge können auch auf Zeigerwerten ausgeführt werden, wie in der Erläuterung für die einzelnen Operatoren dargelegt wird.

Additive Operatoren führen die üblichen arithmetischen Konvertierungen in Operanden vom Typ "integral" oder "floating" aus. Der Ergebnistyp ist der Typ der Operanden nach der Konvertierung. Da Konvertierungen, die von den Addition-Operatoren ausgeführt werden, keine Überlauf- oder Unterlaufbedingungen vorsehen, gehen Informationen möglicherweise verloren, wenn das Ergebnis eines Additionsvorgangs nach der Konvertierung nicht im Typ der Operanden dargestellt werden kann.

## <a name="see-also"></a>Siehe auch

[Additive Operatoren: + und -](../cpp/additive-operators-plus-and.md)
