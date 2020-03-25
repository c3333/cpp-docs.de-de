---
title: fwide
ms.date: 11/04/2016
api_name:
- fwide
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
- fwide
helpviewer_keywords:
- fwide function
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
ms.openlocfilehash: 652aee03bfb5504a51d74efb326cc7a3d7c28649
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171202"
---
# <a name="fwide"></a>fwide

Nicht implementiert

## <a name="syntax"></a>Syntax

```C
int fwide(
   FILE *stream,
   int mode;
);
```

### <a name="parameters"></a>Parameter

*stream*<br/>
Zeiger auf die **Datei** Struktur (ignoriert).

*mode*<br/>
Die neue Breite des Streams: positiv für Breitzeichen, negativ für Bytes, null, um unverändert zu lassen. (Dieser Wert wird ignoriert.)

## <a name="return-value"></a>Rückgabewert

Diese Funktion gibt zurzeit nur den- *Modus*zurück.

## <a name="remarks"></a>Bemerkungen

Die aktuelle Version dieser Funktion stimmt nicht mit dem Standard überein.

## <a name="requirements"></a>Requirements (Anforderungen)

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**fwide**|\<wchar.h>|

Weitere Informationen finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).
