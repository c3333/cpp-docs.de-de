---
title: Erstellen einer OpenGL ES-Anwendung für Android und iOS
ms.date: 10/09/2019
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
ms.openlocfilehash: 278fd66202332417f7663542f0d66a3ec545b715
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924303"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Erstellen einer OpenGL ES-Anwendung für Android und iOS

Sie können Visual Studio-Projekte und -Projektmappen für iOS-Apps und Android-Apps erstellen, die gemeinsamen Code nutzen. Dieser Artikel führt Sie durch eine kombinierte Lösungs Vorlage. Es erstellt sowohl eine IOS-App als auch eine Android Native Activity-app. Die Apps verwenden gemeinsamen C++-Code, der OpenGL ES verwendet, um denselben animierten rotierenden Cube auf jeder Plattform anzuzeigen. OpenGL es (OpenGL für eingebettete Systeme oder GLES) ist eine 2D-und 3D-Grafik-API. Dies wird auf vielen mobilen Geräten unterstützt.

## <a name="requirements"></a>Requirements (Anforderungen)

Erfüllen aller Systemanforderungen zum Erstellen einer OpenGL es-App für IOS und Android. Installieren Sie die Workload „Mobile-Entwicklung mit C++“ im Visual Studio-Installer, sofern dies nicht bereits erfolgt ist. Zum Abrufen der OpenGL ES-Vorlagen und Entwickeln für iOS binden Sie die optionalen C++-Entwicklungstools für iOS ein. Installieren Sie zum Erstellen für Android die C++ Android-Entwicklungs Tools und die erforderlichen Drittanbieter Tools: Android NDK, Apache Ant und Google Android-Emulator.

Für eine bessere emulatorleistung auf Intel-Plattformen besteht eine Möglichkeit darin, den Intel Hardware Accelerated Execution Manager (haxm) zu installieren. Ausführliche Anweisungen finden Sie unter [Installieren der plattformübergreifenden mobilen Entwicklung mit C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md).

