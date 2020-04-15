---
title: 'Ausnahmen: Änderungen für Ausnahmemakros in Version 3.0'
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
ms.openlocfilehash: 82320b0c7ccd6766e016f0437633339f8f8f61d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365492"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>Ausnahmen: Änderungen für Ausnahmemakros in Version 3.0

Dies ist ein fortgeschrittenes Thema.

In MFC-Version 3.0 und höher wurden die Makros für die Ausnahmebehandlung geändert, um C++-Ausnahmen zu verwenden. In diesem Artikel wird erläutert, wie sich diese Änderungen auf das Verhalten des vorhandenen Codes auswirken können, der die Makros verwendet.

In diesem Artikel werden die folgenden Themen behandelt:

- [Ausnahmetypen und das CATCH-Makro](#_core_exception_types_and_the_catch_macro)

- [Wiederauslösen von Ausnahmen](#_core_re.2d.throwing_exceptions)

## <a name="exception-types-and-the-catch-macro"></a><a name="_core_exception_types_and_the_catch_macro"></a>Ausnahmetypen und das CATCH-Makro

In früheren Versionen von MFC verwendete das **CATCH-Makro** MFC-Laufzeittypinformationen, um den Typ einer Ausnahme zu bestimmen. Der Typ der Ausnahme wird bestimmt, d. h. am Fangort. Bei C++-Ausnahmen wird der Typ der Ausnahme jedoch immer am Auswurfort durch den Typ des ausgelösten Ausnahmeobjekts bestimmt. Dies führt zu Inkompatibilitäten in dem seltenen Fall, in dem sich der Typ des Zeigers auf das ausgelöste Objekt vom Typ des ausgelösten Objekts unterscheidet.

Das folgende Beispiel veranschaulicht die Folgen dieses Unterschieds zwischen MFC-Version 3.0 und früheren Versionen:

[!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

Dieser Code verhält sich in Version 3.0 anders, da das Steuerelement immer an den ersten **catch-Block** mit einer übereinstimmenden Ausnahmedeklaration übergibt. Das Ergebnis des Wurfausdrucks

[!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

wird als `CException*`, geworfen, obwohl es `CCustomException`als . Das **CATCH-Makro** in MFC-Versionen `CObject::IsKindOf` 2.5 und früher wird verwendet, um den Typ zur Laufzeit zu testen. Da der Ausdruck

[!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

wahr ist, der erste Catch-Block fängt die Ausnahme ab. In Version 3.0, die C++-Ausnahmen verwendet, um viele der Exception-Handling-Makros zu implementieren, entspricht der zweite catch-Block dem ausgelösten `CException`.

Code wie dieser ist ungewöhnlich. Es wird normalerweise angezeigt, wenn ein Ausnahmeobjekt `CException*`an eine andere Funktion übergeben wird, die ein generisches akzeptiert, die "Pre-Throw"-Verarbeitung durchführt und schließlich die Ausnahme auslöst.

Um dieses Problem zu umgehen, verschieben Sie den Throw-Ausdruck von der Funktion in den aufrufenden Code, und lösen Sie eine Ausnahme des tatsächlichen Typs aus, der dem Compiler zum Zeitpunkt der Generierung der Ausnahme bekannt ist.

## <a name="re-throwing-exceptions"></a><a name="_core_re.2d.throwing_exceptions"></a>Wiederauslösen von Ausnahmen

Ein Catch-Block kann nicht denselben Ausnahmezeiger auslösen, den er abgefangen hat.

Dieser Code war z. B. in früheren Versionen gültig, hat jedoch unerwartete Ergebnisse mit Version 3.0:

[!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

Wenn Sie **THROW** im catch-Block verwenden, wird der Zeiger `e` gelöscht, sodass die äußere Catch-Site einen ungültigen Zeiger erhält. Verwenden Sie **THROW_LAST** `e`zum erneuten Zurückwerfen von .

Weitere Informationen finden Sie unter [Ausnahmen: Abfangen und Löschen von Ausnahmen](../mfc/exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Siehe auch

[Ausnahmebehandlung](../mfc/exception-handling-in-mfc.md)
