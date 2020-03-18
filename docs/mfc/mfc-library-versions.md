---
title: MFC-Bibliotheksversionen
ms.date: 05/08/2019
helpviewer_keywords:
- class libraries [MFC], building versions
- version information [MFC], MFC library
- MFC class library
- MFC class library, building
- MFC libraries
- MFC, library versions
- libraries [MFC], versions
ms.openlocfilehash: b8e32366d9ff43bd6e5770f64f0ba9d8bf6e56ab
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425700"
---
# <a name="mfc-library-versions"></a>MFC-Bibliotheksversionen

Die MFC-Bibliothek ist in Versionen verfügbar, die ANSI-Einzel Byte-und MBCS-Code (Multibytezeichen-Zeichensatz) unterstützen, sowie Versionen, die Unicode (codiert als UTF-16LE, den Windows-systemeigenen Zeichensatz) unterstützen. Jede MFC-Version ist als statische Bibliothek oder als freigegebene DLL verfügbar. Es gibt auch eine kleinere Version der statischen MFC-Bibliothek, mit der MFC-Steuerelemente für Dialoge weggelassen werden, für Anwendungen, die sehr sensibel für die Größe sind und diese Steuerelemente nicht benötigen. Die MFC-Bibliotheken sind sowohl in Debug-als auch in Releaseversionen für unterstützte Architekturen verfügbar, die x86-, x64-und ARM-Prozessoren enthalten. Sie können sowohl Anwendungen (exe-Dateien) als auch DLLs mit einer beliebigen Version der MFC-Bibliotheken erstellen. Es gibt auch eine Reihe von MFC-Bibliotheken, die für die Schnittstellen mit verwaltetem Code kompiliert werden. Die freigegebenen MFC-DLLs enthalten eine Versionsnummer, die die Binärkompatibilität der Bibliothek angibt.

## <a name="automatic-linking-of-mfc-library-versions"></a>Automatisches Verknüpfen von MFC-Bibliotheksversionen

Die MFC-Header Dateien bestimmen automatisch die korrekte Version der MFC-Bibliothek, die verknüpft werden soll, basierend auf den Werten, die in der Buildumgebung definiert sind. Die MFC-Header Dateien fügen Compilerdirektiven hinzu, die den Linker anweisen, eine Verknüpfung mit einer bestimmten Version der MFC-Bibliothek zu verknüpfen.

Beispielsweise das AFX. Die H-Header Datei weist den Linker an, eine Verknüpfung in der vollständigen statischen, beschränkten oder freigegebenen DLL-Version von MFC zu verknüpfen. ANSI/MBCS oder Unicode-Version; und Debug-oder Verkaufsversion, abhängig von der Buildkonfiguration:

```cpp
#ifndef _AFXDLL
    #ifdef _AFX_NO_MFC_CONTROLS_IN_DIALOGS
        #ifdef _DEBUG
            #pragma comment(lib, "afxnmcdd.lib")
        #else
            #pragma comment(lib, "afxnmcd.lib")
        #endif
        #pragma comment(linker, "/include:__afxNoMFCControlSupportInDialogs")
        #pragma comment(linker, "/include:__afxNoMFCControlContainerInDialogs")
    #endif
    #ifndef _UNICODE
        #ifdef _DEBUG
            #pragma comment(lib, "nafxcwd.lib")
        #else
            #pragma comment(lib, "nafxcw.lib")
        #endif
    #else
        #ifdef _DEBUG
            #pragma comment(lib, "uafxcwd.lib")
        #else
            #pragma comment(lib, "uafxcw.lib")
        #endif
    #endif
#else
    #ifndef _UNICODE
        #ifdef _DEBUG
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "d.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "d.lib")
        #else
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER ".lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER ".lib")
        #endif
    #else
        #ifdef _DEBUG
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "ud.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "ud.lib")
        #else
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "u.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "u.lib")
        #endif
    #endif
#endif
```

MFC-Header Dateien enthalten auch Direktiven, die in allen erforderlichen Bibliotheken verknüpft werden müssen, einschließlich MFC-Bibliotheken, Win32-Bibliotheken, OLE-Bibliotheken, aus Beispielen, ODBC-Bibliotheken und so weiter erstellte OLE-Bibliotheken.

## <a name="ansi-mbcs-and-unicode"></a>ANSI, MBCS und Unicode

