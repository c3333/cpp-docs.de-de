---
title: Sicherheitsfunktionen in der CRT
ms.date: 11/04/2016
f1_keywords:
- _CRT_SECURE_NO_DEPRECATE
- _CRT_NONSTDC_NO_WARNINGS
- _CRT_SECURE_NO_WARNINGS
helpviewer_keywords:
- security deprecation warnings [C++]
- CRT_NONSTDC_NO_DEPRECATE
- buffers [C++], buffer overruns
- deprecation warnings (security-related), disabling
- _CRT_NONSTDC_NO_WARNINGS
- security [CRT]
- _CRT_SECURE_NO_WARNINGS
- _CRT_NONSTDC_NO_DEPRECATE
- _CRT_SECURE_NO_DEPRECATE
- security-enhanced CRT
- CRT_SECURE_NO_WARNINGS
- CRT_SECURE_NO_DEPRECATE
- deprecation warnings (security-related)
- buffer overruns
- CRT_NONSTDC_NO_WARNINGS
- CRT, security enhancements
- parameters [C++], validation
ms.assetid: d9568b08-9514-49cd-b3dc-2454ded195a3
ms.openlocfilehash: 1b42c766a7b75cb3f4d5c20d715968905d529d04
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361008"
---
# <a name="security-features-in-the-crt"></a>Sicherheitsfunktionen in der CRT

Viele alte CRT-Funktionen liegen in neueren, sichereren Versionen vor. Wenn eine sichere Funktion vorhanden ist, wird die ältere, weniger sichere Version als veraltet markiert, und die neue Version hat das `_s`-Suffix („sicher“).

In diesem Kontext bedeutet „veraltet“ lediglich, dass die Verwendung einer Funktion nicht empfohlen wird; es gibt nicht an, dass geplant ist, die Funktion aus der CRT zu entfernen.

Sichere Funktionen verhindern weder Sicherheitsfehler, noch korrigieren sie sie; vielmehr fangen sie Fehler beim Auftreten ab. Sie führen zusätzliche Überprüfungen auf Fehlerbedingungen durch und rufen im Falle eines Fehlers einen Fehlerhandler auf (siehe [Parametervalidierung](../c-runtime-library/parameter-validation.md)).

Die `strcpy`-Funktion kann z.B. nicht mitteilen, ob die Zeichenfolge, die sie kopiert, zu groß für den Zielpuffer ist. Ihr sicheres Gegenstück `strcpy_s` übernimmt allerdings die Größe des Puffers als Parameter, damit sie bestimmen kann, wann ein Pufferüberlauf erfolgt. Wenn Sie `strcpy_s` verwenden, um elf Zeichen in einen Zehnzeichenpuffer zu kopieren, liegt der Fehler bei Ihnen; `strcpy_s` kann Ihren Fehler nicht beheben, jedoch erkennen und Sie durch Aufrufen des Handlers für ungültige Parameter informieren.

## <a name="eliminating-deprecation-warnings"></a>Beseitigen von Ablaufwarnungen

Es gibt mehrere Möglichkeiten, um Ablaufwarnungen für die älteren, weniger sicheren Funktionen zu beseitigen. Die einfachste Möglichkeit ist, `_CRT_SECURE_NO_WARNINGS` zu definieren oder das [warning](../preprocessor/warning.md)-Pragma zu verwenden. Jede deaktiviert Ablaufwarnungen, aber die Sicherheitsprobleme, die die Warnung verursacht haben, sind natürlich noch vorhanden. Es ist wesentlich besser, Ablaufwarnungen aktiviert zu lassen und die neuen CRT-Sicherheitsfunktionen zu nutzen.

In C++ erfolgt dies am einfachsten mit der Verwendung von [sicheren Vorlagenüberladungen](../c-runtime-library/secure-template-overloads.md), die in vielen Fällen Ablaufwarnungen durch den Ersatz der Aufrufe veralteter Funktionen durch Aufrufe neuer, sicherer Versionen dieser Funktionen beseitigen. Ein Beispiel ist dieser veraltete Aufruf von `strcpy`:

