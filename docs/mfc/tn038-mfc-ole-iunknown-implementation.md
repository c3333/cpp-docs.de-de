---
title: 'TN038: MFC-OLE IUnknown-Implementierung'
ms.date: 06/28/2018
helpviewer_keywords:
- aggregation macros [MFC]
- COM interfaces, base interface
- IUnknown interface
- END_INTERFACE_MAP macro [MFC]
- TN038
- BEGIN_INTERFACE_PART macro [MFC]
- DECLARE_INTERFACE_MAP macro [MFC]
- BEGIN_INTERFACE_MAP macro [MFC]
- OLE [MFC], implementing IUnknown interface
- METHOD_PROLOGUE macro [MFC]
- STDMETHOD macro [MFC]
- END_INTERFACE_PART macro [MFC]
- INTERFACE_PART macro
ms.assetid: 19d946ba-beaf-4881-85c6-0b598d7f6f11
ms.openlocfilehash: 83166b32a20b8d24f748f85946caa01dbc76d4d0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230440"
---
# <a name="tn038-mfcole-iunknown-implementation"></a>TN038: Implementieren von MFC/OLE-IUnknown

> [!NOTE]
> Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

Das Herzstück von OLE 2 ist das "OLE-Component Object Model" oder COM. COM definiert einen Standard für die Kommunikation kooperierender Objekte miteinander. Dazu gehören Details zum Aussehen eines "Objekts", einschließlich wie Methoden in einem Objekt weitergeleitet werden. COM definiert auch eine Basisklasse, von der alle COM-kompatiblen Klassen abgeleitet werden. Diese Basisklasse ist [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown). Obwohl die [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) -Schnittstelle als C++-Klasse bezeichnet wird, ist com nicht spezifisch für eine Sprache – Sie kann in C, Pascal oder einer beliebigen anderen Sprache implementiert werden, die das binäre Layout eines COM-Objekts unterstützen kann.

OLE bezieht sich auf alle Klassen, die von [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) als "Schnittstellen" abgeleitet werden. Dies ist ein wichtiger Unterschied, da eine "Schnittstelle" wie [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) keine Implementierung enthält. Sie definiert einfach das Protokoll, über das Objekte kommunizieren, nicht die speziellen Aufgaben dieser Implementierungen. Dies ist für ein System, das maximale Flexibilität zulässt, sinnvoll. Es ist die Aufgabe von MFC, ein Standardverhalten für MFC-/C++-Programme zu implementieren.

Um die MFC-Implementierung von [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) zu verstehen, müssen Sie zunächst wissen, was diese Schnittstelle ist. Im folgenden ist eine vereinfachte Version von [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) definiert:

```cpp
class IUnknown
{
public:
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj) = 0;
    virtual ULONG AddRef() = 0;
    virtual ULONG Release() = 0;
};
```

> [!NOTE]
> Bestimmte erforderliche Details der Aufruf Konvention, z **`__stdcall`** . b., werden für diese Abbildung ausgelassen.

Die Funktionen für [adressf](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) und [releasemember](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) steuern die Speicherverwaltung des-Objekts. COM verwendet Verweiszählungsschema, um Objekte nachzuverfolgen. Auf ein Objekt wird nie direkt verwiesen wie in C++. Stattdessen wird auf COM-Objekte immer durch einen Zeiger verwiesen. Um das Objekt freizugeben, wenn der Besitzer es verwendet, wird der [releasemember](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) des Objekts aufgerufen (im Gegensatz zur Verwendung von Operator Delete, wie für ein herkömmliches C++-Objekt). Dank des Verweiszählmechanismus können mehrere Verweise auf ein einzelnes Objekt verwaltet werden. Eine Implementierung von [adressf](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) und [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) behält einen Verweis Zähler für das Objekt bei – das Objekt wird erst gelöscht, wenn der Verweis Zähler Null erreicht.

[Adressf](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) und [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) sind aus Implementierungs Sicht ziemlich unkompliziert. Im Folgenden wird eine einfache Implementierung veranschaulicht:

```cpp
ULONG CMyObj::AddRef()
{
    return ++m_dwRef;
}

ULONG CMyObj::Release()
{
    if (--m_dwRef == 0)
    {
        delete this;
        return 0;
    }
    return m_dwRef;
}
```

Die [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) -Member-Funktion ist ein wenig interessanter. Es ist nicht sehr interessant, ein Objekt zu verwenden, dessen einzige Member-Funktionen [adressf](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) und [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) sind – es wäre schön, das Objekt anzuweisen, mehr Dinge auszuführen, als [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) bereitstellt. Dies ist der Ort, an dem [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) nützlich ist. Sie ermöglicht Ihnen, eine andere "Schnittstelle" für dasselbe Objekt zu erhalten. Diese Schnittstellen werden normalerweise von [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) abgeleitet und fügen zusätzliche Funktionalität hinzu, indem neue Element Funktionen hinzugefügt werden. Für COM-Schnittstellen werden nie Membervariablen in der Schnittstelle deklariert, und alle Memberfunktionen werden als rein virtuell deklariert. Beispiel:

```cpp
class IPrintInterface : public IUnknown
{
public:
    virtual void PrintObject() = 0;
};
```

