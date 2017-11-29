---
title: C-Operatoren (additiv) | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- usual arithmetic conversions
- operators [C], addition
- + operator, additive operators
- additive operators
- arithmetic operators [C++], additive operators
ms.assetid: bb8ac205-b061-41fc-8dd4-dab87c8b900c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d5d41afccc7514c4e6469038b4f592890f9f355f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="c-additive-operators"></a>C-Operatoren (additiv)
Die additiven Operatoren führen Additionen (**+**) und Subtraktionen (**-**) aus.  
  
## <a name="syntax"></a>Syntax  
 *additive-expression*:  
 *multiplicative-expression*  
  
 *additive-expression*  **+**  *multiplicative-expression*  
  
 *additive-expression*  **-**  *multiplicative-expression*  
  
> [!NOTE]
>  Obwohl die Syntax für *additive-expression* auch *multiplicative-expression* enthält, heißt das nicht, dass Ausdrücke erforderlich sind, die Multiplikation verwenden. In der [Zusammenfassung der C-Sprachsyntax](../c-language/c-language-syntax-summary.md) finden Sie weitere Informationen über die Syntax für *multiplicative-expression*, *cast-expression* und *unary-expression*.  
  
 Die Operanden können Ganzzahl- oder Gleitkommawerte sein. Einige Additionsvorgänge können auch auf Zeigerwerten ausgeführt werden, wie in der Erläuterung für die einzelnen Operatoren dargelegt wird.  
  
 Additive Operatoren führen die üblichen arithmetischen Konvertierungen in Operanden vom Typ "integral" oder "floating" aus. Der Ergebnistyp ist der Typ der Operanden nach der Konvertierung. Da Konvertierungen, die von den Addition-Operatoren ausgeführt werden, keine Überlauf- oder Unterlaufbedingungen vorsehen, gehen Informationen möglicherweise verloren, wenn das Ergebnis eines Additionsvorgangs nach der Konvertierung nicht im Typ der Operanden dargestellt werden kann.  
  
## <a name="see-also"></a>Siehe auch  
 [Additive Operatoren: + und -](../cpp/additive-operators-plus-and.md)