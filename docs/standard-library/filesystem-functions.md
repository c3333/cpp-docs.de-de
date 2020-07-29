---
title: '&lt;filesystem&gt;-Funktionen'
ms.date: 03/27/2019
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::absolute
- FILESYSTEM/std::experimental::filesystem::canonical
- FILESYSTEM/std::experimental::filesystem::copy
- FILESYSTEM/std::experimental::filesystem::copy_file
- FILESYSTEM/std::experimental::filesystem::copy_symlink
- FILESYSTEM/std::experimental::filesystem::create_directories
- FILESYSTEM/std::experimental::filesystem::create_directory
- FILESYSTEM/std::experimental::filesystem::create_directory_symlink
- FILESYSTEM/std::experimental::filesystem::create_hard_link
- FILESYSTEM/std::experimental::filesystem::create_symlink
- FILESYSTEM/std::experimental::filesystem::current_path
- FILESYSTEM/std::experimental::filesystem::equivalent
- FILESYSTEM/std::experimental::filesystem::exists
- FILESYSTEM/std::experimental::filesystem::file_size
- FILESYSTEM/std::experimental::filesystem::hard_link_count
- FILESYSTEM/std::experimental::filesystem::hash_value
- FILESYSTEM/std::experimental::filesystem::is_block_file
- FILESYSTEM/std::experimental::filesystem::is_character_file
- FILESYSTEM/std::experimental::filesystem::is_directory
- FILESYSTEM/std::experimental::filesystem::is_empty
- FILESYSTEM/std::experimental::filesystem::is_fifo
- FILESYSTEM/std::experimental::filesystem::is_other
- FILESYSTEM/std::experimental::filesystem::is_regular_file
- FILESYSTEM/std::experimental::filesystem::is_socket
- FILESYSTEM/std::experimental::filesystem::is_symlink
- FILESYSTEM/std::experimental::filesystem::last_write_time
- FILESYSTEM/std::experimental::filesystem::permissions
- FILESYSTEM/std::experimental::filesystem::read_symlink
- FILESYSTEM/std::experimental::filesystem::remove
- FILESYSTEM/std::experimental::filesystem::remove_all
- FILESYSTEM/std::experimental::filesystem::rename
- FILESYSTEM/std::experimental::filesystem::resize_file
- FILESYSTEM/std::experimental::filesystem::space
- FILESYSTEM/std::experimental::filesystem::status
- FILESYSTEM/std::experimental::filesystem::status_known
- FILESYSTEM/std::experimental::filesystem::swap
- FILESYSTEM/std::experimental::filesystem::symlink_status
- FILESYSTEM/std::experimental::filesystem::system_complete
- FILESYSTEM/std::experimental::filesystem::temp_directory_path
- FILESYSTEM/std::experimental::filesystem::u8path
ms.assetid: be3cb821-4728-4d47-ab78-858fa8aa5045
helpviewer_keywords:
- std::experimental::filesystem::absolute
- std::experimental::filesystem::canonical
- std::experimental::filesystem::copy
- std::experimental::filesystem::copy_file
- std::experimental::filesystem::copy_symlink
- std::experimental::filesystem::create_directories
- std::experimental::filesystem::create_directory
- std::experimental::filesystem::create_directory_symlink
- std::experimental::filesystem::create_hard_link
- std::experimental::filesystem::create_symlink
- std::experimental::filesystem::current_path
- std::experimental::filesystem::equivalent
- std::experimental::filesystem::exists
- std::experimental::filesystem::file_size
- std::experimental::filesystem::hard_link_count
- std::experimental::filesystem::hash_value
- std::experimental::filesystem::is_block_file
- std::experimental::filesystem::is_character_file
- std::experimental::filesystem::is_directory
- std::experimental::filesystem::is_empty
- std::experimental::filesystem::is_fifo
- std::experimental::filesystem::is_other
- std::experimental::filesystem::is_regular_file
- std::experimental::filesystem::is_socket
- std::experimental::filesystem::is_symlink
- std::experimental::filesystem::last_write_time
- std::experimental::filesystem::permissions
- std::experimental::filesystem::read_symlink
- std::experimental::filesystem::remove
- std::experimental::filesystem::remove_all
- std::experimental::filesystem::rename
- std::experimental::filesystem::resize_file
- std::experimental::filesystem::space
- std::experimental::filesystem::status
- std::experimental::filesystem::status_known
- std::experimental::filesystem::swap
- std::experimental::filesystem::symlink_status
- std::experimental::filesystem::system_complete
- std::experimental::filesystem::temp_directory_path
- std::experimental::filesystem::u8path
ms.openlocfilehash: c637c4893a13df577fd6c083c8a4f2380c9c4cad
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219156"
---
# <a name="ltfilesystemgt-functions"></a>&lt;filesystem&gt;-Funktionen

