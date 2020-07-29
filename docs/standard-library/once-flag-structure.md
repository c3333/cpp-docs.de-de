---
title: once_flag-Struktur
ms.date: 09/17/2018
f1_keywords:
- mutex/std::once_flag
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
ms.openlocfilehash: 55c3f90f72857a4e4cd3f9075ce5bae10e14d218
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87202726"
---
# <a name="once_flag-structure"></a>once_flag-Struktur

Stellt eine dar **`struct`** , die mit der Vorlagen [call_once](../standard-library/mutex-functions.md#call_once) Funktion verwendet wird, um sicherzustellen, dass der Initialisierungs Code nur einmal aufgerufen wird, auch wenn mehrere Ausführungs Threads vorhanden sind.

## <a name="syntax"></a>Syntax

Struktur once_flag {constexpr once_flag () noaußer;};

## <a name="remarks"></a>Bemerkungen

`once_flag` **`struct`** Verfügt über nur einen Standardkonstruktor.

Objekte vom Typ `once_flag` können erstellt, aber nicht kopiert werden.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<mutex>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
