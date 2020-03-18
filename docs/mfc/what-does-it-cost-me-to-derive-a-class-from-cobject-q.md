---
title: Welcher Overhead entsteht beim Ableiten einer Klasse von CObject?
ms.date: 11/04/2016
helpviewer_keywords:
- CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
ms.openlocfilehash: 8f83bf9ee522487761aaa865a8315a174a47302d
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446042"
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>Welcher Overhead entsteht beim Ableiten einer Klasse von CObject?

Der Aufwand beim Ableiten von der Klasse [CObject](../mfc/reference/cobject-class.md) ist minimal. Ihre abgeleitete Klasse erbt nur vier virtuelle Funktionen und ein einzelnes [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) -Objekt.

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse: Häufig gestellte Fragen](../mfc/cobject-class-frequently-asked-questions.md)
