---
title: Richtungsflag
ms.date: 11/04/2016
helpviewer_keywords:
- direction flag
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
ms.openlocfilehash: 04e096c6a62f806f4c214745a8401b1730eda3a6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443383"
---
# <a name="direction-flag"></a>Richtungsflag

Das Richtungsflag ist ein spezielles CPU-Flag für alle mit Intel x86 kompatiblen Prozessoren. Dies gilt für alle Assemblyanweisungen, die das REP-Präfix (Wiederholung) verwenden, z.B. MOVS, MOVSD, MOVSW und andere. Adressen, die entsprechenden Anweisungen bereitgestellt werden, werden erhöht, wenn das Richtungsflag deaktiviert ist.

Die C-Laufzeitroutinen setzen voraus, dass das Richtungsflag deaktiviert ist. Wenn Sie andere Funktionen mit den C-Laufzeitfunktionen verwenden, müssen Sie sicherstellen, dass die anderen Funktionen das Richtungsflag unbeeinflusst lassen oder in seinem ursprünglichen Zustand wiederherstellen. Die Erwartung, dass das Richtungsflag beim Einstieg deaktiviert ist, macht den Laufzeitcode schneller und effizienter.

Die C-Laufzeitbibliotheksfunktionen wie Zeichenfolgenbearbeitungs- und Pufferbearbeitungsroutinen erwarten, dass das Richtungsflag deaktiviert ist.

## <a name="see-also"></a>Weitere Informationen

[CRT-Bibliotheksfunktionen](../c-runtime-library/crt-library-features.md)
