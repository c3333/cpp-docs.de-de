---
title: _amsg_exit
ms.date: 11/04/2016
api_name:
- _amsg_exit
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
- _amsg_exit
helpviewer_keywords:
- _amsg_exit
ms.assetid: 146d4faf-d763-43a4-b264-12711196456b
ms.openlocfilehash: 31979a3181dc57644f1e6877277884e55cebf733
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170934"
---
# <a name="_amsg_exit"></a>_amsg_exit

Gibt eine angegebene Laufzeit-Fehlermeldung aus und schließt Ihre Anwendung mit dem Fehlercode 255.

## <a name="syntax"></a>Syntax

```cpp
void _amsg_exit ( int rterrnum );
```

### <a name="parameters"></a>Parameter

*rterrnum*<br/>
Die Identifikationsnummer einer systemdefinierten Laufzeit-Fehlermeldung.

## <a name="remarks"></a>Bemerkungen

Diese Funktion gibt für Konsolenanwendungen die Laufzeit-Fehlermeldung in **stderr** aus. Für Windows-Anwendungen zeigt sie die Meldung in einem Meldungsfeld an. Im Debugmodus haben Sie die Möglichkeit, den Debugger aufzurufen, bevor Sie die Anwendung beenden.

## <a name="requirements"></a>Requirements (Anforderungen)

|Routine|Erforderlicher Header|
|-------------|---------------------|
|_amsg_exit|internal.h|
