---
title: 'TN033: DLL-Version der MFC'
ms.date: 06/28/2018
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
ms.openlocfilehash: ad4cb883cfe7e397cf599d659afb02b23501dc5a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370310"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033: DLL-Version der MFC

In diesem Hinweis wird beschrieben, wie Sie die gemeinsam genutzten dynamischen Linkbibliotheken MFCxx.DLL und MFCxxD.DLL (wobei x die MFC-Versionsnummer ist) mit MFC-Anwendungen und MFC-Erweiterungs-DLLs verwenden können. Weitere Informationen zu regulären MFC-DLLs finden Sie unter [Verwenden von MFC als Teil einer DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

Dieser technische Hinweis behandelt drei Aspekte von DLLs. Die letzten beiden sind für fortgeschrittene Benutzer:

- [Wie Sie eine MFC-Erweiterungs-DLL erstellen](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [So erstellen Sie eine MFC-Anwendung, die die DLL-Version von MFC verwendet](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [Implementierung der freigegebenen Dynamic-Link-Bibliotheken von MFC](#_mfcnotes_how_the_mfc30.dll_is_implemented)

Wenn Sie daran interessiert sind, eine DLL mit MFC zu erstellen, die mit Nicht-MFC-Anwendungen verwendet werden kann (dies wird als reguläre MFC-DLL bezeichnet), lesen Sie den [Technischen Hinweis 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>Überblick über MFCxx.DLL Support: Terminologie und Dateien

**Reguläre MFC-DLL:** Sie verwenden eine reguläre MFC-DLL, um eine eigenständige DLL mit einigen der MFC-Klassen zu erstellen. Schnittstellen über die App/DLL-Grenze hinweg sind "C"-Schnittstellen, und die Clientanwendung muss keine MFC-Anwendung sein.

Dies ist die Version der DLL-Unterstützung, die in MFC 1.0 unterstützt wird. Es wird in [Technical Note 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md) und dem MFC Advanced Concepts Beispiel [DLLScreenCap](../overview/visual-cpp-samples.md)beschrieben.

> [!NOTE]
> Ab Visual C++-Version 4.0 ist der Begriff **USRDLL** veraltet und wurde durch eine reguläre MFC-DLL ersetzt, die statisch mit MFC verknüpft ist. Sie können auch eine reguläre MFC-DLL erstellen, die dynamisch mit MFC verknüpft ist.

MFC 3.0 (und höher) unterstützt reguläre MFC-DLLs mit allen neuen Funktionen, einschließlich der OLE- und Database-Klassen.

**AFXDLL**: Dies wird auch als freigegebene Version der MFC-Bibliotheken bezeichnet. Dies ist die neue DLL-Unterstützung, die in MFC 2.0 hinzugefügt wurde. Die MFC-Bibliothek selbst befindet sich in einer Reihe von DLLs (siehe unten), und eine Clientanwendung oder DLL verknüpft die benötigten DLLs dynamisch. Schnittstellen über die Anwendungs-/DLL-Grenze hinweg sind C++/MFC-Klassenschnittstellen. Die Clientanwendung MUSS eine MFC-Anwendung sein. Dies unterstützt alle MFC 3.0-Funktionen (Ausnahme: UNICODE wird für die Datenbankklassen nicht unterstützt).

> [!NOTE]
> Ab Visual C++-Version 4.0 wird dieser DLL-Typ als "Erweiterungs-DLL" bezeichnet.

Dieser Hinweis verwendet MFCxx.DLL, um auf den gesamten MFC-DLL-Satz zu verweisen, der Folgendes umfasst:

- Debuggen: MFCxxD.DLL (kombiniert) und MFCSxxD.LIB (statisch).

- Version: MFCxx.DLL (kombiniert) und MFCSxx.LIB (statisch).

- Unicode-Debug: MFCxxUD.DLL (kombiniert) und MFCSxxD.LIB (statisch).

- Unicode Release: MFCxxU.DLL (kombiniert) und MFCSxxU.LIB (statisch).

> [!NOTE]
> The MFCSxx[U][D]. LIB-Bibliotheken werden in Verbindung mit den freigegebenen MFC-DLLs verwendet. Diese Bibliotheken enthalten Code, der statisch mit der Anwendung oder DLL verknüpft sein muss.

Eine Anwendung verknüpft die entsprechenden Importbibliotheken:

- Debuggen: MFCxxD.LIB

- Veröffentlichung: MFCxx.LIB

- Unicode-Debug: MFCxxUD.LIB

- Unicode-Version: MFCxxU.LIB

Eine "MFC Extension DLL" ist eine DLL, die auf MFCxx.DLL (und/oder den anderen freigegebenen MFC-DLLs) basiert. Hier tritt die MFC-Komponentenarchitektur auf. Wenn Sie eine nützliche Klasse von einer MFC-Klasse ableiten oder ein anderes MFC-ähnliches Toolkit erstellen, können Sie sie in einer DLL platzieren. Diese DLL verwendet MFCxx.DLL, ebenso wie die ultimative Clientanwendung. Dies ermöglicht wiederverwendbare Blattklassen, wiederverwendbare Basisklassen und wiederverwendbare Ansichts-/Dokumentklassen.

## <a name="pros-and-cons"></a>Vor- und Nachteile

Warum sollten Sie die freigegebene Version von MFC verwenden?

- Die Verwendung der freigegebenen Bibliothek kann zu kleineren Anwendungen führen (eine minimale Anwendung, die den größten Teil der MFC-Bibliothek verwendet, ist weniger als 10K).

- Die freigegebene Version von MFC unterstützt MFC-Erweiterungs-DLLs und reguläre MFC-DLLs.

- Das Erstellen einer Anwendung, die die freigegebenen MFC-Bibliotheken verwendet, ist schneller als das Erstellen einer statisch verknüpften MFC-Anwendung, da mFC nicht selbst verknüpft werden muss. Dies gilt **DEBUG** insbesondere für DEBUG-Builds, bei denen der Linker die Debuginformationen komprimieren muss – durch Verknüpfen mit einer DLL, die bereits die Debuginformationen enthält, gibt es weniger Debuginformationen, die in der Anwendung komprimiert werden müssen.

Warum sollten Sie die freigegebene Version von MFC nicht verwenden:

- Für den Versand einer Anwendung, die die freigegebene Bibliothek verwendet, müssen Sie die MFCxx.DLL-Bibliothek (und andere) mit Ihrem Programm versenden. MFCxx.DLL ist wie viele DLLs frei verteilbar, aber Sie müssen die DLL weiterhin in Ihrem SETUP-Programm installieren. Darüber hinaus müssen Sie die MSVCRTxx.DLL versenden, die die C-Runtime-Bibliothek enthält, die sowohl von Ihrem Programm als auch von den MFC-DLLs selbst verwendet wird.

## <a name="how-to-write-an-mfc-extension-dll"></a><a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a>Schreiben einer MFC-Erweiterungs-DLL

Eine MFC-Erweiterungs-DLL ist eine DLL, die Klassen und Funktionen enthält, die geschrieben wurden, um die Funktionalität der MFC-Klassen zu verschönern. Eine MFC-Erweiterungs-DLL verwendet die gemeinsam genutzten MFC-DLLs auf die gleiche Weise, wie eine Anwendung sie verwendet, mit einigen zusätzlichen Überlegungen:

- Der Buildprozess ähnelt dem Erstellen einer Anwendung, die die freigegebenen MFC-Bibliotheken mit einigen zusätzlichen Compiler- und Linkeroptionen verwendet.

- Eine MFC-Erweiterungs-DLL `CWinApp`verfügt nicht über eine -derived-Klasse.

- Eine MFC-Erweiterungs-DLL `DllMain`muss eine spezielle bereitstellen. AppWizard stellt `DllMain` eine Funktion bereit, die Sie ändern können.

- Eine MFC-Erweiterungs-DLL stellt in der `CDynLinkLibrary` Regel eine Initialisierungsroutine `CRuntimeClass`zum Erstellen einer bereit, wenn die MFC-Erweiterungs-DLL es oder Ressourcen in die Anwendung exportieren möchte. Eine abgeleitete `CDynLinkLibrary` Klasse von kann verwendet werden, wenn Daten pro Anwendung von der MFC-Erweiterungs-DLL verwaltet werden müssen.

Diese Überlegungen werden im Folgenden ausführlicher beschrieben. Sie sollten auch auf das MFC Advanced Concepts-Beispiel [DLLHUSK](../overview/visual-cpp-samples.md) verweisen, da es Folgendes veranschaulicht:

- Erstellen einer Anwendung mithilfe der freigegebenen Bibliotheken. (DLLHUSK. EXE ist eine MFC-Anwendung, die dynamisch mit den MFC-Bibliotheken und anderen DLLs verknüpft ist.)

- Erstellen einer MFC-Erweiterungs-DLL. (Beachten Sie die `_AFXEXT` speziellen Flags, die beim Erstellen einer MFC-Erweiterungs-DLL verwendet werden)

- Zwei Beispiele für MFC-Erweiterungs-DLLs. Eine zeigt die grundlegende Struktur einer MFC-Erweiterungs-DLL mit begrenzten Exporten (TESTDLL1) und die andere zeigt den Export einer gesamten Klassenschnittstelle (TESTDLL2).

Sowohl die Clientanwendung als auch alle MFC-Erweiterungs-DLLs müssen dieselbe Version von MFCxx.DLL verwenden. Sie sollten die Konvention von MFC DLL befolgen und sowohl eine Debug- als auch eine Einzelhandelsversion (/Release) Ihrer MFC-Erweiterungs-DLL bereitstellen. Dadurch können Clientprogramme sowohl Debug- als auch Einzelhandelsversionen ihrer Anwendungen erstellen und sie mit der entsprechenden Debug- oder Einzelhandelsversion aller DLLs verknüpfen.

> [!NOTE]
> Da C++-Namensmangling- und -Exportprobleme auftreten, kann sich die Exportliste aus einer MFC-Erweiterungs-DLL zwischen der Debug- und der Einzelhandelsversion derselben DLL und DLLs für verschiedene Plattformen unterscheiden. Die Retail-MFCxx.DLL verfügt über ca. 2000 exportierte Einstiegspunkte; Das Debug-MFCxxD.DLL verfügt über etwa 3000 exportierte Einstiegspunkte.

### <a name="quick-note-on-memory-management"></a>Kurznotiz zur Speicherverwaltung

Der Abschnitt mit dem Titel "Memory Management" am Ende dieses technischen Hinweises beschreibt die Implementierung der MFCxx.DLL mit der freigegebenen Version von MFC. Die Informationen, die Sie wissen müssen, um nur eine MFC-Erweiterungs-DLL zu implementieren, werden hier beschrieben.

MFCxx.DLL und alle MFC-Erweiterungs-DLLs, die in den Adressraum einer Clientanwendung geladen werden, verwenden denselben Speicherallokator, das Laden von Ressourcen und andere MFC-"globale" Zustände, als ob sie sich in derselben Anwendung befänden. Dies ist wichtig, da die Nicht-MFC-DLL-Bibliotheken und regulären MFC-DLLs, die statisch mit MFC verknüpfen, genau das Gegenteil bewirken und jede DLL aus ihrem eigenen Speicherpool zuweisen.

Wenn eine MFC-Erweiterungs-DLL Speicher zuweist, kann sich dieser Speicher frei mit jedem anderen von der Anwendung zugewiesenen Objekt vermischen. Wenn eine Anwendung, die die freigegebenen MFC-Bibliotheken verwendet, abstürzt, behält der Schutz des Betriebssystems die Integrität jeder anderen MFC-Anwendung bei, die die DLL gemeinsam nutzt.

In ähnlicher Weise werden auch andere "globale" MFC-Zustände, wie die aktuelle ausführbare Datei zum Laden von Ressourcen, zwischen der Clientanwendung und allen MFC-Erweiterungs-DLLs sowie MFCxx.DLL selbst gemeinsam genutzt.

### <a name="building-an-mfc-extension-dll"></a>Erstellen einer MFC-Erweiterungs-DLL

Sie können AppWizard verwenden, um ein MFC-Erweiterungs-DLL-Projekt zu erstellen, und es werden automatisch die entsprechenden Compiler- und Linkereinstellungen generiert. Es wurde auch `DllMain` eine Funktion generiert, die Sie ändern können.

Wenn Sie ein vorhandenes Projekt in eine MFC-Erweiterungs-DLL konvertieren, beginnen Sie mit den Standardregeln zum Erstellen einer Anwendung mit der freigegebenen Version von MFC, und gehen Sie wie folgt vor:

- Fügen Sie **/D_AFXEXT** zu den Compilerflags hinzu. Wählen Sie im Dialogfeld Projekteigenschaften den Knoten C/C++aus. Wählen Sie dann die Kategorie Präprozessor aus. Fügen `_AFXEXT` Sie dem Feld Makros definieren hinzu und trennen Sie jedes Element durch Semikolons.

- Entfernen **/Gy** Sie den /Gy-Compiler-Schalter. Wählen Sie im Dialogfeld Projekteigenschaften den Knoten C/C++aus. Wählen Sie dann die Kategorie Codegenerierung aus. Stellen Sie sicher, dass die Option "Verknüpfen auf Funktionsebene aktivieren" nicht aktiviert ist. Dadurch wird das Exportieren von Klassen einfacher, da der Linker nicht referenzierte Funktionen nicht entfernt. Wenn das ursprüngliche Projekt zum Erstellen einer regulären MFC-DLL verwendet wird, die statisch mit MFC verknüpft ist, ändern Sie die Compileroption **/MT[d]** in **/MD[d]**.

- Erstellen Sie eine Exportbibliothek mit der Option **/DLL** in LINK. Diese wird festgelegt, wenn Sie ein neues Ziel erstellen und Win32 Dynamic-Link Library als Zieltyp angeben.

### <a name="changing-your-header-files"></a>Ändern Ihrer Headerdateien

Das Ziel einer MFC-Erweiterungs-DLL besteht in der Regel darin, einige allgemeine Funktionen in eine oder mehrere Anwendungen zu exportieren, die diese Funktionalität verwenden können. Dies läuft auf den Export von Klassen und globalen Funktionen hinaus, die für Ihre Clientanwendungen verfügbar sind.

Dazu müssen Sie sicherstellen, dass jede der Memberfunktionen als Import oder Export entsprechend gekennzeichnet ist. Dies erfordert besondere `__declspec(dllexport)` `__declspec(dllimport)`Erklärungen: und . Wenn Ihre Klassen von den Clientanwendungen verwendet werden, `__declspec(dllimport)`möchten Sie, dass sie als deklariert werden. Wenn die MFC-Erweiterungs-DLL selbst erstellt `__declspec(dllexport)`wird, sollten sie als deklariert werden. Darüber hinaus müssen die Funktionen tatsächlich exportiert werden, damit die Clientprogramme zum Zeitpunkt des Ladens an sie binden.

Um die gesamte Klasse `AFX_EXT_CLASS` zu exportieren, verwenden Sie die Klassendefinition. Dieses Makro wird vom `__declspec(dllexport)` Framework `_AFXDLL` `_AFXEXT` als wann definiert `__declspec(dllimport)` und `_AFXEXT` definiert, aber definiert als wann nicht definiert ist. `_AFXEXT`wie oben beschrieben, wird nur beim Erstellen ihrer MFC-Erweiterungs-DLL definiert. Beispiel:

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>Nicht exportieren der gesamten Klasse

Manchmal möchten Sie vielleicht nur die einzelnen erforderlichen Mitglieder Ihrer Klasse exportieren. Wenn Sie z. B. eine `CDialog`-derived-Klasse exportieren, müssen Sie `DoModal` möglicherweise nur den Konstruktor und den Aufruf exportieren. Sie können diese Elemente mit der DLL exportieren. DEF-Datei, aber Sie `AFX_EXT_CLASS` können auch in der gleichen Weise auf die einzelnen Elemente verwenden, die Sie exportieren müssen.

Beispiel:

```cpp
class CExampleDialog : public CDialog
{
public:
    AFX_EXT_CLASS CExampleDialog();
    AFX_EXT_CLASS int DoModal();
    // rest of class definition
    // ...
};
```

Wenn Sie dies tun, kann es zu einem zusätzlichen Problem kommen, da Sie nicht mehr alle Mitglieder der Klasse exportieren. Das Problem liegt in der Art und Weise, wie MFC-Makros funktionieren. Mehrere Hilfsmakros von MFC deklarieren oder definieren Tatsächlich Datenmember. Daher müssen diese Datenmember auch aus Ihrer DLL exportiert werden.

Beispielsweise wird das DECLARE_DYNAMIC Makro beim Erstellen einer MFC-Erweiterungs-DLL wie folgt definiert:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \
```

Die Zeile, die `AFX_DATA`mit "statisch" beginnt, deklariert ein statisches Objekt innerhalb Ihrer Klasse. Um diese Klasse korrekt zu exportieren und auf die Laufzeitinformationen von einem Client zuzugreifen. EXE müssen Sie dieses statische Objekt exportieren. Da das statische Objekt mit dem `AFX_DATA`Modifikator `AFX_DATA` deklariert `__declspec(dllexport)` wird, müssen Sie nur `__declspec(dllimport)` beim Erstellen der DLL definieren und es als beim Erstellen der ausführbaren Clientdatei definieren.

Wie oben `AFX_EXT_CLASS` beschrieben, ist bereits auf diese Weise definiert. Sie müssen nur neu `AFX_DATA` definieren, um `AFX_EXT_CLASS` die gleiche wie um Ihre Klassendefinition zu sein.

Beispiel:

```cpp
#undef  AFX_DATA
#define AFX_DATA AFX_EXT_CLASS
class CExampleView : public CView
{
    DECLARE_DYNAMIC()
    // ... class definition ...
};
#undef  AFX_DATA
#define AFX_DATA
```

MFC verwendet `AFX_DATA` immer das Symbol für Datenelemente, die es in seinen Makros definiert, sodass diese Technik für alle diese Szenarien funktioniert. Es funktioniert z. B. für DECLARE_MESSAGE_MAP.

> [!NOTE]
> Wenn Sie die gesamte Klasse und nicht die ausgewählten Member der Klasse exportieren, werden statische Datenmember automatisch exportiert.

Sie können dieselbe Technik verwenden, `CArchive` um den Extraktionsoperator automatisch für Klassen zu exportieren, die die DECLARE_SERIAL und IMPLEMENT_SERIAL-Makros verwenden. Exportieren Sie den Archivoperator, indem Sie die Klassendeklarationen in Klammern klammern (befindet sich im . H-Datei) mit folgendem Code:

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-_afxext"></a>Einschränkungen der _AFXEXT

Sie können das Symbol _**AFXEXT-Vorprozessorsymbol** für Ihre MFC-Erweiterungs-DLLs verwenden, solange Sie nicht über mehrere Layer von MFC-Erweiterungs-DLLs verfügen. Wenn Sie über MFC-Erweiterungs-DLLs verfügen, die Klassen in Ihren eigenen MFC-Erweiterungs-DLLs aufrufen oder ableiten, die dann von den MFC-Klassen ableiten, müssen Sie Ihr eigenes Präprozessorsymbol verwenden, um Mehrdeutigkeiten zu vermeiden.

Das Problem ist, dass Sie in Win32 `__declspec(dllexport)` alle Daten explizit so deklarieren `__declspec(dllimport)` müssen, als ob sie aus einer DLL exportiert werden sollen und ob sie aus einer DLL importiert werden sollen. Wenn Sie `_AFXEXT`definieren, stellen die MFC-Header sicher, dass sie `AFX_EXT_CLASS` richtig definiert sind.

Wenn Sie über mehrere Layer `AFX_EXT_CLASS` verfügen, reicht ein Symbol nicht aus, da eine MFC-Erweiterungs-DLL möglicherweise neue Klassen exportiert und andere Klassen aus einer anderen MFC-Erweiterungs-DLL importiert. Um dieses Problem zu beheben, verwenden Sie ein spezielles Präprozessorsymbol, das angibt, dass Sie die DLL selbst im Vergleich zur Verwendung der DLL erstellen. Stellen Sie sich beispielsweise zwei MFC-Erweiterungs-DLLs, A.DLL und B.DLL vor. Sie exportieren jeweils einige Klassen in A.H bzw. B.H. B.DLL verwendet die Klassen aus A.DLL. Die Header-Dateien würden etwa wie folgt aussehen:

```cpp
/* A.H */
#ifdef A_IMPL
    #define CLASS_DECL_A   __declspec(dllexport)
#else
    #define CLASS_DECL_A   __declspec(dllimport)
#endif

class CLASS_DECL_A CExampleA : public CObject
{ /* ... class definition ... */ };

/* B.H */
#ifdef B_IMPL
    #define CLASS_DECL_B   __declspec(dllexport)
#else
    #define CLASS_DECL_B   __declspec(dllimport)
#endif

class CLASS_DECL_B CExampleB : public CExampleA
{ /* ... class definition ... */ };
```

Wenn A.DLL erstellt wird, wird es mit **/DA_IMPL** und wenn B.DLL erstellt wird, wird es mit **/DB_IMPL**erstellt. Durch die Verwendung separater Symbole für jede DLL wird CExampleB exportiert und CExampleA beim Erstellen von B.DLL importiert. CExampleA wird beim Erstellen von A.DLL exportiert und importiert, wenn es von B.DLL (oder einem anderen Client) verwendet wird.

Diese Art der Schichtung kann nicht durchgeführt `AFX_EXT_CLASS` `_AFXEXT` werden, wenn die integrierten und Präprozessorsymbole verwendet werden. Die oben beschriebene Technik löst dieses Problem in einer Weise, die dem Mechanismus nicht unähnlich ist, den MFC selbst beim Erstellen seiner OLE-, Datenbank- und Netzwerk-MFC-Erweiterungs-DLLs verwendet.

### <a name="not-exporting-the-entire-class"></a>Nicht exportieren der gesamten Klasse

Auch hier müssen Sie besonders vorsichtig sein, wenn Sie nicht eine ganze Klasse exportieren. Sie müssen sicherstellen, dass die erforderlichen Datenelemente, die von den MFC-Makros erstellt wurden, korrekt exportiert werden. Dies kann durch Neudefinition `AFX_DATA` des Makros Ihrer spezifischen Klasse erfolgen. Dies sollte jederzeit erfolgen, wenn Sie nicht die gesamte Klasse exportieren.

Beispiel:

```cpp
// A.H
#ifdef A_IMPL
    #define CLASS_DECL_A  _declspec(dllexport)
#else
    #define CLASS_DECL_A  _declspec(dllimport)
#endif

#undef  AFX_DATA
#define AFX_DATA CLASS_DECL_A

class CExampleA : public CObject
{
    DECLARE_DYNAMIC()
    CLASS_DECL_A int SomeFunction();
    // class definition
    // ...
};

#undef AFX_DATA
#define AFX_DATA
```

### <a name="dllmain"></a>DllMain

Im Folgenden finden Sie den genauen Code, den Sie in der Hauptquelldatei für Ihre MFC-Erweiterungs-DLL platzieren sollten. Es sollte nach dem Standard gehören kommen. Beachten Sie, dass, wenn Sie AppWizard verwenden, um Startdateien `DllMain` für eine MFC-Erweiterungs-DLL zu erstellen, diese eine für Sie bereitstellt.

```cpp
#include "afxdllx.h"

static AFX_EXTENSION_MODULE extensionDLL;

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID)
{
   if (dwReason == DLL_PROCESS_ATTACH)
   {
      // MFC extension DLL one-time initialization
      if (!AfxInitExtensionModule(
             extensionDLL, hInstance))
         return 0;

      // TODO: perform other initialization tasks here
   }
   else if (dwReason == DLL_PROCESS_DETACH)
   {
      // MFC extension DLL per-process termination
      AfxTermExtensionModule(extensionDLL);

      // TODO: perform other cleanup tasks here
   }
   return 1;   // ok
}
```

Der Aufruf `AfxInitExtensionModule` zum Erfassen der Module-Laufzeitklassen (Strukturen)`CRuntimeClass` sowie seiner`COleObjectFactory` Objektfabriken (Objekte) `CDynLinkLibrary` zur späteren Verwendung, wenn das Objekt erstellt wird. Der (optionale) `AfxTermExtensionModule` Aufruf von ermöglicht MFC, die MFC-Erweiterungs-DLL zu bereinigen, wenn sich jeder Prozess von der `FreeLibrary` MFC-Erweiterungs-DLL löst (was beim Beenden des Prozesses oder beim Entladen der DLL als Ergebnis eines Aufrufs geschieht). Da die meisten MFC-Erweiterungs-DLLs nicht dynamisch geladen werden (in `AfxTermExtensionModule` der Regel sind sie über ihre Importbibliotheken verknüpft), ist der Aufruf von in der Regel nicht erforderlich.

Wenn Ihre Anwendung MFC-Erweiterungs-DLLs dynamisch lädt `AfxTermExtensionModule` und freigibt, rufen Sie wie oben gezeigt auf. Achten Sie auch `AfxLoadLibrary` `AfxFreeLibrary` darauf, und (anstelle `LoadLibrary` `FreeLibrary`von Win32-Funktionen und ) zu verwenden, wenn Ihre Anwendung mehrere Threads verwendet oder wenn sie dynamisch eine MFC-Erweiterungs-DLL lädt. Durch `AfxLoadLibrary` `AfxFreeLibrary` die Verwendung und Die Versicherung wird sichergestellt, dass der Start- und Herunterfahrcode, der ausgeführt wird, wenn die MFC-Erweiterungs-DLL geladen und entladen wird, den globalen MFC-Status nicht beschädigt.

Die Headerdatei AFXDLLX. H enthält spezielle Definitionen für Strukturen, die in MFC-Erweiterungs-DLLs verwendet werden, z. B. die Definition für `AFX_EXTENSION_MODULE` und `CDynLinkLibrary`.

Die globale *ExtensionDLL* muss wie gezeigt deklariert werden. Im Gegensatz zur 16-Bit-Version von MFC können Sie während dieser Zeit Speicher zuweisen und MFC-Funktionen aufrufen, da die MFCxx.DLL zum Zeitpunkt `DllMain` des Aufrufs vollständig initialisiert wird.

### <a name="sharing-resources-and-classes"></a>Gemeinsame Nutzung von Ressourcen und Klassen

Einfache MFC-Erweiterungs-DLLs müssen nur ein paar Funktionen mit geringer Bandbreite in die Clientanwendung exportieren und nichts mehr. Mehr benutzeroberflächenintensive DLLs möchten möglicherweise Ressourcen und C++-Klassen in die Clientanwendung exportieren.

Der Export von Ressourcen erfolgt über eine Ressourcenliste. In jeder Anwendung befindet sich eine `CDynLinkLibrary` separat verknüpfte Liste von Objekten. Bei der Suche nach einer Ressource sehen die meisten Standard-MFC-Implementierungen, die Ressourcen laden, zuerst das aktuelle Ressourcenmodul (`AfxGetResourceHandle`) und wenn nicht gefunden, die Liste der `CDynLinkLibrary` Objekte, die versuchen, die angeforderte Ressource zu laden.

Die dynamische Erstellung von C++-Objekten mit einem C++-Klassennamen ist ähnlich. Der MFC-Objektdeserialisierungsmechanismus muss `CRuntimeClass` alle Objekte registrieren, damit er rekonstruieren kann, indem es das C++-Objekt des erforderlichen Typs dynamisch basierend auf dem zuvor gespeicherten Erstellen erstellt.

Wenn die Clientanwendung Klassen in Ihrer MFC-Erweiterungs-DLL verwenden soll, die es sind, `DECLARE_SERIAL`müssen Sie Ihre Klassen exportieren, um für die Clientanwendung sichtbar zu sein. Dies geschieht auch, `CDynLinkLibrary` indem Manier in der Liste.

Im Fall des MFC Advanced Concepts-Beispiels [DLLHUSK](../overview/visual-cpp-samples.md)sieht die Liste etwa wie folgt aus:

```Example
head ->   DLLHUSK.EXE   - or - DLLHUSK.EXE
               |                    |
          TESTDLL2.DLL         TESTDLL2.DLL
               |                    |
          TESTDLL1.DLL         TESTDLL1.DLL
               |                    |
               |                    |
           MFC90D.DLL           MFC90.DLL
```

Die MFCxx.DLL ist in der Regel die letzte in der Ressourcen- und Klassenliste. MFCxx.DLL enthält alle Standard-MFC-Ressourcen, einschließlich Eingabeaufforderungszeichenfolgen für alle Standardbefehls-IDs. Wenn Sie es am Ende der Liste platzieren, können DLLs und die Clientanwendung selbst nicht über eine eigene Kopie der Standard-MFC-Ressourcen verfügen, sondern sich stattdessen auf die freigegebenen Ressourcen in der MFCxx.DLL verlassen.

Das Zusammenführen der Ressourcen und Klassennamen aller DLLs im Namensbereich der Clientanwendung hat den Nachteil, dass Sie darauf achten müssen, welche IDs oder Namen Sie auswählen. Sie können diese Funktion natürlich deaktivieren, indem `CDynLinkLibrary` Sie weder Ihre Ressourcen noch ein Objekt in die Clientanwendung exportieren. Das [DLLHUSK-Beispiel](../overview/visual-cpp-samples.md) verwaltet den freigegebenen Ressourcennamenbereich mithilfe mehrerer Headerdateien. Weitere Tipps zur Verwendung freigegebener Ressourcendateien finden Sie unter [Technisches Anmerkungs- 35.000](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md) .

### <a name="initializing-the-dll"></a>Initialisieren der DLL

Wie oben erwähnt, möchten Sie `CDynLinkLibrary` in der Regel ein Objekt erstellen, um Ihre Ressourcen und Klassen in die Clientanwendung zu exportieren. Sie müssen einen exportierten Einstiegspunkt angeben, um die DLL zu initialisieren. Minimal ist dies eine leere Routine, die keine Argumente nimmt und nichts zurückgibt, aber es kann alles sein, was Sie mögen.

Jede Clientanwendung, die Ihre DLL verwenden möchte, muss diese Initialisierungsroutine aufrufen, wenn Sie diesen Ansatz verwenden. Sie können dieses `CDynLinkLibrary` Objekt `DllMain` auch in `AfxInitExtensionModule`Ihrem Objekt direkt nach dem Aufruf zuweisen.

Die Initialisierungsroutine `CDynLinkLibrary` muss ein Objekt im Heap der aktuellen Anwendung erstellen, das mit Ihren MFC-Erweiterungs-DLL-Informationen verknüpft ist. Dies kann mit den folgenden Erfolgen erfolgen:

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

Der Routinename *InitXxxDLL* in diesem Beispiel kann alles sein, was Sie möchten. Es muss nicht **extern "C"** sein, aber dies erleichtert die Verwaltung der Exportliste.

> [!NOTE]
> Wenn Sie Ihre MFC-Erweiterungs-DLL aus einer regulären MFC-DLL verwenden, müssen Sie diese Initialisierungsfunktion exportieren. Diese Funktion muss von der regulären MFC-DLL aufgerufen werden, bevor MFC-Erweiterungs-DLL-Klassen oder -Ressourcen verwendet werden.

### <a name="exporting-entries"></a>Exportieren von Einträgen

Die einfache Möglichkeit, Ihre Klassen `__declspec(dllimport)` `__declspec(dllexport)` zu exportieren, ist die Verwendung und für jede Klasse und globale Funktion, die Sie exportieren möchten. Dies macht es viel einfacher, ist aber weniger effizient als die Benennung jedes Einstiegspunkts (siehe unten), da Sie weniger Kontrolle darüber haben, welche Funktionen exportiert werden, und Sie die Funktionen nicht nach Ordnung exportieren können. TESTDLL1 und TESTDLL2 verwenden diese Methode, um ihre Einträge zu exportieren.

Eine effizientere Methode (und die von MFCxx.DLL verwendete Methode) besteht darin, jeden Eintrag von Hand zu exportieren, indem jeder Eintrag im benannt wird. DEF-Datei. Da wir selektive Exporte aus unserer DLL exportieren (d. h. nicht alles), müssen wir entscheiden, welche speziellen Schnittstellen wir exportieren möchten. Dies ist schwierig, da Sie die verstauchten Namen für den Linker in Form von Einträgen im angeben müssen. DEF-Datei. Exportieren Sie keine C++-Klassen, es sei denn, Sie benötigen wirklich einen symbolischen Link dafür.

Wenn Sie versucht haben, C++-Klassen mit einer zu exportieren. DEF-Datei vor, können Sie ein Tool entwickeln, um diese Liste automatisch zu generieren. Dies kann mit einem zweistufigen Linkprozess erfolgen. Verknüpfen Sie Ihre DLL einmal ohne Exporte, und erlauben Sie dem Linker, eine zu generieren. MAP-Datei. das. MAP-Datei kann verwendet werden, um eine Liste von Funktionen zu generieren, die exportiert werden sollen, so dass mit einigen Neuanordnungen, kann es verwendet werden, um Ihre EXPORT-Einträge für Ihre zu generieren. DEF-Datei. Die Exportliste für MFCxx.DLL und die OLE- und Datenbank-MFC-Erweiterungs-DLLs, mehrere tausend an der Zahl, wurde mit einem solchen Prozess generiert (obwohl es nicht vollständig automatisch ist und ab und zu einige Handabstimmungen erfordert).

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp vs. CDynLinkLibrary

Eine MFC-Erweiterungs-DLL `CWinApp`verfügt nicht über ein eigenes -derived-Objekt. Stattdessen muss es `CWinApp`mit dem -derived-Objekt der Clientanwendung arbeiten. Dies bedeutet, dass die Clientanwendung die Hauptnachrichtenpumpe, die Leerlaufschleife usw. besitzt.

Wenn Ihre MFC-Erweiterungs-DLL zusätzliche Daten für jede Anwendung verwalten `CDynLinkLibrary` muss, können Sie eine neue Klasse ableiten und in der oben beschriebenen InitXxxDLL-Routine erstellen. Bei der Ausführung kann die DLL die `CDynLinkLibrary` Objektliste der aktuellen Anwendung überprüfen, um diejenige für diese spezielle MFC-Erweiterungs-DLL zu finden.

### <a name="using-resources-in-your-dll-implementation"></a>Verwenden von Ressourcen in Ihrer DLL-Implementierung

Wie oben erwähnt, wird die Standardressourcenlast in der Liste der `CDynLinkLibrary` Objekte ausgeführt, die nach der ersten EXE oder DLL suchen, die über die angeforderte Ressource verfügt. Alle MFC-APIs sowie alle internen `AfxFindResourceHandle` Codeverwendet, um die Ressourcenliste zu führen, um eine Ressource zu finden, unabhängig davon, wo sie sich befinden kann.

Wenn Sie nur Ressourcen von einem bestimmten Ort `AfxGetResourceHandle` laden `AfxSetResourceHandle` möchten, verwenden Sie die APIs, und speichern Sie das alte Handle, und legen Sie das neue Handle fest. Achten Sie darauf, dass Sie das alte Ressourcenhandle wiederherstellen, bevor Sie zur Clientanwendung zurückkehren. Das Beispiel TESTDLL2 verwendet diesen Ansatz zum expliziten Laden eines Menüs.

Das Durchlaufen der Liste hat jedoch den Nachteil, dass die Suche etwas langsamer ist und dass die Ressourcen-ID-Bereiche verwaltet werden müssen. Es hat den Vorteil, dass eine Clientanwendung, die mit mehreren MFC-Erweiterungs-DLLs verknüpft ist, jede von DLL bereitgestellte Ressource verwenden kann, ohne das DLL-Instanzhandle angeben zu müssen. `AfxFindResourceHandle` ist eine API, die bei der Suche nach einer bestimmten Übereinstimmung die Ressourcenliste durchläuft. Sie verwendet den Ressourcennamen und -typ als Parameter und gibt das zuerst ermittelte Ressourcenhandle (oder NULL) zurück.

## <a name="writing-an-application-that-uses-the-dll-version"></a><a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a>Schreiben einer Anwendung, die die DLL-Version verwendet

### <a name="application-requirements"></a>Anwendungsanforderungen

Eine Anwendung, die die freigegebene Version von MFC verwendet, muss ein paar einfache Regeln befolgen:

- Es muss `CWinApp` über ein Objekt verfügen und die Standardregeln für eine Nachrichtenpumpe befolgen.

- Sie muss mit einer Reihe von erforderlichen Compilerflags kompiliert werden (siehe unten).

- Sie muss mit den MFCxx-Importbibliotheken verknüpft werden. Durch Festlegen der erforderlichen Compilerflags bestimmen die MFC-Header zur Linkzeit, mit welcher Bibliothek die Anwendung eine Verknüpfung herstellen soll.

- Um die ausführbare Datei auszuführen, muss sich MFCxx.DLL im Pfad oder im Windows-Systemverzeichnis befinden.

### <a name="building-with-the-development-environment"></a>Bauen mit der Entwicklungsumgebung

Wenn Sie die interne Makefile mit den meisten Standardeinstellungen verwenden, können Sie das Projekt einfach ändern, um die DLL-Version zu erstellen.

Im folgenden Schritt wird davon ausgegangen, dass Sie über eine ordnungsgemäß funktionierende MFC-Anwendung verfügen, die mit NAFXCWD verknüpft ist. LIB (für Debug-) und NAFXCW. LIB (für den Einzelhandel) und Sie möchten es konvertieren, um die freigegebene Version der MFC-Bibliothek zu verwenden. Sie führen die Visual C++-Umgebung aus und verfügen über eine interne Projektdatei.

1. Klicken Sie im Menü **Projekte** auf **Eigenschaften**. Legen Sie auf der Seite **Allgemein** unter **Projektstandards**Microsoft Foundation-Klassen fest, **mFC in einer freigegebenen DLL** (MFCxx(d).dll) zu verwenden.

### <a name="building-with-nmake"></a>Bauen mit NMAKE

Wenn Sie die externe Makefile-Funktion von Visual C++ verwenden oder NMAKE direkt verwenden, müssen Sie Ihr Makefile bearbeiten, um Compiler- und Linkeroptionen zu unterstützen.

Erforderliche Compilerflags:

- **/D_AFXDLL /MD**
   **/D_AFXDLL**

Für die Standard-MFC-Header muss dieses Symbol definiert werden:

- **/MD** Die Anwendung muss die DLL-Version der C-Laufzeitbibliothek verwenden.

Alle anderen Compilerflags folgen den MFC-Standards (z. B. _DEBUG für das Debuggen).

Bearbeiten Sie die Linkerliste der Bibliotheken. Ändern Sie NAFXCWD. LIB in MFCxxD.LIB und ändern NAFXCW. LIB zu MFCxx.LIB. Ersetzen Sie LIBC. LIB mit MSVCRT. Lib. Wie bei jeder anderen MFC-Bibliothek ist es wichtig, dass MFCxxD.LIB **vor** c-runtime Bibliotheken platziert wird.

Fügen Sie optional **/D_AFXDLL** zu Ihren Einzelhandels- und Debugressourcen-Compileroptionen hinzu (diejenige, die die Ressourcen tatsächlich mit **/R**kompiliert). Dadurch wird die endgültige ausführbare Datei durch die gemeinsame Nutzung der Ressourcen, die in den MFC-DLLs vorhanden sind, verkleinert.

Nach diesen Änderungen ist eine vollständige Neuerstellung erforderlich.

### <a name="building-the-samples"></a>Erstellen der Beispiele

Die meisten MFC-Beispielprogramme können aus Visual C++ oder aus einer gemeinsam genutzten NMAKE-kompatiblen MAKEFILE über die Befehlszeile erstellt werden.

Um eines dieser Beispiele in MFCxx.DLL zu konvertieren, können Sie die laden. MAK-Datei in Visual C++ und legen Sie die Projektoptionen wie oben beschrieben fest. Wenn Sie den NMAKE-Build verwenden, können Sie "AFXDLL=1" in der NMAKE-Befehlszeile angeben, das das Beispiel mithilfe der freigegebenen MFC-Bibliotheken erstellt.

Das MFC Advanced Concepts-Beispiel [DLLHUSK](../overview/visual-cpp-samples.md) wird mit der DLL-Version von MFC erstellt. In diesem Beispiel wird nicht nur veranschaulicht, wie eine Anwendung erstellt wird, die mit MFCxx.DLL verknüpft ist, sondern auch andere Features der MFC-DLL-Verpackungsoption, z. B. MFC Extension DLLs, die weiter unten in diesem technischen Hinweis beschrieben werden.

### <a name="packaging-notes"></a>Verpackungshinweise

Die Einzelhandelsversion der DLLs (MFCxx[U]. DLL) sind frei verteilbar. Die Debugversion der DLLs ist nicht frei verteilbar und sollte nur während der Entwicklung Ihrer Anwendung verwendet werden.

Die Debug-DLLs werden mit Debuginformationen bereitgestellt. Mithilfe des Visual C++-Debuggers können Sie die Ausführung Ihrer Anwendung sowie der DLL nachverfolgen. Die Release-DLLs (MFCxx[U]. DLL) keine Debuginformationen enthalten.

Wenn Sie die DLLs anpassen oder neu erstellen, sollten Sie sie etwas anderes als "MFCxx" die MFC SRC-Datei MFCDLL nennen. MAK beschreibt Buildoptionen und enthält die Logik zum Umbenennen der DLL. Das Umbenennen der Dateien ist erforderlich, da diese DLLs möglicherweise von vielen MFC-Anwendungen gemeinsam genutzt werden. Wenn Ihre benutzerdefinierte Version der MFC-DLLs die auf dem System installierten ersetzen, kann eine andere MFC-Anwendung mithilfe der freigegebenen MFC-DLLs aufbrechen.

Das Neuaufbau der MFC-DLLs wird nicht empfohlen.

## <a name="how-the-mfcxxdll-is-implemented"></a><a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a>Implementierung der MFCxx.DLL

Im folgenden Abschnitt wird beschrieben, wie die MFC-DLL (MFCxx.DLL und MFCxxD.DLL) implementiert wird. Das Verständnis der Details hier ist auch nicht wichtig, wenn Sie nur die MFC-DLL mit Ihrer Anwendung verwenden möchten. Die Details hier sind nicht wichtig, um zu verstehen, wie eine MFC-Erweiterungs-DLL geschrieben wird, aber das Verständnis dieser Implementierung kann Ihnen helfen, Ihre eigene DLL zu schreiben.

### <a name="implementation-overview"></a>Übersicht über die Implementierung

Die MFC-DLL ist wirklich ein Sonderfall einer MFC Extension DLL, wie oben beschrieben. Es hat eine sehr große Anzahl von Exporten für eine große Anzahl von Klassen. Es gibt ein paar zusätzliche Dinge, die wir in der MFC-DLL tun, die es noch spezieller als eine normale MFC-Erweiterungs-DLL machen.

### <a name="win32-does-most-of-the-work"></a>Win32 macht den größten Teil der Arbeit

Die 16-Bit-Version von MFC benötigte eine Reihe spezieller Techniken, einschließlich Pro-App-Daten im Stapelsegment, spezielle Segmente, die durch etwa 80x86-Assemblycode erstellt wurden, Pro-Prozess-Ausnahmekontexte und andere Techniken. Win32 unterstützt direkt Prozessdaten in einer DLL, was Sie die meiste Zeit wünschen. MFCxx.DLL ist größtenteils nur NAFXCW. LIB in einer DLL verpackt. Wenn Sie sich den MFC-Quellcode ansehen, finden Sie nur sehr wenige #ifdef _AFXDLL, da es nur sehr wenige Sonderfälle gibt, die gemacht werden müssen. Die besonderen Fälle, die es gibt, sind speziell für Win32 unter Windows 3.1 (auch bekannt als Win32s). Win32s unterstützt keine Pro-Prozess-DLL-Daten direkt, daher muss die MFC-DLL die TLS-APIs (Thread-Local Storage) verwenden, um lokale Prozessdaten zu erhalten.

### <a name="impact-on-library-sources-additional-files"></a>Auswirkungen auf Bibliotheksquellen, zusätzliche Dateien

Die Auswirkungen der **_AFXDLL** Version auf die normalen MFC-Klassenbibliotheksquellen und -header sind relativ gering. Es gibt eine spezielle Versionsdatei (AFXV_DLL. H) sowie eine zusätzliche Headerdatei (AFXDLL_. H) vom Haupt-AFXWIN enthalten. H-Header. Die AFXDLL_. Der H-Header enthält die `CDynLinkLibrary` Klasse `_AFXDLL` und andere Implementierungsdetails sowohl von Anwendungen als auch von MFC Extension DLLs. Die AFXDLLX. H-Header werden zum Erstellen von MFC Extension DLLs bereitgestellt (Details siehe oben).

Die regulären Quellen für die MFC-Bibliothek in MFC SRC verfügen über zusätzlichen bedingten Code unter der `_AFXDLL` #ifdef. Eine zusätzliche Quelldatei (DLLINIT. CPP) enthält den zusätzlichen DLL-Initialisierungscode und anderen Klebstoff für die freigegebene Version von MFC.

Um die freigegebene Version von MFC zu erstellen, werden zusätzliche Dateien bereitgestellt. (Weitere Informationen zum Erstellen der DLL finden Sie weiter unten.)

- Zwei. DEF-Dateien werden zum Exportieren der MFC-DLL-Einstiegspunkte für Debugversionen (MFCxxD.DEF) und Releaseversionen (MFCxx.DEF) der DLL verwendet.

- Eine. RC-Datei (MFCDLL. RC) enthält alle Standard-MFC-Ressourcen und eine VERSIONINFO-Ressource für die DLL.

- Eine. CLW-Datei (MFCDLL. CLW) wird bereitgestellt, um das Durchsuchen der MFC-Klassen mit ClassWizard zu ermöglichen. Hinweis: Diese Funktion ist nicht speziell für die DLL-Version von MFC.

### <a name="memory-management"></a>Arbeitsspeicherverwaltung

Eine Anwendung, die MFCxx.DLL verwendet, verwendet einen allgemeinen Speicherzuweisungsdienst, der von MSVCRTxx.DLL, der gemeinsam genutzten C-Runtime-DLL, bereitgestellt wird. Die Anwendung, alle MFC-Erweiterungs-DLLs und die MFC-DLLs selbst verwenden diesen freigegebenen Speicherzuweisungsdienst. Durch die Verwendung einer freigegebenen DLL für die Speicherzuweisung können die MFC-DLLs Speicher zuweisen, der später von der Anwendung freigegeben wird oder umgekehrt. Da sowohl die Anwendung als auch die DLL denselben Allocator verwenden müssen, sollten Sie den globalen C++-Operator **new** oder **operator delete**nicht überschreiben. Die gleichen Regeln gelten für die restlichen C-Laufzeitspeicherzuweisungsroutinen (z. B. **malloc**, **realloc**, **free**und andere).

### <a name="ordinals-and-class-__declspecdllexport-and-dll-naming"></a>Ordinale und Klassen__declspec(dllexport) und DLL-Namen

Wir verwenden nicht `class` die **__declspec(dllexport)** Funktionalität des C++-Compilers. Stattdessen wird eine Liste der Exporte in den Klassenbibliotheksquellen (MFCxx.DEF und MFCxxD.DEF) enthalten. Nur diese ausgewählten Einstiegspunkte (Funktionen und Daten) werden exportiert. Andere Symbole, z. B. private MFC-Implementierungsfunktionen oder -Klassen, werden nicht exportiert Alle Exporte werden durch Ordnungszeichen ohne Zeichenfolgennamen in der Tabelle "Resident" oder "nicht gebietsansässiger Name" ausgeführt.

Die `class` Verwendung **von __declspec(dllexport)** kann eine praktikable Alternative zum Erstellen kleinerer DLLs sein, aber im Fall einer großen DLL wie MFC hat der Standardexportmechanismus Effizienz- und Kapazitätsgrenzen.

Das alles bedeutet, dass wir eine große Menge an Funktionalität in der Version MFCxx.DLL verpacken können, die nur etwa 800 KB beträgt, ohne viel Ausführung sende oder Ladegeschwindigkeit zu beeinträchtigen. MFCxx.DLL wäre 100K größer gewesen, wenn diese Technik nicht verwendet worden wäre. Dadurch ist es auch möglich, zusätzliche Einstiegspunkte am Ende des hinzuzufügen. DEF-Datei, um eine einfache Versionierung zu ermöglichen, ohne die Geschwindigkeit und Größeneffizienz des Exports durch Ordinal zu beeinträchtigen. Wichtige Versionsrevisionen in der MFC-Klassenbibliothek ändern den Bibliotheksnamen. Das heißt, MFC30. DLL ist die verteilbare DLL, die Version 3.0 der MFC-Klassenbibliothek enthält. Ein Upgrade dieser DLL, z. B. in einem hypothetischen MFC 3.1, würde die DLL MFC31 heißen. DLL stattdessen. Wenn Sie den MFC-Quellcode ändern, um eine benutzerdefinierte Version der MFC-DLL zu erstellen, verwenden Sie einen anderen Namen (und vorzugsweise einen namenlos ohne "MFC" im Namen).

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
