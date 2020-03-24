---
title: Assertion und benutzerdefinierte Meldungen (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- user-supplied messages [C++], run time
- user-supplied messages [C++], preprocessor time
- '#error%2C assert%2C static_assert [C++]'
- user-supplied messages [C++], compile time
ms.assetid: ebf7d885-61c8-4233-b0ae-1c9a38e0f385
ms.openlocfilehash: d76f0c2f7dc5a4202bff3f93e097a1c186f4601a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190559"
---
# <a name="assertion-and-user-supplied-messages-c"></a>Assertion und benutzerdefinierte Meldungen (C++)

Die C++ Sprache unterstützt drei Fehler Behandlungs Mechanismen, die Sie beim Debuggen Ihrer Anwendung unterstützen: die [#Error-Direktive](../preprocessor/hash-error-directive-c-cpp.md), das [static_assert](../cpp/static-assert.md) -Schlüsselwort und das [ASSERT-Makro, _ASSERT _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) Makro. Alle drei Mechanismen geben Fehlermeldungen aus, zwei testen auch Softwareassertionen. Eine Softwareassertion gibt eine Bedingung an, die an einer bestimmten Stelle im Programm "true" sein muss. Wenn bei einer Assertion zur Kompilierzeit ein Fehler auftritt, gibt der Compiler eine Diagnosemeldung und einen Kompilierungsfehler aus. Wenn bei einer Assertion zur Laufzeit ein Fehler auftritt, gibt das Betriebssystem eine Diagnosemeldung aus und schließt Ihre Anwendung.

## <a name="remarks"></a>Bemerkungen

Die Lebensdauer der Anwendung besteht aus einer Vorverarbeitungs-, einer Kompilierungs- und einer Laufzeitphase. Jeder Mechanismus zur Fehlerbehandlung greift auf Debuginformationen zu, die während einer dieser Phasen verfügbar sind. Um auf effiziente Weise zu debuggen, wählen Sie den Mechanismus aus, der entsprechende Informationen über diese Phase bereitstellt:

- Die [#Error-Direktive](../preprocessor/hash-error-directive-c-cpp.md) ist während der Vorverarbeitungs Zeit wirksam. Sie gibt bedingungslos eine vom Benutzer angegebene Meldung aus und führt dazu, dass die Kompilierung mit einem Fehler beendet wird. Die Meldung kann Text enthalten, der von Präprozessordirektiven geändert wird, aber Ausdrucksergebnisse werden nicht gewertet.

- Die [static_assert](../cpp/static-assert.md) Deklaration ist zur Kompilierzeit wirksam. Sie testet eine Softwareassertion, die durch einen vom Benutzer angegebenen ganzzahligen Ausdruck dargestellt wird, der in einen booleschen Wert konvertiert werden kann. Wenn der Ausdruck 0 (false) ergibt, gibt der Compiler die vom Benutzer angegebene Meldung aus, und die Kompilierung wird mit einem Fehler beendet.

   Die `static_assert`-Deklaration ist zum Debuggen von Vorlagen besonders nützlich, da Vorlagenargumente in den benutzerdefinierten Ausdruck eingeschlossen werden können.

- Das [ASSERT-Makro, _ASSERT _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) -Makro, ist zur Laufzeit wirksam. Es wertet einen vom Benutzer angegebenen Ausdruck aus, und wenn das Ergebnis null (0) ist, gibt das System eine Diagnosemeldung aus und schließt die Anwendung. Viele andere Makros, wie z. b.[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) und _ASSERTE, ähneln diesem Makro, geben aber unterschiedliche System definierte oder benutzerdefinierte Diagnosemeldungen aus.

## <a name="see-also"></a>Weitere Informationen

[#error-Direktive (C/C++)](../preprocessor/hash-error-directive-c-cpp.md)<br/>
[assert Macro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[_ASSERT-, _ASSERTE-, _ASSERT_EXPR-Makros](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)<br/>
[static_assert](../cpp/static-assert.md)<br/>
[_STATIC_ASSERT Macro](../c-runtime-library/reference/static-assert-macro.md)<br/>
[Vorlagen](../cpp/templates-cpp.md)
