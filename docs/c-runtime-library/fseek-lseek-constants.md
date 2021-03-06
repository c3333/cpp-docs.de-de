---
title: fseek- und _lseek-Konstanten
ms.date: 11/04/2016
f1_keywords:
- SEEK_END
- SEEK_SET
- SEEK_CUR
helpviewer_keywords:
- SEEK_SET constant
- SEEK_END constant
- SEEK_CUR constant
ms.assetid: 9deeb13e-5aa3-4c33-80d8-721c80a4de9d
ms.openlocfilehash: 2e6cb2e0d781212f3b5e7758554507dfa438a716
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743369"
---
# <a name="fseek-lseek-constants"></a>fseek- und _lseek-Konstanten

## <a name="syntax"></a>Syntax

```
#include <stdio.h>
```

## <a name="remarks"></a>Anmerkungen

Das *origin*-Argument gibt die Ausgangsposition an und kann eine der folgenden Manifestkonstanten sein:

|Konstante|Bedeutung|
|--------------|-------------|
|`SEEK_END`|Ende der Datei|
|`SEEK_CUR`|Aktuelle Position des Dateizeigers|
|`SEEK_SET`|Anfang der Datei|

## <a name="see-also"></a>Siehe auch

[fseek, _fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)<br/>
[_lseek, _lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)<br/>
[Globale Konstanten](../c-runtime-library/global-constants.md)
