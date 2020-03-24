---
title: Verwenden mehrerer Resultsets aus einer gespeicherten Prozedur
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
ms.openlocfilehash: 6163eb8bf18edfc3d205f1d012de0c64c5570693
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209286"
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>Verwenden mehrerer Resultsets aus einer gespeicherten Prozedur

Die meisten gespeicherten Prozeduren geben mehrere Ergebnissätze zurück. Eine solche gespeicherte Prozedur umfasst in der Regel eine oder mehrere SELECT-Anweisungen. Der Consumer muss diesen Einschluss in Erwägung gezogen, um alle Resultsets verarbeiten zu können.

## <a name="to-handle-multiple-result-sets"></a>So verarbeiten Sie mehrere Resultsets

1. Erstellen Sie eine `CCommand`-Klasse mit `CMultipleResults` als Vorlagen Argument und mit dem-Accessor Ihrer Wahl, normalerweise ein dynamischer oder manueller Accessor. Wenn Sie einen anderen Accessor verwenden, können Sie möglicherweise nicht die Ausgabespalten für jedes Rowset ermitteln.

1. Führen Sie die gespeicherte Prozedur wie gewohnt aus, und binden Sie die Spalten (Weitere Informationen finden Sie unter Gewusst [wie: Abrufen von Daten](../../data/oledb/fetching-data.md)).

1. Verwenden Sie die Daten.

1. Ruft `GetNextResult` für die `CCommand`-Klasse auf. Wenn ein anderes resultrowset verfügbar ist, gibt `GetNextResult` S_OK zurück, und Sie sollten die Spalten erneut binden, wenn Sie einen manuellen Accessor verwenden. Wenn `GetNextResult` einen Fehler zurückgibt, sind keine weiteren Resultsets verfügbar.

## <a name="see-also"></a>Weitere Informationen

[Verwenden von gespeicherten Prozeduren](../../data/oledb/using-stored-procedures.md)
