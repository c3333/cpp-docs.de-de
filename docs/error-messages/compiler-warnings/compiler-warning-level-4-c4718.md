---
title: Compilerwarnung (Stufe 4) C4718
ms.date: 11/04/2016
f1_keywords:
- C4718
helpviewer_keywords:
- C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
ms.openlocfilehash: 48452ed53b93d7cd89daadd3f7ab3a69b453e1a1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198158"
---
# <a name="compiler-warning-level-4-c4718"></a>Compilerwarnung (Stufe 4) C4718

'Funktionsaufruf': Rekursiver Aufruf besitzt keine Nebeneffekte, wird gelöscht

Eine Funktion enthält einen rekursiven Aufruf, hat aber ansonsten keine Nebeneffekte. Ein Aufruf dieser Funktion wird gelöscht. Die Richtigkeit des Programms ist nicht betroffen, aber die Verhaltensweise. Wenn der Aufruf beibehalten wird, kann dies zu einer Stapelüberlaufausnahme zur Laufzeit führen. Das Löschen des Aufrufs beseitigt diese Möglichkeit.
