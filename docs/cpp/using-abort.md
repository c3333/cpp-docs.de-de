---
title: Verwenden von "abort"
ms.date: 11/04/2016
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
ms.openlocfilehash: e8cc7bce552acf67c0f9bf2025e0040dc051cff6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446422"
---
# <a name="using-abort"></a>Verwenden von "abort"

Das Aufrufen der [Abbruch](../c-runtime-library/reference/abort.md) -Funktion bewirkt eine sofortige Beendigung. Dies umgeht den normalen Zerstörungsprozess für initialisierte globale statische Objekte. Außerdem wird jegliche spezielle Verarbeitung umgangen, die mit der `atexit`-Funktion angegeben wurde.

## <a name="see-also"></a>Weitere Informationen

[Weitere Überlegungen zur Beendigung](../cpp/additional-termination-considerations.md)