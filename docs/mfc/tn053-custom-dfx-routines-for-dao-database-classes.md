---
title: 'TN053: Benutzereigene DFX-Routinen für DAO-Datenbankklassen'
ms.date: 09/17/2019
helpviewer_keywords:
- MFC, DAO and
- database classes [MFC], DAO
- DAO [MFC], MFC
- DFX (DAO record field exchange) [MFC], custom routines
- TN053
- DAO [MFC], classes
- DFX (DAO record field exchange) [MFC]
- custom DFX routines [MFC]
ms.assetid: fdcf3c51-4fa8-4517-9222-58aaa4f25cac
ms.openlocfilehash: f7ad854f4dbb4e90c09e886c69260e4e2eea3be2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365258"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053: Benutzereigene DFX-Routinen für DAO-Datenbankklassen

> [!NOTE]
> DAO wird mit Access-Datenbanken verwendet und wird über Office 2013 unterstützt. DAO 3.6 ist die endgültige Version und gilt als veraltet. Die Visual C++-Umgebung und die Assistenten unterstützen DAO nicht (obwohl die DAO-Klassen enthalten sind und Sie sie weiterhin verwenden können). Microsoft empfiehlt, [OLE DB-Vorlagen](../data/oledb/ole-db-templates.md) oder [ODBC und MFC](../data/odbc/odbc-and-mfc.md) für neue Projekte zu verwenden. Sie sollten DAO nur bei der Verwaltung vorhandener Anwendungen verwenden.

Dieser technische Hinweis beschreibt den DAO-Datensatzfeldaustauschmechanismus (DFX). Um zu verstehen, was in den DFX-Routinen passiert, wird die `DFX_Text` Funktion als Beispiel ausführlich erläutert. Als zusätzliche Informationsquelle zu diesem technischen Hinweis können Sie den Code für die anderen DFX-Funktionen untersuchen. Sie benötigen wahrscheinlich nicht so oft eine benutzerdefinierte DFX-Routine, wie Sie eine benutzerdefinierte RFX-Routine benötigen (die mit ODBC-Datenbankklassen verwendet wird).

Dieser technische Hinweis enthält:

- DFX Übersicht

