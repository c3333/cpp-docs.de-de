---
title: Math-Fehlerkonstanten | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _PLOSS
- _UNDERFLOW
- _TLOSS
- _SING
- _DOMAIN
- _OVERFLOW
dev_langs: C++
helpviewer_keywords:
- _TLOSS constant
- _SING constant
- PLOSS constant
- UNDERFLOW constant
- _UNDERFLOW constant
- _OVERFLOW constant
- DOMAIN constant
- OVERFLOW constant
- TLOSS constant
- SING constant
- _DOMAIN constant
- _PLOSS constant
- math error constants
ms.assetid: 4be933a6-674e-45a5-8ac9-090023542f5b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 003851227d56469436f7c75396803d80052dca15
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="math-error-constants"></a>Mathematische Fehlerkonstanten
## <a name="syntax"></a>Syntax  
  
```  
  
#include <math.h>  
  
```  
  
## <a name="remarks"></a>Hinweise  
 Die mathematischen Routinen der Laufzeitbibliothek können mathematische Fehlerkonstanten generieren.  
  
 Die im Folgenden beschriebenen Fehler entsprechen den Ausnahmetypen, die in MATH.H definiert sind, und werden von der `_matherr`-Funktion zurückgegeben, wenn ein mathematischer Fehler auftritt.  
  
|Konstante|Bedeutung|  
|--------------|-------------|  
|`_DOMAIN`|Das Argument für die Funktion befindet sich außerhalb der Domäne der Funktion.|  
|`_OVERFLOW`|Das Ergebnis ist zu groß, um im Rückgabetyp der Funktion dargestellt werden zu können.|  
|`_PLOSS`|Ein teilweiser Signifikanzverlust ist aufgetreten.|  
|`_SING`|Argumentsingularität: Das Argument für die Funktion enthält einen ungültigen Wert. (Beispiel: Es wird ein Wert von 0 an eine Funktion übergeben, die einen Wert ungleich null erfordert.)|  
|`_TLOSS`|Ein Verlust der gesamten Signifikanz ist aufgetreten.|  
|`_UNDERFLOW`|Das Ergebnis ist zu klein, um dargestellt werden zu können.|  
  
## <a name="see-also"></a>Siehe auch  
 [_matherr](../c-runtime-library/reference/matherr.md)   
 [Globale Konstanten](../c-runtime-library/global-constants.md)