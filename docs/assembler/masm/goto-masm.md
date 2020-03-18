---
title: GOTO (MASM)
ms.date: 12/16/2019
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: 18f286d8634202b57dea788aa6984755a5afb197
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440797"
---
# <a name="goto"></a>GOTO

Überträgt die Assembly an die Zeile, die mit **:** _Macrolabel_gekennzeichnet ist.

## <a name="syntax"></a>Syntax

> **Goto** *makrolabel*

## <a name="remarks"></a>Bemerkungen

**Goto** ist nur innerhalb von [Makros](macro.md), [for](for-masm.md)-, [FORC](forc.md)-, [Repeat](repeat.md)-und [while](while-masm.md) -Blöcken zulässig. Das *Makro Label* -Ziel muss die einzige Anweisung in der Zeile sein, und es muss ein vorangestelltem Doppelpunkt vorangestellt sein.

## <a name="see-also"></a>Weitere Informationen

[Direktivenverweis](directives-reference.md)\
[MASM-BNF-Grammatik](masm-bnf-grammar.md)
