---
title: Compilerfehler C2834
ms.date: 11/04/2016
f1_keywords:
- C2834
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
ms.openlocfilehash: a6a7bc0591fd51c808c303e94eeaaffd6111ffcd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201921"
---
# <a name="compiler-error-c2834"></a>Compilerfehler C2834

Operator Operator muss Global qualifiziert sein

Die `new`-und `delete` Operatoren sind an die Klasse gebunden, in der Sie sich befinden. Die Bereichs Auflösung kann nicht verwendet werden, um eine Version von `new` oder `delete` aus einer anderen Klasse auszuwählen. Um mehrere Formen der `new` oder `delete` Operator zu implementieren, erstellen Sie eine Version des Operators mit zusätzlichen formalen Parametern.
