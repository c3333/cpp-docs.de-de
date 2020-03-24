---
title: 'Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
ms.openlocfilehash: 94177a27a1f99a8c9c37b7fce3f697fd0088b7c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212588"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)

In diesem Thema wird erläutert, wie eine Transaktion in einem Recordset durchgeführt wird.

> [!NOTE]
>  Es wird nur eine Ebene von Transaktionen unterstützt. Transaktionen können nicht geschachtelt werden.

#### <a name="to-perform-a-transaction-in-a-recordset"></a>So führen Sie eine Transaktion in einem Recordset aus

1. Ruft die `BeginTrans` Member-Funktion des `CDatabase` Objekts auf.

1. Wenn Sie das Massen Abrufen von Zeilen nicht implementiert haben, rufen Sie die `AddNew/Update`-, `Edit/Update`-und `Delete` Member-Funktionen von mindestens einem Recordset-Objekt derselben Datenbank so oft wie nötig auf. Weitere Informationen finden Sie unter [Recordset: Hinzufügen, aktualisieren und Löschen von Datensätzen (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md). Wenn Sie das Massen Abrufen von Zeilen implementiert haben, müssen Sie eigene Funktionen schreiben, um die Datenquelle zu aktualisieren.

1. Zum Schluss wird die `CommitTrans` Member-Funktion des `CDatabase` Objekts aufgerufen. Wenn ein Fehler in einem der Updates auftritt oder Sie die Änderungen abbrechen möchten, rufen Sie dessen `Rollback` Member-Funktion auf.

Im folgenden Beispiel werden zwei Recordsets verwendet, um die Registrierung eines Studenten aus einer Schul Registrierungsdatenbank zu löschen, wobei der Student aus allen Klassen entfernt wird, in denen der Student registriert ist. Da die `Delete` Aufrufe in beiden Recordsets erfolgreich sein müssen, ist eine Transaktion erforderlich. Im Beispiel wird davon ausgegangen, dass `m_dbStudentReg`, eine Element Variable vom Typ `CDatabase` bereits mit der Datenquelle verbunden ist, und die Recordset-Klassen `CEnrollmentSet` und `CStudentSet`. Die `strStudentID` Variable enthält einen Wert, der vom Benutzer abgerufen wurde.

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
>  Ein erneuter Aufruf von `BeginTrans`, ohne `CommitTrans` oder `Rollback` aufrufen, ist ein Fehler.

## <a name="see-also"></a>Weitere Informationen

[Transaktion (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transaktion: Wie Transaktionen sich auf Aktualisierungen auswirken (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[CDatabase-Klasse](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)
