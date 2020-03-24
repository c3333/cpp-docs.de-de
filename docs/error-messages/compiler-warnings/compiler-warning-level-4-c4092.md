---
title: Compilerwarnung (Stufe 4) C4092
ms.date: 11/04/2016
f1_keywords:
- C4092
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
ms.openlocfilehash: 6786d692785dbca575d4b241b7b3e3d40575b686
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198548"
---
# <a name="compiler-warning-level-4-c4092"></a>Compilerwarnung (Stufe 4) C4092

sizeof gibt "unsigned long" zurück

Der Operand des `sizeof` Operators war sehr groß, sodass `sizeof` einen Ganzzahl ohne Vorzeichen **Long**-Operator zurückgegeben hat. Diese Warnung tritt unter den Microsoft-Erweiterungen ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)) auf. Unter ANSI Compatibility (/Za) wird das Ergebnis stattdessen abgeschnitten.
