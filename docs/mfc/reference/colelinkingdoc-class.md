---
title: COleLinkingDoc-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleLinkingDoc
- AFXOLE/COleLinkingDoc
- AFXOLE/COleLinkingDoc::COleLinkingDoc
- AFXOLE/COleLinkingDoc::Register
- AFXOLE/COleLinkingDoc::Revoke
- AFXOLE/COleLinkingDoc::OnFindEmbeddedItem
- AFXOLE/COleLinkingDoc::OnGetLinkedItem
helpviewer_keywords:
- COleLinkingDoc [MFC], COleLinkingDoc
- COleLinkingDoc [MFC], Register
- COleLinkingDoc [MFC], Revoke
- COleLinkingDoc [MFC], OnFindEmbeddedItem
- COleLinkingDoc [MFC], OnGetLinkedItem
ms.assetid: 9f547f35-2f95-427f-b9c0-85c31940198b
ms.openlocfilehash: f9f184542aaceb206d3eae110d3a088d5fbc95cf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374942"
---
# <a name="colelinkingdoc-class"></a>COleLinkingDoc-Klasse

Die Basisklasse für OLE-Containerdokumente, die das Verknüpfen mit den enthaltenen eingebetteten Elementen unterstützt.

## <a name="syntax"></a>Syntax

```
class COleLinkingDoc : public COleDocument
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ColeLinkingDoc::COleLinkingDoc](#colelinkingdoc)|Erstellt ein `COleLinkingDoc`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleLinkingDoc::Registrieren](#register)|Registriert das Dokument bei den OLE-System-DLLs.|
|[COleLinkingDoc::Revoke](#revoke)|Widerruft die Registrierung des Dokuments.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleLinkingDoc::OnFindEmbeddedItem](#onfindembeddeditem)|Sucht das angegebene eingebettete Element.|
|[COleLinkingDoc::OnGetLinkedItem](#ongetlinkeditem)|Sucht das angegebene verknüpfte Element.|

## <a name="remarks"></a>Bemerkungen

Eine Containeranwendung, die das Verknüpfen mit eingebetteten Elementen unterstützt, wird als "Linkcontainer" bezeichnet. Die [OCLIENT-Beispielanwendung](../../overview/visual-cpp-samples.md) ist ein Beispiel für einen Linkcontainer.

Wenn die Quelle eines verknüpften Elements ein eingebettetes Element in einem anderen Dokument ist, muss dieses Dokument geladen werden, damit das eingebettete Element bearbeitet werden kann. Aus diesem Grund muss ein Linkcontainer von einer anderen Containeranwendung gestartet werden können, wenn der Benutzer die Quelle eines verknüpften Elements bearbeiten möchte. Ihre Anwendung muss auch die [COleTemplateServer-Klasse](../../mfc/reference/coletemplateserver-class.md) verwenden, damit sie Dokumente erstellen kann, wenn sie programmgesteuert gestartet wird.

Um den Container zu einem Linkcontainer zu `COleLinkingDoc` machen, leiten Sie die Dokumentklasse anstelle von [COleDocument](../../mfc/reference/coledocument-class.md)ab. Wie bei jedem anderen OLE-Container müssen Sie Ihre Klasse zum Speichern der systemeigenen Daten der Anwendung sowie eingebetteter oder verknüpfter Elemente entwerfen. Außerdem müssen Sie Datenstrukturen zum Speichern Ihrer systemeigenen Daten entwerfen. Wenn Sie `CDocItem`eine -derived-Klasse für die systemeigenen Daten Ihrer `COleDocument` Anwendung definieren, können Sie die von Ihnen definierte Schnittstelle verwenden, um Ihre systemeigenen Daten sowie Ihre OLE-Daten zu speichern.

Damit Ihre Anwendung programmgesteuert von einem anderen Container `COleTemplateServer` gestartet werden kann, deklarieren Sie ein Objekt als Member der `CWinApp`-derived-Klasse Ihrer Anwendung:

[!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/cpp/colelinkingdoc-class_1.h)]

Erstellen `InitInstance` Sie in `CWinApp`der Memberfunktion Ihrer -derived-Klasse `COleLinkingDoc`eine Dokumentvorlage, und geben Sie ihre -derived-Klasse als Dokumentklasse an:

[!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/cpp/colelinkingdoc-class_2.cpp)]

Verbinden `COleTemplateServer` Sie das Objekt mit den Dokumentvorlagen, indem Sie die Memberfunktion des Objekts `ConnectTemplate` aufrufen, und registrieren Sie alle Klassenobjekte beim OLE-System, indem Sie `COleTemplateServer::RegisterAll`:

[!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/cpp/colelinkingdoc-class_3.cpp)]

Eine Beispiel-abgeleitete `CWinApp`Klassendefinition und `InitInstance` -Funktion finden Sie unter OCLIENT. H und OCLIENT. CPP im MFC-Beispiel [OCLIENT](../../overview/visual-cpp-samples.md).

Weitere Informationen zur `COleLinkingDoc`Verwendung finden Sie in den Artikeln [Container: Implementieren eines Containers](../../mfc/containers-implementing-a-container.md) und [Container: Erweiterte Funktionen](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

`COleLinkingDoc`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxole.h

## <a name="colelinkingdoccolelinkingdoc"></a><a name="colelinkingdoc"></a>ColeLinkingDoc::COleLinkingDoc

Erstellt ein `COleLinkingDoc` Objekt, ohne die Kommunikation mit den OLE-System-DLLs zu beginnen.

```
COleLinkingDoc();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen `Register` die Memberfunktion aufrufen, um OLE darüber zu informieren, dass das Dokument geöffnet ist.

