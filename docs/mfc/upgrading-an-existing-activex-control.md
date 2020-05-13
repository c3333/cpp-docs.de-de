---
title: Upgrading eines vorhandenen ActiveX-Steuerelements
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX controls [MFC], Internet
- LPK files for Internet controls
- safe for scripting and initialization (controls)
- OLE controls [MFC], upgrading to ActiveX
- CAB files, for ActiveX controls
- Internet applications [MFC], ActiveX controls
- Internet applications [MFC], packaging code for download
- upgrading ActiveX controls
- licensing ActiveX controls
ms.assetid: 4d12ddfa-b491-4f9f-a0b7-b51458e05651
ms.openlocfilehash: dfee42369b698956f4f91ab61a1f37e0ef06d9f1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754507"
---
# <a name="upgrading-an-existing-activex-control"></a>Upgrading eines vorhandenen ActiveX-Steuerelements

Vorhandene ActiveX-Steuerelemente (früher OLE-Steuerelemente) können ohne Änderungen im Internet verwendet werden. Sie können jedoch Steuerelemente ändern, um deren Leistung zu verbessern.

> [!IMPORTANT]
> ActiveX ist eine legacy Technologie, die nicht für Neuentwicklungen verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ablösen, finden Sie unter [ActiveX Controls](activex-controls.md).

Wenn Sie das Steuerelement auf einer Webseite verwenden, gibt es zusätzliche Überlegungen. Die .ocx-Datei und alle unterstützenden Dateien müssen sich auf dem Zielcomputer befinden oder über das Internet heruntergeladen werden. Dies macht die Codegröße und Downloadzeit zu einer wichtigen Überlegung. Downloads können in einer signierten CAB-Datei verpackt werden. Sie können Ihr Steuerelement als sicher für die Skripterstellung und als sicher für die Initialisierung markieren.

In diesem Artikel werden die folgenden Themen behandelt:

