---
title: 'Recordset: Architektur (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, data members
- field data members, recordset architecture
- field data members
- m_nParams data member, recordsets
- recordsets, architecture
- parameter data members in recordsets
- m_nFields data member
- ODBC recordsets, architecture
- m_nParams data member
- m_nFields data member, recordsets
ms.assetid: 47555ddb-11be-4b9e-9b9a-f2931764d298
ms.openlocfilehash: e95250b5ef307eafdb334050fbace945355e0521
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079860"
---
# <a name="recordset-architecture-odbc"></a>Recordset: Architektur (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

In diesem Thema sind die Datenelemente (Datenmember) beschrieben, die zum Aufbau eines Recordset-Objekts gehören:

- [Felddatenmember](#_core_field_data_members)

- [Parameterdatenmember](#_core_parameter_data_members)

- [Verwenden von m_nFields- und m_nParams-Datenmembern](#_core_using_m_nfields_and_m_nparams)

> [!NOTE]
>  Dieses Thema bezieht sich auf von `CRecordset` abgeleitete Objekte, in denen das gesammelte Abrufen von Zeilen nicht implementiert wurde. Wird gesammeltes Abrufen (Massenabrufen) von Zeilen implementiert, ist die Architektur ähnlich. Informationen zu den Unterschieden finden Sie unter [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="sample-class"></a><a name="_core_a_sample_class"></a> Beispielklasse

> [!NOTE]
> Der MFC-ODBC-Consumer-Assistent ist in Visual Studio 2019 und höher nicht verfügbar. Sie können einen Consumer weiterhin manuell erstellen.

Wenn Sie den [MFC-ODBC-Consumer-Assistenten](../../mfc/reference/adding-an-mfc-odbc-consumer.md) aus dem **Klasse hinzufügen**-Assistenten verwenden, um eine aus `CRecordset` abgeleitete Recordset-Klasse zu deklarieren, hat die resultierende Klasse die grundsätzliche Struktur, die für die folgende einfache Klasse dargestellt ist:

```cpp
class CCourse : public CRecordset
{
public:
   CCourse(CDatabase* pDatabase = NULL);
   ...
   CString m_strCourseID;
   CString m_strCourseTitle;
   CString m_strIDParam;
};
```

An den Anfang der Klasse schreibt der Assistent eine Reihe von [Felddatenmembern](#_core_field_data_members). Wenn Sie die Klasse erstellen, müssen Sie mindestens ein Felddatenmember angeben. Ist die Klasse parametrisiert, wie dies für die Beispielklasse der Fall ist (mit dem Datenmember `m_strIDParam`), müssen Sie manuell [Parameterdatenmember](#_core_parameter_data_members) hinzufügen. Der Assistent unterstützt das Hinzufügen von Parametern zu einer Klasse nicht.

##  <a name="field-data-members"></a><a name="_core_field_data_members"></a> Felddatenmember

Die wichtigsten Member des Recordset-Klasse sind die Felddatenmember. Für jede Spalte, die Sie in der Datenquelle auswählen, enthält die Klasse ein Datenmember mit dem entsprechenden Datentyp für diese Spalte. Die am Anfang dieses Themas gezeigte [Beispielklasse](#_core_a_sample_class) hat beispielsweise zwei Felddatenmember namens `CString` und `m_strCourseID`, die beide den Typ `m_strCourseTitle` haben.

Wenn das Recordset eine Menge von Datensätzen auswählt, bindet das Framework die Spalten des aktuellen Datensatzes (nach dem `Open`-Aufruf ist der erste Datensatz aktuell) automatisch an die Felddatenmember des Objekts. Das heißt, das Framework verwendet den entsprechenden Felddatenmember als Puffer, in dem der Inhalt einer Datensatzspalte gespeichert wird.

Wenn der Benutzer zu einem neuen Datensatz scrollt, verwendet das Framework die Felddatenmember, um den aktuellen Datensatz darzustellen. Das Framework aktualisiert die Felddatenmember, wobei die Werte des vorherigen Datensatzes ersetzt werden. Die Felddatenmember werden auch zum Aktualisieren des aktuellen Datensatzes und zum Hinzufügen neuer Datensätze verwendet. Als einen Schritt des Aktualisierens eines Datensatzes geben Sie die Aktualisierungswerte an, indem Sie den entsprechenden Felddatenmembern direkt Werte zuweisen.

##  <a name="parameter-data-members"></a><a name="_core_parameter_data_members"></a> Parameterdatenmember

Ist die Klasse parametrisiert, hat sie mindestens ein Parameterdatenmember. Eine parametrisierte Klasse ermöglicht es Ihnen, für eine Recordset-Abfrage Daten zu verwenden, die zur Laufzeit abgerufen oder berechnet werden.

Üblicherweise hilft der Parameter, die Auswahl einzugrenzen, wie im folgenden Beispiel gezeigt. Ausgehend von der [Beispielklasse](#_core_a_sample_class) am Anfang dieses Themas könnte das Recordset-Objekt die folgende SQL-Anweisung ausführen:

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?
```

Das „?“ ist ein Platzhalter für einen Parameterwert, den Sie zur Laufzeit angeben. Wenn Sie beim Erstellen des Recordsets dessen `m_strIDParam`-Datenmember auf MATH101 festlegen, sieht die resultierende SQL-Anweisung für das Recordset wie folgt aus:

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101
```

Durch Definieren von Parameterdatenmembern informieren Sie das Framework über Parameter in der SQL-Zeichenfolge. Das Framework bindet den Parameter, wodurch ODBC mitgeteilt wird, wo es die Werte abrufen soll, durch die der Platzhalter ersetzt wird. In diesem Beispiel enthält das resultierende Recordset nur einen Datensatz aus der Tabelle „Course“ mit einer „CourseID“-Spalte, die den Wert MATH101 hat. Alle angegebenen Spalten dieses Datensatzes sind ausgewählt. Sie können so viele Parameter (und Platzhalter) angeben, wie Sie benötigen.

> [!NOTE]
>  MFC selbst führt keine Aktionen mit den Parametern aus, insbesondere nimmt es keine Textersetzung vor. Stattdessen teilt MFC ODBC mit, wo der Parameter abgerufen werden soll. ODBC ruft die Daten ab und führt die notwendige Parametrisierung durch.

> [!NOTE]
>  Die Reihenfolge der Parameter ist wichtig. Weitere Informationen zu diesen und weiteren Informationen zu Parametern finden Sie unter [Recordset: parametrialisieren eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

##  <a name="using-m_nfields-and-m_nparams"></a><a name="_core_using_m_nfields_and_m_nparams"></a> Verwenden von m_nFields und m_nParams

Wenn ein Assistent einen Konstruktor für Ihre Klasse schreibt, initialisiert er auch den [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)-Datenmember, der die Anzahl von [Felddatenmembern](#_core_field_data_members) in der Klasse angibt. Wenn Sie [Parameter](#_core_parameter_data_members) zu Ihrer Klasse hinzufügen, müssen Sie auch eine Initialisierung für den [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)-Datenmember hinzufügen, der die Anzahl von Parameterdatenmembern angibt. Das Framework verwendet diese Werte, um mit den Datenelementen zu arbeiten.

Weitere Informationen und Beispiele finden Sie unter [Daten Satz Feld Austausch: Verwenden von RFX](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="see-also"></a>Weitere Informationen

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Deklarieren einer Klasse für eine Tabelle (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Datensatzfeldaustausch (RFX)](../../data/odbc/record-field-exchange-rfx.md)