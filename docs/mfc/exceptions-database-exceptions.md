---
title: 'Ausnahmen: Datenbankausnahmen'
ms.date: 09/17/2019
helpviewer_keywords:
- DAO [MFC], exceptions
- exceptions [MFC], database
- exception handling [MFC], databases
- ODBC exceptions [MFC]
- ODBC [MFC], exceptions
- database exceptions [MFC]
- databases [MFC], exception handling
- error codes [MFC], database exception handling
ms.assetid: 28daf260-f824-4be6-aecc-1f859e6dec26
ms.openlocfilehash: 894960338a7e8c293054ade00e0cdf3295648bb7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366628"
---
# <a name="exceptions-database-exceptions"></a>Ausnahmen: Datenbankausnahmen

In diesem Artikel wird erläutert, wie Datenbankausnahmen behandelt werden. Der größte Teil des Materials in diesem Artikel gilt unabhängig davon, ob Sie mit den MFC-Klassen für Open Database Connectivity (ODBC) oder den MFC-Klassen für Datenzugriffsobjekte (DAO) arbeiten. Material, das für das eine oder andere Modell spezifisch ist, ist explizit markiert. Dabei werden folgende Themen behandelt:

- [Ansätze zur Ausnahmebehandlung](#_core_approaches_to_exception_handling)

- [Ein Beispiel für die Datenbankausnahmebehandlung](#_core_a_database_exception.2d.handling_example)

## <a name="approaches-to-exception-handling"></a><a name="_core_approaches_to_exception_handling"></a>Ansätze zur Ausnahmebehandlung

Der Ansatz ist derselbe, unabhängig davon, ob Sie mit DAO (veraltet) oder ODBC arbeiten.

Sie sollten immer Ausnahmehandler schreiben, um außergewöhnliche Bedingungen zu behandeln.

Der pragmatischste Ansatz zum Abfangen von Datenbankausnahmen besteht darin, die Anwendung mit Ausnahmeszenarien zu testen. Bestimmen Sie die wahrscheinlichen Ausnahmen, die für einen Vorgang im Code auftreten können, und erzwingen Sie die Ausnahme. Überprüfen Sie dann die Ablaufverfolgungsausgabe, um festzustellen, welche Ausnahme ausgelöst wird, oder überprüfen Sie die zurückgegebenen Fehlerinformationen im Debugger. Auf diese Weise erfahren Sie, welche Rückgabecodes für die von Ihnen verwendeten Ausnahmeszenarien angezeigt werden.

### <a name="error-codes-used-for-odbc-exceptions"></a>Fehlercodes, die für ODBC-Ausnahmen verwendet werden

Zusätzlich zu den vom Framework definierten Rückgabecodes, die Namen des Formulars **AFX_SQL_ERROR_XXX**haben, basieren einige [CDBExceptions](../mfc/reference/cdbexception-class.md) auf [ODBC-Rückgabecodes.](../data/odbc/odbc-basics.md) Die Rückgabecodes für solche Ausnahmen haben Namen des Formulars **SQL_ERROR_XXX**.

Die Rückgabecodes, die von den Datenbankklassen zurückgegeben werden können – sowohl von Framework als auch von ODBC definiert  – werden unter dem [m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode) -Datenmember der `CDBException`-Klasse dokumentiert. Weitere Informationen zu den von ODBC definierten Rückgabecodes finden Sie in der *ODBC SDK-Programmiererreferenz* in der MSDN-Bibliothek.

### <a name="error-codes-used-for-dao-exceptions"></a>Fehlercodes, die für DAO-Ausnahmen verwendet werden

Für DAO-Ausnahmen sind in der Regel weitere Informationen verfügbar. Sie können über drei Datenmember eines abgefangenen [CDaoException-Objekts](../mfc/reference/cdaoexception-class.md) auf Fehlerinformationen zugreifen:

- [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) enthält einen Zeiger auf ein [CDaoErrorInfo-Objekt,](../mfc/reference/cdaoerrorinfo-structure.md) das Fehlerinformationen in der DAO-Auflistung von Fehlerobjekten kapselt, die der Datenbank zugeordnet sind.

- [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror) enthält einen erweiterten Fehlercode aus den MFC DAO-Klassen. Diese Fehlercodes, die Namen des Formulars **AFX_DAO_ERROR_XXX**haben, `CDaoException`werden unter dem Datenelement in dokumentiert.

- [m_scode](../mfc/reference/cdaoexception-class.md#m_scode) enthält ggf. einen OLE **SCODE** von DAO. Sie müssen jedoch selten mit diesem Fehlercode arbeiten. In der Regel sind weitere Informationen in den beiden anderen Datenmembern verfügbar. Weitere Informationen zu **SCODE-Werten** finden Sie im Datenmember.

Zusätzliche Informationen zu DAO-Fehlern, dem DAO-Fehlerobjekttyp und der DAO Errors-Auflistung finden Sie unter Klasse [CDaoException](../mfc/reference/cdaoexception-class.md).

## <a name="a-database-exception-handling-example"></a><a name="_core_a_database_exception.2d.handling_example"></a>Ein Beispiel für die Datenbankausnahme-Handhabung

Im folgenden Beispiel wird versucht, ein [CRecordset](../mfc/reference/crecordset-class.md)-derived-Objekt auf dem Heap mit dem **neuen** Operator zu erstellen und dann das Recordset (für eine ODBC-Datenquelle) zu öffnen. Ein ähnliches Beispiel für die DAO-Klassen finden Sie unter "DAO-Ausnahmebeispiel" weiter unten.

### <a name="odbc-exception-example"></a>ODBC-Ausnahmebeispiel

Die [Open-Memberfunktion](../mfc/reference/crecordset-class.md#open) könnte eine Ausnahme auslösen (vom Typ [CDBException](../mfc/reference/cdbexception-class.md) für `Open` die ODBC-Klassen), sodass dieser Code den Aufruf mit einem **try-Block** in Klammern setzt. Der nachfolgende **Fangblock** fängt eine `CDBException`. Sie können das Ausnahmeobjekt `e`selbst mit dem Namen , überprüfen, aber in diesem Fall genügt es zu wissen, dass der Versuch, ein Recordset zu erstellen, fehlgeschlagen ist. Der **catch-Block** zeigt ein Meldungsfeld an und bereinigt das Recordset-Objekt.

[!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]

### <a name="dao-exception-example"></a>DAO-Ausnahmebeispiel

Das DAO-Beispiel ähnelt dem Beispiel für ODBC, aber Sie können in der Regel weitere Arten von Informationen abrufen. Der folgende Code versucht auch, ein Recordset zu öffnen. Wenn dieser Versuch eine Ausnahme auslöst, können Sie ein Datenelement des Ausnahmeobjekts auf Fehlerinformationen untersuchen. Wie beim vorherigen ODBC-Beispiel reicht es wahrscheinlich aus zu wissen, dass der Versuch, ein Recordset zu erstellen, fehlgeschlagen ist.

[!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]

Dieser Code ruft eine Fehlermeldungszeichenfolge vom [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) Member des Ausnahmeobjekts ab. MFC füllt dieses Element aus, wenn die Ausnahme ausgelöst wird.

Eine Erläuterung der von einem `CDaoException` Objekt zurückgegebenen Fehlerinformationen finden Sie unter Die Klassen [CDaoException](../mfc/reference/cdaoexception-class.md) und [CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md).

Wenn Sie mit Microsoft Jet (.mdb)-Datenbanken arbeiten, und in den meisten Fällen, wenn Sie mit ODBC arbeiten, gibt es nur ein Fehlerobjekt. In dem seltenen Fall, wenn Sie eine ODBC-Datenquelle verwenden und mehrere Fehler auftreten, können Sie die Fehlerauflistung von DAO basierend auf der Anzahl der von [CDaoException::GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount)zurückgegebenen Fehler durchlaufen. Rufen Sie jedes Mal durch die Schleife [CDaoException::GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo) auf, um das `m_pErrorInfo` Datenmember aufzufüllen.

## <a name="see-also"></a>Siehe auch

[Ausnahmebehandlung](../mfc/exception-handling-in-mfc.md)