Diese kostenlosen Funktionen im- [\<filesystem>](../standard-library/filesystem.md) Header führen Änderungen und Abfrage Vorgänge für Pfade, Dateien, Symlinks, Verzeichnisse und Volumes durch. Weitere Informationen und Codebeispiele finden Sie unter [Dateisystemnavigation (C++)](../standard-library/file-system-navigation.md).

## <a name="absolute"></a><a name="absolute"></a>UT

```cpp
path absolute(const path& pval, const path& base = current_path());
```

Die-Funktion gibt den absoluten Pfadnamen zurück, der dem *PVal* relativ zum Pfadnamen entspricht `base` :

1. , Wenn `pval.has_root_name() && pval.has_root_directory()` die Funktion " *PVal*" zurückgibt.

1. , Wenn `pval.has_root_name() && !pval.has_root_directory()` die Funktion zurückgibt `pval.root_name()`  /  `absolute(base).root_directory()`  /  `absolute(base).relative_path()`  /  `pval.relative_path()` .

1. , Wenn `!pval.has_root_name() && pval.has_root_directory()` die Funktion " `absolute(base).root_name()`  /  *PVal*" zurückgibt.

1. , Wenn `!pval.has_root_name() && !pval.has_root_directory()` die Funktion " `absolute(base)`  /  *PVal*" zurückgibt.

## <a name="begin"></a><a name="begin"></a>beginnen

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

Beide Funktionen geben *ITER*zurück.

## <a name="canonical"></a><a name="canonical"></a>Kan

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

Die Funktionen bilden einen absoluten Pfadnamen `pabs = absolute(pval, base)` (oder `pabs = absolute(pval)` für die Überladung ohne Basisparameter) und reduzieren Sie dann in der folgenden Schrittfolge auf eine kanonische Form:

1. Jede Pfadkomponente `X` , für `is_symlink(X)` die **`true`** durch ersetzt wird `read_symlink(X)` .

1. Jede Pfadkomponente `.` (Punkt ist das aktuelle Verzeichnis, das von vorherigen Pfad Komponenten festgelegt wurde) wird entfernt.

1. Jedes Paar von Pfad Komponenten `X` / `..` (Punkt Punkt ist das übergeordnete Verzeichnis, das von vorherigen Pfad Komponenten festgelegt wurde) wird entfernt.

Die Funktion gibt dann zurück `pabs` .

## <a name="copy"></a><a name="copy"></a>skopie

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Die Funktionen, die möglicherweise eine oder mehrere Dateien *von* *bis zu unter Kontrolle* von *OPTS*kopieren oder verknüpfen, die als `copy_options::none` für die über Ladungen ohne *OPTS* -Parameter übernommen werden. *OPTS* müssen höchstens einen der folgenden Zeichen enthalten:

- `skip_existing`, `overwrite_existing` oder `update_existing`

- `copy_symlinks` oder `skip_symlinks`

- `directories_only`, `create_symlinks` oder `create_hard_links`

Die Funktionen bestimmen zunächst die file_status Werte `f` für *from* und `t` for *to*:

- Wenn `opts & (copy_options::create_symlinks | copy_options::skip_symlinks)` , durch Aufrufen von`symlink_status`

- andernfalls durch Aufrufen von`status`

- Andernfalls wird ein Fehler gemeldet.

Wenn `!exists(f) || equivalent(f, t) || is_other(f) || is_other(t) || is_directory(f)&& is_regular_file(t)` , dann melden Sie einen Fehler (und führen nichts anderes aus).

Andernfalls `is_symlink(f)` :

- Wenn `options & copy_options::skip_symlinks` , dann wird keine Aktion durchführen.

- Andernfalls `!exists(t)&& options & copy_options::copy_symlinks` `copy_symlink(from, to, opts)` .

- Andernfalls wird ein Fehler gemeldet.

Andernfalls `is_regular_file(f)` :

- Wenn `opts & copy_options::directories_only` , dann wird keine Aktion durchführen.

