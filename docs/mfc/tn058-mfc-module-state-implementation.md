---
title: 'TN058: MFC-Modulzustandsimplementierung'
ms.date: 06/28/2018
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
ms.openlocfilehash: b64fb6b97474007c44a2124315e83e1ac119f9ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366605"
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058: MFC-Modulzustandsimplementierung

> [!NOTE]
> Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

Dieser technische Hinweis beschreibt die Implementierung von MFC-"Modulstatus"-Konstrukten. Ein Verständnis der Modulstatusimplementierung ist für die Verwendung der freigegebenen MFC-DLLs von einer DLL (oder OLE-In-Process-Server) von entscheidender Bedeutung.

Bevor Sie diese Notiz lesen, lesen Sie "Verwalten der Zustandsdaten von MFC-Modulen" unter [Erstellen neuer Dokumente, Windows und Ansichten](../mfc/creating-new-documents-windows-and-views.md). Dieser Artikel enthält wichtige Nutzungsinformationen und Übersichtsinformationen zu diesem Thema.

## <a name="overview"></a>Übersicht

Es gibt drei Arten von MFC-Statusinformationen: Modulstatus, Prozessstatus und Threadstatus. Manchmal können diese Zustandstypen kombiniert werden. Die Handle-Maps von MFC sind z. B. sowohl modullokal als auch threadlokal. Dadurch können zwei verschiedene Module unterschiedliche Karten in jedem ihrer Threads haben.

Prozessstatus und Threadstatus sind ähnlich. Diese Datenelemente sind Dinge, die traditionell globale Variablen waren, aber für eine ordnungsgemäße Win32s-Unterstützung oder für eine ordnungsgemäße Multithreading-Unterstützung spezifisch für einen bestimmten Prozess oder Thread sein müssen. Welche Kategorie ein bestimmtes Datenelement einfügt, hängt von diesem Element und der gewünschten Semantik in Bezug auf Prozess- und Threadgrenzen ab.

Modulstatus ist insofern eindeutig, als er entweder einen wirklich globalen Zustand oder einen Zustand enthalten kann, der lokal oder threadlokal verarbeitet wird. Darüber hinaus kann es schnell geschaltet werden.

## <a name="module-state-switching"></a>Modulstatus-Switching

Jeder Thread enthält einen Zeiger auf den Modulstatus "aktuell" oder "aktiv" (es überrascht nicht, dass der Zeiger Teil des lokalen Threadstatus von MFC ist). Dieser Zeiger wird geändert, wenn der Ausführungsthread eine Modulgrenze überschreitet, z. B. eine Anwendung, die eine OLE-Steuerelement- oder DLL-Datei aufruft, oder ein OLE-Steuerelement, das eine Anwendung zurückruft.

Der aktuelle Modulzustand wird `AfxSetModuleState`durch Aufrufen von umgeschaltet. In den meisten Teilen werden Sie sich nie direkt mit der API befassen. MFC wird es in vielen Fällen für Sie anrufen (bei `AfxWndProc`WinMain, OLE-Einstiegspunkte, etc.). Dies geschieht in jeder Komponente, die Sie `WndProc`schreiben, `WinMain` indem `DllMain`Sie statisch in einem speziellen verknüpfen , und einem speziellen (oder ), der weiß, welcher Modulzustand aktuell sein soll. Sie können diesen Code sehen, indem Sie sich DLLMODUL ansehen. CPP oder APPMODUL. CPP im Verzeichnis MFC-SRC.

Es ist selten, dass Sie den Modulstatus festlegen und dann nicht zurücksetzen möchten. Meistens möchten Sie Ihren eigenen Modulstatus als aktuellen "pushen" und dann, nachdem Sie fertig sind, den ursprünglichen Kontext zurück "popen". Dies geschieht durch die [Makro-AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) und die spezielle Klasse `AFX_MAINTAIN_STATE`.

`CCmdTarget`hat spezielle Funktionen zur Unterstützung des Modulzustandswechsels. Insbesondere ist `CCmdTarget` a die Stammklasse, die für die OLE-Automatisierung und OLE COM-Einstiegspunkte verwendet wird. Wie jeder andere Einstiegspunkt, der dem System ausgesetzt ist, müssen diese Einstiegspunkte den richtigen Modulstatus festlegen. Wie weiß `CCmdTarget` ein gegebener, was der "richtige" Modulzustand sein soll Die Antwort ist, dass es "erinnert", was der "aktuelle" Modulzustand ist, wenn er konstruiert wird, so dass es den aktuellen Modulstatus auf diesen "erinnerten" Wert setzen kann, wenn er später aufgerufen wird. Daher ist der Modulstatus, `CCmdTarget` dem ein bestimmtes Objekt zugeordnet ist, der Modulstatus, der beim Bau des Objekts aktuell war. Nehmen Sie ein einfaches Beispiel für das Laden eines INPROC-Servers, das Erstellen eines Objekts und das Aufrufen seiner Methoden.

