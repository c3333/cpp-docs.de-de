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
ms.openlocfilehash: 3ef89c6f6742d528c427c49fd2a62d8820625e79
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190377"
---
# <a name="_bstr_t-class"></a>_bstr_t-Klasse

**Microsoft-spezifisch**

Ein `_bstr_t`-Objekt kapselt den [BSTR-Datentyp](/previous-versions/windows/desktop/automat/bstr). Die-Klasse verwaltet die Zuordnung und Aufhebung der Zuordnung von Ressourcen über Funktionsaufrufe von `SysAllocString` und `SysFreeString` und anderen `BSTR` APIs, wenn dies angebracht ist. Die **_bstr_t** -Klasse verwendet die Verweis Zählung, um übermäßig mehr Aufwand zu vermeiden.

### <a name="construction"></a>Bauwesen

|||
|-|-|
|[_bstr_t](../cpp/bstr-t-bstr-t.md)|Erstellt ein `_bstr_t`-Objekt.|

### <a name="operations"></a>Operationen (Operations)

|||
|-|-|
|[Assign](../cpp/bstr-t-assign.md)|Kopiert ein `BSTR` in das `BSTR`, das von einem `_bstr_t` umschlossen wird.|
|[Anfügen](../cpp/bstr-t-attach.md)|Verknüpft einen `_bstr_t`-Wrapper mit einem `BSTR`.|
|[copy](../cpp/bstr-t-copy.md)|Erstellt eine Kopie des gekapselten `BSTR`.|
|[Trennen](../cpp/bstr-t-detach.md)|Gibt `BSTR` zurück, das von `_bstr_t` umschlossen ist, und trennt `BSTR` von `_bstr_t`.|
|[GetAddress](../cpp/bstr-t-getaddress.md)|Zeigt auf den `BSTR`, der von einem `_bstr_t` umschlossen ist.|
|[GetBSTR](../cpp/bstr-t-getbstr.md)|Zeigt auf den Anfang des `BSTR`, das vom `_bstr_t` umschlossen ist.|
|[length](../cpp/bstr-t-length.md)|Gibt die Anzahl von Zeichen in `_bstr_t` zurück.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[Operator =](../cpp/bstr-t-operator-equal.md)|Weist einem vorhandenen `_bstr_t`-Objekt einen neuen Wert zu.|
|[Operator + =](../cpp/bstr-t-operator-add-equal-plus.md)|Fügt Zeichen an das Ende des `_bstr_t`-Objekts an.|
|[Operator +](../cpp/bstr-t-operator-add-equal-plus.md)|Verkettet zwei Zeichenfolgen.|
|[Operator !](../cpp/bstr-t-operator-logical-not.md)|Prüft, ob der gekapselte `BSTR` eine NULL-Zeichenfolge ist|
|[Operator = =,! =, \<>, \<=, > =](../cpp/bstr-t-relational-operators.md)|Vergleicht zwei `_bstr_t`-Objekte.|
|[Operator wchar_t * &#124; char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|Extrahiert die Zeiger auf das gekapselten Unicode- oder Mehrbyte-`BSTR`-Objekt.|

**Ende Microsoft-spezifisch**

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<comutil. h >

**Lib:** comsuppw. lib oder comsuppwd. lib (siehe [/Zc: wchar_t (wchar_t ist System eigener Typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) , um weitere Informationen zu erhalten)

## <a name="see-also"></a>Weitere Informationen

[Compilerklassen für COM-Unterstützung](../cpp/compiler-com-support-classes.md)
