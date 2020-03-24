---
title: 'Ressourcencompiler: Warnung RW4004'
ms.date: 11/04/2016
f1_keywords:
- RW4004
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
ms.openlocfilehash: ca0fb271a5ab43994ec37cc8d59c33877903f6e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182343"
---
# <a name="resource-compiler-warning-rw4004"></a>Ressourcencompiler: Warnung RW4004

ASCII-Zeichen entspricht nicht dem virtuellem Tastencode

Für den virtueller Tastencode in einer VIRTKEY-Zugriffstaste wurde ein Zeichenfolgenliteral verwendet.

Trotz der Warnung können Sie den Vorgang fortsetzen. Sie informiert Sie jedoch darüber, dass die generierten Zugriffstasten möglicherweise nicht mit der Zeichenfolge übereinstimmen, die Sie angegeben haben. (VIRTKEY-Zugriffstasten verwenden andere Tastencodes als ASCII-Zugriffstasten.)

Obwohl Zeichenfolgenliterale syntaktisch gültig sind, können Sie nur sicherstellen, dass Sie die gewünschte Zugriffstaste erhalten, indem Sie die **VK_\* #define** Werte in Windows. h verwenden.
