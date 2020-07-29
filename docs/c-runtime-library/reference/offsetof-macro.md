---
title: offsetof-Makro
ms.date: 11/04/2016
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- offsetof
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
ms.openlocfilehash: ee6d5e56bb9f41a842e53984f754c7c07d58a125
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213501"
---
# <a name="offsetof-macro"></a>offsetof-Makro

Ruft den Offset eines Elements vom Anfang seiner übergeordneten Struktur ab.

## <a name="syntax"></a>Syntax

```C
size_t offsetof(
   structName,
   memberName
);
```

### <a name="parameters"></a>Parameter

*structName*<br/>
Der Name der übergeordneten Datenstruktur.

*Membername*<br/>
Der Name des Elements in der übergeordneten Datenstruktur, für das der Offset bestimmt werden soll.

## <a name="return-value"></a>Rückgabewert

**offsetof** gibt den Offset des angegebenen Elements vom Anfang seiner übergeordneten Datenstruktur in Bytes zurück. Ist für Bitfelder nicht definiert.

## <a name="remarks"></a>Bemerkungen

Das **offsetof** -Makro gibt den Offset in Bytes des *Mitgliedsnamens* von dem Anfang der durch *structname* angegebenen Struktur als Wert des Typs **size_t**zurück. Sie können Typen mit dem- **`struct`** Schlüsselwort angeben.

> [!NOTE]
> **offsetof** ist keine Funktion und kann nicht mit einem C-Prototyp beschrieben werden.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**offsetof**|\<stddef.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Weitere Informationen

[Speicher Belegung](../../c-runtime-library/memory-allocation.md)<br/>
