---
title: Schwerwiegender Fehler C1005 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1005
dev_langs: C++
helpviewer_keywords: C1005
ms.assetid: 150daf8e-a38a-4669-9c1a-a05b5a1f65ef
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e558112619e5cbefd641e7906df941d0869ceddb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1005"></a>Schwerwiegender Fehler C1005
Zeichenfolge zu lang für Puffer  
  
 Eine Zeichenfolge in einer Zwischendatei des Compilers hat zu einem Pufferüberlauf geführt.  
  
 Sie erhalten diesen Fehler möglicherweise, wenn der an die Compileroptionen [/Fd](../../build/reference/fd-program-database-file-name.md) oder [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) übergebene Parameter größer als 256 Bytes ist.