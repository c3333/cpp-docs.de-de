---
title: Compilerwarnung (Stufe 1) C4656 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4656
dev_langs: C++
helpviewer_keywords: C4656
ms.assetid: b5aaef74-2320-4345-a6ae-b813881a491c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 790ff92b66fc60ad3310af58ce08a8224b63d37c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4656"></a>Compilerwarnung (Stufe 1) C4656
'Symbol': Datentyp Neuigkeiten gibt es seit dem letzten Build geändert wurde oder an anderer Stelle unterschiedlich definiert ist  
  
 Sie haben einen Datentyp hinzugefügt oder geändert, der seit dem letzten erfolgreichen Build neu zum Quellcode hinzugekommen ist. „Bearbeiten und fortfahren“ unterstützt keine Änderungen an vorhandenen Datentypen.  
  
 Auf diese Warnung folgt immer [Schwerwiegender Fehler C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Weitere Informationen hierzu finden Sie unter [Unterstützte Codeänderungen](/visualstudio/debugger/supported-code-changes-cpp).  
  
### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>So entfernen Sie diese Warnung, ohne die aktuelle Debugsitzung zu beenden  
  
1.  Ändern Sie den Datentyp wieder in den Zustand, den er vor dem Fehler hatte.  
  
2.  Wählen Sie im Menü **Debuggen** den Befehl **Codeänderungen übernehmen**aus.  
  
### <a name="to-remove-this-error-without-changing-your-source-code"></a>So entfernen Sie diesen Fehler, ohne den Quellcode zu ändern  
  
1.  Wählen Sie im Menü **Debuggen** die Option **Debuggen beenden**.  
  
2.  Wählen Sie im Menü **Erstellen** den Befehl **Erstellen**aus.