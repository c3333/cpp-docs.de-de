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
ms.openlocfilehash: b08abdc0e2c17cb61c0c6a14cd712ec32ea816bd
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438021"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>MFC-ActiveX-Steuerelemente: Lizenzieren eines ActiveX-Steuerelements

Lizenzierungs Unterstützung, ein optionales Feature von ActiveX-Steuerelementen, ermöglicht Ihnen, zu steuern, wer das Steuerelement verwenden oder verteilen kann. (Informationen zur weiteren Erörterung von Lizenzierungs Problemen finden Sie unter Lizenzierungsprobleme beim [Upgrade eines vorhandenen ActiveX-Steuer](../mfc/upgrading-an-existing-activex-control.md)Elements.)

> [!IMPORTANT]
> ActiveX ist eine ältere Technologie, die nicht für die neue Entwicklung verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ersetzen, finden Sie unter ActiveX-Steuer [Elemente](activex-controls.md).

In diesem Artikel werden die folgenden Themen behandelt:

- [Übersicht über die ActiveX-Steuerelement Lizenzierung](#_core_overview_of_activex_control_licensing)

- [Erstellen eines lizenzierten Steuer Elements](#_core_creating_a_licensed_control)

- [Lizenzierungs Unterstützung](#_core_licensing_support)

- [Anpassen der Lizenzierung eines ActiveX-Steuer Elements](#_core_customizing_the_licensing_of_an_activex_control)

ActiveX-Steuerelemente, die eine Lizenzierung implementieren, ermöglichen es Ihnen, als Steuerelement Entwickler zu bestimmen, wie andere Benutzer das ActiveX-Steuerelement verwenden werden. Sie stellen dem Steuerelement Käufer das-Steuerelement und bereit. Die-Datei mit der Vereinbarung, dass der Käufer das Steuerelement verteilen darf, jedoch nicht. Die-Datei mit einer Anwendung, die das-Steuerelement verwendet. Dadurch wird verhindert, dass Benutzer dieser Anwendung neue Anwendungen schreiben, die das-Steuerelement verwenden, ohne zuvor das Steuerelement von Ihnen zu lizenzieren.

##  <a name="_core_overview_of_activex_control_licensing"></a>Übersicht über die ActiveX-Steuerelement Lizenzierung

Zur Unterstützung von Lizenzierung für ActiveX-Steuerelemente stellt die [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) -Klasse eine Implementierung für mehrere Funktionen in der `IClassFactory2`-Schnittstelle bereit: `IClassFactory2::RequestLicKey`, `IClassFactory2::GetLicInfo`und `IClassFactory2::CreateInstanceLic`. Wenn der Container Anwendungsentwickler eine Anforderung zum Erstellen einer Instanz des Steuer Elements sendet, wird `GetLicInfo` aufgerufen, um das Steuerelement zu überprüfen. Die Datei "lischen" ist vorhanden. Wenn das Steuerelement lizenziert ist, kann eine Instanz des Steuer Elements erstellt und in den Container eingefügt werden. Nachdem der Entwickler die Containeranwendung erstellt hat, wird dieses `RequestLicKey`mal ein weiterer Funktionsaufruf durchgeführt. Diese Funktion gibt einen Lizenzschlüssel (eine einfache Zeichenfolge) an die Containeranwendung zurück. Der zurückgegebene Schlüssel wird dann in die Anwendung eingebettet.

In der folgenden Abbildung wird die Lizenz Überprüfung eines ActiveX-Steuer Elements veranschaulicht, das während der Entwicklung einer Containeranwendung verwendet wird. Wie bereits erwähnt, muss der Container Anwendungsentwickler über die richtige verfügen. Auf dem Entwicklungs Computer installierter LIC-Datei zum Erstellen einer Instanz des Steuer Elements.

![Lizenzierte ActiveX-Steuerung bei Entwicklung überprüft](../mfc/media/vc374d1.gif "Lizenz bei der Entwicklung von ActiveX-Steuerelementen überprüft") <br/>
Überprüfung eines lizenzierten ActiveX-Steuerelements während der Entwicklung

Der nächste Prozess, der in der folgenden Abbildung gezeigt wird, tritt auf, wenn der Endbenutzer die Containeranwendung ausführt.

Wenn die Anwendung gestartet wird, muss in der Regel eine Instanz des Steuer Elements erstellt werden. Der Container erreicht dies, indem er `CreateInstanceLic`aufruft und den eingebetteten Lizenzschlüssel als Parameter übergibt. Anschließend wird ein Zeichen folgen Vergleich zwischen dem eingebetteten Lizenzschlüssel und der eigenen Kopie des Lizenzschlüssels des-Steuer Elements vorgenommen. Wenn die Entsprechung erfolgreich ist, wird eine Instanz des Steuer Elements erstellt, und die Anwendung wird weiterhin normal ausgeführt. Beachten Sie, dass die. Die LIC-Datei muss auf dem Computer des Steuer Elements nicht vorhanden sein.

![Lizenzierte ActiveX-Steuerung bei Ausführung überprüft](../mfc/media/vc374d2.gif "Lizenz bei der Ausführung von ActiveX-Steuerelementen überprüft") <br/>
Überprüfung eines lizenzierten ActiveX-Steuerelements während der Ausführung

Die Steuerelement Lizenzierung besteht aus zwei grundlegenden Komponenten: spezifischer Code in der Steuerungs-Implementierungs-DLL und der Lizenzdatei. Der Code besteht aus zwei (oder möglicherweise drei) Funktionsaufrufen und einer Zeichenfolge, die im folgenden als "Lizenz Zeichenfolge" bezeichnet wird und einen Urheberrechts Hinweis enthält. Diese Aufrufe und die Lizenz Zeichenfolge finden Sie in der Implementierung des Steuer Elements (. Cpp-Datei. Die vom ActiveX-Steuerelement-Assistenten generierte Lizenzdatei ist eine Textdatei mit einer Copyright Erklärung. Der Name wird mit dem Projektnamen mit einem benannt. Die Erweiterung "lischen", z. b. Beispiel. Fröhlich. Ein lizenziertes Steuerelement muss von der Lizenzdatei begleitet werden, wenn die Entwurfszeit Verwendung erforderlich ist.

##  <a name="_core_creating_a_licensed_control"></a>Erstellen eines lizenzierten Steuer Elements

Wenn Sie den ActiveX-Steuerelement-Assistenten verwenden, um das Steuerelement Framework zu erstellen, können Sie den Lizenzierungs Support problemlos einschließen. Wenn Sie angeben, dass das Steuerelement über eine Laufzeitlizenz verfügen soll, fügt der ActiveX-Steuerelement-Assistent der Control-Klasse Code hinzu, um die Lizenzierung zu unterstützen. Der Code umfasst Funktionen, die einen Schlüssel und eine Lizenzdatei für die Lizenz Überprüfung verwenden. Diese Funktionen können auch so geändert werden, dass die Steuerelement Lizenzierung angepasst wird. Weitere Informationen zur Lizenz Anpassung finden Sie unter [Anpassen der Lizenzierung eines ActiveX-Steuer](#_core_customizing_the_licensing_of_an_activex_control) Elements weiter unten in diesem Artikel.

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>So fügen Sie Unterstützung für die Lizenzierung mit dem ActiveX-Steuerelement-Assistenten hinzu

1. Verwenden Sie die Anweisungen unter [Erstellen eines MFC-ActiveX-Steuer](../mfc/reference/creating-an-mfc-activex-control.md)Elements. Auf der Seite **Anwendungseinstellungen** des ActiveX-Steuerelement-Assistenten ist die Option zum Erstellen des Steuer Elements mit der Laufzeitlizenz enthalten.

Der ActiveX-Steuerelement-Assistent generiert nun ein ActiveX-Steuerelement Framework, das grundlegende Lizenzierungs Unterstützung umfasst Eine ausführliche Erläuterung des Lizenzierungs Codes finden Sie im nächsten Thema.

##  <a name="_core_licensing_support"></a>Lizenzierungs Unterstützung

Wenn Sie mithilfe des ActiveX-Steuerelement-Assistenten einem ActiveX-Steuerelement Lizenzierungs Unterstützung hinzufügen, fügt der ActiveX-Steuerelement-Assistent Code hinzu, der die Lizenzierungs Funktion deklariert und implementiert, dem Steuerelement Header und den Implementierungs Dateien. Dieser Code besteht aus einer `VerifyUserLicense` Member-Funktion und einer `GetLicenseKey` Member-Funktion, die die in [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) gefundenen Standard Implementierungen überschreiben. Diese Funktionen rufen die Steuerelement Lizenz ab und überprüfen Sie.

> [!NOTE]
>  Eine dritte Member-Funktion, `VerifyLicenseKey` wird nicht vom ActiveX-Steuerelement-Assistenten generiert, kann jedoch außer Kraft gesetzt werden, um das Überprüfungs Verhalten des Lizenzschlüssels anzupassen.

Diese Member-Funktionen sind:

- [Verigyuserlicense](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)

   Überprüft, ob das Steuerelement Entwurfszeit Verwendung zulässt, indem das System auf das vorhanden sein der Steuerelement Lizenzdatei überprüft wird. Diese Funktion wird vom Framework als Teil der Verarbeitung von `IClassFactory2::GetLicInfo` und `IClassFactory::CreateInstanceLic`aufgerufen.

- [Getlicenabkey](../mfc/reference/coleobjectfactory-class.md#getlicensekey)

   Fordert einen eindeutigen Schlüssel von der Steuerelement-DLL an. Dieser Schlüssel ist in die Containeranwendung eingebettet und wird später zusammen mit `VerifyLicenseKey`verwendet, um eine Instanz des Steuer Elements zu erstellen. Diese Funktion wird vom Framework als Teil der Verarbeitung von `IClassFactory2::RequestLicKey`aufgerufen.

- [Verifylicenabkey](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)

   Überprüft, ob der eingebettete Schlüssel und der eindeutige Schlüssel des Steuer Elements identisch sind. Dies ermöglicht es dem Container, eine Instanz des Steuer Elements für seine Verwendung zu erstellen. Diese Funktion wird vom Framework als Teil der Verarbeitung `IClassFactory2::CreateInstanceLic` aufgerufen und kann überschrieben werden, um eine angepasste Überprüfung des Lizenzschlüssels bereitzustellen. Die Standard Implementierung führt einen Zeichen folgen Vergleich durch. Weitere Informationen finden Sie weiter unten in diesem Artikel unter [Anpassen der Lizenzierung eines ActiveX-Steuer](#_core_customizing_the_licensing_of_an_activex_control)Elements.

###  <a name="_core_header_file_modifications"></a>Header Dateiänderungen

Der ActiveX-Steuerelement-Assistent platziert den folgenden Code in der Header Datei des Steuer Elements. In diesem Beispiel werden zwei Element Funktionen des-Objekts `CSampleCtrl``factory` deklariert, eine, die das vorhanden sein des-Steuer Elements überprüft. Eine beliebige Datei und eine andere, die den Lizenzschlüssel abruft, der in der Anwendung verwendet werden soll, die das Steuerelement enthält:

[!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

###  <a name="_core_implementation_file_modifications"></a>Implementierungs Dateiänderungen

Der ActiveX-Steuerelement-Assistent platziert die folgenden zwei Anweisungen in der Implementierungs Datei des Steuer Elements, um den Lizenz Dateinamen und die Lizenz Zeichenfolge

[!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
>  Wenn Sie `szLicString` ändern, müssen Sie auch die erste Zeile im Steuerelement ändern. Die Datei-oder Lizenzierungs Funktion funktioniert nicht ordnungsgemäß.

Der ActiveX-Steuerelement-Assistent platziert den folgenden Code in der Implementierungs Datei des Steuer Elements, um die `VerifyUserLicense`-und `GetLicenseKey` Funktionen der Steuerelement Klasse zu definieren:

[!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

Schließlich ändert der **ActiveX-Steuer** Element-Assistent das Steuerelement Projekt. IDL-Datei. Das **lizenzierte** Schlüsselwort wird der Co-Klassen Deklaration des Steuer Elements hinzugefügt, wie im folgenden Beispiel gezeigt:

[!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

##  <a name="_core_customizing_the_licensing_of_an_activex_control"></a>Anpassen der Lizenzierung eines ActiveX-Steuer Elements

Da `VerifyUserLicense`, `GetLicenseKey`und `VerifyLicenseKey` als Virtual Member-Funktionen der Steuerelement-Factoryklasse deklariert werden, können Sie das Lizenzierungs Verhalten des Steuer Elements anpassen.

Beispielsweise können Sie mehrere Lizenzierungs Stufen für das-Steuerelement bereitstellen, indem Sie die Funktionen `VerifyUserLicense` oder `VerifyLicenseKey` Member überschreiben. Innerhalb dieser Funktion können Sie anpassen, welche Eigenschaften oder Methoden für den Benutzer entsprechend der erkannten Lizenz Stufe verfügbar gemacht werden.

Sie können auch der `VerifyLicenseKey`-Funktion Code hinzufügen, der eine benutzerdefinierte Methode bereitstellt, um den Benutzer darüber zu informieren, dass bei der Erstellung des Steuer Elements Beispielsweise können Sie in der `VerifyLicenseKey` Member-Funktion ein Meldungs Feld anzeigen, das besagt, dass das Steuerelement nicht initialisiert werden konnte und warum.

> [!NOTE]
>  Eine andere Möglichkeit zum Anpassen der Überprüfung der ActiveX-Steuerelement Lizenz besteht darin, die Registrierungsdatenbank für einen bestimmten Registrierungsschlüssel zu überprüfen, anstatt `AfxVerifyLicFile`aufrufen. Ein Beispiel für die Standard Implementierung finden Sie im Abschnitt [Implementierungs Dateiänderungen](#_core_implementation_file_modifications) in diesem Artikel.

Weitere Informationen zu Lizenzierungs Problemen finden Sie unter Lizenzierungsprobleme beim [Aktualisieren eines vorhandenen ActiveX-Steuer](../mfc/upgrading-an-existing-activex-control.md)Elements.

## <a name="see-also"></a>Weitere Informationen

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)<br/>
[MFC-ActiveX-Steuerelement-Assistent](../mfc/reference/mfc-activex-control-wizard.md)
