---
title: iostreams-Konventionen
ms.date: 11/04/2016
helpviewer_keywords:
- iostream header
- C++ Standard Library, iostreams
ms.assetid: 9fe5ded0-37a1-48d1-9671-c81ffc4760ad
ms.openlocfilehash: 7bfc497ec7c55a611d29cd62d076c0ac2e9b6e9f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845457"
---
# <a name="iostreams-conventions"></a>iostreams-Konventionen

Der iostreams-Headers unterstützen Konvertierungen zwischen Text und kodierten Formen, und zwischen Eingabe und Ausgabe in externe Dateien:

[\<fstream>](../standard-library/fstream.md)\
[\<iomanip>](../standard-library/iomanip.md)\
[\<ios>](../standard-library/ios.md)\
[\<iosfwd>](../standard-library/iosfwd.md)\
[\<iostream>](../standard-library/iostream.md)\
[\<istream>](../standard-library/istream.md)\
[\<ostream>](../standard-library/ostream.md)\
[\<sstream>](../standard-library/sstream.md)\
[\<streambuf>](../standard-library/streambuf.md)\
[\<strstream>](../standard-library/strstream.md)

Die einfachste Verwendung von Iostreams erfordert nur, dass Sie den-Header einschließen [\<iostream>](../standard-library/iostream.md) . Dann können Sie Werte aus [cin](../standard-library/iostream.md#cin) oder [wcin](../standard-library/iostream.md#wcin) extrahieren, um die Standardeingabe zu lesen. Die Regeln, die Sie dafür befolgen müssen, finden Sie in der Beschreibung der [basic_istream-Klasse](../standard-library/basic-istream-class.md). Außerdem können Sie Werte in [cout](../standard-library/iostream.md#cout) oder [wcout](../standard-library/iostream.md#wcout) einfügen, um die Standardausgabe zu schreiben. Die Regeln, die Sie dafür befolgen müssen, finden Sie in der Beschreibung der [basic_ostream-Klasse](../standard-library/basic-ostream-class.md). Sie können die Formatsteuerung, die Extraktoren und Insertoren gemein ist, mit der [basic-ios-Klasse](../standard-library/basic-ios-class.md) verwalten. Mehrere Manipulatoren sind an der Manipulation von Formatinformationen in Form von Extraktion und Insertion von Objekten beteiligt.

Sie können die gleichen Iostreams-Vorgänge für Dateien, die Sie mit dem Namen öffnen, mithilfe der in deklarierten Klassen ausführen [\<fstream>](../standard-library/fstream.md) . Verwenden Sie die in deklarierten Klassen, um zwischen Iostreams und Objekten der Klasse [Basic_string Klasse](../standard-library/basic-string-class.md)zu konvertieren [\<sstream>](../standard-library/sstream.md) . Verwenden Sie die in deklarierten Klassen, um die gleichen Schritte mit C-Zeichen folgen durchzuführen [\<strstream>](../standard-library/strstream.md) .

Die restlichen Headers bieten Supportdienste, die nur für sehr fortgeschrittene Benutzer der iostreams-Klassen von direktem Interesse sind.

## <a name="see-also"></a>Weitere Informationen

[Übersicht über die C++-Standard Bibliothek](../standard-library/cpp-standard-library-overview.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
