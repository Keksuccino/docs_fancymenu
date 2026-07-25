---
title: Переменные
description: Как создавать и использовать переменные.
---
# Переменные в FancyMenu

Переменные хранят текстовые значения, которые макеты, действия, плейсхолдеры, требования, слушатели, планировщики и Custom GUI могут использовать повторно.

## Создание переменных

Чтобы создать переменную в FancyMenu:

1. Убедитесь, что вы сейчас не находитесь в редакторе макета. 
2. Нажмите на строку меню в верхней части экрана.
3. Перейдите в **Customization -> Variables -> Manage Variables**.
4. В открывшемся окне "Manage Variables" нажмите кнопку **Add Variable**.
5. Введите имя новой переменной и нажмите **OK**.

Вот и всё! Ваша переменная готова к использованию. Вы увидите её в списке в окне "Manage Variables".

Окно Manage Variables поддерживает контекстное меню по правому клику, навигацию с клавиатуры, копирование/вставку, отмену/повтор, поиск по вводу, удаление клавишей **Delete** и сохранение через **Ctrl/Command + S**.

## Задание значений переменных

Пустая переменная сама по себе не очень полезна. Чтобы переменные работали, нужно записывать в них данные. В FancyMenu это называется "задать значение переменной". 

Есть два основных способа задать значение переменной:

1. В окне "Manage Variables" найдите переменную в списке, нажмите на неё, а затем нажмите **Set Value**. Введите данные, которые хотите сохранить.

2. При настройке меню используйте действие [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable) для элемента [Button](./elements#button), [Slider](./elements#slider) или [Ticker](./elements#ticker).

Например, создайте переменную с именем `clicks` и добавьте к кнопке действие [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable):

```
clicks:{"placeholder":"calc","values":{"expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

Вот как это работает:
1. Плейсхолдер [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) получает текущее значение переменной `clicks`.
2. Плейсхолдер [**Calculator**](./placeholders#calculator-calc) берёт это значение и прибавляет к нему 1.
3. Результат сохраняется обратно в `clicks` с помощью действия [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable).

Таким образом, при каждом нажатии кнопки переменная `clicks` будет увеличиваться на 1, фактически подсчитывая общее количество нажатий.

## Использование переменных

Теперь, когда у вас есть переменные с данными, вы можете использовать эти данные в разных частях настройки меню:

* [**Loading Requirements**](./conditions): Проверяйте значение переменной, чтобы управлять тем, когда элементы появляются. Например, показывайте элемент, когда `clicks` больше 5, сочетая [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) с плейсхолдером [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable).

* **Плейсхолдеры**: Вставляйте переменную в текст с помощью плейсхолдера [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable), например `{"placeholder":"getvariable","values":{"name":"clicks"}}`.

* **Вложенные плейсхолдеры**: Вы можете использовать плейсхолдер [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) внутри плейсхолдера [**Calculator**](./placeholders#calculator-calc).

* **Действия**: Переменные могут создавать динамическое поведение:
  - Используйте оператор **IF** в [скрипте действий](./action-scripts#what-are-statements) вместе с [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) и плейсхолдером [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable).
  - Сочетайте плейсхолдер [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) с [**Copy Text to Clipboard**](./action-scripts#copy-text-to-clipboard-copytoclipboard).
  - Используйте переменные в [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui), чтобы выбрать экран из сохранённого прогресса или настроек.

## Примеры переменных

Вот несколько примеров, которые помогут вам придумать собственное использование переменных:

1. **Высокий счёт**: Создайте переменную `highscore` и кнопку, которая устанавливает её в текущий счёт игрока, если он выше существующего значения. Отображайте его с помощью плейсхолдера [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable).

2. **Выбор сложности**: Создайте переменные для разных уровней сложности игры, например `easy`, `medium` и `hard`. Используйте кнопки, чтобы задавать переменную сложности, и показывайте/скрывайте элементы в зависимости от выбранной сложности.

3. **Прогресс обучения**: Добавьте переменные для отслеживания прогресса игрока в обучении, например `tutorial_step`. Увеличивайте значение переменной по мере прохождения каждого шага и используйте требования загрузки, чтобы постепенно открывать всё больше элементов меню.

## Сохранение, область видимости и хранение

Переменные общие для текущего экземпляра Minecraft. Они не разделяются по макету, миру, серверу или игроку.

Значения сохраняются сразу в `<game-directory>/config/fancymenu/user_variables.db` и переживают перезапуск игры.

- **Reset on Launch** очищает эту переменную при следующем запуске игры.
- [**Clear All Variables**](./action-scripts#clear-all-variables-fm-variable-clear_variables) удаляет все сохранённые значения переменных.
- Имена чувствительны к регистру. Используйте простые, уникальные имена, например `tutorial_step`.

Плейсхолдер [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) возвращает `0`, если указанная переменная не существует или если её сохранённое значение пустое. Этот запасной вариант важен при сравнениях и выражениях калькулятора.

Действие [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable) использует формат `variable_name:variable_value` и разделяет строку по первому двоеточию, поэтому значение может содержать больше одного двоеточия.

Не храните пароли, токены и другие секреты в переменных FancyMenu. Это читаемые конфигурационные данные.
