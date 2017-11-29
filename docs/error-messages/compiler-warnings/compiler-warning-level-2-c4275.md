---
title: Compilerwarnung (Stufe 2) C4275 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4275
dev_langs:
- C++
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: f9ecbe931c14cfde1d48438bdb76f70452e324d3
ms.contentlocale: de-de
ms.lasthandoff: 04/01/2017

---
# <a name="compiler-warning-level-2-c4275"></a>Compilerwarnung (Stufe 2) C4275
nicht - DLL-Schnittstelle LocalizedText 'Bezeichner' als Basisklasse verwendet für DLL-Schnittstelle LocalizedText "Bezeichner"  
  
 Eine exportierte Klasse wurde von einer Klasse abgeleitet, die nicht exportiert wurde.  
  
 Die Möglichkeit der Beschädigung von Daten zu minimieren, wenn eine Klasse mit exportieren [__declspec(dllexport)](../../cpp/dllexport-dllimport.md), sicherstellen, dass:  
  
-   Alle statischen Daten erfolgt über Funktionen, die von der DLL exportiert werden.  
  
-   Inlinemethoden der Klasse können statische Daten ändern.  
  
-   Inlinemethoden Ihrer Klasse verwenden CRT-Funktionen oder andere Bibliotheksfunktionen statische Daten.  
  
-   Keine Inline-Klassenfunktionen verwenden CRT-Funktionen oder andere Bibliotheksfunktionen, z. B. greifen Sie auf statische Daten.  
  
-   Keine Methoden der Klasse (unabhängig von inlining) können auch Typen, für die Instanziierung in der EXE und DLL statische Datenunterschiede haben.  
  
 Sie können vermeiden, Exportieren von Klassen definieren, die eine DLL, die definiert eine Klasse mit virtuellen Funktionen und Funktionen aufrufen kann, instanziieren und Löschen von Objekten des Typs.  Sie können dann virtuelle Funktionen nur für den Typ aufrufen.  
  
 Weitere Informationen zum Exportieren von Vorlagen finden Sie unter [Http://support.microsoft.com/default.aspx?scid=KB; EN-US; 168958](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958).  
  
 C4275 kann in Visual C++ ignoriert werden, wenn Sie aus einem Typ in der C++-Standardbibliothek, die eine Debugversion kompilieren abgeleitet werden (**/MTd**) und, in dem die Fehlermeldung des Compilers auf _Container_base bezieht.  
  
```  
// C4275.cpp  
// compile with: /EHsc /MTd /W2 /c  
#include <vector>  
using namespace std;  
class Node;  
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275  
```