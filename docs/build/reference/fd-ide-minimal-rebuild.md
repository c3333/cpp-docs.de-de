---
title: /FD (Minimale Neuerstellung in der IDE)
ms.date: 04/08/2019
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: 896adcb97a259e6714cf23241424841456371491
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439808"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (Minimale Neuerstellung in der IDE)

**/FD** wird nur für Benutzer auf der Eigenschaften Seite [Befehlszeile](command-line-property-pages.md) im Dialogfeld C++ **Eigenschaften Seiten** eines Projekts verfügbar gemacht. Diese Option ist nur dann verfügbar, wenn die Option veraltet und Standard [/GM (minimale Neuerstellung aktivieren)](gm-enable-minimal-rebuild.md) nicht ausgewählt ist. **/FD** hat keine Auswirkung außer der Entwicklungsumgebung. **/FD** wird nicht in der Ausgabe von `cl /?`verfügbar gemacht.

Wenn Sie die Option "veraltet **/GM** " in der Entwicklungsumgebung nicht aktivieren, wird **/FD** verwendet. **/FD** stellt sicher, dass die IDB-Datei über ausreichende Abhängigkeitsinformationen verfügt. **/FD** wird nur von der Entwicklungsumgebung verwendet und sollte nicht über die Befehlszeile oder ein Buildskript verwendet werden.

## <a name="see-also"></a>Weitere Informationen

[Ausgabedatei (/F) Optionen](output-file-f-options.md)<br/>
[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)
