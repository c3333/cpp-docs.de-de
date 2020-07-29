---
title: Aktualisieren von Rowsets
ms.date: 05/09/2019
helpviewer_keywords:
- rowsets, updating data
- updating data, rowsets
- updating rowsets
- rowsets
ms.assetid: 39588758-5c72-4254-a10d-cc2b1f473357
ms.openlocfilehash: 22e362170d645574b40070c6db39c2576d3ae9c8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212942"
---
# <a name="updating-rowsets"></a>Aktualisieren von Rowsets

Eine grundlegende Datenbankoperation stellt das Aktualisieren des Datenspeichers bzw. das Schreiben von Daten in den Datenspeicher dar. In OLE DB ist der Aktualisierungsmechanismus einfach: Die Consumeranwendung legt die Werte gebundener Datenmember fest und schreibt diese Werte dann in das Rowset. Anschließend fordert der Consumer den Anbieter auf, den Datenspeicher zu aktualisieren.

Consumer können Rowsetdaten mithilfe folgender Methoden aktualisieren: Festlegen von Spaltenwerten innerhalb einer Zeile, Einfügen einer Zeile und Löschen einer Zeile. Um diese Operationen vornehmen zu können, implementiert die OLE DB-Vorlagenklasse [CRowset](../../data/oledb/crowset-class.md) die [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))-Schnittstelle und überschreibt die folgenden Schnittstellenmethoden:

- [SetData](../../data/oledb/crowset-setdata.md) ändert Spaltenwerte in einer Zeile eines Rowsets. Dies entspricht dem SQL-Befehl UPDATE.

- [Insert](../../data/oledb/crowset-insert.md) fügt eine Zeile in ein Rowset ein. Dies entspricht dem SQL-Befehl INSERT.

- [Delete](../../data/oledb/crowset-delete.md) löscht Zeilen aus einem Rowset. Dies entspricht dem SQL-Befehl DELETE.

## <a name="supporting-update-operations"></a>Unterstützen von Aktualisierungsoperationen

> [!NOTE]
> Der ATL-OLE DB-Consumer-Assistent ist in Visual Studio 2019 und höher nicht verfügbar. Sie können diese Funktionalität weiterhin manuell hinzufügen. Weitere Informationen finden Sie unter [Erstellen eines Consumers ohne Assistent](creating-a-consumer-without-using-a-wizard.md).

Wenn Sie einen Consumer mit dem **ATL-OLE DB Consumer-Assistenten**erstellen, können Sie die Aktualisierungs Vorgänge unterstützen, indem Sie eines oder mehrere der drei Kontrollkästchen **ändern**, **Einfügen**und **Löschen**auswählen. Wenn Sie diese Optionen aktivieren, ändert der Assistent den Code dahingehend, dass die von Ihnen gewünschten Änderungsarten unterstützt werden. Wenn Sie den Assistenten nicht verwenden, müssen Sie jedoch die folgenden Rowset-Eigenschaften auf `VARIANT_TRUE` festlegen, damit Aktualisierungen unterstützt werden:

- `DBPROPVAL_UP_CHANGE` ermöglicht die Änderung von Datenwerten in einer Zeile.

- `DBPROPVAL_UP_INSERT` ermöglicht Ihnen, eine Zeile einzufügen.

- `DBPROPVAL_UP_DELETE` ermöglicht Ihnen, eine Zeile zu löschen.

Legen Sie die Eigenschaften wie folgt fest:

```cpp
CDBPropSet ps(DBPROPSET_ROWSET);

ps.AddProperty(DBPROP_IRowsetChange, true);
ps.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
```

Bei den Operationen zum Ändern, Einfügen oder Löschen können Fehler auftreten, wenn das Schreiben in eine oder mehrere Spalten nicht möglich ist. Ändern Sie die Cursorzuordnung, um diesen Fehler zu beheben.

## <a name="setting-data-in-rows"></a>Festlegen von Daten in Zeilen

[CRowset::SetData](../../data/oledb/crowset-setdata.md) legt Datenwerte in einer oder mehreren Spalten der aktuellen Zeile fest. Der folgende Code legt die Werte von Datenmembern fest, die an die Spalten `Name` und `Units in Stock` der Tabelle `Products` gebunden sind. Anschließend wird `SetData` aufgerufen, um diese Werte in die hundertste Zeile des Rowsets zu schreiben:

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Change the values of columns "Name" and "Units in Stock" in the current row of the Product table
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Candle" ) );

