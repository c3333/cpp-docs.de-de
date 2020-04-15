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
ms.openlocfilehash: c5e3be3915a0707f8df17d3c9ebe2eb0e4f623b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364641"
---
# <a name="mfc-activex-controls-advanced-topics"></a>MFC-ActiveX-Steuerelemente: Weiterführende Themen

Dieser Artikel behandelt erweiterte Themen im Zusammenhang mit der Entwicklung von ActiveX-Steuerelementen. Dazu gehören:

- [Verwenden von Datenbankklassen in ActiveX-Steuerelementen](#_core_using_database_classes_in_activex_controls)

- [Implementieren einer Parameterized-Eigenschaft](#_core_implementing_a_parameterized_property)

- [Behandeln von Fehlern in Ihrem ActiveX-Steuerelement](#_core_handling_errors_in_your_activex_control)

- [Handhabung von Spezialschlüsseln in der Steuerung](#_core_handling_special_keys_in_your_control)

- [Zugriff auf Dialogsteuerelemente, die zur Laufzeit unsichtbar sind](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)

>[!IMPORTANT]
> ActiveX ist eine legacy Technologie, die nicht für Neuentwicklungen verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ablösen, finden Sie unter [ActiveX Controls](activex-controls.md).

## <a name="using-database-classes-in-activex-controls"></a><a name="_core_using_database_classes_in_activex_controls"></a>Verwenden von Datenbankklassen in ActiveX-Steuerelementen

Da die ActiveX-Steuerelementklassen Teil der Klassenbibliothek sind, können Sie dieselben Prozeduren und Regeln für die Verwendung von Datenbankklassen in einer Standard-MFC-Anwendung auf das Entwickeln von ActiveX-Steuerelementen anwenden, die die MFC-Datenbankklassen verwenden.

Eine allgemeine Übersicht über die MFC-Datenbankklassen finden Sie unter [MFC-Datenbankklassen (DAO und ODBC)](../data/mfc-database-classes-odbc-and-dao.md). Der Artikel stellt sowohl die MFC ODBC-Klassen als auch die MFC DAO-Klassen vor und weist Sie zu weiteren Details auf beiden.

> [!NOTE]
> DAO wird über Office 2013 unterstützt. DAO 3.6 ist die endgültige Version und gilt als veraltet. Die Visual C++-Umgebung und die Assistenten unterstützen DAO nicht (obwohl die DAO-Klassen enthalten sind und Sie sie weiterhin verwenden können). Microsoft empfiehlt, [OLE DB-Vorlagen](../data/oledb/ole-db-programming.md) oder [ODBC und MFC](../data/odbc/odbc-and-mfc.md) für neue Projekte zu verwenden. Sie sollten DAO nur bei der Verwaltung vorhandener Anwendungen verwenden.

## <a name="implementing-a-parameterized-property"></a><a name="_core_implementing_a_parameterized_property"></a>Implementieren einer Parameterized-Eigenschaft

Eine parametrisierte Eigenschaft (manchmal auch als Eigenschaftsarray bezeichnet) ist eine Methode zum Verfügbarmachen einer homogenen Auflistung von Werten als eine einzelne Eigenschaft des Steuerelements. Sie können z. B. eine parametrisierte Eigenschaft verwenden, um ein Array oder ein Wörterbuch als Eigenschaft verfügbar zu machen. In Visual Basic wird auf eine solche Eigenschaft mithilfe der Arraynotation zugegriffen:

[!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]

Verwenden Sie den Assistenten zum Hinzufügen von Eigenschaften, um eine parametrisierte Eigenschaft zu implementieren. Der Eigenschaften-Assistent zum Hinzufügen implementiert die Eigenschaft, indem er ein Paar von Get/Set-Funktionen hinzufügt, die es dem Steuerelementbenutzer ermöglichen, mithilfe der obigen Notation oder in der Standardmethode auf die Eigenschaft zuzugreifen.

Ähnlich wie Methoden und Eigenschaften haben parametrisierte Eigenschaften auch eine Begrenzung auf die Anzahl der zulässigen Parameter. Bei parametrisierten Eigenschaften beträgt der Grenzwert 15 Parameter (wobei ein Parameter für die Speicherung des Eigenschaftswerts reserviert ist).

Mit der folgenden Prozedur wird eine parametrisierte Eigenschaft namens Array hinzugefügt, auf die als zweidimensionales Array ganzer Zahlen zugegriffen werden kann.

#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>So fügen Sie eine parametrisierte Eigenschaft mithilfe des Eigenschaften-Assistenten hinzufügen

1. Laden Sie das Steuerelementprojekt.

1. Erweitern Sie in der Klassenansicht den Bibliotheksknoten des Steuerelements.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten des Steuerelements (den zweiten Knoten des Bibliotheksknotens), um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** und dann auf **Eigenschaft hinzufügen**.

1. Geben Sie `Array`im Feld **Eigenschaftenname** .

1. Wählen Sie im Feld **Eigenschaftentyp** **kurze**aus.

1. Klicken Sie für **Implementierungstyp** auf **Methoden abrufen/festlegen**.

1. Geben Sie in die Felder **Funktion abrufen** und **Funktion festlegen** festlegen eindeutige Namen für Ihre Get- und Set-Funktionen ein, oder akzeptieren Sie die Standardnamen.

1. Fügen Sie einen Parameter hinzu, der als *zeile* (typ *short*) bezeichnet wird, mit den Steuerelementen **Parametername** und **Parametertyp.**

1. Fügen Sie einen zweiten Parameter namens *Spalte* hinzu (Typ *kurz*).

1. Klicken Sie auf **Fertig stellen**.

### <a name="changes-made-by-the-add-property-wizard"></a>Änderungen, die vom Assistenten zum Hinzufügen von Eigenschaften vorgenommen wurden

Wenn Sie eine benutzerdefinierte Eigenschaft hinzufügen, nimmt der Assistenten zum Hinzufügen von Eigenschaften Änderungen am Steuerelementklassenheader (. H) und die Umsetzung (. CPP)-Dateien.

Die folgenden Zeilen werden der Steuerelementklasse hinzugefügt. H-Datei:

[!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]

Dieser Code deklariert `GetArray` zwei `SetArray` aufgerufene Funktionen, die es dem Benutzer ermöglichen, beim Zugriff auf die Eigenschaft eine bestimmte Zeile und Spalte anzufordern.

Darüber hinaus fügt der Assistent eigenschaften hinzufügen die folgenden Zeilen zur Steuerelementdispatchzuordnung hinzu, die sich in der Implementierung der Steuerelementklassen (. CPP)-Datei:

[!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]

Schließlich werden die Implementierungen der `GetArray` und `SetArray` Funktionen am Ende der hinzugefügt. CPP-Datei. In den meisten Fällen ändern Sie die Get-Funktion, um den Wert der Eigenschaft zurückzugeben. Die Set-Funktion enthält in der Regel Code, der entweder vor oder nach den Änderungen der Eigenschaft ausgeführt werden soll.

Damit diese Eigenschaft nützlich ist, können Sie eine zweidimensionale Arraymembervariable in der Steuerelementklasse vom Typ **short**deklarieren, um Werte für die parametrierte Eigenschaft zu speichern. Sie können dann die Get-Funktion ändern, um den Wert zurückzugeben, der in der richtigen Zeile und Spalte gespeichert ist, wie durch die Parameter angegeben, und die Set-Funktion ändern, um den Wert zu aktualisieren, auf den durch die Zeilen- und Spaltenparameter verwiesen wird.

## <a name="handling-errors-in-your-activex-control"></a><a name="_core_handling_errors_in_your_activex_control"></a>Behandeln von Fehlern in Ihrem ActiveX-Steuerelement

Wenn Fehlerbedingungen im Steuerelement auftreten, müssen Sie den Fehler möglicherweise an den Steuerelementcontainer melden. Es gibt zwei Methoden zum Melden von Fehlern, abhängig von der Situation, in der der Fehler auftritt. Wenn der Fehler innerhalb der Get- oder Set-Funktion einer Eigenschaft oder innerhalb der Implementierung einer OLE-Automatisierungsmethode auftritt, sollte das Steuerelement [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror)aufrufen, das dem Steuerelementbenutzer signalisiert, dass ein Fehler aufgetreten ist. Wenn der Fehler zu einem anderen Zeitpunkt auftritt, sollte das Steuerelement [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror)aufrufen, das ein Bestandsfehlerereignis auslöst.

Um die Art des aufgetretenen Fehlers anzugeben, muss `ThrowError` `FireError`das Steuerelement einen Fehlercode an oder übergeben. Ein Fehlercode ist ein OLE-Statuscode, der einen 32-Bit-Wert hat. Wählen Sie nach Möglichkeit einen Fehlercode aus dem im OLECTL definierten Standardcodesatz aus. H-Headerdatei. Die folgende Tabelle fasst diese Codes zusammen.

### <a name="activex-control-error-codes"></a>ActiveX-Steuerungsfehlercodes

|Fehler|BESCHREIBUNG|
|-----------|-----------------|
|CTL_E_ILLEGALFUNCTIONCALL|Unzulässiger Funktionsaufruf|
|CTL_E_OVERFLOW|Überlauf|
|CTL_E_OUTOFMEMORY|Nicht genügend Arbeitsspeicher.|
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
|CTL_E_DISKFULL|Festplatte voll|
|CTL_E_BADRECORDNUMBER|Ungültige Datensatznummer|
|CTL_E_BADFILENAME|Ungültiger Dateiname|
|CTL_E_TOOMANYFILES|Zu viele Dateien|
|CTL_E_DEVICEUNAVAILABLE|Das Gerät ist nicht verfügbar|
|CTL_E_PERMISSIONDENIED|Berechtigung verweigert|
|CTL_E_DISKNOTREADY|Das Laufwerk ist nicht bereit|
|CTL_E_PATHFILEACCESSERROR|Pfad-/Dateizugriffsfehler|
|CTL_E_PATHNOTFOUND|Der Pfad wurde nicht gefunden|
|CTL_E_INVALIDPATTERNSTRING|Ungültige Musterzeichenfolge|
|CTL_E_INVALIDUSEOFNULL|Ungültige Verwendung von NULL|
|CTL_E_INVALIDFILEFORMAT|Ungültiges Dateiformat|
|CTL_E_INVALIDPROPERTYVALUE|Ungültiger Eigenschaftswert|
|CTL_E_INVALIDPROPERTYARRAYINDEX|Ungültiger Eigenschaftenarrayindex|
|CTL_E_SETNOTSUPPORTEDATRUNTIME|"Set" wird zur Laufzeit nicht unterstützt|
|CTL_E_SETNOTSUPPORTED|"Set" wird nicht unterstützt (schreibgeschützte Eigenschaft)|
|CTL_E_NEEDPROPERTYARRAYINDEX|Ein Eigenschaftenarrayindex wird benötigt|
|CTL_E_SETNOTPERMITTED|"Set" ist unzulässig.|
|CTL_E_GETNOTSUPPORTEDATRUNTIME|'Get' wird zur Laufzeit nicht unterstützt.|
|CTL_E_GETNOTSUPPORTED|'Get' wird nicht unterstützt (lesegeschützte Eigenschaft).|
|CTL_E_PROPERTYNOTFOUND|Die Eigenschaft wurde nicht gefunden|
|CTL_E_INVALIDCLIPBOARDFORMAT|Ungültiges Zwischenablageformat|
|CTL_E_INVALIDPICTURE|Ungültiges Bild|
|CTL_E_PRINTERERROR|Druckerfehler|
|CTL_E_CANTSAVEFILETOTEMP|Datei kann nicht in TEMP gespeichert werden|
|CTL_E_SEARCHTEXTNOTFOUND|Suchtext wurde nicht gefunden|
|CTL_E_REPLACEMENTSTOOLONG|Die Ersetzungen sind zu lang|

Verwenden Sie ggf. das CUSTOM_CTL_SCODE Makro, um einen benutzerdefinierten Fehlercode für eine Bedingung zu definieren, die nicht von einem der Standardcodes abgedeckt ist. Der Parameter für dieses Makro sollte eine ganze Zahl zwischen 1000 und 32767 sein, einschließlich. Beispiel:

[!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]

Wenn Sie ein ActiveX-Steuerelement erstellen, um ein vorhandenes VBX-Steuerelement zu ersetzen, definieren Sie Ihre ActiveX-Steuerelementfehlercodes mit denselben numerischen Werten, die das VBX-Steuerelement verwendet, um sicherzustellen, dass die Fehlercodes kompatibel sind.

## <a name="handling-special-keys-in-the-control"></a><a name="_core_handling_special_keys_in_your_control"></a>Handhabung von Spezialschlüsseln in der Steuerung

In einigen Fällen können Sie bestimmte Tastenkombinationen auf besondere Weise behandeln möchten; Fügen Sie z. B. eine neue Zeile ein, wenn die ENTER-Taste in ein mehrzeiliges Textfeldsteuerelement gedrückt wird, oder wechseln Sie zwischen einer Gruppe von Bearbeitungssteuerelementen, wenn eine Richtungsschlüssel-ID gedrückt wird.

Wenn die Basisklasse Ihres ActiveX-Steuerelements lautet, `COleControl`können Sie [CWnd::PreTranslateMessage](../mfc/reference/cwnd-class.md#pretranslatemessage) überschreiben, um Nachrichten zu verarbeiten, bevor der Container sie verarbeitet. Wenn Sie diese Technik **TRUE** verwenden, geben Sie immer TRUE `PreTranslateMessage`zurück, wenn Sie die Nachricht in Ihrer Außerkraftsetzung von behandeln.

Das folgende Codebeispiel veranschaulicht eine mögliche Möglichkeit, Meldungen im Zusammenhang mit den Richtungsschlüsseln zu behandeln.

[!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]

Weitere Informationen zum Umgang mit Tastaturschnittstellen für ein ActiveX-Steuerelement finden Sie in der ActiveX SDK-Dokumentation.

## <a name="accessing-dialog-controls-that-are-invisible-at-run-time"></a><a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a>Zugriff auf Dialogsteuerelemente, die zur Laufzeit unsichtbar sind

Sie können Dialogsteuerelemente erstellen, die über keine Benutzeroberfläche verfügen und zur Laufzeit unsichtbar sind. Wenn Sie ein unsichtbares ActiveX-Steuerelement zur Laufzeit zu einem Dialogfeld hinzufügen und [CWnd::GetDlgItem](../mfc/reference/cwnd-class.md#getdlgitem) für den Zugriff auf das Steuerelement verwenden, funktioniert das Steuerelement nicht ordnungsgemäß. Stattdessen sollten Sie eine der folgenden Techniken verwenden, um ein Objekt zu erhalten, das das Steuerelement darstellt:

- Wählen Sie mit dem Assistenten zum Hinzufügen von Elementvariablen die Option **Steuervariable** aus, und wählen Sie dann die ID des Steuerelements aus. Geben Sie einen Membervariablennamen ein, und wählen Sie die Wrapperklasse des Steuerelements als **Steuerelementtyp aus.**

     - oder -

- Deklarieren Sie eine lokale Variable und Unterklasse als Dialogelement. Fügen Sie Code ein,`CMyCtrl` der dem folgenden ähnelt (ist die Wrapperklasse, IDC_MYCTRL1 die ID des Steuerelements ist):

   [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)
