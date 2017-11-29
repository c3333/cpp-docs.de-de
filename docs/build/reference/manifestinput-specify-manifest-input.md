---
title: -MANIFESTINPUT (angeben Manifesteingabedatei) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a32eb8c65e14684b818341121714ce0359f6521a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (Angeben einer Manifesteingabedatei)
Gibt eine Manifesteingabedatei an, die dem Manifest hinzugefügt wird, das im Image eingebettet ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
/MANIFESTINPUT:filename  
```  
  
#### <a name="parameters"></a>Parameter  
 `filename`  
 Die Manifestdatei, die dem eingebetteten Manifest hinzuzufügen ist.  
  
## <a name="remarks"></a>Hinweise  
 Die **/MANIFESTINPUT** -Option gibt den Pfad einer Eingabedatei zum Erstellen des eingebetteten Manifests in einem ausführbaren Image verwendet. Wenn Sie mehrere Manifesteingabedateien haben, verwenden Sie den Schalter mehrfach, einmal für jede Eingabedatei. Die Manifesteingabedateien werden zusammengeführt, um das eingebettete Manifest zu erstellen. Diese Option erfordert das **/MANIFEST: EMBED** Option.  
  
 Die Option kann nicht direkt in [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] festgelegt werden. Verwenden Sie stattdessen die **zusätzliche Manifestdateien** -Eigenschaft des Projekts an zusätzliche Manifestdateien enthalten. Weitere Informationen finden Sie unter [Eingabe und Ausgabe, Manifesttool, Konfigurationseigenschaften, \<Projectname > Property Pages Dialog Box](../../ide/input-and-output-manifest-tool.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Festlegen von Linkeroptionen](../../build/reference/setting-linker-options.md)   
 [Linkeroptionen](../../build/reference/linker-options.md)