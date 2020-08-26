---
title: Ausnahmebehandlung bei x64-Systemen
ms.date: 10/14/2019
helpviewer_keywords:
- C++ exception handling, x64
- exception handling, x64
ms.assetid: 41fecd2d-3717-4643-b21c-65dcd2f18c93
ms.openlocfilehash: 3d973354f94ca8c9f2e0901e60f2a8009ac08cd6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835050"
---
# <a name="x64-exception-handling"></a>Ausnahmebehandlung bei x64-Systemen

Hier finden Sie eine Übersicht über die strukturierte Ausnahmebehandlung, die C++-Ausnahmebehandlung, Programmierkonventionen und Verhaltensweisen unter x64. Allgemeine Informationen zur Behandlung von Ausnahmen finden Sie unter [Ausnahmebehandlung in Visual C++](../cpp/exception-handling-in-visual-cpp.md).

## <a name="unwind-data-for-exception-handling-debugger-support"></a>Entladen von Daten für die Ausnahmebehandlung, Debuggerunterstützung

Für die Unterstützung der Ausnahmebehandlung und des Debuggens sind mehrere Datenstrukturen erforderlich.

### <a name="struct-runtime_function"></a>struct RUNTIME_FUNCTION

Die tabellenbasierte Ausnahmebehandlung erfordert einen Tabelleneintrag für alle Funktionen, die Stapelspeicher zuordnen oder eine andere Funktion (z. B. Non-Leaf-Funktionen) aufrufen. Funktionstabelleneinträge weisen das folgende Format auf:

|Size|Wert|
|-|-|
|ULONG|Startadresse der Funktion|
|ULONG|Endadresse der Funktion|
|ULONG|Informationsadresse zum Entladen|

Die RUNTIME_FUNCTION-Struktur muss im Arbeitsspeicher auf DWORD ausgerichtet sein. Alle Adressen sind imagerelativ, also 32-Bit-Offsets von der Startadresse des Images, das den Funktionstabelleneintrag enthält. Diese Einträge werden sortiert und im PDATA-Abschnitt eines PE32+-Images eingefügt. Bei dynamisch generierten Funktionen (JIT-Compiler) muss die Runtime zur Unterstützung dieser Funktionen entweder RtlInstallFunctionTableCallback oder RtlAddFunctionTable verwenden, um diese Informationen für das Betriebssystem bereitzustellen. Andernfalls können Ausnahmen unzuverlässig behandelt und Prozesse unzuverlässig gedebuggt werden.

### <a name="struct-unwind_info"></a>struct UNWIND_INFO

Die Informationsstruktur für Entladeinformationen wird verwendet, um die Auswirkungen einer Funktion auf den Stapelzeiger aufzuzeichnen, und um den Speicherort nicht flüchtiger Register im Stapel anzugeben:

|Size|Wert|
|-|-|
|UBYTE: 3|Version|
|UBYTE: 5|Flags|
|UBYTE|Prologgröße|
|UBYTE|Anzahl der Entladungscodes|
|UBYTE: 4|Frameregister|
|UBYTE: 4|Frameregisteroffset (skaliert)|
|USHORT \* n|Entladungscodearray|
|-Variable|Kann entweder dem folgenden Format (1) oder (2) entsprechen|

(1) Ausnahmehandler

|Size|Wert|
|-|-|
|ULONG|Adresse des Ausnahmehandlers|
|-Variable|Sprachspezifische Handlerdaten (optional)|

(2) Verkettete Entladeinformationen

|Size|Wert|
|-|-|
|ULONG|Startadresse der Funktion|
|ULONG|Endadresse der Funktion|
|ULONG|Informationsadresse zum Entladen|

Die UNWIND_INFO-Struktur muss im Arbeitsspeicher auf DWORD ausgerichtet sein. Die einzelnen Felder bedeuten Folgendes:

- **Version**

   Versionsnummer der Entladedaten, derzeit 1

