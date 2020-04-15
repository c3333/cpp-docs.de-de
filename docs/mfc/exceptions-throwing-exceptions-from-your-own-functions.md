---
title: 'Ausnahmen: Ausnahmen in eigenen Funktionen auslösen'
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
ms.openlocfilehash: 6484594df7636fd52ac46ab1cc212c8e2ec0278e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359277"
---
# <a name="exceptions-throwing-exceptions-from-your-own-functions"></a>Ausnahmen: Ausnahmen in eigenen Funktionen auslösen

Es ist möglich, das MFC-Ausnahmebehandlungsparadigma ausschließlich zum Abfangen von Ausnahmen zu verwenden, die von Funktionen in MFC oder anderen Bibliotheken ausgelöst werden. Zusätzlich zum Abfangen von Ausnahmen, die vom Bibliothekscode ausgelöst werden, können Sie Ausnahmen von Ihrem eigenen Code auslösen, wenn Sie Funktionen schreiben, die außergewöhnliche Bedingungen erfüllen können.

Wenn eine Ausnahme ausgelöst wird, wird die Ausführung der aktuellen Funktion angehalten und springt direkt zum **Catch-Block** des innersten Ausnahmerahmens. Der Ausnahmemechanismus umgeht den normalen Ausstiegspfad von einer Funktion. Daher müssen Sie sicher sein, die Speicherblöcke zu löschen, die bei einem normalen Ausgang gelöscht würden.

#### <a name="to-throw-an-exception"></a>So auslösen Sie eine Ausnahme

1. Verwenden Sie eine der MFC-Hilfsfunktionen, z. `AfxThrowMemoryException`B. . Diese Funktionen auslösen ein vorab zugewiesenes Ausnahmeobjekt des entsprechenden Typs.

   Im folgenden Beispiel versucht eine Funktion, zwei Speicherblöcke zuzuweisen, und löst eine Ausnahme aus, wenn eine der beiden Zuweisungen fehlschlägt:

   [!code-cpp[NVC_MFCExceptions#17](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]

   Wenn die erste Zuweisung fehlschlägt, können Sie einfach die Speicherausnahme auslösen. Wenn die erste Zuordnung erfolgreich ist, die zweite jedoch fehlschlägt, müssen Sie den ersten Zuweisungsblock freimachen, bevor Sie die Ausnahme auslösen. Wenn beide Zuordnungen erfolgreich sind, können Sie normal fortfahren und die Blöcke beim Beenden der Funktion freimachen.

     - oder –

1. Verwenden Sie eine benutzerdefinierte Ausnahme, um eine Problembedingung anzugeben. Sie können ein Element eines beliebigen Typs, sogar eine ganze Klasse, als Ausnahme auslösen.

   Im folgenden Beispiel wird versucht, einen Sound über ein Wellengerät abzuspielen, und es wird eine Ausnahme ausgelöst, wenn ein Fehler auftritt.

   [!code-cpp[NVC_MFCExceptions#18](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]

> [!NOTE]
> Die Standardbehandlung von Ausnahmen durch MFC gilt `CException` nur für Zeiger `CException`auf Objekte (und Objekte von -abgeleiteten Klassen). Das obige Beispiel umgeht den MFC-Ausnahmemechanismus.

## <a name="see-also"></a>Siehe auch

[Ausnahmebehandlung](../mfc/exception-handling-in-mfc.md)
