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
ms.openlocfilehash: 987cde2117307cdb5940a31e6f01efb15c527b84
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364597"
---
# <a name="mfc-activex-controls-localizing-an-activex-control"></a>MFC-ActiveX-Steuerelemente: Lokalisieren eines ActiveX-Steuerelements

In diesem Artikel werden Verfahren zum Lokalisieren von ActiveX-Steuerungsschnittstellen erläutert.

>[!IMPORTANT]
> ActiveX ist eine legacy Technologie, die nicht für Neuentwicklungen verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ablösen, finden Sie unter [ActiveX Controls](activex-controls.md).

Wenn Sie ein ActiveX-Steuerelement an einen internationalen Markt anpassen möchten, können Sie das Steuerelement lokalisieren. Windows unterstützt neben dem Standardenglisch viele Sprachen, einschließlich Deutsch, Französisch und Schwedisch. Dies kann Probleme für das Steuerelement darstellen, wenn seine Schnittstelle nur auf Englisch ist.

Im Allgemeinen sollten ActiveX-Steuerelemente ihr Gebietsschema immer auf der Ambient LocaleID-Eigenschaft basieren. Hierzu stehen drei Möglichkeiten zur Verfügung:

- Laden Sie Ressourcen, immer bei Bedarf, basierend auf dem aktuellen Wert der Ambient LocaleID-Eigenschaft. Das MFC ActiveX-Steuerelementbeispiel [LOCALIZE](../overview/visual-cpp-samples.md) verwendet diese Strategie.

- Laden Sie Ressourcen, wenn das erste Steuerelement basierend auf der Ambient LocaleID-Eigenschaft instanziiert wird, und verwenden Sie diese Ressourcen für alle anderen Instanzen. Dieser Artikel veranschaulicht diese Strategie.

    > [!NOTE]
    >  Dies funktioniert in einigen Fällen nicht ordnungsgemäß, wenn zukünftige Instanzen unterschiedliche Gebietsschemas haben.

- Verwenden `OnAmbientChanged` Sie die Benachrichtigungsfunktion, um die richtigen Ressourcen für das Gebietsschema des Containers dynamisch zu laden.

    > [!NOTE]
    >  Dies funktioniert für das Steuerelement, aber die Laufzeit-DLL aktualisiert ihre eigenen Ressourcen nicht dynamisch, wenn sich die Ambient LocaleID-Eigenschaft ändert. Darüber hinaus verwenden Laufzeit-DLLs für ActiveX-Steuerelemente das Threadgebietsschema, um das Gebietsschema für seine Ressourcen zu bestimmen.

