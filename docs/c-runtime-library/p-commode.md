---
title: __p__commode
ms.date: 4/2/2020
api_name:
- __p__commode
- _o___p__commode
api_location:
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__commode
helpviewer_keywords:
- __p__commode
ms.assetid: 4380acb8-e3e4-409c-a60f-6205ac5189ce
ms.openlocfilehash: fa589c1972d27854e3f794d8283f49d9db5d053a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349309"
---
# <a name="__p__commode"></a>__p__commode

Verweist auf die globale Variable `_commode`, die den Standard *Datei-Commit-Modus* für E/A-Dateivorgänge angibt.

## <a name="syntax"></a>Syntax

```cpp
int * __p__commode(
   );
```

## <a name="return-value"></a>Rückgabewert

Zeiger auf die globale Variable `_commode`.

## <a name="remarks"></a>Bemerkungen

Die `__p__commode`-Funktion steht nur für die interne Verwendung zur Verfügung und sollte nicht vom Benutzercode aufgerufen werden.

Der Datei-Commit-Modus gibt an, wenn wichtige Daten auf den Datenträger geschrieben werden. Weitere Informationen finden Sie unter [fflush](../c-runtime-library/reference/fflush.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|__p\__commode|internal.h|
