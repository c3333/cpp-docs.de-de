---
title: ARM-Ausnahmebehandlung
ms.date: 07/11/2018
ms.assetid: fe0e615f-c033-4ad5-97f4-ff96af45b201
ms.openlocfilehash: 4bdf0c88f0c2fe445f3a8865353ca1259ba586fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323225"
---
# <a name="arm-exception-handling"></a>ARM-Ausnahmebehandlung

Windows auf ARM verwendet denselben strukturierten Mechanismus für die Ausnahmebehandlung bei asynchronen – von der Hardware generierten – und synchronen – von der Software generierten – Ausnahmen. Sprachspezifische Ausnahmehandler werden auf von Windows strukturierter Ausnahmebehandlung mithilfe von Sprachhilfsfunktionen erstellt. Dieses Dokument beschreibt die Ausnahmebehandlung in Windows auf ARM und die Sprachhilfen, die von Code verwendet werden, der vom Microsoft-ARM-Assembler und vom MSVC-Compiler generiert wurde.

## <a name="arm-exception-handling"></a>ARM-Ausnahmebehandlung

Windows auf ARM verwendet *Entladungscodes*, um die Stapelentladung während der [strukturierten Ausnahmebehandlung](/windows/win32/debug/structured-exception-handling) (SEH) zu steuern. Entladungscodes sind eine Folge von Bytes, die im „.xdata“-Abschnitt des ausführbaren Images gespeichert sind. Sie beschreiben den Vorgang des Prolog- und Epilogcodes der Funktion auf abstrakte Weise, sodass die Effekte eines Funktionsprologs als Vorbereitung für die Entladung im Stapelrahmen des Aufrufers rückgängig gemacht werden.

Das ARM EABI (Embedded Application Binary Interface) legt ein Ausnahmeentladungsmodell fest, das Entladungscodes verwendet, aber für SEH-Entladung in Windows nicht ausreichend ist. Denn hier müssen asynchrone Fälle gehandhabt werden, in denen der Prozessor inmitten des Prologs oder Epilogs einer Funktion ist. Windows teilt außerdem die Entladungssteuerung in Entladung auf Funktionsebene und für den sprachspezifischen Bereich auf, was in der ARM EABI nicht definiert ist. Deshalb legt Windows auf ARM mehr Details für die Entladung von Daten und Verfahren fest.

### <a name="assumptions"></a>Annahmen

