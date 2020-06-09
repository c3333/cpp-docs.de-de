---
title: 'Ausnahmen: Änderungen für Ausnahmemakros in Version 3.0'
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
ms.openlocfilehash: 25095257096efd869e237383c5cd202ae4e602c2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620168"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>Ausnahmen: Änderungen für Ausnahmemakros in Version 3.0

Dies ist ein erweitertes Thema.

In MFC-Version 3,0 und höher wurden die Makros für die Ausnahmebehandlung geändert, um C++-Ausnahmen zu verwenden. In diesem Artikel wird erläutert, wie sich diese Änderungen auf das Verhalten von vorhandenem Code auswirken können, der die Makros verwendet.

In diesem Artikel werden die folgenden Themen behandelt:

- [Ausnahme Typen und das CATCH-Makro](#_core_exception_types_and_the_catch_macro)

- [Erneutes Auslösen von Ausnahmen](#_core_re.2d.throwing_exceptions)

## <a name="exception-types-and-the-catch-macro"></a><a name="_core_exception_types_and_the_catch_macro"></a>Ausnahme Typen und das CATCH-Makro

In früheren Versionen von MFC verwendete das **catch** -Makro MFC-Lauf Zeittyp Informationen, um den Typ einer Ausnahme zu bestimmen. der Typ der Ausnahme wird mit anderen Worten an der catch-Site festgelegt. Mit C++-Ausnahmen wird der Typ der Ausnahme jedoch immer durch den Typ des ausgelösten Ausnahme Objekts an der Throw-Site bestimmt. Dies führt zu Inkompatibilitäten im seltenen Fall, dass sich der Typ des Zeigers auf das ausgelöste Objekt von dem Typ des ausgelösten Objekts unterscheidet.

Im folgenden Beispiel wird die Folge dieses Unterschieds zwischen MFC-Version 3,0 und früheren Versionen veranschaulicht:

[!code-cpp[NVC_MFCExceptions#1](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

Dieser Code verhält sich in Version 3,0 anders, da die Steuerung immer an den ersten **catch** -Block mit einer entsprechenden Ausnahme Deklaration weitergeleitet wird. Das Ergebnis des Throw-Ausdrucks.

[!code-cpp[NVC_MFCExceptions#19](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

wird als ausgelöst `CException*` , obwohl es als erstellt wird `CCustomException` . Das **catch** -Makro in den MFC-Versionen 2,5 und früher verwendet `CObject::IsKindOf` , um den Typ zur Laufzeit zu testen. Da der Ausdruck

[!code-cpp[NVC_MFCExceptions#20](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

true gibt an, dass der erste catch-Block die Ausnahme abfängt. In Version 3,0, die C++-Ausnahmen verwendet, um viele der Ausnahme Behandlungs Makros zu implementieren, stimmt der zweite catch-Block mit dem ausgelösten überein `CException` .

Ein solcher Code ist nicht üblich. Sie wird normalerweise angezeigt, wenn ein Ausnahme Objekt an eine andere Funktion übergeben wird, die eine generische akzeptiert `CException*` , eine "Pre-Throw"-Verarbeitung ausführt und schließlich die Ausnahme auslöst.

Um dieses Problem zu umgehen, verschieben Sie den Throw-Ausdruck aus der Funktion in den aufrufenden Code und lösen eine Ausnahme des tatsächlichen Typs aus, der dem Compiler zum Zeitpunkt der Ausnahme Generierung bekannt ist.

## <a name="re-throwing-exceptions"></a><a name="_core_re.2d.throwing_exceptions"></a>Erneutes Auslösen von Ausnahmen

Ein catch-Block kann nicht denselben Ausnahme Zeiger auslösen, den er abgefangen hat.

Dieser Code war z. b. in früheren Versionen gültig, hat jedoch unerwartete Ergebnisse mit Version 3,0:

[!code-cpp[NVC_MFCExceptions#2](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

Die Verwendung von **throw** im catch-Block bewirkt `e` , dass der Zeiger gelöscht wird, sodass die äußere catch-Site einen ungültigen Zeiger empfängt. Verwenden Sie **THROW_LAST** , um erneut auszulösen `e` .

Weitere Informationen finden Sie unter [Ausnahmen: abfangen und Löschen von Ausnahmen](exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Siehe auch

[Ausnahmebehandlung](exception-handling-in-mfc.md)
