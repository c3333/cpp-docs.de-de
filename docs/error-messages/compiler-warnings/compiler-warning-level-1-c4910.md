---
title: Compilerwarnung (Stufe 1) C4910
ms.date: 11/04/2016
f1_keywords:
- C4910
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: b17df9d7a9997e5d8ef37a4721de8693968cbbdf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214450"
---
# <a name="compiler-warning-level-1-c4910"></a>Compilerwarnung (Stufe 1) C4910

" \<identifier> ": "__declspec (dllexport)" und "extern" sind bei einer expliziten Instanziierung nicht kompatibel.

Die explizite Vorlagen Instanziierung mit dem Namen *\<identifier>* wird durch das `__declspec(dllexport)` -Schlüsselwort und das-Schlüsselwort geändert **`extern`** . Die beiden Schlüsselwörter schließen sich jedoch gegenseitig aus. Das `__declspec(dllexport)` Schlüsselwort bedeutet, dass die Vorlagen Klasse instanziiert wird, während das **`extern`** Schlüsselwort bedeutet, dass die Vorlagen Klasse nicht automatisch instanziiert.

## <a name="see-also"></a>Weitere Informationen

[Explizite Instanziierung](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[Allgemeine Regeln und Einschränkungen](../../cpp/general-rules-and-limitations.md)
