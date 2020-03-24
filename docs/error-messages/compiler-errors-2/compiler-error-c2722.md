---
title: Compilerfehler C2722
ms.date: 11/04/2016
f1_keywords:
- C2722
helpviewer_keywords:
- C2722
ms.assetid: 4cc2c7fa-cb12-4bcf-9df1-6d627ef62973
ms.openlocfilehash: 7426df1970dee58cd4363ee345e2286165e375b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202173"
---
# <a name="compiler-error-c2722"></a>Compilerfehler C2722

":: Operator": Ungültiger folgender Operator Befehl; use "Operator Operator"

Eine `operator`-Anweisung definiert `::new` oder `::delete`neu. Die Operatoren "`new`" und "`delete`" sind Global, sodass der Bereichs Auflösungs Operator (`::`) bedeutungslos ist. Entfernen Sie den `::` -Operator.
