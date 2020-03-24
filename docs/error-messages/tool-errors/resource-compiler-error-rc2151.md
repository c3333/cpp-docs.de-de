---
title: 'Ressourcencompiler: Fehler RC2151'
ms.date: 11/04/2016
f1_keywords:
- RC2151
helpviewer_keywords:
- RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
ms.openlocfilehash: 9d4eea92321ca8373f3ad5f121f4a8e96d878e79
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191261"
---
# <a name="resource-compiler-error-rc2151"></a>Ressourcencompiler: Fehler RC2151

Zeichen folgen Konstanten können nicht wieder verwendet werden.

Der gleiche Wert wird in einer **STRINGTABLE** -Anweisung zweimal verwendet. Stellen Sie sicher, dass überlappende Dezimal-und hexadezimale Werte nicht gemischt werden.

Jede ID in einer **STRINGTABLE** muss eindeutig sein. Verwenden Sie für maximale Effizienz zusammenhängende Konstanten, die auf einem Vielfachen von 16 starten.
