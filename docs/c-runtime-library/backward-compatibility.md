---
title: Backward Compatibility
description: Verwendung von Microsoft OLDNAMES. LIB-Bibliothek zum Zuordnen von Funktionsnamen aus Gründen der Abwärtskompatibilität.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CRT, compatibility
- backward compatibility, C run-time libraries
- compatibility, C run-time libraries
- backward compatibility
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
ms.openlocfilehash: b09104a5cff4d8e4cc31f9cc4707e808988401d6
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590289"
---
# <a name="backward-compatibility"></a>Backward Compatibility

Um Kompatibilität zwischen Produktversionen bereitzustellen, ordnet die Bibliothek „OLDNAMES.LIB“ alte Namen neuen Namen zu. Beispielsweise wird `open``_open` zugeordnet. Sie müssen nur dann eine explizite Verknüpfung mit OLDNAMES.LIB herstellen, wenn Sie mit Befehlszeilenoptionen in folgenden Kombinationen kompilieren:

- `/Zl`(Standardbibliotheknamen von Objektdatei unterdrücken) und `/Ze` (die Standardeinstellung – Microsoft-Erweiterungen verwenden)

- `/link`(Linker-Steuerelement), `/NOD` („no default library“-Suche) und`/Ze`

Weitere Informationen zu Compilerbefehlszeilenoptionen finden Sie unter [Compilerreferenz](../build/reference/compiler-options.md).

## <a name="see-also"></a>Weitere Informationen

[Kompatibilität](../c-runtime-library/compatibility.md)
