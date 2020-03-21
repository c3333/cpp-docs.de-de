---
title: .CODE
ms.date: 12/17/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 7e53befcc46319d0ecf2287ab96a19a73a0b0b85
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076275"
---
# <a name="code"></a>.CODE

(nur 32-Bit-MASM.) Bei Verwendung mit [. Model](dot-model.md)gibt den Anfang eines Code Segments an.

## <a name="syntax"></a>Syntax

> **. Code** ⟦*Name*⟧ \
> ⟦ *segmentitem* ⟧... \
> ⟦ *codesegmentnameid* wird **beendet**;; ⟧\

### <a name="parameters"></a>Parameter

*Name*\
Optionaler Parameter, der den Namen des Code Segments angibt. Der Standardname ist für kleine, kleine, kompakte und flache [Modelle](dot-model.md) **_text** . Der Standardname ist " *ModuleName*" _text für andere Modelle.

## <a name="see-also"></a>Weitere Informationen

[Direktivenverweis](directives-reference.md)\
[. Daten](dot-data.md)\
[MASM-BNF-Grammatik](masm-bnf-grammar.md)
