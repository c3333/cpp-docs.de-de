---
title: 'TN071: MFC-IOleCommandTarget-Implementierung'
ms.date: 06/28/2018
helpviewer_keywords:
- TN071 [MFC]
- IOleCommandTarget interface [MFC]
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
ms.openlocfilehash: 56745e7985c8af97b0b628d148586ccef346d95a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442072"
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071: MFC-IOleCommandTarget-Implementierung

> [!NOTE]
> Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

Die `IOleCommandTarget`-Schnittstelle ermöglicht es Objekten und ihren Containern, Befehle an einander zu senden. Beispielsweise können die Symbolleisten eines Objekts Schaltflächen für Befehle wie `Print`, `Print Preview`, `Save`, `New`und `Zoom`enthalten. Wenn ein solches Objekt in einen Container eingebettet wäre, der `IOleCommandTarget`unterstützt, könnte das Objekt seine Schaltflächen aktivieren und die Befehle zur Verarbeitung an den Container weiterleiten, wenn der Benutzer darauf geklickt hat. Wenn ein Container das eingebettete Objekt selbst drucken wollte, könnte dies dazu führen, dass ein Befehl über die `IOleCommandTarget`-Schnittstelle des eingebetteten Objekts gesendet wird.

`IOleCommandTarget` ist eine Automatisierungs ähnliche Schnittstelle darin, dass Sie von einem Client verwendet wird, um Methoden auf einem Server aufzurufen. Durch die Verwendung von `IOleCommandTarget` wird jedoch der Aufwand für Aufrufe über Automatisierungs Schnittstellen gespart, da Programmierer nicht die in der Regel teure `Invoke` Methode von `IDispatch`verwenden müssen.

In MFC wird die `IOleCommandTarget`-Schnittstelle von aktiven Dokument Servern verwendet, damit aktive Dokument Container Befehle an den Server verteilen können. Die Active Document Server-Klasse (`CDocObjectServerItem`) verwendet MFC-Schnittstellen Zuordnungen (siehe [TN038: MFC/OLE IUnknown-Implementierung](../mfc/tn038-mfc-ole-iunknown-implementation.md)), um die `IOleCommandTarget`-Schnittstelle zu implementieren.

`IOleCommandTarget` ist auch in der `COleFrameHook`-Klasse implementiert. `COleFrameHook` ist eine nicht dokumentierte MFC-Klasse, die die Rahmen Fenster Funktionalität von direkten Bearbeitungs Containern implementiert. `COleFrameHook` verwendet auch MFC-Schnittstellen Zuordnungen, um die `IOleCommandTarget`-Schnittstelle zu implementieren. durch die `COleFrameHook`Implementierung von `IOleCommandTarget` werden OLE-Befehle an von `COleDocObjectItem`abgeleitete aktive Dokument Container weitergeleitet. Dadurch kann jeder aktive MFC-Dokument Container Nachrichten von enthaltenen aktiven Dokument Servern empfangen.

## <a name="mfc-ole-command-maps"></a>MFC-OLE-Befehls Zuordnungen

MFC-Entwickler können `IOleCommandTarget` mithilfe von MFC-OLE-Befehls Zuordnungen nutzen. OLE-Befehls Zuordnungen ähneln Nachrichten Zuordnungen, da Sie zum Zuordnen von OLE-Befehlen zu Member-Funktionen der Klasse verwendet werden können, die die Befehls Map enthält. Um dies zu tun, platzieren Sie Makros in der Befehls Map, um die OLE-Befehlsgruppe des zu behandelnden Befehls, den OLE-Befehl und die Befehls-ID der [WM_COMMAND](/windows/win32/menurc/wm-command) Nachricht anzugeben, die beim Empfang des OLE-Befehls gesendet wird. MFC stellt außerdem eine Reihe vordefinierter Makros für OLE-Standard Befehle bereit. Eine Liste der OLE-Standard Befehle, die ursprünglich für die Verwendung mit Microsoft Office-Anwendungen entworfen wurden, finden Sie in der olecmdid-Enumeration, die in "docobj. h" definiert ist.