Um eine iprintinterface abzurufen, wenn Sie nur über ein [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)verfügen, können Sie [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) aufrufen, indem Sie den `IID` von verwenden `IPrintInterface` . Eine `IID` ist eine 128-Bit-Zahl, die die Schnittstelle eindeutig identifiziert. Für jede Schnittstelle gibt es eine `IID`, die entweder von Ihnen oder OLE definiert wird. Wenn *Punk* ein Zeiger auf ein [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) -Objekt ist, kann der Code zum Abrufen einer iprintinterface-Schnittstelle wie folgt lauten:

```cpp
IPrintInterface* pPrint = NULL;
if (pUnk->QueryInterface(IID_IPrintInterface, (void**)&pPrint) == NOERROR)
{
    pPrint->PrintObject();
    pPrint->Release();
    // release pointer obtained via QueryInterface
}
```

Das ist ziemlich einfach, aber wie wäre es, wenn Sie ein Objekt implementieren, das sowohl die iprintinterface-als auch die [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) -Schnittstelle unterstützt. in diesem Fall ist es einfach, da die iprintinterface direkt von [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) abgeleitet wird – durch Implementieren von iprintinterface, [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) wird automatisch unterstützt Beispiel:

```cpp
class CPrintObj : public CPrintInterface
{
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);
    virtual ULONG AddRef();
    virtual ULONG Release();
    virtual void PrintObject();
};
```

Die Implementierungen von [adressf](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) und [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) sind genau dieselben wie die oben implementierten. `CPrintObj::QueryInterface`sieht in etwa wie folgt aus:

```cpp
HRESULT CPrintObj::QueryInterface(REFIID iid, void FAR* FAR* ppvObj)
{
    if (iid == IID_IUnknown || iid == IID_IPrintInterface)
    {
        *ppvObj = this;
        AddRef();
        return NOERROR;
    }
    return E_NOINTERFACE;
}
```

Wenn der Schnittstellenbezeichner (IID) erkannt wird, wird ein Zeiger auf das Objekt zurückgegeben. Andernfalls tritt ein Fehler auf. Beachten Sie außerdem, dass eine erfolgreiche [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) zu einer impliziten [adressfolge](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)führt. Natürlich müssten Sie auch CEditObj::Print implementieren. Das ist einfach, da die iprintinterface direkt von der [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) -Schnittstelle abgeleitet wurde. Wenn Sie jedoch zwei verschiedene Schnittstellen unterstützen möchten, die beide von [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)abgeleitet sind, beachten Sie Folgendes:

```cpp
class IEditInterface : public IUnkown
{
public:
    virtual void EditObject() = 0;
};
```

Obwohl es mehrere Möglichkeiten gibt, eine Klasse zu implementieren, die IEditInterface und IPrintInterface unterstützt, einschließlich Verwenden der C++-Mehrfachvererbung, konzentriert sich dieser Hinweis auf die Verwendung von geschachtelten Klassen zur Implementierung dieser Funktionalität.

```cpp
class CEditPrintObj
{
public:
    CEditPrintObj();

    HRESULT QueryInterface(REFIID iid, void**);
    ULONG AddRef();
    ULONG Release();
    DWORD m_dwRef;

    class CPrintObj : public IPrintInterface
    {
    public:
        CEditPrintObj* m_pParent;
        virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);
        virtual ULONG AddRef();
        virtual ULONG Release();
    } m_printObj;

    class CEditObj : public IEditInterface
    {
    public:
        CEditPrintObj* m_pParent;
        virtual ULONG QueryInterface(REFIID iid, void** ppvObj);
        virtual ULONG AddRef();
        virtual ULONG Release();
    } m_editObj;
};
```

Die gesamte Implementierung wird unten aufgeführt:

```cpp
CEditPrintObj::CEditPrintObj()
{
    m_editObj.m_pParent = this;
    m_printObj.m_pParent = this;
}

ULONG CEditPrintObj::AddRef()
{
    return ++m_dwRef;
}

CEditPrintObj::Release()
{
    if (--m_dwRef == 0)
    {
        delete this;
        return 0;
    }
    return m_dwRef;
}

HRESULT CEditPrintObj::QueryInterface(REFIID iid, void** ppvObj)
{
    if (iid == IID_IUnknown || iid == IID_IPrintInterface)
    {
        *ppvObj = &m_printObj;
        AddRef();
        return NOERROR;
    }
    else if (iid == IID_IEditInterface)
    {
        *ppvObj = &m_editObj;
        AddRef();
        return NOERROR;
    }
    return E_NOINTERFACE;
}

ULONG CEditPrintObj::CEditObj::AddRef()
{
    return m_pParent->AddRef();
}

ULONG CEditPrintObj::CEditObj::Release()
{
    return m_pParent->Release();
}

HRESULT CEditPrintObj::CEditObj::QueryInterface(REFIID iid, void** ppvObj)
{
    return m_pParent->QueryInterface(iid, ppvObj);
}

ULONG CEditPrintObj::CPrintObj::AddRef()
{
    return m_pParent->AddRef();
}

ULONG CEditPrintObj::CPrintObj::Release()
{
    return m_pParent->Release();
}

HRESULT CEditPrintObj::CPrintObj::QueryInterface(REFIID iid, void** ppvObj)
{
    return m_pParent->QueryInterface(iid, ppvObj);
}
```

