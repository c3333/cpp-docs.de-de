---
title: '&lt;System_error&gt;-Funktionen'
ms.date: 03/15/2019
f1_keywords:
- system_error/std::generic_category
- system_error/std::make_error_code
- system_error/std::make_error_condition
- system_error/std::system_category
ms.assetid: 57d6f15f-f0b7-4e2f-80fe-31d3c320ee33
helpviewer_keywords:
- std::generic_category
- std::make_error_code
- std::make_error_condition
- std::system_category
ms.openlocfilehash: ab4d0d1ee810df8f719bba762262eb03bf899408
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876266"
---
# <a name="ltsystem_errorgt-functions"></a>&lt;System_error&gt;-Funktionen

## <a name="generic_category"></a>generic_category

Stellt die Kategorie für allgemeine Fehler dar.

```cpp
const error_category& generic_category() noexcept;
```

### <a name="remarks"></a>Bemerkungen

Das `generic_category`-Objekt ist eine Implementierung von [Error_category](../standard-library/error-category-class.md).

## <a name="is_error_code_enum_v"></a>is_error_code_enum_v

```cpp
template <class T> 
    inline constexpr bool is_error_code_enum_v = is_error_code_enum<T>::value;
```

## <a name="is_error_condition_enum_v"></a>is_error_condition_enum_v

```cpp
template <class T> 
    inline constexpr bool is_error_condition_enum_v = is_error_condition_enum<T>::value;
```

## <a name="make_error_code"></a>make_error_code

Erstellt ein Fehlercodeobjekt.

```cpp
error_code make_error_code(std::errc error) noexcept;
```

### <a name="parameters"></a>Parameter

*Fehler*\
Der `std::errc` Enumerationswert, der im Fehlercode Objekt gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

Das Fehlercodeobjekt.

### <a name="remarks"></a>Bemerkungen

## <a name="make_error_condition"></a>make_error_condition

Erstellt ein Fehlerzustandobjekt.

```cpp
error_condition make_error_condition(std::errc error) noexcept;
```

### <a name="parameters"></a>Parameter

*Fehler*\
Der `std::errc` Enumerationswert, der im Fehlercode Objekt gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

Das Fehlerzustandobjekt.

### <a name="remarks"></a>Bemerkungen

## <a name="system_category"></a>system_category

Stellt die Kategorie für Fehler dar, die von Low-Level-Systemüberläufen verursacht wurden.

```cpp
const error_category& system_category() noexcept;
```

### <a name="remarks"></a>Bemerkungen

Das `system_category`-Objekt ist eine Implementierung von [Error_category](../standard-library/error-category-class.md).
