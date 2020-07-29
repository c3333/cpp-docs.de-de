---
title: '&lt;string_view&gt;'
ms.date: 04/18/2019
helpviewer_keywords:
- string_view header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 13b6f5c63b9426fc4c31527f0d1ae8291d07807f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222211"
---
# <a name="ltstring_viewgt"></a>&lt;string_view&gt;

Definiert die Klassen Vorlage `basic_string_view` und verwandte Typen und Operatoren. (Erfordert die Compileroption [Std: c++ 17](../build/reference/std-specify-language-standard-version.md) oder höher.)

## <a name="syntax"></a>Syntax

```cpp
#include <string_view>
```

## <a name="remarks"></a>Bemerkungen

Die string_view Familie von Vorlagen Spezialisierungsmöglichkeiten bietet eine effiziente Möglichkeit, einen schreibgeschützten, Ausnahme sicheren, nicht besitzenden Handle an die Zeichendaten aller Zeichen folgen ähnlichen Objekte zu übergeben, wobei das erste Element der Sequenz an Position 0 (null) ist. Ein Funktionsparameter des Typs `string_view` (bei dem es sich um eine typedef für handelt `basic_string_view<char>` ) kann Argumente wie `std::string` , ** \* char**oder eine beliebige andere Zeichen folgen ähnliche Klasse von schmalen Zeichen annehmen, für die eine implizite Konvertierung in `string_view` definiert ist. Ebenso kann ein Parameter von `wstring_view` `u16string_view` oder `u32string_view` jeden beliebigen Zeichen Folgentyp akzeptieren, für den eine implizite Konvertierung definiert ist. Weitere Informationen finden Sie unter [basic_string_view-Klasse](../standard-library/basic-string-view-class.md).

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[string_view](../standard-library/string-view-typedefs.md#string_view)|Eine Spezialisierung der Klassen Vorlage `basic_string_view` mit Elementen des Typs **`char`** .|
|[wstring_view](../standard-library/string-view-typedefs.md#wstring_view)|Eine Spezialisierung der Klassen Vorlage `basic_string_view` mit Elementen des Typs **`wchar_t`** .|
|[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)|Eine Spezialisierung der Klassen Vorlage `basic_string_view` mit Elementen des Typs **`char16_t`** .|
|[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)|Eine Spezialisierung der Klassen Vorlage `basic_string_view` mit Elementen des Typs **`char32_t`** .|

### <a name="operators"></a>Operatoren

Die- \<string_view> Operatoren können- `string_view` Objekte mit Objekten von konvertierbaren Zeichen folgen Typen vergleichen.

|Operator|BESCHREIBUNG|
|-|-|
|[Operator! =](../standard-library/string-view-operators.md#op_neq)|Testet, ob das Objekt links vom Operator ungleich dem Objekt rechts vom Operator ist.|
|[Operator = =](../standard-library/string-view-operators.md#op_eq_eq)|Testet, ob das Objekt links vom Operator gleich dem Objekt rechts vom Operator ist.|
|[Operator<](../standard-library/string-view-operators.md#op_lt)|Testet, ob das Objekt links vom Operator kleiner als das Objekt auf der rechten Seite ist.|
|[Operator<=](../standard-library/string-view-operators.md#op_lt_eq)|Testet, ob das Objekt links vom Operator kleiner oder gleich dem Objekt auf der rechten Seite ist.|
|[Operator<\<](../standard-library/string-view-operators.md#op_lt_lt)|Eine Vorlagen Funktion, die ein-Objekt `string_view` in einen Ausgabestream einfügt.|
|[Operator>](../standard-library/string-view-operators.md#op_gt)|Testet, ob das Objekt links vom Operator größer als das Objekt auf der rechten Seite ist.|
|[Operator>=](../standard-library/string-view-operators.md#op_gt_eq)|Testet, ob das Objekt links vom Operator größer oder gleich dem Objekt auf der rechten Seite ist.|

### <a name="literals"></a>Literale

|Operator|BESCHREIBUNG|
|-|-|
|[SV](../standard-library/string-view-operators.md#op_sv)|Erstellt eine `string_view` , `wstring_view` , `u16string_view` oder, `u32string_view` abhängig vom Typ des Zeichenfolgenliterals, an das Sie angefügt wird.|

### <a name="classes"></a>Klassen

|Klasse|BESCHREIBUNG|
|-|-|
|[basic_string_view-Klasse](../standard-library/basic-string-view-class.md)|Eine Klassen Vorlage, die eine schreibgeschützte Ansicht in einer Sequenz beliebiger Zeichen ähnlicher Objekte bereitstellt.|
|[hash](string-view-hash.md)|Funktions Objekt, das einen Hashwert für eine string_view erzeugt.|

## <a name="requirements"></a>Requirements (Anforderungen)

- **Header:**\<string_view>

- **Namespace:** std

- **Compileroption:** Std: c++ 17 (oder höher)

## <a name="see-also"></a>Weitere Informationen

[Headerdateienreferenz](../standard-library/cpp-standard-library-header-files.md)
