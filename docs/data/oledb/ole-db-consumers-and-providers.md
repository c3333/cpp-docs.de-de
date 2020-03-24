---
title: OLE DB-Consumer und -Anbieter
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB providers, OLE DB data architecture
- OLE DB providers
- OLE DB consumers, OLE DB data architecture
- OLE DB consumers
- OLE DB, data model
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
ms.openlocfilehash: d57ded9d084971c3562fc7f22e6a1a12a4e3368d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210076"
---
# <a name="ole-db-consumers-and-providers"></a>OLE DB-Consumer und -Anbieter

Die OLE DB-Architektur verwendet das Modell von Consumern und Anbietern. Ein Consumer nimmt Datenanforderungen an. Ein Anbieter antwortet auf diese Anforderungen, indem Daten in einem tabellarischen Format abgelegt und an den Consumer zurückgegeben werden. Alle Aufrufe, die der Consumer vornehmen kann, müssen im Anbieter implementiert werden.

Technisch definiert ist ein Consumer ein beliebiger System-oder Anwendungscode (nicht notwendigerweise eine OLE DB Komponente), der über OLE DB Schnittstellen auf Daten zugreift. Die Schnittstellen werden in einem Anbieter implementiert. Ein Anbieter ist also eine beliebige Softwarekomponente, die OLE DB-Schnittstellen implementiert, um den Zugriff auf Daten zu kapseln und Sie für andere Objekte (d. h. Consumer) verfügbar zu machen.

Bei Rollen Ruft ein Consumer Methoden auf OLE DB-Schnittstellen auf. ein OLE DB-Anbieter implementiert die benötigten OLE DB Schnittstellen.

OLE DB vermeidet die Begriffe Client und Server, da diese Rollen nicht immer sinnvoll sind, insbesondere in einer n-Tier-Situation. Da ein Consumer eine Komponente auf einer Ebene sein könnte, die eine andere Komponente bedient, wäre es verwirrend, eine Client Komponente aufzurufen. Außerdem verhält sich ein Anbieter manchmal eher wie ein Datenbanktreiber als ein Server.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Programmierung](../../data/oledb/ole-db-programming.md)<br/>
[Übersicht über die OLE DB-Programmierung](../../data/oledb/ole-db-programming-overview.md)
