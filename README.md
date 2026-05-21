Автор: Поздеев Юрий Евгеньевич
Дата создания: 18.05.2026


```markdown
# AppProject – Демонстрация Git слияния и разрешения конфликтов

Этот мини-проект показывает процесс работы с Git:
- создание локального репозитория;
- работа с ветками (`feature1`, `feature2`);
- конфликт при слиянии и его разрешение в Visual Studio.

## Структура проекта
```
AppProject/
├── .git/
├── App.cs
└── README.md
```

## Начальное состояние `App.cs`
```csharp
Console.WriteLine("Initial app");
```

## Выполненные шаги

1. **Инициализация Git**  
   ```bash
   git init
   ```

2. **Добавление и коммит начальной версии**  
   ```bash
   echo Console.WriteLine("Initial app"); > App.cs
   git add App.cs
   git commit -m "Add App.cs"
   ```

3. **Ветка `feature1`**  
   - Создана от `main`  
   - Изменён `App.cs`: `Console.WriteLine("Feature 1");`  
   - Зафиксировано коммитом `"Change to Feature 1"`

4. **Ветка `feature2`**  
   - Создана от `main` (параллельно `feature1`)  
   - Изменён `App.cs`: `Console.WriteLine("Feature 2");`  
   - Зафиксировано коммитом `"Change to Feature 2"`

5. **Слияние `feature1` в `main`**  
   ```bash
   git checkout main
   git merge feature1
   ```
   Fast-forward слияние прошло без конфликтов.

6. **Слияние `feature2` в `main`**  
   ```bash
   git merge feature2
   ```
   Возник конфликт в `App.cs`, так как обе ветки изменяли одну и ту же строку.

7. **Разрешение конфликта в Visual Studio**  
   - Открыта папка проекта в VS.  
   - В Team Explorer выбран конфликтный файл → **Merge**.  
   - В инструменте слияния вручную введена итоговая строка:  
     ```csharp
     Console.WriteLine("Merged Features");
     ```  
   - Выполнен **Accept Merge** и зафиксирован коммит слияния.

## Итоговый файл `App.cs` (после слияния)
```csharp
Console.WriteLine("Merged Features");
```

## Граф коммитов (схематично)
```
*   (main) Merge feature2 (resolved)
|\
| * (feature2) Change to Feature 2
* | (main) Change to Feature 1
|/
* Add App.cs
```

## Запуск
Проект является консольным приложением .NET Framework / .NET Core (по условию — консольное приложение net framework).  
Для компиляции и запуска:
```bash
csc App.cs          # если используется компилятор csc
App.exe
# или через dotnet (если проект .NET Core/5+):
dotnet run
```
Вывод в консоли:
```
Merged Features
```

## Примечание
Этот репозиторий создан исключительно в учебных целях для демонстрации разрешения конфликтов с помощью Visual Studio Merge Tool.

