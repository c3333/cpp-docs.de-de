---
title: _set_app_type
ms.date: 4/2/2020
api_name:
- _set_app_type
- _o__set_app_type
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
ms.openlocfilehash: 9791cff55ccd55c32d124ab89cc43ab54c0f9c69
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360975"
---
# <a name="_set_app_type"></a>_set_app_type

Eine beim Start verwendete interne Funktion, die die CRT mitteilen soll, ob die App eine Konsolen-App oder eine GUI-Anwendung ist.

## <a name="syntax"></a>Syntax

```cpp
typedef enum _crt_app_type
{
    _crt_unknown_app,
    _crt_console_app,
    _crt_gui_app
} _crt_app_type;

void __cdecl _set_app_type(
    _crt_app_type appType
    );
```

## <a name="parameters"></a>Parameter

*appType*<br/>
Ein Wert, der den Anwendungstyp angibt. Mögliche Werte:

|Wert|BESCHREIBUNG|
|----------------|-----------------|
|_crt_unknown_app|Unbekannter Anwendungstyp.|
|_crt_console_app|(Befehlszeilen)-Konsolenanwendung.|
|_crt_gui_app|GUI-Anwendung (in Windows).|

## <a name="remarks"></a>Bemerkungen

In der Regel müssen Sie diese Funktion nicht aufrufen. Sie ist Teil des C-Laufzeitstartcodes, der ausgeführt wird, bevor `main` in Ihrer Anwendung aufgerufen wird.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|_set_app_type|process.h|
