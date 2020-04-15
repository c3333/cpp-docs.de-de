---
title: 'MFC-ActiveX-Steuerelemente: Lizenzieren eines ActiveX-Steuerelements'
ms.date: 11/19/2018
helpviewer_keywords:
- COleObjectFactory class [MFC], licensing controls
- MFC ActiveX controls [MFC], licensing
- VerifyLicenseKey method [MFC]
- VerifyUserLicense method [MFC]
- GetLicenseKey method [MFC]
- licensing ActiveX controls
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
ms.openlocfilehash: aaab4ae3bb13790784a66d53b41dbc3a7cdaec89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364606"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>MFC-ActiveX-Steuerelemente: Lizenzieren eines ActiveX-Steuerelements

Die Lizenzierungsunterstützung, eine optionale Funktion von ActiveX-Steuerelementen, ermöglicht es Ihnen, zu steuern, wer das Steuerelement verwenden oder verteilen kann. (Weitere Erläuterungen zu Lizenzierungsproblemen finden Sie unter Lizenzierungsprobleme beim [Aktualisieren eines vorhandenen ActiveX-Steuerelements](../mfc/upgrading-an-existing-activex-control.md).)

> [!IMPORTANT]
> ActiveX ist eine legacy Technologie, die nicht für Neuentwicklungen verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ablösen, finden Sie unter [ActiveX Controls](activex-controls.md).

In diesem Artikel werden die folgenden Themen behandelt:

