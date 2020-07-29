---
title: Compilerfehler C2241
ms.date: 11/04/2016
f1_keywords:
- C2241
helpviewer_keywords:
- C2241
ms.assetid: 2f4e2c2c-b95c-4afe-bbe0-4214cd39d140
ms.openlocfilehash: c02651df5f06b12fd57667fa3d5b470179fd35f7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87208875"
---
# <a name="compiler-error-c2241"></a>Compilerfehler C2241

'Bezeichner': Memberzugriff ist eingeschränkt.

Der Code versucht, auf einen privaten oder geschützten Member zuzugreifen.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>So beheben Sie den Fehler (unterschiedliche Lösungsmöglichkeiten)

1. Ändern Sie die Zugriffsebene des Members.

1. Deklarieren Sie den Member a der Zuordnungs **`friend`** Funktion.
