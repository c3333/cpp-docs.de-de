---
title: 'MFC-ActiveX-Steuerelemente: Lokalisieren eines ActiveX-Steuerelements'
ms.date: 09/12/2018
f1_keywords:
- LocaleID
- AfxOleRegisterTypeLib
helpviewer_keywords:
- localization, ActiveX controls
- MFC ActiveX controls [MFC], localizing
- LocaleID ambient property [MFC]
- LOCALIZE sample [MFC]
ms.assetid: a44b839a-c652-4ec5-b824-04392708a5f9
ms.openlocfilehash: a85ec5cbed797b756afd93cd8423c58d138a0625
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615425"
---
# <a name="mfc-activex-controls-localizing-an-activex-control"></a>MFC-ActiveX-Steuerelemente: Lokalisieren eines ActiveX-Steuerelements

In diesem Artikel werden Verfahren zum Lokalisieren von ActiveX-Steuerelement Schnittstellen erläutert.

>[!IMPORTANT]
> ActiveX ist eine ältere Technologie, die nicht für die neue Entwicklung verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ersetzen, finden Sie unter ActiveX-Steuer [Elemente](activex-controls.md).

Wenn Sie ein ActiveX-Steuerelement an einen internationalen Markt anpassen möchten, können Sie das Steuerelement lokalisieren. Windows unterstützt neben den Standard-Englisch, einschließlich Deutsch, Französisch und Schwedisch, viele Sprachen. Dies kann Probleme für das-Steuerelement darstellen, wenn die Schnittstelle nur in englischer Sprache vorliegt.

Im Allgemeinen sollten ActiveX-Steuerelemente stets Ihr Gebiets Schema auf der Ambient LocaleID-Eigenschaft basieren. Hierzu stehen drei Möglichkeiten zur Verfügung:

- Laden von Ressourcen und Always on-Demand basierend auf dem aktuellen Wert der Ambient LocaleID-Eigenschaft. Die MFC-ActiveX- [LOCALIZE](../overview/visual-cpp-samples.md) Steuerelemente-Beispiel Lokalisierungsbeispiel verwendet diese Strategie.

- Laden von Ressourcen, wenn das erste Steuerelement auf der Basis der LocaleID-Eigenschaft Ambient verwendet wird, und Verwenden dieser Ressourcen für alle anderen Instanzen. Dieser Artikel veranschaulicht diese Strategie.

    > [!NOTE]
    >  Dies funktioniert in einigen Fällen nicht ordnungsgemäß, wenn zukünftige Instanzen über unterschiedliche Gebiets Schemas verfügen.

- Verwenden `OnAmbientChanged` Sie die Benachrichtigungsfunktion, um die richtigen Ressourcen für das Gebiets Schema des Containers dynamisch zu laden.

    > [!NOTE]
    >  Dies funktioniert für das-Steuerelement, aber die Lauf Zeit-dll aktualisiert ihre eigenen Ressourcen nicht dynamisch, wenn sich die LocaleID-Eigenschaft der Umgebung ändert. Außerdem verwenden Lauf Zeit-DLLs für ActiveX-Steuerelemente das Thread Gebiets Schema, um das Gebiets Schema für die Ressourcen zu bestimmen.

