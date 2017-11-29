---
title: 'Vorgehensweise: Drehen von Bildern mit .NET Framework | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- GDI+ [C++], rotating images
- graphics [C++], rotating images
ms.assetid: e32104d5-87d0-47a9-a22f-9bc835b7e8d7
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b5b337186f67758d56dbc0bae06b6886f43f7435
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-rotate-images-with-the-net-framework"></a>Gewusst wie: Drehen von Bildern mit .NET Framework
Das folgende Codebeispiel veranschaulicht die Verwendung von der <xref:System.Drawing.Image?displayProperty=fullName> Klasse, um ein Bild vom Datenträger zu laden, um 90 Grad drehen und als neue JPG-Datei zu speichern.  
  
> [!NOTE]
>  GDI + ist in Windows XP enthalten und ist als verteilbare Komponente für Windows NT 4.0 SP 6, Windows 2000, Windows 98 und Windows Millennium Edition verfügbar. Informationen zum Herunterladen des neuesten verteilbaren Pakets finden Sie unter [http://go.microsoft.com/fwlink/?linkid=11232](http://go.microsoft.com/fwlink/?linkid=11232). 
  
## <a name="example"></a>Beispiel  
  
```  
#using <system.drawing.dll>  
  
using namespace System;  
using namespace System::Drawing;  
  
int main()  
{  
   Image^ image = Image::FromFile("SampleImage.jpg");  
   image->RotateFlip( RotateFlipType::Rotate90FlipNone );  
   image->Save("SampleImage_rotated.jpg");  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [.NET-Programmierung mit C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)