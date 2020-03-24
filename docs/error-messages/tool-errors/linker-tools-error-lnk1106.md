---
title: Linkertoolfehler LNK1106
ms.date: 11/04/2016
f1_keywords:
- LNK1106
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
ms.openlocfilehash: 091d4e173bfb2eff8ffee2b5c30647f4d5e3bc04
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195369"
---
# <a name="linker-tools-error-lnk1106"></a>Linkertoolfehler LNK1106

Ungültige Datei oder Datenträger voll: Suche nach Speicherort nicht möglich.

Das Tool konnte in einer Speicher Abbild Datei nicht auf `location` lesen oder schreiben.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Datenträger ist voll.

   Freigeben von Speicherplatz und erneutes verknüpfen.

1. Es wird versucht, eine Verknüpfung über ein Netzwerk herzustellen.

   Einige Netzwerke unterstützen die Speicher Abbild Dateien, die vom Linker verwendet werden, nicht vollständig. Versuchen Sie, auf Ihrem lokalen Datenträger zu verknüpfen.

1. Ungültiger Block auf Ihrem Datenträger.

   Obwohl das Betriebssystem und die Datenträger Hardware einen solchen Fehler feststellen sollten, empfiehlt es sich, ein Programm zur Datenträger Überprüfung auszuführen.

1. Nicht genügend Heap Speicher.

   Weitere Informationen finden Sie unter [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) .
