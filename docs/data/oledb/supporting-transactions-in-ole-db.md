---
title: Unterstützen von Transaktionen in OLE DB
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB consumer templates [C++], transaction support
- transactions [C++], OLE DB support for
- nested transactions [C++]
- OLE DB [C++], transaction support
- databases [C++], transactions
- distributed transactions [C++]
ms.assetid: 3d72e583-ad38-42ff-8f11-e2166d60a5a7
ms.openlocfilehash: e7ec4f69b4bba497446c94afb94cb5a1d648f7c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209543"
---
# <a name="supporting-transactions-in-ole-db"></a>Unterstützen von Transaktionen in OLE DB

Bei einer [Transaktion](../../data/transactions-mfc-data-access.md) handelt es sich um eine Möglichkeit, eine Reihe von Aktualisierungen einer Datenquelle zu gruppieren oder zu gruppieren, sodass entweder alle erfolgreich ausgeführt werden und ein Commit für einen einzelnen Commit ausgeführt wird, und für die gesamte Transaktion ein Rollback ausgeführt wird. Durch diesen Vorgang wird die Integrität des Ergebnisses in der Datenquelle sichergestellt.

OLE DB unterstützt Transaktionen mit den folgenden drei Methoden:

- [ITransaction local:: Start Transaction](/previous-versions/windows/desktop/ms709786(v=vs.85))

- [ITransaction:: Commit](/previous-versions/windows/desktop/ms713008(v=vs.85))

- [ITransaction:: Abort](/previous-versions/windows/desktop/ms709833(v=vs.85))

## <a name="relationship-of-sessions-and-transactions"></a>Beziehung zwischen Sitzungen und Transaktionen

Mit einem einzelnen Datenquellen Objekt können ein oder mehrere Sitzungs Objekte erstellt werden, von denen jeder zu einem bestimmten Zeitpunkt innerhalb oder außerhalb des Gültigkeits Bereichs einer Transaktion liegen kann.

Wenn eine Sitzung nicht in eine Transaktion eintritt, wird für alle innerhalb dieser Sitzung ausgeführten Vorgänge im Datenspeicher sofort ein Commit für jeden Methoden Aufrufvorgang ausgeführt. (Dies wird manchmal auch als Autocommitmodus oder impliziter Modus bezeichnet.)

Wenn eine Sitzung in eine Transaktion eintritt, sind alle innerhalb der Sitzung im Datenspeicher ausgeführten Arbeiten Teil dieser Transaktion und werden als einzelne Einheit ausgeführt oder abgebrochen. (Dies wird manchmal auch als manueller Commitmodus bezeichnet.)

Die Transaktionsunterstützung ist Anbieter spezifisch. Wenn der von Ihnen verwendete Anbieter Transaktionen unterstützt, kann ein Sitzungs Objekt, von dem `ITransaction` und `ITransactionLocal` unterstützt werden, eine (nicht-nicht-eingefügte) Transaktion eingeben. Die OLE DB Templates-Klasse [CSession](../../data/oledb/csession-class.md) unterstützt diese Schnittstellen und ist die empfohlene Methode zum Implementieren der C++Transaktionsunterstützung in Visual.

## <a name="starting-and-ending-the-transaction"></a>Starten und Beenden der Transaktion

Sie können die Methoden `StartTransaction`, `Commit`und `Abort` im Rowsetobjekt im Consumer aufzurufen.

Durch Aufrufen von `ITransactionLocal::StartTransaction` wird eine neue lokale Transaktion gestartet. Wenn Sie die Transaktion starten, werden alle von späteren Vorgängen vorgeschriebenen Änderungen erst dann auf den Datenspeicher angewendet, wenn Sie einen Commit für die Transaktion durchgeführt haben.

Durch Aufrufen von `ITransaction::Commit` oder `ITransaction::Abort` wird die Transaktion beendet. `Commit` bewirkt, dass alle Änderungen im Bereich der Transaktion auf den Datenspeicher angewendet werden. `Abort` bewirkt, dass alle Änderungen im Gültigkeitsbereich der Transaktion abgebrochen werden, und der Datenspeicher verbleibt in dem Zustand, den er vor dem Start der Transaktion besaß.

## <a name="nested-transactions"></a>Nicht mehr als Transaktionen

Eine [eingefügte Transaktion](/previous-versions/windows/desktop/ms716985(v=vs.85)) tritt auf, wenn Sie eine neue lokale Transaktion starten, wenn in der Sitzung bereits eine aktive Transaktion vorhanden ist. Die neue Transaktion wird als eine unter der aktuellen Transaktion unter der aktuellen Transaktion gestartete Transaktion gestartet. Wenn der Anbieter keine Unterstützung für die Durchführung von unterstützten Transaktionen hat, wird beim Aufrufen von `StartTransaction` XACT_E_XTIONEXISTS zurückgegeben.

## <a name="distributed-transactions"></a>Verteilte Transaktionen

Eine verteilte Transaktion ist eine Transaktion, mit der verteilte Daten aktualisiert werden. Das heißt, Daten auf mehr als einem vernetzten Computersystem. Wenn Sie Transaktionen über ein verteiltes System unterstützen möchten, sollten Sie anstelle der OLE DB Transaktionsunterstützung die .NET Framework verwenden.

## <a name="see-also"></a>Weitere Informationen

[Verwenden von Zugriffsmethoden](../../data/oledb/using-accessors.md)
