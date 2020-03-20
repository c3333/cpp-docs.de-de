---
title: com::ptr
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr/com/com::ptr
helpviewer_keywords:
- com::ptr
ms.assetid: ee302e3c-8fed-4875-a372-2e55003718d3
ms.openlocfilehash: 993511142b72bd769fe8582b2650e5d020bd6ce2
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545858"
---
# <a name="comptr"></a>com::ptr

Ein Wrapper für ein COM-Objekt, das als Member einer CLR-Klasse verwendet werden kann. Der Wrapper automatisiert auch die Lebensdauer Verwaltung des COM-Objekts und gibt eigene Verweise auf das Objekt frei, wenn sein Dekonstruktor aufgerufen wird. Analog zur [CComPtr-Klasse](../atl/reference/ccomptr-class.md).

## <a name="syntax"></a>Syntax

```
#include <msclr\com\ptr.h>
```

## <a name="remarks"></a>Hinweise

[com::p TR-Klasse](../dotnet/com-ptr-class.md) ist in der Datei \<msclr\com\ptr.h > definiert.

## <a name="see-also"></a>Siehe auch

[C++-Standardbibliothek](../dotnet/cpp-support-library.md)