Die MFC-Versionen der ANSI/MBCS-Bibliothek unterstützen sowohl Einzel Byte-Zeichensätze, wie z. b. ASCII, als auch Multibytezeichen-Zeichensätze wie Shift-JIS. Die Versionen der MFC-Unicode-Bibliothek unterstützen Unicode in der UTF-16LE-Zeichenfolge mit breit Zeichen. Verwenden Sie die ANSI/MBCS-Bibliotheksversionen von MFC für die UTF-8-codierte Unicode-Unterstützung.

Verwenden Sie das Dialogfeld " **Projekteigenschaften** ", um die Projekt Konfiguration für die Verwendung von Einzel Byte-, Multibyte-oder breit Zeichen-Unicode-Zeichen folgen-und Zeichen Unterstützung in der IDE festzulegen. Legen Sie auf der Seite **Konfigurations Eigenschaften** > **Allgemein** die **Zeichensatz** -Eigenschaft auf **nicht festgelegt** fest, um einen Einzel Byte-Zeichensatz zu verwenden. Legen Sie die-Eigenschaft so fest, dass Sie einen **Multibytezeichen-** Zeichensatz verwendet, um einen Multibytezeichen-Zeichensatz zu verwenden, oder um Unicode- **Zeichensätze** für die Verwendung von Unicode als UTF-16-

MFC-Projekte verwenden das Präprozessorsymbol \_Unicode zum Angeben von UTF-16-Unicode-Unterstützung für breit Zeichen und \_MBCS, um die MBCS-Unterstützung anzugeben. Diese Optionen schließen sich in einem Projekt gegenseitig aus.

## <a name="mfc-static-library-naming-conventions"></a>Benennungs Konventionen für statische MFC-Bibliothek

Statische Bibliotheken für MFC verwenden die folgenden Benennungs Konventionen. Die Bibliotheksnamen haben das Format

> <em>u</em> AFX-<em>CD</em>. LIB

Dabei sind die in kursiv Kleinbuchstaben gezeigten Buchstaben Platzhalter für Bearbeiter, deren Bedeutungen in der folgenden Tabelle dargestellt werden:

|Bezeichner|Werte und Bedeutungen|
|---------------|-------------------------|
|*u*|ANSI/MBCS (N) oder Unicode (U); für Version ohne MFC-Steuerelemente in Dialogfeldern weglassen|
|*c*|Version mit MFC-Steuerelementen in Dialogfeldern (CW) oder ohne (nmcd)|
|*d*|Debug oder Release: D = Debuggen; Spezifizierer für Release weglassen|

Alle Bibliotheken, die in der folgenden Tabelle aufgeführt sind, sind im Verzeichnis "\atlmfc\lib" für unterstützte buildarchitekturen enthalten.

|Bibliothek|Beschreibung|
|-------------|-----------------|
|NAFXCW.LIB|MFC-Bibliothek für statische Links, Releaseversion|
|NAFXCWD.LIB|MFC-Bibliothek für statische Links, Debugversion|
|UAFXCW.LIB|MFC-Bibliothek mit statischem Link mit Unicode-Unterstützung, Releaseversion|
|UAFXCWD.LIB|MFC-Bibliothek mit statischem Link mit Unicode-Unterstützung, Debugversion|
|AFXNMCD.LIB|MFC-Bibliothek für statische Links ohne MFC-Dialogfeld Steuerelemente, Releaseversion|
|AFXNMCDD.LIB|MFC-Bibliothek für statische Links ohne MFC-Dialogfeld Steuerelemente, Debugversion|

Debugger-Dateien mit demselben Basis Namen und einer pdb-Erweiterung sind auch für jede der statischen Bibliotheken verfügbar.

## <a name="mfc-shared-dll-naming-conventions"></a>MFC-Benennungs Konventionen für freigegebene dll

Die freigegebenen MFC-DLLs befolgen auch eine strukturierte Benennungs Konvention. Dies erleichtert es, zu wissen, welche DLL-oder Bibliothek Sie zu welchem Zweck verwenden sollten.

Die MFC-DLLs verfügen über *Versions* Nummern, die auf binäre Kompatibilität hindeuten. Verwenden Sie MFC-DLLs, die dieselbe Version wie die anderen Bibliotheken und das Compilertoolset aufweisen, um die Kompatibilität innerhalb eines Projekts sicherzustellen.

