---
title: __if_not_exists-Anweisung | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __if_not_exists_cpp
dev_langs:
- C++
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 5eff74bd6405d7ec63b3cc8fbea968df984fddb8
ms.contentlocale: de-de
ms.lasthandoff: 09/25/2017

---
# <a name="ifnotexists-statement"></a>__if_not_exists-Anweisung
Die `__if_not_exists`-Anweisung testet, ob der angegebene Bezeichner vorhanden ist. Wenn der Bezeichner nicht vorhanden ist, wird der angegebene Anweisungsblock ausgeführt.  
  
## <a name="syntax"></a>Syntax  
  
```  
__if_not_exists ( identifier ) {   
statements  
};  
```  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`identifier`|Der Bezeichner, dessen Vorhandensein Sie überprüfen möchten.|  
|`statements`|Eine oder mehrere Anweisungen zum Ausführen von Wenn `identifier` ist nicht vorhanden.|  
  
## <a name="remarks"></a>Hinweise  
  
> [!CAUTION]
>  Um die zuverlässigsten Ergebnisse zu erzielen, verwenden Sie die `__if_not_exists`-Anweisung mit den folgenden Einschränkungen.  
  
-   Wenden Sie die `__if_not_exists`-Anweisung nur auf einfache Typen, nicht auf Vorlagen an.  
  
-   Wenden Sie die `__if_not_exists`-Anweisung auf Bezeichner innerhalb oder außerhalb einer Klasse an. Übernehmen Sie die `__if_not_exists`-Anweisung nicht für lokale Variablen.  
  
-   Verwenden Sie die `__if_not_exists`-Anweisung nur im Text einer Funktion. Außerhalb des Texts einer Funktion kann die `__if_not_exists`-Anweisung nur vollständig definierte Typen testen.  
  
-   Wenn Sie auf überladene Funktionen testen, können Sie nicht auf eine bestimmte Form der Überladung testen.  
  
 Die Ergänzung zu den `__if_not_exists` -Anweisung ist die [__if_exists](../cpp/if-exists-statement.md) Anweisung.  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel zur Verwendung von `__if_not_exists`, finden Sie unter [__if_exists-Anweisung](../cpp/if-exists-statement.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Auswahlanweisungen](../cpp/selection-statements-cpp.md)   
 [Stichwörter](../cpp/keywords-cpp.md)   
 [__if_exists-Anweisung](../cpp/if-exists-statement.md)