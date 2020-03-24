---
title: Compilerwarnung (Stufe 1) C4276
ms.date: 11/04/2016
f1_keywords:
- C4276
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
ms.openlocfilehash: c1de07cd65bbc9f02a979ceebe31be4143af70ad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175817"
---
# <a name="compiler-warning-level-1-c4276"></a>Compilerwarnung (Stufe 1) C4276

"Function": kein Prototyp angegeben; Es wurden keine Parameter angenommen

Wenn Sie die Adresse einer Funktion mit der [__stdcall](../../cpp/stdcall.md) Aufruf Konvention übernehmen, müssen Sie einen Prototyp angeben, damit der Compiler den ergänzten Namen der Funktion erstellen kann. Da die *Funktion* keinen Prototyp hat, geht der Compiler beim Erstellen des ergänzten Namens davon aus, dass die Funktion über keine Parameter verfügt.
