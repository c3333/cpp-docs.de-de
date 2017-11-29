---
title: ATL-Fenster Traits | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: window traits
ms.assetid: c90cf850-9e91-49da-9cf3-ad4efb30347d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6fc90c44fde4db119a8aa6dab097e9a7bd1c7f0f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="understanding-window-traits"></a>Grundlegendes zu Fenster Merkmale
Fenster Traits-Klassen bieten eine einfache Methode zum für die Erstellung eines ATL-Fenster-Objekts verwendeten Stile zu standardisieren. Fenster Merkmale werden als Vorlagenparameter durch akzeptiert [CWindowImpl](../atl/reference/cwindowimpl-class.md) und anderen ATL-Fensterklassen als Möglichkeit Fensterstile auf Klassenebene bereitzustellen.  
  
 Wenn der Ersteller einer Instanz Fenster Stile explizit im Aufruf bietet [erstellen](../atl/reference/cwindowimpl-class.md#create), verwenden Sie eine Traits-Klasse, um sicherzustellen, dass das Fenster immer noch mit den richtigen Stilen erstellt wird. Sie können auch sicher, dass für bestimmte Formate für alle Instanzen dieser Fensterklasse zugleich anderen Formaten-Instanzebene festgelegt werden sollen.  
  
## <a name="atl-window-traits-templates"></a>ATL-Fenster Traits-Vorlagen  
 ATL stellt zwei Fenster Traits Vorlagen, die Sie zum Zeitpunkt der Kompilierung mit ihren Vorlagenparametern Standardstile festlegen können.  
  
|Klasse|Beschreibung|  
|-----------|-----------------|  
|[CWinTraits](../atl/reference/cwintraits-class.md)|Wenn Standard Fensterstile bereitzustellen, die verwendet werden, wenn keine andere Stile im Aufruf angegeben werden sollen, verwenden Sie diese Vorlage **erstellen**. Die Stile, die zur Laufzeit haben Vorrang vor bereitgestellt wird, über die Stile, legen Sie auf die Kompilierungszeit an.|  
|[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)|Verwenden Sie diese Klasse, wenn Sie möchten Stile an, die für die Fensterklasse immer festgelegt werden müssen. Die Stile, die zur Laufzeit bereitgestellt werden mit den Stilen festgelegt, die zum Zeitpunkt der Kompilierung mit dem bitweisen OR-Operator kombiniert.|  
  
 Zusätzlich zu diesen Vorlagen ATL bietet eine Reihe von vordefinierten spezialisierungen der `CWinTraits` Vorlagen für häufig verwendete Parameterkombinationen Fensterstile. Finden Sie unter der [CWinTraits](../atl/reference/cwintraits-class.md) Referenzdokumentation für alle Details.  
  
## <a name="custom-window-traits"></a>Merkmale der benutzerdefinierten Fenster  
 In dem unwahrscheinlichen Fall, dass spezialisierenden eine der Vorlagen aus, die vom ATL nicht ausreichend und müssen Sie eigene trait-Klasse erstellen, müssen Sie nur eine Klasse erstellen, die zwei statische Funktionen implementiert: `GetWndStyle` und **GetWndStyleEx** :  
  
 [!code-cpp[NVC_ATL_Windowing#68](../atl/codesnippet/cpp/understanding-window-traits_1.h)]  
  
 Jede dieser Funktionen wird ein Style-Wert zur Laufzeit übergeben die sie verwenden können, um einen neuen Stilwert zu erzeugen. Wenn Ihre Merkmale Fensterklasse als Vorlagenargument für eine ATL-Fensterklasse verwendet wird, die Style-Werte, die für diese statische Funktionen übergeben werden alle von Ihnen gewünschten als stilargumente übergeben wurde [erstellen](../atl/reference/cwindowimpl-class.md#create).  
  
## <a name="see-also"></a>Siehe auch  
 [Fensterklassen](../atl/atl-window-classes.md)