Der Rest dieses Artikels beschreibt zwei Lokalisierungsstrategien. Die erste Strategie [lokalisiert die Programmierbarkeitsschnittstelle des Steuerelements](#_core_localizing_your_control.92.s_programmability_interface) (Namen von Eigenschaften, Methoden und Ereignissen). Die zweite Strategie [lokalisiert die Benutzeroberfläche des Steuerelements](#_core_localizing_the_control.92.s_user_interface)mithilfe der Ambient LocaleID-Eigenschaft des Containers. Eine Demonstration der Steuerelementlokalisierung finden Sie im MFC ActiveX-Steuerelementbeispiel [LOCALIZE](../overview/visual-cpp-samples.md).

## <a name="localizing-the-controls-programmability-interface"></a><a name="_core_localizing_your_control.92.s_programmability_interface"></a>Lokalisieren der Programmierbarkeitsschnittstelle des Steuerelements

Beim Lokalisieren der Programmierbarkeitsschnittstelle des Steuerelements (der Schnittstelle, die von Programmierern verwendet wird, die Anwendungen schreiben, die das Steuerelement verwenden), müssen Sie eine geänderte Version des Steuerelements erstellen. IDL-Datei (ein Skript zum Erstellen der Steuerelementtypbibliothek) für jede Sprache, die Sie unterstützen möchten. Dies ist der einzige Ort, an dem Sie die Steuerelementeigenschaftsnamen lokalisieren müssen.

Wenn Sie ein lokalisiertes Steuerelement entwickeln, fügen Sie die Gebietsschema-ID als Attribut auf Typbibliotheksebene ein. Wenn Sie beispielsweise eine Typbibliothek mit lokalisierten französischen Eigenschaftsnamen bereitstellen möchten, erstellen Sie eine Kopie Ihrer SAMPLE. IDL-Datei, und nennen Sie es SAMPLEFR. Idl. Fügen Sie der Datei ein Gebietsschema-ID-Attribut hinzu (die Gebietsschema-ID für Französisch ist 0x040c), ähnlich wie folgt:

[!code-cpp[NVC_MFC_AxLoc#1](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_1.idl)]

Ändern Sie die Eigenschaftsnamen in SAMPLEFR. IDL zu ihren französischen Entsprechungen, und verwenden Sie dann MKTYPLIB. EXE, um die französische Typbibliothek SAMPLEFR zu erstellen. Tlb.

Um mehrere lokalisierte Typbibliotheken zu erstellen, können Sie beliebige lokalisierte hinzufügen. IDL-Dateien in das Projekt und werden automatisch erstellt.

#### <a name="to-add-an-idl-file-to-your-activex-control-project"></a>So fügen Sie eine hinzu. IDL-Datei in Ihr ActiveX-Steuerprojekt

1. Wenn Das Steuerelementprojekt geöffnet ist, klicken Sie im Menü **Projekt** auf **Vorhandenes Element hinzufügen**.

   Das Dialogfeld **Vorhandenes Element hinzufügen** wird angezeigt.

1. Wählen Sie ggf. das anzuzeigende Laufwerk und Verzeichnis aus.

1. Wählen Sie im Feld **Typdateien** **Alle Dateien (\*.\*)** aus.

1. Doppelklicken Sie im Dateilistenfeld auf die . IDL-Datei, die Sie in das Projekt einfügen möchten.

1. Klicken Sie auf **Öffnen,** wenn Sie alle erforderlichen hinzugefügt haben. IDL-Dateien.

Da die Dateien dem Projekt hinzugefügt wurden, werden sie erstellt, wenn der Rest des Projekts erstellt wird. Die lokalisierten Typbibliotheken befinden sich im aktuellen ActiveX-Steuerelementprojektverzeichnis.

Innerhalb Ihres Codes werden die internen Eigenschaftsnamen (in der Regel in Englisch) immer verwendet und nie lokalisiert. Dazu gehören die Control Dispatch Map, die Eigenschaftenaustauschfunktionen und der Datenaustauschcode Für Eigenschaftenseiten.

Nur eine Typbibliothek (. TLB)-Datei kann an die Ressourcen der Kontrollimplementierung gebunden werden (. OCX)-Datei. Dies ist in der Regel die Version mit den standardisierten (typischerweise englischen) Namen. Um eine lokalisierte Version Ihres Steuerelements zu versenden, müssen Sie die versenden. OCX (die bereits an den Standardwert gebunden wurde . TLB-Version) und die . TLB für das entsprechende Gebietsschema. Dies bedeutet, dass nur die . OCX wird für englische Versionen benötigt, da die richtige . TLB ist bereits daran gebunden. Für andere Gebietsschemas muss die lokalisierte Typbibliothek auch mit der ausgeliefert werden. Ocx.

Um sicherzustellen, dass Clients Ihres Steuerelements die lokalisierte Typbibliothek finden können, registrieren Sie Ihre gebietsschemaspezifische . TLB-Dateien unter dem Abschnitt TypeLib der Windows-Systemregistrierung. Der dritte Parameter (normalerweise optional) der [Funktion AfxOleRegisterTypeLib](../mfc/reference/registering-ole-controls.md#afxoleregistertypelib) wird zu diesem Zweck bereitgestellt. Im folgenden Beispiel wird eine französische Typbibliothek für ein ActiveX-Steuerelement registriert:

[!code-cpp[NVC_MFC_AxLoc#2](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_2.cpp)]

Wenn Ihr Steuerelement registriert `AfxOleRegisterTypeLib` ist, sucht die Funktion automatisch nach der angegebenen . TLB-Datei im selben Verzeichnis wie das Steuerelement und registriert sie in der Windows-Registrierungsdatenbank. Wenn die . TLB-Datei wurde nicht gefunden, die Funktion hat keine Wirkung.

## <a name="localizing-the-controls-user-interface"></a><a name="_core_localizing_the_control.92.s_user_interface"></a>Lokalisieren der Benutzeroberfläche des Steuerelements

Um die Benutzeroberfläche eines Steuerelements zu lokalisieren, platzieren Sie alle benutzersichtbaren Ressourcen des Steuerelements (z. B. Eigenschaftenseiten und Fehlermeldungen) in sprachspezifischen Ressourcen-DLLs. Anschließend können Sie die Ambient LocaleID-Eigenschaft des Containers verwenden, um die entsprechende DLL für das Gebietsschema des Benutzers auszuwählen.

Im folgenden Codebeispiel wird ein Ansatz zum Suchen und Laden der Ressourcen-DLL für ein bestimmtes Gebietsschema veranschaulicht. Diese Memberfunktion, `GetLocalizedResourceHandle` die für dieses Beispiel aufgerufen wird, kann eine Memberfunktion Ihrer ActiveX-Steuerelementklasse sein:

[!code-cpp[NVC_MFC_AxLoc#3](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_3.cpp)]

Beachten Sie, dass die Untersprachen-ID in jedem Fall der Switch-Anweisung überprüft werden kann, um eine speziellere Lokalisierung bereitzustellen. Eine Demonstration dieser Funktion finden `GetResourceHandle` Sie in der Funktion im MFC ActiveX-Steuerelementbeispiel [LOCALIZE](../overview/visual-cpp-samples.md).

Wenn sich das Steuerelement zum ersten Mal in einen Container lädt, kann es [COleControl::AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid) aufrufen, um die Gebietsschema-ID abzurufen. Das Steuerelement kann dann den zurückgegebenen `GetLocalizedResourceHandle` Gebietsschema-ID-Wert an die Funktion übergeben, die die richtige Ressourcenbibliothek lädt. Das Steuerelement sollte das resultierende Handle ggf. an [AfxSetResourceHandle](../mfc/reference/application-information-and-management.md#afxsetresourcehandle)übergeben:

[!code-cpp[NVC_MFC_AxLoc#4](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_4.cpp)]

Platzieren Sie das obige Codebeispiel in einer Memberfunktion des Steuerelements, z. B. einer Außerkraftsetzung von [COleControl::OnSetClientSite](../mfc/reference/colecontrol-class.md#onsetclientsite). Darüber hinaus sollte *m_hResDLL* eine Membervariable der Steuerelementklasse sein.

Sie können eine ähnliche Logik zum Lokalisieren der Eigenschaftenseite eines Steuerelements verwenden. Um die Eigenschaftenseite zu lokalisieren, fügen Sie Code hinzu, der dem folgenden Beispiel ähnelt, zur Implementierungsdatei Ihrer Eigenschaftenseite (in einer Außerkraftsetzung von [COlePropertyPage::OnSetPageSite):](../mfc/reference/colepropertypage-class.md#onsetpagesite)

[!code-cpp[NVC_MFC_AxLoc#5](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_5.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)
