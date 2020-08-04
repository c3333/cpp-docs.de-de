---
title: Verwendung von Stapeln bei x64-Systemen
ms.date: 12/17/2018
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
ms.openlocfilehash: b1b1e0a8c30d5e24e81372912d5c488efce14841
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218935"
---
# <a name="x64-stack-usage"></a>Verwendung von Stapeln bei x64-Systemen

Der gesamte Arbeitsspeicher, der hinter der aktuellen RSP-Adresse liegt, gilt als flüchtig: Das Betriebssystem oder ein Debugger kann diesen Arbeitsspeicher während einer Benutzerdebugsitzung oder eines Interrupthandlers überschreiben. Daher muss RSP immer gesetzt werden, bevor versucht wird, Werte in einen Stapelrahmen zu lesen oder zu schreiben.

In diesem Abschnitt wird die Belegung des Stapelspeichers für lokale Variablen und die intrinsische Funktion **alloca** besprochen.

## <a name="stack-allocation"></a>Stapelbelegung

Im Prolog einer Funktion wird der Stapelspeicher für lokale Variablen, gespeicherte Register, Stapelparameter und Registerparameter zugeordnet.

Der Parameterbereich befindet sich immer unten im Stapel (selbst wenn `alloca` verwendet wird), sodass er sich während eines Funktionsaufrufs immer neben der Rücksprungadresse befindet. Er enthält mindestens vier Einträge, jedoch immer genügend Speicherplatz für alle Parameter, die von einer beliebigen aufrufbaren Funktion benötigt werden. Beachten Sie, dass für die Registerparameter immer Speicher belegt wird, selbst wenn die Parameter nie im Stapel gespeichert werden. Einer aufgerufenen Funktion wird garantiert, dass für alle ihre Parameter Speicher belegt wurde. Für Registerargumente werden die Stammadressen benötigt, damit ein zusammenhängender Bereich verfügbar ist, falls die aufgerufene Funktion die Adresse der Argumentliste (va_list) oder ein einzelnes Arguments nehmen muss. Dieser Bereich ist außerdem eine gute Stelle, um Registerargumente während der Thunkingausführung zu speichern, und eignet sich als Debugoption (Argumente sind beim Debugging z. B. einfach zu finden, wenn sie an ihrer Stammadresse gespeichert werden). Selbst wenn die aufgerufene Funktion weniger als 4 Parameter hat, gehören diese 4 Speicherorte auf dem Stapel effektiv der aufgerufenen Funktion und können von der aufgerufenen Funktion auch zu anderen Zwecken als der Speicherung der Werte von Registerparametern verwendet werden.  Folglich speichert die aufrufende Funktion während eines Funktionsaufrufs möglicherweise keine Informationen in diesem Stapelbereich.

Wenn Speicherplatz in einer Funktion dynamisch (`alloca`) belegt wird, muss ein nicht flüchtiges Register als Rahmenzeiger verwendet werden, um die Basis des festen Stapelteils zu markieren. Dieses Register muss im Prolog gespeichert und initialisiert werden. Beachten Sie bei Verwendung von `alloca` Folgendes: Die Registerparameter einer aufgerufenen Funktion können unterschiedliche Stammadressen aufweisen, obwohl die Aufrufe von derselben aufrufenden Funktion getätigt werden.