|DLL|Beschreibung|
|---------|-----------------|
|MFC-*Version*. DLL|MFC-DLL, ANSI oder MBCS-Releaseversion|
|MFC-*Version*U. dll|MFC-DLL, Unicode-Releaseversion|
|MFC-*Version*D. dll|MFC-DLL, ANSI-oder MBCS-Debugversion|
|MFC-*Version*UD. DLL|MFC-DLL, Unicode-Debugversion|
|MF-*Version*. DLL|MFC-DLL mit Windows Forms-Steuerelementen, ANSI-oder MBCS-Releaseversion|
|MF-*Version*U. dll|MFC-DLL mit Windows Forms-Steuerelementen, Unicode-Releaseversion|
|MF-*Version*D. dll|MFC-DLL mit Windows Forms-Steuerelementen, ANSI-oder MBCS-Debugversion|
|MF-*Version*UD. DLL|MFC-DLL mit Windows Forms-Steuerelementen, Unicode-Debugversion|

Die Import Bibliotheken, die zum Erstellen von Anwendungen oder MFC-Erweiterungs-DLLs benötigt werden, die diese freigegebenen DLLs verwenden, haben denselben Basis Namen wie die dll, haben aber die Dateinamenerweiterung. lib. Wenn Sie die freigegebenen DLLs verwenden, muss eine kleine statische Bibliothek weiterhin mit dem Code verknüpft werden. Diese Bibliothek heißt MF-*Version*{U} {D}. lib.

Wenn Sie dynamisch eine Verbindung mit der freigegebenen DLL-Version von MFC herstellen, unabhängig davon, ob Sie von einer Anwendung oder einer MFC-Erweiterungs-DLL verwendet wird, müssen Sie die entsprechende MFC-*Version*einschließen. DLL oder MFC-*Version*U. dll, wenn Sie Ihr Produkt bereitstellen.

Eine Liste der visuellen C++ DLLs, die mit Ihren Anwendungen verteilt werden können, finden Sie unter [verteilbarer Code für Microsoft Visual Studio 2017 und Microsoft Visual Studio 2017 SDK (einschließlich Hilfsprogrammen und Buildserver-Dateien)](/visualstudio/productinfo/2017-redistribution-vs) oder [verteilbarer Code für Visual Studio 2019](/visualstudio/releases/2019/redistribution).

Weitere Informationen zur Unterstützung von MBCS und Unicode in MFC finden Sie [unter Unterstützung für Unicode-und Multibyte-Zeichensätze (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

## <a name="dynamic-link-library-support"></a>Dynamic Link Library-Unterstützung

Zum Erstellen von DLLs, die von MFC-und nicht-MFC-ausführbaren Dateien verwendet werden können, können Sie entweder die statischen oder gemeinsamen MFC-Bibliotheken verwenden. Diese werden als "reguläre DLLs" oder "reguläre MFC-DLLs" bezeichnet, um Sie von MFC-Erweiterungs-DLLs zu unterscheiden, die nur von MFC-apps und MFC-DLLs verwendet werden können. Eine DLL, die mithilfe der statischen MFC-Bibliotheken erstellt wurde, wird in älteren verweisen manchmal als "rdll" bezeichnet, da MFC-DLL-Projekte das Präprozessorsymbol\_"- **rdll**" definieren. Eine DLL, die die freigegebenen MFC-DLLs verwendet, wird in älteren verweisen mitunter als AFXDLL bezeichnet, da Sie das Präprozessorsymbol **\_AFXDLL**definiert.

Wenn Sie das DLL-Projekt erstellen, indem Sie eine Verknüpfung mit den statischen MFC-Bibliotheken herstellen, kann die dll ohne die freigegebenen MFC-DLLs bereitgestellt werden. Wenn das DLL-Projekt mit der MFC-*Version*der Import Bibliotheken verknüpft ist. Lib oder MFC-*Version*U. lib Sie müssen die entsprechende MFC-*Version*der MFC-DLL bereitstellen. DLL oder MFC-*Version*U. dll und die dll. Weitere Informationen finden Sie unter [DLLs](../build/dlls-in-visual-cpp.md).

## <a name="see-also"></a>Siehe auch

[Allgemeine MFC-Themen](../mfc/general-mfc-topics.md)