Beachten Sie, dass der größte Teil der [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) -Implementierung in der ceditprintobj-Klasse platziert wird, anstatt den Code in ceditprintobj:: ceditobj und ceditprintobj:: cprintobj zu duplizieren. So wird die Codemenge reduziert und Fehler vermieden. Der wichtigste Punkt hierbei ist, dass von der IUnknown-Schnittstelle [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) aufgerufen werden kann, um eine beliebige Schnittstelle abzurufen, die vom Objekt unterstützt wird, und aus jeder dieser Schnittstellen ist es möglich, das gleiche zu tun. Dies bedeutet, dass alle [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) -Funktionen, die für jede Schnittstelle verfügbar sind, sich genau auf dieselbe Weise Verhalten müssen. Damit diese eingebetteten Objekte die Implementierung im "äußeren Objekt" aufrufen kann, wird ein Gegenzeiger verwendet (m_pParent). Der m_pParent-Zeiger wird während des CEditPrintObj-Konstruktors initialisiert. Anschließend würden Sie CEditPrintObj::CPrintObj::PrintObject und CEditPrintObj::CEditObj::EditObject ebenfalls implementieren. Es wurde relativ viel Code für eine Funktion, die Fähigkeit zum Bearbeiten des Objekts, hinzugefügt. Glücklicherweise ist es recht selten, dass Schnittstellen nur über eine einzelne Memberfunktion verfügen (es kann jedoch durchaus vorkommen) und in diesem Fall würden EditObject und PrintObject normalerweise zu einer einzelnen Schnittstelle kombiniert werden.

Das ist eine umfassende Erläuterung und viel Code für ein solch einfaches Szenario. Die MFC/OLE-Klassen stellen eine einfachere Alternative zur Verfügung. Die MFC-Implementierung verwendet eine Technik, die mit der Methode vergleichbar ist, mit der Windows-Meldungen mit Meldungszuordnungen umschlossen werden. Diese Funktion wird als *Schnittstellen* Zuordnungen bezeichnet und wird im nächsten Abschnitt erläutert.

## <a name="mfc-interface-maps"></a>MFC-Schnittstellenzuordnungen

MFC/OLE beinhaltet die Implementierung von "Schnittstellenzuordnungen", die in Bezug auf Konzept und in der Ausführung den "Meldungszuordnungen" und "Dispatchzuordnungen" von MFC ähneln. Die Kernfunktionen der Schnittstellenzuordnungen von MFC sind folgende:

- Eine Standard Implementierung von [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown), die in die-Klasse integriert ist `CCmdTarget` .

- Wartung des Verweis zählungs, geändert durch die [adressf](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) und die [Freigabe](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)

- Datengestützte Implementierung von [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))

Außerdem unterstützen Schnittstellenzuordnungen die folgenden erweiterten Funktionen:

- Unterstützung für das Erstellen von aggregatfähigen COM-Objekten

- Unterstützung für das Verwenden von aggregierten Objekten in der Implementierung eines COM-Objekts

- Die Implementierung ist "hookable" und erweiterbar

Weitere Informationen zur Aggregation finden Sie im Thema [Aggregation](/windows/win32/com/aggregation) .

Die Unterstützung der Schnittstellenzuordnung von MFC haben ihren Stammpfad in der `CCmdTarget`-Klasse. `CCmdTarget`der Verweis Zähler "*has-a*" und alle der [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) -Implementierung zugeordneten Element Funktionen (z. b. der Verweis Zähler in `CCmdTarget` ). Um eine Klasse zu erstellen, die OLE-COM unterstützt, leiten Sie eine Klasse von `CCmdTarget` ab, und verwenden Sie verschiedene Makros sowie Memberfunktionen von `CCmdTarget`, um die gewünschten Schnittstellen zu implementieren. Die Implementierung von MFC verwendet geschachtelte Klassen, um die jeweilige Schnittstellenimplementierung ähnlich wie im Beispiel oben zu definieren. Dies wird mit einer Standardimplementierung von IUnknown sowie mit einer Reihe von Makros erleichtert, durch die ein Teil des sich wiederholenden Codes entfällt.

## <a name="interface-map-basics"></a>Grundlagen zu Schnittstellenzuordnungen

### <a name="to-implement-a-class-using-mfcs-interface-maps"></a>So implementieren Sie eine Klasse mithilfe der Schnittstellenzuordnungen von MFC

1. Leiten Sie eine Klasse entweder direkt oder indirekt von `CCmdTarget` ab.

2. Verwenden Sie die `DECLARE_INTERFACE_MAP`-Function in der abgeleiteten Klassendefinition.

3. Verwenden Sie für jede Schnittstelle, die Sie unterstützen möchten, die Makros BEGIN_INTERFACE_PART und END_INTERFACE_PART in der Klassendefinition.

4. Verwenden Sie in der Implementierungs Datei die Makros BEGIN_INTERFACE_MAP und END_INTERFACE_MAP, um die Schnittstellen Zuordnung der Klasse zu definieren.

5. Verwenden Sie für jede unterstützte IID das INTERFACE_PART-Makro zwischen den BEGIN_INTERFACE_MAP-und END_INTERFACE_MAP-Makros, um die IID einem bestimmten "Teil" der Klasse zuzuordnen.

6. Implementieren Sie die geschachtelten Klassen, die die von Ihnen unterstützten Schnittstellen darstellen.

7. Verwenden Sie das METHOD_PROLOGUE-Makro, um auf das übergeordnete, von `CCmdTarget` abgeleitete Objekt zuzugreifen.

