---
title: 'Ressourcencompiler: Warnung RC4005'
ms.date: 11/04/2016
f1_keywords:
- RC4005
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
ms.openlocfilehash: c428fefa90cceed6a8bc9b7f6e4b95ec2db5e039
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182408"
---
# <a name="resource-compiler-warning-rc4005"></a>Ressourcencompiler: Warnung RC4005

"Bezeichner": Makro Neudefinition

Der Bezeichner wird zweimal definiert. Der Compiler hat die zweite Makro Definition verwendet.

Diese Warnung kann durch Definieren eines Makros in der Befehlszeile und im Code mit einer `#define`-Direktive verursacht werden. Dies kann auch durch Makros verursacht werden, die aus Includedateien importiert wurden.

Um die Warnung auszuschließen, entfernen Sie entweder eine der Definitionen, oder verwenden Sie eine `#undef` Direktive vor der zweiten Definition.