Der Stapel bleibt immer am 16-Byte-Format ausgerichtet. Die einzigen Ausnahmen sind der Prolog (z. B. nachdem die Rücksprungadresse gepusht wurde) und die unter [Funktionstypen](#function-types) angegebenen Stellen, die für bestimmte Klassen von Rahmenfunktionen vorgesehen sind.

Nachstehend finden Sie ein Beispiel für ein Stapellayout, in dem Funktion A eine Funktion B aufruft, die keine Blattfunktion ist. Im Prolog von Funktion A wurde bereits Speicherplatz für alle Register und Stapelparameter belegt, die von B am Ende des Stapels benötigt werden. Der Aufruf pusht die Rücksprungadresse, und der Prolog von B belegt den Speicherplatz für die lokalen Variablen, die nicht flüchtigen Register und den Speicherplatz der Funktion B, der benötigt wird, um Funktionen aufzurufen. Wenn Funktion B `alloca` verwendet, wird der Speicherplatz zwischen dem Speicherbereich für die lokalen Variablen oder die nicht flüchtigen Register und dem Stapelbereich für die Parameter belegt.

![AMD-Konvertierungsbeispiel](../build/media/vcamd_conv_ex_5.png "AMD-Konvertierungsbeispiel")

Wenn die Funktion B eine andere Funktion aufruft, wird die Rücksprungadresse direkt unterhalb der Stammadresse von RCX eingeordnet.

## <a name="dynamic-parameter-stack-area-construction"></a>Dynamisches Erstellen des Stapelbereichs für Parameter

Wenn ein Rahmenzeiger verwendet wird, kann der Parameterstapelbereich dynamisch erstellt werden. Der x64-Compiler bietet diese Option derzeit nicht.

## <a name="function-types"></a>Funktionstypen

Es gibt im Grunde zwei Arten von Funktionen. Eine Funktion, die einen Stapelrahmen erfordert, wird als *Rahmenfunktion* bezeichnet. Eine Funktion, die keinen Stapelrahmen erfordert, wird *Blattfunktion* genannt.

Eine Rahmenfunktion ist eine Funktion, die Stapelspeicher belegt, andere Funktionen aufruft, nicht flüchtige Register speichert oder die Ausnahmebehandlung verwendet. Außerdem erfordert eine solche Funktion einen Eintrag in eine Funktionstabelle. Eine Rahmenfunktion erfordert außerdem einen Prolog und einen Epilog. Eine Rahmenfunktion kann Stapelspeicher dynamisch belegen und einen Rahmenzeiger einsetzen. Eine Rahmenfunktion verfügt über die vollständige Funktionalität dieses Aufrufstandards.

Wenn eine Rahmenfunktion keine andere Funktion aufruft, ist es nicht erforderlich, den Stapel auszurichten (im Abschnitt [Stapelbelegung](#stack-allocation) angesprochen).

Eine Blattfunktion erfordert keinen Eintrag in eine Funktionstabelle. Blattfunktionen können keine Änderungen an nicht flüchtigen Registern vornehmen, einschließlich RSP. Dies bedeutet, dass sie keine Funktionen aufrufen oder Stapelspeicher belegen können. Es ist zulässig, dass der Stapel während der Ausführung unausgerichtet bleibt.

## <a name="malloc-alignment"></a>malloc-Ausrichtung

[malloc](../c-runtime-library/reference/malloc.md) gibt immer Speicher zurück, der korrekt ausgerichtet ist, um ein beliebiges Objekt zu speichern, das eine grundlegende Ausrichtung hat und in den zugeordneten Speicher passen kann. Eine *grundlegende Ausrichtung* ist eine Ausrichtung, die kleiner oder gleich der größten Ausrichtung ist, die von der Implementierung ohne Ausrichtungsspezifikation unterstützt wird. (In Visual C++ ist dies die Ausrichtung, die für einen **`double`** - oder 8-Byte-Typ erforderlich ist. In einem Code, der auf 64-Bit-Plattformen ausgerichtet ist, sind dies 16 Bytes.) Beispielsweise kann eine Vier-Byte-Speicherbelegung an einer Grenze ausgerichtet werden, die Objekte unterstützt, die maximal vier Byte groß sind.

Visual C++ unterstützt Typen mit einer *erweiterten Ausrichtung*, die auch als Typen mit *erhöhter Ausrichtung* bezeichnet werden. Die SEE-Typen [__m128](../cpp/m128.md) und `__m256` sowie die Typen, die von `__declspec(align( n ))` deklariert werden, wobei `n` größer ist als 8, verfügen beispielsweise über eine erweiterte Ausrichtung. Eine Speicherausrichtung an einer Grenze, die für ein Objekt geeignet ist, das eine erweiterte Ausrichtung erfordert, wird von `malloc` nicht gewährleistet. Verwenden Sie zur Speicherbelegung für erweitert ausgerichtete Typen [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) und verwandte Funktionen.

## <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md) muss an 16-Byte ausgerichtet sein und zusätzlich einen Rahmenzeiger verwenden.

Der zugeordnete Stapel muss danach weiteren Speicherplatz für die Parameter der anschließend aufgerufenen Funktionen enthalten. Dies wird unter [Stapelbelegung](#stack-allocation) erläutert.

## <a name="see-also"></a>Siehe auch

[Softwarekonventionen bei x64-Systemen](../build/x64-software-conventions.md)<br/>
[align](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)
