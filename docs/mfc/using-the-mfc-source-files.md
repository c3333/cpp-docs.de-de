---
title: Verwenden der MFC-Quelldateien
ms.date: 08/19/2019
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
ms.openlocfilehash: acd702f5a032f9dca3480d287142583070701e84
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231753"
---
# <a name="using-the-mfc-source-files"></a>Verwenden der MFC-Quelldateien

Die MFC-Bibliothek (Microsoft Foundation Class) stellt vollständigen Quellcode bereit. Header Dateien (. h) befinden sich im Verzeichnis " *\atlmfc\include* ". Implementierungs Dateien (cpp-Dateien) befinden sich im Verzeichnis *\atlmfc\src\mfc* .

In diesem Artikel werden die Konventionen erläutert, die MFC verwendet, um die verschiedenen Teile der einzelnen Klassen zu kommentieren, was diese Kommentare bedeuten und was Sie in den einzelnen Abschnitten erwarten sollten. Die Visual Studio-Assistenten verwenden ähnliche Konventionen für die Klassen, die Sie für Sie erstellen, und Sie werden diese Konventionen wahrscheinlich für Ihren eigenen Code nützlich finden.

Möglicherweise sind Sie mit den **`public`** **`protected`** **`private`** Schlüsselwörtern, und C++ vertraut. In den MFC-Header Dateien werden Sie feststellen, dass jede Klasse mehrere davon aufweisen kann. Beispielsweise können öffentliche Element Variablen und-Funktionen unter mehr als einem **`public`** Schlüsselwort liegen. Der Grund hierfür ist, dass MFC Element Variablen und-Funktionen abhängig von ihrer Verwendung trennt, nicht nach dem zulässigen Zugriffstyp. MFC verwendet **`private`** sparsam. Sogar Elemente, die als Implementierungsdetails angesehen werden, sind häufig **`protected`** und oft **`public`** . Obwohl der Zugriff auf die Implementierungsdetails nicht empfehlenswert ist, behält MFC die Entscheidung bei.

In den MFC-Quelldateien und den Header Dateien, die der MFC-Anwendungs-Assistent erstellt, finden Sie Kommentare wie diese innerhalb von Klassen Deklarationen (in der Regel in dieser Reihenfolge):

`// Constructors`

`// Attributes`

`// Operations`

`// Overridables`

`// Implementation`

## <a name="an-example-of-the-comments"></a><a name="an-example-of-the-comments"></a>Ein Beispiel für die Kommentare

In der folgenden partiellen Auflistung der-Klasse `CStdioFile` werden die meisten Standard Kommentare verwendet, die von MFC in seinen-Klassen verwendet werden, um Klassenmember nach den Verwendungsmöglichkeiten zu unterteilen:

```cpp
/*============================================================================*/
// STDIO file implementation

class CStdioFile : public CFile
{
    DECLARE_DYNAMIC(CStdioFile)

public:
// Constructors
    CStdioFile();

    // . . .

// Attributes
    FILE* m_pStream;    // stdio FILE
                        // m_hFile from base class is _fileno(m_pStream)

// Operations
    // reading and writing strings
    virtual void WriteString(LPCTSTR lpsz);
    virtual LPTSTR ReadString(_Out_writes_z_(nMax) LPTSTR lpsz, _In_ UINT nMax);
    virtual BOOL ReadString(CString& rString);

// Implementation
public:
    virtual ~CStdioFile();
#ifdef _DEBUG
    void Dump(CDumpContext& dc) const;
#endif
    virtual ULONGLONG GetPosition() const;
    virtual ULONGLONG GetLength() const;
    virtual BOOL Open(LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL);

    // . . .

protected:
    void CommonBaseInit(FILE* pOpenStream, CAtlTransactionManager* pTM);
    void CommonInit(LPCTSTR lpszFileName, UINT nOpenFlags, CAtlTransactionManager* pTM);
};
```

