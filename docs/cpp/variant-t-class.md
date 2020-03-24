---
title: _variant_t-Klasse
ms.date: 11/04/2016
f1_keywords:
- _variant_t
helpviewer_keywords:
- _variant_t class [C++], operators
- _variant_t class
- _variant_t class [C++], member functions
- VARIANT object
- VARIANT object [C++], COM encapsulation
ms.assetid: 6a3cbd4e-0ae8-425e-b4cf-ca0df894c93f
ms.openlocfilehash: e11d31904fd8e54049f69ee4f6530d511c8c7f4e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187751"
---
# <a name="_variant_t-class"></a>_variant_t-Klasse

**Microsoft-spezifisch**

Ein **_variant_t** -Objekt kapselt den `VARIANT` Datentyp. Die-Klasse verwaltet die Zuordnung und Freigabe von Ressourcen und führt Funktionsaufrufe an `VariantInit` und `VariantClear` entsprechend aus.

### <a name="construction"></a>Bauwesen

|||
|-|-|
|[_variant_t](../cpp/variant-t-variant-t.md)|Erstellt ein **_variant_t** -Objekt.|

### <a name="operations"></a>Operationen (Operations)

|||
|-|-|
|[Anfügen](../cpp/variant-t-attach.md)|Fügt ein `VARIANT` Objekt an das **_variant_t** Objekt an.|
|[Clear](../cpp/variant-t-clear.md)|Löscht das gekapselte `VARIANT` Objekt.|
|[ChangeType](../cpp/variant-t-changetype.md)|Ändert den Typ des **_variant_t** Objekts in den angegeben `VARTYPE`.|
|[Trennen](../cpp/variant-t-detach.md)|Trennt das gekapselte `VARIANT`-Objekt von diesem **_variant_t** -Objekt.|
|[SetString](../cpp/variant-t-setstring.md)|Weist diesem **_variant_t** Objekt eine Zeichenfolge zu.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[Operator =](../cpp/variant-t-operator-equal.md)|Weist einem vorhandenen **_variant_t** -Objekt einen neuen Wert zu.|
|[Operator = =,! =](../cpp/variant-t-relational-operators.md)|Vergleicht zwei **_variant_t** Objekte auf Gleichheit oder Ungleichheit.|
|[Extraktoren](../cpp/variant-t-extractors.md)|Extrahieren Sie Daten aus dem gekapselten `VARIANT` Objekt.|

**Ende Microsoft-spezifisch**

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<comutil. h >

**Lib:** comsuppw. lib oder comsuppwd. lib (siehe [/Zc: wchar_t (wchar_t ist System eigener Typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) , um weitere Informationen zu erhalten)

## <a name="see-also"></a>Weitere Informationen

[Compilerklassen für COM-Unterstützung](../cpp/compiler-com-support-classes.md)