## <a name="colelinkingdoconfindembeddeditem"></a><a name="onfindembeddeditem"></a>COleLinkingDoc::OnFindEmbeddedItem

Wird vom Framework aufgerufen, um zu bestimmen, ob das Dokument ein eingebettetes OLE-Element mit dem angegebenen Namen enthält.

```
virtual COleClientItem* OnFindEmbeddedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parameter

*lpszItemName*<br/>
Zeiger auf den Namen des angeforderten eingebetteten OLE-Elements.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das angegebene Element; NULL, wenn das Element nicht gefunden wurde.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung durchsucht die Liste der eingebetteten Elemente nach einem Element mit dem angegebenen Namen (bei dem Namensvergleich wird die Groß-/Kleinschreibung beachtet). Überschreiben Sie diese Funktion, wenn Sie über eine eigene Methode zum Speichern oder Benennen eingebetteter OLE-Elemente verfügen.

## <a name="colelinkingdocongetlinkeditem"></a><a name="ongetlinkeditem"></a>COleLinkingDoc::OnGetLinkedItem

Wird vom Framework aufgerufen, um zu überprüfen, ob das Dokument ein verknüpftes Serverelement mit dem angegebenen Namen enthält.

```
virtual COleServerItem* OnGetLinkedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parameter

*lpszItemName*<br/>
Zeiger auf den Namen des angeforderten verknüpften OLE-Elements.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das angegebene Element; NULL, wenn das Element nicht gefunden wurde.

### <a name="remarks"></a>Bemerkungen

Die `COleLinkingDoc` Standardimplementierung gibt immer NULL zurück. Diese Funktion wird in der `COleServerDoc` abgeleiteten Klasse überzeichnet, um die Liste der OLE-Serverelemente nach einem verknüpften Element mit dem angegebenen Namen zu durchsuchen (bei dem Namensvergleich wird die Groß-/Kleinschreibung beachtet). Überschreiben Sie diese Funktion, wenn Sie eine eigene Methode zum Speichern oder Abrufen verknüpfter Serverelemente implementiert haben.

## <a name="colelinkingdocregister"></a><a name="register"></a>COleLinkingDoc::Registrieren

Informiert die OLE-System-DLLs, dass das Dokument geöffnet ist.

```
BOOL Register(
    COleObjectFactory* pFactory,
    LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parameter

*pFactory*<br/>
Zeiger auf ein OLE-Factoryobjekt (kann NULL sein).

*lpszPathName*<br/>
Zeiger auf den vollqualifizierten Pfad des Containerdokuments.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Dokument erfolgreich registriert wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, wenn Sie eine benannte Datei erstellen oder öffnen, um das Dokument bei den OLE-System-DLLs zu registrieren. Diese Funktion muss nicht aufrufen, wenn das Dokument ein eingebettetes Element darstellt.

Wenn Sie `COleTemplateServer` in Ihrer `Register` Anwendung verwenden, `COleLinkingDoc`wird für `OnNewDocument`Sie `OnOpenDocument`durch `OnSaveDocument`die Implementierung von aufgerufen, und .

## <a name="colelinkingdocrevoke"></a><a name="revoke"></a>COleLinkingDoc::Revoke

Informiert die OLE-System-DLLs, dass das Dokument nicht mehr geöffnet ist.

```
void Revoke();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um die Registrierung des Dokuments bei den OLE-System-DLLs zu widerrufen.

Sie sollten diese Funktion aufrufen, wenn Sie eine benannte Datei schließen, aber Sie müssen sie in der Regel nicht direkt aufrufen. `Revoke`wird für Sie `COleLinkingDoc`durch die `OnCloseDocument` `OnNewDocument`Implementierung `OnOpenDocument`von `OnSaveDocument`aufgerufen, , , und .

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDocument-Klasse](../../mfc/reference/coledocument-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate-Klasse](../../mfc/reference/cdoctemplate-class.md)
