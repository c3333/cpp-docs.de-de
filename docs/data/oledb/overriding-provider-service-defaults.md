---
title: Überschreiben der Standardwerte für Anbieterdienste
ms.date: 10/29/2018
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
ms.openlocfilehash: 4cf3ad1064627f64315822a5045642aa50330d10
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209804"
---
# <a name="overriding-provider-service-defaults"></a>Überschreiben der Standardwerte für Anbieterdienste

Der Registrierungs Wert des Anbieters für OLEDB_SERVICES wird als Standardwert für die Eigenschaft [DBPROP_INIT_OLEDBSERVICES](/previous-versions/windows/desktop/ms716898(v=vs.85)) Initialisierung des Datenquellen Objekts zurückgegeben.

Solange der Registrierungs Eintrag vorhanden ist, werden die Objekte des Anbieters aggregiert. Der Benutzer kann die Standardeinstellung des Anbieters für aktivierte Dienste überschreiben, indem er vor der Initialisierung die DBPROP_INIT_OLEDBSERVICES-Eigenschaft festlegt. Um einen bestimmten Dienst zu aktivieren oder zu deaktivieren, ruft der Benutzer den aktuellen Wert der DBPROP_INIT_OLEDBSERVICES-Eigenschaft ab, legt das Bit für die jeweilige Eigenschaft fest, das aktiviert oder deaktiviert werden soll, und setzt die Eigenschaft zurück. DBPROP_INIT_OLEDBSERVICES können direkt in OLE DB oder in der Verbindungs Zeichenfolge festgelegt werden, die an ADO oder `IDataInitialize::GetDatasource`übermittelt wurde. Die entsprechenden Werte zum Aktivieren/Deaktivieren einzelner Dienste sind in der folgenden Tabelle aufgeführt.

|Aktivierte Standarddienste|Eigenschafts Wert DBPROP_INIT_OLEDBSERVICES|Wert in Verbindungs Zeichenfolge|
|------------------------------|------------------------------------------------|--------------------------------|
|Alle Dienste (Standard)|DBPROPVAL_OS_ENABLEALL|"OLE DB Services =-1;"|
|Alle außer Pooling und automatische Eintragung|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_RESOURCEPOOLING &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT`|"OLE DB Services =-4;"|
|Alle außer Client Cursor|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB Services =-5;"|
|Alle außer Pooling, automatische Eintragung und Client Cursor|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB Services =-7;"|
|Keine Dienste|`~DBPROPVAL_OS_ENABLEALL`|"OLE DB Services = 0;"|

Wenn der Registrierungs Eintrag für den Anbieter nicht vorhanden ist, werden die Objekte des Anbieters vom Komponenten-Manager nicht gesammelt. Es werden keine Dienste eingeschaltet, auch wenn Sie vom Benutzer explizit angefordert werden.

## <a name="see-also"></a>Weitere Informationen

[Ressourcen Pooling](/previous-versions/windows/desktop/ms713655(v=vs.85))<br/>
[Verwendung von Ressourcen Pooling durch Consumer](/previous-versions/windows/desktop/ms715907(v=vs.85))<br/>
[Effektive Funktionsweise von Anbietern mit Ressourcen Pooling](/previous-versions/windows/desktop/ms714906(v=vs.85))<br/>
[Aktivieren und Deaktivieren von OLE DB-Diensten](../../data/oledb/enabling-and-disabling-ole-db-services.md)<br/>