product.m_UnitsInStock = 10000;

// Set the data
HRESULT hr = product.SetData();
```

## <a name="inserting-rows-into-rowsets"></a>Einfügen von Zeilen in Rowsets

[CRowset::Insert](../../data/oledb/crowset-insert.md) erstellt und initialisiert eine neue Zeile unter Verwendung von Daten aus dem Accessor. `Insert` erstellt eine vollständig neue Zeile nach der aktuellen Zeile. Sie müssen angeben, ob die aktuelle Zeile unverändert bleiben soll oder zur nächsten Zeile inkrementiert werden soll. Hierzu müssen Sie den Parameter *bGetRow* festlegen:

```cpp
HRESULT Insert(int nAccessor = 0, bool bGetRow = false)
```

- **`false`**(der Standardwert) gibt an, dass die aktuelle Zeile zur nächsten Zeile Inkrement erhöht wird (in diesem Fall verweist Sie auf die eingefügte Zeile).

- **`true`** Gibt an, dass die aktuelle Zeile dort bleibt, wo Sie ist.

Der folgende Code legt die Werte von Datenmembern fest, die an die Spalten der Tabelle `Products` gebunden sind. Anschließend wird `Insert` aufgerufen, um eine neue Zeile mit diesen Werten nach der hundertsten Zeile des Rowsets einzufügen. Es wird empfohlen, alle Spaltenwerte festzulegen, um zu verhindern, dass sich in der neuen Zeile nicht definierte Daten befinden:

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Set the column values for a row of the Product table, then insert the row
product.m_ProductID = 101;
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Candle" ) );

product.m_SupplierID = 27857;
product.m_CategoryID = 372;
_tcscpy_s(product.m_QuantityPerUnit, product.m_sizeOfQuantityPerUnit, _T( "Pack of 10" ) );

product.m_UnitPrice = 20;
product.m_UnitsInStock = 10000;
product.m_UnitsOnOrder = 5201;
product.m_ReorderLevel = 5000;
product.m_Discontinued = false;

// You must also initialize the status and length fields before setting/inserting data
// Set the column status values
m_dwProductIDStatus = DBSTATUS_S_OK;
m_dwProductNameStatus = DBSTATUS_S_OK;
m_dwSupplierIDStatus = DBSTATUS_S_OK;
m_dwCategoryIDStatus = DBSTATUS_S_OK;
m_dwQuantityPerUnitStatus = DBSTATUS_S_OK;
m_dwUnitPriceStatus = DBSTATUS_S_OK;
m_dwUnitsInStockStatus = DBSTATUS_S_OK;
m_dwUnitsOnOrderStatus = DBSTATUS_S_OK;
m_dwReorderLevelStatus = DBSTATUS_S_OK;
m_dwDiscontinuedStatus = DBSTATUS_S_OK;

// Set the column length value for column data members that are not fixed-length types.
// The value should be the length of the string that you are setting.
m_dwProductNameLength = 6;             // "Candle" has 6 characters
m_dwQuantityPerUnitLength = 10;        // "Pack of 10" has 10 characters

// Insert the data
HRESULT hr = product.Insert();
```

Ein ausführlicheres Beispiel finden Sie unter [CRowset::Insert](../../data/oledb/crowset-insert.md).

Weitere Informationen zum Festlegen der Datenmember für Status und Länge finden Sie unter [Feldstatus-Datenmember in vom Assistenten generierten Accessoren](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).

## <a name="deleting-rows-from-rowsets"></a>Löschen von Zeilen aus Rowsets