- [Übersicht über Die ActiveX Control Licensing](#_core_overview_of_activex_control_licensing)

- [Erstellen eines lizenzierten Steuerelements](#_core_creating_a_licensed_control)

- [Lizenzierungsunterstützung](#_core_licensing_support)

- [Anpassen der Lizenzierung eines ActiveX-Steuerelements](#_core_customizing_the_licensing_of_an_activex_control)

Mit ActiveX-Steuerelementen, die die Lizenzierung implementieren, können Sie als Steuerelemententwickler bestimmen, wie andere Benutzer das ActiveX-Steuerelement verwenden. Sie stellen dem Kontrollkäufer die Steuerung und . LIC-Datei, mit der Vereinbarung, dass der Käufer das Steuerelement verteilen darf, aber nicht die . LIC-Datei mit einer Anwendung, die das Steuerelement verwendet. Dadurch wird verhindert, dass Benutzer dieser Anwendung neue Anwendungen schreiben, die das Steuerelement verwenden, ohne zuvor das Steuerelement von Ihnen zu lizenzieren.

## <a name="overview-of-activex-control-licensing"></a><a name="_core_overview_of_activex_control_licensing"></a>Übersicht über Die ActiveX Control Licensing

Um Lizenzierungsunterstützung für ActiveX-Steuerelemente bereitzustellen, stellt die [COleObjectFactory-Klasse](../mfc/reference/coleobjectfactory-class.md) eine Implementierung für mehrere Funktionen in `IClassFactory2` der Schnittstelle bereit: `IClassFactory2::RequestLicKey`, `IClassFactory2::GetLicInfo`, und `IClassFactory2::CreateInstanceLic`. Wenn der Containeranwendungsentwickler eine Anforderung zum Erstellen einer Instanz `GetLicInfo` des Steuerelements stellt, wird ein Aufruf durchgeführt, um zu überprüfen, ob das Steuerelement . LIC-Datei vorhanden ist. Wenn das Steuerelement lizenziert ist, kann eine Instanz des Steuerelements erstellt und im Container platziert werden. Nachdem der Entwickler die Containeranwendung erstellt hat, wird `RequestLicKey`ein weiterer Funktionsaufruf, diesmal an , durchgeführt. Diese Funktion gibt einen Lizenzschlüssel (eine einfache Zeichenfolge) an die Containeranwendung zurück. Der zurückgegebene Schlüssel wird dann in die Anwendung eingebettet.

Die folgende Abbildung zeigt die Lizenzüberprüfung eines ActiveX-Steuerelements, das bei der Entwicklung einer Containeranwendung verwendet wird. Wie bereits erwähnt, muss der Containeranwendungsentwickler über die richtige verfügen. LIC-Datei, die auf dem Entwicklungscomputer installiert ist, um eine Instanz des Steuerelements zu erstellen.

![Lizenz bei der Entwicklung von ActiveX-Steuerelementen überprüft](../mfc/media/vc374d1.gif "Lizenz bei der Entwicklung von ActiveX-Steuerelementen überprüft") <br/>
Überprüfung eines lizenzierten ActiveX-Steuerelements während der Entwicklung

Der nächste Prozess, der in der folgenden Abbildung dargestellt wird, tritt auf, wenn der Endbenutzer die Containeranwendung ausführt.

Wenn die Anwendung gestartet wird, muss in der Regel eine Instanz des Steuerelements erstellt werden. Der Container erreicht dies, `CreateInstanceLic`indem er einen Aufruf an ausführt, der den eingebetteten Lizenzschlüssel als Parameter übergibt. Anschließend wird ein Zeichenfolgenvergleich zwischen dem eingebetteten Lizenzschlüssel und der eigenen Kopie des Lizenzschlüssels vorgenommen. Wenn die Übereinstimmung erfolgreich ist, wird eine Instanz des Steuerelements erstellt, und die Anwendung wird weiterhin normal ausgeführt. Beachten Sie, dass die . Lic-Datei muss nicht auf dem Computer des Steuerelementbenutzers vorhanden sein.

![Lizenz bei der Ausführung von ActiveX-Steuerelementen überprüft](../mfc/media/vc374d2.gif "Lizenz bei der Ausführung von ActiveX-Steuerelementen überprüft") <br/>
Überprüfung eines lizenzierten ActiveX-Steuerelements während der Ausführung

Die Steuerungslizenzierung besteht aus zwei grundlegenden Komponenten: dem spezifischen Code in der Steuerungsimplementierungs-DLL und der Lizenzdatei. Der Code besteht aus zwei (oder möglicherweise drei) Funktionsaufrufen und einer Zeichenfolge, die im Folgenden als "Lizenzzeichenfolge" bezeichnet wird und einen Copyright-Hinweis enthält. Diese Aufrufe und die Lizenzzeichenfolge befinden sich in der Steuerelementimplementierung (. CPP)-Datei. Die vom ActiveX Control Wizard generierte Lizenzdatei ist eine Textdatei mit einer Copyright-Anweisung. Benannt wird es mit dem Projektnamen mit einer . LIC-Erweiterung, z. B. SAMPLE. Lic. Ein lizenziertes Steuerelement muss von der Lizenzdatei begleitet werden, wenn die Verwendung zur Entwurfszeit erforderlich ist.

## <a name="creating-a-licensed-control"></a><a name="_core_creating_a_licensed_control"></a>Erstellen eines lizenzierten Steuerelements

Wenn Sie den ActiveX Control-Assistenten zum Erstellen des Steuerelementframeworks verwenden, ist es einfach, Lizenzierungsunterstützung einzuschließen. Wenn Sie angeben, dass das Steuerelement über eine Laufzeitlizenz verfügen soll, fügt der ActiveX Control-Assistent der Steuerelementklasse Code hinzu, um die Lizenzierung zu unterstützen. Der Code besteht aus Funktionen, die einen Schlüssel und eine Lizenzdatei für die Lizenzüberprüfung verwenden. Diese Funktionen können auch geändert werden, um die Steuerelementlizenzierung anzupassen. Weitere Informationen zur Lizenzanpassung finden Sie weiter unten in diesem Artikel unter [Anpassen der Lizenzierung eines ActiveX-Steuerelements.](#_core_customizing_the_licensing_of_an_activex_control)

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>So fügen Sie Unterstützung für die Lizenzierung mit dem ActiveX Control-Assistenten hinzu, wenn Sie ihr Steuerungsprojekt erstellen

1. Verwenden Sie die Anweisungen unter [Erstellen eines MFC ActiveX-Steuerelements](../mfc/reference/creating-an-mfc-activex-control.md). Die Seite **Anwendungseinstellungen** des ActiveX-Steuerelement-Assistenten enthält die Option, das Steuerelement mit der Laufzeitlizenz zu erstellen.

Der ActiveX Control Wizard generiert jetzt ein ActiveX-Steuerelementframework, das grundlegende Lizenzierungsunterstützung enthält. Eine ausführliche Erläuterung des Lizenzierungscodes finden Sie im nächsten Thema.

## <a name="licensing-support"></a><a name="_core_licensing_support"></a>Lizenzierungsunterstützung

Wenn Sie den ActiveX Control-Assistenten verwenden, um einem ActiveX-Steuerelement Lizenzierungsunterstützung hinzuzufügen, fügt der ActiveX Control-Assistent Code hinzu, der deklariert und implementiert, dass die Lizenzierungsfunktion dem Steuerelementheader und den Implementierungsdateien hinzugefügt wird. Dieser Code besteht `VerifyUserLicense` aus einer `GetLicenseKey` Memberfunktion und einer Memberfunktion, die die Standardimplementierungen in [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) überschreiben. Diese Funktionen rufen die Kontrolllizenz ab und überprüfen sie.

> [!NOTE]
> Eine dritte Memberfunktion `VerifyLicenseKey` wird nicht vom ActiveX Control Wizard generiert, kann jedoch überschrieben werden, um das Verhalten zur Überprüfung des Lizenzschlüssels anzupassen.

Diese Memberfunktionen sind:

- [VerifyUserLicense](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)

   Überprüft, ob das Steuerelement die Entwurfszeitnutzung ermöglicht, indem das System auf das Vorhandensein der Steuerlizenzdatei überprüft wird. Diese Funktion wird vom Framework als `IClassFactory2::GetLicInfo` `IClassFactory::CreateInstanceLic`Teil der Verarbeitung und aufgerufen.

- [GetLicenseKey](../mfc/reference/coleobjectfactory-class.md#getlicensekey)

   Fordert einen eindeutigen Schlüssel von der Steuerelement-DLL an. Dieser Schlüssel wird in die Containeranwendung eingebettet `VerifyLicenseKey`und später in Verbindung mit verwendet, um eine Instanz des Steuerelements zu erstellen. Diese Funktion wird vom Framework als `IClassFactory2::RequestLicKey`Teil der Verarbeitung aufgerufen.

- [VerifyLicenseKey](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)

   Überprüft, ob der eingebettete Schlüssel und der eindeutige Schlüssel des Steuerelements identisch sind. Dadurch kann der Container eine Instanz des Steuerelements für seine Verwendung erstellen. Diese Funktion wird vom Framework als `IClassFactory2::CreateInstanceLic` Teil der Verarbeitung aufgerufen und kann überschrieben werden, um eine benutzerdefinierte Überprüfung des Lizenzschlüssels bereitzustellen. Die Standardimplementierung führt einen Zeichenfolgenvergleich durch. Weitere Informationen finden Sie weiter unten in diesem Artikel unter [Anpassen der Lizenzierung eines ActiveX-Steuerelements.](#_core_customizing_the_licensing_of_an_activex_control)

### <a name="header-file-modifications"></a><a name="_core_header_file_modifications"></a>Änderungen der Headerdatei

Der ActiveX-Steuerelement-Assistent platziert den folgenden Code in der Steuerelementheaderdatei. In diesem Beispiel werden `CSampleCtrl`zwei Memberfunktionen des Objekts `factory` deklariert, eine, die das Vorhandensein des Steuerelements überprüft. LIC-Datei und eine andere, die den Lizenzschlüssel abruft, der in der Anwendung verwendet werden soll, die das Steuerelement enthält:

[!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

### <a name="implementation-file-modifications"></a><a name="_core_implementation_file_modifications"></a>Implementierungsdateiänderungen

Der ActiveX Control Wizard platziert die folgenden beiden Anweisungen in der Steuerelementimplementierungsdatei, um den Lizenzdateinamen und die Lizenzzeichenfolge zu deklarieren:

[!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
> Wenn Sie `szLicString` in irgendeiner Weise ändern, müssen Sie auch die erste Zeile im Steuerelement ändern. LIC-Datei oder Lizenzierung funktioniert nicht ordnungsgemäß.

Der ActiveX-Steuerelement-Assistent platziert den folgenden Code in der `VerifyUserLicense` `GetLicenseKey` Steuerelementimplementierungsdatei, um die Steuerungsklasse und -funktionen zu definieren:

[!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

Schließlich ändert der **ActiveX-Steuerelement-Assistent** das Steuerelementprojekt . IDL-Datei. Das **lizenzierte** Schlüsselwort wird der Coclass-Deklaration des Steuerelements hinzugefügt, wie im folgenden Beispiel:

[!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

## <a name="customizing-the-licensing-of-an-activex-control"></a><a name="_core_customizing_the_licensing_of_an_activex_control"></a>Anpassen der Lizenzierung eines ActiveX-Steuerelements

Da `VerifyUserLicense` `GetLicenseKey`, `VerifyLicenseKey` und als virtuelle Memberfunktionen der Control Factory-Klasse deklariert werden, können Sie das Lizenzierungsverhalten des Steuerelements anpassen.

Sie können z. B. mehrere Lizenzierungsebenen für `VerifyUserLicense` `VerifyLicenseKey` das Steuerelement bereitstellen, indem Sie die oder Memberfunktionen überschreiben. Innerhalb dieser Funktion können Sie anpassen, welche Eigenschaften oder Methoden dem Benutzer entsprechend der von Ihnen erkannten Lizenzstufe verfügbar gemacht werden.

Sie können der Funktion `VerifyLicenseKey` auch Code hinzufügen, der eine benutzerdefinierte Methode zum Informieren des Benutzers bereitstellt, dass die Steuerelementerstellung fehlgeschlagen ist. In Ihrer `VerifyLicenseKey` Memberfunktion können Sie z. B. ein Meldungsfeld anzeigen, in dem angegeben wird, dass das Steuerelement nicht initialisiert werden konnte und warum.

> [!NOTE]
> Eine weitere Möglichkeit zum Anpassen der ActiveX-Steuerungslizenzüberprüfung besteht darin, `AfxVerifyLicFile`die Registrierungsdatenbank auf einen bestimmten Registrierungsschlüssel zu überprüfen, anstatt aufzurufen. Ein Beispiel für die Standardimplementierung finden Sie im Abschnitt [Implementierungsdateiänderungen](#_core_implementation_file_modifications) in diesem Artikel.

Weitere Informationen zu Lizenzierungsproblemen finden Sie unter Lizenzierungsprobleme unter [Aktualisieren eines vorhandenen ActiveX-Steuerelements](../mfc/upgrading-an-existing-activex-control.md).

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)<br/>
[MFC-ActiveX-Steuerelement-Assistent](../mfc/reference/mfc-activex-control-wizard.md)
