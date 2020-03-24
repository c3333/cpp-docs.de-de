---
title: Testen des schreibgeschützten Anbieters
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, calling
- OLE DB providers, testing
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
ms.openlocfilehash: dc3c4ea36aa9dac64f2aa7861fd5d51927c77ecd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209499"
---
# <a name="testing-the-read-only-provider"></a>Testen des schreibgeschützten Anbieters

Zum Testen eines Anbieters benötigen Sie einen Consumer. Dies ist hilfreich, wenn der Consumer dem Anbieter gerecht werden kann. Die OLE DB Consumervorlagen sind ein schlanker Wrapper um OLE DB und entsprechen den COM-Objekten des Anbieters. Da die Quelle mit den Consumervorlagen ausgeliefert wird, ist es einfach, einen Anbieter mit Ihnen zu debuggen. Die Consumer-Vorlagen sind auch eine sehr kleine und schnelle Möglichkeit, Consumeranwendungen zu entwickeln.

Das Beispiel in diesem Thema erstellt eine Standardanwendung des MFC-Anwendungs-Assistenten für einen Testconsumer. Die Testanwendung ist ein einfaches Dialogfeld mit hinzugefügter OLE DB Consumervorlagen Code.

## <a name="to-create-the-test-application"></a>So erstellen Sie die Testanwendung

1. Klicken Sie im Menü **Datei** auf **Neu** und dann auf **Projekt**.

1. Wählen Sie im Bereich **Projekttypen** den Ordner **installiert** > **Visual C++**  > **MFC/ATL** aus. Wählen Sie im Bereich **Vorlagen** die Option **MFC-Anwendung**aus.

1. Geben Sie als Projektnamen *TestProv*ein, und klicken Sie dann auf **OK**.

   Der **MFC-Anwendungs** -Assistent wird angezeigt.

1. Wählen Sie auf der Seite **Anwendungstyp** die Option **Dialog Feld basiert**aus.

1. Wählen Sie auf der Seite **Erweiterte Features** die Option **Automation**aus, und klicken Sie dann auf **Fertig**stellen.

> [!NOTE]
> Die Anwendung erfordert keine Automatisierungsunterstützung, wenn Sie `CoInitialize` in `CTestProvApp::InitInstance`hinzufügen.

Sie können das Dialogfeld **TestProv** (IDD_TESTPROV_DIALOG) anzeigen und bearbeiten, indem Sie es in **Ressourcenansicht**auswählen. Platzieren Sie im Dialogfeld zwei Listenfelder, eine für jede Zeichenfolge im Rowset. Deaktivieren Sie die Sort-Eigenschaft für beide Listenfelder, indem Sie ALT drücken+**Eingabe** **Taste** drücken, wenn ein Listenfeld ausgewählt ist, und legen Sie die **Sort** -Eigenschaft auf **false**fest. Platzieren Sie außerdem eine Schaltfläche **Ausführen** im Dialogfeld, um die Datei abzurufen. Das fertige Dialogfeld **TestProv** sollte über zwei Listenfelder mit den Bezeichnungen "String 1" und "String 2" verfügen. Außerdem werden die Schaltflächen **OK**, **Abbrechen**und **Ausführen** angezeigt.

Öffnen Sie die Header Datei für die Dialogfeld Klasse (in diesem Fall TestProvDlg. h). Fügen Sie den folgenden Code der Header Datei hinzu (außerhalb von Klassen Deklarationen):

```cpp
////////////////////////////////////////////////////////////////////////
// TestProvDlg.h
#include <atldbcli.h>  

class CProvider
{
// Attributes
public:
   char   szField1[16];
   char   szField2[16];

   // Binding Maps
BEGIN_COLUMN_MAP(CProvider)
   COLUMN_ENTRY(1, szField1)
   COLUMN_ENTRY(2, szField2)
END_COLUMN_MAP()
};
```