[CRowset::Delete](../../data/oledb/crowset-delete.md) löscht die aktuelle Zeile aus dem Rowset. Der folgende Code ruft `Delete` auf, um die hundertste Zeile des Rowsets zu entfernen:

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Delete the row
HRESULT hr = product.Delete();
```

## <a name="immediate-and-deferred-updates"></a>Unverzügliche und verzögerte Aktualisierungen

Wenn nichts anderes festgelegt ist, bewirkt das Aufrufen der `SetData`-Methode, der `Insert`-Methode und der `Delete`-Methode eine unverzügliche Aktualisierung des Datenspeichers. Sie können Aktualisierungen jedoch verzögern. Der Consumer speichert hierbei alle Änderungen in einem lokalen Cache und überträgt sie an den Datenspeicher, wenn eine der folgenden Aktualisierungsmethoden aufgerufen wird:

- [CRowset::Update](../../data/oledb/crowset-update.md) überträgt alle Änderungen, die seit dem letzten Sammeln oder dem letzten `Update`-Aufruf an der aktuellen Zeile vorgenommen wurden.

- [CRowset::UpdateAll](../../data/oledb/crowset-updateall.md) überträgt alle Änderungen, die seit dem letzten Sammeln oder dem letzten `Update`-Aufruf an allen Zeilen vorgenommen wurden.

Der Begriff „Aktualisieren“ wird für die Aktualisierungsmethoden mit der spezifischen Bedeutung „Änderungen auf Befehl“ verwendet und darf nicht mit dem SQL-Befehl **UPDATE** verwechselt werden (`SetData` entspricht dem SQL-Befehl **UPDATE**).

In bestimmten Situationen sind verzögerte Aktualisierungen sinnvoll. Wenn Sie beispielsweise eine Reihe von Geldtransaktionen vornehmen und eine der Transaktionen abgebrochen wird, können Sie die Änderung rückgängig machen, da die Änderungen erst nach der Ausführung der letzten Änderung übermittelt werden. Der Anbieter kann die Änderungen auch in einem Netzwerkaufruf bündeln. Dies ist eine noch effizientere Methode.

Um verzögerte Aktualisierungen zu unterstützen, müssen Sie zusätzlich zu den unter **Unterstützen von Aktualisierungsoperationen** beschriebenen Eigenschaften die `DBPROP_IRowsetChange`-Eigenschaft festlegen:

```cpp
pPropSet->AddProperty(DBPROP_IRowsetUpdate, true);
```

Wenn Sie `Update` oder `UpdateAll` aufrufen, übertragen die Methoden Änderungen vom lokalen Cache in den Datenspeicher. Anschließend wird der lokale Cache bereinigt. Mit „Update“ werden lediglich Änderungen für die aktuelle Zeile übertragen. Deshalb ist es wichtig, dass die Anwendung stets „weiß“, welche Zeile wann aktualisiert werden soll. Im folgenden Beispiel wird das Aktualisieren von zwei aufeinander folgenden Zeilen demonstriert:

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Change the values of columns "Name" and "Units in Stock" in the 100th row of the Product table
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Wick" ) );

product.m_UnitsInStock = 10000;

HRESULT hr = product.SetData();  // No changes made to row 100 yet
product.Update();                 // Update row 100 now

// Change the values of columns "Name" and "Units in Stock" in the 101st row of the Product table
product.MoveNext();

_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName _T( "Wax" ) );

product.m_UnitsInStock = 500;

HRESULT hr = product.SetData();  // No changes made to row 101 yet
product.Update();                 // Update row 101 now
```

Um sicherzustellen, dass vorgenommene Änderungen übertragen werden, sollten Sie `Update` aufrufen, bevor Sie zu einer anderen Zeile wechseln. Erscheint Ihnen dies jedoch als zu aufwendig oder ineffizient, z. B. wenn die Anwendung Hunderte von Zeilen aktualisieren muss, können Sie mithilfe von `UpdateAll` alle Zeilen auf einmal aktualisieren.

Wenn beispielsweise der erste `Update`-Aufruf im oben stehenden Code fehlen würde, bliebe Zeile 100 unverändert, während Zeile 101 geändert würde. Nach diesem Punkt müsste die Anwendung entweder `UpdateAll` aufrufen oder zu Zeile 100 zurückgehen und `Update` aufrufen, damit diese Zeile aktualisiert würde.

Schließlich ist einer der Hauptgründe für die Verwendung verzögerter Aktualisierungen die Möglichkeit, sie rückgängig machen zu können. Wenn Sie [CRowset::Undo](../../data/oledb/crowset-undo.md) aufrufen, wird der lokale Änderungscache auf den Status des Datenspeichers vor dem Ausführen der Änderungen zurückgesetzt. Dabei müssen Sie beachten, dass `Undo` den Status des lokalen Cache nicht um einen einzelnen Schritt (also auf den Zustand vor der letzten Änderung) zurücksetzt, sondern den lokalen Cache für die ganze Zeile bereinigt. Darüber hinaus wirkt sich `Undo` nur auf die aktuelle Zeile aus.

## <a name="see-also"></a>Weitere Informationen

[Arbeiten mit OLE DB Consumervorlagen](../../data/oledb/working-with-ole-db-consumer-templates.md)<br/>
[CRowset-Klasse](../../data/oledb/crowset-class.md)<br/>
[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))<br/>
