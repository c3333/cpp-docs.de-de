---
title: Ein- oder zweistufige Erstellung von Objekten
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
ms.openlocfilehash: 07e006d5b326486c54f23990c604a7d2ee0e4c83
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625286"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>Ein- oder zweistufige Erstellung von Objekten

Sie haben die Wahl zwischen zwei Techniken zum Erstellen von Grafikobjekten, wie z. b. Stifte und Pinsel:

- *Einstufige Konstruktion*: konstruieren und initialisieren Sie das Objekt in einer Phase, alle mit dem-Konstruktor.

- *Zweistufige Konstruktion*: Erstellen und initialisieren Sie das Objekt in zwei separaten Phasen. Der-Konstruktor erstellt das-Objekt, und eine Initialisierungsfunktion initialisiert es.

Die zweistufige Konstruktion ist immer sicherer. Bei der einstufigen Erstellung kann der Konstruktor eine Ausnahme auslösen, wenn Sie falsche Argumente angeben oder die Speicher Belegung fehlschlägt. Dieses Problem wird durch die zweistufige Konstruktion vermieden, obwohl Sie eine Überprüfung auf Fehler durchführen müssen. In beiden Fällen ist das zerstören des Objekts der gleiche Prozess.

> [!NOTE]
> Diese Techniken gelten für das Erstellen von Objekten, nicht nur für Grafik Objekte.

## <a name="example-of-both-construction-techniques"></a>Beispiel für beide Konstruktionstechniken

Das folgende kurze Beispiel zeigt beide Methoden zum Erstellen eines Stift Objekts:

[!code-cpp[NVC_MFCDocViewSDI#6](codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Grafik Objekte](graphic-objects.md)

- [Auswählen eines Grafik Objekts in einen Gerätekontext](selecting-a-graphic-object-into-a-device-context.md)

- [Geräte Kontexte](device-contexts.md)

- [Zeichnen in einer Ansicht](drawing-in-a-view.md)

## <a name="see-also"></a>Siehe auch

[Grafikobjekte](graphic-objects.md)
