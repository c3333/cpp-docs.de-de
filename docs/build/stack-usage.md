---
title: Verwendung von Stapeln bei x64-Systemen
ms.date: 12/17/2018
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
ms.openlocfilehash: 902e4304ac124be46c6edf0860118dc522b34890
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422751"
---
# <a name="x64-stack-usage"></a>Verwendung von Stapeln bei x64-Systemen

Der gesamte Arbeitsspeicher, der über die aktuelle RSP-Adresse hinausgeht, gilt als flüchtig: das Betriebssystem oder ein Debugger kann diesen Arbeitsspeicher während einer benutzerdebugsitzung oder eines Interrupthandlers überschreiben Daher muss RSP immer festgelegt werden, bevor versucht wird, Werte in einen Stapel Rahmen zu lesen oder zu schreiben.

In diesem Abschnitt wird die Zuordnung von Stapel Speicher für lokale Variablen und die systeminterne **alloca** -Funktion erläutert.

## <a name="stack-allocation"></a>Stapel Zuordnung

Der Prolog einer Funktion ist dafür verantwortlich, Stapel Speicher für lokale Variablen, gespeicherte Register, Stapel Parameter und Register Parameter zuzuordnen.

Der Parameter Bereich befindet sich immer am unteren Rand des Stapels (auch wenn `alloca` verwendet wird), sodass er während eines beliebigen Funktions Aufrufes immer an die Rückgabeadresse angrenzt. Sie enthält mindestens vier Einträge, aber immer genug Platz, um alle Parameter zu speichern, die von einer Funktion benötigt werden, die aufgerufen werden kann. Beachten Sie, dass Speicherplatz immer für die Register Parameter zugewiesen wird, auch wenn die Parameter selbst niemals dem Stapel zugeordnet werden. bei einem aufgerufenen ist sichergestellt, dass der Speicherplatz für alle seine Parameter reserviert wurde. Privatadressen werden für die Register Argumente benötigt, damit ein zusammenhängender Bereich verfügbar ist, wenn die aufgerufene Funktion die Adresse der Argumentliste (va_list) oder eines einzelnen Arguments annehmen muss. Dieser Bereich bietet auch eine praktische Möglichkeit zum Speichern von Register Argumenten während der Thunk-Ausführung und als Debugoption (z. b., wenn die Argumente beim Debuggen an ihrer eigenen Adresse gespeichert werden). Auch wenn die aufgerufene Funktion über weniger als vier Parameter verfügt, sind diese vier Stapel Speicherorte im Besitz der aufgerufenen Funktion und können von der aufgerufenen Funktion für andere Zwecke verwendet werden, neben dem Speichern der Parameter Registerwerte.  Folglich speichert der Aufrufer möglicherweise keine Informationen in diesem Stapelbereich über einen Funktionsaufruf.

Wenn Speicherplatz dynamisch (`alloca`) in einer Funktion zugewiesen wird, muss ein nicht flüchtiges Register als Frame Zeiger verwendet werden, um die Basis des fixierten Teils des Stapels zu markieren, und dieses Register muss im Prolog gespeichert und initialisiert werden. Beachten Sie, dass bei der Verwendung von `alloca` die Aufrufe desselben Aufrufers von demselben Aufrufer möglicherweise unterschiedliche Privatadressen für die Register Parameter aufweisen.

