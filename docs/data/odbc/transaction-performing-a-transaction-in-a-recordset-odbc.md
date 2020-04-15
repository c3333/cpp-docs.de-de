---
title: 'Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
ms.openlocfilehash: 45ae414c318376b2c4d787498e9a288a0037af83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358095"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)

In diesem Thema wird erläutert, wie eine Transaktion in einem Recordset ausgeführt wird.

> [!NOTE]
> Es wird nur eine Transaktionsebene unterstützt. Sie können keine Transaktionen verschachteln.

#### <a name="to-perform-a-transaction-in-a-recordset"></a>So führen Sie eine Transaktion in einem Recordset aus

1. Rufen `CDatabase` Sie die `BeginTrans` Memberfunktion des Objekts auf.

1. Wenn Sie das Abrufen von Massenzeilen `AddNew/Update` `Edit/Update`nicht `Delete` implementiert haben, rufen Sie die , - und Memberfunktionen eines oder mehrerer Recordset-Objekte derselben Datenbank so oft wie nötig auf. Weitere Informationen finden Sie unter [Recordset: Hinzufügen, Aktualisieren und Löschen von Datensätzen (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md). Wenn Sie das Abrufen von Massenzeilen implementiert haben, müssen Sie eigene Funktionen schreiben, um die Datenquelle zu aktualisieren.

1. Rufen Sie `CDatabase` schließlich die `CommitTrans` Memberfunktion des Objekts auf. Wenn bei einer der Aktualisierungen ein Fehler auftritt oder `Rollback` Sie die Änderungen abbrechen möchten, rufen Sie die Memberfunktion auf.

Im folgenden Beispiel werden zwei Recordsets verwendet, um die Einschreibung eines Schülers aus einer Schulregistrierungsdatenbank zu löschen, wodurch der Schüler aus allen Klassen entfernt wird, in denen der Schüler registriert ist. Da `Delete` die Aufrufe in beiden Recordsets erfolgreich ausgeführt werden müssen, ist eine Transaktion erforderlich. Im Beispiel wird `m_dbStudentReg`das Vorhandensein von `CDatabase` , einer Membervariablen des Typs, `CEnrollmentSet` `CStudentSet`der bereits mit der Datenquelle verbunden ist, und der Recordsetklassen und angenommen. Die `strStudentID` Variable enthält einen vom Benutzer erhaltenen Wert.

```
BOOL CEnrollDoc::RemoveStudent( CString strStudentID )
{
    // remove student from all the classes
    // the student is enrolled in

    if ( !m_dbStudentReg.BeginTrans( ) )
        return FALSE;

    CEnrollmentSet rsEnrollmentSet(&m_dbStudentReg);
    rsEnrollmentSet.m_strFilter = "StudentID = " + strStudentID;

    if ( !rsEnrollmentSet.Open(CRecordset::dynaset) )
        return FALSE;

    CStudentSet rsStudentSet(&m_dbStudentReg);
    rsStudentSet.m_strFilter = "StudentID = " + strStudentID;

    if ( !rsStudentSet.Open(CRecordset::dynaset) )
        return FALSE;

    TRY
    {
        while ( !rsEnrollmentSet.IsEOF( ) )
        {
            rsEnrollmentSet.Delete( );
            rsEnrollmentSet.MoveNext( );
        }

        // delete the student record
        rsStudentSet.Delete( );

        m_dbStudentReg.CommitTrans( );
    }

    CATCH_ALL(e)
    {
        m_dbStudentReg.Rollback( );
        return FALSE;
    }
    END_CATCH_ALL

    rsEnrollmentSet.Close( );
    rsStudentSet.Close( );

    return TRUE;

}
```

> [!NOTE]
> Rufen `BeginTrans` Sie `CommitTrans` erneut `Rollback` auf, ohne aufzurufen, oder ist ein Fehler.

## <a name="see-also"></a>Siehe auch

[Transaktion (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transaktion: Auswirkungen von Transaktionen auf Aktualisierungen (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[CDatabase-Klasse](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)
