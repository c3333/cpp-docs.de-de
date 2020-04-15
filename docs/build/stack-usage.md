---
title: Verwendung von Stapeln bei x64-Systemen
ms.date: 12/17/2018
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
ms.openlocfilehash: b598c33fbdd56630ca3e5ef0da551f38a73baa26
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335535"
---
# <a name="x64-stack-usage"></a>Verwendung von Stapeln bei x64-Systemen

Der gesamte Speicher, der über die aktuelle Adresse von RSP hinausgeht, wird als flüchtig betrachtet: Das Betriebssystem oder ein Debugger kann diesen Speicher während einer Benutzerdebugsitzung oder eines Interrupthandlers überschreiben. Daher muss RSP immer festgelegt werden, bevor versucht wird, Werte in einen Stapelrahmen zu lesen oder zu schreiben.

In diesem Abschnitt wird die Zuweisung von Stapelspeicher für lokale Variablen und die intrinsische **Zuordnung** erläutert.

## <a name="stack-allocation"></a>Stack allocation (Stapelreservierung)

Der Prolog einer Funktion ist für die Zuweisung von Stapelspeicher für lokale Variablen, gespeicherte Register, Stapelparameter und Registerparameter verantwortlich.

Der Parameterbereich befindet sich immer am unteren `alloca` Rand des Stapels (auch wenn er verwendet wird), so dass er während eines Funktionsaufrufs immer an die Rückgabeadresse angrenzt. Es enthält mindestens vier Einträge, aber immer genug Platz, um alle Parameter zu enthalten, die für jede Funktion benötigt werden, die aufgerufen werden kann. Beachten Sie, dass für die Registerparameter immer Speicherplatz reserviert ist, auch wenn die Parameter selbst nie im Stapel enthalten sind. Ein Angerufener ist garantiert, dass Platz für alle parameter zugewiesen wurde. Für die Registerargumente sind Startadressen erforderlich, sodass ein zusammenhängender Bereich verfügbar ist, falls die aufgerufene Funktion die Adresse der Argumentliste (va_list) oder eines einzelnen Arguments annehmen muss. Dieser Bereich bietet auch einen bequemen Ort, um Registerargumente während der Thunk-Ausführung und als Debugging-Option zu speichern (z. B. macht es die Argumente beim Debuggen leicht zu finden, wenn sie an ihren Stammadressen im Prolog-Code gespeichert sind). Selbst wenn die aufgerufene Funktion weniger als 4 Parameter hat, sind diese 4 Stapelpositionen effektiv im Besitz der aufgerufenen Funktion und können von der aufgerufenen Funktion für andere Zwecke außer dem Speichern von Parameterregisterwerten verwendet werden.  Daher kann der Aufrufer keine Informationen in diesem Bereich des Stapels über einen Funktionsaufruf speichern.

Wenn In einer`alloca`Funktion dynamisch Platz zugewiesen wird ( ), muss ein nichtflüchtiges Register als Framezeiger verwendet werden, um die Basis des festen Teils des Stapels zu markieren, und dieses Register muss im Prolog gespeichert und initialisiert werden. Beachten Sie, dass Anrufe an denselben Angerufenen vom gleichen Aufrufer unterschiedliche Startadressen für ihre Registerparameter haben können, wenn `alloca` sie verwendet werden.

