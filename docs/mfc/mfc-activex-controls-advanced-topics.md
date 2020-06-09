---
title: 'MFC-ActiveX-Steuerelemente: Weiterführende Themen'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- MFC ActiveX controls [MFC], accessing invisible dialog controls
- MFC ActiveX controls [MFC], advanced topics
- FireError method [MFC]
- MFC ActiveX controls [MFC], database classes
- MFC ActiveX controls [MFC], special keys
- PreTranslateMessage method [MFC]
- MFC ActiveX controls [MFC], parameterized property
- ThrowError method [MFC]
ms.assetid: e9e34abb-8e2d-461e-bb9c-a1aec5dcecbd
ms.openlocfilehash: 87cc0000f74935990cb5956e0fb3afd44e01532b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624196"
---
# <a name="mfc-activex-controls-advanced-topics"></a>MFC-ActiveX-Steuerelemente: Weiterführende Themen

In diesem Artikel werden erweiterte Themen zum Entwickeln von ActiveX-Steuerelementen behandelt. Dazu gehören:

- [Verwenden von Datenbankklassen in ActiveX-Steuerelementen](#_core_using_database_classes_in_activex_controls)

- [Implementieren einer parametrisierten Eigenschaft](#_core_implementing_a_parameterized_property)

- [Behandeln von Fehlern in Ihrem ActiveX-Steuerelement](#_core_handling_errors_in_your_activex_control)

- [Behandeln von sonderschlüsseln im Steuerelement](#_core_handling_special_keys_in_your_control)

- [Zugreifen auf Dialog Feld Steuerelemente, die zur Laufzeit nicht sichtbar sind](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)

>[!IMPORTANT]
> ActiveX ist eine ältere Technologie, die nicht für die neue Entwicklung verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ersetzen, finden Sie unter ActiveX-Steuer [Elemente](activex-controls.md).

## <a name="using-database-classes-in-activex-controls"></a><a name="_core_using_database_classes_in_activex_controls"></a>Verwenden von Datenbankklassen in ActiveX-Steuerelementen

Da die ActiveX-Steuerelement Klassen in der Klassenbibliothek enthalten sind, können Sie dieselben Prozeduren und Regeln zum Verwenden von Datenbankklassen in einer MFC-Standardanwendung anwenden, um ActiveX-Steuerelemente zu entwickeln, die MFC-Datenbankklassen verwenden.

Eine allgemeine Übersicht über die MFC-Datenbankklassen finden Sie unter [MFC-Datenbankklassen (DAO und ODBC)](../data/mfc-database-classes-odbc-and-dao.md). Der Artikel führt sowohl die MFC-ODBC-Klassen als auch die MFC-DAO-Klassen ein und leitet Sie zu weiteren Details zu.

> [!NOTE]
> DAO wird über Office 2013 unterstützt. DAO 3,6 ist die endgültige Version, die als veraltet eingestuft wird. Der Visual C++ Umgebung und die Assistenten unterstützen DAO nicht (obwohl die DAO-Klassen eingeschlossen sind und Sie Sie weiterhin verwenden können). Microsoft empfiehlt, [OLE DB Vorlagen](../data/oledb/ole-db-programming.md) oder [ODBC und MFC](../data/odbc/odbc-and-mfc.md) für neue Projekte zu verwenden. Sie sollten DAO nur für die Wartung vorhandener Anwendungen verwenden.

## <a name="implementing-a-parameterized-property"></a><a name="_core_implementing_a_parameterized_property"></a>Implementieren einer parametrisierten Eigenschaft

Eine parametrisierte Eigenschaft (manchmal als Eigenschafts Array bezeichnet) ist eine Methode zum Bereitstellen einer homogenen Auflistung von Werten als einzelne Eigenschaft des Steuer Elements. Beispielsweise können Sie eine parametrisierte Eigenschaft verwenden, um ein Array oder ein Wörterbuch als Eigenschaft verfügbar zu machen. In Visual Basic erfolgt der Zugriff auf eine solche Eigenschaft mithilfe der Array Notation:

[!code-vb[NVC_MFC_AxVb#1](codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]

Verwenden Sie den Assistenten zum Hinzufügen von Eigenschaften, um eine parametrisierte Eigenschaft zu implementieren. Der Assistent zum Hinzufügen von Eigenschaften implementiert die-Eigenschaft durch Hinzufügen eines Paares von Get/Set-Funktionen, die dem Steuerelement Benutzer den Zugriff auf die Eigenschaft mithilfe der obigen Notation oder standardmäßig ermöglichen.

Ähnlich wie Methoden und Eigenschaften haben parametrisierte Eigenschaften auch eine Beschränkung auf die zulässige Anzahl von Parametern. Bei parametrisierten Eigenschaften beträgt der Grenzwert 15 Parameter (mit einem Parameter, der zum Speichern des Eigenschafts Werts reserviert ist).

Im folgenden Verfahren wird eine parametrisierte Eigenschaft namens Array hinzugefügt, auf die als zweidimensionales Array von ganzen Zahlen zugegriffen werden kann.

#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>So fügen Sie mithilfe des Assistenten zum Hinzufügen von Eigenschaften eine parametrisierte Eigenschaft hinzu

1. Laden Sie das Steuerelementprojekt.

1. Erweitern Sie in der Klassenansicht den Bibliotheksknoten des Steuerelements.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten des Steuerelements (den zweiten Knoten des Bibliotheksknotens), um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie dann auf **Eigenschaft hinzufügen**.

1. Geben Sie im Feld **Eigenschafts Name den Namen** ein `Array` .

1. Wählen Sie im Feld **Eigenschaftentyp** die Option **Short**aus.

1. Klicken Sie unter **Implementierungstyp auf** **Get/Set Methods**.

1. Geben Sie in den Feldern **Get Function** und **Set Function** eindeutige Namen für Ihre Get-und Set-Funktionen ein, oder übernehmen Sie die Standardnamen.

1. Fügen Sie einen Parameter namens *Row* (Type *Short*) mithilfe der **Parameter Name** und **Parametertyp** -Steuerelemente hinzu.

1. Fügen Sie einen zweiten Parameter mit dem Namen *Column* (Typ *Short*) hinzu.

1. Klicken Sie auf **Fertig stellen**.

### <a name="changes-made-by-the-add-property-wizard"></a>Vom Assistenten zum Hinzufügen von Eigenschaften vorgenommene Änderungen

Wenn Sie eine benutzerdefinierte Eigenschaft hinzufügen, nimmt der Assistent zum Hinzufügen von Eigenschaften Änderungen am Header der Steuerelement Klasse vor (. H) und die-Implementierung (. Cpp-Dateien.

Die folgenden Zeilen werden der Steuerelement Klasse hinzugefügt. H-Datei:

[!code-cpp[NVC_MFC_AxUI#35](codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]

Dieser Code deklariert zwei Funktionen `GetArray` `SetArray` mit dem Namen und, die es dem Benutzer ermöglichen, beim Zugriff auf die-Eigenschaft eine bestimmte Zeile und Spalte anzufordern.

Außerdem fügt der Assistent zum Hinzufügen von Eigenschaften der Steuerelement Dispatchzuordnung die folgenden Zeilen hinzu, die sich in der Implementierung der Steuerelement Klasse befinden (. Cpp-Datei:

[!code-cpp[NVC_MFC_AxUI#36](codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]

Schließlich werden die Implementierungen der `GetArray` - `SetArray` Funktion und der-Funktion am Ende der hinzugefügt. Cpp-Datei. In den meisten Fällen ändern Sie die Get-Funktion, um den Wert der-Eigenschaft zurückzugeben. Die Set-Funktion enthält normalerweise Code, der ausgeführt werden soll, entweder vor oder nach der Änderung der-Eigenschaft.

Damit diese Eigenschaft nützlich ist, können Sie eine zweidimensionale Array Element Variable in der Steuerelement Klasse, vom Typ **Short**, deklarieren, um Werte für die parametrisierte Eigenschaft zu speichern. Anschließend können Sie die Get-Funktion so ändern, dass Sie den Wert zurückgibt, der in der entsprechenden Zeile und Spalte gespeichert wird, wie in den Parametern angegeben, und die Set-Funktion ändern, um den Wert zu aktualisieren, auf den die Zeilen-und Spalten

## <a name="handling-errors-in-your-activex-control"></a><a name="_core_handling_errors_in_your_activex_control"></a>Behandeln von Fehlern in Ihrem ActiveX-Steuerelement

Wenn im Steuerelement Fehlerbedingungen auftreten, müssen Sie möglicherweise den Fehler an den Steuerelement Container melden. Es gibt zwei Methoden zum Melden von Fehlern, abhängig von der Situation, in der der Fehler auftritt. Wenn der Fehler in der Get-oder Set-Funktion einer Eigenschaft oder innerhalb der Implementierung einer OLE-Automatisierungs Methode auftritt, sollte das Steuerelement [COleControl:: ThrowError](reference/colecontrol-class.md#throwerror)aufruft, das dem Steuerelement Benutzer signalisiert, dass ein Fehler aufgetreten ist. Wenn der Fehler zu einem beliebigen Zeitpunkt auftritt, sollte das Steuerelement [COleControl:: FireError](reference/colecontrol-class.md#fireerror)aufzurufen, das ein Aktien Fehler Ereignis auslöst.

Um die Art des aufgetretenen Fehlers anzugeben, muss das Steuerelement einen Fehlercode an `ThrowError` oder übergeben `FireError` . Ein Fehlercode ist ein OLE-Statuscode, der über einen 32-Bit-Wert verfügt. Wählen Sie nach Möglichkeit einen Fehlercode aus dem Standardsatz von Codes aus, der in der OLECTL definiert ist. H-Header Datei. In der folgenden Tabelle werden diese Codes zusammengefasst.

### <a name="activex-control-error-codes"></a>ActiveX-Steuerelement-Fehler Codes

|Fehler|Beschreibung|
|-----------|-----------------|
|CTL_E_ILLEGALFUNCTIONCALL|Ungültiger Funktionsaufruf|
|CTL_E_OVERFLOW|Überlauf|
|CTL_E_OUTOFMEMORY|Nicht genügend Arbeitsspeicher|
|CTL_E_DIVISIONBYZERO|Division durch Null|
|CTL_E_OUTOFSTRINGSPACE|Nicht genügend Zeichenfolgenspeicher|
|CTL_E_OUTOFSTACKSPACE|Nicht genügend Stapelspeicher|
|CTL_E_BADFILENAMEORNUMBER|Der Dateiname oder die Zahl ist ungültig.|
|CTL_E_FILENOTFOUND|Datei nicht gefunden|
|CTL_E_BADFILEMODE|Fehlerhafter Dateimodus.|
|CTL_E_FILEALREADYOPEN|Die Datei ist bereits geöffnet.|
|CTL_E_DEVICEIOERROR|Geräte-E/A-Fehler|
|CTL_E_FILEALREADYEXISTS|Datei bereits vorhanden|
|CTL_E_BADRECORDLENGTH|Ungültige Datensatzlänge.|
|CTL_E_DISKFULL|Datenträger voll|
|CTL_E_BADRECORDNUMBER|Ungültige Datensatznummer|
|CTL_E_BADFILENAME|Ungültiger Dateiname|
|CTL_E_TOOMANYFILES|Zu viele Dateien|
|CTL_E_DEVICEUNAVAILABLE|Das Gerät ist nicht verfügbar|
|CTL_E_PERMISSIONDENIED|Berechtigung verweigert|
|CTL_E_DISKNOTREADY|Das Laufwerk ist nicht bereit|
|CTL_E_PATHFILEACCESSERROR|Pfad/Datei Zugriffsfehler|
|CTL_E_PATHNOTFOUND|Der Pfad wurde nicht gefunden|
|CTL_E_INVALIDPATTERNSTRING|Ungültige Musterzeichenfolge|
|CTL_E_INVALIDUSEOFNULL|Ungültige Verwendung von NULL.|
|CTL_E_INVALIDFILEFORMAT|Ungültiges Dateiformat|
|CTL_E_INVALIDPROPERTYVALUE|Ungültiger Eigenschafts Wert|
|CTL_E_INVALIDPROPERTYARRAYINDEX|Ungültiger Eigenschafts Array Index.|
|CTL_E_SETNOTSUPPORTEDATRUNTIME|"Set" wird zur Laufzeit nicht unterstützt|
|CTL_E_SETNOTSUPPORTED|"Set" wird nicht unterstützt (schreibgeschützte Eigenschaft)|
|CTL_E_NEEDPROPERTYARRAYINDEX|Ein Eigenschaftenarrayindex wird benötigt|
|CTL_E_SETNOTPERMITTED|"Set" ist unzulässig.|
|CTL_E_GETNOTSUPPORTEDATRUNTIME|'Get' wird zur Laufzeit nicht unterstützt.|
|CTL_E_GETNOTSUPPORTED|'Get' wird nicht unterstützt (lesegeschützte Eigenschaft).|
|CTL_E_PROPERTYNOTFOUND|Die Eigenschaft wurde nicht gefunden|
|CTL_E_INVALIDCLIPBOARDFORMAT|Ungültiges Zwischenablage Format|
|CTL_E_INVALIDPICTURE|Ungültiges Bild|
|CTL_E_PRINTERERROR|Druckerfehler|
|CTL_E_CANTSAVEFILETOTEMP|Datei kann nicht in Temp gespeichert werden.|
|CTL_E_SEARCHTEXTNOTFOUND|Suchtext wurde nicht gefunden|
|CTL_E_REPLACEMENTSTOOLONG|Die Ersetzungen sind zu lang|

Verwenden Sie ggf. das CUSTOM_CTL_SCODE-Makro, um einen benutzerdefinierten Fehlercode für eine Bedingung zu definieren, die nicht von einem der Standard Codes abgedeckt wird. Der-Parameter für dieses Makro muss eine ganze Zahl zwischen 1000 und 32767 (einschließlich) sein. Beispiel:

[!code-cpp[NVC_MFC_AxUI#37](codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]

Wenn Sie ein ActiveX-Steuerelement zum Ersetzen eines vorhandenen VBX-Steuer Elements erstellen, definieren Sie die Fehlercodes des ActiveX-Steuer Elements mit denselben numerischen Werten, die das VBX-Steuerelement verwendet, um sicherzustellen, dass die Fehlercodes kompatibel sind

## <a name="handling-special-keys-in-the-control"></a><a name="_core_handling_special_keys_in_your_control"></a>Behandeln von sonderschlüsseln im Steuerelement

In einigen Fällen möchten Sie möglicherweise bestimmte Tastenkombinationen auf besondere Weise verarbeiten. Fügen Sie beispielsweise eine neue Zeile ein, wenn die EINGABETASTE in einem mehrzeiligen Textfeld-Steuerelement gedrückt wird, oder wechseln Sie zwischen einer Gruppe von Bearbeitungs Steuerelementen, wenn eine direktionale Schlüssel-ID gedrückt

Wenn die Basisklasse des ActiveX-Steuer Elements ist `COleControl` , können Sie [CWnd::P retranslatemess Age](reference/cwnd-class.md#pretranslatemessage) überschreiben, um Nachrichten zu verarbeiten, bevor Sie vom Container verarbeitet werden. Wenn Sie diese Technik verwenden, wird immer **true** zurückgegeben, wenn Sie die Nachricht in ihrer außer Kraft Setzung von verarbeiten `PreTranslateMessage` .

Im folgenden Codebeispiel wird eine mögliche Möglichkeit zur Behandlung von Nachrichten veranschaulicht, die mit den direktionalen Schlüsseln verknüpft sind.

[!code-cpp[NVC_MFC_AxUI#38](codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]

Weitere Informationen zur Handhabung von Tastatur Schnittstellen für ein ActiveX-Steuerelement finden Sie in der ActiveX SDK-Dokumentation.

## <a name="accessing-dialog-controls-that-are-invisible-at-run-time"></a><a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a>Zugreifen auf Dialog Feld Steuerelemente, die zur Laufzeit nicht sichtbar sind

Sie können Dialogfeld Steuerelemente erstellen, die keine Benutzeroberfläche aufweisen und zur Laufzeit unsichtbar sind. Wenn Sie ein unsichtbares ActiveX-Steuerelement zur Laufzeit einem Dialogfeld hinzufügen und mit [CWnd:: GetDlgItem](reference/cwnd-class.md#getdlgitem) auf das Steuerelement zugreifen, funktioniert das Steuerelement nicht ordnungsgemäß. Verwenden Sie stattdessen eine der folgenden Verfahren, um ein-Objekt abzurufen, das das-Steuerelement darstellt:

- Wählen Sie mithilfe des Assistenten zum Hinzufügen von Element Variablen die Option **Steuerungs Variable** aus, und wählen Sie die ID des Steuer Elements Geben Sie einen Element Variablennamen ein, und wählen Sie die Wrapper Klasse des Steuer Elements als **Steuer Elementtyp**aus.

     - oder -

- Deklarieren Sie eine lokale Variable und eine Unterklasse als Dialogfeld Element. Fügen Sie Code ein, der dem folgenden ähnelt ( `CMyCtrl` ist die Wrapper Klasse, IDC_MYCTRL1 die ID des Steuer Elements ist):

   [!code-cpp[NVC_MFC_AxCont#19](codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)
