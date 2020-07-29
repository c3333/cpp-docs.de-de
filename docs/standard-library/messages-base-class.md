---
title: messages_base-Klasse
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages_base
helpviewer_keywords:
- messages_base class
ms.assetid: 9aad38c6-4c13-445d-b096-364bd0836efb
ms.openlocfilehash: b0fe7d66842fb77c6fd03f62b012babcbc9f7f3a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215646"
---
# <a name="messages_base-class"></a>messages_base-Klasse

Die-Basisklasse beschreibt einen- **`int`** Typ für den Katalog von Meldungen.

## <a name="syntax"></a>Syntax

```cpp
struct messages_base : locale::facet {
    typedef int catalog;
    explicit messages_base(size_t _Refs = 0)
};
```

## <a name="remarks"></a>Bemerkungen

Der typkatalog ist ein Synonym für **`int`** den Typ, der die möglichen Rückgabewerte aus "Messages:: [Do_open](../standard-library/messages-class.md#do_open)" beschreibt.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<locale>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
