---
title: 'Serialisierung: Erstellen einer serialisierbaren Klasse'
ms.date: 11/04/2016
helpviewer_keywords:
- serializable class [MFC]
- DECLARE_SERIAL macro [MFC]
- default constructor [MFC]
- VERSIONABLE_SCHEMA macro [MFC]
- classes [MFC], derived
- IMPLEMENT_SERIAL macro [MFC]
- no-arguments constructor [MFC]
- Serialize method, overriding
- defaults [MFC], constructor
- CObject class [MFC], deriving serializable classes
- constructors [MFC], defining with no arguments
- serialization [MFC], serializable classes
- no default constructor
ms.assetid: 59a14d32-1cc8-4275-9829-99639beee27c
ms.openlocfilehash: 9648bd4f516a5f174534336b1ca3b42bb51ca0c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372705"
---
# <a name="serialization-making-a-serializable-class"></a>Serialisierung: Erstellen einer serialisierbaren Klasse

Fünf Hauptschritte sind erforderlich, um eine Klasse serialisierbar zu machen. Sie sind unten aufgeführt und in den folgenden Abschnitten erläutert:

1. [Ableiten der Klasse von CObject](#_core_deriving_your_class_from_cobject) (oder `CObject`von einer von ) abgeleiteten Klasse).

1. [Überschreiben der Serialize-Memberfunktion](#_core_overriding_the_serialize_member_function).

1. [Verwenden des DECLARE_SERIAL-Makros](#_core_using_the_declare_serial_macro) in der Klassendeklaration.

1. [Definieren eines Konstruktors, der keine Argumente verwendet.](#_core_defining_a_constructor_with_no_arguments)

1. [Verwenden des IMPLEMENT_SERIAL-Makros in der Implementierungsdatei](#_core_using_the_implement_serial_macro_in_the_implementation_file) für Ihre Klasse.

Wenn Sie `Serialize` direkt und nicht über die >> und << Operatoren von [CArchive](../mfc/reference/carchive-class.md)aufrufen, sind die letzten drei Schritte für die Serialisierung nicht erforderlich.

## <a name="deriving-your-class-from-cobject"></a><a name="_core_deriving_your_class_from_cobject"></a>Ableiten Ihrer Klasse von CObject

Das grundlegende Serialisierungsprotokoll und `CObject` die Funktionalität sind in der Klasse definiert. Durch Ableiten Ihrer `CObject` Klasse aus (oder `CObject`aus einer von ) abgeleiteten Klasse, wie in der folgenden Klassendeklaration `CPerson`gezeigt, erhalten Sie Zugriff auf das Serialisierungsprotokoll und die Funktionalität von `CObject`.

## <a name="overriding-the-serialize-member-function"></a><a name="_core_overriding_the_serialize_member_function"></a>Überschreiben der Serialize-Memberfunktion

Die `Serialize` Memberfunktion, die in `CObject` der Klasse definiert ist, ist für die faktische Serialisierung der Daten verantwortlich, die zum Erfassen des aktuellen Status eines Objekts erforderlich sind. Die `Serialize` Funktion `CArchive` verfügt über ein Argument, das zum Lesen und Schreiben der Objektdaten verwendet wird. Das [CArchive-Objekt](../mfc/reference/carchive-class.md) verfügt `IsStoring`über eine `Serialize` Memberfunktion , die angibt, ob Daten gespeichert (Schreiben) oder geladen (Daten gelesen) werden. Anhand der `IsStoring` Ergebnisse von als Leitfaden fügen Sie entweder `CArchive` die Daten Ihres**<** Objekts mit dem Einfügeoperator ( ) in das Objekt ein oder extrahieren Daten mit dem Extraktionsoperator (**>>**).

Betrachten Sie eine Klasse, die von `CObject` zwei neuen `CString` Membervariablen abgeleitet ist und über zwei neue Membervariablen verfügt, von Typen und **WORD**. Das folgende Klassendeklarationsfragment zeigt die neuen Membervariablen und die Deklaration für die überschriebene `Serialize` Memberfunktion:

[!code-cpp[NVC_MFCSerialization#1](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_1.h)]

#### <a name="to-override-the-serialize-member-function"></a>So überschreiben Sie die Serialize-Memberfunktion

1. Rufen Sie Ihre `Serialize` Basisklassenversion von auf, um sicherzustellen, dass der geerbte Teil des Objekts serialisiert wird.

1. Fügen Sie die für Ihre Klasse spezifischen Membervariablen ein oder extrahieren Sie sie.

   Die Einfüge- und Extraktionsoperatoren interagieren mit der Archivklasse, um die Daten zu lesen und zu schreiben. Das folgende Beispiel zeigt, `CPerson` wie Sie die oben deklarierte Klasse implementieren: `Serialize`

   [!code-cpp[NVC_MFCSerialization#2](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_2.cpp)]

Sie können auch die [Memberfunktionen CArchive::Read](../mfc/reference/carchive-class.md#read) und [CArchive::Write](../mfc/reference/carchive-class.md#write) verwenden, um große Mengen nicht typisierter Daten zu lesen und zu schreiben.

## <a name="using-the-declare_serial-macro"></a><a name="_core_using_the_declare_serial_macro"></a>Verwenden des DECLARE_SERIAL-Makros

Das DECLARE_SERIAL Makro in der Deklaration von Klassen erforderlich, die die Serialisierung unterstützen, wie hier gezeigt:

[!code-cpp[NVC_MFCSerialization#3](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_3.h)]

## <a name="defining-a-constructor-with-no-arguments"></a><a name="_core_defining_a_constructor_with_no_arguments"></a>Definieren eines Konstruktors ohne Argumente

MFC erfordert einen Standardkonstruktor, wenn er Ihre Objekte neu erstellt, wenn sie deserialisiert (vom Datenträger geladen) werden. Der Deserialisierungsprozess füllt alle Membervariablen mit den Werten aus, die zum erneuten Erstellen des Objekts erforderlich sind.

Dieser Konstruktor kann als öffentlich, geschützt oder privat deklariert werden. Wenn Sie es geschützt oder privat machen, stellen Sie sicher, dass es nur von den Serialisierungsfunktionen verwendet wird. Der Konstruktor muss das Objekt in einen Zustand versetzen, in dem es bei Bedarf gelöscht werden kann.

> [!NOTE]
> Wenn Sie vergessen, einen Konstruktor ohne Argumente in einer Klasse zu definieren, die die DECLARE_SERIAL- und IMPLEMENT_SERIAL-Makros verwendet, erhalten Sie in der Zeile, in der das IMPLEMENT_SERIAL-Makro verwendet wird, eine Compilerwarnung "kein Standardkonstruktor verfügbar".

## <a name="using-the-implement_serial-macro-in-the-implementation-file"></a><a name="_core_using_the_implement_serial_macro_in_the_implementation_file"></a>Verwenden des IMPLEMENT_SERIAL-Makros in der Implementierungsdatei

Das IMPLEMENT_SERIAL Makro wird verwendet, um die verschiedenen Funktionen zu `CObject`definieren, die beim Ableiten einer serialisierbaren Klasse von erforderlich sind. Sie verwenden dieses Makro in der Implementierungsdatei (. CPP) für Ihre Klasse. Die ersten beiden Argumente für das Makro sind der Name der Klasse und der Name ihrer unmittelbaren Basisklasse.

Das dritte Argument für dieses Makro ist eine Schemanummer. Die Schemanummer ist im Wesentlichen eine Versionsnummer für Objekte der Klasse. Verwenden Sie eine ganze Zahl größer oder gleich 0 für die Schemanummer. (Verwechseln Sie diese Schemanummer nicht mit der Datenbankterminologie.)

Der MFC-Serialisierungscode überprüft die Schemanummer beim Lesen von Objekten in den Speicher. Wenn die Schemanummer des Objekts auf dem Datenträger nicht mit der Schemanummer `CArchiveException`der Klasse im Arbeitsspeicher übereinstimmt, löst die Bibliothek eine aus, die verhindert, dass das Programm eine falsche Version des Objekts liest.

Wenn Sie `Serialize` möchten, dass Ihre Memberfunktion mehrere Versionen lesen kann, d. h. Dateien, die mit verschiedenen Versionen der Anwendung geschrieben wurden, können Sie den Wert *VERSIONABLE_SCHEMA* als Argument für das IMPLEMENT_SERIAL-Makro verwenden. Verwendungsinformationen und ein Beispiel `GetObjectSchema` finden Sie `CArchive`in der Memberfunktion von class .

Das folgende Beispiel zeigt, wie IMPLEMENT_SERIAL `CPerson`für eine `CObject`Klasse verwendet wird, die von : abgeleitet ist:

[!code-cpp[NVC_MFCSerialization#4](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_4.cpp)]

Sobald Sie über eine serialisierbare Klasse verfügen, können Sie Objekte der Klasse serialisieren, wie im Artikel [Serialisierung: Serialisieren eines Objekts](../mfc/serialization-serializing-an-object.md)beschrieben.

## <a name="see-also"></a>Siehe auch

[Serialisierung](../mfc/serialization-in-mfc.md)