8. [Adressf](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)und [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) können an die `CCmdTarget` Implementierung dieser Funktionen delegieren ( `ExternalAddRef` , `ExternalRelease` und `ExternalQueryInterface` ).

Das obige CPrintEditObj-Beispiel kann implementiert wie folgt werden:

```cpp
class CPrintEditObj : public CCmdTarget
{
public:
    // member data and member functions for CPrintEditObj go here

// Interface Maps
protected:
    DECLARE_INTERFACE_MAP()

    BEGIN_INTERFACE_PART(EditObj, IEditInterface)
        STDMETHOD_(void, EditObject)();
    END_INTERFACE_PART(EditObj)

    BEGIN_INTERFACE_PART(PrintObj, IPrintInterface)
        STDMETHOD_(void, PrintObject)();
    END_INTERFACE_PART(PrintObj)
};
```

Die obige Deklaration erstellt eine Klasse, die von `CCmdTarget` abgeleitet wird. Das DECLARE_INTERFACE_MAP-Makro weist das Framework an, dass diese Klasse über eine benutzerdefinierte Schnittstellen Zuordnung verfügt. Außerdem definieren die Makros "BEGIN_INTERFACE_PART" und "END_INTERFACE_PART" Klassen, die in diesem Fall die Namen "ceditobj" und "cprintobj" enthalten. (das X wird nur zur Unterscheidung der in der Tabelle verwendeten Klassen von globalen Klassen verwendet, die mit "C" beginnen, und Schnittstellen Klassen, die mit "I" beginnen). Zwei geschachtelte Member dieser Klassen werden erstellt: m_CEditObj bzw. m_CPrintObj. Die Makros deklarieren automatisch die Funktionen " [adressf](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)", " [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)" und " [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) ". Daher deklarieren Sie nur die Funktionen, die für diese Schnittstelle spezifisch sind: editobject und PrintObject (das OLE-Makro STDMETHOD wird verwendet, sodass **_stdcall** und virtuelle Schlüsselwörter entsprechend für die Zielplattform bereitgestellt werden).

So implementieren Sie Schnittstellenzuordnung für diese Klasse:

```cpp
BEGIN_INTERFACE_MAP(CPrintEditObj, CCmdTarget)
    INTERFACE_PART(CPrintEditObj, IID_IPrintInterface, PrintObj)
    INTERFACE_PART(CPrintEditObj, IID_IEditInterface, EditObj)
END_INTERFACE_MAP()
```

Damit wird die IID "IID_IPrintInterface" mit "m_CPrintObj" und "IID_IEditInterface" mit "m_CEditObj" verbunden. Die `CCmdTarget` Implementierung von [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) ( `CCmdTarget::ExternalQueryInterface` ) verwendet diese Zuordnung, um Zeiger auf m_CPrintObj und m_CEditObj zurückzugeben, wenn dies angefordert wird. Es ist nicht erforderlich, einen Eintrag für `IID_IUnknown` einzuschließen. Das Framework verwendet die erste Schnittstelle in der Zuordnung (in diesem Fall "m_CPrintObj"), wenn `IID_IUnknown` angefordert wird.

Obwohl das BEGIN_INTERFACE_PART-Makro die [adressf](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)-, [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) -und [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) -Funktionen für Sie automatisch deklariert hat, müssen Sie Sie dennoch implementieren:

```cpp
ULONG FAR EXPORT CEditPrintObj::XEditObj::AddRef()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return pThis->ExternalAddRef();
}

ULONG FAR EXPORT CEditPrintObj::XEditObj::Release()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return pThis->ExternalRelease();
}

HRESULT FAR EXPORT CEditPrintObj::XEditObj::QueryInterface(
    REFIID iid,
    void FAR* FAR* ppvObj)
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return (HRESULT)pThis->ExternalQueryInterface(&iid, ppvObj);
}

void FAR EXPORT CEditPrintObj::XEditObj::EditObject()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    // code to "Edit" the object, whatever that means...
}
```

Die Implementierung für CEditPrintObj::CPrintObj entspricht weitgehend den oben beschriebenen Definitionen für CEditPrintObj::CEditObj. Obwohl es möglich wäre, ein Makro zu erstellen, mit dem diese Funktionen automatisch generiert werden (was am Anfang der MFC/OLE-Entwicklung der Fall war), wird es schwierig, Haltepunkte festzulegen, wenn ein Makro mehrere Codezeilen generiert. Aus diesem Grund wird dieser Code manuell erweitert.

Durch Verwendung der Frameworkimplementierung von Meldungszuordnungen mussten einige Vorgänge nicht ausgeführt werden:

- Implementieren von QueryInterface

- Implementieren von AddRef und Release

- Deklarieren eine dieser integrierten Methoden auf beiden Schnittstellen

Darüber hinaus verwendet das Framework Meldungszuordnungen intern. So können Sie aus einer Frameworkklasse ableiten, beispielsweise `COleServerDoc`, die bereits bestimmte Schnittstellen unterstützt und entweder Ersatz oder Hinzufügungen zu den Schnittstellen bereitstellt, die im Framework enthalten sind. Dies ist möglich, da das Framework das Erben einer Schnittstellenzuordnung von einer Basisklasse vollständig unterstützt. Dies ist der Grund, warum BEGIN_INTERFACE_MAP als zweiten Parameter den Namen der Basisklasse annimmt.

