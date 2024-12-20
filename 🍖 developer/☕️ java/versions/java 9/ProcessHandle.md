[[🧁 Java9]]

### `java.lang.ProcessHandle`

`ProcessHandle` представляет собой дескриптор процесса. Он предоставляет API для управления и получения информации о процессах, запущенных на вашей системе. Некоторые ключевые методы включают:

- **`ProcessHandle.current()`**: возвращает дескриптор текущего процесса.
- **`ProcessHandle.allProcesses()`**: возвращает поток всех процессов, запущенных на системе.
- **`ProcessHandle.children()`**: возвращает поток дескрипторов дочерних процессов.
- **`ProcessHandle.parent()`**: возвращает `Optional<ProcessHandle>`, представляющий родительский процесс, если он существует.
- **`ProcessHandle.destroy()`**: пытается завершить процесс.
- **`ProcessHandle.isAlive()`**: проверяет, активен ли процесс.
- **`ProcessHandle.Info()`**: возвращает информацию о процессе в виде экземпляра вложенного класса `ProcessHandle.Info`.

### `java.lang.ProcessHandle.Info`

`ProcessHandle.Info` - это вложенный интерфейс в `ProcessHandle`, который используется для получения информации о процессе. Он предоставляет методы для доступа к различным атрибутам процесса:

- **`command()`**: возвращает `Optional<String>`, содержащий команду, использованную для запуска процесса.
- **`arguments()`**: возвращает `Optional<String[]>`, содержащий аргументы, переданные процессу.
- **`startInstant()`**: возвращает `Optional<Instant>`, представляющий время начала процесса.
- **`totalCpuDuration()`**: возвращает `Optional<Duration>`, представляющий общее время использования CPU процессом.
- **`user()`**: возвращает `Optional<String>`, представляющий имя пользователя, запустившего процесс.

Пример использования:
`ProcessHandle currentProcess = ProcessHandle.current(); ProcessHandle.Info processInfo = currentProcess.info();  System.out.println("Process ID: " + currentProcess.pid()); System.out.println("Command: " + processInfo.command().orElse("Unknown")); System.out.println("Arguments: " + Arrays.toString(processInfo.arguments().orElse(new String[]{}))); System.out.println("Start time: " + processInfo.startInstant().orElse(Instant.now())); System.out.println("CPU time: " + processInfo.totalCpuDuration().orElse(Duration.ZERO)); System.out.println("User: " + processInfo.user().orElse("Unknown"));`

Этот код выводит информацию о текущем процессе, включая его ID, команду, аргументы, время начала, общее время использования CPU и пользователя.