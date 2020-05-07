---
title: Auswertung von Tokens
ms.date: 11/04/2016
helpviewer_keywords:
- tokens, evaluating
ms.assetid: 28870b62-dff6-4644-8b75-d58f340b48d2
ms.openlocfilehash: 15775ca9a7ada46aaf4e53ae952cd67e95bbf8d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234022"
---
# <a name="evaluation-of-tokens"></a>Auswertung von Tokens

Wenn der Compiler Token interpretiert, schließt er so viele Zeichen wie möglich in einem einzelnen Token ein, bevor er mit dem nächsten Token fortfährt. Aufgrund dieses Verhaltens interpretiert der Compiler möglicherweise die Token nicht wie beabsichtigt, wenn sie nicht ordnungsgemäß durch Leerzeichen getrennt werden. Betrachten Sie hierzu den folgenden Ausdruck:

```
i+++j
```

In diesem Beispiel erstellt der Compiler zunächst den längsten möglichen Operator (`++`) aus den drei Pluszeichen, dann verarbeitet er das verbleibende Pluszeichen als Addition-Operator (`+`). Daher wird der Ausdruck als `(i++) + (j)` und nicht als `(i) + (++j)` interpretiert. Verwenden Sie in diesem und ähnlichen Fällen Leerzeichen und Klammern, um Mehrdeutigkeiten zu vermeiden und eine ordnungsgemäße Ausdrucksbewertung sicherzustellen.

**Microsoft-spezifisch**

Der C-Compiler behandelt ein STRG+Z-Zeichen als Dateiendeindikator. Er ignoriert jeden Text nach STRG+Z.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[C-Tokens](../c-language/c-tokens.md)
