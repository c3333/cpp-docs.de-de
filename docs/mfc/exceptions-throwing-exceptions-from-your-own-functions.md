---
title: 'Ausnahmen: Ausnahmen in eigenen Funktionen auslösen'
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
ms.openlocfilehash: ebdfea18e6e8445dd734bf43fb6a4ecf422975e9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622744"
---
# <a name="exceptions-throwing-exceptions-from-your-own-functions"></a>Ausnahmen: Ausnahmen in eigenen Funktionen auslösen

Es ist möglich, das MFC-Ausnahme Behandlungs Paradigma ausschließlich zu verwenden, um Ausnahmen abzufangen, die von Funktionen in MFC oder anderen Bibliotheken ausgelöst werden. Zusätzlich zum Abfangen von Ausnahmen, die vom Bibliotheks Code ausgelöst werden, können Sie Ausnahmen aus dem eigenen Code auslösen, wenn Sie Funktionen schreiben, die auf Ausnahmebedingungen stoßen können.

Wenn eine Ausnahme ausgelöst wird, wird die Ausführung der aktuellen Funktion beendet und springt direkt in den **catch** -Block des innersten Ausnahme Rahmens. Der Ausnahme Mechanismus umgeht den normalen Beendigungs Pfad von einer Funktion. Daher müssen Sie sicherstellen, dass Sie die Speicherblöcke löschen, die bei einem normalen beenden gelöscht werden.

#### <a name="to-throw-an-exception"></a>So lösen Sie eine Ausnahme aus

1. Verwenden Sie eine der MFC-Hilfsfunktionen, z `AfxThrowMemoryException` . b.. Diese Funktionen lösen ein vorab zugeordneter Exception-Objekt des entsprechenden Typs aus.

   Im folgenden Beispiel versucht eine Funktion, zwei Speicherblöcke zuzuordnen, und löst eine Ausnahme aus, wenn eine der Zuordnungen fehlschlägt:

   [!code-cpp[NVC_MFCExceptions#17](codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]

   Wenn die erste Zuordnung fehlschlägt, können Sie einfach die Speicher Ausnahme auslösen. Wenn die erste Zuordnung erfolgreich ist, die zweite jedoch fehlschlägt, müssen Sie den ersten Zuordnungs Block freigeben, bevor Sie die Ausnahme auslösen. Wenn beide Zuordnungen erfolgreich sind, können Sie den Vorgang normal fortsetzen und die Blöcke freigeben, wenn Sie die Funktion beenden.

     - ODER

1. Verwenden Sie eine benutzerdefinierte Ausnahme, um eine Problem Bedingung anzugeben. Sie können ein Element eines beliebigen Typs, auch eine ganze Klasse, als Ausnahme auslösen.

   Im folgenden Beispiel wird versucht, einen Sound über ein Wave-Gerät wiederzugeben, und es wird eine Ausnahme ausgelöst, wenn ein Fehler auftritt.

   [!code-cpp[NVC_MFCExceptions#18](codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]

> [!NOTE]
> Die Standardbehandlung von Ausnahmen in MFC gilt nur für Zeiger auf `CException` Objekte (und Objekte von von `CException` abgeleiteten Klassen). Im obigen Beispiel wird der MFC-Ausnahme Mechanismus umgangen.

## <a name="see-also"></a>Siehe auch

[Ausnahmebehandlung](exception-handling-in-mfc.md)