Wenn ein OLE-Befehl von einer MFC-Anwendung empfangen wird, die eine OLE-Befehls Map enthält, versucht MFC, die Befehls-ID und die Befehlsgruppe für den angeforderten Befehl in der OLE-Befehls Map der Anwendung zu finden. Wenn eine Entsprechung gefunden wird, wird eine WM_COMMAND Meldung an die Anwendung weitergeleitet, die die Befehls Map mit der ID des angeforderten Befehls enthält. (Weitere Informationen finden Sie unten in der Beschreibung der `ON_OLECMD`.) Auf diese Weise werden OLE-Befehle, die an eine Anwendung gesendet werden, von MFC in WM_COMMAND-Nachrichten umgewandelt. Die WM_COMMAND-Nachrichten werden dann mithilfe der standardmäßigen MFC- [Befehls Routing](../mfc/command-routing.md) Architektur durch die Meldungs Zuordnungen der Anwendung weitergeleitet.

Anders als bei Nachrichten Zuordnungen werden MFC-OLE-Befehls Zuordnungen von ClassWizard nicht unterstützt. MFC-Entwickler müssen OLE-Befehls Zuordnungs Unterstützung und OLE-Befehls Zuordnungs Einträge von Hand hinzufügen. OLE-Befehls Maps können MFC-aktiven Dokument Servern in jeder Klasse hinzugefügt werden, die sich in der WM_COMMAND-Nachrichten Weiterleitungs Kette befindet, wenn das aktive Dokument in einem Container aktiv ist. Diese Klassen enthalten die von [CWinApp](../mfc/reference/cwinapp-class.md), [CView](../mfc/reference/cview-class.md), [CDocument](../mfc/reference/cdocument-class.md)und [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)abgeleiteten Klassen der Anwendung. In aktiven Dokument Containern können OLE-Befehls Maps nur der von [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)abgeleiteten Klasse hinzugefügt werden. Außerdem werden die WM_COMMAND-Nachrichten in aktiven Dokument Containern nur an die Meldungs Zuordnung in der von `COleDocObjectItem`abgeleiteten Klasse gesendet.

## <a name="ole-command-map-macros"></a>OLE-Befehls Zuordnungs Makros

Verwenden Sie die folgenden Makros, um der-Klasse Befehls Zuordnungs Funktionen hinzuzufügen:

```cpp
DECLARE_OLECMD_MAP ()
```

Dieses Makro wird in die Klassen Deklaration (in der Regel in der Header Datei) der-Klasse eingefügt, die die Befehls Map enthält.

```cpp
BEGIN_OLECMD_MAP(theClass, baseClass)
```

*spiegeln*<br/>
Der Name der Klasse, die die Befehls Map enthält.

*BaseClass*<br/>
Der Name der Basisklasse der Klasse, die die Befehls Map enthält.

Dieses Makro markiert den Anfang der Befehls map. Verwenden Sie dieses Makro in der Implementierungs Datei für die-Klasse, die die Befehls Map enthält.

```
END_OLECMD_MAP()
```

Dieses Makro markiert das Ende der Befehls map. Verwenden Sie dieses Makro in der Implementierungs Datei für die-Klasse, die die Befehls Map enthält. Dieses Makro muss immer dem BEGIN_OLECMD_MAP-Makro folgen.

```
ON_OLECMD(pguid, olecmdid, id)
```

*pguid*<br/>
Zeiger auf die GUID der Befehlsgruppe des OLE-Befehls. Dieser Parameter ist für die Standard-OLE-Befehlsgruppe **null** .

*olecmdid*<br/>
Die OLE-Befehls-ID des aufzurufenden Befehls.

*id*<br/>
ID der WM_COMMAND Nachricht, die an die Anwendung gesendet werden soll, die die Befehls Map enthält, wenn dieser OLE-Befehl aufgerufen wird.

