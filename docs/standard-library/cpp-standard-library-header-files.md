---
title: Header Dateien der C++-Standardbibliothek
ms.date: 07/12/2019
helpviewer_keywords:
- header files, C++ Standard Library
- C++ Standard Library, header files
ms.assetid: e7bf497a-0f63-48d0-9b54-cb0eef4073c4
ms.openlocfilehash: 207e7b7d2d689d3912399e3a867102ee893e003a
ms.sourcegitcommit: 1a8fac06478da8bee1f6d70e25afbad94144af1a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2020
ms.locfileid: "84226043"
---
# <a name="c-standard-library-header-files"></a>Header Dateien der C++-Standardbibliothek

Header Dateien für die C++-Standardbibliothek und-Erweiterungen nach Kategorie.

## <a name="headers-by-category"></a>Header nach Kategorie

::: moniker range=">=vs-2017"

| Kategorie | Header |
| - | - |
| [Algorithmen](../cpp/algorithms-modern-cpp.md) | [\<algorithm>](algorithm.md), [\<cstdlib>](cstdlib.md), [\<numeric>](numeric.md) |
| Atomarische Vorgänge |  [\<atomic>](atomic.md)<sup>11:</sup> |
| Wrapper für die C-Bibliothek | [\<cassert>](cassert.md), [\<ccomplex>](ccomplex.md) <sup>11 a</sup>b, [\<cctype>](cctype.md) , [\<cerrno>](cerrno.md) , [\<cfenv>](cfenv.md) <sup>11</sup>, [\<cfloat>](cfloat.md) , [\<cinttypes>](cinttypes.md) <sup>11</sup>, [\<ciso646>](ciso646.md) <sup>b</sup>, [\<climits>](climits.md) , [\<clocale>](clocale.md) , [\<cmath>](cmath.md) , [\<csetjmp>](csetjmp.md) , [\<csignal>](csignal.md) , [\<cstdalign>](cstdalign.md) <sup>11 a b</sup>, [\<cstdarg>](cstdarg.md) , [\<cstdbool>](cstdbool.md) <sup>11 a b</sup>, [\<cstddef>](cstddef.md) , [\<cstdint>](cstdint.md) <sup>11</sup>, [\<cstdio>](cstdio.md) , [\<cstdlib>](cstdlib.md) , [\<cstring>](cstring.md) , [\<ctgmath>](ctgmath.md) <sup>11 a b</sup>, [\<ctime>](ctime.md) , [\<cuchar>](cuchar.md) <sup>11</sup>, [\<cwchar>](cwchar.md) ,[\<cwctype>](cwctype.md) |
| Konzepte | \<concepts><sup>20</sup> |
| [Container](../cpp/containers-modern-cpp.md) | |
| Sequenz Container | [\<array>](array.md)<sup>11</sup>, [\<deque>](deque.md) , [\<forward_list>](forward-list.md) <sup>11</sup>, [\<list>](list.md) ,[\<vector>](vector.md) |
| Geordnete assoziative Container| [\<map>](map.md), [\<set>](set.md) |
| Ungeordnete assoziative Container | [\<unordered_map>](unordered-map.md)<sup>11</sup>, [\<unordered_set>](unordered-set.md) <sup>11</sup> |
| Container Adapter | [\<queue>](queue.md), [\<stack>](stack.md) |
| Container Sichten | [\<span>](span.md)<sup>20</sup> |
| [Fehler-und Ausnahmebehandlung](../cpp/errors-and-exception-handling-modern-cpp.md) | [\<cassert>](cassert.md), [\<exception>](exception.md) , [\<stdexcept>](stdexcept.md) , [\<system_error>](system-error.md) <sup>11</sup> |
| Allgemeine Hilfsprogramme | \<any><sup>17</sup>, [\<bitset>](bitset.md) , \<charconv> <sup>17</sup>, [\<cstdlib>](cstdlib.md) , \<execution> <sup>17</sup>, [\<functional>](functional.md) , [\<memory>](memory.md) , \<memory_resource> <sup>17</sup>, \<optional> <sup>17</sup>, 11 [\<ratio>](ratio.md) <sup>11</sup> [\<scoped_allocator>](scoped-allocator.md) <sup>11</sup> [\<tuple>](tuple.md) <sup>11</sup> [\<type_traits>](type-traits.md) <sup>11</sup> [\<typeindex>](typeindex.md) <sup>11</sup> [\<utility>](utility.md) \<variant> <sup>17</sup> , 11, 11, 11, 11, 17 |
| [E/a und Formatierung](../text/string-and-i-o-formatting-modern-cpp.md) | [\<cinttypes>](cinttypes.md)<sup>11</sup>, [\<cstdio>](cstdio.md) , [\<filesystem>](filesystem.md) <sup>17</sup>, [\<fstream>](fstream.md) , [\<iomanip>](iomanip.md) , [\<ios>](ios.md) , [\<iosfwd>](iosfwd.md) , [\<iostream>](iostream.md) , [\<istream>](istream.md) , [\<ostream>](ostream.md) , [\<sstream>](sstream.md) , [\<streambuf>](streambuf.md) , [\<strstream>](strstream.md) <sup>c</sup>, \<syncstream> <sup>20</sup> |
| Iterators | [\<iterator>](iterator.md) |
| Sprachunterstützung | [\<cfloat>](cfloat.md), [\<climits>](climits.md) , [\<codecvt>](codecvt.md) <sup>11 a</sup>, \<compare> <sup>20</sup>, \<contract> <sup>20</sup>, \<coroutine> <sup>20</sup>, [\<csetjmp>](csetjmp.md) , [\<csignal>](csignal.md) , [\<cstdarg>](cstdarg.md) , [\<cstddef>](cstddef.md) , [\<cstdint>](cstdint.md) <sup>11</sup>, [\<cstdlib>](cstdlib.md) , [\<exception>](exception.md) , [\<initializer_list>](initializer-list.md) <sup>11</sup>, [\<limits>](limits.md) , [\<new>](new.md) , [\<typeinfo>](typeinfo.md) , \<version> <sup>20</sup> |
| Lokalisierung | [\<clocale>](clocale.md), [\<codecvt>](codecvt.md) <sup>11 a</sup>, [\<cvt/wbuffer>](cvt-wbuffer.md) , [\<cvt/wstring>](cvt-wstring.md) ,[\<locale>](locale.md) |
| Math und Numerics | \<bit><sup>20</sup>, [\<cfenv>](cfenv.md) <sup>11</sup>, [\<cmath>](cmath.md) , [\<complex>](complex.md) , [\<cstdlib>](cstdlib.md) , [\<limits>](limits.md) , [\<numeric>](numeric.md) , [\<random>](random.md) <sup>11</sup>, [\<ratio>](ratio.md) <sup>11</sup>,[\<valarray>](valarray.md) |
| [Speicherverwaltung](../cpp/smart-pointers-modern-cpp.md) | [\<allocators>](allocators-header.md), [\<memory>](memory.md) , \<memory_resource> <sup>17</sup>, [\<new>](new.md) , [\<scoped_allocator>](scoped-allocator.md) <sup>11</sup> |
| Multithreading | [\<atomic>](atomic.md)<sup>11</sup>, [\<condition_variable>](condition-variable.md) <sup>11</sup>, [\<future>](future.md) <sup>11</sup>, [\<mutex>](mutex.md) <sup>11</sup>, [\<shared_mutex>](shared-mutex.md) <sup>14</sup>, [\<thread>](thread.md) <sup>11</sup> |
| Bereiche | \<ranges><sup>20</sup> |
| Reguläre Ausdrücke | [\<regex>](regex.md)<sup>11:</sup> |
| Zeichen folgen und Zeichendaten | [\<cctype>](cctype.md), [\<cstdlib>](cstdlib.md) , [\<cstring>](cstring.md) , [\<cuchar>](cuchar.md) <sup>11</sup>, [\<cwchar>](cwchar.md) , [\<cwctype>](cwctype.md) , [\<regex>](regex.md) <sup>11</sup>, [\<string>](string.md) , [\<string_view>](string-view.md) <sup>17</sup> |
| Zeit | [\<chrono>](chrono.md)<sup>11</sup>,[\<ctime>](ctime.md) |