Der Stapel wird immer mit einem 16-Byte-Ausrichtung verwaltet, mit Ausnahme des Prologs (z. b. Nachdem die Rückgabeadresse gedrückt wurde) und mit Ausnahme der Angabe in den [Funktionstypen](#function-types) für eine bestimmte Klasse von Frame Funktionen.

Im folgenden finden Sie ein Beispiel für das Stapel Layout, bei dem Funktion a eine nicht Blatt Funktion B aufruft. der Prolog von function a hat bereits Speicherplatz für alle Register-und Stapel Parameter zugewiesen, die von B am unteren Rand des Stapels benötigt werden. Der-Befehl überträgt die Rückgabeadresse, und der Prolog von B ordnet Speicherplatz für die lokalen Variablen, nicht flüchtige Register und den Speicherplatz zu, der benötigt wird, um Funktionen aufzurufen. Wenn B `alloca`verwendet, wird der Speicherplatz zwischen dem lokalen Variablen/dem nicht flüchtigen Registrierungs Speicherbereich und dem Parameter Stapelbereich zugeordnet.

![AMD-Konvertierungs Beispiel](../build/media/vcamd_conv_ex_5.png "AMD-Konvertierungsbeispiel")

Wenn die Funktion B eine andere Funktion aufruft, wird die Rückgabeadresse direkt unterhalb der Home-Adresse für RCX übermittelt.

## <a name="dynamic-parameter-stack-area-construction"></a>Dynamische Parameter Stapel Bereichs Konstruktion

Wenn ein Frame Zeiger verwendet wird, ist die Option vorhanden, um den Parameter Stapelbereich dynamisch zu erstellen. Dies erfolgt zurzeit nicht im x64-Compiler.

## <a name="function-types"></a>Funktionstypen

Es gibt im Grunde zwei Arten von Funktionen. Eine Funktion, die einen Stapel Rahmen erfordert, wird als *Frame Funktion*bezeichnet. Eine Funktion, die keinen Stapel Rahmen erfordert, wird als *Blatt Funktion*bezeichnet.

Eine Frame-Funktion ist eine Funktion, die Stapel Speicher belegt, andere Funktionen aufruft, nicht flüchtige Register speichert oder die Ausnahmebehandlung verwendet. Außerdem ist ein Funktionstabellen Eintrag erforderlich. Eine Frame-Funktion erfordert einen Prolog und ein Epilog. Eine Frame-Funktion kann Stapel Speicher dynamisch zuordnen und einen Frame Zeiger verwenden. Eine Frame Funktion verfügt über die vollständigen Funktionen dieses aufrufenden Standards.

Wenn eine Frame-Funktion keine andere Funktion aufruft, muss der Stapel nicht ausgerichtet werden (in der Abschnitts [Stapel Zuordnung](#stack-allocation)wird darauf verwiesen).

Eine Blatt Funktion ist ein Eintrag, der keinen Funktionstabellen Eintrag erfordert. Es können keine Änderungen an nicht flüchtigen Registern vorgenommen werden, einschließlich RSP. Dies bedeutet, dass keine Funktionen aufgerufen oder Stapel Speicher belegt werden kann. Der Stapel kann während der Ausführung nicht ausgerichtet bleiben.

## <a name="malloc-alignment"></a>malloc-Ausrichtung

[malloc](../c-runtime-library/reference/malloc.md) gibt sicher einen Speicher zurück, der für das Speichern von Objekten geeignet ist, die eine grundlegende Ausrichtung haben und in den zugeordneten Arbeitsspeicher passen. Eine *grundlegende Ausrichtung* ist eine Ausrichtung, die kleiner oder gleich der größten Ausrichtung ist, die von der Implementierung ohne eine Ausrichtungs Spezifikation unterstützt wird. (In Visual C++ ist dies die Ausrichtung, die für einen `double` oder 8 Bytes erforderlich ist. In Code, der auf 64-Bit-Plattformen ausgerichtet ist, sind es 16 Bytes.) Beispielsweise würde eine 4-Byte-Zuordnung an einer Begrenzung ausgerichtet sein, die ein beliebiges vier-Byte-Objekt unterstützt.

Visual C++ lässt Typen zu, die über *Erweiterte Ausrichtung*verfügen und auch als *über ausgerichtete* Typen bezeichnet werden. Beispielsweise haben die SSE-Typen [__m128](../cpp/m128.md) und `__m256`, und Typen, die mithilfe `__declspec(align( n ))` deklariert werden, bei denen `n` größer als 8 ist, haben die Ausrichtung erweitert. Eine Speicherausrichtung an einer Grenze, die für ein Objekt geeignet ist, das eine erweiterte Ausrichtung erfordert, wird von `malloc` nicht gewährleistet. Um Arbeitsspeicher für über ausgerichtete Typen zuzuweisen, verwenden Sie [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) und verwandte Funktionen.

## <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md) muss 16-Byte-ausgerichtet sein, und zusätzlich muss ein Frame Zeiger verwendet werden.

Der zugeordnete Stapel muss nach ihm für Parameter der später aufgerufenen Funktionen Leerzeichen enthalten, wie in der [Stapel Zuordnung](#stack-allocation)erläutert.

## <a name="see-also"></a>Siehe auch

[Softwarekonventionen bei x64-Systemen](../build/x64-software-conventions.md)<br/>
[align](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)
