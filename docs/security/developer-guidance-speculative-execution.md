---
title: C++ Anleitung für Entwickler für spekulative Ausführungs seitige Kanäle
ms.date: 07/10/2018
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
- Spectre
- CVE-2017-5753
- Speculative Execution
ms.openlocfilehash: 72dffd25eef847d1bdffe61c4a18a27d9cb33644
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842454"
---
# <a name="c-developer-guidance-for-speculative-execution-side-channels"></a>C++ Anleitung für Entwickler für spekulative Ausführungs seitige Kanäle

Dieser Artikel enthält Anleitungen für Entwickler, die Unterstützung beim identifizieren und Beheben von Hardware Sicherheitslücken bei der Ausführung von spekulativen Ausführungs seitigen Kanälen in C++-Software Diese Sicherheitsrisiken können vertrauliche Informationen über Vertrauensgrenzen hinweg offenlegen und sich auf Software auswirken, die auf Prozessoren ausgeführt wird, die eine spekulative, nicht ordnungs mäßig ausgeführte Ausführung von Anweisungen unterstützen. Diese Klasse von Sicherheitsrisiken wurde zunächst im Januar 2018 beschrieben, und zusätzliche Hintergrundinformationen und Anleitungen finden Sie in [der Sicherheitsempfehlung von Microsoft](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002).

Die Anleitungen in diesem Artikel beziehen sich auf die Klassen von Sicherheitsrisiken, die durch dargestellt werden:

