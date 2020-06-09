---
title: ActiveX-Steuerelemente für das Internet
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX controls [MFC], creating
- ActiveX controls [MFC], Internet
- downloading data with ActiveX controls
- OLE controls [MFC], upgrading to ActiveX
- Internet applications [MFC], ActiveX controls
- networks [MFC], downloading with ActiveX controls
ms.assetid: 7ab943c8-2022-41df-9065-d629b616eeec
ms.openlocfilehash: f06a6f6f71e922163fd95c59836c50b88b05ed3a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616478"
---
# <a name="activex-controls-on-the-internet"></a>ActiveX-Steuerelemente für das Internet

ActiveX-Steuerelemente sind die aktualisierte Version der OLE-Steuerelement Spezifikation.

>[!IMPORTANT]
> ActiveX ist eine ältere Technologie, die nicht für die neue Entwicklung verwendet werden sollte. Weitere Informationen finden Sie unter [ActiveX](activex-controls.md)-Steuerelemente.

Steuerelemente sind eine primäre Architektur zum entwickeln programmierbarer Softwarekomponenten, die in einer Vielzahl verschiedener Container verwendet werden können, einschließlich com-fähiger Webbrowser im Internet. Jedes ActiveX-Steuerelement kann ein Internet Steuerelement sein und seine Funktionalität einem aktiven Dokument hinzufügen oder Teil einer Webseite sein. Steuerelemente auf einer Webseite können mithilfe der Skripterstellung miteinander kommunizieren.

ActiveX-Steuerelemente sind nicht auf das Internet beschränkt. Ein ActiveX-Steuerelement kann auch in einem beliebigen Container verwendet werden, solange das Steuerelement die für diesen Container erforderlichen Schnittstellen unterstützt.

**ActiveX-Steuerelemente haben mehrere Vorteile, einschließlich:**

- Weniger erforderliche Schnittstellen als vorherige OLE-Steuerelemente.

- Die Möglichkeit, fensterlose und immer direkte aktive zu sein.

**Um ein ActiveX-Steuerelement zu sein, muss ein Steuerelement folgende Aktionen ausführen:**

- Unterstützung der- `IUnknown` Schnittstelle.

- Ist ein COM-Objekt.

- Exportieren Sie **DllRegisterServer** und **DllUnregisterServer**.

- Unterstützen Sie zusätzliche Schnittstellen nach Bedarf für die Funktionalität.

## <a name="making-your-existing-controls-internet-friendly"></a>Die vorhandenen Steuerelemente Internet freundlich gestalten

Wenn Sie ein Steuerelement entwerfen, das in einer Internet Umgebung gut funktioniert, müssen Sie die relativ geringen Übertragungsraten im Internet berücksichtigen. Sie können vorhandene Steuerelemente verwenden. Es gibt jedoch Schritte, die Sie durchführen sollten, um die Größe Ihres Codes zu verkleinern und die Steuerelement Eigenschaften asynchron herunterzuladen.

Um die Leistung Ihrer Steuerelemente zu verbessern, befolgen Sie die folgenden Tipps zu effizienzüberlegungen:

- Implementieren Sie die im Artikel ActiveX-Steuer [Elemente: Optimierung](mfc-activex-controls-optimization.md)beschriebenen Techniken.

- Beachten Sie, wie ein Steuerelement instanziiert wird.

- Asynchron sein; halten Sie keine anderen Programme an.

- Laden Sie Daten in kleinen Blöcken herunter.

   Wenn Sie große Datenströme wie Bitmaps oder Videodaten herunterladen, greifen Sie in Zusammenarbeit mit dem Container asynchron auf die Daten eines Steuer Elements zu. Rufen Sie die Daten inkrementell oder progressiv ab, und arbeiten Sie zusammen mit anderen Steuerelementen, die auch Daten abrufen können. Code kann auch asynchron heruntergeladen werden.

- Herunterladen von Code und Eigenschaften im Hintergrund.

- Die Benutzeroberfläche wird so schnell wie möglich aktiviert.

