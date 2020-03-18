---
title: IF (MASM)
ms.date: 12/17/2019
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
ms.openlocfilehash: 6e63f5c8075b3c94370ad8863d224c097cf0ecdf
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440750"
---
# <a name="if"></a>IF

Erteilt eine Assembly von *if-Anweisungen* , wenn *expression1* den Wert true hat (ungleich 0 (null)) oder *ElseIf-Anweisungen* , wenn *expression1* false (0) und *expression2* true ist.

## <a name="syntax"></a>Syntax

> **Wenn** *expression1*\
> *if-Anweisungen*\
> ⟦**ElseIf** *expression2*\
> *ElseIf-Anweisungen*⟧ \
> ⟦**Else** -\
> *else-Anweisungen*⟧ \
> **EndIf**

## <a name="remarks"></a>Bemerkungen

Die folgenden Direktiven können für [ElseIf](elseif-masm.md)ersetzt werden: **elseifb**, **ELSEIFDEF**, **elseifdif**, **elseifdifi**, **elseife**, **elseifdn**, **elseimedni**, **elseifnb**und **ELSEIFNDEF**. Optional: assembliert *else--Anweisungen* , wenn der vorherige Ausdruck false ist. Beachten Sie, dass die Ausdrücke zur assemblyzeit ausgewertet werden.

## <a name="see-also"></a>Weitere Informationen

[Direktivenverweis](directives-reference.md)\
[MASM-BNF-Grammatik](masm-bnf-grammar.md)