Diese Kommentare markieren konsistent Abschnitte der Klassen Deklaration, die ähnliche Arten von Klassenmembern enthalten. Denken Sie daran, dass es sich um MFC-Konventionen und nicht um festgelegte Regeln handelt.

## <a name="-constructors-comment"></a>Konstruktorkommentar

Der `// Constructors` -Abschnitt einer MFC-Klassen Deklaration deklariert Konstruktoren (in der C++ Sense) und alle Initialisierungs Funktionen, die erforderlich sind, um das-Objekt tatsächlich zu verwenden. Beispielsweise `CWnd::Create` befindet sich im Abschnitt Konstruktoren, weil Sie vor der Verwendung des- `CWnd` Objekts "vollständig konstruiert" sein muss, indem Sie zuerst den C++-Konstruktor aufrufen und dann die- `Create` Funktion aufrufen. In der Regel sind diese Mitglieder öffentlich.

Beispielsweise `CStdioFile` verfügt die-Klasse über fünf Konstruktoren, von denen eine in der Auflistung unter [einem Beispiel der Kommentare](#an-example-of-the-comments)angezeigt wird.

## <a name="-attributes-comment"></a>Attributekommentar

Der- `// Attributes` Abschnitt einer MFC-Klassen Deklaration enthält die öffentlichen Attribute (oder Eigenschaften) des-Objekts. In der Regel sind die Attribute Element Variablen oder Get/Set-Funktionen. Die "Get"-und "Set"-Funktionen können virtuell oder nicht virtuell sein. Die "Get"-Funktionen sind häufig **`const`** , da Sie in den meisten Fällen keine Nebeneffekte haben. Diese Member sind normalerweise öffentlich. Geschützte und private Attribute werden in der Regel im Implementierungs Abschnitt gefunden.

In der Beispiel Auflistung aus der-Klasse `CStdioFile` enthält die Liste unter [einem Beispiel der Kommentare](#an-example-of-the-comments)eine Member-Variable, *m_pStream*. Class `CDC` listet in diesem Kommentar fast 20 Member auf.

> [!NOTE]
> Große Klassen, wie z. b. `CDC` und `CWnd` , haben möglicherweise so viele Member, dass die einfache Auflistung aller Attribute in einer Gruppe nicht viel zur Übersichtlichkeit hinzufügt. In solchen Fällen verwendet die Klassenbibliothek andere Kommentare als Überschriften, um die Elemente weiter zu gliedern. Beispielsweise `CDC` verwendet `// Device-Context Functions` , `// Drawing Tool Functions` , `// Drawing Attribute Functions` und weitere. Gruppen, die Attribute darstellen, folgen der oben beschriebenen üblichen Syntax. Viele OLE-Klassen verfügen über einen Implementierungs Abschnitt mit dem Namen `// Interface Maps` .

## <a name="-operations-comment"></a>Vorgangs Kommentar

Der- `// Operations` Abschnitt einer MFC-Klassen Deklaration enthält Element Funktionen, die Sie für das-Objekt zum Ausführen von Aktionen oder zum Ausführen von Aktionen (Ausführen von Vorgängen) abrufen können. Diese Funktionen sind in der Regel nicht, **`const`** da Sie normalerweise Nebeneffekte haben. Sie sind möglicherweise virtuell oder nicht virtuell, abhängig von den Anforderungen der-Klasse. In der Regel sind diese Mitglieder öffentlich.

In der Beispiel Auflistung aus der-Klasse `CStdioFile` enthält die Liste in [einem Beispiel der Kommentare](#an-example-of-the-comments)drei Element Funktionen unter diesem Kommentar: `WriteString` und zwei über Ladungen von `ReadString` .

Wie bei Attributen können Vorgänge auch weiter unterteilt werden.

## <a name="-overridables-comment"></a>Overridables-Kommentar

Der- `// Overridables` Abschnitt einer MFC-Klassen Deklaration enthält virtuelle Funktionen, die Sie in einer abgeleiteten Klasse überschreiben können, wenn Sie das Verhalten der Basisklasse ändern müssen. Sie werden in der Regel mit "on" benannt, obwohl dies nicht unbedingt erforderlich ist. Funktionen können hier überschrieben werden und implementieren oft eine Art von "Rückruf" oder "Hook" oder stellen Sie bereit. In der Regel sind diese Member geschützt.

In MFC selbst werden reine virtuelle Funktionen immer in diesem Abschnitt platziert. Eine rein virtuelle Funktion in C++ hat folgendes Format:

`virtual void OnDraw( ) = 0;`

In der Beispiel Auflistung aus der-Klasse `CStdioFile` enthält die Liste in [einem Beispiel für die Kommentare](#an-example-of-the-comments)keinen Overridables-Abschnitt. Die Klasse hingegen `CDocument` Listet ungefähr 10 über schreibbare Element Funktionen auf.

In einigen Klassen wird möglicherweise auch der Kommentar angezeigt `// Advanced Overridables` . Diese Funktionen können nur von erweiterten Programmierern versucht werden zu überschreiben. Sie müssen Sie wahrscheinlich nie außer Kraft setzen.

> [!NOTE]
> Die in diesem Artikel beschriebenen Konventionen funktionieren im Allgemeinen auch für Automatisierungsmethoden und-Eigenschaften (früher als OLE-Automatisierung bezeichnet). Automatisierungsmethoden ähneln MFC-Vorgängen. Automatisierungs Eigenschaften ähneln MFC-Attributen. Automatisierungs Ereignisse (die für ActiveX-Steuerelemente unterstützt werden, früher als OLE-Steuerelemente bezeichnet) ähneln den über schreibbaren Member-Funktionen von MFC.

## <a name="-implementation-comment"></a>Implementierungs Kommentar

Der `// Implementation` Abschnitt ist der wichtigste Teil jeder MFC-Klassen Deklaration.

In diesem Abschnitt werden alle Implementierungsdetails erläutert. In diesem Abschnitt können sowohl Element Variablen als auch Element Funktionen angezeigt werden. Alles unterhalb dieser Zeile kann sich in einer zukünftigen Version von MFC ändern. Wenn Sie es nicht vermeiden können, sollten Sie sich unter der Zeile nicht auf die Details verlassen `// Implementation` . Außerdem werden Member, die unter der Implementierungs Zeile deklariert sind, nicht dokumentiert, obwohl einige Implementierungen in technischen Hinweisen erläutert werden. Über schreibungen virtueller Funktionen in der-Basisklasse befinden sich in diesem Abschnitt, unabhängig davon, in welchem Abschnitt die Basisklassen Funktion definiert ist. Wenn eine Funktion die Implementierung der Basisklasse überschreibt, wird Sie als Implementierungsdetail betrachtet. In der Regel sind diese Member geschützt, aber nicht immer.

In der `CStdioFile` Auflistung unter [einem Beispiel der Kommentare](#an-example-of-the-comments)können Member, die unterhalb des `// Implementation` Kommentars deklariert werden, als **`public`** , oder deklariert werden **`protected`** **`private`** . Verwenden Sie diese Member nur mit Vorsicht, da Sie sich in der Zukunft ändern können. Das Deklarieren einer Gruppe von Membern ist **`public`** möglicherweise erforderlich, damit die Implementierung der Klassenbibliothek ordnungsgemäß funktioniert. Dies bedeutet jedoch nicht, dass Sie die Member, die so deklariert sind, sicher verwenden können.

> [!NOTE]
> Möglicherweise finden Sie Kommentare der verbleibenden Typen entweder oberhalb oder unterhalb des `// Implementation` Kommentars. In beiden Fällen beschreiben Sie die Arten von Membern, die unter Ihnen deklariert werden. Wenn Sie unter dem `// Implementation` Kommentar auftreten, sollten Sie davon ausgehen, dass sich die Member in zukünftigen Versionen von MFC ändern können.

## <a name="see-also"></a>Weitere Informationen

[Allgemeine MFC-Themen](../mfc/general-mfc-topics.md)
