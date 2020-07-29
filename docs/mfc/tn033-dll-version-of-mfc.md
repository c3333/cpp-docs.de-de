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
ms.openlocfilehash: c627f891efc893f4eb8dae4bfb0b3b78f7af1a46
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215932"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033: DLL-Version der MFC

In diesem Hinweis wird beschrieben, wie Sie die MFCxx.DLL und MFCxxD.DLL (wobei x die MFC-Versionsnummer ist) freigegebene Dynamic Link Libraries mit MFC-Anwendungen und MFC-Erweiterungs-DLLs verwenden können. Weitere Informationen zu regulären MFC-DLLs finden [Sie unter Verwenden von MFC als Teil einer DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

Dieser Technische Hinweis umfasst drei Aspekte von DLLs. Die letzten zwei sind für erweiterte Benutzer:

- [So erstellen Sie eine MFC-Erweiterungs-DLL](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [So erstellen Sie eine MFC-Anwendung, die die dll-Version von MFC verwendet](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [Implementierung der gemeinsam genutzten MFC-Dynamic-Link-Bibliotheken](#_mfcnotes_how_the_mfc30.dll_is_implemented)

Wenn Sie eine DLL mit MFC entwickeln möchten, die mit nicht-MFC-Anwendungen verwendet werden kann (Dies wird als reguläre MFC-DLL bezeichnet), lesen Sie [Technische Notiz 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>Übersicht über MFCxx.DLL-Unterstützung: Terminologie und Dateien

**Reguläre MFC-DLL**: Sie verwenden eine reguläre MFC-DLL, um mithilfe einiger MFC-Klassen eine eigenständige dll zu erstellen. Schnittstellen über die App/DLL-Grenze hinweg sind C-Schnittstellen, und die Client Anwendung muss keine MFC-Anwendung sein.

Dies ist die Version der DLL-Unterstützung, die in MFC 1,0 unterstützt wird. Dies wird in [Technical Note 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md) und im MFC Advanced Concepts Sample [DLLScreenCap](../overview/visual-cpp-samples.md)beschrieben.

> [!NOTE]
> Ab Visual C++ Version 4,0 ist der Begriff " **rdll** " veraltet und wurde durch eine reguläre MFC-DLL ersetzt, die statisch mit MFC verknüpft ist. Sie können auch eine reguläre MFC-DLL erstellen, die dynamisch mit MFC verknüpft ist.

MFC 3,0 (und höher) unterstützt reguläre MFC-DLLs mit allen neuen Funktionen, einschließlich der OLE-und Datenbankklassen.

**AFXDLL**: Dies wird auch als freigegebene Version der MFC-Bibliotheken bezeichnet. Dies ist die neue DLL-Unterstützung, die in MFC 2,0 hinzugefügt wurde. Die MFC-Bibliothek selbst ist in einer Reihe von DLLs (unten beschrieben), und eine Client Anwendung oder DLL verknüpft dynamisch die erforderlichen DLLs. Schnittstellen über die Anwendungs-/DLL-Grenze hinweg sind C++/MFC-Klassen Schnittstellen. Bei der Client Anwendung muss es sich um eine MFC-Anwendung handeln. Dies unterstützt alle MFC 3,0-Funktionen (Ausnahme: Unicode wird für die Datenbankklassen nicht unterstützt).

> [!NOTE]
> Ab Visual C++ Version 4,0 wird dieser DLL-Typ als "Erweiterungs-DLL" bezeichnet.

In diesem Hinweis wird MFCxx.DLL verwendet, um auf den gesamten MFC-DLL-Satz zu verweisen, der Folgendes umfasst:

- Debug: MFCxxD.DLL (kombiniert) und MF csxxd. lib (statisch).

- Release: MFCxx.DLL (kombiniert) und MF csxx. lib (statisch).

- Unicode-Debuggen: MFCxxUD.DLL (kombiniert) und MF csxxd. lib (statisch).

- Unicode-Release: MFCxxU.DLL (kombiniert) und MF csxxu. lib (statisch).

> [!NOTE]
> MF csxx [U] [D]. LIB-Bibliotheken werden in Verbindung mit den freigegebenen MFC-DLLs verwendet. Diese Bibliotheken enthalten Code, der statisch mit der Anwendung oder DLL verknüpft werden muss.

Eine Anwendung wird mit den entsprechenden Import Bibliotheken verknüpft:

- Debuggen: MFCxxD. lib

- Release: MFCxx. lib

- Unicode-Debuggen: mfcxxud. lib

- Unicode-Release: mfcxxu. lib

Eine "MFC-Erweiterungs-DLL" ist eine DLL, die auf MFCxx.DLL (und/oder den anderen gemeinsam genutzten MFC-DLLs) basiert. Hier kommt die MFC-Komponentenarchitektur vor. Wenn Sie eine nützliche Klasse von einer MFC-Klasse ableiten oder ein weiteres MFC-ähnliches Toolkit erstellen, können Sie es in einer DLL platzieren. Diese DLL verwendet MFCxx.DLL, ebenso wie die ultimative Client Anwendung. Dies ermöglicht wiederverwendbare Blatt Klassen, wiederverwendbare Basisklassen und wiederverwendbare Sicht-/Dokument-Klassen.

## <a name="pros-and-cons"></a>Vor-und Nachteile

Warum sollten Sie die freigegebene Version von MFC verwenden?

- Die Verwendung der freigegebenen Bibliothek kann zu kleineren Anwendungen führen (eine minimale Anwendung, die den größten Teil der MFC-Bibliothek verwendet, ist kleiner als 10K).

- Die freigegebene Version von MFC unterstützt MFC-Erweiterungs-DLLs und reguläre MFC-DLLs.

- Das Entwickeln einer Anwendung, die gemeinsam genutzte MFC-Bibliotheken verwendet, ist schneller als das Aufbauen einer statisch verknüpften MFC-Anwendung, da es nicht erforderlich ist, MFC selbst zu verknüpfen. Dies gilt insbesondere für **Debug** -Builds, bei denen der Linker die Debuginformationen komprimieren muss – durch das Verknüpfen mit einer DLL, die bereits die Debuginformationen enthält, gibt es weniger Debuginformationen, die in Ihrer Anwendung komprimiert werden können.

Warum sollten Sie die freigegebene Version von MFC nicht verwenden:

- Das Versenden einer Anwendung, die die freigegebene Bibliothek verwendet, erfordert, dass Sie die MFCxx.DLL Bibliothek (und andere) an Ihr Programm senden. MFCxx.DLL ist wie viele DLLs frei Verteil Bar, aber Sie müssen die dll weiterhin in Ihrem Setup Programm installieren. Außerdem müssen Sie die MSVCRTxx.DLL mit der C-Lauf Zeit Bibliothek liefern, die sowohl von Ihrem Programm als auch von den MFC-DLLs selbst verwendet wird.

## <a name="how-to-write-an-mfc-extension-dll"></a><a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a>Schreiben einer MFC-Erweiterungs-DLL

Eine MFC-Erweiterungs-DLL ist eine DLL, die Klassen und Funktionen enthält, die zur verschönungs Funktion der MFC-Klassen geschrieben wurden. Eine MFC-Erweiterungs-DLL verwendet die gemeinsam genutzten MFC-DLLs auf die gleiche Weise, wie eine Anwendung Sie verwendet. es gibt jedoch einige zusätzliche Überlegungen:

- Der Buildprozess ähnelt dem Erstellen einer Anwendung, die die freigegebenen MFC-Bibliotheken mit einigen zusätzlichen Compileroptionen und Linkeroptionen verwendet.

- Eine MFC-Erweiterungs-DLL weist keine von `CWinApp` abgeleitete Klasse auf.

- Eine MFC-Erweiterungs-DLL muss ein spezielles bereitstellen `DllMain` . Der AppWizard stellt eine `DllMain` Funktion bereit, die Sie ändern können.

- Eine MFC-Erweiterungs-DLL stellt in der Regel eine Initialisierungs Routine bereit, um eine zu erstellen, `CDynLinkLibrary` Wenn die MFC-Erweiterungs-DLL `CRuntimeClass` es oder Ressourcen in die Anwendung exportieren möchte. Eine abgeleitete Klasse von `CDynLinkLibrary` kann verwendet werden, wenn anwendungsspezifische Daten von der MFC-Erweiterungs-DLL verwaltet werden müssen.

Diese Überlegungen werden im folgenden ausführlicher beschrieben. Sie sollten auch auf das MFC Advanced Concepts Sample [DLLHUSK](../overview/visual-cpp-samples.md) verweisen, da es Folgendes veranschaulicht:

- Entwickeln einer Anwendung, die die freigegebenen Bibliotheken verwendet. (DLLHUSK.EXE ist eine MFC-Anwendung, die dynamisch mit den MFC-Bibliotheken und anderen DLLs verknüpft ist.)

- Aufbauen einer MFC-Erweiterungs-DLL. (Beachten Sie die speziellen Flags, z. b. `_AFXEXT` , die beim Aufbau einer MFC-Erweiterungs-DLL verwendet werden.

- Zwei Beispiele für MFC-Erweiterungs-DLLs. Eine zeigt die grundlegende Struktur einer MFC-Erweiterungs-DLL mit eingeschränkten Exporten (TESTDLL1), und die andere zeigt das Exportieren einer vollständigen Klassen Schnittstelle (TESTDLL2).

Sowohl die Client Anwendung als auch alle MFC-Erweiterungs-DLLs müssen die gleiche Version von MFCxx.DLL verwenden. Befolgen Sie die MFC-DLL-Konvention, und geben Sie eine Debug-und Einzelhandelsversion (/Release) Ihrer MFC-Erweiterungs-DLL an. Dadurch können Client Programme sowohl Debug-als auch Einzelhandelsversionen Ihrer Anwendungen erstellen und Sie mit der entsprechenden Debug-oder Verkaufsversion aller DLLs verknüpfen.

> [!NOTE]
> Da Probleme beim melden und Exportieren von C++ auftreten, kann die Exportliste aus einer MFC-Erweiterungs-DLL zwischen den Debug-und Einzelhandelsversionen derselben DLL und DLLs für verschiedene Plattformen abweichen. Der Einzelhandels MFCxx.DLL hat ungefähr 2000 exportierte Einstiegspunkte. der DebugMFCxxD.DLL hat ungefähr 3000 exportierte Einstiegspunkte.

### <a name="quick-note-on-memory-management"></a>Kurz Notiz zur Speicherverwaltung

Der Abschnitt "Speicherverwaltung" am Ende dieses technischen Hinweises beschreibt die Implementierung des MFCxx.DLL mit der gemeinsam genutzten MFC-Version. Die Informationen, die Sie wissen müssen, um nur eine MFC-Erweiterungs-DLL zu implementieren, werden hier beschrieben.

MFCxx.DLL und alle MFC-Erweiterungs-DLLs, die in den Adressraum einer Client Anwendung geladen werden, verwenden dieselbe Speicherzuweisung, dasselbe Laden von Ressourcen und andere globale MFC-Zustände, als wären Sie in derselben Anwendung. Dies ist von Bedeutung, da die nicht-MFC-DLL-Bibliotheken und regulären MFC-DLLs, die statisch mit MFC verknüpft sind, genau das Gegenteil erreichen und jede DLL aus Ihrem eigenen Speicherpool zuordnet.

Wenn eine MFC-Erweiterungs-DLL Arbeitsspeicher zuordnet, kann dieser Arbeitsspeicher mit jedem anderen von der Anwendung zugewiesenen Objekt frei gemischt werden. Wenn eine Anwendung, die die freigegebenen MFC-Bibliotheken verwendet, abstürzt, behält der Schutz des Betriebssystems auch die Integrität aller anderen MFC-Anwendungen bei, die die DLL gemeinsam verwenden.

Ebenso werden andere "globale" MFC-Zustände, wie z. b. die aktuelle ausführbare Datei, aus der Ressourcen geladen werden, auch von der Client Anwendung und allen MFC-Erweiterungs-DLLs sowie von MFCxx.DLL selbst gemeinsam genutzt.

### <a name="building-an-mfc-extension-dll"></a>Aufbauen einer MFC-Erweiterungs-DLL

Sie können AppWizard verwenden, um ein MFC-Erweiterungs-DLL-Projekt zu erstellen, und es werden automatisch die entsprechenden Compiler-und Linkereinstellungen generiert. Außerdem wurde eine Funktion generiert `DllMain` , die Sie ändern können.

Wenn Sie ein vorhandenes Projekt in eine MFC-Erweiterungs-DLL-Datei umrechnen, beginnen Sie mit den Standardregeln zum Entwickeln einer Anwendung, die die freigegebene Version von MFC verwendet, und führen Sie dann Folgendes aus:

- Hinzufügen **/D_AFXEXT** zu den Compilerflags. Wählen Sie im Dialogfeld Projekteigenschaften den Knoten C/C++ aus. Wählen Sie dann die Kategorie Präprozessor aus. Fügen Sie `_AFXEXT` dem Feld Makros definieren hinzu, wobei die einzelnen Elemente durch Semikolons voneinander getrennt werden.

- Entfernen Sie den **/Gy** -Compilerschalter. Wählen Sie im Dialogfeld Projekteigenschaften den Knoten C/C++ aus. Wählen Sie dann die Kategorie Code Generierung aus. Stellen Sie sicher, dass die Option Funktionsebene aktivieren nicht aktiviert ist. Dadurch wird das Exportieren von Klassen vereinfacht, da der Linker keine Funktionen entfernt, auf die nicht verwiesen wird. Wenn das ursprüngliche Projekt verwendet wird, um eine reguläre, statisch mit MFC verknüpfte MFC-DLL zu erstellen, ändern Sie die **/MT [d]-** Compileroption in **/MD [d]**.

- Erstellen Sie eine Export Bibliothek mit der Option **/dll** , um einen Link zu erstellen. Dieser Wert wird festgelegt, wenn Sie ein neues Ziel erstellen und eine Win32-Dynamic-Link-Bibliothek als Zieltyp angeben.

### <a name="changing-your-header-files"></a>Ändern der Header Dateien

Das Ziel einer MFC-Erweiterungs-DLL besteht in der Regel darin, einige allgemeine Funktionen in eine oder mehrere Anwendungen zu exportieren, die diese Funktion verwenden können. Dies geht auf den Export von Klassen und globalen Funktionen ein, die für Ihre Client Anwendungen verfügbar sind.

Um dies zu erreichen, müssen Sie sicherstellen, dass jede der Element Funktionen entsprechend als Import oder Export gekennzeichnet ist. Hierfür sind spezielle Deklarationen erforderlich: `__declspec(dllexport)` und `__declspec(dllimport)` . Wenn Ihre Klassen von den Client Anwendungen verwendet werden, sollen Sie als deklariert werden `__declspec(dllimport)` . Wenn die MFC-Erweiterungs-DLL selbst erstellt wird, sollten Sie als deklariert werden `__declspec(dllexport)` . Außerdem müssen die Funktionen tatsächlich exportiert werden, damit die Client Programme zur Ladezeit an Sie gebunden werden.

Um die gesamte Klasse zu exportieren, verwenden Sie `AFX_EXT_CLASS` in der Klassendefinition. Dieses Makro wird vom Framework definiert, als `__declspec(dllexport)` Wenn `_AFXDLL` und `_AFXEXT` definiert sind, aber definiert als, `__declspec(dllimport)` Wenn `_AFXEXT` nicht definiert ist. `_AFXEXT`wie oben beschrieben, wird nur beim Aufbau ihrer MFC-Erweiterungs-DLL definiert. Beispiel:

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>Exportieren von Teilen einer Klasse

Manchmal möchten Sie möglicherweise nur die einzelnen erforderlichen Member ihrer Klasse exportieren. Wenn Sie z. B. eine von `CDialog` abgeleitete Klasse exportieren, müssen Sie möglicherweise nur den Konstruktor und den `DoModal`-Aufruf exportieren. Sie können diese Member mithilfe der dll-Elemente exportieren. DEF-Datei, aber Sie können auch `AFX_EXT_CLASS` in den einzelnen Membern, die Sie exportieren müssen, auf die gleiche Weise verwenden.

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

Wenn Sie dies tun, kann ein zusätzliches Problem auftreten, da Sie nicht mehr alle Member der Klasse exportieren. Das Problem liegt in der Art und Weise, wie MFC-Makros funktionieren. Mehrere MFC-Hilfsmakros deklarieren oder definieren Datenmember. Daher müssen diese Datenmember auch aus der dll exportiert werden.

Beispielsweise wird das DECLARE_DYNAMIC-Makro beim Aufbau einer MFC-Erweiterungs-DLL wie folgt definiert:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \
```

Die Zeile, in der "static" beginnt, `AFX_DATA` deklariert ein statisches Objekt in der Klasse. , Um diese Klasse ordnungsgemäß zu exportieren und auf die Laufzeitinformationen von einem Client zuzugreifen. EXE, Sie müssen dieses statische Objekt exportieren. Da das statische Objekt mit dem Modifizierer `AFX_DATA` deklariert ist, müssen Sie `AFX_DATA` beim Erstellen Ihrer DLL nur als `__declspec(dllexport)` und beim Erstellen der ausführbaren Clientdatei als `__declspec(dllimport)` definieren.

Wie bereits erläutert, `AFX_EXT_CLASS` ist bereits auf diese Weise definiert. Sie müssen nur neu definieren `AFX_DATA` , damit Sie mit der `AFX_EXT_CLASS` Klassendefinition identisch sind.

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

MFC verwendet immer das `AFX_DATA` Symbol für Datenelemente, die in den Makros definiert werden, sodass dieses Verfahren für alle Szenarien funktioniert. Beispielsweise funktioniert Sie für DECLARE_MESSAGE_MAP.

> [!NOTE]
> Wenn Sie die gesamte Klasse anstelle ausgewählter Member der Klasse exportieren, werden statische Datenmember automatisch exportiert.

Sie können das gleiche Verfahren verwenden, um den `CArchive` Extraktions Operator für Klassen, die die DECLARE_SERIAL-und IMPLEMENT_SERIAL-Makros verwenden, automatisch zu exportieren. Exportieren Sie den Archive-Operator, indem Sie die Klassen Deklarationen (die sich im befinden. H-Datei) mit folgendem Code:

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-_afxext"></a>Einschränkungen für _AFXEXT

Sie können das _**Afxext** -Präprozessorsymbol für MFC-Erweiterungs-DLLs verwenden, solange Sie nicht über mehrere Ebenen von MFC-Erweiterungs-DLLs verfügen. Wenn Sie über MFC-Erweiterungs-DLLs verfügen, die Klassen aus Ihren eigenen MFC-Erweiterungs-DLLs aufrufen oder davon abgeleitet sind, und diese wiederum von den MFC-Klassen abgeleitet sind, müssen Sie ein eigenes Präprozessorsymbol verwenden, um Mehrdeutigkeit zu vermeiden.

Das Problem besteht darin, dass Sie in Win32 alle Daten explizit so deklarieren müssen `__declspec(dllexport)` , als ob Sie aus einer DLL exportiert werden sollen, und `__declspec(dllimport)` ob Sie aus einer DLL importiert werden sollen. Wenn Sie definieren `_AFXEXT` , stellen die MFC-Header sicher, dass `AFX_EXT_CLASS` ordnungsgemäß definiert ist.

Wenn Sie über mehrere Ebenen verfügen, ist ein Symbol wie `AFX_EXT_CLASS` nicht ausreichend, da eine MFC-Erweiterungs-DLL neue Klassen exportieren und andere Klassen aus einer anderen MFC-Erweiterungs-DLL importieren kann. Um dieses Problem zu beheben, verwenden Sie ein spezielles Präprozessorsymbol, das angibt, dass Sie die DLL selbst oder die DLL verwenden. Stellen Sie sich beispielsweise zwei MFC-Erweiterungs-DLLs, A.DLL und B.DLL vor. Sie exportieren jeweils einige Klassen in H bzw. B. h. B.DLL verwendet die Klassen aus A.DLL. Die Headerdateien würden in etwa wie folgt aussehen:

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

Wenn A.DLL erstellt wird, wird es mit **/DA_IMPL** erstellt, und wenn B.DLL erstellt wird, wird es mit **/DB_IMPL**erstellt. Durch die Verwendung separater Symbole für jede DLL wird CExampleB exportiert und CExampleA beim Aufbau B.DLL importiert. CExampleA wird bei der Erstellung A.DLL exportiert und importiert, wenn Sie von B.DLL (oder einem anderen Client) verwendet wird.

Diese Art von Schichten kann nicht durchgeführt werden, wenn die integrierten `AFX_EXT_CLASS` und `_AFXEXT` Präprozessorsymbole verwendet werden. Mit dem oben beschriebenen Verfahren wird dieses Problem auf eine Weise gelöst, anders als bei dem Mechanismus, den MFC bei der Erstellung seiner OLE-, Datenbank-und Netzwerk-MFC-Erweiterungs-DLLs verwendet.

### <a name="not-exporting-the-entire-class"></a>Exportieren von Teilen einer Klasse

Auch hier müssen Sie besonders vorsichtig vorgehen, wenn Sie nicht die gesamte Klasse exportieren. Sie müssen sicherstellen, dass die von den MFC-Makros erstellten erforderlichen Datenelemente ordnungsgemäß exportiert werden. Dies kann durch die erneute Definition des `AFX_DATA` Makros für die jeweilige Klasse erreicht werden. Dies sollten Sie immer tun, wenn Sie nicht die gesamte Klasse exportieren.

Zum Beispiel:

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

Im folgenden finden Sie den genauen Code, den Sie in Ihrer Haupt Quelldatei für die MFC-Erweiterungs-DLL platzieren sollten. Er sollte nach dem Standard-enthalten sein. Beachten Sie, dass bei Verwendung von AppWizard zum Erstellen von Starter-Dateien für eine MFC-Erweiterungs-DLL eine `DllMain` für Sie bereitstellt.

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

Der-Befehl `AfxInitExtensionModule` erfasst die Lauf Zeit Klassen der Module (Strukturen) sowie die zugehörigen `CRuntimeClass` objektfactorys (- `COleObjectFactory` Objekte), die später beim Erstellen des-Objekts verwendet werden `CDynLinkLibrary` . Der (optionale)-Befehl `AfxTermExtensionModule` von ermöglicht MFC das Bereinigen der MFC-Erweiterungs-DLL, wenn jeder Prozess trennt (was geschieht, wenn der Prozess beendet wird, oder wenn die dll als Ergebnis eines- `FreeLibrary` Aufrufes entladen wird) von der MFC-Erweiterungs-DLL. Da die meisten MFC-Erweiterungs-DLLs nicht dynamisch geladen werden (in der Regel werden Sie über Ihre Import Bibliotheken verknüpft), ist der-Befehl in `AfxTermExtensionModule` der Regel nicht erforderlich.

Wenn Ihre Anwendung MFC-Erweiterungs-DLLs dynamisch lädt und freigibt, müssen Sie `AfxTermExtensionModule` wie oben gezeigt aufzurufen. Achten Sie auch darauf, `AfxLoadLibrary` und `AfxFreeLibrary` (anstelle von Win32-Funktionen und) zu verwenden, `LoadLibrary` `FreeLibrary` Wenn Ihre Anwendung mehrere Threads verwendet oder wenn eine MFC-Erweiterungs-DLL dynamisch geladen wird. Mit `AfxLoadLibrary` und `AfxFreeLibrary` wird sichergestellt, dass der Code zum Starten und Herunterfahren, der ausgeführt wird, wenn die MFC-Erweiterungs-DLL geladen und entladen wird, den globalen MFC-Zustand nicht beschädigt.

Die Header Datei "Afxdllx". H enthält spezielle Definitionen für Strukturen, die in MFC-Erweiterungs-DLLs verwendet werden, z. b. die Definition für `AFX_EXTENSION_MODULE` und `CDynLinkLibrary` .

Die globale *ExtensionDLL* muss wie gezeigt deklariert werden. Anders als bei der 16-Bit-Version von MFC können Sie während dieser Zeit Arbeitsspeicher zuweisen und MFC-Funktionen aufrufen, da die MFCxx.DLL vollständig durch den Zeitpunkt des Aufrufs von initialisiert wird `DllMain` .

### <a name="sharing-resources-and-classes"></a>Gemeinsame Nutzung von Ressourcen und Klassen

Einfache MFC-Erweiterungs-DLLs müssen nur wenige Funktionen mit geringer Bandbreite in die Client Anwendung exportieren. Weitere Benutzeroberflächen intensive DLLs möchten möglicherweise Ressourcen und C++-Klassen in die Client Anwendung exportieren.

Der Export von Ressourcen erfolgt über eine Ressourcenliste. In jeder Anwendung ist eine einzeln verknüpfte Liste von `CDynLinkLibrary` Objekten. Bei der Suche nach einer Ressource sehen die meisten MFC-Standard Implementierungen, mit denen Ressourcen geladen werden, zuerst das aktuelle Ressourcen Modul ( `AfxGetResourceHandle` ). Wenn Sie nicht gefunden werden, können Sie die Liste der Objekte durchlaufen, die `CDynLinkLibrary` versuchen, die angeforderte Ressource zu laden.

Die dynamische Erstellung von C++-Objekten bei Angabe eines C++-Klassen namens ist ähnlich. Der MFC-objektdeserialisierungsmechanismus muss alle `CRuntimeClass` Objekte registriert haben, damit er wieder hergestellt werden kann, indem er das C++-Objekt des erforderlichen Typs basierend auf den zuvor gespeicherten Daten dynamisch erstellt.

Wenn Sie möchten, dass die Client Anwendung Klassen in der MFC-Erweiterungs-DLL verwendet, die sind `DECLARE_SERIAL` , müssen Sie die Klassen exportieren, damit Sie für die Client Anwendung sichtbar sind. Dies wird auch durch das Durchlaufen der `CDynLinkLibrary` Liste erreicht.

Im Fall des MFC-Beispiel für erweiterte Konzepte [DLLHUSK](../overview/visual-cpp-samples.md)sieht die Liste in etwa wie folgt aus:

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

Der MFCxx.DLL wird in der Regel in der Ressourcen-und Klassenliste angezeigt. MFCxx.DLL enthält alle standardmäßigen MFC-Ressourcen, einschließlich der Eingabe Aufforderungs Zeichenfolgen für alle Standard Befehls-IDs. Wenn Sie es am Ende der Liste platzieren, können DLLs und die Client Anwendung selbst nicht über eine eigene Kopie der standardmäßigen MFC-Ressourcen verfügen, sondern sich stattdessen auf die freigegebenen Ressourcen im MFCxx.DLL verlassen.

Das Zusammenführen der Ressourcen und Klassennamen aller DLLs in den Namespace der Client Anwendung hat den Nachteil, dass Sie sorgfältig angeben müssen, welche IDs oder Namen Sie auswählen. Natürlich können Sie diese Funktion deaktivieren, indem Sie weder ihre Ressourcen noch ein- `CDynLinkLibrary` Objekt in die Client Anwendung exportieren. Im [DLLHUSK](../overview/visual-cpp-samples.md)-Beispiel wird der Namespace für gemeinsam genutzte Ressourcen mithilfe mehrerer Headerdateien verwaltet. Weitere Tipps zur Verwendung von freigegebenen Ressourcen Dateien finden [Sie im technischen Hinweis 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md) .

### <a name="initializing-the-dll"></a>Initialisieren der dll

Wie bereits erwähnt, möchten Sie in der Regel ein-Objekt erstellen, um `CDynLinkLibrary` Ihre Ressourcen und Klassen in die Client Anwendung zu exportieren. Sie müssen einen exportierten Einstiegspunkt angeben, um die dll zu initialisieren. Dies ist mindestens eine void-Routine, die keine Argumente annimmt und nichts zurückgibt, aber es kann etwas sein, was Sie möchten.

Jede Client Anwendung, die die DLL verwenden möchte, muss diese Initialisierungs Routine aufrufen, wenn Sie diesen Ansatz verwenden. Sie können dieses Objekt auch `CDynLinkLibrary` `DllMain` direkt nach dem Aufrufen von zuordnen `AfxInitExtensionModule` .

Die Initialisierungs Routine muss ein `CDynLinkLibrary` -Objekt im Heap der aktuellen Anwendung erstellen, das mit den Informationen ihrer MFC-Erweiterungs-DLL verknüpft ist. Dies kann mit folgendem erreicht werden:

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

Der Routine Name ( *initxxxdll* ) in diesem Beispiel kann alles sein, was Sie möchten. Es muss nicht **extern "C"** sein, aber dadurch wird die Exportliste leichter zu verwalten.

> [!NOTE]
> Wenn Sie die MFC-Erweiterungs-DLL aus einer regulären MFC-DLL verwenden, müssen Sie diese Initialisierungsfunktion exportieren. Diese Funktion muss von der regulären MFC-DLL vor der Verwendung von MFC-Erweiterungs-DLL-Klassen oder-Ressourcen aufgerufen werden.

### <a name="exporting-entries"></a>Exportieren von Einträgen

Die einfache Möglichkeit zum Exportieren von Klassen ist die Verwendung `__declspec(dllimport)` `__declspec(dllexport)` von und für die einzelnen Klassen und globalen Funktionen, die Sie exportieren möchten. Dies vereinfacht dies, ist jedoch weniger effizient als das Benennen der einzelnen Einstiegspunkte (unten beschrieben), da Sie weniger Kontrolle über die exportierten Funktionen haben und die Funktionen nicht nach Ordinalzahl exportieren können. TESTDLL1 und Testdll2 verwenden Sie diese Methode, um Ihre Einträge zu exportieren.

Eine effizientere Methode (und die von MFCxx.DLL verwendete Methode) besteht darin, jeden Eintrag von Hand zu exportieren, indem Sie jeden Eintrag in der benennen. DEF-Datei. Da wir selektive Exporte aus unserer DLL exportieren (d. h. nicht alles), müssen wir entscheiden, welche Schnittstellen Sie exportieren möchten. Dies ist schwierig, da Sie die geschsich gten Namen für den Linker in Form von Einträgen in der angeben müssen. DEF-Datei. Exportieren Sie keine C++-Klassen, es sei denn, Sie benötigen einen symbolischen Link dafür.

Wenn Sie versucht haben, C++-Klassen mit einem zu exportieren. DEF-Datei vor können Sie ein Tool entwickeln, um diese Liste automatisch zu generieren. Dies kann mit einem zweistufigen Link Prozess erfolgen. Verknüpfen Sie die dll einmal ohne Exporte, und lassen Sie den Linker einen generieren. Zuordnungs Datei. Die. Die Zuordnungs Datei kann verwendet werden, um eine Liste von Funktionen zu generieren, die exportiert werden sollen. bei einigen Neuanordnungen kann Sie also verwendet werden, um die Export Einträge für die zu generieren. DEF-Datei. Die Exportliste für MFCxx.DLL und die MFC-Erweiterungs-DLLs der OLE-und MFC-Datenbank wurden mit einem derartigen Prozess generiert (obwohl Sie nicht vollständig automatisch ist und jede Weile eine gewisse Hand Optimierung erfordert).

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp im Vergleich zu CDynLinkLibrary

Eine MFC-Erweiterungs-DLL weist kein `CWinApp` eigenes Objekt auf, sondern muss mit dem `CWinApp` von abgeleiteten Objekt der Client Anwendung arbeiten. Dies bedeutet, dass die Client Anwendung das hauptnachrichtenpump, die Leerlauf Schleife usw. besitzt.

Wenn Ihre MFC-Erweiterungs-DLL zusätzliche Daten für jede Anwendung beibehalten muss, können Sie eine neue Klasse von ableiten `CDynLinkLibrary` und Sie in der oben beschriebenen initxxxdll-Routine erstellen. Bei der Ausführung kann die dll die Liste der Objekte der aktuellen Anwendung überprüfen `CDynLinkLibrary` , um die Liste für diese bestimmte MFC-Erweiterungs-DLL zu finden.

### <a name="using-resources-in-your-dll-implementation"></a>Verwenden von Ressourcen in der dll-Implementierung

Wie bereits erwähnt, durchläuft der Standard Ressourcen Ladevorgang die Liste der Objekte, die nach `CDynLinkLibrary` der ersten exe-oder dll-Ressource mit der angeforderten Ressource suchen. Alle MFC-APIs und der gesamte interne Code verwenden, `AfxFindResourceHandle` um die Ressourcen Liste zu durchlaufen, um beliebige Ressourcen zu finden, unabhängig davon, wo Sie sich befinden.

Wenn Sie nur Ressourcen von einem bestimmten Speicherort laden möchten, verwenden Sie die APIs `AfxGetResourceHandle` und `AfxSetResourceHandle` , um das alte Handle zu speichern und das neue Handle festzulegen. Achten Sie darauf, dass Sie das alte Ressourcenhandle wiederherstellen, bevor Sie zur Clientanwendung zurückkehren. Das Beispiel Testdll2 verwendet diesen Ansatz, um ein Menü explizit zu laden.

Das Durchlaufen der Liste hat jedoch den Nachteil, dass die Suche etwas langsamer ist und dass die Ressourcen-ID-Bereiche verwaltet werden müssen. Der Vorteil liegt darin, dass eine Clientanwendung, die mit mehreren MFC-Erweiterungs-DLLs verknüpft ist, jede durch die DLL zur Verfügung gestellte Ressource nutzen kann, ohne dass das DLL-Instanzenhandle angegeben werden muss. `AfxFindResourceHandle` ist eine API, die bei der Suche nach einer bestimmten Übereinstimmung die Ressourcenliste durchläuft. Sie verwendet den Ressourcennamen und -typ als Parameter und gibt das zuerst ermittelte Ressourcenhandle (oder NULL) zurück.

## <a name="writing-an-application-that-uses-the-dll-version"></a><a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a>Schreiben einer Anwendung, die die dll-Version verwendet

### <a name="application-requirements"></a>Anwendungsanforderungen

Eine Anwendung, die die freigegebene Version von MFC verwendet, muss einige einfache Regeln befolgen:

- Er muss über ein `CWinApp` -Objekt verfügen und die Standardregeln für ein nachrichtenpump befolgen.

- Er muss mit einem Satz erforderlicher Compilerflags kompiliert werden (siehe unten).

- Es muss mit den MFCxx-Import Bibliotheken verknüpft werden. Indem die erforderlichen Compilerflags festgelegt werden, bestimmen die MFC-Header zur Verknüpfungs Zeit, mit welcher Bibliothek die Anwendung verknüpft werden soll.

- Um die ausführbare Datei auszuführen, müssen sich MFCxx.DLL im Pfad oder im Windows-System Verzeichnis befinden.

### <a name="building-with-the-development-environment"></a>Entwickeln mit der Entwicklungsumgebung

Wenn Sie das interne Makefile mit den meisten Standard Standardwerten verwenden, können Sie das Projekt problemlos so ändern, dass die dll-Version erstellt wird.

Im folgenden Schritt wird davon ausgegangen, dass eine ordnungsgemäß funktionierende MFC-Anwendung mit Nafxcwd verknüpft ist. LIB (für Debug) und NAFXCW. LIB (für den Einzelhandel), und Sie möchten ihn so konvertieren, dass die freigegebene Version der MFC-Bibliothek verwendet wird. Sie führen die Visual C++ Umgebung aus und verfügen über eine interne Projektdatei.

1. Klicken Sie im Menü **Projekte** auf **Eigenschaften**. Legen Sie auf der Seite **Allgemein** unter **Projekt**Standards Microsoft Foundation Classes fest, dass **MFC in einer freigegebenen DLL** (MFCxx (d). dll) verwendet werden soll.

### <a name="building-with-nmake"></a>Erstellen mit NMAKE

Wenn Sie die externe Makefile-Funktion des Visual C++ verwenden oder NMAKE direkt verwenden, müssen Sie das Makefile-Element für die Unterstützung von Compileroptionen und Linkeroptionen bearbeiten.

Erforderliche Compilerflags:

- **/D_AFXDLL/MD** 
   **/D_AFXDLL**

Für die MFC-Standard Header muss dieses Symbol definiert werden:

- **/MD** Die Anwendung muss die dll-Version der C-Lauf Zeit Bibliothek verwenden.

Alle anderen Compilerflags folgen den MFC-Standardeinstellungen (z. b. _DEBUG für Debug).

Bearbeiten Sie die linkerliste der Bibliotheken. Ändern Sie NAFXCWD. Lib in MFCxxD. lib und Ändern von NAFXCW. Lib in MFCxx. lib. Ersetzen Sie libc. LIB mit MSVCRT. LIB. Wie bei jeder anderen MFC-Bibliothek ist es wichtig, dass "MFCxxD. lib" **vor** allen C-Laufzeitbibliotheken platziert wird.

Optional können Sie die Compileroptionen für den Einzelhandel und die debugressource hinzufügen **/D_AFXDLL** (die Datei, die die Ressourcen tatsächlich mit **/R**kompiliert). Dadurch wird die endgültige ausführbare Datei kleiner, indem die Ressourcen freigegeben werden, die in den MFC-DLLs vorhanden sind.

Nachdem diese Änderungen vorgenommen wurden, ist eine vollständige Neuerstellung erforderlich.

### <a name="building-the-samples"></a>Erstellen der Beispiele

Die meisten MFC-Beispiel Programme können aus Visual C++ oder aus einem freigegebenen NMAKE-kompatiblen Makefile-Element von der Befehlszeile aus erstellt werden.

Um diese Beispiele zum Verwenden von MFCxx.DLL zu konvertieren, können Sie das Laden. MAK-Datei in die Visual C++, und legen Sie die Projektoptionen wie oben beschrieben fest. Wenn Sie den NMAKE-Build verwenden, können Sie "AFXDLL = 1" in der Befehlszeile NMAKE angeben und das Beispiel mithilfe der gemeinsam genutzten MFC-Bibliotheken erstellen.

Das MFC Advanced Concepts Sample [DLLHUSK](../overview/visual-cpp-samples.md) wird mit der dll-Version von MFC erstellt. In diesem Beispiel wird nicht nur veranschaulicht, wie eine mit MFCxx.DLL verknüpfte Anwendung erstellt wird, sondern es werden auch andere Funktionen der MFC-DLL-Paket Erstellungs Option veranschaulicht, wie später in diesem technischen Hinweis beschrieben.

### <a name="packaging-notes"></a>Hinweise zur Paket Erstellung

Die Verkaufsversion der DLLs (MFCxx [U]. DLL) sind frei Verteil Bar. Die Debugversion der DLLs ist nicht frei weitervertreibbar und sollte nur während der Entwicklung der Anwendung verwendet werden.

Die debugdlls werden mit Debuginformationen bereitgestellt. Mithilfe des Visual C++-Debuggers können Sie die Ausführung der Anwendung und der dll verfolgen. Die releasedlls (MFCxx [U]. DLL) enthalten keine Debuginformationen.

Wenn Sie die DLLs anpassen oder neu erstellen, sollten Sie Sie als "MFCxx" für die MFC-src-Datei "mfcdll" bezeichnen. MAK beschreibt Buildoptionen und enthält die Logik zum Umbenennen der dll. Das Umbenennen der Dateien ist erforderlich, da diese DLLs potenziell von vielen MFC-Anwendungen gemeinsam genutzt werden. Wenn Sie die benutzerdefinierte Version der MFC-DLLs ersetzen, die auf dem System installiert sind, kann eine andere MFC-Anwendung unter Verwendung der gemeinsam genutzten MFC-DLLs unterbrechen

Es wird nicht empfohlen, MFC-DLLs neu zu erstellen.

## <a name="how-the-mfcxxdll-is-implemented"></a><a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a>Implementierung der MFCxx.DLL

Im folgenden Abschnitt wird beschrieben, wie die MFC-DLL (MFCxx.DLL und MFCxxD.DLL) implementiert wird. Das Verständnis der hier aufgeführten Details ist auch nicht wichtig, wenn Sie nur die MFC-DLL mit Ihrer Anwendung verwenden möchten. Die hier aufgeführten Details sind nicht zwingend erforderlich, um zu verstehen, wie Sie eine MFC-Erweiterungs-DLL schreiben, aber das Verständnis dieser Implementierung kann Ihnen beim Schreiben Ihrer eigenen dll helfen.

### <a name="implementation-overview"></a>Implementierungs Übersicht

Die MFC-DLL ist ein Sonderfall einer MFC-Erweiterungs-DLL, wie oben beschrieben. Sie verfügt über eine sehr große Anzahl von Exporten für eine große Anzahl von Klassen. In der MFC-DLL gibt es einige zusätzliche Dinge, die Sie noch spezieller machen als eine reguläre MFC-Erweiterungs-DLL.

### <a name="win32-does-most-of-the-work"></a>Win32 erledigt den größten Teil der Arbeit.

Die 16-Bit-Version von MFC benötigte eine Reihe spezieller Verfahren, einschließlich APP-basierter Daten im Stapel Segment, spezieller Segmente, die durch einige 80x86-Assemblycodes, prozessspezifische Ausnahme Kontexte und andere Techniken erstellt wurden. Win32 unterstützt direkt Prozess interne Daten in einer DLL, die Sie in den meisten Fällen benötigen. Der größte Teil MFCxx.DLL ist nur NAFXCW. In eine DLL gepackte lib. Wenn Sie sich den MFC-Quellcode ansehen, finden Sie nur wenige #ifdef _AFXDLL, da nur sehr wenige Sonderfälle durchgeführt werden müssen. Die speziellen Fälle, in denen es sich um die Verwendung von Win32 unter Windows 3,1 handelt (wird auch als Win32s bezeichnet). Win32s unterstützt nicht direkt Prozess interne dll-Daten, sodass die MFC-DLL die TLS-Win32-APIs (Thread-Local Storage) verwenden muss, um Prozess lokale Daten abzurufen.

### <a name="impact-on-library-sources-additional-files"></a>Auswirkung auf Bibliotheks Quellen, zusätzliche Dateien

Die Auswirkung der **_AFXDLL** Version auf die normalen MFC-Klassen Bibliotheks Quellen und-Header ist relativ gering. Es gibt eine spezielle Versionsdatei (AFXV_DLL. H) und eine zusätzliche Header Datei (AFXDLL_. H) im Haupt-AFXWIN enthalten. H-Header. Der AFXDLL_. Der H-Header enthält die `CDynLinkLibrary` -Klasse und andere Implementierungsdetails sowohl für `_AFXDLL` Anwendungen als auch für MFC-Erweiterungs-DLLs. Der Afxdllx. Der H-Header wird zum Aufbauen von MFC-Erweiterungs-DLLs bereitgestellt (Weitere Informationen finden Sie oben).

Die regulären Quellen für die MFC-Bibliothek in MFC src verfügen unter dem #ifdef über zusätzlichen bedingten Code `_AFXDLL` . Eine zusätzliche Quelldatei (dllinit). Cpp) enthält den zusätzlichen DLL-Initialisierungs Code und andere Bindungen für die freigegebene Version von MFC.

Um die freigegebene Version von MFC zu erstellen, werden zusätzliche Dateien bereitgestellt. (Weitere Informationen zum Erstellen der dll finden Sie unten.)

- Zweikampf. DEF-Dateien werden zum Exportieren der MFC-DLL-Einstiegspunkte für die Debugversionen (MFCxxD. def) und Release (MFCxx. def) der dll verwendet.

- Halbe. RC-Datei (mfcdll. RC) enthält alle Standard-MFC-Ressourcen und eine VERSIONINFO-Ressource für die dll.

- Ein. CLW-Datei (mfcdll. CLW) wird bereitgestellt, um das Durchsuchen der MFC-Klassen mithilfe von ClassWizard zuzulassen. Hinweis: dieses Feature ist für die dll-Version von MFC nicht besonders.

### <a name="memory-management"></a>Speicherverwaltung

Eine Anwendung, die MFCxx.DLL verwendet, verwendet eine gemeinsame, von MSVCRTxx.DLL bereitgestellte Speicherzuweisung, die freigegebene C-Runtime-DLL. Diese Shared Memory-Zuweisung wird von der Anwendung, allen MFC-Erweiterungs-DLLs und den MFC-DLLs selbst verwendet. Durch die Verwendung einer freigegebenen DLL für die Speicher Belegung können die MFC-DLLs Speicher belegen, der später von der Anwendung freigegeben wird (oder umgekehrt). Da sowohl die Anwendung als auch die dll denselben Zuweisungsoperator verwenden müssen, sollten Sie den C++ Global **Operator new** oder **Operator Delete**nicht überschreiben. Die gleichen Regeln gelten für den Rest der C-Laufzeitspeicher Belegungs Routinen (z. b. **malloc**, **realloc**, **Free**und andere).

### <a name="ordinals-and-class-__declspecdllexport-and-dll-naming"></a>Ordinale und Klassen __declspec (dllexport) und dll-Benennung

Die `class` **`__declspec(dllexport)`** Funktionalität des C++-Compilers wird nicht verwendet. Stattdessen ist eine Liste der Exporte in den Klassen Bibliotheks Quellen (MFCxx. def und MFCxxD. def) enthalten. Nur diese Auswahl Punkte (Funktionen und Daten) werden exportiert. Andere Symbole, wie z. b. private MFC-Implementierungs Funktionen oder-Klassen, werden nicht exportiert. alle Exporte werden von der Ordinalzahl ohne einen Zeichen folgen Namen in der residenten oder nicht Residenten namens Tabelle durchgeführt.

`class` **`__declspec(dllexport)`** Die Verwendung von ist möglicherweise eine geeignete Alternative zum aufbauen kleinerer DLLs, aber im Fall einer großen dll wie MFC weist der Standard Exportmechanismus Effizienz-und Kapazitäts Limits auf.

Dies bedeutet, dass wir eine große Menge an Funktionalität im Release MFCxx.DLL verpacken können, die nur um 800 KB liegt, ohne dass die Ausführungs-oder Ladegeschwindigkeit beeinträchtigt wird. MFCxx.DLL hätte 100 KB größer gewesen, hätte dieses Verfahren nicht verwendet. Dies ermöglicht auch das Hinzufügen zusätzlicher Einstiegspunkte am Ende der. Die DEF-Datei, um eine einfache Versionsverwaltung zu ermöglichen, ohne die Geschwindigkeit und Größen Effizienz des Exports durch ordinale zu beeinträchtigen. Bei größeren Versions Revisionen in der MFC-Klassenbibliothek wird der Bibliotheksname geändert. Das heißt, MFC30.DLL ist die verteilbare dll, die Version 3,0 der MFC-Klassenbibliothek enthält. Wenn Sie diese DLL beispielsweise in einem hypothetischen MFC 3,1 aktualisieren, wird die dll stattdessen MFC31.DLL benannt. Wenn Sie den MFC-Quellcode so ändern, dass eine benutzerdefinierte Version der MFC-DLL erzeugt wird, verwenden Sie einen anderen Namen (und vorzugsweise einen Namen ohne "MFC" im Namen).

## <a name="see-also"></a>Weitere Informationen

[Technische Hinweise nach Zahl](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise nach Kategorie](../mfc/technical-notes-by-category.md)
