---
title: 'Recordset: Dynamisches Binden von Datenspalten (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets [C++], binding columns dynamically
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- columns [C++], binding to recordsets
ms.assetid: bff67254-d953-4ae4-9716-91c348cb840b
ms.openlocfilehash: 8bc9ba8a143234bec7927c9578a69a95a511bb9f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837787"
---
# <a name="recordset-dynamically-binding-data-columns-odbc"></a>Recordset: Dynamisches Binden von Datenspalten (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

Recordsets verwalten bindende Tabellenspalten, die Sie zur Entwurfszeit angeben. Es gibt aber Fälle, in denen Sie möglicherweise Spalten binden möchten, die Ihnen zur Entwurfszeit nicht bekannt waren. In diesem Thema wird Folgendes erläutert:

- [Gründe, warum Spalten dynamisch an ein Recordset gebunden werden sollen](#_core_when_you_might_bind_columns_dynamically)

- [Dynamisches Binden von Spalten zur Laufzeit](#_core_how_to_bind_columns_dynamically)

> [!NOTE]
> Dieses Thema bezieht sich auf von `CRecordset` abgeleitete Objekte, in denen das gesammelte Abrufen von Zeilen nicht implementiert wurde. Die hier beschriebenen Vorgehensweisen sind grundsätzlich nicht zu empfehlen, wenn Sie gesammeltes Abrufen (Massenabrufen) von Zeilen verwenden. Weitere Informationen zum Abrufen von Massen Zeilen finden Sie unter [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="when-you-might-bind-columns-dynamically"></a><a name="_core_when_you_might_bind_columns_dynamically"></a> Gründe für dynamisches Binden von Spalten

> [!NOTE]
> Der MFC-ODBC-Consumer-Assistent ist in Visual Studio 2019 und höher nicht verfügbar. Sie können einen Consumer weiterhin manuell erstellen.

Zur Entwurfszeit erstellt der MFC-Anwendungs-Assistent oder der [MFC-ODBC-Consumer-Assistent](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (aus **Klasse hinzufügen**) Recordset-Klassen anhand der bekannten Tabellen und Spalten aus Ihrer Datenquelle. Datenbanken können, nachdem Sie diese entworfen haben, später geändert worden sein, wenn Sie deren Tabellen und Spalten zur Laufzeit in Ihrer Anwendung verwenden. Sie oder ein anderer Benutzer hat möglicherweise eine Tabelle hinzugefügt oder gelöscht oder Spalten zu einer Tabelle hinzugefügt oder aus einer Tabelle entfernt, auf der das Recordset Ihrer Anwendung basiert. Dies ist wahrscheinlich nicht für alle Datenzugriffsanwendungen von Belang, aber wenn dies für Ihre Anwendung zutrifft, wie können Sie mit Änderungen im Datenbankschema anders umgehen als über Neugestaltung und Neukompilierung? Diese Frage soll in diesem Thema beantwortet werden.

In diesem Thema ist der häufigste Fall beschrieben, in dem Sie Spalten möglicherweise dynamisch binden möchten: Nachdem Sie mit einem Recordset begonnen haben, das auf einem bekannten Datenbankschema basiert, möchten Sie zur Laufzeit zusätzliche Spalten verarbeiten. Für das Thema wird weiter davon ausgegangen, dass die zusätzlichen Spalten zu `CString`-Felddatenmembern zugeordnet werden, was dem häufigsten Fall entspricht. Es sind aber Vorschläge dazu angegeben, wie Sie mit anderen Datentypen umgehen können.

Mit wenig zusätzlichem Code können Sie:

- [Zur Laufzeit ermitteln, welche Spalten verfügbar sind](#_core_how_to_bind_columns_dynamically).

- [Zur Laufzeit zusätzliche Spalten dynamisch an Ihr Recordset binden](#_core_adding_the_columns).

Das Recordset enthält weiterhin Datenmember für die Spalten, die Ihnen zur Entwurfszeit bekannt waren. Außerdem enthält es wenig zusätzlichen Code, in dem dynamisch ermittelt wird, ob Ihrer Zieltabelle neue Spalten hinzugefügt wurden. Ist dies der Fall, werden diese neuen Spalten im zusätzlichen Code an dynamisch zugeordneten Speicher (anstatt an Recordset-Datenmember) gebunden.

In diesem Thema geht es nicht um andere dynamische Bindungsfälle, etwa gelöschte Tabellen oder Spalten. Für diese Fälle müssen Sie ODBC-API-Aufrufe direkter verwenden. Weitere Informationen finden Sie in der [ODBC Programmer es Reference](/sql/odbc/reference/odbc-programmer-s-reference).

## <a name="how-to-bind-columns-dynamically"></a><a name="_core_how_to_bind_columns_dynamically"></a> Dynamisches Binden von Spalten

Um Spalten dynamisch zu binden, müssen Sie die Namen der zusätzlichen Spalten wissen (oder ermitteln können). Sie müssen außerdem Speicher für die zusätzliche Felddatenmember zuordnen und deren Namen und Typen sowie die Anzahl von Spalten angeben, die Sie hinzufügen.

In der folgenden Erläuterung sind zwei verschiedene Recordsets aufgeführt. Das erste ist das Hauptrecordset, für das Datensätze in der Zieltabelle ausgewählt werden. Das zweite ist ein spezielles Spaltenrecordset, über das Informationen zu den Spalten Ihrer Zieltabelle abgerufen werden.

### <a name="general-process"></a><a name="_core_the_general_process"></a> Allgemeine Vorgehensweise

Auf der allgemeinsten Ebene gehen Sie folgendermaßen vor:

1. Sie erstellen Ihr Haupt-Recordset-Objekt.

   Übergeben Sie optional einen Zeiger auf ein offenes `CDatabase`-Objekt, oder bieten Sie auf andere Weise die Möglichkeit, Verbindungsinformationen für das Spaltenrecordset anzugeben.

1. Führen Sie Schritte aus, um Spalten dynamisch hinzuzufügen.

   Die Vorgehensweise ist im folgenden Abschnitt „Hinzufügen der Spalten“ beschrieben.

1. Öffnen Sie Ihr Hauptrecordset.

   Im Recordset werden Datensätze ausgewählt und wird Datensatzfeldaustausch (Record Field Exchange, RFX) verwendet, um sowohl die statischen Spalten (diejenigen, die Recordset-Felddatenmembern zugeordnet sind) als auch die dynamischen Spalten (zugeordnet zu zusätzlichem Speicher, den Sie zuordnen) zu binden.

### <a name="adding-the-columns"></a><a name="_core_adding_the_columns"></a> Hinzufügen der Spalten

Dynamisches Binden von hinzugefügten Spalten zur Laufzeit erfordert die folgenden Schritte:

1. Sie ermitteln zur Laufzeit, welche Spalten in der Zieltabelle enthalten sind. Sie extrahieren aus diesen Informationen eine Liste der Spalten, die der Tabelle hinzugefügt wurden, seit die Recordset-Klasse entworfen wurde.

   Ein guter Ansatz ist die Verwendung einer Recordset-Klasse für Spalten, in der die Datenquelle auf Spalteninformationen für die Zieltabelle (etwa Spaltenname und Datentyp) abgefragt wird.

1. Stellen Sie Speicher für die neuen Felddatenmember bereit. Da Ihre Haupt-Recordset-Klasse keine Felddatenmember für unbekannte Spalten enthält, müssen Sie einen Platz bereitstellen, in dem die Namen, Ergebniswerte und eventuell Datentypinformationen (wenn die Spalten unterschiedliche Datentypen haben) gespeichert werden.

   Ein Ansatz besteht darin, dynamische Listen zu erstellen: eine für die Namen der neuen Spalten, eine weitere für deren Ergebniswerte und eine dritte für deren Datentypen (falls erforderlich). Diese Listen, insbesondere die Werteliste, stellen Sie die Informationen und den notwendigen Speicher für die Bindung bereit. Die folgende Abbildung veranschaulicht das Erstellen der Listen.

   ![Auflisten von Spalten, die dynamisch gebunden werden sollen](../../data/odbc/media/vc37w61.gif "Listen für dynamisch gebundene Spalten werden erstellt")<br/>
   Erstellen von Listen für dynamisch gebundene Spalten

1. Fügen Sie für jede hinzugefügte Spalte einen RFX-Funktionsaufruf in der `DoFieldExchange`-Funktion Ihres Hauptrecordsets hinzu. Diese RFX Aufrufe erledigen das Abrufen eines Datensatzes, einschließlich der zusätzlichen Spalten, und das Binden der Spalten an Recordset-Datenmember oder an den Speicher, den Sie dynamisch für diese bereitgestellt haben.

   Ein Ansatz besteht darin, eine Schleife zur `DoFieldExchange`-Funktion Ihres Hauptrecordsets hinzuzufügen, in der Ihre Liste neuer Spalten durchlaufen wird, wobei die entsprechende RFX-Funktion für jede Spalte in der Liste aufgerufen wird. Übergeben Sie in jedem RFX-Aufruf einen Spaltennamen aus der Liste der Spaltennamen und einen Speicherort im entsprechenden Member der Ergebniswertliste.

### <a name="lists-of-columns"></a><a name="_core_lists_of_columns"></a> Listen der Spalten

Die vier Listen, mit denen Sie arbeiten müssen, sind in der folgenden Tabelle aufgeführt.

| List | Beschreibung |
|--|--|
| **Aktuelle-Tabellenspalten** | (Liste 1 in der Abbildung) Eine Liste der Spalten, die derzeit in der Tabelle in der Datenquelle enthalten sind. Diese Liste kann mit der Liste der Spalten übereinstimmen, die derzeit in Ihrem Recordset gebunden sind. |
| **Gebundene-Recordset-Spalten** | (Liste 2 in der Abbildung) Eine Liste der Spalten, die in Ihrem Recordset gebunden sind. Für diese Spalten gibt es bereits RFX-Anweisungen in Ihrer `DoFieldExchange`-Funktion. |
| **Dynamisch-zu-bindende-Spalten** | (Liste 3 in der Abbildung) Eine Liste der Spalten, die in der Tabelle, aber nicht in Ihrem Recordset vorhanden sind. Diese Spalten sind diejenigen, die Sie dynamisch binden möchten. |
| **Werte-dynamischer-Spalten** | (Liste 4 in der Abbildung) Eine Liste, die Speicher für die Werte enthält, die aus den Spalten abgerufen werden, die Sie dynamisch binden. Die Elemente in dieser Liste entsprechen eins-zu-eins den Elementen in Dynamisch-zu-bindende-Spalten. |

### <a name="building-your-lists"></a><a name="_core_building_your_lists"></a> Erstellen Ihrer Listen

Mit einer allgemeinen Strategie im Blick können Sie sich den Details zuwenden. In den Verfahren im weiteren Verlauf dieses Themas erfahren Sie, wie Sie die Listen erstellen, die in [Listen der Spalten](#_core_lists_of_columns) aufgeführt sind. In den Verfahren werden Sie durch folgende Schritte geführt:

- [Ermitteln der Namen von Spalten, die nicht in Ihrem Recordset enthalten sind](#_core_determining_which_table_columns_are_not_in_your_recordset)

- [Bereitstellen von dynamischem Speicher für Spalten, die neu zur Tabelle hinzugefügt wurden](#_core_providing_storage_for_the_new_columns)

- [Dynamisches Hinzufügen von RFX Aufrufen für neue Spalten](#_core_adding_rfx_calls_to_bind_the_columns)

### <a name="determining-which-table-columns-are-not-in-your-recordset"></a><a name="_core_determining_which_table_columns_are_not_in_your_recordset"></a> Ermitteln, welche Tabellenspalten nicht in Ihrem Recordset enthalten sind

Erstellen Sie eine Liste (Gebundene-Recordset-Spalten, wie in Liste 2 in der Abbildung), die eine Liste der Spalten enthält, die bereits in Ihrem Hauptrecordsets gebunden sind. Erstellen Sie dann eine Liste (Dynamisch-zu-bindende-Spalten, die aus Aktuelle-Tabellenspalten und Gebundene-Recordset-Spalten abgeleitet ist), die die Namen der Spalten enthält, die in der Tabelle für die Datenquelle, jedoch nicht in Ihrem Hauptrecordset enthalten sind.

##### <a name="to-determine-the-names-of-columns-not-in-the-recordset-columns-to-bind-dynamically"></a>So ermitteln Sie die Namen der Spalten, die nicht im Recordset enthalten sind (Dynamisch-zu-bindende-Spalten)

1. Erstellen Sie eine Liste (Gebundene-Recordset-Spalten) der Spalten, die bereits in Ihrem Hauptrecordset gebunden sind.

   Ein Ansatz besteht darin, Gebundene-Recordset-Spalten zur Entwurfszeit zu erstellen. Sie können sich die RFX-Funktionsaufrufe in der `DoFieldExchange`-Funktion des Recordsets ansehen, um diese Namen zu ermitteln. Richten Sie dann Ihre Liste als ein Array ein, das mit den Namen initialisiert wird.

   In der Abbildung ist Gebundene-Recordset-Spalten (Liste 2) z. B. mit drei Elementen dargestellt. In Gebundene-Recordset-Spalten fehlt die Spalte „Phone“, die in Aktuelle-Tabellenspalten (Liste 1) aufgeführt ist.

1. Vergleichen Sie Aktuelle-Tabellenspalten und Gebundene-Recordset-Spalten, um eine Liste (Dynamisch-zu-bindende-Spalten) der Spalten zu erstellen, die noch nicht in Ihrem Hauptrecordset gebunden sind.

   Ein Ansatz besteht darin, die Liste der Spalten in der Tabelle (Aktuelle-Tabellenspalten) und parallel dazu die Liste der Spalten, die bereits in Ihrem Recordset (Gebundene-Recordset-Spalten) gebunden sind, in einer Schleife zu durchlaufen. Schreiben Sie jeden Namen, der in Aktuelle-Tabellenspalten, aber nicht in Gebundene-Recordset-Spalten enthalten ist, in Dynamisch-zu-bindende-Spalten.

   In der Abbildung ist Dynamisch-zu-bindende-Spalten (Liste 3) beispielsweise mit einem Element gezeigt: die Spalte „Phone“, die in Aktuelle-Tabellen-Spalten (Liste 1), aber nicht in Gebundene-Recordset-Spalten (Liste 2) zu finden ist.

1. Erstellen Sie eine Liste der Werte-dynamischer-Spalten (wie in Liste 4 in der Abbildung), in der die Datenwerte zu speichern sind, die jedem Spaltennamen entsprechen, der in Ihrer Liste der dynamisch zu bindenden Spalten (Dynamisch-zu-bindende-Spalten) gespeichert ist.

   Die Elemente in dieser Liste sind neue Recordset-Felddatenmember. Sie sind die Speicherorte, an die die dynamischen Spalten gebunden sind. Beschreibungen der Listen finden Sie unter [Listen der Spalten](#_core_lists_of_columns).

### <a name="providing-storage-for-the-new-columns"></a><a name="_core_providing_storage_for_the_new_columns"></a> Bereitstellen von Speicher für die neuen Spalten

Richten Sie im nächsten Schritt Speicherorte für die Spalten ein, die dynamisch zu binden sind. Die Idee ist, ein Listenelement bereitzustellen, in dem der Wert jeder Spalte gespeichert wird. Diese Speicherorte entsprechen den Recordset-Membervariablen, in denen die normalerweise gebundenen Spalten gespeichert werden.

#### <a name="to-provide-dynamic-storage-for-new-columns-dynamic-column-values"></a>So stellen Sie dynamischen Speicher für neue Spalten bereit (Werte-dynamischer-Spalten)

1. Erstellen Sie Werte-dynamischer-Spalten, parallel zu Dynamisch-zu-bindende-Spalten, um die Werte der Daten in jeder Spalte aufzunehmen.

   Die Abbildung zeigt z. b. dynamische Spaltenwerte (List 4) mit einem Element: ein- `CString` Objekt, das die tatsächliche Telefonnummer für den aktuellen Datensatz enthält: "555-1212".

   Im üblichsten Fall enthält Werte-dynamischer-Spalten Elemente des Typs `CString`. Arbeiten Sie mit Spalten, die unterschiedliche Datentypen haben können, benötigen Sie eine Liste, die Elemente mit einer Vielzahl von Typen enthalten kann.

Das Ergebnis der vorangegangenen Prozeduren sind zwei Haupt Listen: Spalten-zu-Bindung-dynamisch mit den Namen von Spalten und dynamischen Spaltenwerten, die die Werte in den Spalten für den aktuellen Datensatz enthalten.

> [!TIP]
> Wenn die neuen Spalten nicht alle denselben Datentyp haben, sollten Sie eine weitere Liste erstellen, die Elemente enthält, die jeweils den Typ jedes entsprechenden Elements in der Spaltenliste definieren. (Sie können hierfür die Werte AFX_RFX_BOOL, AFX_RFX_BYTE und so weiter verwenden, wenn Sie dies möchten. Diese Konstanten werden in AFXDB definiert. H.) wählen Sie basierend auf der Darstellung der Spaltendatentypen einen Listentyp aus.

### <a name="adding-rfx-calls-to-bind-the-columns"></a><a name="_core_adding_rfx_calls_to_bind_the_columns"></a> Hinzufügen von RFX-Aufrufen, um die Spalten zu binden

Sorgen Sie schließlich dafür, dass die dynamische Bindung erfolgt. Platzieren Sie dazu RFX-Aufrufe für die neuen Spalten in Ihrer `DoFieldExchange`-Funktion.

##### <a name="to-dynamically-add-rfx-calls-for-new-columns"></a>So fügen Sie RFX Aufrufe für neue Spalten dynamisch hinzu

1. Fügen Sie in der `DoFieldExchange`-Memberfunktion Ihres Hauptrecordsets Code hinzu, in dem Ihre Liste neuer Spalten (Dynamisch-zu-bindende-Spalten) durchlaufen wird. Extrahieren Sie in jeder Schleife einen Spaltennamen aus Dynamisch-zu-bindende-Spalten und einen Ergebniswert für die Spalte aus Werte-dynamischer-Spalten. Übergeben Sie diese Elemente an einen RFX-Funktionsaufruf entsprechend dem Datentyp der Spalte. Beschreibungen der Listen finden Sie unter [Listen der Spalten](#_core_lists_of_columns).

Im üblichen Fall extrahieren Sie in Ihren `RFX_Text`-Funktionsaufrufen `CString`-Objekte aus den Listen, wie in den folgenden Codezeilen, in denen Dynamisch-zu-bindende-Spalten ein `CStringList`-Objekt namens `m_listName` und Werte-dynamischer-Spalten ein `CStringList`-Objekt namens `m_listValue` ist:

```cpp
RFX_Text( pFX,
            m_listName.GetNext( posName ),
            m_listValue.GetNext( posValue ));
```

Weitere Informationen über RFX-Funktionen finden Sie unter [MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md) in der *Klassenbibliotheksreferenz*.

> [!TIP]
> Wenn die neuen Spalten verschiedene Datentypen haben, verwenden Sie eine switch-Anweisung in der Schleife, um die entsprechende RFX-Funktion für jeden Typ aufzurufen.

Wenn das Framework `DoFieldExchange` während des `Open`-Vorgangs aufruft, um Spalten an das Recordset zu binden, werden diese Spalten durch die RFX-Aufrufe für die statischen Spalten gebunden. Anschließend werden in der Schleife wiederholt RFX-Funktionen für die dynamischen Spalten aufgerufen.

## <a name="see-also"></a>Weitere Informationen

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Arbeiten mit großen Datenelementen (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)
