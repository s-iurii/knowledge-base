[[🪁 Java11]]

**writeString():** записывает содержимое в файл.
```shell
jshell>Files.writeString(Path.of(example.txt), "GeeksForGeeks!");
```

**readString():** используется для чтения содержимого файла.

jshell>Файлы.readString(Путь.к(примеру.txt));
**Вывод:** «GeeksForGeeks!»

**isSameFile():** этот метод используется для определения того, указывают ли два пути на один и тот же файл или нет.

jshell>Files.isSameFile(Path.of("example1.txt"), Path.of("example1.txt"));
 **Вывод:** true
jshell>Файлы.isSameFile(Путь.из("example2.txt"), Путь.из("example1.txt"));
**Вывод:** ложь



