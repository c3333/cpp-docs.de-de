---
title: Compilerfehler C2439
ms.date: 11/04/2016
f1_keywords:
- C2439
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
ms.openlocfilehash: 99f3644869f6c5395684643f0e7802f3a01baa62
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205360"
---
# <a name="compiler-error-c2439"></a>Compilerfehler C2439

"Bezeichner": Member konnte nicht initialisiert werden.

Klassen-, Struktur-oder Union-Member können nicht initialisiert werden.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Es wird versucht, eine indirekte Basisklasse oder Struktur zu initialisieren.

1. Es wird versucht, einen geerbten Member einer Klasse oder Struktur zu initialisieren. Ein geerbter Member muss vom Konstruktor der Klasse oder Struktur initialisiert werden.