- Beachten Sie, wie persistente Daten gespeichert werden, sowohl Eigenschaften als auch große Daten-BLOB (z. b. ein Bitmap-Bild oder Videodaten).

   Steuerelemente mit erheblichen Mengen von persistenten Daten, wie z. b. große Bitmaps oder AVI-Dateien, erfordern eine sorgfältige Aufmerksamkeit beim Herunterladen der Methode. Ein Dokument oder eine Seite kann so bald wie möglich sichtbar werden, und der Benutzer kann mit der Seite interagieren, während Steuerelemente Daten im Hintergrund abrufen.

- Schreiben Sie effiziente Routinen, um die Codegröße und die Lauf Zeit Zeit zu unterhalten.

   Kleine Schaltflächen-und Bezeichnungs Steuerelemente, die nur wenige Bytes beständiger Daten verwenden, sind für die Verwendung in der Internet Umgebung geeignet und funktionieren gut in Browsern.

- Der Fortschritt wird an den Container übermittelt.

   Benachrichtigen Sie den Status des Containers im asynchronen Download, z. b., wenn der Benutzer mit der Interaktion mit einer Seite beginnen kann und wenn der Download abgeschlossen ist. Der Container kann dem Benutzer den Fortschritt (z. b. "Prozent abgeschlossen") anzeigen.

- Beachten Sie, wie Steuerelemente auf dem Client Computer registriert werden.

## <a name="creating-a-new-activex-control"></a>Erstellen eines neuen ActiveX-Steuer Elements

Beim Erstellen eines neuen Steuer Elements mithilfe des Anwendungs-Assistenten können Sie die Unterstützung für asynchrone Moniker und andere Optimierungen aktivieren. Gehen Sie folgendermaßen vor, um die Unterstützung zum asynchronen Herunterladen von Steuerungseigenschaften hinzuzufügen:

#### <a name="to-create-your-project-using-the-mfc-activex-control-wizard"></a>So erstellen Sie ein Projekt mit dem MFC-ActiveX-Steuerelement-Assistenten

1. Klicken Sie im Menü **Datei** auf **neu** .

1. Wählen Sie in den Visual Studio C++-Projekten den **MFC-ActiveX-Steuer** Element-Assistenten aus, und nennen Sie

1. Wählen Sie auf der Seite **Steuerungseinstellungen** die Option **Eigenschaften asynchron**laden aus. Wenn Sie diese Option auswählen, werden die Eigenschaft für den Bereitschafts Zustand und das Ereignis für den Status "bereit" angezeigt.

   Sie können auch andere Optimierungen auswählen, z. b. die **Fensterlose Aktivierung**, die unter ActiveX-Steuer [Elemente: Optimierung](mfc-activex-controls-optimization.md)beschrieben wird.

1. Klicken Sie auf **Fertig stellen**, um das Projekt zu erstellen.

#### <a name="to-create-a-class-derived-from-cdatapathproperty"></a>So erstellen Sie eine Klasse, die von CDataPathProperty abgeleitet ist

1. Erstellen Sie eine von abgeleitete Klasse `CDataPathProperty` .

1. Fügen Sie in jeder der Quelldateien, die die Header Datei für das Steuerelement enthalten, die Header Datei für diese Klasse hinzu.

