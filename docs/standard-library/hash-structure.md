---
title: hash-Struktur
ms.date: 11/04/2016
f1_keywords:
- typeindex/std::hash
ms.assetid: e5a41202-ef3b-45d0-b3a7-4c2dbdc0487a
ms.openlocfilehash: 4f73d1bfe7f3370d76b39b95f740a4d3a759b908
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876268"
---
# <a name="hash-structure"></a>hash-Struktur

Die Klassen Vorlage definiert Ihre Methode als Rückgabe `val.hash_code()`. Die Methode definiert eine Hashfunktion, die verwendet wird, um einer Verteilung von Indexwerten Werte des Typs [type_index](../standard-library/type-index-class.md) zuzuordnen.

## <a name="syntax"></a>Syntax

```cpp
template <> struct hash<type_index>
: public unary_function<type_index, size_t>
{ // hashes a typeinfo object
    size_t operator()(type_index val) const;
};
```

## <a name="specialized-types"></a>Spezialisierte Typen

### <a name="system_error"></a>\<System_Error >

```cpp
template <class T> struct hash;
template <> struct hash<error_code>;
template <> struct hash<error_condition>;
```

## <a name="see-also"></a>Weitere Informationen

[\<typeindex>](../standard-library/typeindex.md)
