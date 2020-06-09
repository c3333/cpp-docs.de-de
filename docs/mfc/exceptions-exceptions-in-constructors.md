---
title: 'Ausnahmen: Ausnahmen in Konstruktoren'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
ms.openlocfilehash: 4089f4d44f03c7de3432f137b5d28f74189e1cb9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624616"
---
# <a name="exceptions-exceptions-in-constructors"></a>Ausnahmen: Ausnahmen in Konstruktoren

Wenn Sie eine Ausnahme in einem Konstruktor auslösen, bereinigen Sie alle Objekte und Speicher Belegungen, die Sie vor dem Auslösen der Ausnahme erstellt haben, wie in [Ausnahmen: Auslösen von Ausnahmen von ihren eigenen Funktionen](exceptions-throwing-exceptions-from-your-own-functions.md)erläutert.

Wenn eine Ausnahme in einem Konstruktor ausgelöst wird, wurde der Speicher für das Objekt selbst bereits durch die Zeit zugewiesen, zu der der Konstruktor aufgerufen wird. Daher wird der von dem-Objekt belegte Arbeitsspeicher vom Compiler automatisch aufgehoben, nachdem die Ausnahme ausgelöst wurde.

Weitere Informationen finden Sie unter [Ausnahmen: Freigeben von Objekten in Ausnahmen](exceptions-freeing-objects-in-exceptions.md).

## <a name="see-also"></a>Siehe auch

[Ausnahmebehandlung](exception-handling-in-mfc.md)
