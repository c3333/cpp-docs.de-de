---
title: Makefile-Beispiel | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 8343ce71-5556-4ae0-8d1e-7efd82673070
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 845c1c5d816b1553ed63a3c2d520c5489ecffeea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="sample-makefile"></a>Beispielmakefile
Dieses Thema enthält ein Beispielmakefile.  
  
## <a name="sample"></a>Beispiel  
  
### <a name="code"></a>Code  
  
```  
# Sample makefile  
  
!include <win32.mak>  
  
all: simple.exe challeng.exe  
  
.c.obj:  
  $(cc) $(cdebug) $(cflags) $(cvars) $*.c  
  
simple.exe: simple.obj  
  $(link) $(ldebug) $(conflags) -out:simple.exe simple.obj $(conlibs) lsapi32.lib  
  
challeng.exe: challeng.obj md4c.obj  
  $(link) $(ldebug) $(conflags) -out:challeng.exe $** $(conlibs) lsapi32.lib  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Inhalt eines Makefiles](../build/contents-of-a-makefile.md)