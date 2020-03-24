---
title: Compilerfehler C2241
ms.date: 11/04/2016
f1_keywords:
- C2241
helpviewer_keywords:
- C2241
ms.assetid: 2f4e2c2c-b95c-4afe-bbe0-4214cd39d140
ms.openlocfilehash: 4d09af5b29318e1481c666fcfe56b3f80434d4a0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206498"
---
# <a name="compiler-error-c2241"></a>Compilerfehler C2241

'Bezeichner': Memberzugriff ist eingeschränkt.

Der Code versucht, auf einen privaten oder geschützten Member zuzugreifen.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>So beheben Sie den Fehler (unterschiedliche Lösungsmöglichkeiten)

1. Ändern Sie die Zugriffsebene des Members.

1. Deklarieren Sie den Member als `friend` der zugreifenden Funktion.
