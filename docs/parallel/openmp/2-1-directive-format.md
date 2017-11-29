---
title: 2.1 Direktivenformat | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 918b6445-d35e-4176-9565-b045be941b4d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5760c4ccd3fcaf036f0d6d0aef09d29bbbaf8862
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="21-directive-format"></a>2.1 Anweisungsformat
Die Syntax für eine Direktive von OpenMP wird offiziell angegeben, indem die Grammatik in [Anhang C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md), informell wie folgt:  
  
```  
#pragma omp directive-name  [clause[ [,] clause]...] new-line  
```  
  
 Jede Direktive beginnt mit **#pragma Omp**, um potenzielle Konflikte mit anderen (nicht-OpenMP oder Hersteller Erweiterungen mit OpenMP) pragma-Direktiven mit den gleichen Namen zu reduzieren. Der Rest der Anweisung folgt die Konventionen der C- und C++-Standards für Compilerdirektiven. Insbesondere Leerraum genutzt werden vor und nach der  **#** , und manchmal Leerzeichen zum Trennen Sie die Wörter in einer Anweisung verwendet werden muss. Vorverarbeitungstoken nach der **#pragma Omp** makroersetzung unterliegen.  
  
 Direktiven sind Groß-/Kleinschreibung beachtet. Die Reihenfolge der Klauseln in Direktiven spielt keine. Klauseln auf Direktiven können wiederholt werden, unterliegen den oben angegebenen, in der Beschreibung der einzelnen Klauseln Einschränkungen bei Bedarf. Wenn *Variablenliste* wird in einer Klausel nur Variablen angegeben werden muss. Nur ein *Richtlinie-Name* pro Direktive kann angegeben werden.  Die folgende Anweisung ist z. B. nicht zulässig:  
  
```  
/* ERROR - multiple directive names not allowed */  
#pragma omp parallel barrier  
```  
  
 Eine OpenMP-Direktive gilt für höchstens eine nachfolgende-Anweisung, die einem strukturierten Block sein muss.