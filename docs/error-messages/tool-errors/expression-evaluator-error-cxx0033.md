---
title: Ausdrucksauswertungsfehler CXX0033
ms.date: 11/04/2016
f1_keywords:
- CXX0033
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
ms.openlocfilehash: 2916808d98f1fabc2157fbedc96d76e196661279
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195512"
---
# <a name="expression-evaluator-error-cxx0033"></a>Ausdrucksauswertungsfehler CXX0033

Fehler in OMF-Typinformationen

Die ausführbare Datei hat kein gültiges Objekt Modulformat (OMF) für das Debuggen.

Dieser Fehler ist mit CAN0033 identisch.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Die ausführbare Datei wurde nicht mit dem Linker erstellt, der mit dieser Version C++von Visual veröffentlicht wurde. Verknüpfen Sie den Objektcode mithilfe der aktuellen Version von Link. exe erneut.

1. Die exe-Datei ist möglicherweise beschädigt. Kompilieren Sie das Programm erneut, und verknüpfen Sie es erneut.