- **Flags**

   Derzeit sind drei Flags definiert:

   |Flag|Beschreibung|
   |-|-|
   |`UNW_FLAG_EHANDLER`| Die Funktion enthält einen Ausnahmehandler, der bei der Suche nach Funktionen aufgerufen werden muss, die Ausnahmen untersuchen müssen.|
   |`UNW_FLAG_UHANDLER`| Die Funktion verfügt über einen Beendigungshandler, der beim Entladen einer Ausnahme aufgerufen werden sollte.|
   |`UNW_FLAG_CHAININFO`| Diese Entladeinformationsstruktur ist nicht die primäre Struktur für die Prozedur, denn der Eintrag der verketteten Entladeinformationen ist der Inhalt eines vorherigen RUNTIME_FUNCTION-Eintrags. Weitere Informationen finden Sie unter [Verkettete Entladeinformationsstrukturen](#chained-unwind-info-structures). Wenn dieses Flag festgelegt ist, müssen die Flags UNW_FLAG_EHANDLER und UNW_FLAG_UHANDLER gelöscht werden. Außerdem müssen die Felder für das Frameregister und die feste Stapelzuordnung dieselben Werte wie die primären Entladeinformationen aufweisen.|

- **Prologgröße**

   Die Länge des Funktionsprologs in Bytes

- **Anzahl der Entladungscodes**

   Die Anzahl der Slots im Array der Entladungscodes, wobei einige Entladungscodes wie UWOP_SAVE_NONVOL mehr als einen Slot im Array benötigen

- **Frameregister**

   Wenn dieses ungleich 0 (null) ist, verwendet die Funktion einen Framezeiger (Frame Pointer, FP), und dieses Feld wird mit der Nummer des nicht flüchtigen Registers aufgefüllt, das als Framezeiger verwendet wird. Dabei wird die gleiche Codierung für das Informationsfeld für Vorgänge des UNWIND_CODE-Knotens verwendet.

- **Frameregisteroffset (skaliert)**

   Wenn das Frameregisterfeld ungleich 0 (null) ist, wird dieses Feld mit dem skalierten Offset des RSP (Register Stack Pointer, Registerstapelzeiger) aufgefüllt, der bei der Erstellung auf das FP-Register angewendet wird. Das tatsächliche FP-Register wird auf „RSP + 16 \* n“ festgelegt, sodass Offsets zwischen 0 und 240 möglich sind. Dieser Offset ermöglicht das Verweisen auf das FP-Register in der Mitte der lokalen Stapelzuordnung für dynamische Stapelrahmen. Dadurch wird die Codedichte verbessert, da die Anweisungen kürzer sind. (Das heißt, dass mehr Anweisungen im 8-Bit-Offsetformat mit Vorzeichen verwendet werden können.)

- **Entladungscodearray**

   Ein Elementarray, das die Auswirkung des Prologs auf die nicht flüchtigen Register und RSPs erklärt, Informationen zu den Bedeutungen einzelner Elemente finden Sie im Abschnitt zu UNWIND_CODE. Für eine optimale Ausrichtung enthält dieses Array immer eine gerade Anzahl von Einträgen, und der letzte Eintrag wird möglicherweise nicht verwendet. In diesem Fall ist das Array um ein Element länger als durch das Feld für die Anzahl der Entladungscodes angegeben.

- **Adresse des Ausnahmehandlers**

   Ein imagerelativer Zeiger auf den sprachspezifischen Ausnahme- oder Beendigungshandler der Funktion, wenn das Flag UNW_FLAG_CHAININFO leer und das Flag UNW_FLAG_EHANDLER oder UNW_FLAG_UHANDLER festgelegt ist.

- **Sprachspezifische Handlerdaten**

   Die sprachspezifischen Ausnahmehandlerdaten der Funktion – das Format dieser Daten ist nicht angegeben und wird vollständig durch den verwendeten Ausnahmehandler bestimmt.

- **Verkettete Entladeinformationen**

   Wenn das Flag UNW_FLAG_CHAININFO festgelegt ist, endet die UNWIND_INFO-Struktur mit drei UWORD-Elementen.  Diese UWORD-Elemente stellen die RUNTIME_FUNCTION-Informationen für die Funktion der verketteten Entladung dar.

### <a name="struct-unwind_code"></a>struct UNWIND_CODE

Das Entladungscodearray wird verwendet, um die Abfolge der Vorgänge im Prolog aufzuzeichnen, die sich auf die nicht flüchtigen Register und RSPs auswirken. Jedes Codeelement weist das folgende Format auf:

|Size|Wert|
|-|-|
|UBYTE|Offset im Prolog|
|UBYTE: 4|Code für den Entladevorgang|
|UBYTE: 4|Vorgangsinformationen|

Das Array wird absteigender Reihenfolge des Offsets im Prolog sortiert.

#### <a name="offset-in-prolog"></a>Offset im Prolog

Der Offset (ab dem Anfang des Prologs) am Ende der Anweisung, die diesen Vorgang ausführt, plus 1 (d. h. der Offset am Anfang der nächsten Anweisung)

#### <a name="unwind-operation-code"></a>Code für den Entladevorgang

Hinweis: Bestimmte Opcodes erfordern einen Offset ohne Vorzeichen für einen Wert im lokalen Stapelrahmen. Dieser Offset wird am Anfang hinzugefügt, also zur niedrigsten Adresse der festen Stapelzuordnung. Wenn das Frameregisterfeld in UNWIND_INFO gleich 0 (null) ist, wird dieser Offset zum RSP hinzugefügt. Wenn das Frameregisterfeld ungleich 0 (null) ist, wird dieser Offset an der Position des RSP hinzugefügt, als das FP-Register erstellt wurde. Es entspricht dem FP-Register abzüglich des FP-Registeroffsets (16 \* skalierter Frameregisteroffset in UNWIND_INFO). Wenn ein FP-Register verwendet wird, darf jeder Entladungscode, der einen Offset verwendet, erst verwendet werden, nachdem das FP-Register im Prolog erstellt wurde.

Für alle Opcodes mit Ausnahme von `UWOP_SAVE_XMM128` und `UWOP_SAVE_XMM128_FAR` ist der Offset immer ein Vielfaches von 8, da alle relevanten Stapelwerte in 8-Byte-Grenzen gespeichert werden (der Stapel selbst ist immer auf 16 Byte ausgerichtet). Bei Opcodes mit kurzem Offset (weniger als 512 KB) enthält das abschließende USHORT-Schlüsselwort in den Knoten für diesen Code den Offset geteilt durch 8. Bei Opcodes mit langem Offset (512 KB <= Offset < 4 GB) enthalten die letzten beiden USHORT-Knoten für diesen Code den Offset (im Little-Endian-Format).

Für die Opcodes `UWOP_SAVE_XMM128` und `UWOP_SAVE_XMM128_FAR` ist der Offset immer ein Vielfaches von 16, da alle 128-Bit-XMM-Vorgänge in einem auf 16 Byte ausgerichteten Arbeitsspeicher ausgeführt werden müssen. Aus diesem Grund wird ein Skalierungsfaktor von 16 für `UWOP_SAVE_XMM128` verwendet, der Offsets von weniger als 1 MB zulässt.

Der Code für den Entladungsvorgang entspricht einem der folgenden Werte:

- `UWOP_PUSH_NONVOL` (0) 1 Knoten

  Ein nicht flüchtiges Integerregister wird übertragen, und der RSP wird um 8 dekrementiert. Die Registernummer entspricht den Vorgangsinformationen. Aufgrund der Einschränkungen für Epiloge müssen `UWOP_PUSH_NONVOL`-Entladungscodes zuerst im Prolog und zuletzt im Entladungscodearray angezeigt werden. Diese relative Reihenfolge gilt für alle weiteren Entladungscodes außer `UWOP_PUSH_MACHFRAME`.

- `UWOP_ALLOC_LARGE` (1) 2 oder 3 Knoten

  Hiermit wird dem Stapel ein großer Bereich zugewiesen. Es gibt zwei Varianten. Wenn die Vorgangsinformationen gleich 0 (null) sind, wird die Größe der Zuordnung geteilt durch 8 im nächsten Slot aufgezeichnet, sodass eine Zuordnung von bis zu 512 KB – 8 möglich ist. Wenn die Vorgangsinformationen gleich 1 sind, wird die nicht skalierte Größe der Zuordnung in den nächsten zwei Slots im Little-Endian-Format aufgezeichnet, sodass eine Zuordnung von bis zu 4 GB – 8 möglich ist.

- `UWOP_ALLOC_SMALL` (2) 1 Knoten

  Hiermit wird dem Stapel ein kleiner Bereich zugewiesen. Die Größe der Zuordnung entspricht dem Feld für Vorgangsinformationen \* 8 + 8, sodass eine Zuordnung von 8 bis 128 Bytes möglich ist.

  Für den Entladungscode einer Stapelzuordnung sollte immer die kürzestmögliche Codierung verwendet werden:

  |**Zuordnungsgröße**|**Entladungscode**|
  |-|-|
  |8 bis 128 Bytes|`UWOP_ALLOC_SMALL`|
  |136 bis 512 KB – 8 Byte|`UWOP_ALLOC_LARGE`, Vorgangsinformationen = 0|
  |512 KB bis 4 GB – 8 Byte|`UWOP_ALLOC_LARGE`, Vorgangsinformationen = 1|

- `UWOP_SET_FPREG` (3) 1 Knoten

  Richten Sie das FP-Register ein, indem Sie es auf einen Offset des aktuellen RSP festlegen. Der Offset ist gleich dem Feld „Frameregisteroffset (skaliert)“ in UNWIND_INFO \* 16, sodass Offsets zwischen 0 und 240 möglich sind. Durch die Verwendung eines Offsets kann ein Framezeiger festgelegt werden, der auf die Mitte der festen Stapelzuordnung zeigt, wodurch die Codedichte verbessert wird, indem mehr Zugriffe auf kurze Anweisungsformen möglich sind. Das Feld für die Vorgangsinformationen ist reserviert und sollte nicht verwendet werden.

- `UWOP_SAVE_NONVOL` (4) 2 Knoten

  Verwenden Sie MOV statt PUSH, um ein nicht flüchtiges Integerregister im Stapel zu speichern. Dieser Code wird hauptsächlich für das *Shrink Wrapping* verwendet, bei dem ein nicht flüchtiges Register im Stapel an einer zuvor zugewiesenen Position gespeichert wird. Die Registernummer entspricht den Vorgangsinformationen. Der Offset des nach 8 skalierten Stapels wird wie zuvor beschrieben im nächsten Codeslot des Entladevorgangs aufgezeichnet.

- `UWOP_SAVE_NONVOL_FAR` (5) 3 Knoten

  Speichern Sie ein nicht flüchtiges Integerregister im Stapel mit einem langen Offset, und verwenden Sie dabei MOV anstelle von PUSH. Dieser Code wird hauptsächlich für das *Shrink Wrapping* verwendet, bei dem ein nicht flüchtiges Register im Stapel an einer zuvor zugewiesenen Position gespeichert wird. Die Registernummer entspricht den Vorgangsinformationen. Der Offset des nicht skalierten Stapels wird wie zuvor beschrieben in den nächsten zwei Codeslots des Entladevorgangs aufgezeichnet.

- `UWOP_SAVE_XMM128` (8) 2 Knoten

  Speichert alle 128 Bit eines nicht flüchtigen XMM-Registers im Stapel. Die Registernummer entspricht den Vorgangsinformationen. Der Offset des nach 16 skalierten Stapels wird im nächsten Slot aufgezeichnet.

- `UWOP_SAVE_XMM128_FAR` (9) 3 Knoten

  Speichert alle 128 Bit eines nicht flüchtigen XMM-Registers im Stapel mit langem Offset. Die Registernummer entspricht den Vorgangsinformationen. Der Offset des nicht skalierten Stapels wird in den nächsten beiden Slot aufgezeichnet.

- `UWOP_PUSH_MACHFRAME` (10) 1 Knoten

  Ein Computerframe wird übertragen.  Dieser Entladungscode wird verwendet, um die Auswirkungen von Hardwareunterbrechungen oder Ausnahmen aufzuzeichnen. Es gibt zwei Varianten. Wenn die Vorgangsinformationen gleich 0 (null) sind, wurde einer dieser Frames an den Stapel übertragen:

  |Position|Wert|
  |-|-|
  |RSP + 32|SS|
  |RSP + 24|RSP (alt)|
  |RSP + 16|EFLAGS|
  |RSP + 8|CS|
  |RSP|RIP|

  Wenn die Vorgangsinformationen gleich 1 sind, wurde einer dieser Frames übertragen:

  |Position|Wert|
  |-|-|
  |RSP + 40|SS|
  |RSP + 32|RSP (alt)|
  |RSP + 24|EFLAGS|
  |RSP + 16|CS|
  |RSP + 8|RIP|
  |RSP|Fehlercode|

  Dieser Entladungscode wird immer in einem Dummyprolog angezeigt, der nie ausgeführt, sondern vor dem tatsächlichen Einstiegspunkt einer Unterbrechungsroutine angezeigt wird. Er ist nur vorhanden, um die Übertragung eines Computerframes zu simulieren. `UWOP_PUSH_MACHFRAME` zeichnet diese Simulation auf. Daraus geht hervor, dass der Computer diesen Vorgang konzeptionell ausgeführt hat:

  1. RIP-Rückgabeadresse von der obersten Position des Stapels in *Temp* verschieben
  
  1. SS übertragen

  1. Alten RSP übertragen

  1. EFLAGS übertragen

  1. CS übertragen

  1. *Temp* übertragen

  1. Pushfehlercode (wenn die Vorgangsinformationen gleich 1 sind)

  Der simulierte `UWOP_PUSH_MACHFRAME`-Vorgang dekrementiert den RSP um 40 (Vorgangsinformationen gleich 0) oder um 48 (Vorgangsinformationen gleich 1).

#### <a name="operation-info"></a>Vorgangsinformationen

Die Bedeutung der einzelnen Bits der Vorgangsinformationen hängt vom Opcode ab. Folgende Zuordnung wird verwendet, um ein allgemeines Register (Integer) zu codieren:

|bit|Registrieren|
|-|-|
|0|RAX|
|1|RCX|
|2|RDX|
|3|RBX|
|4|RSP|
|5|RBP|
|6|RSI|
|7|RDI|
|8 bis 15|R8 bis R15|

### <a name="chained-unwind-info-structures"></a>Verkettete Entladeinformationsstrukturen

Wenn das Flag UNW_FLAG_CHAININFO festgelegt ist, ist eine Entladeinformationsstruktur eine sekundäre Struktur, und das Adressfeld für den gemeinsam genutzten Ausnahmehandler und die verketteten Informationen enthält die primären Entladeinformationen. Dieser Beispielcode ruft die primären Entladeinformationen ab. Hierbei wird angenommen, dass `unwindInfo` die Struktur ist, für die das Flag UNW_FLAG_CHAININFO festgelegt ist.

```cpp
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

Verkettete Informationen sind in zwei Situationen nützlich. Sie können einerseits für nicht zusammenhängende Codesegmente verwendet werden. Durch die Verwendung von verketteten Informationen können Sie die Größe der erforderlichen Entladeinformationen reduzieren, da Sie das Array für Entladungscodes nicht aus den primären Entladeinformationen duplizieren müssen.

Sie können verkettete Informationen andererseits verwenden, um flüchtige Registerspeicherungen zu gruppieren. Der Compiler kann die Speicherung einiger flüchtiger Register verzögern, bis er sich außerhalb des Prologs für den Funktionseinstieg befindet. Sie können diese aufzeichnen, indem die primären Entladeinformationen für diesen Teil der Funktion vor dem gruppierten Code eingefügt und die verketteten Informationen dann mit einem Prolog eingerichtet werden, der ungleich 0 ist und bei dem die Entladungscodes in den verketteten Informationen Speicherungen der nicht flüchtigen Register darstellen. In diesem Fall sind alle Entladungscodes Instanzen von UWOP_SAVE_NONVOL. Eine Gruppierung, die nicht flüchtige Register mithilfe von PUSH speichert oder das RSP-Register mithilfe einer zusätzlichen festen Stapelzuordnung ändert, wird nicht unterstützt.

Ein UNWIND_INFO-Element, bei dem UNW_FLAG_CHAININFO festgelegt ist, kann einen RUNTIME_FUNCTION-Eintrag enthalten, bei dessen UNWIND_INFO-Element ebenfalls UNW_FLAG_CHAININFO festgelegt ist. Das wird manchmal als *mehrfaches Shrink Wrapping* bezeichnet. Schließlich gelangen die verketteten Zeiger für Entladeinformationen bei einem UNWIND_INFO-Element an, bei dem UNW_FLAG_CHAININFO leer ist. Bei diesem Element handelt es sich um das primäre UNWIND_INFO-Element, das auf den eigentlichen Einstiegspunkt der Prozedur zeigt.

## <a name="unwind-procedure"></a>Entladeprozedur

Das Entladungscodearray wird in absteigender Reihenfolge sortiert. Wenn eine Ausnahme auftritt, wird der gesamte Kontext vom Betriebssystem in einem Kontextdatensatz gespeichert. Anschließend wird die Dispatchlogik für Ausnahmen aufgerufen, die wiederholt die folgenden Schritte ausführt, um einen Ausnahmehandler zu finden:

1. Verwenden Sie den aktuellen RIP (Return Instruction Pointer, Zeiger für Rückgabeanweisungen), der im Kontextdatensatz gespeichert ist, um nach einem RUNTIME_FUNCTION-Tabelleneintrag zu suchen, der die aktuelle Funktion (oder den Funktionsteil für verkettete UNWIND_INFO-Einträge) beschreibt.

1. Wenn kein Funktionstabelleneintrag gefunden wird, befindet er sich in einer Leaf-Funktion, und der RSP steuert direkt den Rückgabezeiger an. Der Rückgabezeiger bei [rsp] wird im aktualisierten Kontext gespeichert. Der simulierte RSP wird um 8 inkrementiert, und Schritt 1 wird wiederholt.

1. Wenn ein Funktionstabelleneintrag gefunden wird, kann der RIP innerhalb von drei Bereichen liegen: a) in einem Epilog, b) im Prolog oder c) im Code, der möglicherweise von einem Ausnahmehandler abgedeckt wird.

   - Fall a) Wenn der RIP innerhalb eines Epilogs liegt, verlässt das Steuerelement die Funktion, der Ausnahme für diese Funktion kann kein Ausnahmehandler zugeordnet werden, und die Auswirkungen des Epilogs müssen fortgesetzt werden, damit der Kontext der aufrufenden Funktion berechnet werden kann. Der Codestream wird vom RIP aus weiter untersucht, um zu ermitteln, ob sich der RIP in einem Epilog befindet. Wenn dieser Codestream mit dem nachfolgenden Teil eines legitimen Epilogs übereinstimmt, befindet er sich in einem Epilog, und der verbleibende Teil des Epilogs wird simuliert, wobei der Kontextdatensatz bei der Verarbeitung jeder Anweisung aktualisiert wird. Nach diesem Vorgang wird Schritt 1 wiederholt.

   - Fall b) Wenn der RIP innerhalb eines Prologs liegt, hat das Steuerelement die Funktion noch nicht verarbeitet, der Ausnahme für diese Funktion kann kein Ausnahmehandler zugeordnet werden, und die Auswirkungen des Prologs müssen rückgängig gemacht werden, damit der Kontext der aufrufenden Funktion berechnet werden kann. Der RIP befindet sich innerhalb des Prologs, wenn der Abstand vom Funktionsbeginn zum RIP-Wert kleiner oder gleich der in den Entladeinformationen codierten Prologgröße ist. Die Auswirkungen des Prologs werden entladen, indem das Entladungscodearrays für den ersten Eintrag mit einem Offset durchsucht wird, der kleiner oder gleich dem Offset des RIP von Funktionsbeginn an ist, und die Auswirkung aller verbleibenden Elemente im Entladungscodearray rückgängig gemacht werden. Anschließend wird Schritt 1 wiederholt.

   - Fall c) Wenn der RIP nicht innerhalb eines Prologs oder Epilogs liegt und die Funktion über einen Ausnahmehandler verfügt (UNW_FLAG_EHANDLER ist festgelegt), wird der sprachspezifische Handler aufgerufen. Der Handler scannt die Daten und ruft diesen entsprechend Filterfunktionen auf. Der sprachspezifische Handler kann zurückgeben, dass die Ausnahme behandelt wurde oder dass die Suche fortgesetzt werden soll. Außerdem kann eine Entladung direkt initiiert werden.

1. Wenn der sprachspezifische Handler den Status „handled“ (verarbeitet) zurückgibt, wird die Ausführung mit dem ursprünglichen Kontextdatensatz fortgesetzt.

1. Wenn kein sprachspezifischer Handler vorhanden ist oder der Handler den Status „continue search“ (Suche fortsetzen) zurückgibt, muss der Kontextdatensatz in den Zustand der aufrufenden Funktion entladen werden. Hierfür werden alle Elemente im Entladungscodearray verarbeitet, sodass deren Auswirkungen rückgängig gemacht werden. Anschließend wird Schritt 1 wiederholt.

Wenn verkettete Entladeinformationen vorhanden sind, werden diese grundlegenden Schritte trotzdem befolgt. Der einzige Unterschied besteht darin, dass beim Durchlaufen des Entladungscodearrays zum Entladen der Auswirkungen eines Prologs eine Verknüpfung zu den übergeordneten Entladeinformationen hergestellt wird, wenn das Ende des Arrays erreicht wird. Anschließend wird das gesamte gefundene Entladungscodearray durchlaufen. Diese Verknüpfung besteht so lange, bis eine Entladeinformation ohne das Flag UNW_CHAINED_INFO erreicht wird. Damit wird das Durchlaufen des Entladungscodearrays beendet.

Der kleinste Entladungsdatensatz beträgt 8 Byte. Dabei würde es sich um eine Funktion handeln, der nur 128 Byte oder weniger eines Stapels zugeordnet sind und in der möglicherweise ein nicht flüchtiges Register gespeichert ist. Der Wert entspricht auch der Größe einer verketteten Entladeinformationsstruktur für einen Prolog mit einer Länge von 0 (null) ohne Entladungscodes.

## <a name="language-specific-handler"></a>Sprachspezifische Handler

Die relative Adresse des sprachspezifischen Handlers befindet sich in UNWIND_INFO, wenn die Flags UNW_FLAG_EHANDLER oder UNW_FLAG_UHANDLER festgelegt werden. Wie im vorherigen Abschnitt beschrieben wurde, wird der sprachspezifische Handler als Teil der Suche nach einem Ausnahmehandler oder als Teil einer Entladung aufgerufen. Der Prototyp sieht folgendermaßen aus:

```cpp
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**ExceptionRecord** stellt einen Zeiger auf einen Ausnahmedatensatz bereit, der der Standarddefinition für Win64 folgt.

**EstablisherFrame** ist die Adresse der Basis der festen Stapelzuordnung für diese Funktion.

**ContextRecord** zeigt auf den Ausnahmekontext zu dem Zeitpunkt, als die Ausnahme ausgelöst wurde (im Fall eines Ausnahmehandlers), oder auf den aktuellen Entladekontext (im Fall eines Beendigungshandlers).

**DispatcherContext** verweist auf den Dispatcherkontext für diese Funktion. Hierbei gilt folgende Definition:

```cpp
typedef struct _DISPATCHER_CONTEXT {
    ULONG64 ControlPc;
    ULONG64 ImageBase;
    PRUNTIME_FUNCTION FunctionEntry;
    ULONG64 EstablisherFrame;
    ULONG64 TargetIp;
    PCONTEXT ContextRecord;
    PEXCEPTION_ROUTINE LanguageHandler;
    PVOID HandlerData;
} DISPATCHER_CONTEXT, *PDISPATCHER_CONTEXT;
```

**ControlPc** ist der Wert des RIP innerhalb dieser Funktion. Dieser Wert ist entweder eine Ausnahmeadresse oder die Adresse, an der das Steuerelement die erstellende Funktion verlassen hat. Der RIP-Wert wird verwendet, um zu bestimmen, ob sich die Steuerung innerhalb dieser Funktion in einem geschützten Konstrukt befindet, z. B. in einem `__try`-Block für `__try`/ **`__except`** oder `__try`/ **`__finally`** .

**ImageBase** ist die Imagebasis (Ladeadresse) des Moduls, das diese Funktion enthält, die zu den im Funktionseintrag verwendeten 32-Bit-Offsets und den Entladeinformationen addiert werden soll, um relative Adressen aufzuzeichnen.

**FunctionEntry** stellt einen Zeiger auf den RUNTIME_FUNCTION-Funktionseintrag bereit, der die Funktion und die relative Imagebasisadresse der Entladeinformationen für diese Funktion enthält.

**EstablisherFrame** ist die Adresse der Basis der festen Stapelzuordnung für diese Funktion.

**TargetIp** stellt eine optionale Anweisungsadresse bereit, die die Fortsetzungsadresse der Entladung angibt. Diese Adresse wird ignoriert, wenn **EstablisherFrame** nicht angegeben wird.

**ContextRecord** zeigt auf den Ausnahmekontext, der vom Dispatch- bzw. Entladungscode für Systemausnahmen verwendet werden soll.

**LanguageHandler** zeigt auf die sprachspezifische Handlerroutine, die aufgerufen wird.

**HandlerData** zeigt auf die sprachspezifischen Handlerdaten für diese Funktion.

## <a name="unwind-helpers-for-masm"></a>Entladehilfsprogramme für MASM

Zum Schreiben gültiger Assemblyroutinen stehen Ihnen einige Pseudovorgänge zur Verfügung, die parallel mit den eigentlichen Assemblyanweisungen verwendet werden können, um die entsprechenden PDATA- und XDATA-Dateien zu erstellen. Außerdem gibt es einige Makros, die den Einsatz der Pseudovorgänge für die gängigsten Anwendungsfälle vereinfacht.

### <a name="raw-pseudo-operations"></a>Unformatierte Pseudovorgänge

|Pseudovorgänge|Beschreibung|
|-|-|
|PROC FRAME \[:*Ausnahmehandler*]|Hierdurch generiert MASM einen Funktionstabelleneintrag in der PDATA-Datei und Entladeinformationen in der XDATA-Datei für das strukturierte Entladeverhalten der Ausnahmebehandlung einer Funktion.  Wenn ein *Ausnahmehandler* angegeben wird, wird diese Prozedur in der XDATA-Datei als sprachspezifischer Handler verwendet.<br /><br /> Wenn das FRAME-Attribut verwendet wird, muss diesem eine .ENDPROLOG-Anweisung folgen.  Wenn es sich bei der Funktion um eine Leaf-Funktion handelt (wie unter [Funktionstypen](../build/stack-usage.md#function-types)definiert), sind das FRAME-Attribut und die restlichen Pseudovorgänge nicht nötig.|
|.PUSHREG *Register*|Generiert unter Verwendung des aktuellen Offsets im Prolog einen UWOP_PUSH_NONVOL-Entladungscodeeintrag für die angegebene Registernummer.<br /><br /> Verwenden Sie diesen nur mit nicht flüchtigen Integerregistern.  Verwenden Sie für die Übertragung flüchtiger Register stattdessen den Vorgang .ALLOCSTACK 8.|
|.SETFRAME *Register*, *Offset*|Füllt das Frameregisterfeld und den Offset in den Entladeinformationen mit dem angegebenen Register und Offset aus. Der Offset muss ein Vielfaches von 16 und kleiner oder gleich 240 sein. Diese Anweisung generiert außerdem unter Verwendung des aktuellen Prologoffsets einen UWOP_SET_FPREG-Entladungscodeeintrag für das angegebene Register.|
|.ALLOCSTACK *Größe*|Generiert UWOP_ALLOC_SMALL oder UWOP_ALLOC_LARGE mit der angegebenen Größe für den aktuellen Offset im Prolog.<br /><br /> Der *Größe*-Operand muss ein Vielfaches von 8 sein.|
|.SAVEREG *Register*, *Offset*|Generiert unter Verwendung des aktuellen Prologoffsets entweder einen UWOP_SAVE_NONVOL- oder einen UWOP_SAVE_NONVOL_FAR-Entladungscodeeintrag für das angegebene Register und den Offset. MASM wählt die effizienteste Codierung aus.<br /><br /> Der *Offset* muss positiv und ein Vielfaches von 8 sein. Der *Offset* ist relativ zur Framebasis der Prozedur, die sich in der Regel im RSP befindet. Wenn ein Framezeiger verwendet wird, befindet sie sich im nicht skalierten Framezeiger.|
|.SAVEXMM128 *Register*, *Offset*|Generiert unter Verwendung des aktuellen Prologoffsets entweder einen UWOP_SAVE_XMM128- oder einen UWOP_SAVE_XMM128_FAR-Entladungscodeeintrag für das angegebene XMM-Register und den Offset. MASM wählt die effizienteste Codierung aus.<br /><br /> Der *Offset* muss positiv und ein Vielfaches von 16 sein.  Der *Offset* ist relativ zur Framebasis der Prozedur, die sich in der Regel im RSP befindet. Wenn ein Framezeiger verwendet wird, befindet sie sich im nicht skalierten Framezeiger.|
|.PUSHFRAME \[*Code*]|Generiert einen UWOP_PUSH_MACHFRAME-Entladungscodeeintrag. Wenn das optionale *Code*-Element angegeben wird, wird der Modifizierer 1 auf den Entladungscodeeintrag angewendet. Andernfalls wird der Modifizierer 0 angewendet.|
|.ENDPROLOG|Signalisiert das Ende der Prologdeklarationen und  muss in den ersten 255 Byte der Funktion auftreten.|

Im Folgenden finden Sie ein Beispiel für einen Funktionsprolog mit korrekter Verwendung der meisten Opcodes:

```MASM
sample PROC FRAME
    db      048h; emit a REX prefix, to enable hot-patching
    push rbp
    .pushreg rbp
    sub rsp, 040h
    .allocstack 040h
    lea rbp, [rsp+020h]
    .setframe rbp, 020h
    movdqa [rbp], xmm7
    .savexmm128 xmm7, 020h ;the offset is from the base of the frame
                           ;not the scaled offset of the frame
    mov [rbp+018h], rsi
    .savereg rsi, 038h
    mov [rsp+010h], rdi
    .savereg rdi, 010h ; you can still use RSP as the base of the frame
                       ; or any other register you choose
    .endprolog

; you can modify the stack pointer outside of the prologue (similar to alloca)
; because we have a frame pointer.
; if we didn't have a frame pointer, this would be illegal
; if we didn't make this modification,
; there would be no need for a frame pointer

    sub rsp, 060h

; we can unwind from the next AV because of the frame pointer

    mov rax, 0
    mov rax, [rax] ; AV!

; restore the registers that weren't saved with a push
; this isn't part of the official epilog, as described in section 2.5

    movdqa xmm7, [rbp]
    mov rsi, [rbp+018h]
    mov rdi, [rbp-010h]

; Here's the official epilog

    lea rsp, [rbp+020h] ; deallocate both fixed and dynamic portions of the frame
    pop rbp
    ret
sample ENDP
```

Weitere Informationen zum Epilogbeispiel finden Sie im Artikel [Prolog und Epilog bei x64-Systemen](prolog-and-epilog.md) unter [Epilogcode](prolog-and-epilog.md#epilog-code).

### <a name="masm-macros"></a>MASM-Makros

Sie können den Einsatz [unformatierter Pseudovorgänge](#raw-pseudo-operations) vereinfachen, indem Sie die Makros in „ksamd64.inc“ verwenden, um typische Prozedurprologe und -epiloge zu erstellen.

|Makro|Beschreibung|
|-|-|
|alloc_stack(n)|Ordnet einen Stapelrahmen von n Byte (mit `sub rsp, n`) zu und gibt die entsprechenden Entladeinformationen (.ALLOCSTACK n) aus.|
|save_reg *reg*, *loc*|Speichert ein nicht flüchtiges Register (*reg*) im Stapel beim RSP-Offset *loc* und gibt die entsprechenden Entladeinformationen aus. (.savereg reg, loc)|
|push_reg *reg*|Überträgt ein nicht flüchtiges Register (*reg*) im Stapel und gibt die entsprechenden Entladeinformationen aus. (.pushreg reg)|
|rex_push_reg *reg*|Speichert unter Verwendung eines 2-Byte-Pushs ein nicht flüchtiges Register im Stapel und gibt die entsprechenden Entladeinformationen (.pushreg reg) aus.  Verwenden Sie dieses Makro, wenn der Push die erste Anweisung in der Funktion ist, damit sichergestellt wird, dass die Funktion hotpatchfähig ist.|
|save_xmm128 *reg*, *loc*|Speichert ein nicht flüchtiges XMM-Register (*reg*) im Stapel des RSP-Offsets *loc* und gibt die entsprechenden Entladeinformationen (.savexmm128 reg, loc) aus.|
|set_frame *reg*, *offset*|Legt das Frameregister *reg* auf RSP + *Offset* (unter Verwendung von `mov`oder `lea`) fest und gibt die entsprechenden Entladeinformationen aus (.set_frame reg, offset).|
|push_eflags|Überträgt eflags mit einer `pushfq`-Anweisung und gibt die entsprechenden Entladeinformationen aus (.alloc_stack 8).|

Im Folgenden finden Sie ein Beispiel für einen Funktionsprolog mit korrekter Verwendung der Makros:

```MASM
sampleFrame struct
    Fill     dq ?; fill to 8 mod 16
    SavedRdi dq ?; Saved Register RDI
    SavedRsi dq ?; Saved Register RSI
sampleFrame ends

sample2 PROC FRAME
    alloc_stack(sizeof sampleFrame)
    save_reg rdi, sampleFrame.SavedRdi
    save_reg rsi, sampleFrame.SavedRsi
    .end_prolog

; function body

    mov rsi, sampleFrame.SavedRsi[rsp]
    mov rdi, sampleFrame.SavedRdi[rsp]

; Here's the official epilog

    add rsp, (sizeof sampleFrame)
    ret
sample2 ENDP
```

## <a name="unwind-data-definitions-in-c"></a>Definitionen für Entladedaten in C

Im Folgenden finden Sie eine Beschreibung der Entladedaten:

```C
typedef enum _UNWIND_OP_CODES {
    UWOP_PUSH_NONVOL = 0, /* info == register number */
    UWOP_ALLOC_LARGE,     /* no info, alloc size in next 2 slots */
    UWOP_ALLOC_SMALL,     /* info == size of allocation / 8 - 1 */
    UWOP_SET_FPREG,       /* no info, FP = RSP + UNWIND_INFO.FPRegOffset*16 */
    UWOP_SAVE_NONVOL,     /* info == register number, offset in next slot */
    UWOP_SAVE_NONVOL_FAR, /* info == register number, offset in next 2 slots */
    UWOP_SAVE_XMM128 = 8, /* info == XMM reg number, offset in next slot */
    UWOP_SAVE_XMM128_FAR, /* info == XMM reg number, offset in next 2 slots */
    UWOP_PUSH_MACHFRAME   /* info == 0: no error-code, 1: error-code */
} UNWIND_CODE_OPS;

typedef union _UNWIND_CODE {
    struct {
        UBYTE CodeOffset;
        UBYTE UnwindOp : 4;
        UBYTE OpInfo   : 4;
    };
    USHORT FrameOffset;
} UNWIND_CODE, *PUNWIND_CODE;

#define UNW_FLAG_EHANDLER  0x01
#define UNW_FLAG_UHANDLER  0x02
#define UNW_FLAG_CHAININFO 0x04

typedef struct _UNWIND_INFO {
    UBYTE Version       : 3;
    UBYTE Flags         : 5;
    UBYTE SizeOfProlog;
    UBYTE CountOfCodes;
    UBYTE FrameRegister : 4;
    UBYTE FrameOffset   : 4;
    UNWIND_CODE UnwindCode[1];
/*  UNWIND_CODE MoreUnwindCode[((CountOfCodes + 1) & ~1) - 1];
*   union {
*       OPTIONAL ULONG ExceptionHandler;
*       OPTIONAL ULONG FunctionEntry;
*   };
*   OPTIONAL ULONG ExceptionData[]; */
} UNWIND_INFO, *PUNWIND_INFO;

typedef struct _RUNTIME_FUNCTION {
    ULONG BeginAddress;
    ULONG EndAddress;
    ULONG UnwindData;
} RUNTIME_FUNCTION, *PRUNTIME_FUNCTION;

#define GetUnwindCodeEntry(info, index) \
    ((info)->UnwindCode[index])

#define GetLanguageSpecificDataPtr(info) \
    ((PVOID)&GetUnwindCodeEntry((info),((info)->CountOfCodes + 1) & ~1))

#define GetExceptionHandler(base, info) \
    ((PEXCEPTION_HANDLER)((base) + *(PULONG)GetLanguageSpecificDataPtr(info)))

#define GetChainedFunctionEntry(base, info) \
    ((PRUNTIME_FUNCTION)((base) + *(PULONG)GetLanguageSpecificDataPtr(info)))

#define GetExceptionDataPtr(info) \
    ((PVOID)((PULONG)GetLanguageSpecificData(info) + 1)
```

## <a name="see-also"></a>Siehe auch

[Softwarekonventionen bei x64-Systemen](../build/x64-software-conventions.md)
