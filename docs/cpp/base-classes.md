---
title: Basisklassen
ms.date: 11/19/2018
helpviewer_keywords:
- inheritance, multiple
- base classes [C++], virtual
- derived classes [C++], multiple bases
- multiple inheritance, base classes
- virtual base classes [C++]
- base classes [C++]
ms.assetid: 6e6d54d0-6f21-4a16-9103-22935d98f596
ms.openlocfilehash: 50bddef3ea1ee1462d8cf115c0980270c8deab25
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181472"
---
# <a name="base-classes"></a>Basisklassen

Der Vererbungsprozess erstellt eine neue abgeleitete Klasse, die aus den Membern der Basisklasse(n) besteht, zuzüglich aller neuer Member, die von der abgeleiteten Klasse hinzugefügt werden. Bei einer Mehrfachvererbung ist es möglich, ein Vererbungsdiagramm zu erstellen, in dem dieselbe Basisklasse Teil von mehr als einer der abgeleiteten Klassen ist. Die folgende Abbildung zeigt ein solches Diagramm.

![Mehrere Instanzen einer Basisklasse](../cpp/media/vc38xn1.gif "Mehrere Instanzen einer Basisklasse") <br/>
Mehrere Instanzen einer einzelnen Basisklasse

In der Abbildung werden bildliche Darstellungen der Komponenten von `CollectibleString` und `CollectibleSortable` angezeigt. Allerdings gibt es die Basisklasse `Collectible` über den `CollectibleSortableString`-Pfad und den `CollectibleString`-Pfad in `CollectibleSortable`. Um diese Redundanz zu entfernen, können solche Klassen als virtuelle Basisklassen deklariert werden, wenn sie vererbt werden.
