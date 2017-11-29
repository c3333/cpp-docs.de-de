---
title: _set_doserrno | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_doserrno
apilocation:
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_doserrno
- set_doserrno
dev_langs: C++
helpviewer_keywords:
- _set_doserrno function
- doserrno global variable
- set_doserrno function
- _doserrno global variable
ms.assetid: 8686c159-3797-4705-a53e-7457869ca6f3
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 63824d9a9bd9e05d184656f641dca52891c7f0cd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="setdoserrno"></a>_set_doserrno
Legt den Wert der globalen Variable [_doserrno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
errno_t _set_doserrno(   
   int value   
);  
```  
  
#### <a name="parameters"></a>Parameter  
 [in] `value`  
 Der neue Wert von `_doserrno`.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt 0 zurück, wenn erfolgreich.  
  
## <a name="remarks"></a>Hinweise  
 Mögliche Werte sind in Errno.h definiert.  
  
## <a name="requirements"></a>Anforderungen  
  
|Routine|Erforderlicher Header|Optionaler Header|  
|-------------|---------------------|---------------------|  
|`_set_doserrno`|\<stdlib.h>|\<errno.h>|  
  
 Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md) in der Einführung.  
  
## <a name="see-also"></a>Siehe auch  
 [_get_doserrno](../../c-runtime-library/reference/get-doserrno.md)   
 [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)