> [!NOTE]
> Es ist im Allgemeinen nicht möglich, die Implementierung der integrierten MFC-Implementierungen der OLE-Schnittstellen nur durch Vererben der eingebetteten Spezialisierung dieser Schnittstelle von der MFC-Version wiederzuverwenden. Dies ist nicht möglich, da durch die Verwendung des METHOD_PROLOGUE-Makros zum Abrufen des Zugriffs auf das enthaltende `CCmdTarget` abgeleitete Objekt ein *fester Offset* des eingebetteten Objekts aus dem von `CCmdTarget` abgeleiteten Objekt impliziert wird. Dies bedeutet z. B., dass Sie kein eingebettetes XMyAdviseSink von der MFC-Implementierung in `COleClientItem::XAdviseSink` ableiten können, da XAdviseSink sich an einem bestimmten Offset oben im `COleClientItem`-Objekt befinden muss.

> [!NOTE]
> Sie können alle Funktionen, für die das Standardverhalten von MFC gelten soll, jedoch an die MFC-Implementierung delegieren. Dies wird in der MFC-Implementierung von `IOleInPlaceFrame` (XOleInPlaceFrame) in der `COleFrameHook`-Klasse ausgeführt (sie delegiert viele Funktionen zu m_xOleInPlaceUIWindow). Dieser Entwurf wurde ausgewählt, um die Laufzeitgröße von Objekten zu reduzieren, die viele Schnittstellen implementieren. Mit diesem Entwurf ist kein Gegenzeiger mehr erforderlich (wie bei Verwendung von m_pParent im vorherigen Abschnitt).

### <a name="aggregation-and-interface-maps"></a>Aggregation und Schnittstellenzuordnungen

Zusätzlich zur Unterstützung von eigenständigen COM-Objekten unterstützt MFC auch Aggregation. Die Aggregation selbst ist zu komplex und kann hier nicht erörtert werden. Weitere Informationen zur Aggregation finden Sie im Thema [Aggregation](/windows/win32/com/aggregation) . Dieser Hinweis beschreibt einfach die Unterstützung für die Aggregation, die in den Framework und die Schnittstellenzuordnungen integriert ist.

Es gibt zwei Möglichkeiten, Aggregation zu verwenden: (1) mit einem COM-Objekt, das Aggregation unterstützt und (2) durch Implementierung eines Objekts, von einem anderen aggregiert werden kann. Diese Funktionen können als "Verwenden eines Aggregatobjekts" und "Ausstatten einer Objekt-Implementierung mit Aggregatfähigkeit" bezeichnet werden. MFC unterstützt beide Funktionen.

### <a name="using-an-aggregate-object"></a>Verwenden eines Aggregatobjekts

Zur Verwendung eines Aggregatobjekts, muss es eine Methode geben, um das Aggregat in den QueryInterface-Mechanismus einzubinden. Das heißt, das Aggregatobjekt muss sich wie ein systemeigener Teil des Objekts verhalten. Wie funktioniert das in den MFC-Schnittstellen Zuordnungs Mechanismus, zusätzlich zum INTERFACE_PART-Makro, bei dem ein gespeichertes Objekt einer IID zugeordnet ist, können Sie auch ein Aggregat Objekt als Teil ihrer `CCmdTarget` abgeleiteten Klasse deklarieren. Zu diesem Zweck wird das INTERFACE_AGGREGATE-Makro verwendet. Auf diese Weise können Sie eine Member-Variable angeben (bei der es sich um einen Zeiger auf eine [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) -Klasse oder eine abgeleitete Klasse handeln muss), die in den Schnittstellen Zuordnungs Mechanismus integriert werden soll. Wenn der Zeiger nicht NULL ist `CCmdTarget::ExternalQueryInterface` , wenn aufgerufen wird, ruft das Framework automatisch die [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) -Member-Funktion des Aggregat Objekts auf, wenn die `IID` angeforderte nicht eine der nativen, `IID` von dem Objekt selbst unterstützten s ist `CCmdTarget` .

#### <a name="to-use-the-interface_aggregate-macro"></a>So verwenden Sie das INTERFACE_AGGREGATE-Makro

1. Deklarieren Sie eine Membervariable (`IUnknown*`), die einen Zeiger auf das Aggregatobjekt enthält.

2. Fügen Sie ein INTERFACE_AGGREGATE-Makro in ihre Schnittstellen Zuordnung ein, das auf die Element Variable anhand des Namens verweist.

3. Daraufhin (normalerweise während `CCmdTarget::OnCreateAggregates`) initialisieren Sie die Membervariable auf einen anderen Wert als NULL.

Beispiel:

```cpp
class CAggrExample : public CCmdTarget
{
public:
    CAggrExample();

protected:
    LPUNKNOWN m_lpAggrInner;
    virtual BOOL OnCreateAggregates();

    DECLARE_INTERFACE_MAP()
    // "native" interface part macros may be used here
};

CAggrExample::CAggrExample()
{
    m_lpAggrInner = NULL;
}

BOOL CAggrExample::OnCreateAggregates()
{
    // wire up aggregate with correct controlling unknown
    m_lpAggrInner = CoCreateInstance(CLSID_Example,
        GetControllingUnknown(), CLSCTX_INPROC_SERVER,
        IID_IUnknown, (LPVOID*)&m_lpAggrInner);

    if (m_lpAggrInner == NULL)
        return FALSE;
    // optionally, create other aggregate objects here
    return TRUE;
}

BEGIN_INTERFACE_MAP(CAggrExample, CCmdTarget)
    // native "INTERFACE_PART" entries go here
    INTERFACE_AGGREGATE(CAggrExample, m_lpAggrInner)
END_INTERFACE_MAP()
```