- Andernfalls `opts & copy_options::create_symlinks` `create_symlink(to, from)` .

- Andernfalls `opts & copy_options::create_hard_links` `create_hard_link(to, from)` .

- Andernfalls `is_directory(f)` `copy_file(from, to`  /  `from.filename(), opts)` .

- Andernfalls `copy_file(from, to, opts)`.

Andernfalls `is_directory(f) && (opts & copy_options::recursive || !opts)` :

```cpp
if (!exists(t))
{  // copy directory contents recursively
    create_directory(to, from, ec);

    for (directory_iterator next(from), end; ec == error_code() && next != end; ++next)
    {
        copy(next->path(), to / next->path().filename(), opts, ec);
    }
}
```

Andernfalls keinen weiteren Schritt ausführen.

## <a name="copy_file"></a><a name="copy_file"></a>copy_file

```cpp
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Die-Funktionen kopieren möglicherweise die Datei *from* unter von *in in* die Kontrolle von *OPTS*, die als `copy_options::none` für die über Ladungen ohne *OPTS* -Parameter übernommen wird. *OPTS* müssen höchstens einen der-,-oder-Zeichen enthalten `skip_existing` `overwrite_existing` `update_existing` .

Wenn `exists(to) && !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options::update_existing))` der Wert ist, melden Sie sich als Fehler an, dass die Datei bereits vorhanden ist.

Andernfalls sollten Sie `!exists(to) || opts & copy_options::overwrite_existing || opts & copy_options::update_existing&& last_write_time(to) < last_write_time(from) || !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options:update_existing))` versuchen, den Inhalt und die Attribute der Datei *aus* in die Datei *zu*kopieren. Wenn beim Kopierversuch ein Fehler auftritt, diesen dann melden.

Die Funktionen geben zurück **`true`** , wenn die Kopie versucht wird und erfolgreich ist, andernfalls **`false`** .

## <a name="copy_symlink"></a><a name="copy_symlink"></a>copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

Wenn `is_directory(from)` , ruft die Funktion auf `create_directory_symlink(from, to)` . Andernfalls wird aufgerufen `create_symlink(from, to)` .

## <a name="create_directories"></a><a name="create_directories"></a>create_directories

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

Für einen Pfadnamen wie z. \/ b. b \/ c erstellt die Funktion die Verzeichnisse a und \/ b nach Bedarf, damit das Verzeichnis a \/ b c nach Bedarf erstellt werden kann \/ . Sie wird nur zurückgegeben, **`true`** Wenn das Verzeichnis " *PVal*" tatsächlich erstellt wird.

## <a name="create_directory"></a><a name="create_directory"></a>create_directory

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

Die-Funktion erstellt das Verzeichnis " *PVal* " nach Bedarf. Sie gibt nur dann "true" zurück, wenn das Verzeichnis " *PVal*" tatsächlich erstellt wird. in diesem Fall werden Berechtigungen aus der vorhandenen Datei " *attr*" kopiert, oder `perms::all` für die über Ladungen ohne *attr* -Parameter wird verwendet.

## <a name="create_directory_symlink"></a><a name="create_directory_symlink"></a>create_directory_symlink

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

Die-Funktion erstellt eine Verknüpfung als Symlink *zum Verzeichnis.*

## <a name="create_hard_link"></a><a name="create_hard_link"></a>create_hard_link

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

Die Funktion erstellt eine Verknüpfung als festen Link zum Verzeichnis oder *zu*der Datei.

## <a name="create_symlink"></a><a name="create_symlink"></a>create_symlink

```cpp
void create_symlink(const path& to, const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

Die-Funktion erstellt eine *Verknüpfung* als Symlink zu der Datei *mit*.

## <a name="current_path"></a><a name="current_path"></a>current_path

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

Die Funktionen ohne *PVal* -Parameter geben den Pfadnamen für das aktuelle Verzeichnis zurück. Die übrigen Funktionen legen das aktuelle Verzeichnis auf " *PVal*" fest.

## <a name="end"></a><a name="end"></a>Schließlich

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

Die erste Funktion gibt zurück, `directory_iterator()` und die zweite Funktion gibt zurück.`recursive_directory_iterator()`

## <a name="equivalent"></a>Äquivalent in <a name="equivalent"></a>

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

Die Funktionen geben **`true`** nur dann zurück, wenn *left* und *right* dieselbe Dateisystem Entität auswählen.

## <a name="exists"></a><a name="exists"></a>gebe

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

Diese erste Funktion gibt `status_known && stat.type() != file_not_found` zurück. Die zweite und dritte Funktion geben zurück `exists(status(pval))` .

## <a name="file_size"></a><a name="file_size"></a>file_size

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

Die-Funktionen geben die Größe der von *PVal*ausgewählten Datei in Bytes zurück, wenn `exists(pval) && is_regular_file(pval)` und die Dateigröße bestimmt werden kann. Andernfalls melden Sie einen Fehler und geben zurück `uintmax_t(-1)` .

## <a name="hard_link_count"></a><a name="hard_link_count"></a>hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

Die-Funktion gibt die Anzahl der festen Links für *PVal*oder \- 1 zurück, wenn ein Fehler auftritt.

## <a name="hash_value"></a><a name="hash_value"></a>hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

Die-Funktion gibt einen Hashwert für zurück `pval.native()` .

## <a name="is_block_file"></a><a name="is_block_file"></a>is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

Diese erste Funktion gibt `stat.type() == file_type::block` zurück. Die übrigen Funktionen geben zurück `is_block_file(status(pval))` .

## <a name="is_character_file"></a><a name="is_character_file"></a>is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

Diese erste Funktion gibt `stat.type() == file_type::character` zurück. Die übrigen Funktionen geben zurück `is_character_file(status(pval))` .

## <a name="is_directory"></a><a name="is_directory"></a>is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

Diese erste Funktion gibt `stat.type() == file_type::directory` zurück. Die übrigen Funktionen geben zurück `is_directory_file(status(pval))` .

## <a name="is_empty"></a><a name="is_empty"></a>is_empty

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

Wenn `is_directory(pval)` der Wert ist, gibt die Funktion zurück `directory_iterator(pval) == directory_iterator()` ; andernfalls wird zurückgegeben `file_size(pval) == 0` .

## <a name="is_fifo"></a><a name="is_fifo"></a>is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

Diese erste Funktion gibt `stat.type() == file_type::fifo` zurück. Die übrigen Funktionen geben zurück `is_fifo(status(pval))` .

## <a name="is_other"></a><a name="is_other"></a>is_other

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

Diese erste Funktion gibt `stat.type() == file_type::other` zurück. Die übrigen Funktionen geben zurück `is_other(status(pval))` .

## <a name="is_regular_file"></a><a name="is_regular_file"></a>is_regular_file

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

Diese erste Funktion gibt `stat.type() == file_type::regular` zurück. Die übrigen Funktionen geben zurück `is_regular_file(status(pval))` .

## <a name="is_socket"></a><a name="is_socket"></a>is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

Diese erste Funktion gibt `stat.type() == file_type::socket` zurück. Die übrigen Funktionen geben zurück `is_socket(status(pval))` .

## <a name="is_symlink"></a><a name="is_symlink"></a>is_symlink

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

Diese erste Funktion gibt `stat.type() == file_type::symlink` zurück. Die übrigen Funktionen geben zurück `is_symlink(status(pval))` .

## <a name="last_write_time"></a><a name="last_write_time"></a>last_write_time

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

Die ersten beiden Funktionen geben den Zeitpunkt der letzten Datenänderung für *PVal*zurück, oder, `file_time_type(-1)` Wenn ein Fehler auftritt. Die letzten beiden Funktionen haben den Zeitpunkt der letzten Datenänderung für *PVal* auf *new_time*festgelegt.

## <a name="permissions"></a><a name="permissions"></a>Griff

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

Die-Funktionen legen die Berechtigungen für den von *PVal* ausgewählten Pfadnamen auf `mask & perms::mask` unter Kontrolle von fest `perms & (perms::add_perms | perms::remove_perms)` . *Mask* darf höchstens einen von und enthalten `perms::add_perms` `perms::remove_perms` .

Wenn `mask & perms::add_perms` der Wert ist, legen die Funktionen die Berechtigungen auf fest `status(pval).permissions() | mask & perms::mask` . Andernfalls `mask & perms::remove_perms` legen die Funktionen die Berechtigungen auf fest `status(pval).permissions() & ~(mask & perms::mask)` . Andernfalls legen die Funktionen die Berechtigungen auf fest `mask & perms::mask` .

## <a name="proximate"></a><a name="proximate"></a>Gerät in

```cpp
path proximate(const path& p, error_code& ec);
path proximate(const path& p, const path& base = current_path());
path proximate(const path& p, const path& base, error_code& ec);
```

## <a name="read_symlink"></a><a name="read_symlink"></a>read_symlink

```cpp
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```

Die Funktionen melden einen Fehler und geben zurück, `path()` Wenn `!is_symlink(pval)` . Andernfalls geben die Funktionen ein Objekt vom Typ `path` zurück, das die symbolische Verknüpfung enthält.

## <a name="relative"></a><a name="relative"></a>verwandt

```cpp
path relative(const path& p, error_code& ec);
path relative(const path& p, const path& base = current_path());
path relative(const path& p, const path& base, error_code& ec);
```

## <a name="remove"></a><a name="remove"></a>aufgeh

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

Die Funktionen geben **`true`** nur dann zurück, wenn `exists(symlink_status(pval))` die Datei erfolgreich entfernt wurde. Ein symlink wird selbst entfernt, nicht die Datei, die er auswählt.

## <a name="remove_all"></a><a name="remove_all"></a>remove_all

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

Wenn *PVal* ein Verzeichnis ist, entfernen die Funktionen alle Verzeichniseinträge rekursiv und dann den Eintrag selbst. Andernfalls ruft der Functions-Befehl auf `remove` . Sie geben die Anzahl aller Elemente zurück, die erfolgreich entfernt wurden.

## <a name="rename"></a><a name="rename"></a>benen

```cpp
void rename(const path& from, const path& to);
void rename(const path& from, const path& to, error_code& ec) noexcept;
```

Die Funktionen benennen *von* in in *um*. Ein symlink wurde umbenannt, nicht die Datei, die er wählt.

## <a name="resize_file"></a><a name="resize_file"></a>resize_file

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

Die Funktionen ändern die Größe einer Datei, sodass`file_size(pval) == size`

## <a name="space"></a><a name="space"></a>BRaum

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

Die Funktion gibt Informationen über das von *PVal*ausgewählte Volume in einer Struktur vom Typ zurück `space_info` . Die-Struktur enthält `uintmax_t(-1)` für einen beliebigen Wert, der nicht bestimmt werden kann.

## <a name="status"></a><a name="status"></a>Stands

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

Die-Funktionen geben den Pfadnamen Status, den Dateityp und die Berechtigungen zurück, die mit dem *PVal*verknüpft sind. Ein symlink ist selbst nicht getestet, aber die Datei, die er wählt.

## <a name="status_known"></a><a name="status_known"></a>status_known

```cpp
bool status_known(file_status stat) noexcept;
```

Die Funktion gibt zurück.`stat.type() != file_type::none`

## <a name="swap"></a><a name="swap"></a>Wechsel

```cpp
void swap(path& left, path& right) noexcept;
```

Die-Funktion tauscht den Inhalt von *Links* und *Rechts*aus.

## <a name="symlink_status"></a><a name="symlink_status"></a>symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, error_code& ec) noexcept;
```

Die-Funktionen geben den Pfadname Symlink-Status, den Dateityp und die Berechtigungen zurück, die mit dem *PVal*verknüpft sind. Die-Funktionen Verhalten sich genauso wie, `status(pval)` mit der Ausnahme, dass ein symlink selbst getestet wird und nicht die Datei, die er wählt.

## <a name="system_complete"></a><a name="system_complete"></a>system_complete

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

Die Funktionen geben einen absoluten Pfadnamen zurück, der bei Bedarf das aktuelle Verzeichnis berücksichtigt, das seinem Stammnamen zugeordnet ist. \(Für POSIX geben die Funktionen zurück `absolute(pval)` .\)

## <a name="temp_directory_path"></a><a name="temp_directory_path"></a>temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

Die Funktionen geben einen Pfadnamen für ein Verzeichnis zurück, das für die Aufnahme temporärer Dateien geeignet ist.

## <a name="u8path"></a><a name="u8path"></a>u8path

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

Die erste Funktion verhält sich wie `path(source)` , und die zweite Funktion verhält sich genauso wie `path(first, last)` , mit der Ausnahme, dass die ausgewählte Quelle in jedem Fall als Sequenz von Char-Elementen, die als UTF-8 codiert sind, wie das Dateisystem, übernommen wird.

## <a name="weakly_canonical"></a><a name="weakly_canonical"></a>weakly_canonical

```cpp
path weakly_canonical(const path& p);
path weakly_canonical(const path& p, error_code& ec);
```
