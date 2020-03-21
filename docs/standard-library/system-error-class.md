---
title: system_error-Klasse
ms.date: 11/04/2016
f1_keywords:
- system_error/std::system_error
helpviewer_keywords:
- system_error class
ms.assetid: 2eeaacbb-8a4a-4ad7-943a-997901a77f32
ms.openlocfilehash: 7a18d2f9f229a62a539be072870e38a990677636
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076362"
---
# <a name="system_error-class"></a>system_error-Klasse

Stellt die Basisklasse für alle Ausnahmen dar, die ausgelöst werden, um einen Systemfehler auf niedriger Ebene zu melden.

## <a name="syntax"></a>Syntax

```cpp
class system_error : public runtime_error {
    explicit system_error(error_code _Errcode, const string& _Message = "");
    system_error(error_code _Errcode, const char *_Message);
    system_error(error_code::value_type _Errval, const error_category& _Errcat, const string& _Message);
    system_error(error_code::value_type _Errval, const error_category& _Errcat, const char *_Message);

    const error_code& code() const throw();
    const char* what() const noexcept override;
};
```

## <a name="remarks"></a>Bemerkungen

Der von `what` in der Klasse [exception](../standard-library/exception-class.md) zurückgegebene Wert wird auf der Grundlage von `_Message` und dem gespeicherten Objekt vom Typ [error_code](../standard-library/error-code-class.md) (`code` oder `error_code(_Errval, _Errcat)`) erstellt.

Die Memberfunktion `code` gibt das gespeicherte [error_code](../standard-library/error-code-class.md)-Objekt zurück.
