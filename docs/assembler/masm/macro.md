---
title: MACRO
ms.date: 12/16/2019
f1_keywords:
- MACRO
helpviewer_keywords:
- MACRO directive
ms.assetid: 89434f7c-bc2c-4e91-8940-fe2db8785233
ms.openlocfilehash: 8eb0afdf73270c3e741f43b2e1fba02fe965846c
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076140"
---
# <a name="macro"></a>MACRO

Markiert einen Makroblock namens *Name* und richtet *Parameter* Platzhalter für Argumente ein, die übergeben werden, wenn das Makro aufgerufen wird.

## <a name="syntax"></a>Syntax

> *Name***Macro** ⟦*Parameter* ⟦ **: req** | : =*default* | *args* **: vararg**⟧... ⟧\
> *Anweisungen*\
⟦**Goto** :*makrolabelid*⟧ \
> ⟦**Exitm**⟧ \
> **ENDM** ⟦*Wert*⟧

## <a name="remarks"></a>Bemerkungen

Eine Makrofunktion gibt einen *Wert* an die aufrufenden Anweisung zurück.

## <a name="see-also"></a>Weitere Informationen

[Direktivenverweis](directives-reference.md)\
[Goto (MASM)](goto-masm.md) -\
[ENDM](endm.md) -\
[MASM-BNF-Grammatik](masm-bnf-grammar.md)