Der Stapel wird immer 16-Byte ausgerichtet gehalten, außer innerhalb des Prologs (z. B. nachdem die Rückgabeadresse gedrückt wurde), und es sei denn, dies ist in [Funktionstypen](#function-types) für eine bestimmte Klasse von Framefunktionen angegeben.

Im Folgenden finden Sie ein Beispiel für das Stapellayout, bei dem Funktion A eine Nicht-Blattfunktion B aufruft. Der Prolog von Funktion A hat bereits Platz für alle Register- und Stapelparameter zugewiesen, die von B am unteren Rand des Stapels benötigt werden. Der Aufruf überträgt die Rückgabeadresse, und Bs Prolog weist Platz für seine lokalen Variablen, nichtflüchtigen Register und den Platz zu, der für den Aufruf von Funktionen benötigt wird. Wenn B `alloca`verwendet, wird der Abstand zwischen dem lokalen Variablen-/Nichtflüchtigen-Registerspeicherbereich und dem Parameterstapelbereich zugewiesen.

![AMD-Konvertierungsbeispiel](../build/media/vcamd_conv_ex_5.png "AMD-Konvertierungsbeispiel")

Wenn die Funktion B eine andere Funktion aufruft, wird die Rücksendeadresse knapp unter die Home-Adresse für RCX gedrückt.

## <a name="dynamic-parameter-stack-area-construction"></a>Dynamische Parameter-Stack-Flächenkonstruktion

Wenn ein Framezeiger verwendet wird, ist die Option zum dynamischen Erstellen des Parameterstapelbereichs vorhanden. Dies geschieht derzeit nicht im x64-Compiler.

## <a name="function-types"></a>Funktionstypen

Es gibt im Grunde zwei Arten von Funktionen. Eine Funktion, die einen Stapelrahmen erfordert, wird als *Framefunktion*bezeichnet. Eine Funktion, die keinen Stapelrahmen erfordert, wird als *Blattfunktion*bezeichnet.

Eine Frame-Funktion ist eine Funktion, die Stapelspeicher zuweist, andere Funktionen aufruft, nichtflüchtige Register speichert oder Ausnahmebehandlung verwendet. Es erfordert auch einen Funktionstabelleneintrag. Eine Frame-Funktion erfordert einen Prolog und einen Epilog. Eine Frame-Funktion kann stapelbaren Speicherplatz dynamisch zuweisen und einen Framezeiger verwenden. Eine Frame-Funktion verfügt über die vollen Funktionen dieses Aufrufstandards.

Wenn eine Frame-Funktion keine andere Funktion aufruft, ist es nicht erforderlich, den Stapel auszurichten (im Abschnitt [Stack Allocation](#stack-allocation)referenziert).

Eine Blattfunktion ist eine Funktion, die keinen Funktionstabelleneintrag erfordert. Es kann keine Änderungen an nichtflüchtigen Registern vornehmen, einschließlich RSP, was bedeutet, dass es keine Funktionen aufrufen oder Stapelspeicher zuweisen kann. Es ist erlaubt, den Stapel nicht ausgerichtet zu lassen, während er ausgeführt wird.

## <a name="malloc-alignment"></a>malloc Ausrichtung

[malloc](../c-runtime-library/reference/malloc.md) gibt garantiert Speicher zurück, der für die Speicherung eines Objekts, das eine grundlegende Ausrichtung hat und in die zugewiesene Speichermenge passen könnte, angemessen ausgerichtet ist. Eine *grundlegende Ausrichtung* ist eine Ausrichtung, die kleiner oder gleich der größten Ausrichtung ist, die von der Implementierung ohne Ausrichtungsspezifikation unterstützt wird. (In Visual C++ ist dies die Ausrichtung, die für einen `double` oder 8 Bytes erforderlich ist. In Code, der auf 64-Bit-Plattformen abzielt, sind es 16 Bytes.) Beispielsweise würde eine Zuweisung mit vier Byte an einer Grenze ausgerichtet, die ein beliebiges Vierbyte- oder kleineres Objekt unterstützt.

Visual C++ ermöglicht Typen mit *erweiterter Ausrichtung*, die auch als *überausgerichtete* Typen bezeichnet werden. Beispielsweise weisen die SSE-Typen [__m128](../cpp/m128.md) und `__m256`, `__declspec(align( n ))` und `n` die Typen, die mit der Verwendung von where größer als 8 deklariert werden, eine erweiterte Ausrichtung. Eine Speicherausrichtung an einer Grenze, die für ein Objekt geeignet ist, das eine erweiterte Ausrichtung erfordert, wird von `malloc` nicht gewährleistet. Um Speicher für überausgerichtete Typen zuzuweisen, verwenden Sie [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) und verwandte Funktionen.

## <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md) ist erforderlich, um 16-Byte-ausgerichtet zu sein und zusätzlich erforderlich, um einen Frame-Zeiger zu verwenden.

Der zugeordnete Stapel muss Speicherplatz für Parameter von später aufgerufenen Funktionen enthalten, wie in [Stack Allocation](#stack-allocation)erläutert.

## <a name="see-also"></a>Siehe auch

[Softwarekonventionen bei x64-Systemen](../build/x64-software-conventions.md)<br/>
[Ausrichten](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)
