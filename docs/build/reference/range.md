---
title: -BEREICH | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /RANGE
dev_langs: C++
helpviewer_keywords:
- /RANGE dumpbin option
- -RANGE dumpbin option
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2558beae1a7bd689beba001f4637b1109b70faa5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="range"></a>/RANGE
Ändert die Ausgabe von Dumpbin bei Verwendung mit anderen Dumpbin-Optionen, z. B./RAWDATA oder/DISASM an.  
  
## <a name="syntax"></a>Syntax  
  
```  
/RANGE:vaMin[,vaMax]  
```  
  
## <a name="flags"></a>Flags  
 **vaMin**  
 Die virtuelle Adresse, an der Sie der Dumpbin beginnen soll.  
  
 **VaMax** (optional)  
 Die virtuelle Adresse, an der die Dumpbin-Operation beendet werden soll. Wenn nicht angegeben wird, geht die Dumpbin bis zum Ende der Datei.  
  
## <a name="remarks"></a>Hinweise  
 Um die virtuellen Adressen für ein Bild angezeigt wird, verwenden Sie die Zuordnungsdatei für das Bild (RVA + Basis), die **DISASM** oder **/Headers** -Option von Dumpbin oder im Disassemblyfenster in Visual Studio-Debugger.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel **/range** wird verwendet, um die Anzeige der Ändern der **DISASM** Option. In diesem Beispiel wird der Startwert wird als Dezimalzahl angegeben, und der Endwert als eine hexadezimale Zahl angegeben wird.  
  
```  
dumpbin /disasm /range:4219334,0x004061CD t.exe  
```  
  
## <a name="see-also"></a>Siehe auch  
 [DUMPBIN-Optionen](../../build/reference/dumpbin-options.md)