Zum Erstellen und Testen der IOS-App benötigen Sie einen Mac-Computer. Richten Sie ihn gemäß den Installationsanweisungen ein. Weitere Informationen zum Einrichten von für die IOS-Entwicklung finden Sie unter [Installieren und Konfigurieren von Tools zum Erstellen mit IOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="create-a-new-opengles-application-project"></a>Erstellen eines neuen OpenGLES-Anwendungsprojekts

In diesem Tutorial erstellen Sie zunächst ein neues OpenGL ES-Anwendungsprojekt, und dann erstellen Sie die Standard-App und führen sie im Android-Emulator aus. Als Nächstes erstellen Sie die App für iOS und führen sie auf einem iOS-Gerät aus.

::: moniker range="msvc-150"

1. Wählen Sie in Visual Studio **Datei** > **neu** > **Projekt** aus.

1. Wählen Sie im Dialogfeld **Neues Projekt** unter **Vorlagen** die Option **Visual C++** > **Plattformübergreifend** und dann die Vorlage **OpenGLES-Anwendung (Android, iOS)** aus.

1. Geben Sie der App einen Namen wie *MyOpenGLESApp* , und klicken Sie dann auf **OK** .

   ![Erstellen eines neuen OpenGLES-Anwendungsprojekts](../cross-platform/media/cppmdd-opengles-newproj.png "Erstellen eines neuen OpenGLES-Anwendungsprojekts")

   Visual Studio erstellt die neue Projektmappe und öffnet den Projektmappen-Explorer.

   ![MyOpenGLESApp im Projektmappen-Explorer](../cross-platform/media/cppmdd-opengles-solexpl.png "MyOpenGLESApp im Projektmappen-Explorer")

::: moniker-end

::: moniker range=">=msvc-160"

1. Wählen Sie in Visual Studio **Datei** > **neu** > **Projekt** aus.

1. Wählen Sie im Dialogfeld **Neues Projekt erstellen** die Vorlage **OpenGLES-Anwendung (Android, iOS)** aus, und klicken Sie dann auf **Weiter** .

1. Geben Sie im Dialogfeld **Neues Projekt konfigurieren** einen Namen wie *MyOpenGLESApp* in **Projektname** ein, und klicken Sie dann auf **Erstellen** .

   Visual Studio erstellt die neue Projektmappe und öffnet den Projektmappen-Explorer.

   ![MyOpenGLESApp im Projektmappen-Explorer](../cross-platform/media/cppmdd-opengles-solexpl.png "MyOpenGLESApp im Projektmappen-Explorer")

::: moniker-end

Die neue OpenGL ES-Anwendungsprojektmappe umfasst drei Bibliotheksprojekte und zwei Anwendungsprojekte. Der Bibliotheks Ordner enthält ein Projekt mit frei gegebenem Code. Und zwei plattformspezifische Projekte, die auf den gemeinsam verwendeten Code verweisen:

- `MyOpenGLESApp.Android.NativeActivity` enthält die Verweise und den Verbindungscode, mit denen Ihre App als eine systemeigene Aktivität auf Android implementiert werden kann. Die Einstiegspunkte aus dem Verbindungscode sind in der Datei *main.cpp* implementiert, die den gemeinsamen Code in `MyOpenGLESApp.Shared` enthält. Vorkompilierte Header befinden sich in *pch.h* . Das Native Activity-App-Projekt wird in eine gemeinsam genutzte Bibliotheksdatei ( *SO* ) kompiliert, die durch das `MyOpenGLESApp.Android.Packaging`-Projekt ausgewählt wird.

- `MyOpenGLESApp.iOS.StaticLibrary` erstellt eine statische iOS-Bibliotheksdatei ( *A* )-Datei mit dem freigegebenen Code in `MyOpenGLESApp.Shared`. Diese ist mit der vom `MyOpenGLESApp.iOS.Application`-Projekt erstellten App verknüpft.

- `MyOpenGLESApp.Shared` enthält den freigegebenen Code, der plattformübergreifend verwendet werden kann. Die App verwendet Präprozessormakros für die bedingte Kompilierung von plattformspezifischem Code. Der freigegebene Code wird durch den Projektverweis sowohl in `MyOpenGLESApp.Android.NativeActivity` als auch `MyOpenGLESApp.iOS.StaticLibrary` übernommen.

Die Projektmappe enthält zwei Projekte zum Erstellen der Apps für die Android- und iOS-Plattform:

- `MyOpenGLESApp.Android.Packaging` erstellt die *APK* -Datei für die Bereitstellung auf einem Android-Gerät oder -Emulator. Diese Datei enthält die Ressourcen sowie die Datei „AndroidManifest.xml“, in der Sie Manifesteigenschaften festlegen. Es enthält zudem die Datei *build.xml* , die den Ant-Buildprozess steuert. Es ist standardmäßig als Startprojekt festgelegt, sodass es bereitgestellt und direkt in Visual Studio ausgeführt werden kann.

- `MyOpenGLESApp.iOS.Application` enthält die Ressourcen und Objective-C-Verbindungscode zum Erstellen einer iOS-App, die mit dem Code der statischen C++-Bibliothek in `MyOpenGLESApp.iOS.StaticLibrary` verknüpft ist. Dieses Projekt erstellt ein Buildpaket, das von Visual Studio und dem Remote-Agent auf Ihren Mac übertragen wird. Beim Erstellen dieses Projekts sendet Visual Studio die Dateien und Befehle zum Erstellen und Bereitstellen der App auf dem Mac.

## <a name="build-and-run-the-android-app"></a>Erstellen und Ausführen der Android-App

Durch die von der Vorlage erstellte Projektmappe wird die Android-App als Standardprojekt festgelegt.  Sie können die App erstellen und ausführen, um die Installation und Einrichtung zu überprüfen. Führen Sie die App in einem ersten Test in einem der Geräteprofile aus, die vom Emulator für Android installiert werden. Wenn Sie Ihre APP auf einem anderen Ziel testen möchten, können Sie den Ziel Emulator laden. Alternativ dazu können Sie ein Gerät mit Ihrem Computer verbinden.

### <a name="to-build-and-run-the-android-native-activity-app"></a>So erstellen und führen Sie die Android Native Activity-App aus

1. Wählen Sie **x86** aus der Dropdownliste **Projektmappenplattformen** aus (falls diese Plattform nicht bereits ausgewählt ist).

   ![Festlegen der Projektmappenplattform auf x86](../cross-platform/media/cppmdd-opengles-solutionplat.png "Festlegen der Projektmappenplattform auf "x86"")

   Wählen Sie "x86" aus, wenn Sie den Emulator als Ziel verwenden möchten. Um ein Gerät als Ziel zu verwenden, wählen Sie je nach Geräteprozessor die entsprechende Projektmappenplattform aus. Wenn die Liste **Projektmappenplattformen** nicht angezeigt wird, wählen Sie **Projektmappenplattformen** aus der Liste **Schaltflächen hinzufügen/entfernen** aus, und wählen Sie dann Ihre Plattform aus.

1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das `MyOpenGLESApp.Android.Packaging`-Projekt, und wählen Sie dann **Erstellen** aus.

   ![Erstellen eines Android-Paketprojekts](../cross-platform/media/cppmdd-opengles-andbuild.png "Erstellen eines Android-Paketprojekts")

   Das Ausgabefenster zeigt die Ausgabe des Buildprozesses für die freigegebene Android-Bibliothek und die Android-App an.

   ![Buildausgabe für Android-Objekte](../cross-platform/media/cppmdd-opengles-andoutput.png "Buildausgabe für Android-Objekte")

1. Wählen Sie eins der emulierten Android-Geräteprofile als Bereitstellungsziel aus.

   ![Auswählen des Bereitstellungsziels](../cross-platform/media/cppmdd-opengles-pickemulator.png "Auswählen des Bereitstellungsziels")

   Möglicherweise haben Sie andere Emulatoren installiert oder mit einem Android-Gerät verbunden. Sie können Sie in der Dropdown Liste Bereitstellungs Ziel auswählen. Damit die App ausgeführt werden kann, muss die integrierte Projektmappenplattform mit der Plattform des Zielgeräts übereinstimmen.

1. Drücken Sie **F5** , um das Debuggen zu starten **, oder drücken** + Sie **F5** , um ohne Debugging

   Visual Studio startet den Emulator, wobei das Laden und Bereitstellen Ihres Codes mehrere Sekunden in Anspruch nimmt. So wird die App im Emulator angezeigt:

   ![Ausführen einer App im Android-Emulator](../cross-platform/media/cppmdd-opengles-andemulator.png "Ausführen einer App im Android-Emulator")

   Nachdem Ihre App gestartet wurde, können Sie Haltepunkte festlegen und den Debugger verwenden, um den Code schrittweise zu durchlaufen, lokale Variablen zu prüfen und Werte anzuzeigen.

1. Drücken Sie **UMSCHALT** + **Taste F5** , um das Debugging zu verhindern.

   Der Emulator ist ein separater Prozess, der weiterhin ausgeführt wird. Sie können Ihren Code mehrfach auf demselben Emulator bearbeiten, kompilieren und bereitstellen. Die App wird in der App-Sammlung für den Emulator angezeigt und kann direkt von dort aus gestartet werden.

   Die generierten Android Native Activity-APP-und Bibliotheks Projekte legen den freigegebenen C++-Code in einer dynamischen Bibliothek ab. Es enthält "Klebe Code" für die Schnittstelle mit der Android-Plattform. Der größte Teil des App-Codes befindet sich in der-Bibliothek. Manifest, Ressourcen und Buildanweisungen befinden sich im Paket Erstellungs Projekt. Der freigegebene Code wird von "main.cpp" im NativeActivity-Projekt aufgerufen. Weitere Informationen über das Programmieren einer Android Native Activity-App finden Sie im Android Developer NDK auf der Seite [Konzepte](https://developer.android.com/ndk/guides/concepts.html) .

   Visual Studio erstellt Android Native Activity-Projekte mithilfe des Android-NDK. Clang wird als Platt Form Toolset verwendet. Visual Studio ordnet die Eigenschaften des Projekts den Befehlen zum Kompilieren, verknüpfen und Debuggen auf der Zielplattform zu. Um weitere Informationen zu erhalten, öffnen Sie das Dialogfeld **Eigenschaftenseiten** des MyOpenGLESApp.Android.NativeActivity-Projekts. Weitere Informationen zu den Befehlszeilenschaltern finden Sie im [Clang Compiler-Benutzerhandbuch](https://clang.llvm.org/docs/UsersManual.html) (in englischer Sprache).

## <a name="build-and-run-the-ios-app-on-an-ios-device"></a>Erstellen und Ausführen der iOS-App auf einem iOS-Gerät

Sie erstellen und bearbeiten das IOS-App-Projekt in Visual Studio. Aufgrund von Lizenzierungs Einschränkungen muss Sie von einem Mac erstellt und bereitgestellt werden. Visual Studio kommuniziert mit einem Remote-Agent, der auf dem Mac ausgeführt wird, um Projektdateien zu übertragen und Build-, Bereitstellungs- und Debugbefehle auszuführen. Sie müssen Ihren Mac und Visual Studio für die Kommunikation einrichten und konfigurieren, bevor Sie die iOS-App erstellen können. Ausführliche Anweisungen finden Sie unter [Installieren und Konfigurieren von Tools zum Erstellen mit iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Führen Sie den Remote-Agent auf Ihrem Mac aus, und koppeln Sie ihn mit Visual Studio. Anschließend können Sie die IOS-app erstellen und ausführen, um Ihre Installation und Einrichtung zu überprüfen.

Zum Bereitstellen der APP auf einem IOS-Gerät richten Sie zunächst die automatische Signierung in Xcode ein. Bei der automatischen Signierung wird ein Bereitstellungs Profil erstellt, um einen Build der APP zu signieren.

### <a name="to-set-up-automatic-signing-on-xcode"></a>So richten Sie die automatische Signierung in Xcode ein

1. Installieren Sie [Xcode](https://developer.apple.com/xcode/) auf Ihrem Mac, sofern noch nicht geschehen.

1. Öffnen Sie die Xcode-App auf Ihrem Mac.

1. Erstellen Sie ein neues Xcode-Projekt für eine **Einzelansichtanwendung** . Füllen Sie bei der Projekterstellung die Pflichtfelder aus. Die Werte können beliebig sein, da das Projekt nur zum Erstellen eines Bereitstellungsprofils verwendet wird, mit dem später ein Build der App signiert werden soll.

1. Fügen Sie dem Xcode Ihre Apple ID hinzu, die in einem [Apple Developer Program](https://developer.apple.com/programs/)-Konto registriert ist. Ihre Apple ID wird als Signierungsidentität zum Signieren von Apps verwendet. Um die Signierungsidentität zu Xcode hinzuzufügen, öffnen Sie das Menü **Xcode** , und wählen Sie **Einstellungen** aus. Wählen Sie **Konten** aus, und klicken Sie auf die Schaltfläche „Hinzufügen“ (+), um Ihre Apple ID hinzuzufügen. Detaillierte Anweisungen finden Sie unter [Hinzufügen Ihres Apple ID-Kontos](https://help.apple.com/xcode/mac/current/#/devaf282080a).

1. Ändern Sie in den allgemeinen Einstellungen Ihres Xcode-Projekts den **Paketbezeichner** zu `com.<NameOfVSProject>`, wobei `<NameOfVSProject>` der Name des von Ihnen erstellten Visual Studio-Projektmappenprojekts ist. Ein Beispiel: Wenn Sie ein Projekt namens `MyOpenGLESApp` in Visual Studio erstellt haben, legen Sie den **Paketbezeichner** auf `com.MyOpenGLESApp` fest.

   ![Xcode-Bündel-ID](../cross-platform/media/cppmdd-opengles-iosxcodeid.png "Xcode-Bündel-ID")

1. Um das automatische Signieren zu aktivieren, aktivieren Sie das Kontrollkästchen **Signierung automatisch verwalten**.

   ![Automatische Signatur von Xcode](../cross-platform/media/cppmdd-opengles-iosxcodesign.png "Automatische Signatur von Xcode")

1. Wählen Sie den Teamnamen der Apple ID aus, die Sie als **Team** für die Entwicklung hinzugefügt haben.

   ![Xcode-Team](../cross-platform/media/cppmdd-opengles-iosxcodeteam.png "Xcode-Team")

### <a name="to-build-and-run-the-ios-app-on-an-ios-device"></a>So erstellen Sie die iOS-App auf einem iOS-Gerät und führen sie aus

1. Führen Sie den Remote-Agent auf Ihrem Mac aus, und stellen Sie sicher, dass Visual Studio mit dem Remote-Agent gekoppelt ist. Wenn Sie den Remote-Agent starten möchten, öffnen Sie ein Terminal-App-Fenster, und geben Sie `vcremote`. Weitere Informationen finden Sie unter [Konfigurieren des Remote-Agents in Visual Studio](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS).

   ![Mac-Terminalfenster bei Ausführung von „vcremote“](../cross-platform/media/cppmdd-common-vcremote.png "Mac Terminal-Fenster bei Ausführung von "vcremote"")

1. Schließen Sie ein iOS-Gerät an Ihren Mac an. Wenn Sie ein Gerät zum ersten Mal an einen Computer anschließen, werden Sie in einer Warnung gefragt, ob der Computer auf das Gerät zugreifen darf. Teilen Sie dem Gerät mit, dass es dem Mac-Computer vertrauen darf.

1. Wählen Sie in Visual Studio aus der Dropdownliste **Projektmappenplattformen** die Projektmappenplattform aus, die dem Geräteprozessor entspricht (sofern diese nicht bereits ausgewählt ist). In diesem Beispiel handelt es sich um einen **ARM64** -Prozessor.

   ![Festlegen der Projektmappenplattform auf ARM64](../cross-platform/media/cppmdd-opengles-pickplatformarm64.png "Festlegen der Projektmappenplattform auf ARM64")

1. Öffnen Sie im Projektmappen-Explorer das Kontextmenü des MyOpenGLESApp.iOS.Application-Projekts, und wählen Sie **Projekt entladen** aus, um das Projekt zu entladen.

1. Öffnen Sie erneut das Kontextmenü für das entladene MyOpenGLESApp.iOS.Application-Projekt, und wählen Sie **„project.pbxproj“ bearbeiten** aus, um die Projektdatei zu bearbeiten. Suchen Sie in der Datei `project.pbxproj` nach dem `buildSettings`-Attribut, und fügen Sie `DEVELOPMENT_TEAM` mit Ihrer Apple Team ID hinzu. Der Screenshot unten zeigt einen Beispielwert von `123456ABC` für die Apple Team ID. Sie finden den Wert Ihrer Apple Team ID in Xcode. Wechseln Sie zu **Buildeinstellungen** , und halten Sie den Mauszeiger auf den Namen Ihres Entwicklungsteams, um eine QuickInfo anzuzeigen. Die QuickInfo zeigt Ihre Team-ID an.

   ![Festlegen des Entwicklungsteams](../cross-platform/media/cppmdd-opengles-iosdevelopmentteam.png "Festlegen des Entwicklungsteams")

1. Schließen Sie die Datei `project.pbxproj`. Öffnen Sie dann das Kontextmenü für das entladene MyOpenGLESApp.iOS.Application-Projekt, und wählen Sie **Projekt erneut laden** aus, um das Projekt erneut zu laden.

1. Erstellen Sie jetzt das MyOpenGLESApp.iOS.Application-Projekt, indem Sie das Kontextmenü des Projekts öffnen und **Build** auswählen.

   ![Erstellen eines iOS-Anwendungsprojekts](../cross-platform/media/cppmdd-opengles-iosbuild.png "Erstellen eines iOS-Anwendungsprojekts")

   Im Fenster Ausgabe wird die Ausgabe des Buildprozesses angezeigt. Es zeigt Ergebnisse für die statische IOS-Bibliothek und die IOS-APP an. Auf dem Mac zeigt das Terminal-Fenster, in dem der Remote-Agent ausgeführt wird, die Befehls- und Dateiübertragungsaktivitäten an.

   Auf Ihrem Mac-Computer werden Sie möglicherweise aufgefordert, Codesign den Zugriff auf Ihre Keychain zu ermöglichen. Wählen Sie **Zulassen** aus, um den Vorgang fortzusetzen.

1. Wählen Sie auf der Symbolleiste Ihr iOS-Gerät aus, um die App auf dem Gerät auszuführen, das an Ihren Mac angeschlossen ist. Wenn die App nicht gestartet wird, vergewissern Sie sich, dass das Gerät der bereitgestellten Anwendung die Berechtigung für die Ausführung auf dem Gerät erteilt hat. Diese Berechtigung kann festgelegt werden, indem Sie zu **Einstellungen**  >  **Allgemeine**  >  **Geräteverwaltung** auf dem Gerät wechseln. Wählen Sie das Konto Ihrer Developer-App aus, legen Sie das Konto als vertrauenswürdig fest, und überprüfen Sie die App. Versuchen Sie erneut, die App in Visual Studio auszuführen.

   ![iOS-App auf iOS-Gerät](../cross-platform/media/cppmdd-opengles-iosdevice.png "iOS-App auf iOS-Gerät")

   Nachdem Ihre App gestartet wurde, können Sie Haltepunkte festlegen und den Visual Studio-Debugger verwenden, um lokale Variablen zu prüfen, die Aufrufliste anzuzeigen und Werte zu überwachen.

   ![Debugger an Haltepunkt in iOS-App](../cross-platform/media/cppmdd-opengles-iosdebug.png "Debugger an Haltepunkt in iOS-App")

1. Drücken Sie **UMSCHALT** + **Taste F5** , um das Debugging zu verhindern.

   Der C++-Code wird von den generierten iOS-App- und -Bibliotheksprojekten in einer statischen Bibliothek abgelegt, die nur den freigegebenen Code implementiert. Der Hauptteil des Anwendungscodes befindet sich im `Application`-Projekt. Die Aufrufe des freigegebenen Bibliothekscodes in diesem Vorlagenprojekt werden in der Datei *GameViewController.m* ausgeführt. Zur Erstellung der iOS-App verwendet Visual Studio das Xcode-Plattformtoolset, das die Kommunikation mit einem Remoteclient erfordert, der auf einem Mac ausgeführt wird.

   Visual Studio überträgt die Projektdateien an den Remote Client. Anschließend sendet er Befehle zum Erstellen der App mithilfe von Xcode. Der Remoteclient sendet Buildstatusinformationen zurück an Visual Studio. Nachdem die APP erfolgreich erstellt wurde, kann Visual Studio Befehle senden, um die APP auszuführen und zu debuggen. Der Debugger in Visual Studio steuert die App, die auf dem an Ihren Mac angeschlossenen iOS-Gerät ausgeführt wird. Visual Studio ordnet Projekteigenschaften den Optionen zu, die zum Kompilieren, verknüpfen und Debuggen auf der IOS-Zielplattform verwendet werden. Um ausführliche Informationen zur Compiler-Befehlszeilenoption zu erhalten, öffnen Sie das Dialogfeld **Eigenschaftenseiten** für das MyOpenGLESApp.iOS.StaticLibrary-Projekt.

## <a name="customize-your-apps"></a>Anpassen der Apps

Sie können den freigegebenen C++-Code bearbeiten, um allgemeine Funktionen hinzuzufügen oder zu ändern. Ändern Sie die Aufrufe des freigegebenen Codes in `MyOpenGLESApp.Android.NativeActivity` den `MyOpenGLESApp.iOS.Application` Projekten und entsprechend. Sie können Präprozessormakros verwenden, um plattformspezifische Abschnitte im gemeinsamen Code anzugeben. Der Präprozessormakro `__ANDROID__` ist bei der Erstellung für Android vordefiniert. Der Präprozessormakro `__APPLE__` ist bei der Erstellung für iOS vordefiniert.

Um IntelliSense für eine bestimmte Projektplattform anzuzeigen, wählen Sie das Projekt in der Dropdown Liste Kontext Umschaltung aus. Sie befindet sich in der Navigationsleiste oben im Editor Fenster.

![Dropdownelement zum Wechseln des Projektkontexts im Editor](../cross-platform/media/cppmdd-opengles-contextswitcher.png)

IntelliSense-Probleme im vom aktuellen Projekt verwendeten Code sind durch eine rote Wellenlinie gekennzeichnet. Ein lila Wellenlinien Kennzeichen in anderen Projekten. Visual Studio unterstützt weder eine farbliche Kennzeichnung von Code noch IntelliSense für Java- oder Objective-C-Dateien. Sie können jedoch weiterhin die Quelldateien und-Ressourcen ändern. Verwenden Sie diese, um den Anwendungsnamen, das Symbol und weitere Implementierungsdetails festzulegen.