- [Beispiele](#_mfcnotes_tn053_examples) für DAO Record Field Exchange und Dynamic Binding

- [Funktionsweise von DFX](#_mfcnotes_tn053_how_dfx_works)

- [Was Ihre benutzerdefinierte DFX-Routine tut](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)

- [Details zu DFX_Text](#_mfcnotes_tn053_details_of_dfx_text)

**DFX Übersicht**

Der DAO-Datensatzfeldaustauschmechanismus (DFX) wird verwendet, um das Abrufen `CDaoRecordset` und Aktualisieren von Daten bei Verwendung der Klasse zu vereinfachen. Der Prozess wird mithilfe von `CDaoRecordset` Datenmembern der Klasse vereinfacht. Durch Ableiten `CDaoRecordset`von können Sie der abgeleiteten Klasse Datenmember hinzufügen, die jedes Feld in einer Tabelle oder Abfrage darstellen. Dieser Mechanismus der "statischen Bindung" ist einfach, ist jedoch möglicherweise nicht die Methode zum Abrufen/Aktualisieren von Daten für alle Anwendungen. DFX ruft jedes gebundene Feld jedes Mal ab, wenn der aktuelle Datensatz geändert wird. Wenn Sie eine leistungskritische Anwendung entwickeln, für die bei der Änderung der Währung `CDaoRecordset::GetFieldValue` `CDaoRecordset::SetFieldValue` nicht jedes Feld abgerufen werden muss, ist die "dynamische Bindung" über die "dynamische Bindung" die Methode der Datenzugriffsmethode ihrer Wahl.

> [!NOTE]
> DFX und dynamische Bindung schließen sich nicht gegenseitig aus, so dass eine hybride Verwendung von statischer und dynamischer Bindung verwendet werden kann.

## <a name="example-1--use-of-dao-record-field-exchange-only"></a><a name="_mfcnotes_tn053_examples"></a>Beispiel 1 — Nur Verwendung von DAO Record Field Exchange

(angenommen `CDaoRecordset` — `CMySet` abgeleitete Klasse bereits geöffnet)

```
// Add a new record to the customers table
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```

**Beispiel 2 — Nur dynamische Bindung verwenden**

(nimmt `CDaoRecordset` die `rs`Verwendung von Klasse , an, und sie ist bereits geöffnet)

```
// Add a new record to the customers table
COleVariant  varFieldValue1 (_T("MSFT"),
    VT_BSTRT);

//Note: VT_BSTRT flags string type as ANSI,
    instead of UNICODE default
COleVariant  varFieldValue2  (_T("Microsoft"),
    VT_BSTRT);

rs.AddNew();

rs.SetFieldValue(_T("Customer_ID"),
    varFieldValue1);

rs.SetFieldValue(_T("Customer_Name"),
    varFieldValue2);

rs.Update();
```

**Beispiel 3 — Verwendung von DAO Record Field Exchange und dynamischer Bindung**

(nimmt das Durchsuchen `CDaoRecordset`von `emp`Mitarbeiterdaten mit der -abgeleiteten Klasse an )

```
// Get the employee's data so that it can be displayed
emp.MoveNext();

// If user wants to see employee's photograph,
// fetch it
COleVariant varPhoto;
if (bSeePicture)
    emp.GetFieldValue(_T("photo"),
    varPhoto);

// Display the data
PopUpEmployeeData(emp.m_strFirstName,
    emp.m_strLastName,
    varPhoto);
```

## <a name="how-dfx-works"></a><a name="_mfcnotes_tn053_how_dfx_works"></a>Funktionsweise von DFX

Der DFX-Mechanismus funktioniert ähnlich wie der RFX-Mechanismus (Record Field Exchange), der von den MFC ODBC-Klassen verwendet wird. Die Prinzipien von DFX und RFX sind die gleichen, aber es gibt zahlreiche interne Unterschiede. Das Design der DFX-Funktionen war so, dass praktisch der gesamte Code von den einzelnen DFX-Routinen geteilt wird. Auf der höchsten Ebene macht DFX nur ein paar Dinge.

- DFX erstellt bei Bedarf die SQL **SELECT-Klausel** und die SQL **PARAMETERS-Klausel.**

- DFX erstellt die Bindungsstruktur, `GetRows` die von der DAO-Funktion verwendet wird (mehr dazu später).

- DFX verwaltet den Datenpuffer, der zum Erkennen schmutziger Felder verwendet wird (wenn Doppelpufferung verwendet wird)

- DFX verwaltet die Statusarrays **NULL** und **DIRTY** und legt bei Bedarf Werte für Aktualisierungen fest.

Das Herzstück des DFX-Mechanismus `CDaoRecordset` ist die `DoFieldExchange` Funktion der abgeleiteten Klasse. Diese Funktion löst Aufrufe an die einzelnen DFX-Funktionen eines entsprechenden Vorgangstyps aus. Legen `DoFieldExchange` Sie vor dem Aufruf der internen MFC-Funktionen den Vorgangstyp fest. Die folgende Liste zeigt die verschiedenen Vorgangstypen und eine kurze Beschreibung.

|Vorgang|BESCHREIBUNG|
|---------------|-----------------|
|`AddToParameterList`|Builds PARAMETERS-Klausel|
|`AddToSelectList`|Erstellt die SELECT-Klausel|
|`BindField`|Richtet die Bindungsstruktur ein|
|`BindParam`|Legt Parameterwerte fest|
|`Fixup`|Legt den NULL-Status fest|
|`AllocCache`|Ordnet Cache für die Schmutzprüfung zu|
|`StoreField`|Speichert den aktuellen Datensatz in den Cache|
|`LoadField`|Stellt den Cache auf Memberwerte wieder her|
|`FreeCache`|Frees Cache|
|`SetFieldNull`|Legt den Feldstatus & Wert auf NULL fest.|
|`MarkForAddNew`|Markiert Felder schmutzig, wenn nicht PSEUDO NULL|
|`MarkForEdit`|Markiert Felder schmutzig, wenn sie nicht mit dem Cache übereinstimmen|
|`SetDirtyField`|Legt Feldwerte fest, die als verschmutzt markiert sind|

Im nächsten Abschnitt wird jeder Vorgang für `DFX_Text`ausführlicher erläutert.

Das wichtigste Feature, das Sie über den DAO-Datensatzfeldaustauschprozess verstehen können, ist, dass er die `GetRows` Funktion des `CDaoRecordset` Objekts verwendet. Die DAO-Funktion `GetRows` kann auf verschiedene Weise funktionieren. Dieser technische Vermerk wird `GetRows` nur kurz beschreiben, da er außerhalb des Rahmens dieses technischen Vermerks liegt.
DAO `GetRows` kann auf verschiedene Arten arbeiten.

- Es kann mehrere Datensätze und mehrere Datenfelder gleichzeitig abrufen. Dies ermöglicht einen schnelleren Datenzugriff mit der Komplikation des Umgangs mit einer großen Datenstruktur und den entsprechenden Offsets für jedes Feld und für jeden Datensatz in der Struktur. MFC nutzt diesen Mechanismus zum Abrufen mehrerer Datensätze nicht.

- Eine `GetRows` andere Möglichkeit besteht darin, Programmierern die Angabe von Bindungsadressen für die abgerufenen Daten jedes Feldes für einen Datensatz zu ermöglichen.

- DAO ruft auch für Spalten mit variabler Länge in den Aufrufer zurück, damit der Aufrufer Speicher zuweisen kann. Diese zweite Funktion hat den Vorteil, dass die Anzahl der Kopien von Daten minimiert wird und `CDaoRecordset` die direkte Speicherung von Daten in Membern einer Klasse (der abgeleiteten Klasse) ermöglicht wird. Dieser zweite Mechanismus ist die Methode, die `CDaoRecordset` MFC zum Binden an Datenmember in abgeleiteten Klassen verwendet.

## <a name="what-your-custom-dfx-routine-does"></a><a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a>Was Ihre benutzerdefinierte DFX-Routine tut

Aus dieser Diskussion geht hervor, dass die wichtigste Operation, die in einer DFX-Funktion `GetRows`implementiert wurde, die Möglichkeit sein muss, die erforderlichen Datenstrukturen einzurichten, um erfolgreich aufzurufen. Es gibt eine Reihe anderer Vorgänge, die eine DFX-Funktion ebenfalls unterstützen muss, `GetRows` aber keine so wichtig oder komplex wie die korrekte Vorbereitung auf den Aufruf.

Die Verwendung von DFX wird in der Online-Dokumentation beschrieben. Im Wesentlichen gibt es zwei Anforderungen. Zunächst müssen Member für `CDaoRecordset` jedes gebundene Feld und jeden Parameter der abgeleiteten Klasse hinzugefügt werden. Dies `CDaoRecordset::DoFieldExchange` sollte überschrieben werden. Beachten Sie, dass der Datentyp des Elements wichtig ist. Sie sollte mit den Daten aus dem Feld in der Datenbank übereinstimmen oder zumindest für diesen Typ konvertierbar sein. Beispielsweise kann ein numerisches Feld in der Datenbank, z. B. eine `CString` lange ganze Zahl, immer in Text konvertiert und an ein Element gebunden werden, aber ein Textfeld in einer Datenbank kann nicht unbedingt in eine numerische Darstellung konvertiert werden, z. B. lange ganze Zahl und an ein Long-Integer-Element gebunden. DAO und das Microsoft Jet-Datenbankmodul sind für die Konvertierung (anstelle von MFC) verantwortlich.

## <a name="details-of-dfx_text"></a><a name="_mfcnotes_tn053_details_of_dfx_text"></a>Details zu DFX_Text

Wie bereits erwähnt, ist der beste Weg, um zu erklären, wie DFX funktioniert, ein Beispiel zu arbeiten. Zu diesem Zweck sollte die `DFX_Text` Durchsicht der Interna von ganz gut funktionieren, um zumindest ein grundlegendes Verständnis von DFX zu vermitteln.

- `AddToParameterList`

   Dieser Vorgang erstellt die SQL`Parameters <param name>, <param type> ... ;` **PARAMETERS-Klausel** (" "), die von Jet benötigt wird. Jeder Parameter wird benannt und eingegeben (wie im RFX-Aufruf angegeben). Sehen Sie `CDaoFieldExchange::AppendParamType` sich die Funktionsfunktion an, um die Namen der einzelnen Typen anzuzeigen. Im Fall `DFX_Text`von ist der verwendete Typ **Text**.

- `AddToSelectList`

   Erstellt die **SELECT** SQL SELECT-Klausel. Dies ist ziemlich geradlinig, da der spaltenname,`SELECT <column name>, ...`der durch den DFX-Aufruf angegeben wird, einfach angehängt wird (" ").

- `BindField`

   Die komplexeste der Operationen. Wie bereits erwähnt, wird hier die `GetRows` von dpa verwendete DAO-Bindungsstruktur eingerichtet. Wie Sie aus dem `DFX_Text` Code in den Informationstypen in der Struktur sehen können, gehören `DFX_Text`der DAO-Typ verwendet **(DAO_CHAR** oder **DAO_WCHAR** im Fall von ). Darüber hinaus wird auch der Typ der verwendeten Bindung eingerichtet. In einem `GetRows` früheren Abschnitt wurde nur kurz beschrieben, aber es genügte zu erklären, dass der Typ der Bindung, die von MFC verwendet wird, immer direkte Adressbindung ist (**DAOBINDING_DIRECT**). Zusätzlich wird für die Spaltenbindung `DFX_Text`variabler Länge (z. B. ) die Rückrufbindung verwendet, damit MFC die Speicherzuordnung steuern und eine Adresse mit der richtigen Länge angeben kann. Das bedeutet, dass MFC DAO immer sagen kann, "wo" die Daten zu setzen, wodurch eine direkte Bindung an Membervariablen möglich ist. Der Rest der Bindungsstruktur wird mit Dingen wie der Adresse der Speicherzuweisungsrückruffunktion und dem Typ der Spaltenbindung (Bindung nach Spaltenname) ausgefüllt.

- `BindParam`

   Dies ist eine `SetParamValue` einfache Operation, die mit dem in Ihrem Parametermember angegebenen Parameterwert aufruft.

- `Fixup`

   Füllt den **STATUS NULL** für jedes Feld aus.

- `SetFieldNull`

   Dieser Vorgang markiert nur jeden Feldstatus als **NULL** und legt den Wert der Membervariablen auf **PSEUDO_NULL**fest.

- `SetDirtyField`

   Ruft `SetFieldValue` für jedes Feld auf, das als "schmutzig" markiert ist.

Alle verbleibenden Vorgänge befassen sich nur mit der Verwendung des Datencache. Der Datencache ist ein zusätzlicher Puffer der Daten im aktuellen Datensatz, der verwendet wird, um bestimmte Dinge zu vereinfachen. Beispielsweise können "schmutzige" Felder automatisch erkannt werden. Wie in der Online-Dokumentation beschrieben, kann es komplett oder auf Feldebene ausgeschaltet werden. Die Implementierung des Puffers verwendet eine Karte. Diese Zuordnung wird verwendet, um dynamisch zugeordnete Kopien der Daten mit `CDaoRecordset` der Adresse des Feldes "gebunden" (oder abgeleitetes Datenelement) abzugleichen.

- `AllocCache`

   Ordnet den zwischengespeicherten Feldwert dynamisch zu und fügt ihn der Karte hinzu.

- `FreeCache`

   Löscht den zwischengespeicherten Feldwert und entfernt ihn aus der Karte.

- `StoreField`

   Kopiert den aktuellen Feldwert in den Datencache.

- `LoadField`

   Kopiert den zwischengespeicherten Wert in das Feldelement.

- `MarkForAddNew`

   Überprüft, ob der aktuelle Feldwert nicht**NULL** ist, und markiert ihn bei Bedarf als schmutzig.

- `MarkForEdit`

   Vergleicht den aktuellen Feldwert mit dem Datencache und markiert bei Bedarf verschmutzte Werte.

> [!TIP]
> Modellieren Sie Ihre benutzerdefinierten DFX-Routinen anhand der vorhandenen DFX-Routinen für Standarddatentypen.

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
