---
title: Db_command (C++ com-Attribut)
ms.date: 07/10/2018
f1_keywords:
- vc-attr.db_command
helpviewer_keywords:
- db_command attribute
ms.assetid: 714c3e15-85d7-408b-9a7c-88505c3e5d24
ms.openlocfilehash: d9ee1ed1bede6a5deaeae0be3783d6abbd05a0d9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831371"
---
# <a name="db_command"></a>db_command

Erstellt einen OLE DB-Befehl.

## <a name="syntax"></a>Syntax

```cpp
[ db_command(command, name, source_name, hresult, bindings, bulk_fetch)
]
```

### <a name="parameters"></a>Parameter

*command*<br/>
Eine Befehlszeichenfolge, die den Text eines OLE DB-Befehls enthält. Ein einfaches Beispiel lautet:

```cpp
[ db_command ( command = "Select * from Products" ) ]
```

Die *Befehlssyntax* lautet wie folgt:

> Bindungs Parameter Block 1 \
> &nbsp;&nbsp;OLE DB Befehl \
> Bindungs Parameter Block 2 \
> &nbsp;&nbsp;Fortsetzung von OLE DB Befehl \
> Bindungs Parameter Block 3 \
> ...

*binding parameter block* ist folgendermaßen definiert:

> **( \[ ** *BindType* **]** *szVar1* \[ , *szVar2* \[ , *nVar3* \[ ,...]] **)**

Dabei gilt:

- **(** kennzeichnet den Anfang des Datenbindungsblocks.

- **\[***BindType* **]** ist eine der folgenden Zeichen folgen ohne Beachtung der Groß-/Kleinschreibung:

  - ** \[ Db_column]** bindet jede der Element Variablen an eine Spalte in einem Rowset.

  - ** \[ Bindto]** (identisch mit ** \[ Db_column]**).

  - ** \[ in]** werden Element Variablen als Eingabeparameter gebunden.

  - ** \[ out]** bindet Element Variablen als Ausgabeparameter.

  - ** \[ in, out]** bindet Element Variablen als Eingabe-/Ausgabeparameter.

- *SzVarX*, *nvarx* , wird in eine Member-Variable im aktuellen Gültigkeitsbereich aufgelöst.

- **)** kennzeichnet das Ende des Datenbindungsblocks.

Wenn die Befehls Zeichenfolge einen oder mehrere Spezifizierer wie \[ in], \[ out] oder \[ in/out] enthält, **db_command** eine Parameter Zuordnung erstellt.

Wenn die Befehls Zeichenfolge einen oder mehrere Parameter enthält, wie z. b. \[ Db_column] oder \[ Bindto], generiert **db_command** ein Rowset und eine accessorzuordnung, um diese gebundenen Variablen zu bedienen. Weitere Informationen finden Sie unter [db_accessor](db-accessor.md) .

> [!NOTE]
> \[*BindType*] die Syntax und der Binding *-Parameter sind* nicht gültig, wenn Sie **db_command** auf Klassenebene verwenden.

Nachfolgend finden Sie einige Beispiele für „binding parameter block“. Im folgenden Beispiel werden die Datenmember `m_au_fname` und `m_au_lname` jeweils an die Spalten `au_fname` und `au_lname` der Autorentabelle in der pubs-Datenbank gebunden:

```cpp
TCHAR m_au_fname[21];
TCHAR m_au_lname[41];
TCHAR m_state[3] = 'CA';

[db_command (command = "SELECT au_fname([bindto]m_au_fname), au_lname([bindto]m_au_lname) " \
   "FROM dbo.authors " \
   "WHERE state = ?([in]m_state)")
]
```

*name*<br/>
Optionale Der Name des Handles, das Sie verwenden, um mit dem Rowset zu arbeiten. Wenn Sie *name*angeben, generiert **db_command** eine Klasse mit dem angegebenen *Namen*, das verwendet werden kann, um das Rowset zu traversieren oder mehrere Aktionsabfragen auszuführen. Wenn Sie *name*nicht angeben, ist es nicht möglich, mehr als eine Zeile mit Ergebnissen an den Benutzer zurückzugeben.

*source_name*<br/>
Optionale Die `CSession` Variable oder die Instanz einer Klasse, auf die das `db_source` Attribut angewendet wird, auf der der Befehl ausgeführt wird. Informationen hierzu finden Sie unter [db_source](db-source.md).

**db_command** stellt sicher, dass die Variable für *source_name* gültig ist, um den Gültigkeitsbereich der angegebenen Variablen auf eine Funktion oder als global festzulegen.

*HRESULT*<br/>
Optionale Gibt die Variable an, die das HRESULT dieses Daten Bank Befehls empfängt. Wenn die Variable nicht existiert, wird sie automatisch durch das Attribut eingefügt.

*Land*<br/>
Optionale Ermöglicht die Trennung der Bindungs Parameter vom OLE DB-Befehl.

Wenn Sie einen Wert für *Bindungen*angeben, analysiert **db_command** den zugeordneten Wert und analysiert den Parameter " \[ *BindType*" nicht. Dies ermöglicht Ihnen die Verwendung der OLE DB-Anbietersyntax. Geben Sie zum Deaktivieren der Verarbeitung ohne Bindungs Parameter an `Bindings=""` .

Wenn Sie keinen Wert für *Bindungen*angeben, analysiert **db_command** den Bindungs Parameter Block, sucht nach "**(**", gefolgt von " **\[** _BindType_"**]** in Klammern, gefolgt von einer oder mehreren zuvor deklarierten C++-Element Variablen, gefolgt von "**)**". Der in Klammern gefasste Text wird aus dem sich ergebenden Befehl entfernt, und diese Parameter werden verwendet, um die Spalten- und Parameterbindungen für diesen Befehl zu erstellen.