- [Verpackungscode zum Herunterladen](#_core_packaging_code_for_downloading)

- [Markieren eines Kontrollsafes für Skripterstellung und Initialisierung](#_core_marking_a_control_safe_for_scripting_and_initializing)

- [Lizenzierungsprobleme](#_core_licensing_issues)

- [Signaturcode](#_core_signing_code)

- [Verwalten der Palette](#_core_managing_the_palette)

- [Internet Explorer Browser-Sicherheitsstufen und Kontrollverhalten](#_core_internet_explorer_browser_safety_levels_and_control_behavior)

Sie können auch Optimierungen hinzufügen, wie unter [ActiveX-Steuerelemente: Optimierung](../mfc/mfc-activex-controls-optimization.md)beschrieben. Moniker können verwendet werden, um Eigenschaften und große BLOBs asynchron herunterzuladen, wie unter [ActiveX-Steuerelemente im Internet](../mfc/activex-controls-on-the-internet.md)beschrieben.

## <a name="packaging-code-for-downloading"></a><a name="_core_packaging_code_for_downloading"></a>Verpackungscode zum Herunterladen

Weitere Informationen zu diesem Thema finden Sie unter [Verpacken von ActiveX-Steuerelementen](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa751974%28v%3dvs.85%29).

### <a name="the-codebase-tag"></a>Das CODEBASE-Tag

ActiveX-Steuerelemente werden mithilfe `<OBJECT>` des Tags in Webseiten eingebettet. Der `CODEBASE` Parameter `<OBJECT>` des Tags gibt den Speicherort an, von dem das Steuerelement heruntergeladen werden soll. `CODEBASE`kann erfolgreich auf eine Reihe verschiedener Dateitypen verweisen.

### <a name="using-the-codebase-tag-with-an-ocx-file"></a>Verwenden des CODEBASE-Tags mit einer OCX-Datei

```
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"
```

Diese Lösung lädt nur die .ocx-Datei des Steuerelements herunter und erfordert, dass alle unterstützenden DLLs bereits auf dem Clientcomputer installiert sind. Dies funktioniert für Internet Explorer- und MFC ActiveX-Steuerelemente, die mit Visual C++ erstellt wurden, da Internet Explorer mit den unterstützenden DLLs für Visual C++-Steuerelemente ausgeliefert wird. Wenn zum Anzeigen dieses Steuerelements ein anderer Internetbrowser verwendet wird, der ActiveX-steuerelementfähig ist, funktioniert diese Lösung nicht.

### <a name="using-the-codebase-tag-with-an-inf-file"></a>Verwenden des CODEBASE-Tags mit einer INF-Datei

```
CODEBASE="http://example.microsoft.com/trustme.inf"
```

Eine .inf-Datei steuert die Installation einer .ocx und ihrer unterstützenden Dateien. Diese Methode wird nicht empfohlen, da es nicht möglich ist, eine INF-Datei zu signieren (siehe [Signaturcode](#_core_signing_code) für Zeiger auf die Codesignatur).

### <a name="using-the-codebase-tag-with-a-cab-file"></a>Verwenden des CODEBASE-Tags mit einer CAB-Datei

```
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"
```

Ablagedateien sind die empfohlene Methode zum Verpacken von ActiveX-Steuerelementen, die MFC verwenden. Durch das Verpacken eines MFC ActiveX-Steuerelements in einer Ablagedatei kann eine Inf-Datei eingeschlossen werden, um die Installation des ActiveX-Steuerelements und aller abhängigen DLLs (z. B. der MFC-DLLs) zu steuern. Durch die Verwendung einer CAB-Datei wird der Code automatisch komprimiert, um ihn schneller herunterzuladen. Wenn Sie eine CAB-Datei für den Komponentendownload verwenden, ist es schneller, die gesamte CAB-Datei als jede einzelne Komponente zu signieren.

### <a name="creating-cab-files"></a>Erstellen von CAB-Dateien

Tools zum Erstellen von Ablagedateien sind jetzt Teil des [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk).

Die Ablagedatei, `CODEBASE` auf die verwiesen wird, sollte die .ocx-Datei für Ihr ActiveX-Steuerelement und eine INf-Datei enthalten, um die Installation zu steuern. Sie erstellen die Ablagedatei, indem Sie den Namen der Steuerdatei und eine INF-Datei angeben. Schließen Sie keine abhängigen DLLs ein, die möglicherweise bereits auf dem System vorhanden sind, in dieser Ablagedatei. Beispielsweise werden die MFC-DLLs in einer separaten Ablagedatei verpackt und von der steuernden .inf-Datei erwähnt.

Weitere Informationen zum Erstellen einer CAB-Datei finden Sie unter [Erstellen einer CAB-Datei](/windows/win32/devnotes/cabinet-api-functions).

### <a name="the-inf-file"></a>Die INF-Datei

Im folgenden Beispiel, spindial.inf, werden die unterstützenden Dateien und die Versionsinformationen aufgeführt, die für das MFC Spindial-Steuerelement erforderlich sind. Beachten Sie, dass der Speicherort für die MFC-DLLs eine Microsoft-Website ist. Die mfc42.cab wird von Microsoft bereitgestellt und signiert.

```
Contents of spindial.inf:
[mfc42installer]
file-win32-x86=http://activex.microsoft.com/controls/vc/mfc42.cab
[Olepro32.dll] - FileVersion=5,
    0,
    4261,
    0
[Mfc42.dll] - FileVersion=6,
    0,
    8168,
    0
[Msvcrt.dll] - FileVersion=6,
    0,
    8168,
    0
```

### <a name="the-object-tag"></a>Der \<OBJECT> Tag

Das folgende Beispiel veranschaulicht `<OBJECT>` die Verwendung des Tags zum Verpacken des MFC Spindial-Beispielsteuerelements.

```
<OBJECT ID="Spindial1" WIDTH=100 HEIGHT=51
    CLASSID="CLSID:06889605-B8D0-101A-91F1-00608CEAD5B3"
    CODEBASE="http://example.microsoft.com/spindial.cab#Version=1,0,0,001">
<PARAM NAME="_Version" VALUE="65536">
<PARAM NAME="_ExtentX" VALUE="2646">
<PARAM NAME="_ExtentY" VALUE="1323">
<PARAM NAME="_StockProps" VALUE="0">
<PARAM NAME="NeedlePosition" VALUE="2">
</OBJECT>
```

In diesem Fall enthält spindial.cab zwei Dateien, spindial.ocx und spindial.inf. Der folgende Befehl erstellt die Ablagedatei:

```
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf
```

Der `-s 6144` Parameter reserviert Platz in der Ablage für die Codesignatur.

### <a name="the-version-tag"></a>Das Versions-Tag

Beachten Sie `#Version` hier, dass die mit einer CAB-Datei angegebenen Informationen `<OBJECT>` für das Steuerelement gelten, das durch den *CLASSID-Parameter* des Tags angegeben wird.

Abhängig von der angegebenen Version können Sie den Download Dessteuerelement erzwingen. Vollständige Spezifikationen des `OBJECT` Tags einschließlich des *CODEBASE-Parameters* finden Sie in der W3C-Referenz.

## <a name="marking-a-control-safe-for-scripting-and-initializing"></a><a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a>Markieren eines Kontrollsafes für Skripterstellung und Initialisierung

ActiveX-Steuerelemente, die in Webseiten verwendet werden, sollten als sicher für Skripting und sicher für die Initialisierung markiert werden, wenn sie tatsächlich sicher sind. Ein sicheres Steuerelement führt keine Datenträger-E/A aus oder greift nicht direkt auf den Speicher oder die Register eines Computers zu.

Steuerelemente können als sicher für Skripting und sicher für die Initialisierung über die Registrierung markiert werden. Ändern `DllRegisterServer` Sie diese, um Einträge hinzuzufügen, die den folgenden ähneln, um das Steuerelement als sicher für Skripterstellung und Persistenz in der Registrierung zu markieren. Eine alternative Methode `IObjectSafety`ist die Implementierung von .

Sie definieren GUIDs (Globally Unique Identifiers) für Ihr Steuerelement, um es für Skripting und Persistenz sicher zu markieren. Steuerelemente, die sicher skriptgesteuert werden können, enthalten einen Registrierungseintrag ähnlich dem folgenden:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
```

Steuerelemente, die sicher aus persistenten Daten initialisiert werden können, werden für die Persistenz mit einem Registrierungseintrag wie:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

Fügen Sie Einträge hinzu, die den folgenden ähneln (ersetzen `{06889605-B8D0-101A-91F1-00608CEAD5B3}`Sie die Klassen-ID des Steuerelements anstelle von ), um Ihre Schlüssel der folgenden Klassen-ID zuzuordnen:

```
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

## <a name="licensing-issues"></a><a name="_core_licensing_issues"></a>Lizenzierungsprobleme

Wenn Sie ein lizenziertes Steuerelement auf einer Webseite verwenden möchten, müssen Sie überprüfen, ob der Lizenzvertrag die Verwendung im Internet zulässt, und eine Lizenzpaketdatei (LPK) dafür erstellen.

Ein lizenziertes ActiveX-Steuerelement wird nicht ordnungsgemäß in eine HTML-Seite geladen, wenn der Computer, auf dem Internet Explorer ausgeführt wird, nicht für die Verwendung des Steuerelements lizenziert ist. Wenn z. B. ein lizenziertes Steuerelement mit Visual C++ erstellt wurde, wird die HTML-Seite, die das Steuerelement verwendet, ordnungsgemäß auf den Computer geladen, auf dem das Steuerelement erstellt wurde, aber es wird nicht auf einen anderen Computer geladen, es sei denn, es sind Lizenzinformationen enthalten.

Um ein lizenziertes ActiveX-Steuerelement in Internet Explorer zu verwenden, müssen Sie die Lizenzvereinbarung des Kreditors überprüfen, um zu überprüfen, ob die Lizenz für das Steuerelement Folgendes zulässt:

- Weiterverteilung

- Verwendung des Steuerelements im Internet

- Verwendung des Codebase-Parameters

Um ein lizenziertes Steuerelement auf einer HTML-Seite auf einem nicht lizenzierten Computer zu verwenden, müssen Sie eine Lizenzpaketdatei (LpK) generieren. Die LPK-Datei enthält Laufzeitlizenzen für lizenzierte Steuerelemente auf der HTML-Seite. Diese Datei wird über LPK_TOOL generiert. EXE, das mit dem ActiveX SDK enthalten ist.

#### <a name="to-create-an-lpk-file"></a>So erstellen Sie eine LPK-Datei

1. Führen Sie LPK_TOOL aus. EXE auf einem Computer, der für die Verwendung des Steuerelements lizenziert ist.

1. Wählen Sie im Dialogfeld **Lizenzpaket-Authoring-Tool** im Listenfeld **Verfügbare Steuerelemente** jedes lizenzierte ActiveX-Steuerelement aus, das auf der HTML-Seite verwendet wird, und klicken Sie auf **Hinzufügen**.

1. Klicken Sie auf **& Beenden speichern,** und geben Sie einen Namen für die LPK-Datei ein. Dadurch wird die LPK-Datei erstellt und die Anwendung geschlossen.

#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>So betten Sie ein lizenziertes Steuerelement auf einer HTML-Seite ein

1. Bearbeiten Sie Ihre HTML-Seite. Fügen Sie auf der \<HTML-Seite ein OBJECT>-Tag für das License Manager-Objekt ein, bevor andere \<OBJECT-> Tags. Der Lizenz-Manager ist ein ActiveX-Steuerelement, das mit Internet Explorer installiert ist. Die Klassen-ID wird unten angezeigt. Legen Sie die LPKPath-Eigenschaft des License Manager-Objekts auf den Pfad und den Namen der LPK-Datei fest. Sie können nur eine LPK-Datei pro HTML-Seite haben.

```
<OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">
</OBJECT>
```

1. Fügen \<Sie das OBJEKT->-Tag für Ihr lizenziertes Steuerelement nach dem License Manager-Tag ein.

   Im Folgenden wird z. B. eine HTML-Seite angezeigt, auf der das Steuerelement "Microsoft Masked Edit" angezeigt wird. Die erste Klassen-ID ist für das License Manager-Steuerelement, die ID der zweiten Klasse für das Masked Edit-Steuerelement. Ändern Sie die Tags so, dass sie auf den relativen Pfad der zuvor erstellten .lpk-Datei verweisen, und fügen Sie ein Objekt-Tag mit der Klassen-ID für das Steuerelement hinzu.

1. Fügen \<Sie das EMBED->-Attribut für Ihre LPK-Datei ein, wenn Sie das NCompass ActiveX-Plug-In verwenden.

   Wenn Ihr Steuerelement in anderen Aktiv-aktivierten Browsern angezeigt werden kann, z. B. Netscape mit dem NCompass ActiveX-Plug-In, müssen Sie die \<EMBED->-Syntax hinzufügen, wie unten gezeigt.

```
<OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="maskedit.lpk">

<EMBED SRC = "maskedit.LPK">

</OBJECT>
<OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>
</OBJECT>
```

Weitere Informationen zur Steuerelementlizenzierung finden Sie unter [ActiveX-Steuerelemente: Lizenzierung eines ActiveX-Steuerelements](../mfc/mfc-activex-controls-licensing-an-activex-control.md).

## <a name="signing-code"></a><a name="_core_signing_code"></a>Signaturcode

Die Codesignatur dient dazu, die Codequelle zu identifizieren und sicherzustellen, dass sich der Code seit der Signatur nicht geändert hat. Abhängig von den Sicherheitseinstellungen des Browsers können Benutzer gewarnt werden, bevor der Code heruntergeladen wird. Benutzer können bestimmten Zertifikatsbesitzern oder Unternehmen vertrauen, in diesem Fall wird der von den Vertrauenswürdigen signierte Code ohne Vorwarnung heruntergeladen. Code ist digital signiert, um Manipulationen zu vermeiden.

Stellen Sie sicher, dass Ihr endgültiger Code signiert ist, damit das Steuerelement automatisch heruntergeladen werden kann, ohne vertrauenswürdige Warnmeldungen anzuzeigen. Weitere Informationen zum Signieren von Code finden Sie in der Dokumentation zu Authenticode im ActiveX SDK und unter [Signieren einer CAB-Datei](/windows/win32/devnotes/cabinet-api-functions).

Abhängig von den Einstellungen für die Vertrauensstellung und die Browsersicherheit kann ein Zertifikat angezeigt werden, um die unterzeichnende Person oder das Unternehmen zu identifizieren. Wenn die Sicherheitsstufe keine ist oder wenn der Zertifikatbesitzer des signierten Steuerelements vertrauenswürdig ist, wird kein Zertifikat angezeigt. Weitere Informationen dazu, wie die Browsersicherheitseinstellung bestimmt, ob das Steuerelement heruntergeladen und ein Zertifikat angezeigt wird, finden Sie unter [Internet Explorer Browser Safety Levels and Control Behavior.](#_core_internet_explorer_browser_safety_levels_and_control_behavior)

Der Code für die digitale Signaturgarantie hat sich seit der Unterzeichnung nicht geändert. Ein Hash des Codes wird übernommen und in das Zertifikat eingebettet. Dieser Hash wird später mit einem Hash des Codes verglichen, der nach dem Herunterladen des Codes, aber vor der Ausgeführten übernommen wurde. Unternehmen wie Verisign können private und öffentliche Schlüssel bereitstellen, die zum Signieren von Code erforderlich sind. Das ActiveX SDK wird mit MakeCert ausgeliefert, einem Dienstprogramm zum Erstellen von Testzertifikaten.

## <a name="managing-the-palette"></a><a name="_core_managing_the_palette"></a>Verwalten der Palette

Container bestimmen die Palette und stellen sie als Umgebungseigenschaft zur Verfügung, **DISPID_AMBIENT_PALETTE**. Ein Container (z. B. Internet Explorer) wählt eine Palette aus, die von allen ActiveX-Steuerelementen auf einer Seite verwendet wird, um ihre eigene Palette zu bestimmen. Dies verhindert das Flackern der Anzeige und zeigt ein einheitliches Erscheinungsbild.

Ein Steuerelement kann `OnAmbientPropertyChange` überschreiben, um Benachrichtigungen über Änderungen an der Palette zu behandeln.

Ein Steuerelement kann `OnGetColorSet` überschreiben, um einen Farbsatz zum Zeichnen der Palette zurückzugeben. Container verwenden den Rückgabewert, um zu ermitteln, ob ein Steuerelement palettenaware ist.

Nach den OCX 96-Richtlinien muss ein Steuerelement seine Palette immer im Hintergrund realisieren.

Ältere Container, die die Umgebungspaletteneigenschaft nicht verwenden, senden WM_QUERYNEWPALETTE und WM_PALETTECHANGED Nachrichten. Ein Steuerelement kann `OnQueryNewPalette` `OnPaletteChanged` diese Nachrichten überschreiben und verarbeiten.

## <a name="internet-explorer-browser-safety-levels-and-control-behavior"></a><a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a>Internet Explorer Browser-Sicherheitsstufen und Kontrollverhalten

Ein Browser verfügt über Optionen für das Sicherheitsniveau, die vom Benutzer konfigurierbar sind. Da Webseiten aktive Inhalte enthalten können, die möglicherweise den Computer eines Benutzers beschädigen können, können Benutzer in Browsern Optionen für die Sicherheitsstufe auswählen. Je nachdem, wie ein Browser Sicherheitsstufen implementiert, wird ein Steuerelement möglicherweise überhaupt nicht heruntergeladen oder zeigt ein Zertifikat oder eine Warnmeldung an, damit der Benutzer zur Laufzeit auswählen kann, ob das Steuerelement heruntergeladen werden soll oder nicht. Das Verhalten von ActiveX-Steuerelementen unter hohen, mittleren und niedrigen Sicherheitsstufen in Internet Explorer ist unten aufgeführt.

### <a name="high-safety-mode"></a>Hoher Sicherheitsmodus

- Nicht signierte Steuerelemente werden nicht heruntergeladen.

- Signierte Steuerelemente zeigen ein Zertifikat an, wenn es nicht vertrauenswürdig ist (ein Benutzer kann von nun an eine Option auswählen, um Code von diesem Zertifikatbesitzer immer zu vertrauen).

- Nur Steuerelemente, die als sicher markiert sind, verfügen über persistente Daten und/oder können skriptfähig sein.

### <a name="medium-safety-mode"></a>Mittlerer Sicherheitsmodus

- Nicht signierte Steuerelemente zeigen vor dem Herunterladen eine Warnung an.

- Signierte Steuerelemente zeigen ein Zertifikat an, wenn es nicht vertrauenswürdig ist.

- Steuerelemente, die nicht als sicher markiert sind, zeigen eine Warnung an.

### <a name="low-safety-mode"></a>Niedriger Sicherheitsmodus

- Steuerelemente werden ohne Vorwarnung heruntergeladen.

- Skripterstellung und Persistenz erfolgen ohne Warnung.

## <a name="see-also"></a>Weitere Informationen

[MFC-Internetprogrammierungsaufgaben](../mfc/mfc-internet-programming-tasks.md)<br/>
[Grundlagen der MFC-Internetprogrammierung](../mfc/mfc-internet-programming-basics.md)<br/>
[MFC-ActiveX-Steuerelemente: Lizenzieren eines ActiveX-Steuerelements](../mfc/mfc-activex-controls-licensing-an-activex-control.md)
