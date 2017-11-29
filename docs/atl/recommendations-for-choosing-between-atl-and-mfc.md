---
title: "Empfehlungen für die Wahl zwischen ATL- und MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, ATL support
- ATL, vs. MFC
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d912c6cd997c23b9623d20a104327fb6e4701494
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="recommendations-for-choosing-between-atl-and-mfc"></a>Empfehlungen für die Wahl zwischen ATL- und MFC
Wenn Sie Komponenten und Anwendungen zu entwickeln, können Sie zwischen zwei Ansätze auswählen – ATL- und MFC (Microsoft Foundation Class-Bibliothek).  
  
## <a name="using-atl"></a>Verwendung von ATL  
 ATL handelt es sich um eine schnelle und einfache Möglichkeit, eine COM-Komponente in C++ erstellen und verwalten einen geringen Ressourcenbedarf. Verwenden Sie ATL, um ein Steuerelement zu erstellen, wenn Sie alle integrierten Funktionen benötigen, die MFC automatisch bereitstellt.  
  
## <a name="using-mfc"></a>Verwenden von MFC  
 MFC bietet die Möglichkeit zum Erstellen von Anwendungen mit vollem, ActiveX-Steuerelemente und aktive Dokumente. Wenn Sie bereits ein Steuerelement mit MFC erstellt haben, empfiehlt es sich um Development in MFC zu fortfahren. Wenn Sie ein neues Steuerelement zu erstellen, sollten Sie mit ATL, wenn Sie alle MFC integrierte Funktionen benötigen.  
  
## <a name="using-atl-in-an-mfc-project"></a>Verwenden ATL in einem MFC-Projekt  
 Sie können Unterstützung für die Verwendung von ATL in einem vorhandenen MFC-Projekt mithilfe ein Assistenten hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen von ATL-Unterstützung auf MFC-Projekt](../mfc/reference/adding-atl-support-to-your-mfc-project.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Einführung in ATL](../atl/introduction-to-atl.md)
