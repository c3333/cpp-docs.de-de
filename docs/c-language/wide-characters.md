---
title: Breitzeichen | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: wide characters
ms.assetid: 165c4a12-8ab9-45fb-9964-c55e9956194c
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 81a5b6476c21ae725e89ecf81f1e05949d3a0107
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="wide-characters"></a>Breitzeichen
**ANSI 3.1.3.4** Der Wert einer ganzzahligen Zeichenkonstante, die mehr als ein Zeichen enthält, oder der Breitzeichenkonstante, die mehr als ein Multibytezeichen enthält  
  
 Die reguläre Zeichenkonstante "ab" verfügt über den Ganzzahlwert (int)0x6162. Wenn es mehr als ein Byte gibt, werden die zuvor gelesenen Bytes durch den Wert von **CHAR_BIT** nach links verschoben, und das nächste Byte wird unter Verwendung des bitweisen OR-Operators mit den niedrigsten **CHAR_BIT**-Bits verglichen. Die Anzahl von Bytes in der Mehrbytezeichenkonstante kann "sizeof(int)" nicht überschreiten, was für den 32-Bit-Zielcode 4 bedeutet.  
  
 Die Mehrbytezeichenkonstante wird wie oben gelesen und mithilfe der `mbtowc`-Laufzeitfunktion zu einer Breitzeichenkonstante konvertiert. Wenn sich daraus keine gültige Mehrbytezeichenkonstante ergibt, wird ein Fehler ausgegeben. In jeden Fall wird die von der `mbtowc`-Funktion überprüfte Anzahl von Bytes auf den Wert von `MB_CUR_MAX` beschränkt.  
  
## <a name="see-also"></a>Siehe auch  
 [Zeichen](../c-language/characters.md)