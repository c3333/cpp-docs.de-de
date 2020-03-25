---
title: OLE DB-Objektmodell
ms.date: 10/22/2018
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
ms.openlocfilehash: 192195d02b034546e50b1cb860b1f11c47dc2b65
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210118"
---
# <a name="ole-db-object-model"></a>OLE DB-Objektmodell

Das OLE DB-Objektmodell besteht aus den folgenden Objekten oder Komponenten. Mit den ersten vier aufgeführten Objekten oder Komponenten (Datenquellen, Sitzungen, Befehle und Rowsets) können Sie eine Verbindung mit einer Datenquelle herstellen und diese anzeigen. Der Rest, beginnend mit Accessoren, bezieht sich auf die Arbeit mit den Daten, wenn Sie angezeigt wird.

## <a name="data-sources"></a>Projektmappen-Explorer

Mit Datenquellen Objekten können Sie eine Verbindung mit einer Datenquelle, z. b. einer Datei oder einem DBMS, herstellen. Ein Datenquellen Objekt erstellt und verwaltet die Verbindung und enthält Berechtigungen und Authentifizierungen (z. b. Anmelde Name und Kennwort). Ein Datenquellen Objekt kann eine oder mehrere Sitzungen erstellen.

## <a name="sessions"></a>Sitzungen

Eine Sitzung verwaltet eine bestimmte Interaktion mit der Datenquelle, um Daten abzufragen und abzurufen. Jede Sitzung ist eine einzelne Transaktion. Eine Transaktion ist eine unteilbare Arbeitseinheit, die durch den Acid-Test definiert wird. Eine Definition von Acid finden Sie unter [Transaktionen](#vcconoledbcomponents_transactions).

Sitzungen führen wichtige Aufgaben aus, z. b. das Öffnen von Rowsets und das Zurückgeben des Datenquellen Objekts, das es erstellt Sitzungen können auch Metadaten oder Informationen über die Datenquelle selbst (z. b. Tabellen Informationen) zurückgeben.

Eine Sitzung kann mindestens einen Befehl erstellen.

## <a name="commands"></a>Befehle

Befehle führen einen Textbefehl aus, z. b. eine SQL-Anweisung. Wenn der Text-Befehl ein Rowset (z. b. eine SQL- **Select** -Anweisung) angibt, erstellt der Befehl das Rowset.

Ein Befehl ist einfach ein Container für einen Textbefehl, bei dem es sich um eine Zeichenfolge (z. b. eine SQL-Anweisung) handelt, die von einem Consumer an ein Datenquellen Objekt zur Ausführung durch den zugrunde liegenden Datenspeicher des Anbieters übermittelt wird. In der Regel handelt es sich bei dem Textbefehl um eine SQL **Select** -Anweisung (in diesem Fall, da SQL **Select** ein Rowset angibt, erstellt der Befehl automatisch ein Rowset).

## <a name="rowsets"></a>Rowsets

Rowsets zeigen Daten im Tabellenformat an. Ein Index ist ein Sonderfall eines Rowsets. Sie können Rowsets aus der Sitzung oder dem Befehl erstellen.

### <a name="schema-rowsets"></a>Schemarowsets

Schemas verfügen über Metadaten (Strukturinformationen) zu einer Datenbank. Schemarowsets sind Rowsets mit Schema Informationen. Einige OLE DB Anbieter für DBMS unterstützen Schemarowsetobjekte. Weitere Informationen zu Schemarowsets finden Sie unter Abrufen von [Metadaten mit Schemarowsets](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) und [Schemarowset-Klassen und typedef-Klassen](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

### <a name="view-objects"></a>Objekte anzeigen

Ein View-Objekt definiert eine Teilmenge der Zeilen und Spalten eines Rowsets. Sie verfügt über keine eigenen Daten. Ansichts Objekte können keine Daten aus mehreren Rowsets kombinieren.

## <a name="accessors"></a>Accessoren

Nur OLE DB verwendet das Konzept von Accessoren. Ein Accessor beschreibt, wie Daten in einem Consumer gespeichert werden. Sie verfügt über einen Satz von Bindungen (eine Spalten Zuordnung genannt) zwischen Rowsetfeldern (Spalten) und Datenmembern, die Sie im Consumer deklarieren.

##  <a name="transactions"></a><a name="vcconoledbcomponents_transactions"></a> Transaktionen

Transaktions Objekte werden beim committen oder Abbrechen von nicht der niedrigsten Ebene verwendet. Eine Transaktion ist eine unteilbare Arbeitseinheit, die durch den Acid-Test definiert wird. ACID steht für:

- Atomizität, kann nicht in kleinere Arbeitseinheiten aufgeteilt werden

- Parallelität, mehrere Transaktionen können gleichzeitig ausgeführt werden.

- Isolation: eine Transaktion hat nur eingeschränkte Kenntnisse über Änderungen, die von einer anderen vorgenommen wurden.

- Dauerhaftigkeit: die Transaktion führt persistente Änderungen aus.

## <a name="enumerators"></a>Enumeratoren

Enumeratoren suchen nach verfügbaren Datenquellen und anderen Enumeratoren. Consumer, die nicht für eine bestimmte Datenquelle angepasst sind, verwenden Enumeratoren für die Suche nach einer Datenquelle, die verwendet werden soll.

Ein root-Enumerator, der im Microsoft Data Access SDK enthalten ist, durchläuft die Registrierung nach Datenquellen und anderen Enumeratoren. Andere Enumeratoren durchlaufen die Registrierung oder suchen auf anbieterspezifische Weise.

## <a name="errors"></a>Errors

Eine beliebige Schnittstelle für ein beliebiges OLE DB Objekt kann Fehler erzeugen. Fehler enthalten zusätzliche Informationen zu einem Fehler, einschließlich eines optionalen benutzerdefinierten Fehler Objekts. Diese Informationen werden in einem HRESULT gespeichert.

## <a name="notifications"></a>Benachrichtigungen

Benachrichtigungen werden von Gruppen von kooperierenden Consumern verwendet, die ein Rowset gemeinsam nutzen (die Freigabe bedeutet, dass die Consumer in derselben Transaktion arbeiten). Mithilfe von Benachrichtigungen können kooperierende Consumer, die ein Rowset gemeinsam nutzen, über Aktionen für das von ihren Peers ausgeführte Rowset informiert werden.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Programmierung](../../data/oledb/ole-db-programming.md)<br/>
[Übersicht über die OLE DB-Programmierung](../../data/oledb/ole-db-programming-overview.md)
