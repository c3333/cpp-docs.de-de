---
title: Compilerfehler C2585
ms.date: 11/04/2016
f1_keywords:
- C2585
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
ms.openlocfilehash: 57a0cd7a200c5bbb875821eb9e10314d98e58185
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177390"
---
# <a name="compiler-error-c2585"></a>Compilerfehler C2585

die explizite Konvertierung in "Typ" ist mehrdeutig.

Die Typkonvertierung kann mehr als ein Ergebnis verursachen.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Die Umstellung von einer Klasse oder einem Strukturtyp auf der Grundlage mehrerer Vererbung. Wenn der Typ dieselbe Basisklasse mehrmals erbt, muss die Konvertierungs Funktion oder der Operator Bereichs Auflösung (`::`) verwenden, um anzugeben, welche der geerbten Klassen bei der Konvertierung verwendet werden soll.

1. Ein Konvertierungs Operator und ein Konstruktor wurden definiert, sodass die gleiche Konvertierung durchführen.
