---
title: CSocketFile-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSocketFile
- AFXSOCK/CSocketFile
- AFXSOCK/CSocketFile::CSocketFile
helpviewer_keywords:
- CSocketFile [MFC], CSocketFile
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
ms.openlocfilehash: 83810a05925e5c8302240b61d95c131fdd78b426
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318162"
---
# <a name="csocketfile-class"></a>CSocketFile-Klasse

Ein `CFile` -Objekt zum Senden und Empfangen von Daten in einem Netzwerk über Windows Sockets.

## <a name="syntax"></a>Syntax

```
class CSocketFile : public CFile
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSocketFile::CSocketFile](#csocketfile)|Erstellt ein `CSocketFile`-Objekt.|

## <a name="remarks"></a>Bemerkungen

Sie können `CSocketFile` das Objekt `CSocket` zu diesem Zweck an ein Objekt anfügen. Sie können und können das `CSocketFile` Objekt auch `CArchive` an ein Objekt anfügen, um das Senden und Empfangen von Daten mithilfe der MFC-Serialisierung zu vereinfachen.

Um Daten zu serialisieren (senden), fügen Sie `CSocketFile` sie in das Archiv `CSocket` ein, das Memberfunktionen aufruft, um Daten in das Objekt zu schreiben. Um Daten zu deserialisieren (empfangen), extrahieren Sie aus dem Archiv. Dies bewirkt, `CSocketFile` dass das Archiv `CSocket` Memberfunktionen aufruft, um Daten aus dem Objekt zu lesen.

> [!TIP]
> Neben `CSocketFile` der Verwendung, wie hier beschrieben, können Sie es als eigenständiges Dateiobjekt verwenden, genau wie Sie es mit `CFile`der Basisklasse verwenden können. Sie können `CSocketFile` auch mit beliebigen archivbasierten MFC-Serialisierungsfunktionen verwenden. Da `CSocketFile` nicht alle `CFile`Funktionen von unterstützt werden, sind einige standardmäßige `CSocketFile`MFC-Serialisierungsfunktionen nicht mit kompatibel. Dies gilt insbesondere `CEditView` für die Klasse. Sie sollten nicht versuchen, Daten `CArchive` über ein `CSocketFile` Objekt `CEditView::SerializeRaw`zu serialisieren, `CEditView` das mit einem Objekt verbunden ist. verwenden. `CEditView::Serialize` Die `SerializeRaw` Funktion erwartet, dass das Dateiobjekt Funktionen hat, z. `Seek`B. , die `CSocketFile` nicht vorhanden sind.

Wenn Sie `CArchive` `CSocketFile` mit `CSocket`und verwenden, kann `CSocket::Receive` es vorkommen, `PumpMessages(FD_READ)`dass eine Schleife (durch ) eintritt, die auf die angeforderte Menge an Bytes wartet. Dies liegt daran, dass Windows-Sockets nur `CSocketFile` einen `CSocket` recv-Aufruf pro FD_READ Benachrichtigung zulassen, aber mehrere recv-Aufrufe pro FD_READ. Wenn Sie eine FD_READ erhalten, wenn keine Daten zum Lesen vorhanden sind, hängt die Anwendung. Wenn Sie nie eine weitere FD_READ erhalten, beendet die Anwendung die Kommunikation über den Socket.

Sie können dieses Problem wie folgt beheben. Rufen `OnReceive` Sie in der Methode `CAsyncSocket::IOCtl(FIONREAD, ...)` ihrer Socketklasse auf, bevor Sie die `Serialize` Methode Ihrer Nachrichtenklasse aufrufen, wenn die erwarteten Daten, die vom Socket gelesen werden sollen, die Größe eines TCP-Pakets überschreiten (maximale Übertragungseinheit des Netzwerkmediums, in der Regel mindestens 1096 Bytes). Wenn die Größe der verfügbaren Daten geringer ist als erforderlich, warten Sie, bis alle Daten empfangen wurden, und starten Sie dann den Lesevorgang.

Im folgenden Beispiel `m_dwExpected` ist die ungefähre Anzahl von Bytes, die der Benutzer erwartet. Es wird davon ausgegangen, dass Sie es an anderer Stelle im Code deklarieren.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]

Weitere Informationen finden Sie unter [Windows Sockets in MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md)sowie Windows [Sockets 2 API](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CSocketFile`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxsock.h

## <a name="csocketfilecsocketfile"></a><a name="csocketfile"></a>CSocketFile::CSocketFile

Erstellt ein `CSocketFile`-Objekt.

```
explicit CSocketFile(
    CSocket* pSocket,
    BOOL bArchiveCompatible = TRUE);
```

### <a name="parameters"></a>Parameter

*pSocket*<br/>
Der Socket, der `CSocketFile` an das Objekt angefügt werden soll.

*bArchiveKompatibel*<br/>
Gibt an, ob das Dateiobjekt `CArchive` für die Verwendung mit einem Objekt bestimmt ist. Übergeben Sie FALSE nur, `CSocketFile` wenn Sie das Objekt auf eigenständige Weise `CFile` verwenden möchten, wie sie es bei einem eigenständigen Objekt mit bestimmten Einschränkungen tun würden. Dieses Flag ändert, wie `CArchive` `CSocketFile` das dem Objekt angefügte Objekt seinen Puffer zum Lesen verwaltet.

### <a name="remarks"></a>Bemerkungen

Der Destruktor des Objekts trennt sich vom Socketobjekt, wenn das Objekt den Gültigkeitsbereich verlässt oder gelöscht wird.

> [!NOTE]
> A `CSocketFile` kann auch als (begrenzte) Datei `CArchive` ohne Objekt verwendet werden. Standardmäßig ist `CSocketFile` der *bArchiveCompatible-Parameter* des Konstruktors TRUE. Dadurch wird angegeben, dass das Dateiobjekt für die Verwendung mit einem Archiv bestimmt ist. Um das Dateiobjekt ohne Archiv zu verwenden, übergeben Sie FALSE im Parameter *bArchiveCompatible.*

Im Modus "Archivkompatibel" `CSocketFile` bietet ein Objekt eine bessere Leistung und reduziert die Gefahr eines "Deadlocks". Ein Deadlock tritt auf, wenn sowohl die sendenden als auch die empfangenden Sockets auf einander oder auf eine gemeinsame Ressource warten. Diese Situation kann `CArchive` auftreten, wenn `CSocketFile` das Objekt so `CFile` gearbeitet hat, wie es mit einem Objekt funktioniert. Mit `CFile`kann das Archiv davon ausgehen, dass das Ende der Datei erreicht wurde, wenn es weniger Bytes empfängt, als es angefordert hat.

Bei `CSocketFile`sind die Daten jedoch nachrichtenbasiert. Der Puffer kann mehrere Nachrichten enthalten, sodass der Empfang von weniger als der Anzahl der angeforderten Bytes nicht das Ende der Datei impliziert. Die Anwendung blockiert in diesem Fall `CFile`nicht wie bei , und sie kann weiterhin Nachrichten aus dem Puffer lesen, bis der Puffer leer ist. Die [CArchive::IsBufferEmpty-Funktion](../../mfc/reference/carchive-class.md#isbufferempty) ist nützlich, um den Status des Archivpuffers in einem solchen Fall zu überwachen.

Weitere Informationen zur Verwendung `CSocketFile`von finden Sie in den Artikeln [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md) and Windows [Sockets: Example of Sockets Using Archives](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="see-also"></a>Siehe auch

[CFile-Klasse](../../mfc/reference/cfile-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket-Klasse](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocket-Klasse](../../mfc/reference/csocket-class.md)