Die m_lpAggrInner-Variable wird im Konstruktor auf NULL initialisiert. Das Framework ignoriert eine Null-Member-Variable in der Standard Implementierung von [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)). Das `OnCreateAggregates`-Objekt eignet sich gut, um die Aggregatobjekte tatsächlich zu erstellen. Sie müssen dieses Objekt explizit aufrufen, wenn Sie das Objekt außerhalb der MFC-Implementierung von `COleObjectFactory` erstellen. Der Grund für das Erstellen von Aggregaten in `CCmdTarget::OnCreateAggregates` und die Verwendung von `CCmdTarget::GetControllingUnknown` wird offensichtlich, wenn das Erstellen von aggregatfähigen Objekten erläutert wird.

Mit dieser Methode erhält das Objekt alle Schnittstellen, die das Aggregatobjekt unterstützt, sowie deren systemeigene Schnittstellen. Wenn Sie nur eine Teilmenge der Schnittstellen benötigen, die das Aggregat unterstützt, können Sie `CCmdTarget::GetInterfaceHook` überschreiben. Dies ermöglicht eine sehr niedrige hookability, ähnlich wie bei [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)). Normalerweise werden alle Schnittstellen gewünscht, die das Aggregat unterstützt.

### <a name="making-an-object-implementation-aggregatable"></a>Ausstatten einer Objekt-Implementierung mit Aggregationsfähigkeit

Damit ein Objekt aggregierbar ist, muss die Implementierung von [adressf](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)und [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) an ein "kontrollierendes unbekanntes" delegiert werden. Anders ausgedrückt: damit es Teil des Objekts ist, muss es die [adressf](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)und [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) an ein anderes Objekt delegieren, das auch von [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)abgeleitet ist. Dieses "controlling unknown"-Objekt wird dem Objekt beim Erstellen zur Verfügung gestellt, d. h., es wird der Implementierung von `COleObjectFactory` bereitgestellt. Das Implementieren bedeutet einen geringen Mehraufwand, und in einigen Fällen ist es nicht wünschenswert, sodass dies laut MFC optional ist. Um ein Objekt aggregatfähig zu machen, rufen Sie `CCmdTarget::EnableAggregation` im Konstruktor des Objekts auf.

Wenn das Objekt auch Aggregate verwendet, müssen Sie zudem sicherstellen, das richtige "controlling unknown"-Objekt an die Aggregatobjekte zu übergeben. Normalerweise wird dieser [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) -Zeiger beim Erstellen des Aggregats an das-Objekt übermittelt. Beispielsweise ist der pUnkOuter-Parameter der "controlling unknown"-Zeiger für Objekte, die mit `CoCreateInstance` erstellt werden. Der richtige "controlling unknown"-Zeiger kann durch Aufrufen von `CCmdTarget::GetControllingUnknown` abgerufen werden. Der Wert, der von dieser Funktion zurückgegeben wird, ist jedoch während des Konstruktors ungültig. Aus diesem Grund wird vorgeschlagen, die Aggregate nur in einer Überschreibung von `CCmdTarget::OnCreateAggregates` zu erstellen, bei der der Rückgabewert von `GetControllingUnknown` zuverlässig ist, auch wenn er von der `COleObjectFactory`-Implementierung erstellt wird.

Wichtig ist auch, dass das Objekt den richtigen Verweiszähler bearbeitet, wenn künstliche Verweiszähler hinzugefügt oder freigegeben werden. Um dies sicherzustellen, rufen Sie immer `ExternalAddRef` und `ExternalRelease` statt `InternalRelease` und `InternalAddRef` auf. Es passiert nur selten, dass `InternalRelease` oder `InternalAddRef` für eine Klasse aufgerufen werden, die Aggregation unterstützt.

## <a name="reference-material"></a>Referenzmaterial

Die erweiterte Verwendung von OLE, wie Definieren eigener Schnittstellen oder Überschreiben der Implementierung des Frameworks der OLE-Schnittstellen, erfordert die Nutzung des zugrunde liegenden Schnittstellenzuordnungsmechanismus.

In diesem Abschnitt werden alle Makros und APIs erläutert, die zum Implementieren dieser erweiterten Funktionen verwendet werden.

### <a name="ccmdtargetenableaggregation--function-description"></a>CCmdTarget::EnableAggregation – Funktionsbeschreibung

```cpp
void EnableAggregation();
```

#### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion im Konstruktor der abgeleiteten Klasse auf, wenn Sie OLE-Aggregation für Objekte dieses Typs unterstützen möchten. Dadurch wird eine besondere IUnknown-Implementierung vorbereitet, die für aggregatfähige Objekte erforderlich ist.

### <a name="ccmdtargetexternalqueryinterface--function-description"></a>CCmdTarget::ExternalQueryInterface – Funktionsbeschreibung

```cpp
DWORD ExternalQueryInterface(
    const void FAR* lpIID,
    LPVOIDFAR* ppvObj
);
```

#### <a name="parameters"></a>Parameter

*lpIID*<br/>
Ein ferner Zeiger auf eine IID (das erste Argument für QueryInterface)