<sup>11</sup> wurde im c++ 11-Standard hinzugefügt. \
<sup>14</sup> hinzugefügt im c++ 14-Standard. \
<sup>17</sup> wurde im c++ 17-Standard hinzugefügt. \
<sup>20</sup> in Draft c++ 20 Standard. \
<sup>ein</sup> , der im c++ 17-Standard veraltet ist. \
<sup>b</sup> entfernt im Entwurf c++ 20 Standard. \
<sup>c</sup> veraltet im Standard c++ 98.

::: moniker-end

::: moniker range="vs-2015"

|Kategorie|Header|
|-|-|
|[Algorithmen](../cpp/algorithms-modern-cpp.md)|[\<algorithm>](algorithm.md)|
|Wrapper für die C-Bibliothek|[\<cassert>](cassert.md), [\<cctype>](cctype.md), [\<cerrno>](cerrno.md), [\<cfenv>](cfenv.md), [\<cfloat>](cfloat.md), [\<cinttypes>](cinttypes.md), [\<ciso646>](ciso646.md), [\<climits>](climits.md), [\<clocale>](clocale.md), [\<cmath>](cmath.md), [\<csetjmp>](csetjmp.md), [\<csignal>](csignal.md), [\<cstdarg>](cstdarg.md), [\<cstdbool>](cstdbool.md), [\<cstddef>](cstddef.md), [\<cstdint>](cstdint.md), [\<cstdio>](cstdio.md), [\<cstdlib>](cstdlib.md), [\<cstring>](cstring.md), [\<ctgmath>](ctgmath.md), [\<ctime>](ctime.md), [\<cwchar>](cwchar.md), [\<cwctype>](cwctype.md)|
|[Container](../cpp/containers-modern-cpp.md)||
|Sequenz Container|[\<array>](array.md), [\<deque>](deque.md), [\<forward_list>](forward-list.md), [\<list>](list.md), [\<vector>](vector.md)|
|Geordnete assoziative Container| [\<map>](map.md), [\<set>](set.md)|
|Ungeordnete assoziative Container|[\<unordered_map>](unordered-map.md), [\<unordered_set>](unordered-set.md)|
|Adaptor Container|[\<queue>](queue.md), [\<stack>](stack.md)|
|[Fehler-und Ausnahmebehandlung](../cpp/errors-and-exception-handling-modern-cpp.md)|[\<exception>](exception.md), [\<stdexcept>](stdexcept.md), [\<system_error>](system-error.md)|
|[E/a und Formatierung](../text/string-and-i-o-formatting-modern-cpp.md)|[\<filesystem>](filesystem.md), [\<fstream>](fstream.md), [\<iomanip>](iomanip.md), [\<ios>](ios.md), [\<iosfwd>](iosfwd.md), [\<iostream>](iostream.md), [\<istream>](istream.md), [\<ostream>](ostream.md), [\<sstream>](sstream.md), [\<streambuf>](streambuf.md), [\<strstream>](strstream.md)|
|Iterators|[\<iterator>](iterator.md)|
|Lokalisierung|[\<codecvt>](codecvt.md), [\<cvt/wbuffer>](cvt-wbuffer.md), [\<cvt/wstring>](cvt-wstring.md), [\<locale>](locale.md)|
|Math und Numerics|[\<complex>](complex.md), [\<limits>](limits.md), [\<numeric>](numeric.md), [\<random>](random.md), [\<ratio>](ratio.md), [\<valarray>](valarray.md)|
|[Speicherverwaltung](../cpp/smart-pointers-modern-cpp.md)|[\<allocators>](allocators-header.md), [\<memory>](memory.md), [\<new>](new.md), [\<scoped_allocator>](scoped-allocator.md)|
|Multithreading|[\<atomic>](atomic.md), [\<condition_variable>](condition-variable.md), [\<future>](future.md), [\<mutex>](mutex.md), [\<shared_mutex>](shared-mutex.md), [\<thread>](thread.md)|
|Andere Hilfsprogramme|[\<bitset>](bitset.md), [\<chrono>](chrono.md), [\<functional>](functional.md), [\<initializer_list>](initializer-list.md), [\<tuple>](tuple.md), [\<type_traits>](type-traits.md), [\<typeinfo>](typeinfo.md), [\<typeindex>](typeindex.md), [\<utility>](utility.md)|
|Zeichen folgen und Zeichendaten|[\<regex>](regex.md), [\<string>](string.md), [\<string_view>](string-view.md)

::: moniker-end

## <a name="see-also"></a>Weitere Informationen

[Verwenden von C++-Bibliotheks Headern](using-cpp-library-headers.md)\
[C++-Standardbibliothek](cpp-standard-library-reference.md)
