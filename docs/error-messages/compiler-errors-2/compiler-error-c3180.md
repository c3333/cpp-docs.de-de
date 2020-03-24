---
title: Compilerfehler C3180
ms.date: 11/04/2016
f1_keywords:
- C3180
helpviewer_keywords:
- C3180
ms.assetid: 5281f583-7df7-418a-8507-d4da67ed6572
ms.openlocfilehash: c94019bf7a58492fcbb27c4f092a6e5f7e36ca25
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176454"
---
# <a name="compiler-error-c3180"></a>Compilerfehler C3180

' Typname ': der Name überschreitet das Metadatenlimit von ' Limit '-Zeichen.

Der Compiler hat den Namen für einen verwalteten Typ in den Metadaten abgeschnitten. Durch das Abschneiden wird der Typ mit der `#using`-Direktive (oder der Entsprechung in einer anderen Sprache) unbrauchbar.

Der Typ-Name-Grenzwert schließt alle Namespace Qualifikationen ein.
