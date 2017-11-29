---
title: Compilerfehler C2241 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2241
dev_langs: C++
helpviewer_keywords: C2241
ms.assetid: 2f4e2c2c-b95c-4afe-bbe0-4214cd39d140
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0625c4682ff44904ce166d370ec797c1d147ad02
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2241"></a>Compilerfehler C2241
'Bezeichner': Memberzugriff ist eingeschränkt.  
  
 Der Code versucht, auf einen privaten oder geschützten Member zuzugreifen.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>So beheben Sie den Fehler (unterschiedliche Lösungsmöglichkeiten)  
  
1.  Ändern Sie die Zugriffsebene des Members.  
  
2.  Deklarieren Sie den Member als `friend` der zugreifenden Funktion.