Verwenden Sie das ON_OLECMD-Makro in der Befehls Map, um Einträge für die OLE-Befehle hinzuzufügen, die Sie behandeln möchten. Wenn die OLE-Befehle empfangen werden, werden Sie in die angegebene WM_COMMAND Nachricht konvertiert und mithilfe der standardmäßigen MFC-Befehls Weiterleitungs Architektur durch die Meldungs Zuordnung der Anwendung weitergeleitet.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie Sie einem MFC-Active Document-Server OLE-Befehls Verarbeitungsfunktionen hinzufügen, um den [OLECMDID_PRINT](/windows/win32/api/docobj/ne-docobj-olecmdid) OLE-Befehl zu verarbeiten. In diesem Beispiel wird davon ausgegangen, dass Sie AppWizard zum Generieren einer MFC-Anwendung verwendet haben, die ein aktiver Dokument Server ist.

1. Fügen Sie der Klassen Deklaration in der Header Datei der von `CView`abgeleiteten Klasse das DECLARE_OLECMD_MAP-Makro hinzu.

    > [!NOTE]
    > Verwenden Sie die von `CView`abgeleitete Klasse, da Sie eine der Klassen im aktiven Dokument Server in der WM_COMMAND-Nachrichten Weiterleitungs Kette ist.

    ```cpp
    class CMyServerView : public CView
    {
    protected: // create from serialization only
        CMyServerView();
        DECLARE_DYNCREATE(CMyServerView)
        DECLARE_OLECMD_MAP()
        // . . .
    };
    ```

2. Fügen Sie in der Implementierungs Datei für die `CView`-abgeleitete Klasse die Makros BEGIN_OLECMD_MAP und END_OLECMD_MAP hinzu:

    ```cpp
    BEGIN_OLECMD_MAP(CMyServerView, CView)

    END_OLECMD_MAP()
    ```

3. Um den standardmäßigen OLE Print-Befehl zu verarbeiten, fügen Sie der Befehls Map ein [ON_OLECMD](reference/message-map-macros-mfc.md#on_olecmd) -Makro hinzu, indem Sie die OLE-Befehls-ID für den Standarddruck Befehl angeben und **ID_FILE_PRINT** für die WM_COMMAND-ID. **ID_FILE_PRINT** ist die standardmäßige Druck Befehls-ID, die von von AppWizard generierten MFC-Anwendungen verwendet wird:

    ```
    BEGIN_OLECMD_MAP(CMyServerView, CView)
        ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)
    END_OLECMD_MAP()
    ```

Beachten Sie, dass eines der Standard-OLE-Befehls Makros, die in afxdocob. h definiert sind, anstelle des ON_OLECMD-Makros verwendet werden kann, da **OLECMDID_PRINT** eine Standard-OLE-Befehls-ID ist. Das ON_OLECMD_PRINT-Makro führt dieselbe Aufgabe aus wie das oben gezeigte ON_OLECMD-Makro.

Wenn eine Containeranwendung an diesen Server einen **OLECMDID_PRINT** Befehl über die `IOleCommandTarget` Schnittstelle des Servers sendet, wird der MFC-Druck Befehls Handler auf dem Server aufgerufen, sodass der Server die Anwendung druckt. Der Code des aktiven Dokument Containers zum Aufrufen des Druck Befehls, der in den obigen Schritten hinzugefügt wurde, sieht in etwa wie folgt aus:

```cpp
void CContainerCntrItem::DoOleCmd()
{
    IOleCommandTarget *pCmd = NULL;
    HRESULT hr = E_FAIL;
    OLECMD ocm={OLECMDID_PRINT, 0};

    hr = m_lpObject->QueryInterface(
        IID_IOleCommandTarget,reinterpret_cast<void**>(&pCmd));

    if (FAILED(hr))
        return;

    hr = pCmd->QueryStatus(NULL, 1, &ocm, NULL);

    if (SUCCEEDED(hr) && (ocm.cmdf& OLECMDF_ENABLED))
    {
        //Command is available and enabled so call it
        COleVariant vIn;
        COleVariant vOut;
        hr = pCmd->Exec(NULL, OLECMDID_PRINT,
            OLECMDEXECOPT_DODEFAULT, &vIn, &vOut);
        ASSERT(SUCCEEDED(hr));
    }
    pCmd->Release();
}
```

## <a name="see-also"></a>Weitere Informationen

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
