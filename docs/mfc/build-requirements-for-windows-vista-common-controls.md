---
title: Buildanforderungen für allgemeine Windows-Steuerelemente
ms.date: 08/19/2019
helpviewer_keywords:
- Common Controls (MFC), build requirements
- Common Controls (MFC)
ms.assetid: 025f7d55-55a2-4dcd-8f62-02424e3dcc04
ms.openlocfilehash: cf2139e04d2f72feb7951010caa351d67ccc5a93
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619740"
---
# <a name="build-requirements-for-windows-common-controls"></a>Buildanforderungen für allgemeine Windows-Steuerelemente

Die MFC-Bibliothek (Microsoft Foundation Class) unterstützt [Allgemeine Windows](/windows/win32/controls/common-controls-intro)-Steuerelemente. Die allgemeinen Steuerelemente sind in Windows enthalten, und die Bibliothek ist in Visual Studio enthalten. Die MFC-Bibliothek stellt neue Methoden bereit, mit denen vorhandene Klassen erweitert werden, sowie weitere Klassen und Methoden, die allgemeine Windows-Steuerelemente unterstützen. Wenn Sie die Anwendung erstellen, sollten Sie die in den folgenden Abschnitten beschriebenen Kompilierungs-und Migrations Anforderungen befolgen.

## <a name="compilation-requirements"></a>Kompilierungs Anforderungen

### <a name="supported-versions"></a>Unterstützte Versionen

MFC unterstützt alle Versionen der allgemeinen Steuerelemente. Informationen zu allgemeinen Windows-Steuerelement Versionen finden Sie unter [allgemeine Steuerelement Versionen](/windows/win32/controls/common-control-versions).

### <a name="supported-character-sets"></a>Unterstützte Zeichensätze

Die allgemeinen Windows-Steuerelemente unterstützen nur den Unicode-Zeichensatz und nicht den ANSI-Zeichensatz. Wenn Sie die Anwendung in der Befehlszeile erstellen, verwenden Sie die beiden folgenden define-Compileroptionen (/D), um Unicode als zugrunde liegenden Zeichensatz anzugeben:

```
/D_UNICODE /DUNICODE
```

Wenn Sie die Anwendung in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio erstellen, geben Sie die Option **Unicode-Zeichensatz** der Eigenschaft **Zeichensatz** im Knoten **Allgemein** der Projekteigenschaften an.

## <a name="migration-requirements"></a>Migrations Anforderungen

Wenn Sie die Visual Studio-IDE verwenden, um eine neue MFC-Anwendung zu erstellen, die allgemeine Windows-Steuerelemente verwendet, deklariert die IDE automatisch ein entsprechendes Manifest. Wenn Sie jedoch eine vorhandene MFC-Anwendung von Visual Studio 2005 oder früher migrieren und die allgemeinen Steuerelemente verwenden möchten, stellt die IDE nicht automatisch manifestressformationen bereit, um die Anwendung zu aktualisieren. Stattdessen müssen Sie den folgenden Quellcode manuell in die vorkompilierte Header Datei einfügen:

```
#ifdef UNICODE
#if defined _M_IX86
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='x86' publicKeyToken='6595b64144ccf1df' language='*'\"")
#elif defined _M_IA64
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='ia64' publicKeyToken='6595b64144ccf1df' language='*'\"")
#elif defined _M_X64
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='amd64' publicKeyToken='6595b64144ccf1df' language='*'\"")
#else
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='*' publicKeyToken='6595b64144ccf1df' language='*'\"")
#endif
#endif
```

## <a name="see-also"></a>Siehe auch

[Allgemeine MFC-Themen](general-mfc-topics.md)<br/>
[Hierarchiediagramm](hierarchy-chart.md)<br/>
[Veraltete ANSI-APIs](deprecated-ansi-apis.md)
