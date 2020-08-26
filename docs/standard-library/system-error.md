---
title: '&lt;system_error&gt;'
ms.date: 03/15/2019
f1_keywords:
- <system_error>
- system_error
helpviewer_keywords:
- system_error header
ms.assetid: 5e046c6e-48d9-4740-8c8a-05f3727c1215
ms.openlocfilehash: 18df18379fbee8271ba5cf851b04210f1dfddf57
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841882"
---
# <a name="ltsystem_errorgt"></a>&lt;system_error&gt;

Schließen Sie den \<system_error> zum Definieren der Ausnahmeklasse `system_error` und zugehörige Vorlagen für die Verarbeitung von Low-Level-Systemfehlern ein.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<system_error>

**Namespace:** std

## <a name="members"></a>Member

### <a name="objects"></a>Objekte

|Name|Beschreibung|
|-|-|
|[generic_category](../standard-library/system-error-functions.md#generic_category)|Stellt die Kategorie für allgemeine Fehler dar.|
|[is_error_code_enum_v](../standard-library/system-error-functions.md#is_error_code_enum_v)||
|[is_error_condition_enum_v](../standard-library/system-error-functions.md#is_error_condition_enum_v)||
|[system_category](../standard-library/system-error-functions.md#system_category)|Stellt die Kategorie für Fehler dar, die von Low-Level-Systemüberläufen verursacht wurden.|

### <a name="functions"></a>Functions

|Name|Beschreibung|
|-|-|
|[make_error_code](../standard-library/system-error-functions.md#make_error_code)|Sie erstellt ein `error_code`-Objekt.|
|[make_error_condition](../standard-library/system-error-functions.md#make_error_condition)|Sie erstellt ein `error_condition`-Objekt.|

### <a name="operators"></a>Operatoren

|Name|Beschreibung|
|-|-|
|[Operator = =](../standard-library/system-error-operators.md#op_eq_eq)|Testet, ob das Objekt links vom Operator gleich dem Objekt rechts vom Operator ist.|
|[Operator! =](../standard-library/system-error-operators.md#op_neq)|Testet, ob das Objekt links vom Operator ungleich dem Objekt rechts vom Operator ist.|
|[Operator<](../standard-library/system-error-operators.md#op_lt)|Testet, ob ein Objekt kleiner ist als das Objekt, das für den Vergleich übergeben wurde.|
|[Operator<<](../standard-library/system-error-operators.md#op_ostream)||

### <a name="enums"></a>Enumerationen

|Name|Beschreibung|
|-|-|
|[errc](../standard-library/system-error-enums.md#errc)|Gibt symbolische Namen für alle Fehlercode Makros an, die von POSIX in definiert werden `<errno.h>` .|

### <a name="classes-and-structs"></a>Klassen und Strukturen

|Name|Beschreibung|
|-|-|
|[error_category](../standard-library/error-category-class.md)|Stellt die abstrakte, allgemeine Basis für Objekte dar, die eine Fehlercodekategorie beschreibt.|
|[error_code](../standard-library/error-code-class.md)|Stellt Low-Level-Systemfehler dar, die von der Implementierung abhängen.|
|[error_condition](../standard-library/error-condition-class.md)|Stellt benutzerdefinierte Fehlercodes dar.|
|[hash](../standard-library/hash-structure.md#system_error)||
|[is_error_code_enum](../standard-library/is-error-code-enum-class.md)|Stellt ein Typprädikat dar, das auf die [error_code-Klasse](../standard-library/error-code-class.md)-Enumeration testet.|
|[is_error_condition_enum](../standard-library/is-error-condition-enum-class.md)|Stellt ein Typprädikat dar, das auf die [error_codition-Klasse](../standard-library/error-condition-class.md)-Enumeration testet.|
|[system_error](../standard-library/system-error-class.md)|Eine Basisklasse für alle Ausnahmen, die ausgelöst werden, um einen Low-Level-Systemüberlauf zu melden.|

## <a name="see-also"></a>Weitere Informationen

[Headerdateienreferenz](../standard-library/cpp-standard-library-header-files.md)
