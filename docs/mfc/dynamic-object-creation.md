---
title: Dynamische Objekterstellung
ms.date: 03/27/2020
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
ms.openlocfilehash: 40a17d3ed458d0634fd5bf27b54d0a36a65e35b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364805"
---
# <a name="dynamic-object-creation"></a>Dynamische Objekterstellung

In diesem Artikel wird erläutert, wie ein Objekt zur Laufzeit dynamisch erstellt wird. Das Verfahren verwendet Laufzeitklasseninformationen, wie im Artikel [Zugriff auf Laufzeitklasseninformationen](../mfc/accessing-run-time-class-information.md)erläutert.

#### <a name="dynamically-create-an-object-given-its-run-time-class"></a>Dynamisches Erstellen eines Objekts aufgrund seiner Laufzeitklasse

1. Verwenden Sie den folgenden Code, `CreateObject` um dynamisch `CRuntimeClass`ein Objekt mit der Funktion der zu erstellen. Gibt bei `CreateObject` einem Fehler **NULL** zurück, anstatt eine Ausnahme auszulösen:

   [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>Siehe auch

[Zerstören von Fensterobjekten](tn017-destroying-window-objects.md)
[mit CObject](using-cobject.md)