1. Die DLL wird von `LoadLibrary`OLE mit geladen.

1. `RawDllMain`wird zuerst aufgerufen. Der Modulstatus wird auf den bekannten statischen Modulstatus für die DLL festgelegt. Aus diesem `RawDllMain` Grund ist statisch mit der DLL verknüpft.

1. Der Konstruktor für die Klassenfactory, die unserem Objekt zugeordnet ist, wird aufgerufen. `COleObjectFactory`abgeleitet ist `CCmdTarget` und als Ergebnis, es erinnert sich, in welchem Modulzustand es instanziiert wurde. Dies ist wichtig – wenn die Klassenfactory aufgefordert wird, Objekte zu erstellen, weiß sie jetzt, welchen Modulstatus sie aktuell machen soll.

1. `DllGetClassObject`wird aufgerufen, um die Klassenfabrik zu erhalten. MFC durchsucht die diesem Modul zugeordnete Klassenfactoryliste und gibt sie zurück.

1. `COleObjectFactory::XClassFactory2::CreateInstance` wird aufgerufen. Vor dem Erstellen und Zurückgeben des Objekts legt diese Funktion den Modulstatus auf den Modulstatus `COleObjectFactory` fest, der in Schritt 3 aktuell war (der aktuelle, als der instanziiert wurde). Dies geschieht innerhalb von [METHOD_PROLOGUE](com-interface-entry-points.md).

1. Wenn das Objekt erstellt wird, `CCmdTarget` ist es auch `COleObjectFactory` eine Ableitung und in der gleichen Weise erinnert, welcher Modulzustand aktiv war, ebenso wie dieses neue Objekt. Jetzt weiß das Objekt, in welchen Modulstatus es wechseln soll, wenn es aufgerufen wird.

1. Der Client ruft eine Funktion für das `CoCreateInstance` OLE COM-Objekt auf, das er von seinem Aufruf empfangen hat. Wenn das Objekt aufgerufen `METHOD_PROLOGUE` wird, wird es `COleObjectFactory` verwendet, um den Modulstatus genau wie zu wechseln.

Wie Sie sehen können, wird der Modulstatus von Objekt zu Objekt weitergegeben, während sie erstellt werden. Es ist wichtig, den Modulstatus entsprechend festzulegen. Wenn es nicht festgelegt ist, kann Ihr DLL- oder COM-Objekt schlecht mit einer MFC-Anwendung interagieren, die sie aufruft, oder sie kann keine eigenen Ressourcen finden oder auf andere miserable Weise fehlschlagen.

Beachten Sie, dass bestimmte Arten von DLLs, insbesondere "MFC Extension"-DLLs, den Modulstatus nicht in ihrem `RawDllMain` (tatsächlich haben sie in der Regel nicht einmal eine `RawDllMain`) wechseln. Dies liegt daran, dass sie sich "wie" verhalten sollen, wenn sie tatsächlich in der Anwendung vorhanden waren, die sie verwendet. Sie sind sehr stark ein Teil der Anwendung, die ausgeführt wird, und es ist ihre Absicht, den globalen Status dieser Anwendung zu ändern.

OLE-Steuerelemente und andere DLLs unterscheiden sich sehr. Sie möchten den Status der aufrufenden Anwendung nicht ändern. Die Anwendung, die sie aufruft, ist möglicherweise nicht einmal eine MFC-Anwendung, und es gibt daher möglicherweise keinen Status zum Ändern. Dies ist der Grund, warum die Modulstatusumschaltung erfunden wurde.

