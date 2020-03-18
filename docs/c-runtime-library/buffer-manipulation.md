---
title: Pufferbearbeitung
ms.date: 04/04/2018
helpviewer_keywords:
- buffers, manipulation routines
- buffers
ms.assetid: 164f4860-ce66-412c-8291-396fbd70f03e
ms.openlocfilehash: a79bfdb33d2bff5e18c916a2e116ab03251afdf1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443590"
---
# <a name="buffer-manipulation"></a>Pufferbearbeitung

Verwenden Sie diese Routinen, um auf Einzelbytebasis mit Arbeitsspeicherbereichen zu arbeiten.

## <a name="buffer-manipulation-routines"></a>Routinen der Pufferbearbeitung

|Routine|Zweck|
|-------------|---------|
|[_memccpy](../c-runtime-library/reference/memccpy.md)|Kopiert Zeichen aus einem Puffer in einen anderen, bis das angegebene Zeichen oder die angegebene Anzahl von Zeichen kopiert wurde.|
|[memchr, wmemchr](../c-runtime-library/reference/memchr-wmemchr.md)|Gibt einen Zeiger auf das erste Vorkommen des angegebenen Zeichens innerhalb einer angegebenen Anzahl von Zeichen im Puffer zurück.|
|[memcmp, wmemcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|Vergleicht die angegebene Anzahl von Zeichen in zwei Puffern.|
|[memcpy, wmemcpy](../c-runtime-library/reference/memcpy-wmemcpy.md), [memcpy_s, wmemcpy_s](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|Kopiert eine angegebene Anzahl von Zeichen aus einem Puffer in einen anderen.|
|[_memicmp, _memicmp_l](../c-runtime-library/reference/memicmp-memicmp-l.md)|Vergleicht die angegebene Anzahl von Zeichen in zwei Puffern ohne Berücksichtigung der Groß- und Kleinschreibung.|
|[memmove, wmemmove](../c-runtime-library/reference/memmove-wmemmove.md),[memmove_s, wmemmove_s](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|Kopiert eine angegebene Anzahl von Zeichen aus einem Puffer in einen anderen.|
|[memset, wmemset](../c-runtime-library/reference/memset-wmemset.md)|Verwendet das angegebene Zeichen, um die angegebene Anzahl von Bytes im Puffer zu initialisieren.|
|[_swab](../c-runtime-library/reference/swab.md)|Lagert Datenbytes aus und speichert sie am angegebenen Speicherort.|

Wenn die Quell- und Zielbereiche überlappen, garantiert nur **memmove**, dass die vollständige Quelle ordnungsgemäß kopiert wird.

## <a name="see-also"></a>Weitere Informationen

[Universelle C-Laufzeitroutinen nach Kategorie](../c-runtime-library/run-time-routines-by-category.md)