*ppvObj*<br/>
Ein Zeiger auf ein IUnknown*-Objekt (das zweite Argument für QueryInterface)

#### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion in der Implementierung von IUnknown für jede Schnittstelle auf, die Ihre Klasse implementiert. Diese Funktion stellt die datengesteuerte Standardimplementierung von QueryInterface auf Grundlage der Schnittstellenzuordnung des Objekts bereit. Es ist erforderlich, den Rückgabewert in ein HRESULT umzuwandeln. Wenn das Objekt aggregiert wird, ruft diese Funktion das "controlling IUnknown"-Objekt auf, anstatt die lokale Schnittstellenzuordnung zu verwenden.

### <a name="ccmdtargetexternaladdref--function-description"></a>CCmdTarget::ExternalAddRef – Funktionsbeschreibung

```cpp
DWORD ExternalAddRef();
```

#### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion in der Implementierung von IUnknown::AddRef für jede Schnittstelle auf, die Ihre Klasse implementiert. Der Rückgabewert ist der neue Verweiszähler für das CCmdTarget-Objekt. Wenn das Objekt aggregiert wird, ruft diese Funktion das "controlling IUnknown"-Objekt auf, anstatt den lokalen Verweiszähler zu bearbeiten.

### <a name="ccmdtargetexternalrelease--function-description"></a>CCmdTarget::ExternalRelease – Funktionsbeschreibung

```cpp
DWORD ExternalRelease();
```

#### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion in der Implementierung von IUnknown::Release für jede Schnittstelle auf, die Ihre Klasse implementiert. Der Rückgabewert gibt den neuen Verweiszähler für das Objekt an. Wenn das Objekt aggregiert wird, ruft diese Funktion das "controlling IUnknown"-Objekt auf, anstatt den lokalen Verweiszähler zu bearbeiten.

### <a name="declare_interface_map--macro-description"></a>DECLARE_INTERFACE_MAP – Makrobeschreibung

```cpp
DECLARE_INTERFACE_MAP
```

#### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro in einer Klasse, die von `CCmdTarget` abgeleitet ist und über eine Schnittstellenzuordnung verfügt. Wird auf die gleiche Weise wie DECLARE_MESSAGE_MAP verwendet. Dieser Makroaufruf sollte in die Klassendefinition, normalerweise in einer Headerdatei (.H), platziert werden. Eine Klasse mit DECLARE_INTERFACE_MAP muss die Schnittstellen Zuordnung in der Implementierungs Datei () definieren. Cpp) mit den BEGIN_INTERFACE_MAP-und END_INTERFACE_MAP-Makros.

### <a name="begin_interface_part-and-end_interface_part--macro-descriptions"></a>BEGIN_INTERFACE_PART und END_INTERFACE_PART – Makrobeschreibungen

```cpp
BEGIN_INTERFACE_PART(localClass, iface);
END_INTERFACE_PART(localClass)
```

#### <a name="parameters"></a>Parameter

*localclass*<br/>
Der Name der Klasse, die die Schnittstelle implementiert

*iface*<br/>
Der Name der Schnittstelle, die diese Klasse implementiert

#### <a name="remarks"></a>Bemerkungen

Für jede Schnittstelle, die von der Klasse implementiert wird, benötigen Sie eine BEGIN_INTERFACE_PART und END_INTERFACE_PART Paar. Diese Makros definieren eine lokale Klasse, die von der von Ihnen definierten OLE-Schnittstelle abgeleitet wird, sowie eine eingebettete Membervariable dieser Klasse. Die Member " [adressf](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)", " [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)" und " [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) " werden automatisch deklariert. Sie müssen die Deklarationen für die anderen Element Funktionen einschließen, die Teil der implementierten Schnittstelle sind (diese Deklarationen werden zwischen den BEGIN_INTERFACE_PART-und END_INTERFACE_PART-Makros platziert).

Das *iface* -Argument ist die OLE-Schnittstelle, die Sie implementieren möchten, z `IAdviseSink` `IPersistStorage` . b. oder (oder Ihre eigene benutzerdefinierte Schnittstelle).

Das *localclass* -Argument ist der Name der lokalen Klasse, die definiert wird. Der Buchstabe "x" wird dem Namen automatisch vorangestellt. Diese Namenskonvention wird verwendet, um Konflikte mit gleichnamigen globalen Klassen zu vermeiden. Außerdem ist der Name des eingebetteten Members identisch mit dem Namen der *localclass* , mit dem Unterschied, dass er "m_x" vorangestellt ist.

Beispiel:

```cpp
BEGIN_INTERFACE_PART(MyAdviseSink, IAdviseSink)
    STDMETHOD_(void, OnDataChange)(LPFORMATETC, LPSTGMEDIUM);
    STDMETHOD_(void, OnViewChange)(DWORD, LONG);
    STDMETHOD_(void, OnRename)(LPMONIKER);
    STDMETHOD_(void, OnSave)();
    STDMETHOD_(void, OnClose)();
END_INTERFACE_PART(MyAdviseSink)
```

würde eine lokale Klasse mit dem Namen XMyAdviseSink definieren, der von IAdviseSink abgeleitet wurde, und ein Member der Klasse, in der es als m_xMyAdviseSink.Note deklariert wird:

> [!NOTE]
> Die Zeilen, die mit _ beginnen, `STDMETHOD` werden im Wesentlichen aus OLE2 kopiert. H und leicht geändert. Durch Kopieren aus OLE2.H lassen sich Fehler reduzieren, die andernfalls schwer zu beheben sind.