Der Code stellt einen Benutzerdaten Satz dar, der definiert, welche Spalten im Rowset verwendet werden. Wenn der Client `IAccessor::CreateAccessor`aufruft, verwendet er diese Einträge, um anzugeben, welche Spalten gebunden werden sollen. Die OLE DB Consumervorlagen ermöglichen es Ihnen außerdem, Spalten dynamisch zu binden. Die COLUMN_ENTRY-Makros sind die Client seitige Version der PROVIDER_COLUMN_ENTRY Makros. Die beiden COLUMN_ENTRY Makros geben die Ordinalzahl, den Typ, die Länge und den Datenmember für die beiden Zeichen folgen an.

Fügen Sie eine Handlerfunktion für die Schaltfläche **Ausführen** hinzu, indem Sie **STRG** drücken und auf die Schaltfläche **Ausführen** doppelklicken. Platzieren Sie den folgenden Code in der-Funktion:

```cpp
///////////////////////////////////////////////////////////////////////
// TestProvDlg.cpp

void CTestProvDlg::OnRun()
{
   CCommand<CAccessor<CProvider>> table;
   CDataSource source;
   CSession session;

   if (source.Open("Custom.Custom.1", NULL) != S_OK)
      return;

   if (session.Open(source) != S_OK)
      return;

   if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)
      return;

   while (table.MoveNext() == S_OK)
   {
      m_ctlString1.AddString(table.szField1);
      m_ctlString2.AddString(table.szField2);
   }
}
```

Die Klassen `CCommand`, `CDataSource`und `CSession` gehören alle zu den OLE DB Consumer-Vorlagen. Jede Klasse imitiert ein COM-Objekt im Anbieter. Das `CCommand`-Objekt übernimmt die `CProvider` Klasse, die in der Header Datei deklariert ist, als Vorlagen Parameter. Der `CProvider`-Parameter stellt Bindungen dar, die Sie verwenden, um auf die Daten des Anbieters zuzugreifen.

Mit den Zeilen zum Öffnen der einzelnen Klassen werden alle COM-Objekte im Anbieter erstellt. Um den Anbieter zu suchen, verwenden Sie den `ProgID` des Anbieters. Sie können die `ProgID` aus der Systemregistrierung oder in der Datei Custom. RGS (Datei "Custom. RGS") erhalten (Öffnen Sie das Verzeichnis des Anbieters, und suchen Sie nach der `ProgID` Key).

Die Datei "mydata. txt" ist im `MyProv` Beispiel enthalten. Wenn Sie eine eigene Datei erstellen möchten, verwenden Sie einen Editor, und geben Sie eine gerade Anzahl von Zeichen folgen ein, und drücken **Sie die Eingabe** Taste. Ändern Sie den Pfadnamen, wenn Sie die Datei verschieben.

Übergeben Sie die Zeichenfolge "c:\\\Samples\\\myprov\\\mydata.txt" in der `table.Open` Zeile. Wenn Sie in den `Open`-Befehl eintreten, sehen Sie, dass diese Zeichenfolge an die `SetCommandText`-Methode im Anbieter übermittelt wird. Beachten Sie, dass die `ICommandText::Execute`-Methode diese Zeichenfolge verwendet hat.

Rufen Sie zum Abrufen der Daten `MoveNext` in der Tabelle auf. `MoveNext` Ruft die Funktionen `IRowset::GetNextRows`, `GetRowCount`und `GetData` auf. Wenn keine weiteren Zeilen vorhanden sind (d. h. die aktuelle Position im Rowset ist größer als `GetRowCount`), wird die Schleife beendet.

Wenn keine Zeilen mehr vorhanden sind, geben Anbieter DB_S_ENDOFROWSET zurück. Der DB_S_ENDOFROWSET Wert ist kein Fehler. Sie sollten immer eine Prüfung auf S_OK durchführen, um eine Datenabruf Schleife abzubrechen und das Makro "erfolgreich" nicht zu verwenden.

Sie sollten jetzt in der Lage sein, das Programm zu erstellen und zu testen.

## <a name="see-also"></a>Weitere Informationen

[Erweitern des einfachen schreibgeschützten Anbieters](../../data/oledb/enhancing-the-simple-read-only-provider.md)
