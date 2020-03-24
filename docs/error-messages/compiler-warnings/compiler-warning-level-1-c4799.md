---
title: Compilerwarnung (Stufe 1) C4799
ms.date: 11/04/2016
f1_keywords:
- C4799
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
ms.openlocfilehash: ec92da425718cd5ddc579d1d733a0bc4e56dc04a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175102"
---
# <a name="compiler-warning-level-1-c4799"></a>Compilerwarnung (Stufe 1) C4799

> Keine EMMS am Ende der Funktion "*Function*"

Die Funktion verfügt über mindestens eine MMX-Anweisung, verfügt jedoch nicht über eine `EMMS` Anweisung. Wenn eine Multimedia-Anweisung verwendet wird, sollte auch eine `EMMS` Anweisung oder eine systeminterne `_mm_empty` verwendet werden, um das Multimedia-Tagwort am Ende des MMX-Codes zu löschen.

Sie erhalten möglicherweise C4799 bei Verwendung von "ivec. h", was darauf hinweist, dass der Code die EMMS-Anweisung vor der Rückgabe nicht ordnungsgemäß ausführt. Dies ist eine falsche Warnung für diese Header. Sie können diese deaktivieren, indem Sie _SILENCE_IVEC_C4799 in "ivec. h" definieren. Beachten Sie jedoch, dass dies auch dazu führt, dass der Compiler keine korrekten Warnungen dieses Typs gibt.

Weitere Informationen finden Sie im [MMX-Anweisungs Satz von Intel](../../assembler/inline/intel-s-mmx-instruction-set.md).
