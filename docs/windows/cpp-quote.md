---
title: Cpp_quote | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.cpp_quote
dev_langs: C++
helpviewer_keywords: cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cc91c884bb58ce21e4419a8082f15792a0fc2246
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="cppquote"></a>cpp_quote
Gibt die angegebene Zeichenfolge, ohne die Anführungszeichen in der generierten IDL-Datei aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      [ cpp_quote(  
   "statement"  
) ];  
```  
  
#### <a name="parameters"></a>Parameter  
 *statement*  
 Eine C#-Anweisung.  
  
## <a name="remarks"></a>Hinweise  
 Die **Cpp_quote** C++-Attribut ist nützlich, wenn Sie eine Präprozessordirektive in einer IDL-Datei aufnehmen möchten.  
  
 Sie können auch **Cpp_quote** und .h-Datei als Teil der Kompilierung MIDL generiert werden soll. Beispielsweise, wenn Sie eine C++-Headerdatei enthalten, die verwendet der C++-IDL-Attribute, aber verwenden Sie diese Datei kann nicht für eine Aufgabe, können Sie kompilieren es dann zum Erstellen einer MIDL-generierten h-Datei, die Sie verwenden sollten.  
  
 Die **Cpp_quote** Attribut hat die gleiche Funktionalität wie die [Cpp_quote](http://msdn.microsoft.com/library/windows/desktop/aa366765) MIDL-Attribut.  
  
## <a name="example"></a>Beispiel  
 Siehe das Beispiel für [duale](../windows/dual.md) verwenden Sie ein Beispiel für die Verwendung **Cpp_quote**.  
  
## <a name="requirements"></a>Anforderungen  
  
### <a name="attribute-context"></a>Attributkontext  
  
|||  
|-|-|  
|**Betrifft**|Überall|  
|**Wiederholbar**|Nein|  
|**Erforderliche Attribute**|Keine|  
|**Ungültige Attribute**|Keine|  
  
 Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Siehe auch  
 [IDL-Attribute](../windows/idl-attributes.md)   
 [Eigenständige Attribute](../windows/stand-alone-attributes.md)   