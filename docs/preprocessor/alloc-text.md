---
title: alloc_text-Pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
helpviewer_keywords:
- alloc_text pragma
- pragmas, alloc_text
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
ms.openlocfilehash: c638c2026a493453aeb5aff00ba6273efb5f184e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219442"
---
# <a name="alloc_text-pragma"></a>alloc_text-Pragma

Namen des Codeabschnitts, in dem sich die angegebenen Funktionsdefinitionen befinden müssen. Das Pragma muss zwischen einem Funktionsdeklarator und der Funktionsdefinition für die benannten Funktionen auftreten.

## <a name="syntax"></a>Syntax

> **#pragma alloc_text (** "*Textsection*" **,** *Funktion1* [**,** *Funktion2* ...] **)**

## <a name="remarks"></a>Bemerkungen

Das **alloc_text** -Pragma verarbeitet keine C++-Member-Funktionen oder überladenen Funktionen. Dies gilt nur für Funktionen, die mit C-Verknüpfung deklariert sind, d. –. Funktionen, die mit der **externen "c"** -Verknüpfungs Spezifikation deklariert werden. Wenn Sie versuchen, diese Pragma für eine Funktion mit C++-Bindung zu verwenden, wird ein Compilerfehler generiert.

Da die Verwendung von mit der Verwendung **`__based`** von nicht unterstützt wird, muss für die Angabe von Abschnitts Speicherorten das **alloc_text** -Pragma verwendet werden Der von *Text section* angegebene Name muss in doppelte Anführungszeichen eingeschlossen werden.

Das **alloc_text** -Pragma muss nach den Deklarationen der angegebenen Funktionen und vor den Definitionen dieser Funktionen angezeigt werden.

Funktionen, auf die in einem **alloc_text** -Pragma verwiesen wird, müssen im selben Modul wie das Pragma definiert werden. Andernfalls kann der Fehler abgefangen werden, wenn eine nicht definierte Funktion später in einen anderen Textabschnitt kompiliert wird. Obwohl das Programm in der Regel ordnungsgemäß ausgeführt wird, ist die Funktion nicht in den vorgesehenen Abschnitten zugeordnet.

Weitere Einschränkungen für **alloc_text** lauten wie folgt:

- Sie kann nicht innerhalb einer Funktion verwendet werden.

- Es muss verwendet werden, nachdem die Funktion deklariert wurde, aber bevor die Funktion definiert wurde.

## <a name="see-also"></a>Weitere Informationen

[Pragma-Anweisungen und das __pragma-Schlüsselwort](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
