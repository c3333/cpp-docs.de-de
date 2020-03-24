---
title: Linkertoolfehler LNK2017
ms.date: 11/04/2016
f1_keywords:
- LNK2017
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
ms.openlocfilehash: 02e80de5c34809a331003f3b0fb28d32e138a531
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194732"
---
# <a name="linker-tools-error-lnk2017"></a>Linkertoolfehler LNK2017

die Verschiebung von "Symbol" in "Segment" ist ungültig, ohne/LARGEADDRESSAWARE: Nein

Sie versuchen, ein 64-Bit-Image mit 32-Bit-Adressen zu erstellen. Zu diesem Zweck müssen Sie folgende Schritte ausführen:

- Verwenden Sie eine Adresse mit fester Auslastung.

- Beschränken Sie das Bild auf 3 GB.

- Geben Sie [/LARGEADDRESSAWARE: No](../../build/reference/largeaddressaware-handle-large-addresses.md)an.