Im weiteren Verlauf dieses Artikels werden zwei Lokalisier Ende Strategien beschrieben. Die erste Strategie [lokalisiert die Programmierbarkeits-Schnittstelle des Steuer](#_core_localizing_your_control.92.s_programmability_interface) Elements (Namen von Eigenschaften, Methoden und Ereignissen). Die zweite Strategie [lokalisiert die Benutzeroberfläche des Steuer](#_core_localizing_the_control.92.s_user_interface)Elements unter Verwendung der Ambient LocaleID-Eigenschaft des Containers. Eine Demonstration der Lokalisierung von Steuerelementen finden Sie unter Beispiel für MFC-ActiveX-Steuerelemente [lokalisieren](../overview/visual-cpp-samples.md).

## <a name="localizing-the-controls-programmability-interface"></a><a name="_core_localizing_your_control.92.s_programmability_interface"></a>Lokalisieren der Programmierbarkeits-Schnittstelle des Steuer Elements

Beim Lokalisieren der Programmierbarkeits-Schnittstelle des Steuer Elements (die Schnittstelle, die Programmierer zum Schreiben von Anwendungen verwendet, die Ihr Steuerelement verwenden), müssen Sie eine geänderte Version des-Steuer Elements erstellen. IDL-Datei (ein Skript zum Erstellen der Steuerelement-Typbibliothek) für jede Sprache, die Sie unterstützen möchten. Dies ist die einzige Stelle, an der Sie die Namen der Steuerelement Eigenschaften lokalisieren müssen.

Wenn Sie ein lokalisiertes Steuerelement entwickeln, schließen Sie die Gebiets Schema-ID als Attribut auf der Ebene der Typbibliothek ein. Wenn Sie z. b. eine Typbibliothek mit französischen, lokalisierten Eigenschaftsnamen bereitstellen möchten, erstellen Sie eine Kopie Ihres Beispiels. IDL-Datei, und nennen Sie Sie SAMPLEFR. IDL. Fügen Sie der Datei ein Gebiets Schema-ID-Attribut hinzu (die Gebiets Schema-ID für Französisch lautet 0x040c), ähnlich wie im folgenden Beispiel:

[!code-cpp[NVC_MFC_AxLoc#1](codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_1.idl)]

Ändern Sie die Eigenschaftsnamen in SAMPLEFR. Verwenden Sie IDL zu ihren französischen Entsprechungen, und verwenden Sie dann MKTYPLIB. EXE zum Entwickeln der französischen Typbibliothek, SAMPLEFR. TLB.

Um mehrere lokalisierte Typbibliotheken zu erstellen, können Sie beliebige lokalisierte Typen hinzufügen. IDL-Dateien für das Projekt und werden automatisch erstellt.

#### <a name="to-add-an-idl-file-to-your-activex-control-project"></a>Zum Hinzufügen einer. IDL-Datei für das ActiveX-Steuerelement Projekt

1. Wenn das Steuerelement Projekt geöffnet ist, klicken Sie im Menü **Projekt** auf **Vorhandenes Element hinzufügen**.

   Das Dialogfeld **Vorhandenes Element hinzufügen** wird angezeigt.

1. Wählen Sie ggf. das Laufwerk und das Verzeichnis zum Anzeigen aus.

1. Wählen Sie im Feld **Dateityp** die Option **alle Dateien ( \* . \* )** aus.

1. Doppelklicken Sie im Listenfeld Datei auf. Die IDL-Datei, die Sie in das Projekt einfügen möchten.

1. Wenn Sie alle erforderlichen hinzugefügt haben, klicken Sie auf **Öffnen** . IDL-Dateien.

Da die Dateien dem Projekt hinzugefügt wurden, werden Sie erstellt, wenn der Rest des Projekts erstellt wird. Die lokalisierten Typbibliotheken befinden sich im aktuellen Projektverzeichnis des ActiveX-Steuer Elements.

Im Code werden die internen Eigenschaftsnamen (normalerweise in englischer Sprache) immer verwendet und nie lokalisiert. Hierzu gehören die Steuerelement Dispatchzuordnung, die Eigenschaften Austausch Funktionen und der Datenaustausch Code der Eigenschaften Seite.

Nur eine Typbibliothek (. Die TLB-Datei kann an die Ressourcen der Steuerelement Implementierung gebunden werden (. OCX-Datei). Dies ist normalerweise die Version mit den standardisierten (in der Regel englischen) Namen. Wenn Sie eine lokalisierte Version Ihres Steuer Elements versenden möchten, müssen Sie das versenden. Ocx (das bereits an den Standard gebunden wurde. TLB-Version) und. TLB für das entsprechende Gebiets Schema. Dies bedeutet, dass nur die. Ocx ist für englische Versionen erforderlich, da das richtige ist. TLB wurde bereits gebunden. Bei anderen Gebiets Schemata muss die lokalisierte Typbibliothek auch mit ausgeliefert werden. OCX.

Registrieren Sie Ihr Gebiets Schema spezifisches, um sicherzustellen, dass Clients Ihres Steuer Elements die lokalisierte Typbibliothek finden können. TLB-Datei (en) im TypeLib-Abschnitt der Windows-Systemregistrierung. Der dritte Parameter (normalerweise optional) der [AfxOleRegisterTypeLib](reference/registering-ole-controls.md#afxoleregistertypelib) -Funktion wird zu diesem Zweck bereitgestellt. Im folgenden Beispiel wird eine französische Typbibliothek für ein ActiveX-Steuerelement registriert:

[!code-cpp[NVC_MFC_AxLoc#2](codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_2.cpp)]

Wenn das Steuerelement registriert ist, `AfxOleRegisterTypeLib` sucht die Funktion automatisch nach dem angegebenen. Die TLB-Datei im gleichen Verzeichnis wie das Steuerelement und registriert Sie in der Windows-Registrierungsdatenbank. , Wenn die. Die TLB-Datei wurde nicht gefunden, die Funktion hat keine Auswirkung.

## <a name="localizing-the-controls-user-interface"></a><a name="_core_localizing_the_control.92.s_user_interface"></a>Lokalisieren der Benutzeroberfläche des Steuer Elements

Um die Benutzeroberfläche eines Steuer Elements zu lokalisieren, platzieren Sie alle Benutzer sichtbaren Ressourcen des Steuer Elements (z. b. Eigenschaften Seiten und Fehlermeldungen) in sprachspezifische Ressourcen-DLLs. Anschließend können Sie die Ambient LocaleID-Eigenschaft des Containers verwenden, um die entsprechende dll für das Gebiets Schema des Benutzers auszuwählen.

Im folgenden Codebeispiel wird ein Ansatz zum Suchen und Laden der Ressourcen-DLL für ein bestimmtes Gebiets Schema veranschaulicht. Diese Member-Funktion, `GetLocalizedResourceHandle` die für dieses Beispiel aufgerufen wird, kann eine Member-Funktion ihrer ActiveX-Steuerelement Klasse sein:

[!code-cpp[NVC_MFC_AxLoc#3](codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_3.cpp)]

Beachten Sie, dass die unter Sprachen-ID in jedem Fall der Switch-Anweisung aktiviert werden kann, um eine speziellere Lokalisierung bereitzustellen. Eine Demonstration dieser Funktion finden Sie unter der- `GetResourceHandle` Funktion in der MFC-ActiveX-Steuerelemente-Beispiel [lokalisieren](../overview/visual-cpp-samples.md).

Wenn das-Steuerelement zum ersten Mal in einen Container geladen wird, kann es [COleControl:: AmbientLocaleID](reference/colecontrol-class.md#ambientlocaleid) aufrufen, um die Gebiets Schema-ID abzurufen. Das-Steuerelement kann dann den zurückgegebenen Gebiets Schema-ID-Wert an die- `GetLocalizedResourceHandle` Funktion übergeben, die die richtige Ressourcen Bibliothek lädt. Das Steuerelement sollte das resultierende Handle, falls vorhanden, an [afxctresourcehandle](reference/application-information-and-management.md#afxsetresourcehandle)übergeben:

[!code-cpp[NVC_MFC_AxLoc#4](codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_4.cpp)]

Platzieren Sie das obige Codebeispiel in eine Member-Funktion des Steuer Elements, z. b. eine außer Kraft Setzung von [COleControl:: OnSetClientSite](reference/colecontrol-class.md#onsetclientsite). Außerdem sollte *m_hResDLL* eine Member-Variable der Steuerelement Klasse sein.

Sie können eine ähnliche Logik zum Lokalisieren der Eigenschaften Seite eines Steuer Elements verwenden. Um die Eigenschaften Seite zu lokalisieren, fügen Sie der Implementierungs Datei ihrer Eigenschaften Seite Code ähnlich dem folgenden Beispiel hinzu (in einer außer Kraft Setzung von [COlePropertyPage:: onsetpagesite](reference/colepropertypage-class.md#onsetpagesite)):

[!code-cpp[NVC_MFC_AxLoc#5](codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_5.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)