*bulk_fetch*<br/>
Optionale Ein ganzzahliger Wert, der die Anzahl der abzurufenden Zeilen angibt.

Mit dem Standardwert 1 werden die Zeilen einzeln abgerufen (das Rowset ist vom Typ [CRowset](../../data/oledb/crowset-class.md)).

Ein höherer Wert als 1 gibt das Massenabrufen von Zeilen an. Das Massenabrufen von Zeilen bezieht sich auf die Fähigkeit von Massenrowsets, mehrere Zeilenhandles abzurufen (das Rowset ist vom Typ [CBulkRowset](../../data/oledb/cbulkrowset-class.md) und wird `SetRows` mit der angegebenen Anzahl von Zeilen aufrufen).

Wenn *bulk_fetch* kleiner als 1 ist, gibt `SetRows` 0 (Null) zurück.

## <a name="remarks"></a>Bemerkungen

**db_command** erstellt ein [CCommand](../../data/oledb/ccommand-class.md) -Objekt, das von einem OLE DB-Consumer verwendet wird, um einen Befehl auszuführen.

Sie können **db_command** entweder mit einem Klassen- oder Funktionsbereich verwenden. Der Hauptunterschied liegt im Bereich des `CCommand` -Objekts. Ist der Gültigkeitsbereich auf die Funktion beschränkt, werden Daten wie z.B. Bindungen bei Beendigung der Funktion ebenfalls beendet. Die Verwendung von Klassen-und Funktionsbereichen umfasst die OLE DB Consumervorlagen Klasse `CCommand<>` , aber die Vorlagen Argumente unterscheiden sich für die Funktions-und Klassen Fälle. Im Funktions Fall werden Bindungen an einen vorgenommen, `Accessor` der lokale Variablen umfasst, während die Klassen Verwendung eine von `CAccessor` abgeleitete Klasse als Argument ableiten wird. Wenn es als Klassenattribut verwendet wird, funktioniert **db_command** zusammen mit **db_column**.

Mit**db_command** können Befehle ausgeführt werden, die kein Resultset zurückgeben.

Wenn der Consumer-Attribut Anbieter dieses Attribut auf eine Klasse anwendet, benennt der Compiler die Klasse in den \_ *yourclassname*-Accessor um, wobei *yourclassname* der Name ist, den Sie der Klasse gegeben haben, und der Compiler erstellt außerdem eine Klasse namens *yourclassname*, die vom \_ *yourclassname*-Accessor abgeleitet wird.  In dieser Klassenansicht werden beide Klassen angezeigt.

## <a name="example"></a>Beispiel