Für exportierte Funktionen aus einer DLL, z. B. eine, die ein Dialogfeld in Ihrer DLL startet, müssen Sie den folgenden Code am Anfang der Funktion hinzufügen:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState())
```

Dadurch wird der aktuelle Modulstatus mit dem von [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate) zurückgegebenen Status bis zum Ende des aktuellen Bereichs ausgetauscht.

Probleme mit Ressourcen in DLLs treten auf, wenn das AFX_MODULE_STATE Makro nicht verwendet wird. Standardmäßig verwendet MFC das Ressourcenhandle der Hauptanwendung, um die Ressourcenvorlage zu laden. Diese Vorlage wird tatsächlich in der DLL gespeichert. Die Hauptursache ist, dass die Modulstatusinformationen von MFC nicht vom AFX_MODULE_STATE-Makro summiert wurden. Das Ressourcenhandle wird aus dem MFC-Modulstatus wiederhergestellt. Wenn Sie den Modulstatus nicht wechseln, wird das falsche Ressourcenhandle verwendet.

AFX_MODULE_STATE muss nicht in jede Funktion in der DLL eingesetzt werden. Beispielsweise kann `InitInstance` der MFC-Code in der Anwendung aufgerufen werden, ohne AFX_MODULE_STATE `InitInstance` da MFC `InitInstance` den Modulstatus automatisch vor verschiebt und ihn dann nach Rückgaben zurückschaltet. Dasselbe gilt für alle Nachrichtenzuordnungshandler. Normale MFC-DLLs verfügen tatsächlich über eine spezielle Masterfensterprozedur, die den Modulstatus automatisch wechselt, bevor eine Nachricht weiterleitet.

## <a name="process-local-data"></a>Verarbeiten lokaler Daten

Die Verarbeitung lokaler Daten wäre nicht so besorgniserregend, wenn es nicht um die Schwierigkeit des Win32s-DLL-Modells gegangen wäre. In Win32s teilen alle DLLs ihre globalen Daten, auch wenn sie von mehreren Anwendungen geladen werden. Dies unterscheidet sich stark vom "echten" Win32-DLL-Datenmodell, bei dem jede DLL in jedem Prozess, der an die DLL angefügt wird, eine separate Kopie ihres Datenraums erhält. Um die Komplexität zu erhöhen, sind Daten, die auf dem Heap in einer Win32s-DLL zugewiesen sind, in der Tat prozessspezifisch (zumindest was den Besitz betrifft). Berücksichtigen Sie die folgenden Daten und Codes:

```cpp
static CString strGlobal; // at file scope

__declspec(dllexport)
void SetGlobalString(LPCTSTR lpsz)
{
    strGlobal = lpsz;
}

__declspec(dllexport)
void GetGlobalString(LPCTSTR lpsz, size_t cb)
{
    StringCbCopy(lpsz, cb, strGlobal);
}
```

Überlegen Sie, was passiert, wenn sich der obige Code in einer DLL befindet und diese DLL von zwei Prozessen A und B geladen wird (es könnte sich in der Tat um zwei Instanzen derselben Anwendung handelt). Ein `SetGlobalString("Hello from A")`Anruf . Als Ergebnis wird Speicher für `CString` die Daten im Kontext von Prozess `CString` A zugewiesen. Beachten Sie, dass der selbst global ist und sowohl für A als auch für B sichtbar ist. Jetzt ruft `GetGlobalString(sz, sizeof(sz))`B an. B kann die von A eingestellten Daten sehen. Dies liegt daran, Win32s bietet keinen Schutz zwischen Prozessen wie Win32 tut. Das ist das erste Problem; In vielen Fällen ist es nicht wünschenswert, dass eine Anwendung globale Daten beeinflusst, die als Eigentum einer anderen Anwendung betrachtet werden.

Es gibt noch weitere Probleme. Nehmen wir an, Dass A jetzt austritt. Wenn A beendet wird, wird`strGlobal`der von der ' ' -Zeichenfolge verwendete Speicher für das System verfügbar gemacht, d. h., der gesamte Speicher, der von Prozess A zugewiesen wird, wird automatisch vom Betriebssystem freigegeben. Es wird nicht `CString` befreit, weil der Destruktor aufgerufen wird; es wurde noch nicht aufgerufen. Es wird freigegeben, nur weil die Anwendung, die sie zugewiesen hat, die Szene verlassen hat. Wenn B `GetGlobalString(sz, sizeof(sz))`aufgerufen hat, erhält es möglicherweise keine gültigen Daten. Eine andere Anwendung hat diesen Speicher möglicherweise für etwas anderes verwendet.

Es besteht eindeutig ein Problem. MFC 3.x verwendete eine Technik namens Thread-Local Storage (TLS). MFC 3.x würde einen TLS-Index zuweisen, der unter Win32s wirklich als prozesslokaler Speicherindex fungiert, obwohl er nicht als dieser bezeichnet wird, und dann auf alle Daten verweisen, die auf diesem TLS-Index basieren. Dies ähnelt dem TLS-Index, der zum Speichern von threadlokalen Daten auf Win32 verwendet wurde (weitere Informationen zu diesem Thema finden Sie weiter unten). Dies führte dazu, dass jede MFC-DLL mindestens zwei TLS-Indizes pro Prozess nutzte. Wenn Sie das Laden vieler OLE Control DLLs (OCXs) berücksichtigen, gehen die TLS-Indizes schnell aus (es sind nur 64 verfügbar). Darüber hinaus musste MFC all diese Daten an einem Ort, in einer einzigen Struktur, platzieren. Es war nicht sehr erweiterbar und war nicht ideal in Bezug auf seine Verwendung von TLS-Indizes.

MFC 4.x adressiert dies mit einer Reihe von Klassenvorlagen, die Sie um die Daten "umwickeln" können, die lokal verarbeitet werden sollen. Das oben erwähnte Problem könnte z. B. durch Schreiben behoben werden:

```cpp
struct CMyGlobalData : public CNoTrackObject
{
    CString strGlobal;
};
CProcessLocal<CMyGlobalData> globalData;