### <a name="begin_interface_map-and-end_interface_map--macro-descriptions"></a>BEGIN_INTERFACE_MAP und END_INTERFACE_MAP – Makrobeschreibungen

```cpp
BEGIN_INTERFACE_MAP(theClass, baseClass)
END_INTERFACE_MAP
```

#### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Die Klasse, in der die Schnittstellenzuordnung definiert werden soll

*BaseClass*<br/>
Die Klasse, von der *TheClass* abgeleitet ist.

#### <a name="remarks"></a>Bemerkungen

Die BEGIN_INTERFACE_MAP-und END_INTERFACE_MAP-Makros werden in der Implementierungs Datei verwendet, um die Schnittstellen Zuordnung tatsächlich zu definieren. Für jede Schnittstelle, die implementiert wird, ist mindestens ein INTERFACE_PART Makro Aufruf vorhanden. Für jedes Aggregat, das von der-Klasse verwendet wird, gibt es einen INTERFACE_AGGREGATE Makro Aufruf.

### <a name="interface_part--macro-description"></a>INTERFACE_PART – Makrobeschreibung

```cpp
INTERFACE_PART(theClass, iid, localClass)
```

#### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Der Name der Klasse, die die Schnittstellenzuordnung enthält.

*IID*<br/>
Die `IID`, die der eingebetteten Klasse zugeordnet werden soll.

*localclass*<br/>
Der Name der lokalen Klasse (ohne das "X").

#### <a name="remarks"></a>Bemerkungen

Dieses Makro wird zwischen dem BEGIN_INTERFACE_MAP-Makro und dem END_INTERFACE_MAP-Makro für jede Schnittstelle verwendet, die von Ihrem Objekt unterstützt wird. Sie ermöglicht es Ihnen, eine IID einem Member der Klasse zuzuordnen, die von *TheClass* und *localclass*angegeben wird. Das "m_x" wird der *localclass* automatisch hinzugefügt. Beachten Sie, dass maximal eine `IID` mit einem einzigen Member zugeordnet werden kann. Dies ist hilfreich, wenn Sie nur eine "am stärksten abgeleitete" Schnittstelle implementieren und alle Zwischenschnittstellen ebenfalls bereitstellen möchten. Ein gutes Beispiel hierfür ist die `IOleInPlaceFrameWindow`-Schnittstelle. Die Hierarchie sieht wie folgt aus:

```Hierarchy
IUnknown
    IOleWindow
        IOleUIWindow
            IOleInPlaceFrameWindow
```

Wenn ein Objekt implementiert `IOleInPlaceFrameWindow` , kann ein Client eine `QueryInterface` der folgenden Schnittstellen haben: `IOleUIWindow` , `IOleWindow` oder [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown), neben der "am stärksten abgeleiteten" Schnittstelle `IOleInPlaceFrameWindow` (der, den Sie tatsächlich implementieren). Um dies zu umgehen, können Sie mehr als ein INTERFACE_PART Makro verwenden, um jede und jede Basisschnittstelle der-Schnittstelle zuzuordnen `IOleInPlaceFrameWindow` :

in der Klassendefinitionsdatei:

```cpp
BEGIN_INTERFACE_PART(CMyFrameWindow, IOleInPlaceFrameWindow)
```

in der Klassenimplementierungsdatei:

```cpp
BEGIN_INTERFACE_MAP(CMyWnd, CFrameWnd)
    INTERFACE_PART(CMyWnd, IID_IOleWindow, MyFrameWindow)
    INTERFACE_PART(CMyWnd, IID_IOleUIWindow, MyFrameWindow)
    INTERFACE_PART(CMyWnd, IID_IOleInPlaceFrameWindow, MyFrameWindow)
END_INTERFACE_MAP
```

Das Framework berücksichtigt IUnknown, da es immer erforderlich ist.

### <a name="interface_part--macro-description"></a>INTERFACE_PART – Makrobeschreibung

```cpp
INTERFACE_AGGREGATE(theClass, theAggr)
```

#### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Der Name der Klasse, die die Schnittstellenzuordnung enthält,

*der Aggr*<br/>
Der Name der Membervariable, die aggregiert werden soll.

#### <a name="remarks"></a>Bemerkungen

Dieses Makro wird verwendet, um dem Framework mitzuteilen, dass die Klasse ein Aggregatobjekt verwendet. Es muss zwischen den BEGIN_INTERFACE_PART-und END_INTERFACE_PART-Makros angezeigt werden. Ein Aggregat Objekt ist ein separates Objekt, das von [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)abgeleitet ist. Wenn Sie ein Aggregat und das INTERFACE_AGGREGATE-Makro verwenden, können Sie festlegen, dass alle Schnittstellen, die das Aggregat unterstützt, von dem-Objekt direkt unterstützt werden. Das Argument "- *aggr* " ist einfach der Name einer Element Variablen ihrer Klasse, die von [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) (entweder direkt oder indirekt) abgeleitet ist. Alle INTERFACE_AGGREGATE Makros müssen den INTERFACE_PART Makros folgen, wenn Sie in eine Schnittstellen Zuordnung eingefügt werden.

## <a name="see-also"></a>Weitere Informationen

[Technische Hinweise nach Zahl](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise nach Kategorie](../mfc/technical-notes-by-category.md)
