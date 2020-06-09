---
title: Dynamische Objekterstellung
ms.date: 03/27/2020
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
ms.openlocfilehash: 00e627e6d73e510ca694966291e2ef518fef18b5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619546"
---
# <a name="dynamic-object-creation"></a>Dynamische Objekterstellung

In diesem Artikel wird erläutert, wie ein Objekt zur Laufzeit dynamisch erstellt wird. Die Prozedur verwendet Lauf Zeit Klassen Informationen, wie im Artikel [zugreifen auf Lauf Zeit Klassen Informationen](accessing-run-time-class-information.md)erläutert.

#### <a name="dynamically-create-an-object-given-its-run-time-class"></a>Dynamisches Erstellen eines Objekts bei Angabe der Lauf Zeit Klasse

1. Verwenden Sie den folgenden Code, um mithilfe der-Funktion von ein-Objekt dynamisch zu erstellen `CreateObject` `CRuntimeClass` . Bei einem Fehler `CreateObject` wird **null** zurückgegeben, anstatt eine Ausnahme zu verursachen:

   [!code-cpp[NVC_MFCCObjectSample#6](codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>Siehe auch

[Zerstören von Fenster Objekten](tn017-destroying-window-objects.md) 
 [Verwenden von CObject](using-cobject.md)