In diesem Beispiel wird ein Befehl definiert, der die Vor- und Nachnamen aus einer Tabelle auswählt, in der die Statusspalte „CA“ entspricht. **db_command** erstellt und liest ein Rowset, für das Sie sowohl über den Assistenten generierte Funktionen wie [OpenAll und CloseAll](../../data/oledb/consumer-wizard-generated-methods.md)als auch `CRowset` -Memberfunktionen wie [MoveNext](../../data/oledb/crowset-movenext.md)ausführen können.

Beachten Sie, dass Sie für diesen Code eine eigene Verbindungszeichenfolge bereitstellen müssen, die eine Verbindung mit der pubs-Datenbank herstellt. Informationen dazu, wie Sie dies in der Entwicklungsumgebung durchführen, finden Sie unter Gewusst [wie: Herstellen einer Verbindung mit einer Datenbank und Durchsuchen vorhandener Objekte](/sql/ssdt/how-to-connect-to-a-database-and-browse-existing-objects) und [Hinzufügen neuer Verbindungen](/visualstudio/data-tools/add-new-connections).

```cpp
// db_command.h
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

#pragma once

[  db_source(L"your connection string"), db_command(L" \
      SELECT au_lname, au_fname \
      FROM dbo.authors \
      WHERE state = 'CA'")  ]

struct CAuthors {
   // In order to fix several issues with some providers, the code below may bind
   // columns in a different order than reported by the provider

   DBSTATUS m_dwau_lnameStatus;
   DBSTATUS m_dwau_fnameStatus;
   DBLENGTH m_dwau_lnameLength;
   DBLENGTH m_dwau_fnameLength;

   [ db_column("au_lname", status="m_dwau_lnameStatus", length="m_dwau_lnameLength") ] TCHAR m_au_lname[41];
   [ db_column("au_fname", status="m_dwau_fnameStatus", length="m_dwau_fnameLength") ] TCHAR m_au_fname[21];

   [ db_param("7", paramtype="DBPARAMIO_INPUT") ] TCHAR m_state[3];

   void GetRowsetProperties(CDBPropSet* pPropSet) {
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   }
};
```

## <a name="example"></a>Beispiel

```cpp
// db_command.cpp
// compile with: /c
#include "db_command.h"

int main(int argc, _TCHAR* argv[]) {
   HRESULT hr = CoInitialize(NULL);

   // Instantiate rowset
   CAuthors rs;

   // Open rowset and move to first row
   strcpy_s(rs.m_state, sizeof(rs.m_state), _T("CA"));
   hr = rs.OpenAll();
   hr = rs.MoveFirst();

   // Iterate through the rowset
   while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET ) {
      // Print out the column information for each row
      printf("First Name: %s, Last Name: %s\n", rs.m_au_fname, rs.m_au_lname);
      hr = rs.MoveNext();
   }

   rs.CloseAll();
   CoUninitialize();
}
```

## <a name="example"></a>Beispiel

In diesem Beispiel wird `db_source` auf die Datenquellenklasse `CMySource`angewendet und `db_command` auf die Befehlsklassen `CCommand1` und `CCommand2`.

```cpp
// db_command_2.cpp
// compile with: /c
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>
// class usage for both db_source and db_command

[  db_source(L"your connection string"), db_command(L" \
      SELECT au_lname, au_fname \
      FROM dbo.authors \
      WHERE state = 'CA'")  ]
struct CMySource {
   HRESULT OpenDataSource() {
      return S_OK;
   }
};

[db_command(command = "SELECT * FROM Products")]
class CCommand1 {};

[db_command(command = "SELECT FNAME, LNAME FROM Customers")]
class CCommand2 {};

int main() {
   CMySource s;
   HRESULT hr = s.OpenDataSource();
   if (SUCCEEDED(hr)) {
      CCommand1 c1;
      hr = c1.Open(s);

      CCommand2 c2;
      hr = c2.Open(s);
   }

   s.CloseDataSource();
}
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**`class`**, **`struct`** , Member, Methode, local|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[OLE DB Consumer-Attribute](ole-db-consumer-attributes.md)<br/>
[Eigenständige Attribute](stand-alone-attributes.md)