1. CVE-2017-5753, auch als Spectre Variant 1 bezeichnet. Diese Hardware Sicherheitsrisiko-Klasse bezieht sich auf neben Kanäle, die durch eine spekulative Ausführung ausgelöst werden können, die als Ergebnis einer bedingten Verzweigungs-fehl Setzung auftritt. Der Microsoft C++-Compiler in Visual Studio 2017 (beginnend mit Version 15.5.5) umfasst Unterstützung für den `/Qspectre` Switch, der eine Kompilierzeit Entschärfung für eine begrenzte Anzahl von potenziell anfälligen Codierungs Mustern im Zusammenhang mit CVE-2017-5753 bereitstellt. Der `/Qspectre` Schalter ist auch in Visual Studio 2015 Update 3 bis [KB 4338871](https://support.microsoft.com/help/4338871)verfügbar. In der Dokumentation für das- [`/Qspectre`](../build/reference/qspectre.md) Flag finden Sie weitere Informationen zu den Auswirkungen und der Verwendung.

2. CVE-2018-3639, auch als " [spekulative Store Bypass (SSB)](https://aka.ms/sescsrdssb)" bezeichnet. Diese Hardware Sicherheitsrisiko-Klasse bezieht sich auf neben Kanäle, die aufgrund der spekulativen Ausführung einer Last vor einem abhängigen Speicher aufgrund einer Speicherzugriffs-midepdiction auftreten können.

Eine barrierefreie Einführung in Sicherheitsrisiken für spekulative Ausführungs seitige Kanäle finden Sie in der Präsentation mit dem Titel " [Spectre" und](https://www.youtube.com/watch?v=_4O0zMW-Zu4) der Zusammenführung durch eines der Forschungsteams, das diese Probleme erkannt hat.

## <a name="what-are-speculative-execution-side-channel-hardware-vulnerabilities"></a>Was sind Sicherheitsrisiken für die spekulative Ausführungs seitige Kanal Hardware?

Moderne CPUs sorgen für eine höhere Leistung, da Sie eine spekulative und nicht ordnungsgemäße Ausführung von Anweisungen verwenden. Dies wird z. b. häufig durch Vorhersagen des Ziels von branches (bedingt und indirekt) erreicht, wodurch die CPU mit der Ausführung von Anweisungen am vorhergesagten Verzweigungs Ziel beginnen kann. so wird ein Stall vermieden, bis das tatsächliche Verzweigungs Ziel aufgelöst wird. Wenn die CPU später feststellt, dass eine miftdiction aufgetreten ist, wird der gesamte Computer Status, der als spekulativ berechnet wurde, verworfen. Dadurch wird sichergestellt, dass es keine architektonisch sichtbaren Auswirkungen der falsch eingeblendeten Spekulation gibt.

Die spekulative Ausführung wirkt sich nicht auf den architektonisch sichtbaren Zustand aus, aber Sie kann die Rest-Ablauf Verfolgungen im nicht architektonischen Zustand belassen, wie z. b. die verschiedenen zwischen Speicherungen, die von der CPU verwendet werden. Dabei handelt es sich um die Rest-Ablauf Verfolgungen der spekulativen Ausführung, die zu Sicherheitsrisiken im Außendienst führen können. Um dies besser zu verstehen, sehen Sie sich das folgende Code Fragment an, das ein Beispiel für CVE-2017-5753 (Umgehungs Umgehung der Begrenzungs Überprüfung) bereitstellt:

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

In diesem Beispiel `ReadByte` wird ein Puffer, eine Puffergröße und ein Index in diesem Puffer bereitgestellt. Der Index Parameter, wie von angegeben, `untrusted_index` wird durch einen Kontext mit weniger Berechtigungen, z. b. ein nicht administrativer Prozess, bereitgestellt. Wenn `untrusted_index` kleiner als ist `buffer_size` , wird das Zeichen an diesem Index aus gelesen `buffer` und zum Indizieren in einen freigegebenen Speicherbereich verwendet, auf den von verwiesen wird `shared_buffer` .

Aus Sicht der Architektur ist diese Code Sequenz ganz sicher, da sichergestellt ist, dass `untrusted_index` immer kleiner als ist `buffer_size` . Bei einer spekulativen Ausführung ist es jedoch möglich, dass die CPU den bedingten Branch falsch anweist und den Text der if-Anweisung ausführt, auch wenn `untrusted_index` größer als oder gleich ist `buffer_size` . Infolgedessen liest die CPU möglicherweise ein Byte aus den Grenzen von `buffer` (was ein geheimer Schlüssel sein kann) und kann dann diesen Bytewert verwenden, um die Adresse einer nachfolgenden Last durch zu berechnen `shared_buffer` .

Obwohl die CPU diese fehl Grenze schließlich erkennen kann, verbleiben die übrigen Nebeneffekte im CPU-Cache, die Informationen über den Bytewert offenlegen, der aus den Begrenzungen gelesen wurde `buffer` . Diese Nebeneffekte können durch einen weniger privilegierten Kontext erkannt werden, der auf dem System ausgeführt wird, indem geprüft wird, wie schnell auf die einzelnen Cache Zeilen in `shared_buffer` zugegriffen wird. Hierfür können Sie folgende Schritte ausführen:

1. **Rufen `ReadByte` Sie mehrmals auf `untrusted_index` , wenn kleiner `buffer_size` als ist **. Der Angriffs Kontext kann bewirken, dass der Opfer Kontext `ReadByte` (z. b. über RPC) aufgerufen wird, sodass der Verzweigungs-Prätor so trainiert wird, dass er nicht als "kleiner als" verwendet wird `untrusted_index` `buffer_size` .

2. **Leeren Sie alle Cache Zeilen `shared_buffer` in **. Der Angriffs Kontext muss alle Cache Zeilen in dem freigegebenen Speicherbereich leeren, auf den von verwiesen wird `shared_buffer` . Da der Speicherbereich freigegeben ist, ist dies unkompliziert und kann mit systeminternen Funktionen wie erreicht werden `_mm_clflush` .

3. ** `ReadByte` `untrusted_index` Wird aufgerufen, wenn größer `buffer_size` als ist **. Der Angriffs Kontext bewirkt, dass der Opfer Kontext aufgerufen `ReadByte` wird, sodass falsch vorhergesagt wird, dass die Verzweigung nicht übernommen wird. Dies bewirkt, dass der Prozessor den Text des If-Blocks `untrusted_index` , der größer als `buffer_size` ist, auf eine Weise ausführt, was zu einem Lesevorgang außerhalb des gültigen Bereichs führt `buffer` . Folglich `shared_buffer` wird mit einem potenziell geheimen Wert indiziert, der außerhalb der Grenzen gelesen wurde, sodass die jeweilige Cache Zeile von der CPU geladen wird.

4. **Lesen Sie jede Cache Zeile in `shared_buffer` , um festzustellen, auf welche zugegriffen wird**. Der Angriffs Kontext kann jede Cache Zeile in lesen `shared_buffer` und die Cache Zeile erkennen, die erheblich schneller geladen wird als die anderen. Dies ist die Cache Zeile, die wahrscheinlich von Schritt 3 eingefügt wurde. Da in diesem Beispiel eine 1:1-Beziehung zwischen Bytewert und Cache Zeile vorhanden ist, kann der Angreifer den tatsächlichen Wert des Bytes ableiten, das außerhalb der Grenzen gelesen wurde.

In den obigen Schritten wird ein Beispiel für die Verwendung eines Verfahrens, das als leeren und erneuten Laden bezeichnet wird, in Verbindung mit der Verwendung einer Instanz von CVE-2017-5753 beschrieben.

## <a name="what-software-scenarios-can-be-impacted"></a>Welche Software Szenarien können beeinträchtigt werden?

Wenn Sie sichere Software mit einem Prozess wie dem [Security Development Lifecycle](https://www.microsoft.com/sdl/) (SDL) entwickeln, müssen Entwickler in der Regel die Vertrauensgrenzen identifizieren, die in Ihrer Anwendung vorhanden sind. An Orten, an denen eine Anwendung mit Daten interagieren kann, die von einem weniger vertrauenswürdigen Kontext bereitgestellt werden, z. b. ein anderer Prozess im System oder ein nicht administrativer Benutzermodusprozess im Falle eines Gerätetreibers im Kernel Modus. Die neue Klasse von Sicherheitsrisiken, die spekulative Ausführungs seitige Kanäle betreffen, ist für viele der Vertrauensgrenzen in vorhandenen Software Sicherheitsmodellen relevant, die den Code und die Daten auf einem Gerät isolieren.

In der folgenden Tabelle finden Sie eine Zusammenfassung der Software Sicherheitsmodelle, in denen sich Entwickler möglicherweise Gedanken über diese Sicherheitslücken machen müssen:

|Vertrauensgrenze|Beschreibung|
|----------------|----------------|
|Grenze für virtuelle Computer|Anwendungen, die Arbeits Auslastungen auf separaten virtuellen Computern isolieren, die nicht vertrauenswürdige Daten von einem anderen virtuellen Computer empfangen, können gefährdet sein.|
|Kernel Grenze|Ein Kernel Modus-Gerätetreiber, der nicht vertrauenswürdige Daten von einem nicht administrativen Benutzermodusprozess empfängt, ist möglicherweise gefährdet.|
|Prozess Grenze|Eine Anwendung, die nicht vertrauenswürdige Daten von einem anderen Prozess empfängt, der auf dem lokalen System ausgeführt wird, z. b. über einen Remote Prozedur Aufruf (RPC), gemeinsam genutzten Arbeitsspeicher oder andere IPC-Mechanismen (Inter-Process Communication).|
|Enclave-Grenze|Eine Anwendung, die in einer sicheren Enclave (z. b. Intel SGX) ausgeführt wird, die nicht vertrauenswürdige Daten von außerhalb der Enclave empfängt, ist möglicherweise gefährdet.|
|Sprachgrenze|Eine Anwendung, die einen nicht vertrauenswürdigen Code, der in einer höheren Sprache geschrieben ist, oder Just-in-time (JIT) kompiliert und ausführt, ist möglicherweise gefährdet.|

Anwendungen mit Angriffsfläche, die für eine der obigen Vertrauensgrenzen verfügbar gemacht werden, sollten den Code auf der Angriffsfläche überprüfen, um mögliche Instanzen von Sicherheitsrisiken für spekulative Ausführungs seitige Kanäle zu identifizieren und zu verringern. Beachten Sie, dass Vertrauensgrenzen, die für Remote Angriffsflächen verfügbar gemacht werden (z. b. Remote Netzwerkprotokolle), nicht als Risiko für spekulative Ausführungs seitige Kanal Sicherheitsanfälligkeiten angezeigt werden.

## <a name="potentially-vulnerable-coding-patterns"></a>Potenziell anfällige Codierungs Muster

Die Sicherheitsrisiken für die spekulative Ausführungs Seite können als Folge mehrerer Codierungs Muster auftreten. In diesem Abschnitt werden potenziell anfällige Codierungs Muster beschrieben, und es werden Beispiele dafür bereitstellt, aber es sollte erkannt werden, dass Variationen dieser Designs möglicherweise vorhanden sind. Daher wird empfohlen, dass diese Muster als Beispiele und nicht als vollständige Liste aller potenziell anfälligen Codierungs Muster übernommen werden. Die gleichen Klassen von Sicherheitsrisiken für die Speicher Sicherheit, die heute in der Software vorhanden sein können, sind möglicherweise auch an spekulativen und nicht ordnungsgemäß ausgeführten Ausführungs Pfaden, einschließlich, aber nicht beschränkt auf Pufferüberläufe, Array Zugriffen außerhalb der Grenzen, nicht initialisierte Speicher Verwendung, typverwirrung usw. Die gleichen primitiven, die Angreifer verwenden können, um Sicherheitsrisiken für die Speicher Sicherheit in Architektur Pfaden auszunutzen, können auch auf spekulative Pfade zutreffen.

Im Allgemeinen können spekulative Ausführungs seitige Kanäle im Zusammenhang mit der bedingten Verzweigung falsch auftreten, wenn ein bedingter Ausdruck auf Daten angewendet wird, die von einem weniger vertrauenswürdigen Kontext gesteuert oder beeinflusst werden können. Dies kann z. b. bedingte Ausdrücke enthalten, die in-,-,-,- **`if`** **`for`** **`while`** **`switch`** oder ternäre-Anweisungen verwendet werden. Für jede dieser Anweisungen generiert der Compiler möglicherweise eine bedingte Verzweigung, die die CPU dann zur Laufzeit für das Verzweigungs Ziel vorhersagen kann.

Für jedes Beispiel wird ein Kommentar mit dem Ausdruck "Spekulations Barriere" eingefügt, in dem ein Entwickler eine Barriere als Entschärfung einführen könnte. Dies wird im Abschnitt zu entschärfungen ausführlicher erläutert.

## <a name="speculative-out-of-bounds-load"></a>Spekulative Auslastung außerhalb des gültigen Bereichs

Diese Kategorie von Codierungs Mustern umfasst eine bedingte Verzweigung, die zu einem spekulativen Speicherzugriff führt.

### <a name="array-out-of-bounds-load-feeding-a-load"></a>Lasten Zufuhr für ein Array außerhalb der Grenzen

Dieses Codierungs Muster ist das ursprünglich beschriebene verwundbare Codierungs Muster für CVE-2017-5753 (Umgehungs Umgehung von Begrenzungen). Im Hintergrund Abschnitt dieses Artikels wird dieses Muster ausführlich erläutert.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        // SPECULATION BARRIER
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

Ebenso kann ein Array außerhalb des gültigen Bereichs in Verbindung mit einer-Schleife auftreten, die die Beendigungs Bedingung aufgrund einer fehl Setzung überschreitet. In diesem Beispiel kann der bedingte Branch, der dem `x < buffer_size` Ausdruck zugeordnet ist, falsch sein und den Text der Schleife auf die **`for`** gleiche Weise ausführen `x` , wenn größer als oder gleich ist `buffer_size` . Dies führt zu einer spekulativen Auslastung außerhalb des gültigen Bereichs.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadBytes(unsigned char *buffer, unsigned int buffer_size) {
    for (unsigned int x = 0; x < buffer_size; x++) {
        // SPECULATION BARRIER
        unsigned char value = buffer[x];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="array-out-of-bounds-load-feeding-an-indirect-branch"></a>Ein Array, das eine indirekte Verzweigung als Lasten Zufuhr durch ein Array aufweist

Dieses Codierungs Muster bezieht sich auf den Fall, in dem eine bedingte Verzweigung fehl setzen kann, um einen Out-of-Bounds-Zugriff auf ein Array von Funktions Zeigern zu erreichen, das dann zu einer indirekten Verzweigung der Zieladresse führt, die außerhalb der Grenzen gelesen wurde. Der folgende Code Ausschnitt stellt ein Beispiel dar, das dies veranschaulicht.

In diesem Beispiel wird eine nicht vertrauenswürdige Nachrichten-ID für DispatchMessage mithilfe des- `untrusted_message_id` Parameters bereitgestellt. Wenn `untrusted_message_id` kleiner als ist `MAX_MESSAGE_ID` , wird es verwendet, um in ein Array von Funktions Zeigern zu indizieren und zum entsprechenden Verzweigungs Ziel zu verzweigen. Dieser Code ist in architektonischer Weise sicher, aber wenn der bedingte Branch von der CPU falsch festgestellt wird, kann dies dazu führen, `DispatchTable` dass die Indizierung durchgeführt wird, `untrusted_message_id` wenn sein Wert größer als oder gleich ist `MAX_MESSAGE_ID` , was zu einem Zugriff außerhalb der Grenzen führt. Dies kann zu einer spekulativen Ausführung von einer Zweigstellen Zieladresse führen, die über die Grenzen des Arrays hinaus abgeleitet ist. Dies kann zur Offenlegung von Informationen in Abhängigkeit von dem Code führen, der als spekulativ ausgeführt wird.

```cpp
#define MAX_MESSAGE_ID 16

typedef void (*MESSAGE_ROUTINE)(unsigned char *buffer, unsigned int buffer_size);

const MESSAGE_ROUTINE DispatchTable[MAX_MESSAGE_ID];

void DispatchMessage(unsigned int untrusted_message_id, unsigned char *buffer, unsigned int buffer_size) {
    if (untrusted_message_id < MAX_MESSAGE_ID) {
        // SPECULATION BARRIER
        DispatchTable[untrusted_message_id](buffer, buffer_size);
    }
}
```

Wie bei einem Array außerhalb der Grenzen, das eine andere Last lädt, kann diese Bedingung auch in Verbindung mit einer-Schleife auftreten, die die Beendigungs Bedingung aufgrund einer fehl Setzung überschreitet.

### <a name="array-out-of-bounds-store-feeding-an-indirect-branch"></a>Out-of-Bounds-Array, das eine indirekte Verzweigung ernährt

Im vorherigen Beispiel wurde gezeigt, wie eine spekulative Auslastung außerhalb der Grenzen ein indirektes Verzweigungs Ziel beeinflussen kann. es ist auch möglich, dass in einem Out-of-Bounds-Speicher ein indirektes Verzweigungs Ziel (z. b. ein Funktionszeiger oder eine Rückgabeadresse) geändert wird. Dies kann möglicherweise dazu führen, dass eine Angreifer-angegebene Adresse die spekulative Ausführung durchführt.

In diesem Beispiel wird ein nicht vertrauenswürdiger Index durch den- `untrusted_index` Parameter übergeben. Wenn `untrusted_index` kleiner als die Element Anzahl des `pointers` Arrays (256 Elemente) ist, wird der bereitgestellte Zeiger Wert in in `ptr` das Array geschrieben `pointers` . Dieser Code ist in architektonischer Weise sicher, aber wenn die CPU den bedingten Branch falsch schreibt, kann dies dazu führen, `ptr` dass Sie über die Grenzen des vom Stapel zugewiesenen Arrays hinaus spekulativ geschrieben werden `pointers` . Dies kann zu einer spekulativen Beschädigung der Rückgabeadresse für führen `WriteSlot` . Wenn ein Angreifer den Wert von Steuern kann `ptr` , kann er möglicherweise eine spekulative Ausführung von einer beliebigen Adresse auslösen, wenn er `WriteSlot` an dem spekulativen Pfad zurückgibt.

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
}
```

Wenn eine lokale Variable `func` für den Funktionszeiger im Stapel zugeordnet wurde, kann es auch möglich sein, die Adresse, auf die verwiesen wird, `func` zu ändern, wenn die bedingte Verzweigung falsch ist. Dies kann zu einer spekulativen Ausführung von einer beliebigen Adresse führen, wenn der Funktionszeiger durch aufgerufen wird.

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    void (*func)() = &callback;
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
    func();
}
```

Beachten Sie, dass beide Beispiele eine spekulative Änderung der durch den Stapel zugewiesenen indirekten Verzweigungs Zeiger beinhalten. Es ist möglich, dass eine spekulative Änderung auch bei globalen Variablen, Heap zugewiesener Speicher und sogar Schreib geschütztem Arbeitsspeicher auf einigen CPUs stattfindet. Für den Stapel zugeordneten Arbeitsspeicher führt der Microsoft C++-Compiler bereits Schritte aus, um das spekulative Ändern der durch den Stapel zugewiesenen indirekten Verzweigungs Ziele zu erschweren, wie z. b. durch Neuanordnen von lokalen Variablen, sodass Puffer neben einem Sicherheits Cookie als Teil der [`/GS`](../build/reference/gs-buffer-security-check.md) compilersicherheitsfunktion platziert werden.

## <a name="speculative-type-confusion"></a>Spekulative typverwirrung

Diese Kategorie behandelt Codierungs Muster, die eine spekulative typverwirrung verursachen können. Dies tritt auf, wenn während der spekulativen Ausführung auf den Speicher mit einem falschen Typ auf einem nicht architektonischen Pfad zugegriffen wird. Sowohl bedingte Verzweigungs-als auch spekulative Speicher Umgehungen können möglicherweise zu einer spekulativen typverwirrung führen.

Bei der Umgehung des spekulativen Stores kann dies in Szenarios auftreten, in denen ein Compiler einen Stapel Speicherort für Variablen mehrerer Typen wieder verwendet. Dies liegt daran, dass der Architektur Speicher einer Variablen vom Typ `A` umgangen werden kann, sodass das Laden des Typs `A` vor der Zuweisung der Variablen spekulativ ausgeführt werden kann. Wenn die zuvor gespeicherte Variable einen anderen Typ hat, können dadurch die Bedingungen für eine spekulative typverwechslung erstellt werden.

Für die bedingte Verzweigung midepdiction wird der folgende Code Ausschnitt verwendet, um unterschiedliche Bedingungen zu beschreiben, für die spekulative typverwirrung entstehen kann.

```cpp
enum TypeName {
    Type1,
    Type2
};

class CBaseType {
public:
    CBaseType(TypeName type) : type(type) {}
    TypeName type;
};

class CType1 : public CBaseType {
public:
    CType1() : CBaseType(Type1) {}
    char field1[256];
    unsigned char field2;
};

class CType2 : public CBaseType {
public:
    CType2() : CBaseType(Type2) {}
    void (*dispatch_routine)();
    unsigned char field2;
};

// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ProcessType(CBaseType *obj)
{
    if (obj->type == Type1) {
        // SPECULATION BARRIER
        CType1 *obj1 = static_cast<CType1 *>(obj);

        unsigned char value = obj1->field2;

        return shared_buffer[value * 4096];
    }
    else if (obj->type == Type2) {
        // SPECULATION BARRIER
        CType2 *obj2 = static_cast<CType2 *>(obj);

        obj2->dispatch_routine();

        return obj2->field2;
    }
}
```

### <a name="speculative-type-confusion-leading-to-an-out-of-bounds-load"></a>Spekulative typverwirrung, die zu einer Auslastung außerhalb des gültigen Bereichs führt

Dieses Codierungs Muster umfasst die Groß-/Kleinschreibung, bei der eine spekulative typverwirrung zu einem nicht gültigen oder typverwirrten Feld Zugriff führen kann, bei dem der geladene Wert eine nachfolgende Lade Adresse als Feed eingibt. Dies ähnelt dem Array für das Out-of-Bounds-Codierungs Muster, wird jedoch durch eine Alternative Codierungs Sequenz dargestellt, wie oben gezeigt. In diesem Beispiel könnte ein Angriffs Kontext bewirken, dass der Opfer Kontext mehrmals `ProcessType` mit einem Objekt des Typs `CType1` ( `type` Feld ist gleich) ausgeführt wird `Type1` . Dies hat den Effekt, dass die bedingte Verzweigung für die erste **`if`** Anweisung trainiert wird, um vorherzusagen, dass Sie nicht übernommen wurde. Der Angriffs Kontext kann dann bewirken, dass der Opfer Kontext `ProcessType` mit einem Objekt des Typs ausgeführt wird `CType2` . Dies kann zu einer spekulativen typverwirrung führen, wenn die bedingte Verzweigung für die erste **`if`** Anweisung den Text der Anweisung falsch eingibt und ausführt **`if`** , wodurch ein Objekt vom Typ in umgewandelt wird `CType2` `CType1` . Da `CType2` kleiner als ist `CType1` , führt der Speicherzugriff auf zu `CType1::field2` einer spekulativen ausgehenden Daten Last, die möglicherweise geheim ist. Dieser Wert wird dann in einem Ladevorgang verwendet `shared_buffer` , von dem Observable-Nebeneffekte erstellt werden können, wie im zuvor beschriebenen Beispiel für ein Out-of-Bounds-Array.

### <a name="speculative-type-confusion-leading-to-an-indirect-branch"></a>Spekulative typverwirrung, die zu einem indirekten Branch führt

Dieses Codierungs Muster bezieht sich auf den Fall, in dem eine spekulative typverwirrung während der spekulativen Ausführung zu einer unsicheren indirekten Verzweigung führen kann. In diesem Beispiel könnte ein Angriffs Kontext bewirken, dass der Opfer Kontext mehrmals `ProcessType` mit einem Objekt des Typs `CType2` ( `type` Feld ist gleich) ausgeführt wird `Type2` . Dies hat die Auswirkung, den bedingten Branch für die erste auszuführende **`if`** Anweisung zu trainieren, und die `else if` Anweisung wird nicht übernommen. Der Angriffs Kontext kann dann bewirken, dass der Opfer Kontext `ProcessType` mit einem Objekt des Typs ausgeführt wird `CType1` . Dies kann zu einer spekulativen typverwirrung führen, wenn die bedingte Verzweigung für die erste **`if`** Anweisung erstellt wird und die- `else if` Anweisung nicht akzeptiert wird. Dadurch wird der Hauptteil der ausgeführt `else if` und ein Objekt vom Typ `CType1` in umgewandelt `CType2` . Da `CType2::dispatch_routine` sich das Feld mit dem **`char`** Array überlappt `CType1::field1` , könnte dies zu einer spekulativen indirekten Verzweigung in einem unbeabsichtigten Verzweigungs Ziel führen. Wenn der Angriffs Kontext die Byte Werte im Array steuern kann `CType1::field1` , kann er möglicherweise die Zieladresse der Verzweigung steuern.

## <a name="speculative-uninitialized-use"></a>Spekulative nicht initialisierte Verwendung

Diese Kategorie von Codierungs Mustern umfasst Szenarien, in denen die spekulative Ausführung möglicherweise auf nicht initialisierten Speicher zugreift und Sie zum Feed einer nachfolgenden Last oder indirekten Verzweigung verwendet. Damit diese Codierungs Muster ausgenutzt werden können, muss ein Angreifer in der Lage sein, den Inhalt des Arbeitsspeichers, der verwendet wird, zu steuern oder sinnvoll zu beeinflussen, ohne durch den Kontext initialisiert zu werden, in dem er verwendet wird.

### <a name="speculative-uninitialized-use-leading-to-an-out-of-bounds-load"></a>Die spekulative nicht initialisierte Verwendung führt zu einer Auslastung außerhalb des gültigen Bereichs.

Eine spekulative nicht initialisierte Verwendung kann möglicherweise zu einer Auslastung außerhalb des gültigen Bereichs führen, die einen von Angreifern kontrollierten Wert verwendet. Im folgenden Beispiel wird der Wert von `index` `trusted_index` auf allen Architektur Pfaden zugewiesen, und `trusted_index` es wird davon ausgegangen, dass er kleiner als oder gleich ist `buffer_size` . Abhängig vom Code, der vom Compiler erzeugt wird, kann es jedoch vorkommen, dass eine spekulative Speicher Umgehung stattfindet, mit der die Auslastung von `buffer[index]` und abhängigen Ausdrücken vor der Zuweisung zu ausgeführt werden kann `index` . Wenn dies der Fall ist, wird ein nicht initialisierter Wert für `index` als Offset verwendet, `buffer` der es einem Angreifer ermöglichen könnte, vertrauliche Informationen außerhalb der Grenzen zu lesen und diese über einen seitigen Kanal durch die abhängige Auslastung von zu übermitteln `shared_buffer` .

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

void InitializeIndex(unsigned int trusted_index, unsigned int *index) {
    *index = trusted_index;
}

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int trusted_index) {
    unsigned int index;

    InitializeIndex(trusted_index, &index); // not inlined

    // SPECULATION BARRIER
    unsigned char value = buffer[index];
    return shared_buffer[value * 4096];
}
```

### <a name="speculative-uninitialized-use-leading-to-an-indirect-branch"></a>Spekulative nicht initialisierte Verwendung, die zu einem indirekten Branch führt

Eine spekulative nicht initialisierte Verwendung kann potenziell zu einer indirekten Verzweigung führen, bei der das branchziel von einem Angreifer gesteuert wird. Im folgenden Beispiel `routine` wird entweder oder zugewiesen, `DefaultMessageRoutine1` `DefaultMessageRoutine` abhängig vom Wert von `mode` . Im Architektur Pfad führt dies dazu, `routine` dass immer vor der indirekten Verzweigung initialisiert wird. Abhängig vom Code, der vom Compiler erzeugt wird, kann jedoch eine spekulative Speicher Umgehung auftreten, die es ermöglicht, dass die indirekte Verzweigung `routine` vor der Zuweisung zu spekulativ ausgeführt wird `routine` . Wenn dies auftritt, kann ein Angreifer möglicherweise eine willkürliche Ausführung von einer beliebigen Adresse ausführen, vorausgesetzt, der Angreifer kann den nicht initialisierten Wert von beeinflussen oder Steuern `routine` .

```cpp
#define MAX_MESSAGE_ID 16

typedef void (*MESSAGE_ROUTINE)(unsigned char *buffer, unsigned int buffer_size);

const MESSAGE_ROUTINE DispatchTable[MAX_MESSAGE_ID];
extern unsigned int mode;

void InitializeRoutine(MESSAGE_ROUTINE *routine) {
    if (mode == 1) {
        *routine = &DefaultMessageRoutine1;
    }
    else {
        *routine = &DefaultMessageRoutine;
    }
}

void DispatchMessage(unsigned int untrusted_message_id, unsigned char *buffer, unsigned int buffer_size) {
    MESSAGE_ROUTINE routine;

    InitializeRoutine(&routine); // not inlined

    // SPECULATION BARRIER
    routine(buffer, buffer_size);
}
```

## <a name="mitigation-options"></a>Abhilfeoptionen

Sicherheitsanfälligkeiten für die spekulative Ausführungs Seite können durch Änderungen am Quellcode verringert werden. Diese Änderungen können dazu führen, dass bestimmte Instanzen eines Sicherheitsrisikos abgemindert werden, z. b. durch Hinzufügen einer *Spekulations Barriere*oder durch Ändern des Entwurfs einer Anwendung, um sensible Informationen für die spekulative Ausführung nicht zugänglich zu machen.

### <a name="speculation-barrier-via-manual-instrumentation"></a>Spekulations Barriere durch manuelle Instrumentierung

Eine *Spekulations Barriere* kann von einem Entwickler manuell eingefügt werden, um zu verhindern, dass die spekulative Ausführung an einem nicht-architektonischen Pfad fortgesetzt wird. Ein Entwickler kann z. b. eine Spekulations Barriere vor einem gefährlichen Codierungs Muster im Text eines bedingten Blocks einfügen, entweder am Anfang des Blocks (nach dem bedingten Branch) oder vor dem ersten zu überprüfenden Problem. Dadurch wird verhindert, dass eine bedingte Verzweigung den gefährlichen Code in einem nicht architektonischen Pfad ausführt, indem die Ausführung serialisiert wird. Die Spekulations Barriere unterscheidet sich von der Hardwarearchitektur, wie in der folgenden Tabelle beschrieben:

|Aufbau|Systeminterne Spekulations Barriere für CVE-2017-5753|Systeminterne Spekulations Barriere für CVE-2018-3639|
|----------------|----------------|----------------|
|x86/x64|_mm_lfence ()|_mm_lfence ()|
|ARM|aktuell nicht verfügbar|__dsb (0)|
|ARM64|aktuell nicht verfügbar|__dsb (0)|

Beispielsweise kann das folgende Code muster mithilfe der systeminternen Funktion, `_mm_lfence` wie unten dargestellt, verringert werden.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        _mm_lfence();
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="speculation-barrier-via-compiler-time-instrumentation"></a>Spekulations Barriere durch compilerzeit Instrumentation

Der Microsoft C++-Compiler in Visual Studio 2017 (beginnend mit Version 15.5.5) umfasst die Unterstützung für den `/Qspectre` Switch, der automatisch eine Spekulations Barriere für einen begrenzten Satz potenziell anfälliger Codierungs Muster im Zusammenhang mit CVE-2017-5753 einfügt. In der Dokumentation für das- [`/Qspectre`](../build/reference/qspectre.md) Flag finden Sie weitere Informationen zu den Auswirkungen und der Verwendung. Es ist wichtig zu beachten, dass dieses Flag nicht alle potenziell anfälligen Codierungs Muster abdeckt und solche Entwickler nicht als umfassende Entschärfung für diese Klasse von Sicherheitsrisiken verlassen sollten.

### <a name="masking-array-indices"></a>Maskieren von Array Indizes

In Fällen, in denen eine spekulative out-of-Bounds-Auslastung auftreten kann, kann der Array Index sowohl für den Architektur-als auch den nicht-architektonischen Pfad begrenzt werden, indem Logik zum expliziten Binden des Array Indexes hinzugefügt wird. Wenn ein Array z. b. einer Größe zugeordnet werden kann, die auf eine Potenz von zwei ausgerichtet ist, kann eine einfache Maske eingefügt werden. Dies wird im folgenden Beispiel veranschaulicht, wobei angenommen wird, dass `buffer_size` auf eine Potenz von zwei ausgerichtet ist. Dadurch wird sichergestellt, dass `untrusted_index` immer kleiner als ist `buffer_size` , auch wenn eine bedingte Verzweigung nicht ausgeführt wird und `untrusted_index` mit einem Wert übergeben wurde, der größer oder gleich ist `buffer_size` .

Beachten Sie, dass die hier ausgeführte Index Maskierung je nach dem vom Compiler generierten Code eine spekulative Speicher Umgehung unterliegen kann.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        untrusted_index &= (buffer_size - 1);
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="removing-sensitive-information-from-memory"></a>Entfernen von sensiblen Informationen aus dem Arbeitsspeicher

Ein weiteres Verfahren, das verwendet werden kann, um die Sicherheitsrisiken für spekulative Ausführungs Seiten zu vermeiden, besteht darin, vertrauliche Informationen aus dem Arbeitsspeicher Software Entwickler können nach Möglichkeiten zum Umgestalten ihrer Anwendung suchen, damit vertrauliche Informationen während der spekulativen Ausführung nicht zugänglich sind. Dies kann erreicht werden, indem Sie den Entwurf einer Anwendung umgestalten, um sensible Informationen in separaten Prozessen zu isolieren. Beispielsweise kann eine Webbrowser Anwendung versuchen, die den einzelnen Webrollen zugeordneten Daten in separaten Prozessen zu isolieren. so kann verhindert werden, dass ein Prozess über die spekulative Ausführung auf Ursprungs übergreifende Daten zugreifen kann.

## <a name="see-also"></a>Weitere Informationen

[Leitfaden zur Vermeidung von Sicherheitsrisiken für den spekulativen Ausführungs Rand](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002)<br/>
[Mindern von Sicherheitsrisiken bei der Vermeidung von spekulativen Ausführungs seitigen Kanälen](https://blogs.technet.microsoft.com/srd/2018/03/15/mitigating-speculative-execution-side-channel-hardware-vulnerabilities/)
