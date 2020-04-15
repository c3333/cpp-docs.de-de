---
title: Ein- oder zweistufige Erstellung von Objekten
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
ms.openlocfilehash: 8f221ac6b63a06c65f932a695dfbf7b93ae7ac96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375967"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>Ein- oder zweistufige Erstellung von Objekten

Sie haben die Wahl zwischen zwei Techniken zum Erstellen von Grafikobjekten, z. B. Stifte und Pinsel:

- *Ein-Bauweise:* Erstellen und initialisieren Sie das Objekt in einer Phase, alle mit dem Konstruktor.

- *Zweistufige Konstruktion*: Konstruieren und initialisieren Sie das Objekt in zwei separaten Stufen. Der Konstruktor erstellt das Objekt, und eine Initialisierungsfunktion initialisiert es.

Zweistufiger Bau ist immer sicherer. Bei einer einstufigen Konstruktion kann der Konstruktor eine Ausnahme auslösen, wenn Sie falsche Argumente angeben oder die Speicherzuweisung fehlschlägt. Dieses Problem wird durch zweistufige Konstruktion vermieden, obwohl Sie auf Fehler überprüfen müssen. In beiden Fällen ist das Zerstören des Objekts derselbe Prozess.

> [!NOTE]
> Diese Techniken gelten für das Erstellen von Objekten, nicht nur für Grafikobjekte.

## <a name="example-of-both-construction-techniques"></a>Beispiel für beide Konstruktionstechniken

Das folgende kurze Beispiel zeigt beide Methoden zum Erstellen eines Stiftobjekts:

[!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr darüber wissen?

- [Grafische Objekte](../mfc/graphic-objects.md)

- [Auswählen eines Grafikobjekts in einem Gerätekontext](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [Gerätekontexte](../mfc/device-contexts.md)

- [Zeichnen in einer Ansicht](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>Siehe auch

[Grafikobjekte](../mfc/graphic-objects.md)
