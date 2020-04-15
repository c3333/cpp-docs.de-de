---
title: '&lt;codecvt&gt;-Enumerationen'
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: e67290d8de0b8251191c4a93b66b7e19a293ed61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371947"
---
# <a name="ltcodecvtgt-enums"></a>&lt;codecvt&gt;-Enumerationen

## <a name="codecvt_mode-enumeration"></a><a name="codecvt_mode"></a>codecvt_mode-Enumeration

Gibt Konfigurationsinformationen für [Gebietsschemafacets](../standard-library/locale-class.md) an.

```cpp
enum codecvt_mode {
    consume_header = 4,
    generate_header = 2,
    little_endian = 1
};
```

### <a name="remarks"></a>Bemerkungen

Die Enumeration definiert drei Konstanten, die Konfigurationsinformationen für die in [ \<codecvt>](../standard-library/codecvt.md)deklarierten Gebietsschema-Facetten bereitstellen. Die unterschiedlichen Werte lauten:

- `consume_header`, um eine Sequenz des ursprünglichen Headers zu verwenden, wenn eine Multibytesequenz gelesen wird, und um die Bytereihenfolge der nachfolgenden zu lesenden Multibytesequenz zu bestimmen

- `generate_header`, um eine Sequenz des ursprünglichen Headers zu generieren, wenn eine Multibytesequenz geschrieben wird, um die Bytereihenfolge der nachfolgenden zu schreibenden Multibytesequenz anzukündigen

- `little_endian`, um eine Multibytesequenz in der Little-Endian-Reihenfolge zu generieren (und nicht in der standardmäßigen Big-Endian-Reihenfolge)

Diese Konstanten können mit OR beliebig kombiniert werden.

## <a name="see-also"></a>Siehe auch

[\<codecvt>](../standard-library/codecvt.md)
