---
title: Container (Modern C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 6e10b758-e928-4827-9c3f-86cafe54bf5b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8617bf35f3de0575c365f57ba78edbc8a79cc0e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="containers-modern-c"></a>Container (Modern C++)  
  
Standardmäßig verwenden [Vektor](../standard-library/vector-class.md) als der bevorzugte sequenziellen Container in C++. Dies entspricht dem `List<T>` in .NET-Sprachen.  
  
```cpp  
vector<string> apples;  
apples.push_back("Granny Smith");  
```  
  
Verwendung [Zuordnung](../standard-library/map-class.md) (nicht `unordered_map`) als standardmäßigen assoziativen Container. Verwendung [festgelegt](../standard-library/set-class.md), [mehrfachzuordnung](../standard-library/multimap-class.md), und [Multimenge](../standard-library/multiset-class.md) für degenerierte & mehrfachfälle.  
  
```cpp  
map<string, string> apple_color;  
// ...  
apple_color["Granny Smith"] = "Green";  
```  
  
Wenn eine Leistungsoptimierung erforderlich ist, erwägen Sie folgende Verwendungen:  
  
1.  Die [Array](../standard-library/array-class-stl.md) eingeben, wenn das Einbetten wichtig ist, z. B. einen Klassenmember ist.  
  
2.  Ungeordnete assoziative Container wie z. B. ["unordered_map"] ((.. /Standard-Library/Unordered-Map-Class.MD). Diese weisen Mehraufwand pro Element niedriger und Konstante zeitsuche, aber sie können schwieriger zu ordnungsgemäß und effizient zu verwenden.  
  
3.  Sortiert `vector`. Weitere Informationen finden Sie unter [Algorithmen](../cpp/algorithms-modern-cpp.md).  
  
Verwenden Sie keine Arrays im C-Stil. Verwenden Sie für ältere APIs, die Zugriff auf die Daten weiterleiten müssen, z. B. Methoden des Eigenschaftenaccessors `f(vec.data(), vec.size());` stattdessen.  
  
Weitere Informationen zu Containern finden Sie unter [Standard C++-Bibliothek-Container](../standard-library/stl-containers.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Willkommen zurück bei C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C++-Sprachreferenz](../cpp/cpp-language-reference.md)   
 [C++-Standardbibliothek](../standard-library/cpp-standard-library-reference.md)