1. Überschreiben Sie in dieser Klasse `OnDataAvailable` . Diese Funktion wird immer dann aufgerufen, wenn Daten für die Anzeige verfügbar sind. Wenn Daten verfügbar werden, können Sie Sie beliebig behandeln, z. b. durch progressiv Rendering.

   Der folgende Code Ausschnitt ist ein einfaches Beispiel für die schrittweise Anzeige von Daten in einem Bearbeitungs Steuerelement. Beachten Sie die Verwendung der Flag- **BSCF_FIRSTDATANOTIFICATION** , um das Bearbeitungs Steuerelement zu löschen.

   [!code-cpp[NVC_MFCActiveXControl#1](codesnippet/cpp/activex-controls-on-the-internet_1.cpp)]

   Beachten Sie, dass Sie AFXCMN einschließen müssen. H, um die-Klasse zu verwenden `CListCtrl` .

1. Wenn sich der Gesamtstatus Ihres Steuer Elements ändert (z. b. vom Laden in initialisiert oder User Interactive), wird aufgerufen `COleControl::InternalSetReadyState` . Wenn das Steuerelement nur über eine Datenpfad Eigenschaft verfügt, können Sie Code auf **BSCF_LASTDATANOTIFICATION** hinzufügen, um den Container zu benachrichtigen, dass der Download beendet ist. Beispiel:

   [!code-cpp[NVC_MFCActiveXControl#2](codesnippet/cpp/activex-controls-on-the-internet_2.cpp)]

1. Überschreiben Sie `OnProgress`. In erhalten `OnProgress` Sie eine Zahl, die den maximalen Bereich anzeigt, und eine Zahl, die anzeigt, wie weit das aktuelle herunterladen ist. Mit diesen Zahlen können Sie dem Benutzer den Status, z. b. den Prozentsatz, anzeigen.

Die nächste Prozedur fügt eine Eigenschaft zum-Steuerelement hinzu, um die soeben abgeleitete Klasse zu verwenden.

#### <a name="to-add-a-property"></a>So fügen Sie eine Eigenschaft hinzu

1. Klicken Sie in **Klassenansicht**mit der rechten Maustaste auf die Schnittstelle unterhalb des Knotens Bibliothek, und wählen Sie **Hinzufügen**und dann **Eigenschaft hinzufügen** Dadurch wird der **Assistent zum Hinzufügen von Eigenschaften**gestartet.

1. Aktivieren Sie im **Assistenten zum Hinzufügen von Eigenschaften**das Optionsfeld **Set/Get Methods** , geben Sie den **Eigenschaftsnamen**(z. b. editcontroltext) ein, und wählen Sie BSTR als **Eigenschaftentyp**aus.

1. Klicken Sie auf **Fertig stellen**.

1. Deklarieren Sie eine Member-Variable der von `CDataPathProperty` abgeleiteten Klasse in ihrer ActiveX-Steuerelement Klasse.

   [!code-cpp[NVC_MFCActiveXControl#3](codesnippet/cpp/activex-controls-on-the-internet_3.h)]

1. Implementieren Sie die `Get/Set`-Methoden. Geben Sie für `Get` die Zeichenfolge zurück. Laden Sie für `Set` die-Eigenschaft, und fordern Sie auf `SetModifiedFlag` .

   [!code-cpp[NVC_MFCActiveXControl#4](codesnippet/cpp/activex-controls-on-the-internet_4.cpp)]

1. Fügen Sie in [DoPropExchange](reference/colecontrol-class.md#dopropexchange)die folgende Zeile hinzu:

   [!code-cpp[NVC_MFCActiveXControl#5](codesnippet/cpp/activex-controls-on-the-internet_5.cpp)]

1. Überschreiben Sie [ResetData](reference/cdatapathproperty-class.md#resetdata) , um die Eigenschaft zu benachrichtigen, indem Sie die folgende Zeile hinzufügen:

   [!code-cpp[NVC_MFCActiveXControl#6](codesnippet/cpp/activex-controls-on-the-internet_6.cpp)]

## <a name="deciding-whether-to-derive-from-cdatapathproperty-or-ccacheddatapathproperty"></a>Entscheiden, ob von CDataPathProperty oder CCachedDataPathProperty abgeleitet werden soll

Im vorherigen Beispiel werden die Schritte zum Ableiten der-Eigenschaft des Steuer Elements von beschrieben `CDataPathProperty` . Dies ist eine gute Wahl, wenn Sie Echtzeitdaten herunterladen, die sich häufig ändern, und für die Sie nicht alle Daten beibehalten müssen, sondern nur den aktuellen Wert. Ein Beispiel hierfür ist ein Stock Ticker-Steuerelement.

Sie können auch von ableiten `CCachedDataPathProperty` . In diesem Fall werden die heruntergeladenen Daten in einer Speicherdatei zwischengespeichert. Dies ist eine gute Wahl, wenn Sie alle heruntergeladenen Daten beibehalten müssen, z. –. ein Steuerelement, das eine Bitmap progressiv rendert. In diesem Fall verfügt die-Klasse über eine Member-Variable, die Ihre Daten enthält:

`CMemFile m_Cache;`

In ihrer ActiveX-Steuerelement Klasse können Sie diese Speicher Abbild Datei in verwenden, `OnDraw` um die Daten anzuzeigen. Überschreiben Sie in der von einem ActiveX-Steuerelement `CCachedDataPathProperty` abgeleiteten Klasse die Member-Funktion, und machen Sie `OnDataAvailable` das Steuerelement ungültig, nachdem Sie die Basisklassen Implementierung aufgerufen

[!code-cpp[NVC_MFCActiveXControl#7](codesnippet/cpp/activex-controls-on-the-internet_7.cpp)]

## <a name="downloading-data-asynchronously-using-activex-controls"></a>Asynchrones Laden von Daten mit ActiveX-Steuerelementen

Das Herunterladen von Daten über ein Netzwerk muss asynchron erfolgen. Der Vorteil besteht darin, dass bei einer großen Datenmenge oder bei einer langsamen Verbindung vom Downloadprozess keine anderen Prozesse auf dem Client blockiert werden.

Asynchrone Moniker bieten eine Möglichkeit zum asynchronen Herunterladen von Daten über ein Netzwerk. Ein Lesevorgang für einen asynchronen Moniker wird sofort zurückgegeben, auch wenn der Vorgang nicht abgeschlossen wurde.

Wenn z. b. nur 10 Bytes verfügbar sind und lesen in einer 1K-Datei asynchron aufgerufen wird, wird lesen nicht blockiert, sondern mit den derzeit verfügbaren 10 Bytes zurückgegeben.

[Asynchrone Moniker](asynchronous-monikers-on-the-internet.md) werden mithilfe der- `CAsyncMonikerFile` Klasse implementiert. Allerdings können ActiveX-Steuerelemente die- `CDataPathProperty` Klasse verwenden, die von abgeleitet ist `CAsyncMonikerFile` , um die Implementierung von asynchronen Steuerelement Eigenschaften zu unterstützen.

## <a name="displaying-a-control-on-a-web-page"></a>Anzeigen eines Steuer Elements auf einer Webseite

Im folgenden finden Sie ein Beispiel für ein Objekttag und Attribute für das Einfügen eines Steuer Elements auf einer Webseite.

```xml
<OBJECT
  CLASSID="clsid:FC25B780-75BE-11CF-8B01-444553540000"
  CODEBASE="/ie/download/activex/iechart.ocx"
  ID=chart1
  WIDTH=400
  HEIGHT=200
  ALIGN=center
  HSPACE=0
  VSPACE=0>
  <PARAM NAME="BackColor" value="#ffffff"/>
  <PARAM NAME="ForeColor" value="#0000ff"/>
  <PARAM NAME="url" VALUE="/ie/controls/chart/mychart.txt"/>
</OBJECT>
```

## <a name="updating-an-existing-ole-control-to-use-new-activex-control-features"></a>Aktualisieren eines vorhandenen OLE-Steuer Elements zur Verwendung der neuen ActiveX-Steuerelement Features

Wenn Ihr OLE-Steuerelement mit einer Version von Visual C++ vor 4,2 erstellt wurde, können Sie Maßnahmen ergreifen, um die Leistung zu verbessern und die Funktionalität zu verbessern. Eine ausführliche Erläuterung dieser Änderungen finden Sie unter ActiveX-Steuer [Elemente: Optimierung](mfc-activex-controls-optimization.md).

Wenn Sie einem vorhandenen Steuerelement Unterstützung für asynchrone Eigenschaften hinzufügen, müssen Sie die Eigenschaft "Ready State" und das `ReadyStateChange` Ereignis selbst hinzufügen. Fügen Sie im Konstruktor für das Steuerelement Folgendes hinzu:

[!code-cpp[NVC_MFCActiveXControl#8](codesnippet/cpp/activex-controls-on-the-internet_8.cpp)]

Wenn Sie den Code herunterladen, aktualisieren Sie den Status "bereit", indem Sie [COleControl:: InternalSetReadyState](reference/colecontrol-class.md#internalsetreadystate)aufrufen. Ein Ort, den Sie anrufen können, `InternalSetReadyState` ist die `OnProgress` außer Kraft setzung der von `CDataPathProperty` abgeleiteten Klasse.

## <a name="see-also"></a>Siehe auch

[MFC-Internetprogrammierungsaufgaben](mfc-internet-programming-tasks.md)<br/>
[Grundlagen der MFC-Internetprogrammierung](mfc-internet-programming-basics.md)
