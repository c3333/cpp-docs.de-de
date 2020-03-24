---
title: 'Recordset: Parametrisieren eines Recordsets (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
ms.openlocfilehash: ec4198c283700daa2e02e2507b9874eaf02858e9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212809"
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>Recordset: Parametrisieren eines Recordsets (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

Manchmal möchten Sie in der Lage sein, zur Laufzeit Datensätze mit Informationen auszuwählen, die Sie berechnet oder von Ihrem Endbenutzer erhalten haben. Dies können Sie mit Recordset-Parametern erreichen.

In diesem Thema wird Folgendes erläutert:

- [Der Zweck eines parametrisierten Recordsets](#_core_parameterized_recordsets)

- [Wann und warum ein Recordset möglicherweise parametrisiert werden soll](#_core_when_to_use_parameters)

- [Deklarieren von Parameterdatenmembern in Ihrer Recordset-Klasse](#_core_parameterizing_your_recordset_class)

- [Übergeben von Parameterinformationen an ein Recordset-Objekt zur Laufzeit](#_core_passing_parameter_values_at_run_time).

##  <a name="parameterized-recordsets"></a><a name="_core_parameterized_recordsets"></a> Parametrisierte Recordsets

Ein parametrisiertes Recordset ermöglicht es Ihnen, Parameterinformationen zur Laufzeit zu übergeben. Dies hat zwei nützliche Auswirkungen:

- Es kann sich eine bessere Ausführungsgeschwindigkeit ergeben.

- Sie können zur Laufzeit eine Abfrage erstellen, die auf Informationen basiert, die Ihnen zur Entwurfszeit nicht zur Verfügung stehen, etwa Informationen, die Sie zur Laufzeit von einem Benutzer erhalten oder die Sie berechnet haben.

Wenn Sie `Open` aufrufen, um die Abfrage auszuführen, verwendet das Recordset die Parameterinformationen, um seine **SELECT**-SQL-Anweisung zu vervollständigen. Sie können jedes Recordset parametrisieren.

##  <a name="when-to-use-parameters"></a><a name="_core_when_to_use_parameters"></a> Wann Parameter zu verwenden sind

Typische Verwendungen für Parameter sind:

- Übergeben von Argumenten an eine vordefinierte Abfrage zur Laufzeit

   Um Parameter an eine gespeicherte Prozedur zu übergeben, müssen Sie eine vollständige benutzerdefinierte **CALL**-ODBC-Anweisung – mit Parameterplatzhaltern – angeben, wenn Sie `Open` aufrufen. Dabei wird die Standard-SQL-Anweisung des Recordsets überschrieben. Weitere Informationen finden Sie unter [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) in der *Klassen Bibliotheks Referenz* und [SQL: Anpassen der SQL-Anweisung (ODBC) Ihres Recordsets](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md) und [Recordset: Deklarieren einer Klasse für eine vordefinierte Abfrage (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).

- Effizientes Ausführen zahlreicher erneuter Abfragen mit unterschiedlichen Parameterinformationen

   Beispielsweise können Sie jedes Mal, wenn ein Endbenutzer Informationen zu einem bestimmten Schüler in der Registrierungsdatenbank für Schüler nachschlägt, den Namen oder die ID des Schülers als Parameter angeben, den Sie vom Benutzer erhalten haben. Dann wird, wenn Sie die `Requery`-Memberfunktion des Recordsets aufrufen, nur der Datensatz dieses Schülers für die Abfrage ausgewählt.

   Die für Ihren Recordset verwendete Filterzeichenfolge, die in `m_strFilter` gespeichert ist, könnte wie folgt aussehen:

    ```cpp
    "StudentID = ?"
    ```

   Angenommen, Sie erhalten die Schüler-ID in der Variablen `strInputID`. Wenn Sie einen Parameter auf `strInputID` festlegen(z. B. die Schüler-ID 100), wird der Wert der Variablen an den Parameterplatzhalter gebunden, der durch das „?“ in der Filterzeichenfolge dargestellt ist.

   Weisen Sie den Parameterwert wie folgt zu:

    ```cpp
    strInputID = "100";
    ...
    m_strParam = strInputID;
    ```

   Eine Filterzeichenfolge können Sie auf folgende Weise einrichten:

    ```cpp
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted
                                       // for some drivers
    ```

   Eine Erläuterung der ordnungsgemäßen Verwendung von Anführungszeichen für Filter [Zeichenfolgen finden Sie unter Recordset: Filtern von Datensätzen (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

   Der Parameterwert ist jedes Mal anders, wenn Sie das Recordset nach einer neuen Schüler-ID abfragen.

   > [!TIP]
   > Ein Verwenden von Parametern ist effizienter, als einfach einen Filter zu nutzen. Für ein parametrisiertes Recordset muss die Datenbank eine **SELECT**-SQL-Anweisung nur einmal verarbeiten. Für ein gefiltertes Recordset ohne Parameter muss die **SELECT**-Anweisung jedes Mal verarbeitet werden, wenn Sie über `Requery` mit einem neuen Filterwert abfragen.

Weitere Informationen zu Filtern finden Sie unter [Recordset: Filtern von Datensätzen (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

##  <a name="parameterizing-your-recordset-class"></a><a name="_core_parameterizing_your_recordset_class"></a> Parametrisieren Ihrer Recordset-Klasse

> [!NOTE]
> Dieser Abschnitt bezieht sich auf aus `CRecordset` abgeleitete Objekte, in denen das gesammelte Abrufen (Massenabrufen) von Zeilen nicht implementiert wurde. Wenn Sie Massenabrufen von Zeilen verwenden, erfolgt das Implementieren von Parametern in einem ähnlichen Vorgang. Weitere Informationen finden Sie unter [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Bevor Sie Ihre Recordset-Klasse erstellen, müssen Sie bestimmen, welche Parameter Sie benötigen, welche Datentypen diese Parameter haben sollen und wie sie vom Recordset verwendet werden sollen.

#### <a name="to-parameterize-a-recordset-class"></a>Parametrisieren einer Recordset-Klasse

> [!NOTE]
> Der MFC-ODBC-Consumer-Assistent ist in Visual Studio 2019 und höher nicht verfügbar. Sie können diese Funktionalität weiterhin manuell erstellen.

1. Führen Sie den [MFC-ODBC-Consumer-Assistenten](../../mfc/reference/adding-an-mfc-odbc-consumer.md) über **Klasse hinzufügen** aus, um die Klasse zu erstellen.

1. Geben Sie die Felddatenmember für die Spalten des Recordsets an.

1. Nachdem der Assistent die Klasse in eine Datei in Ihrem Projekt geschrieben hat, öffnen Sie die .h-Datei, und fügen Sie manuell die entsprechenden Parameterdatenmember zur Klassendeklaration hinzu. Die Hinzufügung könnte in etwa wie das folgende Beispiel aussehen als Bestandteil einer Momentaufnahme-Klasse zur Beantwortung der Frage „Welche Schüler sind in der Oberstufe?“.

    ```cpp
    class CStudentSet : public CRecordset
    {
    // Field/Param Data
        CString m_strFirstName;
        CString m_strLastName;
        CString m_strStudentID;
        CString m_strGradYear;

        CString m_strGradYrParam;
    };
    ```

   Fügen Sie Ihre Parameterdatenmember hinzu, nachdem der Assistent Felddatenmember generiert hat. Die Konvention besteht darin, dass an jeden benutzerdefinierten Parameternamen das Wort „param“ angefügt wird.

1. Ändern Sie die [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)-Memberfunktionsdefinition in der CPP-Datei. Fügen Sie einen RFX-Funktionsaufruf für jeden Parameterdatenmember hinzu, den Sie der Klasse hinzugefügt haben. Weitere Informationen zum Schreiben von RFX-Funktionen finden Sie unter [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Setzen Sie vor die RFX-Aufrufe für die Parameter folgenden einzelnen Aufruf:

    ```cpp
    pFX->SetFieldType( CFieldExchange::param );
    // RFX calls for parameter data members
    ```

1. Inkrementieren Sie im Konstruktor Ihrer Recordset-Klasse die Anzahl der Parameter, `m_nParams`.

   Weitere Informationen finden Sie unter [Daten Satz Feld Austausch: Arbeiten mit dem Assistenten Code](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md).

1. Wenn Sie den Code schreiben, in dem ein Recordset-Objekt dieser Klasse erstellt wird, platzieren Sie ein „?“ (Fragezeichen) an jeder Stelle in Ihren SQL-Anweisungzeichenfolgen, an der ein Parameter ersetzt werden muss.

   Zur Laufzeit werden die „?“-Platzhalter in der vorliegenden Reihenfolge durch die Parameterwerte ersetzt, die Sie übergeben. Der erste Parameterdatenmember, der nach dem [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)-Aufruf festgelegt ist, ersetzt das erste „?“ in der SQL-Zeichenfolge, der zweite Parameterdatenmember ersetzt das zweite „?“ und so weiter.

> [!NOTE]
> Die Parameterreihenfolge ist wichtig: Die Reihenfolge der RFX-Aufrufe für Parameter in Ihrer `DoFieldExchange`-Funktion muss mit der Reihenfolge der Parameterplatzhalter in Ihrer SQL-Zeichenfolge übereinstimmen.

> [!TIP]
> Die wahrscheinlichste Zeichenfolge, mit der gearbeitet wird, ist die Zeichenfolge (sofern vorhanden), die Sie für den [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter)-Datenmember der Klasse angeben, es kann aber sein, dass einige ODBC-Treiber Parameter in anderen SQL-Klauseln unterstützen.

##  <a name="passing-parameter-values-at-run-time"></a><a name="_core_passing_parameter_values_at_run_time"></a> Übergeben von Parameterwerten zur Laufzeit

Sie müssen die Parameterwerte angeben, bevor Sie `Open` (für ein neues Recordset-Objekt) oder `Requery` (für eine vorhandene Ressourcengruppe) aufrufen.

#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>So übergeben Sie Parameterwerte zur Laufzeit an ein Recordset-Objekt

1. Erstellen Sie das Recordset-Objekt.

1. Bereiten Sie Zeichenfolgen vor, z. B. die `m_strFilter`-Zeichenfolge, die die SQL-Anweisung oder Teile dieser Anweisung enthalten. Setzen Sie „?“-Platzhalter an die Stellen, an denen die Parameterinformationen eingefügt werden sollen.

1. Weisen Sie jedem Parameterdatenmember des Objekts einen Laufzeitparameterwert zu.

1. Rufen Sie die `Open`-Memberfunktion auf (oder `Requery` für ein vorhandenes Recordset).

Angenommen, Sie möchten eine Filterzeichenfolge für Ihr Recordset mit Informationen angeben, die zur Laufzeit bereitgestellt werden. Nehmen Sie weiterhin an, dass Sie bereits ein Recordset der Klasse `CStudentSet` namens `rsStudents` erstellt haben und nun dieses Recordset erneut hinsichtlich einer bestimmten Art von Schülerinformationen abfragen möchten.

```cpp
// Set up a filter string with
// parameter placeholders
rsStudents.m_strFilter = "GradYear <= ?";

// Obtain or calculate parameter values
// to pass--simply assigned here
CString strGradYear = GetCurrentAcademicYear( );

// Assign the values to parameter data members
rsStudents.m_strGradYrParam = strGradYear;

// Run the query
if( !rsStudents.Requery( ) )
    return FALSE;
```

Das Recordset enthält Datensätze für die Schüler, deren Datensätze die Bedingungen erfüllen, die durch den Filter angegeben sind, der aus den Laufzeitparametern erstellt wurde. In diesem Fall enthält das Recordset Datensätze für alle Oberstufenschüler.

> [!NOTE]
>  Bei Bedarf können Sie den Wert eines Parameterdatenmembers mit [SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull) auf den Nullwert festlegen. Mit [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull) können Sie entsprechend prüfen, ob ein Parameterdatenmember den Nullwert hat.

## <a name="see-also"></a>Weitere Informationen

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Hinzufügen, Aktualisieren und Löschen von Datensätzen (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[Recordset: Wie Recordsets Datensätze auswählen (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)
