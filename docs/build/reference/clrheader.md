---
title: -CLRHEADER | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /CLRHEADER
dev_langs: C++
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 699fa0e97236b1c5cf207e73dcbb39156bfbb130
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="clrheader"></a>/CLRHEADER
```  
/CLRHEADER file  
```  
  
## <a name="remarks"></a>Hinweise  
 Dabei gilt:  
  
 `file`  
 Eine Bilddatei mit erstellten ["/ CLR"](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="remarks"></a>Hinweise  
 CLRHEADER zeigt Informationen über die in jeder verwalteten Anwendung verwendet. Die Ausgabe zeigt den Speicherort und die Größe in Bytes, die .NET Header und die Abschnitte in der Kopfzeile an.  
  
 Nur die [/Headers](../../build/reference/headers.md) DUMPBIN-Option ist verfügbar für die Verwendung in den Dateien erstellt wird, mit der [/GL](../../build/reference/gl-whole-program-optimization.md) -Compileroption.  
  
 Beim CLRHEADER auf eine Datei verwendet wird, die mit "/ CLR" kompiliert wurde, ergibt sich eine **Clr-Header:** Abschnitt in der Dumpbin-Ausgabe.  Der Wert der **Flags** gibt an, welche Option "/ CLR" verwendet wurde:  
  
-   0 – "/ CLR" (Image darf nativen Code).  
  
-   1 – / CLR: safe (Abbildung ist MSIL nur auf einer beliebigen CLR-Plattform ausführen und möglicherweise überprüfbar).  
  
-   3 – / clr: pure (Image ist nur MSIL, jedoch nur zum Ausführen auf X86 Plattformen).  
  
 Sie können auch programmgesteuert überprüfen, wenn ein Bild für die common Language Runtime erstellt wurde.  Weitere Informationen finden Sie unter [wie: bestimmen, ob ein Bild systemeigen oder CLR ist](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md).  
  
 Die Compileroptionen **/clr:pure** und **/clr:safe** sind in Visual Studio 2015 veraltet.  
  
## <a name="see-also"></a>Siehe auch  
 [DUMPBIN-Optionen](../../build/reference/dumpbin-options.md)