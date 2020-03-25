---
title: Compilerfehler C2692
ms.date: 11/04/2016
f1_keywords:
- C2692
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
ms.openlocfilehash: 7ce57cd50e9ec83cf80ec64e14f49eb9714f9208
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177091"
---
# <a name="compiler-error-c2692"></a>Compilerfehler C2692

' function_name ': vollständig Prototypfunktionen, die im C-Compiler mit der Option '/CLR ' erforderlich sind

Beim Kompilieren für verwalteten .NET-Code erfordert der C-Compiler ANSI-Funktions Deklarationen. Wenn eine Funktion keine Parameter annimmt, muss Sie außerdem explizit `void` als Parametertyp deklarieren.
