---
title: uuid (C++)
ms.date: 11/04/2016
f1_keywords:
- uuid_cpp
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
ms.openlocfilehash: 09e40d38382bea0f902fda03d15d24e0cf1a627d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187803"
---
# <a name="uuid-c"></a>uuid (C++)

**Microsoft-spezifisch**

Der Compiler fügt eine GUID an eine Klasse oder Struktur an, die deklariert oder definiert wurde (nur vollständige COM-Objekt Definitionen) mit dem **UUID** -Attribut.

## <a name="syntax"></a>Syntax

```
__declspec( uuid("ComObjectGUID") ) declarator
```

## <a name="remarks"></a>Bemerkungen

Das **UUID** -Attribut nimmt eine Zeichenfolge als Argument an. Diese Zeichenfolge benennt eine GUID im normalen Registrierungs Format mit oder ohne **{}** -Trennzeichen. Beispiel:

```cpp
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;
```

Dieses Attribut kann in einer Neudeklaration angewendet werden. Dies ermöglicht es den Systemheadern, die Definitionen der Schnittstellen wie `IUnknown`bereitzustellen, und die Neudeklaration in einem anderen Header (z. b. \<comdef. h >), um die GUID bereitzustellen.

Das Schlüsselwort [__uuidof](../cpp/uuidof-operator.md) kann angewendet werden, um die Konstante GUID abzurufen, die an einen benutzerdefinierten Typ angefügt ist.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[__declspec](../cpp/declspec.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
