---
title: INVOKE
ms.date: 11/05/2019
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: ba1377359ba9bc960e5d7d2a55df15adfe0d5d33
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076222"
---
# <a name="invoke"></a>INVOKE

(nur 32-Bit-MASM.) Ruft die Prozedur bei der von *Ausdruck*angegebenen Adresse auf und übergibt die Argumente auf dem Stapel oder in Registern gemäß den Standard Aufruf Konventionen des sprach Typs.

## <a name="syntax"></a>Syntax

> **INVOKE** *Ausdruck* aufrufen ⟦ __,__ *Argument* ... ⟧

## <a name="remarks"></a>Bemerkungen

Jedes Argument, das an die Prozedur übermittelt wird, kann ein Ausdruck, ein Registrierungs Paar oder ein Adress Ausdruck (ein Ausdruck mit vorangestelltem **addr**) sein.

## <a name="see-also"></a>Weitere Informationen

[Direktivenverweis](directives-reference.md)\
[MASM-BNF-Grammatik](masm-bnf-grammar.md)