```
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

Durch Definieren von `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` als 1 wird die Warnung beseitigt, indem der `strcpy`-Aufruf in `strcpy_s` geändert wird, was Pufferüberläufe verhindert. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../c-runtime-library/secure-template-overloads.md).

Für diese veralteten Funktionen ohne sichere Vorlagenüberladungen sollten Sie definitiv erwägen, den Code manuell zu aktualisieren, um die sicheren Versionen zu verwenden.

Eine andere Quelle von Ablaufwarnungen, unabhängig von der Sicherheit, sind POSIX-Funktionen. Ersetzen Sie POSIX-Funktionsnamen durch Ihre Standardentsprechungen (ändern Sie z.B. [access](../c-runtime-library/reference/access-crt.md) in [_access](../c-runtime-library/reference/access-waccess.md)), oder deaktivieren Sie POSIX-bezogene Ablaufwarnungen durch Definieren von `_CRT_NONSTDC_NO_WARNINGS`. Weitere Informationen finden Sie unter [Kompatibilität](compatibility.md).

## <a name="additional-security-features"></a>Zusätzliche Sicherheitsfunktionen

Zu den wichtigsten Sicherheitsfunktionen zählen Folgende:

- `Parameter Validation`. An CRT-Funktionen übergebene Parameter werden sowohl in sicheren Funktionen als auch in vielen bereits vorhandenen Versionen der Funktionen überprüft. Diese Überprüfungen umfassen:

  - Überprüfung auf **NULL**-Werte, die den Funktionen übergeben werden.

  - Überprüfung von Enumerationswerten auf Gültigkeit.

  - Überprüfen, ob ganzzahlige Werte im gültigen Bereiche liegen.

- Weitere Informationen finden Sie unter [Parametervalidierung](../c-runtime-library/parameter-validation.md).

- Auf einen Handler für ungültige Parameter kann auch der Entwickler zugreifen. Wenn ein ungültiger Parameter festgestellt wird, bietet die CRT eine Möglichkeit, diese Probleme mit der [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)-Funktion zu überprüfen, anstatt dies zu bestätigen und die Anwendung zu beenden.

- `Sized Buffers`. Die sicheren Funktionen erfordern, dass die Größe des Puffers an alle Funktionen übergeben wird, die in einen Puffer schreiben. Die sicheren Versionen überprüfen, ob der Puffer groß genug ist, bevor sie darin schreiben, um gefährliche Pufferüberlauffehler zu vermeiden, die die Ausführung bösartigen Codes zulassen könnten. Diese Funktionen geben in der Regel einen Fehlercode des Typs `errno` zurück und rufen den Handler für ungültige Parameter auf, wenn der Puffer zu klein ist. Funktionen, die wie `gets` aus Eingabepuffern lesen, haben sichere Versionen, die von Ihnen die Angabe einer maximalen Größe fordern.

- `Null termination`. Einige Funktionen, die potenziell nicht beendete Zeichenfolgen hinterlassen haben, haben sichere Versionen, die sicherstellen, dass Zeichenfolgen ordnungsgemäß mit NULL enden.

- `Enhanced error reporting`. Die sicheren Funktionen geben Fehlercodes mit mehr Fehlerinformationen zurück, als bei den bereits vorhandenen Funktionen verfügbar waren. Die sicheren Funktionen und viele der bereits vorhandenen Funktionen legen jetzt `errno` fest und geben häufig ebenfalls einen `errno`-Codetyp zurück, um eine bessere Fehlerberichterstattung zu bieten.

- `Filesystem security`. Sichere Datei-E/A-APIs unterstützen sicheren Dateizugriff im Standardfall.

- `Windows security`. Sichere Prozess-APIs setzen Sicherheitsrichtlinien durch und lassen die Angabe von ACLs zu.

- `Format string syntax checking`. Ungültige Zeichenfolgen werden erkannt, z.B. Verwendung falscher Typfeldzeichen in `printf`-Formatzeichenfolgen.

## <a name="see-also"></a>Siehe auch

[Parameterüberprüfung](../c-runtime-library/parameter-validation.md)<br/>
[Sichere Vorlagenüberladungen](../c-runtime-library/secure-template-overloads.md)<br/>
[CRT-Bibliotheksfunktionen](../c-runtime-library/crt-library-features.md)