__declspec(dllexport)
void SetGlobalString(LPCTSTR lpsz)
{
    globalData->strGlobal = lpsz;
}

__declspec(dllexport)
void GetGlobalString(LPCTSTR lpsz, size_t cb)
{
    StringCbCopy(lpsz, cb, globalData->strGlobal);
}
```

MFC implementiert dies in zwei Schritten. Zunächst befindet sich eine Ebene über den Win32 __Tls-APIs\* __ (**TlsAlloc**, **TlsSetValue**, **TlsGetValue**usw.), die nur zwei TLS-Indizes pro Prozess verwenden, unabhängig davon, wie viele DLLs Sie haben. Zweitens wird `CProcessLocal` die Vorlage für den Zugriff auf diese Daten bereitgestellt. Es überschreibt Operator-> was die intuitive Syntax ermöglicht, die Sie oben sehen. Alle Objekte, die `CProcessLocal` von umschlossen werden, müssen von `CNoTrackObject`abgeleitet werden. `CNoTrackObject`bietet einen übergeordneten Allocator (**LocalAlloc**/**LocalFree**) und einen virtuellen Destruktor, sodass MFC die lokalen Prozessobjekte automatisch zerstören kann, wenn der Prozess beendet wird. Solche Objekte können einen benutzerdefinierten Destruktor haben, wenn eine zusätzliche Bereinigung erforderlich ist. Das obige Beispiel erfordert keines, da der Compiler einen Standarddestruktor generiert, um das eingebettete `CString` Objekt zu zerstören.

Dieser Ansatz hat weitere interessante Vorteile. Nicht nur `CProcessLocal` werden alle Objekte automatisch zerstört, sie werden erst konstruiert, wenn sie benötigt werden. `CProcessLocal::operator->`instanziiert das zugeordnete Objekt beim ersten Aufruf, und zwar nicht früher. Im obigen Beispiel bedeutet dies, dass die '`strGlobal`'-Zeichenfolge erst beim ersten Mal `SetGlobalString` erstellt oder `GetGlobalString` aufgerufen wird. In einigen Fällen kann dies dazu beitragen, die DLL-Startzeit zu verringern.

## <a name="thread-local-data"></a>Lokale Threaddaten

Ähnlich wie bei der Verarbeitung lokaler Daten werden lokale Threaddaten verwendet, wenn die Daten für einen bestimmten Thread lokal sein müssen. Das heißt, Sie benötigen für jeden Thread, der auf diese Daten zugreift, eine separate Instanz der Daten. Dies kann oft anstelle umfangreicher Synchronisationsmechanismen verwendet werden. Wenn die Daten nicht von mehreren Threads gemeinsam genutzt werden müssen, können solche Mechanismen teuer und unnötig sein. Angenommen, wir `CString` hatten ein Objekt (ähnlich wie das obige Beispiel). Wir können den Thread lokal umschließen, indem wir es mit einer `CThreadLocal` Vorlage umschließen:

```cpp
struct CMyThreadData : public CNoTrackObject
{
    CString strThread;
};
CThreadLocal<CMyThreadData> threadData;

void MakeRandomString()
{
    // a kind of card shuffle (not a great one)
    CString& str = threadData->strThread;
    str.Empty();
    while (str.GetLength() != 52)
    {
        unsigned int randomNumber;
        errno_t randErr;
        randErr = rand_s(&randomNumber);

        if (randErr == 0)
        {
            TCHAR ch = randomNumber % 52 + 1;
            if (str.Find(ch) <0)
            str += ch; // not found, add it
        }
    }
}
```

Wenn `MakeRandomString` von zwei verschiedenen Threads aufgerufen wurde, würde jeder die Zeichenfolge auf unterschiedliche Weise "mischen", ohne den anderen zu stören. Dies liegt daran, `strThread` dass es tatsächlich eine Instanz pro Thread anstelle nur einer globalen Instanz gibt.

Beachten Sie, wie ein `CString` Verweis verwendet wird, um die Adresse einmal statt einmal pro Schleifeniteration zu erfassen. Der Schleifencode hätte überall `threadData->strThread` geschrieben`str`werden können ' ' wird verwendet, aber der Code wäre viel langsamer in der Ausführung. Es ist am besten, einen Verweis auf die Daten zwischenzuspeichern, wenn solche Verweise in Schleifen auftreten.

Die `CThreadLocal` Klassenvorlage verwendet dieselben `CProcessLocal` Mechanismen wie und dieselben Implementierungstechniken.

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
