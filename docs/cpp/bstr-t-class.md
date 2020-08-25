---
title: _bstr_t-Klasse
ms.date: 11/04/2016
f1_keywords:
- _bstr_t
helpviewer_keywords:
- BSTR object
- _bstr_t class
- BSTR object [C++], COM encapsulation
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
ms.openlocfilehash: f521681da10eeda3b8024b0865d5164021296353
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838710"
---
# <a name="_bstr_t-class"></a>_bstr_t-Klasse

**Microsoft-spezifisch**

Ein- `_bstr_t` Objekt kapselt den [BSTR-Datentyp](/previous-versions/windows/desktop/automat/bstr). Die-Klasse verwaltet die Zuordnung und Freigabe von Ressourcen durch Funktionsaufrufe von `SysAllocString` und `SysFreeString` und anderen `BSTR` APIs, wenn dies angebracht ist. Die **_bstr_t** -Klasse verwendet die Verweis Zählung, um übermäßig mehr Aufwand zu vermeiden.

### <a name="construction"></a>Bauwesen

| Konstruktor | BESCHREIBUNG |
|--|--|
| [_bstr_t](../cpp/bstr-t-bstr-t.md) | Erstellt ein `_bstr_t`-Objekt. |

### <a name="operations"></a>Operationen (Operations)

| Funktion | Beschreibung |
|--|--|
| [Assign](../cpp/bstr-t-assign.md) | Kopiert ein `BSTR` in das `BSTR`, das von einem `_bstr_t` umschlossen wird. |
| [Anfügen](../cpp/bstr-t-attach.md) | Verknüpft einen `_bstr_t`-Wrapper mit einem `BSTR`. |
| [copy](../cpp/bstr-t-copy.md) | Erstellt eine Kopie des gekapselten `BSTR`. |
| [Trennen](../cpp/bstr-t-detach.md) | Gibt `BSTR` zurück, das von `_bstr_t` umschlossen ist, und trennt `BSTR` von `_bstr_t`. |
| [GetAddress](../cpp/bstr-t-getaddress.md) | Zeigt auf den `BSTR`, der von einem `_bstr_t` umschlossen ist. |
| [GetBSTR](../cpp/bstr-t-getbstr.md) | Zeigt auf den Anfang des `BSTR`, das vom `_bstr_t` umschlossen ist. |
| [length](../cpp/bstr-t-length.md) | Gibt die Anzahl von Zeichen in `_bstr_t` zurück. |

### <a name="operators"></a>Operatoren

| Operator | Beschreibung |
|--|--|
| [Operator =](../cpp/bstr-t-operator-equal.md) | Weist einem vorhandenen `_bstr_t`-Objekt einen neuen Wert zu. |
| [Operator + =](../cpp/bstr-t-operator-add-equal-plus.md) | Fügt Zeichen an das Ende des `_bstr_t`-Objekts an. |
| [Operator +](../cpp/bstr-t-operator-add-equal-plus.md) | Verkettet zwei Zeichenfolgen. |
| [KOM!](../cpp/bstr-t-operator-logical-not.md) | Überprüft, ob das gekapselt `BSTR` eine NULL-Zeichenfolge ist. |
| [Operator = =,! =, \<, > , \<=, >=](../cpp/bstr-t-relational-operators.md) | Vergleicht zwei `_bstr_t`-Objekte. |
| [Operator wchar_t * &#124; Char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md) | Extrahiert die Zeiger auf das gekapselten Unicode- oder Mehrbyte-`BSTR`-Objekt. |

**Ende Microsoft-spezifisch**

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<comutil.h>

**Lib:** comsuppw. lib oder comsuppwd. lib (siehe [/Zc: wchar_t (wchar_t ist System eigener Typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) , um weitere Informationen zu erhalten)

## <a name="see-also"></a>Weitere Informationen

[Compiler-com-Unterstützungs Klassen](../cpp/compiler-com-support-classes.md)
