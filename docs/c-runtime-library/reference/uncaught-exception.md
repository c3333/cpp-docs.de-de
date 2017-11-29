---
title: __uncaught_exception | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- __uncaught_exception
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
apitype: DLLExport
f1_keywords:
- __uncaught_exception
dev_langs:
- C++
helpviewer_keywords:
- __uncaught_exception
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
caps.latest.revision: 2
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 2b43a6b08087dcaeeda7959eaadbee9c250f4de9
ms.contentlocale: de-de
ms.lasthandoff: 10/09/2017

---
# <a name="uncaughtexception"></a>__uncaught_exception
Gibt an, ob eine oder mehrere Ausnahmen ausgelöst, aber noch nicht durch den entsprechenden `catch`-Block einer [try-catch](../../cpp/try-throw-and-catch-statements-cpp.md)-Anweisung bearbeitet wurden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
bool __uncaught_exception(  
   );  
```  
  
## <a name="return-value"></a>Rückgabewert  
 `true` ab dem Zeitpunkt, an dem eine Ausnahme in einem `try`-Block ausgelöst und bis der passende `catch`-Block initialisiert wurde, andernfalls `false`.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="requirements"></a>Anforderungen  
  
|Routine|Erforderlicher Header|  
|-------------|---------------------|  
|__uncaught_exception|eh.h|  
  
## <a name="see-also"></a>Siehe auch  
 [try, throw, and catch Statements (C++) (try-, throw- und catch-Anweisungen (C++))](../../cpp/try-throw-and-catch-statements-cpp.md)