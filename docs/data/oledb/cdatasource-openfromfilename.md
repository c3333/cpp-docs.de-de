---
title: 'CDataSource:: Openfromfilename | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataSource::OpenFromFileName
- ATL::CDataSource::OpenFromFileName
- OpenFromFileName
- CDataSource.OpenFromFileName
- ATL.CDataSource.OpenFromFileName
dev_langs: C++
helpviewer_keywords: OpenFromFileName method
ms.assetid: c4226de6-59da-4368-9c15-c5afab86f68b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c807ead64a068a9797b49606d41d16664b6331e4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="cdatasourceopenfromfilename"></a>CDataSource::OpenFromFileName
Öffnet eine Datenquelle aus einer Datei, die durch den vom Benutzer bereitgestellten Dateinamen angegeben wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      HRESULT OpenFromFileName(   
   LPCOLESTR szFileName    
) throw( );  
```  
  
#### <a name="parameters"></a>Parameter  
 `szFileName`  
 [in] Der Name einer Datei, in der Regel eine Datenquellenverbindungsdatei (UDL-Datei).  
  
 Weitere Informationen zu Datenverknüpfungsdateien (UDL-Dateien), finden Sie unter [Data Link API Overview](https://msdn.microsoft.com/en-us/library/ms718102.aspx) im Windows SDK.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Standard `HRESULT`-Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode öffnet ein Datenquellenobjekt mit den Dienstkomponenten im oledb32.dll; Diese DLL enthält die Implementierung von Dienstkomponentenfunktionen wie z. B. Ressourcenpooling, automatische Transaktionseintragung usw. Weitere Informationen finden Sie unter "OLE DB-Dienste" in der OLE DB Programmer's Reference am [http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** atldbcli.h  
  
## <a name="see-also"></a>Siehe auch  
 [CDataSource-Klasse](../../data/oledb/cdatasource-class.md)