Ausführbare Dateien für Windows auf ARM verwenden das portierbare ausführbare Format (Portable Executable, PE). Weitere Informationen finden Sie in der [Microsoft PE- und COFF-Spezifikation](https://go.microsoft.com/fwlink/p/?linkid=84140). Ausnahmebehandlungsinformationen werden in den Abschnitten .pdata und .xdata des Bilds gespeichert.

Der Ausnahmebehandlungsmechanismus geht von bestimmten Annahmen über den Code aus, der ABI für Windows auf ARM folgt:

- Wenn eine Ausnahme im Funktionstext auftritt, spielt es keine Rolle, ob die Vorgänge des Prologs rückgängig gemacht werden oder ob die Vorgänge des Epilogs auf eine nach vorn gerichtete Weise durchgeführt werden. Beides sollte zum gleichen Ergebnis führen.

- Prologe und Epiloge entsprechen einander tendenziell. Das lässt sich nutzen, um die Größe der für die Beschreibung der Entladung nötigen Metadaten zu verringern.

- Funktionen sind eher relativ klein. Verschiedene Optimierungen stützen sich darauf im Hinblick auf das effiziente Packen von Daten.

- Wenn eine Bedingung in einen Epilog eingefügt wird, gilt sie gleichermaßen für jede Anweisung im Epilog.

- Wenn der Stapelzeiger (Stack Pointer, SP) in einem anderen Register im Prolog gespeichert wird, muss dieses in der ganzen Funktion unverändert bleiben, sodass der ursprüngliche SP jederzeit wiederhergestellt werden kann.

- Sämtliche Bearbeitungen des SP müssen strikt innerhalb von Prolog und Epilog erfolgen, außer wenn er in einem anderen Register gespeichert ist.

- Folgende Vorgänge sind nötig, damit ein Stapelrahmen entladen werden kann:

  - Anpassen von r13 (SP) in 4-Byte-Schritten.

  - Eines oder mehrere Ganzzahlregister per Pop entfernen.

  - Eines oder mehrere VFP-Register (Virtual Floating-Poin, Gleitkomma) per Pop entfernen.

  - Einen willkürlichen Registerwert nach r13 (SP) kopieren.

  - SP mithilfe eines kleinen Postdekrementvorgangs aus dem Stapel laden.

  - Einen Rahmentyp aus einigen klar definierten Rahmentypen analysieren.

### <a name="pdata-records"></a>.pdata-Datensätze

Die .pdata-Datensätze in einem PE-Format-Bild sind ein geordnetes Array von Elementen mit fester Länge, die jede Stapelbearbeitungsfunktion beschreiben. Blattfunktionen – das sind Funktionen, die keine andere Funktionen aufrufen – erfordern keine .pdata-Datensätze, wenn sie den Stapel nicht bearbeiten. (Das heißt, sie erfordern keinerlei lokales Speichern und müssen nicht flüchtige Register weder speichern noch wiederherstellen.). Datensätze für diese Funktionen können im .pdata-Bereich weggelassen werden, sodass Platz gespart wird. Ein Entladevorgang aus einer dieser Funktionen kann einfach die Rückgabeadresse aus dem Link Register (LR) an den Programmzähler (Program Counter, PC) kopieren, um nach oben zum Aufrufer zu bewegen.

Jeder .pdata-Datensatz für ARM ist 8 Byte lang. Das allgemeine Format für einen Datensatz platziert die relative virtuelle Adresse (RVA) des Funktionsstarts in das erste 32-Bit-Wort gefolgt von einem zweiten Wort, das entweder einen Zeiger zu einem .xdata-Block mit variabler Länge enthält oder ein gepacktes Wort, dass die Entladesequenz einer kanonischen Funktion beschreibt, wie in dieser Tabelle dargestellt:

|Wortoffset|Bits|Zweck|
|-----------------|----------|-------------|
|0|0-31|*Function Start RVA* (RVA für Funktionsbeginn) ist der 32-Bit-RVA des Funktionsbeginns. Wenn die Funktion Thumb-Code enthält, muss der niedrigste Bitwert dieser Adresse festgelegt werden.|
|1|0-1|*Flag* ist ein 2-Bit-Feld, das angibt, wie die verbleibenden 30 Bit des zweiten PDATA-Worts zu interpretieren sind. Wenn *Flag* den Wert 0 hat, bilden die übrigen Bits den *Exception Information RVA* (RVA für Ausnahmeinformationen), wobei die beiden niedrigsten Bits implizit 0 sind. Wenn *Flag* ungleich 0 (null) ist, bilden die übrigen Bits die Struktur *Packed Unwind Data* (Gepackte Entladedaten).|
|1|2-31|*Exception Information RVA* (RVA für Ausnahmeinformationen) oder *Packed Unwind Data* (Gepackte Entladedaten)<br /><br /> *Exception Information RVA* (RVA für Ausnahmeinformationen) enthält die Adresse der Ausnahmeinformationsstruktur mit variabler Länge, die im XDATA-Abschnitt gespeichert wird. Diese Daten müssen 4-Bytes ausgerichtet sein.<br /><br /> *Packed Unwind Data* (Gepackte Entladedaten) enthält eine komprimierte Beschreibung der Vorgänge, die für die Entladung einer Funktion nötig sind. Dabei wird von einer kanonischen Form ausgegangen. In diesem Fall ist kein .xdata-Datensatz erforderlich.|

### <a name="packed-unwind-data"></a>Gepackte Entladedaten

Bei Funktionen, deren Prolog und Epilog der unten beschriebenen kanonischen Form entsprechen, können gepackte Entladedaten verwendet werden. Damit wird kein .xdata-Datensatz benötigt und der erforderliche Platz für die Entladung der Daten deutlich reduziert. Die kanonischen Prologe und Epiloge wurden entwickelt, sodass sie den allgemeinen Anforderung einer einfachen Funktion entsprechen, die keinen Ausnahmehandler erfordert und ihre Setup- und Teardownvorgänge in der standardmäßigen Reihenfolge durchführt.

Diese Tabelle zeigt das Format eines .pdata-Datensatzes, der Entladedaten gepackt hat:

|Wortoffset|Bits|Zweck|
|-----------------|----------|-------------|
|0|0-31|*Function Start RVA* (RVA für Funktionsbeginn) ist der 32-Bit-RVA des Funktionsbeginns. Wenn die Funktion Thumb-Code enthält, muss der niedrigste Bitwert dieser Adresse festgelegt werden.|
|1|0-1|Ein *Flag* ist ein 2-Bit-Feld mit folgenden Bedeutungen:<br /><br />00 = gepackte Entladedaten werden nicht verwendet; verbleibende Bits zeigen auf den XDATA-Datensatz.<br />01 = gepackte Entladedaten<br />10 = gepackte Entladedaten, bei denen davon ausgegangen wird, dass die Funktion keinen Prolog hat. Das ist nützlich beim Beschreiben von Funktionsfragmenten, die nicht mit dem Start der Funktion verbunden sind.<br />11 = Reserviert|
|1|2-12|*Function Length* (Funktionslänge) ist ein 11-Bit-Feld, das die Länge der gesamten Funktion in Byte geteilt durch 2 angibt. Wenn die Funktion größer als 4 KB ist, muss stattdessen ein voller .xdata-Datensatz verwendet werden.|
|1|13-14|*Ret* ist ein 2-Bit-Feld, das angibt, wie die Rückgabe der Funktion erfolgt:<br /><br />00 = Rückgabe über Pop {pc} (das *L*-Flag muss in diesem Fall auf 1 festgelegt sein)<br />01 = Rückgabe mithilfe eines 16-Bit-Branches<br />10 = Rückgabe mithilfe eines 32-Bit-Branches<br />11 = kein Epilog Das ist nützlich, wenn ein nicht verbundenes Funktionsfragment beschrieben werden soll, das nur aus ein Prolog bestehen kann, aber dessen Epilog sich anderswo befindet.|
|1|15|*H* ist ein 1-Bit-Flag, das angibt, ob die Funktion die Ganzzahlparameterregister (r0-r3) „herausgreift“, indem es sie an den Beginn der Funktion schiebt und die 16 Bytes des Stapels vor der Rückgabe freigibt. (0 = greift die Register nicht heraus, 1 = Greift Register heraus.)|
|1|16-18|*Reg* ist ein 3-Bit-Feld, das den Index des letzten gespeicherten, nicht flüchtigen Registers angibt. Wenn das *R*-Bit 0 ist, dann werden nur die Ganzzahlregister gespeichert und es wird davon ausgegangen, dass sie sich im Bereich r4-rN befinden, wobei N gleich 4 + *Reg* ist. Wenn das *R*-Bit 1 ist, dann werden nur die Gleitkommaregister gespeichert und es wird davon ausgegangen, dass sie sich im Bereich d8-dN befinden, wobei N gleich 8 + *Reg* ist. Die spezielle Kombination von *R* = 1 und *Reg* = 7 gibt an, dass keine Register gespeichert wurden.|
|1|19|*R* ist ein 1-Bit-Flag, das angibt, ob die gespeicherten nicht flüchtigen Register Ganzzahlregister (0) oder Gleitkommaregister (1) sind. Wenn *R* auf 1 eingestellt und das Feld *Reg* auf 7 eingestellt ist, werden keine nicht flüchtigen Register per Push abgelegt.|
|1|20|*L* ist ein 1-Bit-Flag, das angibt, ob die Funktion LR zusammen mit anderen Registern speichert/wiederherstellt, wie im Feld *Reg* angegeben. (0 = speichert nicht/stellt nicht wieder her, 1 = speichert/stellt wieder her.)|
|1|21|*C* ist ein 1-Bit-Flag, das angibt, ob die Funktion zusätzliche Anweisungen für das Einrichten einer Rahmenkette für schnelle Stackwalks (1) enthält oder nicht (0). Wen das Bit festgelegt wurde, wird r11 implizit in der Liste nicht flüchtiger Ganzzahlregister gespeichert. (Sehen Sie sich die Einschränkungen unten an, wenn das *C*-Flag verwendet wird.)|
|1|22-31|*Stack Adjust* (Stapelanpassung) ist ein 10-Bit-Feld, das die Anzahl der von dieser Funktion zugeordneten Bytes eines Stapels geteilt durch 4 angibt. Es lassen sich allerdings nur Werte zwischen 0x000 und 0x3F3 direkt codieren. Funktionen, die über 4044 Bytes an Stapel zuzuordnen, müssen einen vollständigen .xdata-Datensatz verwenden. Wenn das Feld *Stack Adjust* (Stapelanpassung) 0x3F4 oder größer ist, haben die niedrigsten 4 Bits eine besondere Bedeutung:<br /><br />Die Bits 0-1 enthalten die Anzahl der Worte der Stapelanpassung (1-4) minus 1.<br />Das Bit 2 ist auf 1 festgelegt, wenn der Prolog diese Anpassung in seinen Pushübertragungsvorgang kombiniert hat.<br />Das Bit 3 ist auf 1 festgelegt, wenn der Epilog diese Anpassung in seinen Popvorgang kombiniert hat.|

Wegen möglicher Redundanzen in den oben genannten Codierungen gelten folgende Einschränkungen:

- Wenn das *C*-Flag auf 1 festgelegt wurde:

  - Muss das *L*-Flag ebenfalls auf 1 festgelegt werden, da für r11 und LR Rahmenverknüpfung erforderlich ist.

  - r11 darf nicht in den Registern enthalten sein, die von *Reg* beschrieben werden. Das bedeutet, wenn r4-r11 gepusht werden, darf *Reg* nur r4-r10 beschreiben, da das *C*-Flag r11 impliziert.

- Wenn das Feld *Ret* auf 0 festgelegt ist, muss das *L*-Flag auf 1 festgelegt werden.

Werden diese Einschränkungen übergangen, kann dies eine nicht unterstützte Sequenz hervorrufen.

Zum Zwecke der nachfolgenden Auseinandersetzung werden zwei Pseudoflags von *Stack Adjust* abgeleitet:

- *PF* oder „Prologue Folding“ gibt an, dass *Stack Adjust* gleich 0x3F4 oder größer ist und Bit 2 festgelegt wurde.

- *EF* oder „Epilogue Folding“ gibt an, dass *Stack Adjust* gleich 0x3F4 oder größer ist und Bit 3 festgelegt wurde.

Prologe für nicht kanonische Funktionen können bis zu 5 Anweisungen haben (beachten Sie, dass 3a und 3b sich gegenseitig ausschließen):

|Anweisung|Es wird davon ausgegangen, dass Opcode vorhanden ist, wenn:|Größe|Opcode|Entladungscodes|
|-----------------|-----------------------------------|----------|------------|------------------|
|1|*H*==1|16|`push {r0-r3}`|04|
|2|*C*==1 oder *L*==1 oder *R*==0 oder PF==1|16/32|`push {registers}`|80-BF/D0-DF/EC-ED|
|3a|*C*==1 und (*L*==0 und *R*==1 und PF==0)|16|`mov r11,sp`|C0-CF/FB|
|3b|*C*==1 und (*L*==1 oder *R*==0 oder PF==1)|32|`add r11,sp,#xx`|FC|
|4|*R*==1 und *Reg* != 7|32|`vpush {d8-dE}`|E0-E7|
|5|*Stack Adjust* != 0 und PF==0|16/32|`sub sp,sp,#xx`|00-7F/E8-EB|

Anweisung 1 liegt immer vor, wenn das *H*-Bit auf 1 festgelegt wurde.

Zum Festlegen der Rahmenverknüpfung muss entweder die Anweisung 3a oder 3b vorhanden sein, wenn das *C*-Bit festgelegt wird. Es ist ein 16-Bit-`mov`, wenn kein Register außer r11 und LR per Push abgelegt wird; ansonsten ist es ein 32-Bit-`add`.

Wird eine nicht gefaltete Anpassung festgelegt, ist Anweisung die ausdrückliche Stapelanpassung.

Die Anweisungen 2 und 4 werden abhängig davon festgelegt, ob eine Pushübertagung erforderlich ist. In dieser Tabelle wird zusammengefasst, welche Register in den Feldern *C*, *L*, *R* und *PF* gespeichert werden. In allen Fällen ist *N* gleich *Reg* + 4, *E* gleich *Reg* + 8 und *S* gleich (~*Stack Adjust*) & 3.

|C|L|R|PF|Ganzzahlregister per Push abgelegt|VFP-Register per Push abgelegt|
|-------|-------|-------|--------|------------------------------|--------------------------|
|0|0|0|0|r4-r*N*|Keine|
|0|0|0|1|r*S*-r*N*|Keine|
|0|0|1|0|Keine|d8-d*E*|
|0|0|1|1|r*S*-r3|d8-d*E*|
|0|1|0|0|r4-r*N*, LR|Keine|
|0|1|0|1|r*S*-r*N*, LR|Keine|
|0|1|1|0|LR|d8-d*E*|
|0|1|1|1|r*S*-r3, LR|d8-d*E*|
|1|0|0|0|r4-r*N*, r11|Keine|
|1|0|0|1|r*S*-r*N*, r11|Keine|
|1|0|1|0|r11|d8-d*E*|
|1|0|1|1|r*S*-r3, r11|d8-d*E*|
|1|1|0|0|r4-r*N*, r11, LR|Keine|
|1|1|0|1|r*S*-r*N*, r11, LR|Keine|
|1|1|1|0|r11, LR|d8-d*E*|
|1|1|1|1|r*S*-r3, r11, LR|d8-d*E*|

Die Epiloge für kanonische Funktionen ermöglichen es, einer ähnlichen Form zu folgen, doch rückwärts und mit ein paar zusätzlichen Optionen. Der Epiloge kann bis zu 5 Anweisungen lang sein und seine Form wird streng durch das Format des Prologs diktiert.

|Anweisung|Es wird davon ausgegangen, dass Opcode vorhanden ist, wenn:|Größe|Opcode|
|-----------------|-----------------------------------|----------|------------|
|6|*Stack Adjust*!=0 und *EF*==0|16/32|`add   sp,sp,#xx`|
|7|*R*==1 und *Reg*!=7|32|`vpop  {d8-dE}`|
|8|*C*==1 oder (*L*==1 und *H*==0) oder *R*==0 oder *EF*==1|16/32|`pop   {registers}`|
|9a|*H*==1 und *L*==0|16|`add   sp,sp,#0x10`|
|9b|*H*==1 und *L*==1|32|`ldr   pc,[sp],#0x14`|
|10a|*Ret*==1|16|`bx    reg`|
|10b|*Ret*==2|32|`b     address`|

Anweisung 6 ist die ausdrückliche Stapelanpassung, wenn eine nicht gefaltete Anpassung festgelegt wurde. Da *PF* unabhängig von *EF* ist, ist es möglich, dass eine Anweisung 5 ohne 6 vorhanden ist und umgekehrt.

Die Anweisungen 7 und 8 verwenden dieselbe Logik wie der Prolog, um zu bestimmen, welche Register aus dem Stapel wiederhergestellt werden, aber mit den beiden folgenden Änderungen: Erstens wird *EF* anstelle von *PF* verwendet; zweitens, wenn *Ret* = 0 vorliegt, dann wird LR in der Registerliste durch PC ersetzt und der Epilog endet sofort.

Wenn *H* festgelegt ist, dann ist entweder Anweisung 9a oder 9b vorhanden. Die Anweisung 9a wird verwendet, wenn *L* gleich 0 ist, um anzuzeigen, dass sich LR nicht im Stapel befindet. In diesem Fall wird der Stapel manuell angepasst und *Ret* muss 1 oder 2 sein, damit eine explizite Rückgabe festgelegt wird. Die Anweisung 9b wird verwendet, wenn *L* gleich 1 ist, um ein frühes Ende des Epilogs anzugeben und gleichzeitig den Stack zurückzugeben und anzupassen.

Wenn der Epilog noch nicht beendet wurde, dann ist entweder Anweisung 10a oder 10b vorhanden und gibt einen 16- oder 32-Bit-Branch auf Grundlage des Werts von *Ret* an.

### <a name="xdata-records"></a>.xdata-Datensätze

Wenn das gepackte Entladeformat nicht zur Beschreibung der Entladung einer Funktion ausreicht, muss ein .xdata-Datensatz mit variabler Länge erstellt werden. Die Adresse dieses Datensatzes wird im zweiten Wort des .pdata-Datensatzes gespeichert. Das Format von .xdata ist ein gepackter Satz an Worten mit variabler Länge, der vier Abschnitte hat:

1. Ein 1- oder 2-Wort-Header, der die Gesamtgröße der .xdata-Struktur beschreibt und wichtige Funktionsdaten enthält. Das zweite Wort ist nur vorhanden, wenn die Felder *Epilog Count* (Epiloganzahl) und *Code Words* (Codewörter) auf 0 festgelegt sind. Die Felder sind in dieser Tabelle aufgeteilt:

   |Word|Bits|Zweck|
   |----------|----------|-------------|
   |0|0-17|*Function Length* (Funktionslänge) ist ein 18-Bit-Feld, das die Gesamtlänge der Funktion in Bytes geteilt durch 2 angibt. Wenn eine Funktion größer als 512 KB ist, dann müssen mehrere .pdata- und .xdata-Datensätze verwendet werden, um die Funktion zu beschreiben. Weitere Informationen finden Sie im Abschnitt "Große Funktionen" in diesem Dokument.|
   |0|18-19|*Vers* ist ein 2-Bit-Feld, das die Version der verbleibenden xdata beschreibt. Nur Version 0 ist derzeit definiert; die Werte 1-3 sind reserviert.|
   |0|20|*X* ist ein 1-Bit-Feld, das das Vorhandensein (1) oder Fehlen (0) von Ausnahmedaten angibt.|
   |0|21|*E* ist ein 1-Bit-Feld, das die Informationen angibt, die einen einzelnen Epilog beschreiben in den Header gepackt werden (1), sodass später keine zusätzlichen Bereichswörter mehr erforderlich sind (0).|
   |0|22|*F* ist ein 1-Bit-Feld, das angibt, dass dieser Datensatz ein Funktionsfragment (1) oder eine vollständige Funktion (0) beschreibt. Ein Fragment impliziert, dass es keinen Prolog gibt und dass sämtliche Prologverarbeitung ignoriert werden soll.|
   |0|23-27|*Epilog Count* (Epiloganzahl) ist ein 5-Bit-Feld mit zwei Bedeutungen, die vom Status des *E*-Bits abhängen:<br /><br /> Wenn *E* den Wert 0 aufweist, ist dieses Feld eine Aufzählung der Gesamtzahl von Ausnahmebereichen, die in Abschnitt 3 beschrieben werden. Sind über 31 Bereiche in der Funktion vorhanden, müssen dieses Feld und das Feld *Code Words* (Codewörter) auf 0 festgelegt werden, damit angegeben wird, dass ein Ausnahmewort erforderlich ist.<br />Wenn *E* den Wert 1 aufweist, legt dieses Feld den Index des ersten Entladungscodes fest, der nur den Epilog beschreibt.|
   |0|28-31|*Code Words* (Codewörter) ist ein 4-Bit-Feld, das die Anzahl der 32-Bit-Wörter angibt, die für alle Entladungscodes in Abschnitt 4 benötigt werden. Wenn mehr als 15 Wörter für mehr als 63 Entladungscodebytes erforderlich sind, müssen dieses Feld und das Feld *Epilogue Count* (Epiloganzahl) auf 0 festgelegt werden, um anzugeben, dass ein Erweiterungswort erforderlich ist.|
   |1|0-15|*Extended Epilogue Count* (Erweiterte Epiloganzahl) ist ein 16-Bit-Feld, das mehr Raum für die Codierung bietet als eine ungewöhnlich große Anzahl von Epilogen. Das Erweiterungswort, das dieses Feld enthält, ist nur vorhanden, wenn die Felder *Epilogue Count* (Epiloganzahl) und *Code Words* (Codewörter) im ersten Headerwort auf 0 festgelegt sind.|
   |1|16-23|*Extended Code Words* (Erweiterte Codewörter) ist ein 8-Bit-Feld, das mehr Raum für die Codierung bietet als eine ungewöhnlich große Anzahl von Entladungscodeworten. Das Erweiterungswort, das dieses Feld enthält, ist nur vorhanden, wenn die Felder *Epilogue Count* (Epiloganzahl) und *Code Words* (Codewörter) im ersten Headerwort auf 0 festgelegt sind.|
   |1|24-31|Reserviert|

1. Nach den Ausnahmedaten (wenn das *E*-Bit im Header auf 0 festgelegt wurde) ist eine Liste von Informationen über Epilogbereiche, die in ein Wort gepackt und in der Reihenfolge zunehmender Startoffsets gespeichert werden. Jeder Bereich enthält folgende Felder:

   |Bits|Zweck|
   |----------|-------------|
   |0-17|*Epilog Start Offset* (Startoffset des Epilogs) ist ein 18-Bit-Feld, das den Epilogoffset in Byte geteilt durch 2 beschreibt, der relativ zum Funktionsbeginn ist.|
   |18-19|*Res* (Reserviert) ist ein 2-Bit-Feld, das für künftige Erweiterungen reserviert ist. Sein Wert muss 0 sein.|
   |20-23|*Condition* (Bedingung) ist ein 4-Bit-Feld, das die Bedingung angibt, unter der der Epilog ausgeführt wird. Für bedingungslose Epiloge muss es auf 0xE festgelegt sein, was "immer" bedeutet. (Ein Epilog muss vollständig beginnt oder bedingungslos sein und im Thumb-2-Modus beginnt der Epilog mit der ersten Anweisung nach dem IT-Opcode.)|
   |24-31|*Epilogue Start Index* (Epilogstartindex) ist ein 8-Bit-Feld, das den Byte-Index des ersten Entladungscodes angibt, der diesen Epilog beschreibt.|

1. Nach der Liste von Epilogbereichen kommt ein Array von Bytes, das Entladungscodes enthält. Diese werden detailliert im Abschnitt Entladungscodes dieses Artikels beschrieben. Dieses Array ist am Ende aufgefüllt bis zur nächsten vollen Wortgrenze. Die Bytes werden in Little-Endian-Reihenfolge gespeichert, sodass sie im Little-Endian-Modus direkt abgerufen werden können.

1. Wenn das *X*-Feld im Header 1 ist, folgen die Ausnahmehandlerinformationen auf die Entladungscodebytes. Sie bestehen aus einer *Exception Handler RVA* (RVA für Ausnahmehandler), die die Adresse des Ausnahmehandlers enthält, unmittelbar gefolgt von der vom Ausnahmehandler benötigten Datenmenge (mit variabler Länge).

Der .xdata-Datensatz ist so gestaltet, dass es möglich ist, die ersten 8 Bytes abzurufen und die volle Größe des Datensatzes zu berechnen, ausgenommen die Länge der folgenden Ausnahmedaten mit variabler Größe. Dieser Codeausschnitt berechnet die Datensatzgröße:

```cpp
ULONG ComputeXdataSize(PULONG *Xdata)
{
    ULONG EpilogueScopes;
    ULONG Size;
    ULONG UnwindWords;

    if ((Xdata[0] >> 23) != 0) {
        Size = 4;
        EpilogueScopes = (Xdata[0] >> 23) & 0x1f;
        UnwindWords = (Xdata[0] >> 28) & 0x0f;
    } else {
        Size = 8;
        EpilogueScopes = Xdata[1] & 0xffff;
        UnwindWords = (Xdata[1] >> 16) & 0xff;
    }

    if (!(Xdata[0] & (1 << 21))) {
        Size += 4 * EpilogueScopes;
    }
    Size += 4 * UnwindWords;
    if (Xdata[0] & (1 << 20)) {
        Size += 4;
    }
    return Size;
}
```

Obwohl der Prolog und jeder Epilog einen Index in den Entladungscodes besitzen, teilen sich die beiden die Tabelle. Es ist nicht ungewöhnlich, dass alle denselben Entladungscode teilen. Wir empfehlen, dass Compiler-Autoren für diesen Fall optimieren, denn der größte Index, der festgelegt werden kann, ist 255 und das begrenzt die Gesamtzahl der Entladungscodes, die für eine bestimmte Funktion mögliche sind.

### <a name="unwind-codes"></a>Entladungscodes

Das Array an Entladungscodes ist ein Pool von Anweisungsequenzen, der genau beschreibt, wie die Wirkungen des Prologs rückgängig gemacht werden und in welcher Reihenfolge. Die Entladungscodes sind ein Satz von Minianweisungen, die als eine Zeichenfolge von Bytes codiert wurden. Wenn die Ausführung abgeschlossen ist, befindet sich die Rückgabeadresse im LR-Register und alle nicht flüchtigen Register werden auf ihre Werte zu Beginn des Funktionsaufrufs zurückgesetzt.

Würden Ausnahmen garantiert immer nur innerhalb einer Funktion auftreten und niemals im Prolog oder Epilog, dann wäre nur eine Entladesequenz nötig. Doch das Windows-Entlademodell erfordert die Fähigkeit, von innerhalb eines teilweise ausgeführten Prologs oder Epilogs aus zu entladen. Damit dieser Anforderung Rechnung getragen wird, wurden die Entladungscodes sorgfältig so entwickelt, dass sie eine unzweifelhafte Eins-zu-Eins-Zuordnung zu jedem relevanten Opcode im Prolog und Epilog haben. Das hat eine Reihe von Auswirkungen:

- Es ist möglich, die Länge von Prolog und Epilog zu berechnen, indem man die Anzahl von Entladungscodes zählt. Das ist selbst mit Thumb-2-Anweisungen mit variabler Länge möglich, da es eine eindeutige Zuordnung für 16- und 32-Bit-Opcodes gibt.

- Durch Zählen der Anzahl von Anweisungen nach dem Start eines Epilogbereichs ist es möglich, die gleiche Anzahl von Entladungscodes zu überspringen und den Rest einer Sequenz auszuführen, um die teilweise ausgeführte Entladung abzuschließen, die der Epilog durchgeführt hat.

- Durch Zählen der Anzahl von Anweisungen vor dem Ende eines Prologs ist es möglich, die gleiche Anzahl von Entladungscodes zu überspringen und den Rest einer Sequenz auszuführen, sodass nur die Teile des Prologs rückgängig gemacht werden, die der Prolog durchgeführt hat.

Die folgende Tabelle zeigt die Zuordnung von Entladungscodes zu Opcodes. Die häufigsten Codes sind nur ein Byte, während weniger übliche zwei, drei oder sogar vier Bytes benötigen. Jeder Code wird vom signifikantesten bis zum am wenigsten signifikanten Byte gespeichert. Die Entladungscodestruktur unterscheidet sich von der Entladung, die in ARM EABI beschrieben ist, da diese Entladungscodes mit einer Eins-zu-Eins-Zuordnung zu den Opcodes in Prolog und Epilog entwickelt wurden, was die Entladung teilweise ausgeführter Prologe und Epiloge möglich macht.

|Byte 1|Byte 2|Byte 3|Byte 4|Opsize|Erklärung|
|------------|------------|------------|------------|------------|-----------------|
|00-7F||||16|`add   sp,sp,#X`<br /><br /> wobei X gleich (Code & 0x7F) \* 4 ist|
|80-BF|00-FF|||32|`pop   {r0-r12, lr}`<br /><br /> wobei LR per Pop ausgelesen wird, wenn Code & 0x2000 und r0-r12 per Pop ausgelesen werden, falls das korrespondierende Bit in Code & 0x1FFF festgelegt wurde|
|C0-CF||||16|`mov   sp,rX`<br /><br /> wobei X gleich Code & 0x0F ist|
|D0-D7||||16|`pop   {r4-rX,lr}`<br /><br /> wobei X gleich (Code & 0x03) + 4 ist und LR per Pop ausgelesen wird, wenn Code & 0x04 vorliegt|
|D8-DF||||32|`pop   {r4-rX,lr}`<br /><br /> wobei X gleich (Code & 0x03) + 8 ist und LR per Pop ausgelesen wird, wenn Code & 0x04 vorliegt|
|E0-E7||||32|`vpop  {d8-dX}`<br /><br /> wobei X gleich (Code & 0x07) + 8 ist|
|E8-EB|00-FF|||32|`addw  sp,sp,#X`<br /><br /> wobei X gleich (Code & 0x03FF) \* 4 ist|
|EC-ED|00-FF|||16|`pop   {r0-r7,lr}`<br /><br /> wobei LR per Pop ausgelesen wird, wenn Code & 0x0100 und r0-r7 per Pop ausgelesen werden, falls das korrespondierende Bit in Code & 0x00FF festgelegt wurde|
|EE|00-0F|||16|Microsoft-spezifisch|
|EE|10-FF|||16|Verfügbar|
|EF|00-0F|||32|`ldr   lr,[sp],#X`<br /><br /> wobei X gleich (Code & 0x000F) \* 4 ist|
|EF|10-FF|||32|Verfügbar|
|F0-F4||||-|Verfügbar|
|F5|00-FF|||32|`vpop  {dS-dE}`<br /><br /> wobei S gleich (Code & 0x00F0) >> 4 und E gleich Code & 0x000F ist|
|F6|00-FF|||32|`vpop  {dS-dE}`<br /><br /> wobei S gleich ((Code & 0x00F0) >> 4) + 16 und E gleich (Code & 0x000F) + 16 ist|
|F7|00-FF|00-FF||16|`add   sp,sp,#X`<br /><br /> wobei X gleich (Code & 0x00FFFF) \* 4 ist|
|F8|00-FF|00-FF|00-FF|16|`add   sp,sp,#X`<br /><br /> wobei X gleich (Code & 0x00FFFFFF) \* 4 ist|
|F9|00-FF|00-FF||32|`add   sp,sp,#X`<br /><br /> wobei X gleich (Code & 0x00FFFF) \* 4 ist|
|FA|00-FF|00-FF|00-FF|32|`add   sp,sp,#X`<br /><br /> wobei X gleich (Code & 0x00FFFFFF) \* 4 ist|
|FB||||16|nop (16-Bit)|
|FC||||32|nop (32-Bit)|
|FD||||16|end + 16-Bit nop im Epilog|
|FE||||32|end + 32-Bit nop im Epilog|
|FF||||-|end|

Dies zeigt einen Bereich hexadezimaler Werte für jedes Byte in einem Entladungscode (*Code*) zusammen mit der Opcodegröße (*Opsize*) und der entsprechenden ursprünglichen Anweisungsinterpretation. Leere Zellen weisen auf kürzere Entladungscodes hin. Die Anweisungen mit großen Werten umfassen mehrere Bytes, wobei die signifikanten zuerst gespeichert sind. Das Feld *Opsize* zeigt die implizite Opcodegröße, die jedem Thumb-2-Vorgang zugeordnet ist. Die offensichtlichen Doppeleinträge in der Tabelle bei verschiedenen Codierungen werden verwendet, damit zwischen den verschiedenen Opcodegrößen unterschieden werden kann.

Die Entladungscodes wurden entwickelt, sodass das erste Byte des Codes sowohl die Gesamtgröße des Codes in Bytes als auch die Größe des entsprechenden Opcodes im Anweisungsstream verrät. Um die Größe von Prolog oder Epilog berechnen zu können, gehen Sie die Entladungscodes vom Beginn der Sequenz bis zum Ende durch und verwenden eine Nachschlagetabelle oder eine vergleichbare Methode, um zu bestimmen, wie lange der entsprechende Opcode ist.

Die Entladungscodes 0xFD und 0xFE sind gleich dem regulären Endcode 0xFF, machen aber einen zusätzlichen nop-Opcode im Epilogfall aus, entweder 16- oder 32-Bit. Bei Prologen sind die Codes 0xFD, 0xFE und 0xFF genau gleich. Dies umfasst die gemeinsamen Epilogenden `bx lr` oder `b <tailcall-target>`, die keine identischen Prologanweisungen aufweisen. Das erhöht die Möglichkeit, Entladungssequenzen zwischen Prolog und Epilog zu teilen.

In vielen Fällen sollte es möglich sein, denselben Satz an Entladungscodes für Prologe und Epiloge zu verwenden. Um jedoch die Entladung teilweise ausgeführter Prologe und Epiloge bewältigen zu können, benötigen Sie möglicherweise mehrere Entladungscodesequenzen, die sich hinsichtlich Sortierung oder Verhalten unterscheiden. Deshalb hat jeder Epilog seinen eigenen Index im Entladungsarray, sodass angezeigt wird, wo mit der Umsetzung zu beginnen ist.

### <a name="unwinding-partial-prologues-and-epilogues"></a>Entladen partieller Prologe und Epiloge

Der häufigste Entladungsfall ist eine Ausnahme, die im Text der Funktion auftritt, jenseits vom Prolog und allen Epilogen. In diesem Fall führt der Entlader die Codes im Entladungsarray aus, beginnend bei Index 0, und er fährt fort, bis ein Endopcode festgestellt wird.

Wenn während der Ausführung eines Prologs oder Epilogs eine Ausnahme auftritt, wird der Stapelrahmen nur teilweise konstruiert und der Entlader muss genau bestimmen, was vorgefallen ist, um dies korrekt rückgängig machen zu können.

Betrachten Sie beispielsweise diese Prolog-Epilog-Sequenz:

```asm
0000:   push  {r0-r3}         ; 0x04
0002:   push  {r4-r9, lr}     ; 0xdd
0006:   mov   r7, sp          ; 0xc7
...
0140:   mov   sp, r7          ; 0xc7
0142:   pop   {r4-r9, lr}     ; 0xdd
0146:   add   sp, sp, #16     ; 0x04
0148:   bx    lr
```

Neben jedem Opcode befindet sich der entsprechende Entladungscode, der diesen Vorgang beschreibt. Die Sequenz der Entladungscodes für den Prolog ist ein Spiegelbild derjenigen für den Epilog, abgesehen von der letzten Anweisung. Dieser Fall tritt häufig auf und ist der Grund dafür, weshalb immer davon ausgegangen wird, dass die Entladungscodes für den Prolog in umgekehrter Reihenfolge zur ihrer Ausführung gespeichert werden. Damit erhalten wir einen gemeinsamen Satz von Entladungscodes:

```asm
0xc7, 0xdd, 0x04, 0xfd
```

Der Code 0xFD ist ein Spezialcode für das Ende der Sequenz und bedeutet, dass der Epilog eine 16-Bit-Anweisung länger als der Prolog ist. Damit ist es öfter möglich, Entladungscodes gemeinsam zu nutzen.

Im Beispiel beginnt die Entladung mit dem Epilogfall, wenn beim Ausführen des Funktionstextes zwischen Prolog und Epilog eine Ausnahme auftritt, und zwar bei Offset 0 im Epilogcode. Das entspricht dem Offset 0x140 im Beispiel. Der Entlader führt die volle Entladesequenz aus, da keine Bereinigung vorgenommen wurde. Wenn stattdessen die Ausnahme eine Anweisung nach dem Beginn des Epilogcodes auftritt, kann der Entlader erfolgreich entladen, indem er den ersten Entladungscode überspringt. Bei einer 1:1-Zuordnung von Opcodes und Entladungscodes, sollte der Entlader die ersten *n* Entladungscodes überspringen, wenn eine Entladung der Anweisung *n* im Epilog erfolgt.

Die gleiche Logik gilt umgekehrt für den Prolog. Findet die Entladung von Offset 0 im Prolog statt, muss nichts ausgeführt werden. Findet die Entladung von einer Anweisung weiter innen statt, sollte die Entladungssequenz einen Entladungscode vom Ende starten, da Prolog-Entladungscodes in umgekehrter Reihenfolge gespeichert werden. Im Allgemeinen gilt: Wenn die Entladung bei der Anweisung *n* im Prolog beginnt, sollten zuerst *n* Entladungscodes vom Ende der Codeliste ausgeführt werden.

Prolog- und Epilog-Entladungscodes stimmen nicht immer genau überein. In diesem Fall muss das Entladungscode-Array eine Reihe von Codesequenzen enthalten. Verwenden Sie folgende Logik, um den Offset für den Beginn der Verarbeitungscodes zu bestimmen:

1. Wenn die Entladung im Funktionstext erfolgt, beginnen Sie mit der Ausführung der Entladungscodes bei Index 0 und fahren Sie fort, bis ein Endopcode erreicht wird.

2. Wenn die Entladung in einem Epilog erfolgt, verwenden Sie den epilogspezifischen Index, der vom Epilogbereich zur Verfügung gestellt wird. Kalkulieren Sie, wie viele Bytes sich der PC vom Beginn des Epilogs befindet. Springen Sie in den Entladungscodes vorwärts, bis alle bereits ausgeführten Anweisungen einbezogen sind. Der Start der Entladesequenz beginnt hier.

3. Erfolgt die Entladung im Prolog, beginnen Sie ab Index 0 in den Entladungscodes. Kalkulieren Sie die Länge des Prologcodes aus der Sequenz und dann, wie viele Bytes der PC sich vom Ende des Prologs befindet. Springen Sie in den Entladungscodes vorwärts, bis alle nicht ausgeführten Anweisungen einbezogen sind. Der Start der Entladesequenz beginnt hier.

Die Entladungscodes für den Prolog müssen immer zuerst im Array sein. Sie sind auch die Codes, die für die Entladung im Text verwendet werden. Jede epilogspezifische Codesequenz muss unmittelbar nach der Prologcodesequenz folgen.

### <a name="function-fragments"></a>Funktionsfragmente

Zur Codeoptimierung kann es hilfreich sein, eine Funktion in nicht verbundene Teile aufteilen. Wenn das geschieht, erfordert jedes Funktionsfragment einen eigenen .pdata-Datensatz – und möglicherweise einen .xdata-Datensatz.

Angenommen der Funktionsprolog befindet sich am Beginn der Funktion und kann nicht geteilt werden, dann gibt es vier Funktionsfragmentfälle:

- Nur Prolog; alle Epiloge in anderen Fragmenten.

- Prolog und einer oder mehr Epiloge; weitere Epiloge in anderen Fragmenten.

- Weder Prolog noch Epilog; Prolog und einer oder mehr Epiloge in anderen Fragmenten.

- Nur Epilog; Prolog und möglicherweise weitere Epiloge in anderen Fragmenten.

In ersterem Fall muss nur der Prolog beschrieben werden. Dies kann im kompakten PDATA-Format durchgeführt werden, indem der Prolog normal beschrieben und ein *Ret*-Wert von 3 festgelegt wird, um anzugeben, dass kein Epilog vorhanden ist. Im vollen .xdata-Format kann das erledigt werden, indem man wie üblich die Prologentladungscodes in Index 0 festlegt und eine Epiloganzahl von 0 angibt.

Der zweite Fall ist genauso wie eine normale Funktion. Wenn es nur einen Epilog im Fragment gibt und sich dieser am Ende des Fragments befindet, dann kann ein kompakter PDATA-Datensatz verwendet werden. Andernfalls muss ein vollständiger .xdata-Datensatzes eingesetzt werden. Beachten Sie, dass die für den Epilogstart festgelegten Offsets relativ zum Start des Fragments und nicht dem ursprünglichen Start der Funktion sind.

Der dritte und vierte Fall ist jeweils eine Variante des ersten und zweiten Falls, mit der Ausnahme, dass kein Prolog enthalten ist. In diesen Situationen wird davon ausgegangen, dass es Code vor dem Start des Epilogs gibt und er wird als Teil des Funktionstexts betrachtet, der normalerweise durch das Rückgängigmachen des Prologeffekts entladen wird. Diese Fälle müssen deshalb mit einem Pseudoprolog codiert werden, der beschreibt, wie im Text entladen wird, aber als 0-Länge bei der Bestimmung behandelt wird, ob beim Start des Fragments eine teilweise Entladung durchgeführt wird. Alternativ lässt sich dieser Pseudoprolog beschreiben, indem dieselben Entladungscodes wie beim Epilog verwendet werden, denn sie führen mutmaßlich gleiche Vorgänge durch.

Im dritten und vierten Fall wird das Vorhandensein eines Pseudoprologs entweder durch Festlegen des *Flag*-Felds im PDATA-Datensatz auf 2 angegeben oder durch Festlegen des *F*-Flags im XDATA-Header auf 1. In beiden Fällen wird die Überprüfung auf eine teilweise Prologentladung ignoriert und alle Nicht-Epilogentladungen werden als voll betrachtet.

#### <a name="large-functions"></a>Große Funktionen

Fragmente lassen sich für die Beschreibung von Funktionen einsetzen, die größer als das 512 KB-Limit sind, das von den Bit-Feldern im .xdata-Header vorgegeben wird. Um eine sehr große Funktion zu beschreiben, brechen Sie diese einfach in Fragmente herunter, die kleiner als 512 KB sind. Jedes Fragment sollte angepasst sein, sodass es einen Epilog nicht in mehrere Teile aufteilt.

Nur das erste Fragment der Funktion enthält einen Prolog; alle anderen sind mit einer Markierung versehen, wonach sie keinen Prolog enthalten. Je nach Anzahl der Epiloge kann jedes Fragment null oder mehr Epiloge enthalten. Beachten Sie, dass jeder Epilogbereich in einem Fragment dessen Startoffset relativ zum Start des Fragments und nicht dem Start der Funktion festlegt.

Wenn ein Fragment keinen Prolog und Epilog hat, erfordert er dennoch einen eigenen .pdata-Datensatz – möglicherweise auch einen .xdata-Datensatz – für die Beschreibung, wie die Entladung im Text der Funktion stattfindet.

#### <a name="shrink-wrapping"></a>Shrink-Wrapping

Ein komplexerer Sonderfall von Funktionsfragmenten ist das *Shrink-Wrapping*. Bei dieser Technik für das Verschieben von Registerspeicherungen vom Start der Funktion zu einem späteren Zeitpunkt in der Funktion werden einfache Fälle optimiert, bei denen eine Registerspeicherung nicht erforderlich ist. Das lässt sich als eine äußere Region beschreiben, die den Stapelspeicher zuweist, aber einen minimalen Registersatz speichert sowie einer inneren Region, die weitere Register speichert und wiederherstellt.

```asm
ShrinkWrappedFunction
    push   {r4, lr}          ; A: save minimal non-volatiles
    sub    sp, sp, #0x100    ; A: allocate all stack space up front
    ...                      ; A:
    add    r0, sp, #0xE4     ; A: prepare to do the inner save
    stm    r0, {r5-r11}      ; A: save remaining non-volatiles
    ...                      ; B:
    add    r0, sp, #0xE4     ; B: prepare to do the inner restore
    ldm    r0, {r5-r11}      ; B: restore remaining non-volatiles
    ...                      ; C:
    pop    {r4, pc}          ; C:
```

Bei Funktionen mit Shrink-Wrapping geht man typischerweise davon aus, dass der Platz für die zusätzlichen Registerspeicherungen im normalen Prolog im Voraus zugewiesen wird und die Registerspeicherungen dann mithilfe von `str` oder `stm` erfolgen statt mit `push`. Damit werden alle Stapelzeigerbearbeitungen im ursprünglichen Prolog der Funktion gehalten.

Die Beispielfunktion mit Shrink-Wrapping muss in drei Regionen aufgeteilt werden, die in den Kommentaren mit A, B und C gekennzeichnet sind. Die erste Region A deckt den Start der Funktion bis zum Ende der zusätzlichen nicht flüchtigen Speicherungen ab. Es muss ein .pdata- oder .xdata-Datensatz konstruiert werden, der beschreibt, dass dieses Fragment einen Prolog und keine Epiloge hat.

Die mittlere B-Region hat einen eigenen .pdata- oder .xdata-Datensatz, der beschreibt, dass ein Fragment weder Prolog noch Epilog hat. Allerdings müssen die Entladungscodes für diese Region immer noch vorhanden sein, denn sie wird als Funktionstext betrachtet. Die Codes müssen einen zusammengesetzten Prolog beschreiben, der sowohl die ursprünglichen Register darstellt, die im Region-A-Prolog gespeichert sind, als auch die zusätzlichen Register, die vor Eintritt in Region B gespeichert wurden, als wären sie von einer Vorgangssequenz produziert worden.

Diese Registerspeicherung für Region B können nicht als "innerer Prolog" betrachtet werden, denn der für Region B beschriebene zusammengesetzte Prolog muss sowohl den Region-A-Prolog als auch die zusätzlichen, gespeicherten Register beschreiben. Würde man Fragment B so beschreiben, als hätte es einen Prolog, dann würden die Entladungscodes auch die Größe dieses Prologs implizieren, und es gibt keine Möglichkeit, den zusammengesetzten Prolog so zu beschreiben, dass eine Eins-zu-Eins-Zuordnung mit den Opcodes möglich ist, die nur die zusätzlichen Register speichern.

Die zusätzlichen Registerspeicherungen müssen als Teil von Region A betrachtet werden, denn ehe sie abgeschlossen sind, beschreibt der zusammengesetzte Prolog nicht genau den Zustand des Stapels.

Die letzte Region, C., erhält einen eigenen .pdata- oder .xdata-Datensatz, der ein Fragment beschreibt, das keinen Prolog, wohl aber einen Epilog hat.

Ein alternativer Ansatz kann ebenfalls funktionieren, wenn die Stapelbearbeitung vor Eintritt in Region B sich auf eine Anweisung reduzieren lässt:

```asm
ShrinkWrappedFunction
    push   {r4, lr}          ; A: save minimal non-volatile registers
    sub    sp, sp, #0xE0     ; A: allocate minimal stack space up front
    ...                      ; A:
    push   {r4-r9}           ; A: save remaining non-volatiles
    ...                      ; B:
    pop    {r4-r9}           ; B: restore remaining non-volatiles
    ...                      ; C:
    pop    {r4, pc}          ; C: restore non-volatile registers
```

Entscheidend ist hier, dass der Stapel bei jeder Anweisungsgrenze ganz mit den Entladungscodes für die Region übereinstimmt. Findet eine Entladung vor der inneren Pushübertagung in diesem Beispiel statt, wird sie als Teil von Region A betrachtet und nur der Region-A-Prolog wird entladen. Wenn die Entladung nach der inneren Pushübertragung stattfindet, wird sie als Teil von Region B betrachtet, die keinen Prolog hat, aber Entladungscodes besitzt, die sowohl die innere Pushübertragung als auch den ursprünglichen Prolog aus Region A beschreiben. Für den inneren Pop gilt ähnliche Logik.

### <a name="encoding-optimizations"></a>Optimierungen codieren

Da die Entladungscodes so umfangreich sind und kompakte und erweiterte Datenformen nutzen können, gibt es viele Gelegenheiten, die Codierung zu optimieren und so Platz zu sparen. Durch aggressiven Einsatz dieser Techniken lässt sich der Nettoaufwand zur Beschreibung von Funktionen und Fragmenten mithilfe von Entladungscodes recht stark minimieren.

Die wichtigste Optimierung besteht darin, sorgfältig darauf zu achten, die Prolog-/Epiloggrenzen für Entladungszwecke nicht mit ihren logischen Pendants aus Compilerperspektive zu verwechseln. Die Entladungsgrenzen lassen sich schrumpfen und verengen, was für mehr Effizienz sorgt. Ein Prolog kann beispielsweise Code für das Durchführen zusätzlicher Überprüfungen nach dem Stapelsetup enthalten. Doch nachdem die Stapelbearbeitung abgeschlossen ist, müssen keine weiteren Vorgänge mehr codiert werden und alles danach kann aus dem Entladungsprolog entfernt werden.

Die gleiche Regel gilt für Funktionslänge. Wenn es Daten gibt – zum Beispiel ein Literalpool –, der auf einen Epilog in einer Funktion folgt, dann sollte dieser nicht als Teil der Funktionslänge enthalten sein. Durch das Schrumpfen der Funktion auf lediglich den Code, der Teil der Funktion ist, sind die Chancen deutlich größer, dass der Epilog ganz am Ende und ein kompakter .pdata-Datensatz verwendet werden kann.

In einem Prolog ist es üblicherweise nicht nötig, weitere Opcodes aufzuzeichnen, nachdem der Stapelzeiger in ein anderes Register gespeichert wurde. Das erste, was zur Entladung der Funktion unternommen wird, ist das Wiederherstellen des SP aus dem gespeicherten Register. Weitere Vorgänge haben damit keine Auswirkung auf die Entladung.

Nur aus einer Anweisung bestehende Epiloge müssen überhaupt nicht codiert werden, weder als Bereiche noch als Entladungscodes. Findet eine Entladung statt, ehe diese Anweisung ausgeführt wurde, dann kann davon ausgegangen werden, dass sie aus dem Funktionstext stammt und es ist ausreichend, einfach nur die Prologentladungscodes auszuführen. Wenn die Entladung nach der einzelnen Anweisung ausgeführt wird, dann findet sie per Definition in einer anderen Region statt.

Epiloge mit mehreren Anweisungen müssen die erste Anweisung des Epilogs nicht codieren, aus demselben Grund wie im vorangehenden Punkt: Wenn die Entladung vor dem Ausführen der Anweisung stattfindet, ist eine vollständige Prologentladung ausreichend. Findet die Entladung nach dieser Anweisung statt, dann müssen nur die folgenden Vorgänge berücksichtigt werden.

Entladungscode sollte aggressiv wiederverwendet werden. Der von jedem Epilogbereich festgelegte Index zeigt auf einen willkürlichen Startpunkt im Array der Entladungscodes. Er muss nicht auf den Start einer vorangehenden Sequenz zeigen; er kann auch auf die Mitte zeigen. Der beste Ansatz hier besteht darin, die gewünschte Codesequenz zu generieren und dann nach einer exakten Byteübereinstimmung im bereits codierten Sequenzenpool zu suchen und irgendeine perfekte Übereinstimmung als Startpunkt für die Wiederverwendung zu nutzen.

Wenn nach dem Ignorieren von Epilogen mit nur einer Anweisung keine Epiloge verbleiben, dann sollten Sie den Einsatz eines kompakten .pdata-Formats in Betracht ziehen; das wird beim Fehlen eines Epilogs viel wahrscheinlicher.

## <a name="examples"></a>Beispiele

In diesen Beispielen ist die Abbildbasis bei 0x00400000.

### <a name="example-1-leaf-function-no-locals"></a>Beispiel 1: Leaf-Funktion, keine lokale Variablen

```asm
Prologue:
  004535F8: B430      push        {r4-r5}
Epilogue:
  00453656: BC30      pop         {r4-r5}
  00453658: 4770      bx          lr
```

.pdata (fest, 2 Worte):

- Word 0

  - *Function Start RVA* = 0x000535F8 (= 0x004535F8-0x00400000)

- Word 1

  - *Flag* = 1 gibt kanonische Prolog- und Epilogformate an

  - *Function Length* = 0x31 (= 0x62/2)

  - *Ret* = 1 gibt eine 16-Bit-Branchrückgabe an

  - *H* = 0 gibt an, dass die Parameter nicht herausgegriffen wurden

  - *R*=0 und *Reg* = 1 geben einen Push/Pop von r4-r5 an

  - *L* = 0 gibt an, dass es kein Speicherung/Wiederherstellung von LR gibt

  - *C* = 0 gibt an, dass es keine Rahmenverknüpfung gibt

  - *Stack Adjust* = 0 gibt an, dass es keine Stapelanpassungen gibt

### <a name="example-2-nested-function-with-local-allocation"></a>Beispiel 2: Geschachtelte Funktion mit lokaler Zuteilung

```asm
Prologue:
  004533AC: B5F0      push        {r4-r7, lr}
  004533AE: B083      sub         sp, sp, #0xC
Epilogue:
  00453412: B003      add         sp, sp, #0xC
  00453414: BDF0      pop         {r4-r7, pc}
```

.pdata (fest, 2 Worte):

- Word 0

  - *Function Start RVA* = 0x000533AC (= 0x004533AC -0x00400000)

- Word 1

  - *Flag* = 1 gibt kanonische Prolog- und Epilogformate an

  - *Function Length* = 0x35 (= 0x6A/2)

  - *Ret* = 0 gibt eine Rückgabe per Pop {pc} an

  - *H* = 0 gibt an, dass die Parameter nicht herausgegriffen wurden

  - *R*=0 und *Reg* = 3 geben einen Push/Pop von r4-r7 an

  - *L* = 1 gibt an, dass kein LR gespeichert/wiederhergestellt wurde

  - *C* = 0 gibt an, dass es keine Rahmenverknüpfung gibt

  - *Stack Adjust* = 3 (= 0x0C/4)

### <a name="example-3-nested-variadic-function"></a>Beispiel 3: Geschachtelte variadische Funktion

```asm
Prologue:
  00453988: B40F      push        {r0-r3}
  0045398A: B570      push        {r4-r6, lr}
Epilogue:
  004539D4: E8BD 4070 pop         {r4-r6}
  004539D8: F85D FB14 ldr         pc, [sp], #0x14
```

.pdata (fest, 2 Worte):

- Word 0

  - *Function Start RVA* = 0x00053988 (= 0x00453988-0x00400000)

- Word 1

  - *Flag* = 1 gibt kanonische Prolog- und Epilogformate an

  - *Function Length* = 0x2A (= 0x54/2)

  - *Ret* = 0 gibt eine Rückgabe per Pop {pc} an (in diesem Fall eine ldr pc,[sp],#0x14-Rückgabe)

  - *H* = 1 gibt an, dass die Parameter herausgegriffen wurden

  - *R*=0 und *Reg* = 2 geben einen Push/Pop von r4-r6 an

  - *L* = 1 gibt an, dass kein LR gespeichert/wiederhergestellt wurde

  - *C* = 0 gibt an, dass es keine Rahmenverknüpfung gibt

  - *Stack Adjust* = 0 gibt an, dass es keine Stapelanpassungen gibt

### <a name="example-4-function-with-multiple-epilogues"></a>Beispiel 4: Funktionen mit mehreren Epilogen

```asm
Prologue:
  004592F4: E92D 47F0 stmdb       sp!, {r4-r10, lr}
  004592F8: B086      sub         sp, sp, #0x18
Epilogues:
  00459316: B006      add         sp, sp, #0x18
  00459318: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  0045943E: B006      add         sp, sp, #0x18
  00459440: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  004595D4: B006      add         sp, sp, #0x18
  004595D6: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  00459606: B006      add         sp, sp, #0x18
  00459608: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  00459636: F028 FF0F bl          KeBugCheckEx     ; end of function
```

.pdata (fest, 2 Worte):

- Word 0

  - *Function Start RVA* = 0x000592F4 (= 0x004592F4-0x00400000)

- Word 1

  - *Flag* = 0 gibt an, dass ein XDATA-Datensatz vorhanden ist (aufgrund mehrerer Epiloge erforderlich)

  - *.xdata address:* 0x00400000

.xdata (variabel, 6 Worte):

- Word 0

  - *Function Length* = 0x0001A3 (= 0x000346/2)

  - *Vers* = 0 gibt die erste Version von XDATA an

  - *X* = 0 gibt an, dass keine Ausnahmedaten vorhanden sind

  - *E* = 0 gibt eine Liste von Epilogbereichen an

  - *F* = 0 gibt eine volle Funktionsbeschreibung einschließlich Prolog an

  - *Epilogue Count* = 0x04 gibt insgesamt 4 Epilogbereiche an

  - *Code Words* = 0x01 gibt ein 32-Bit-Wort mit Entladungscodes an

- Worte 1-4 beschreiben 4 Epilogbereiche an 4 Stellen. Jeder Bereich besitzt einen gemeinsamen Satz an Entladungscodes, der mit dem Prolog geteilt wird mit einem Offset 0x00; er ist bedingungslos, legt die Bedingung 0x0E (immer) fest.

- Entladungscodes ab Wort 5: (von Prolog und Epilog gemeinsam genutzt)

  - Entladungscode 0 = 0x06: sp += (6 << 2)

  - Entladungscode 1 = 0xDE: pop {r4-r10, lr}

  - Entladungscode 2 = 0xFF: end

### <a name="example-5-function-with-dynamic-stack-and-inner-epilogue"></a>Beispiel 5: Funktion mit dynamischem Stapel und innerem Epilog

```asm
Prologue:
  00485A20: B40F      push        {r0-r3}
  00485A22: E92D 41F0 stmdb       sp!, {r4-r8, lr}
  00485A26: 466E      mov         r6, sp
  00485A28: 0934      lsrs        r4, r6, #4
  00485A2A: 0124      lsls        r4, r4, #4
  00485A2C: 46A5      mov         sp, r4
  00485A2E: F2AD 2D90 subw        sp, sp, #0x290
Epilogue:
  00485BAC: 46B5      mov         sp, r6
  00485BAE: E8BD 41F0 ldm         sp!, {r4-r8, lr}
  00485BB2: B004      add         sp, sp, #0x10
  00485BB4: 4770      bx          lr
  ...
  00485E2A: F7FF BE7D b           #0x485B28    ; end of function
```

.pdata (fest, 2 Worte):

- Word 0

  - *Function Start RVA* = 0x00085A20 (= 0x00485A20-0x00400000)

- Word 1

  - *Flag* = 0 gibt an, dass ein XDATA-Datensatz vorhanden ist (aufgrund mehrerer Epiloge erforderlich)

  - *.xdata address:* 0x00400000

.xdata (variabel, 3 Worte):

- Word 0

  - *Function Length* = 0x0001A3 (= 0x000346/2)

  - *Vers* = 0 gibt die erste Version von XDATA an

  - *X* = 0 gibt an, dass keine Ausnahmedaten vorhanden sind

  - *E* = 0 gibt eine Liste von Epilogbereichen an

  - *F* = 0 gibt eine volle Funktionsbeschreibung einschließlich Prolog an

  - *Epilogue Count* = 0x001 gibt insgesamt einen Epilogbereiche an

  - *Code Words* = 0x01 gibt ein 32-Bit-Wort mit Entladungscodes an

- Wort 1: Epilogbereich bei einem Offset von 0xC6 (= 0x18C/2), Entladungscodeindex ab 0x00 und mit der Bedingung 0x0E (immer)

- Entladungscodes ab Wort 2: (von Prolog und Epilog gemeinsam genutzt)

  - Entladungscode 0 = 0xC6: sp = r6

  - Entladungscode 1 = 0xDC: pop {r4-r8, lr}

  - Entladungscode 2 = 0x04: sp += (4 << 2)

  - Entladungscode 3 = 0xFD: Ende, zählt als 16-Bit-Anweisung für Epilog

### <a name="example-6-function-with-exception-handler"></a>Beispiel 6: Funktion mit Ausnahmehandler

```asm
Prologue:
  00488C1C: 0059 A7ED dc.w  0x0059A7ED
  00488C20: 005A 8ED0 dc.w  0x005A8ED0
FunctionStart:
  00488C24: B590      push        {r4, r7, lr}
  00488C26: B085      sub         sp, sp, #0x14
  00488C28: 466F      mov         r7, sp
Epilogue:
  00488C6C: 46BD      mov         sp, r7
  00488C6E: B005      add         sp, sp, #0x14
  00488C70: BD90      pop         {r4, r7, pc}
```

.pdata (fest, 2 Worte):

- Word 0

  - *Function Start RVA* = 0x00088C24 (= 0x00488C24-0x00400000)

- Word 1

  - *Flag* = 0 gibt an, dass ein XDATA-Datensatz vorhanden ist (aufgrund mehrerer Epiloge erforderlich)

  - *.xdata address:* 0x00400000

.xdata (variabel, 5 Worte):

- Word 0

  - *Function Length* =0x000027 (= 0x00004E/2)

  - *Vers* = 0 gibt die erste Version von XDATA an

  - *X* = 1 gibt an, dass Ausnahmedaten vorhanden sind

  - *E* = 1 gibt einen einzelnen Epilog an

  - *F* = 0 gibt eine volle Funktionsbeschreibung einschließlich Prolog an

  - *Epilogue Count* = 0x00 gibt den Start der Epilogentladungscodes bei einem Offset von 0x00 an

  - *Code Words* = 0x02, gibt zwei 32-Bit-Worte mit Entladungscodes an

- Entladungscodes, beginnend bei Wort 1:

  - Entladungscode 0 = 0xC7: sp = r7

  - Entladungscode 1 = 0x05: sp += (5 << 2)

  - Entladungscode 2 = 0xED/0x90: pop {r4, r7, lr}

  - Entladungscode 4 = 0xFF: end

- Wort 3 legt einen Ausnahmehandler fest = 0x0019A7ED (= 0x0059A7ED – 0x00400000)

- Worte 4 und darüber hinaus sind inline gesetzte Ausnahmedaten

### <a name="example-7-funclet"></a>Beispiel 7: Funclet

```asm
Function:
  00488C72: B500      push        {lr}
  00488C74: B081      sub         sp, sp, #4
  00488C76: 3F20      subs        r7, #0x20
  00488C78: F117 0308 adds        r3, r7, #8
  00488C7C: 1D3A      adds        r2, r7, #4
  00488C7E: 1C39      adds        r1, r7, #0
  00488C80: F7FF FFAC bl          target
  00488C84: B001      add         sp, sp, #4
  00488C86: BD00      pop         {pc}
```

.pdata (fest, 2 Worte):

- Word 0

  - *Function Start RVA* = 0x00088C72 (= 0x00488C72-0x00400000)

- Word 1

  - *Flag* = 1 gibt kanonische Prolog- und Epilogformate an

  - *Function Length* = 0x0B (= 0x16/2)

  - *Ret* = 0 gibt eine Rückgabe per Pop {pc} an

  - *H* = 0 gibt an, dass die Parameter nicht herausgegriffen wurden

  - *R*=0 und *Reg* = 7 geben an, dass keine Register gespeichert/wiederhergestellt wurden

  - *L* = 1 gibt an, dass kein LR gespeichert/wiederhergestellt wurde

  - *C* = 0 gibt an, dass es keine Rahmenverknüpfung gibt

  - *Stack Adjust* = 1 gibt eine 1 × 4 Bytestapelanpassung an

## <a name="see-also"></a>Siehe auch

[Übersicht über ARM-ABI-Konventionen](overview-of-arm-abi-conventions.md)<br/>
[Häufig auftretende ARM-Migrationsprobleme bei Visual C++](common-visual-cpp-arm-migration-issues.md)
