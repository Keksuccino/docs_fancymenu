---
title: Змінні
description: Як створювати та використовувати змінні.
sourceBlobSha: dcd1512bc7f20f3ab535205f24a67c6489231e11
---

# Змінні у FancyMenu

Змінні зберігають текстові значення, які можуть повторно використовувати макети, дії, заповнювачі, вимоги, слухачі, планувальники та Custom GUI.

## Створення змінних

Щоб створити змінну у FancyMenu:

1. Переконайтеся, що ви зараз не перебуваєте в редакторі макетів. 
2. Натисніть меню у верхній частині екрана.
3. Перейдіть до **Customization -> Variables -> Manage Variables**.
4. У вікні "Manage Variables", що відкриється, натисніть кнопку **Add Variable**.
5. Введіть назву нової змінної та натисніть **OK**.

Ось і все! Ваша змінна готова до використання. Вона відображатиметься у вікні "Manage Variables".

Вікно Manage Variables підтримує контекстне меню, яке відкривається правою кнопкою миші, навігацію за допомогою клавіатури, копіювання й вставлення, скасування та повторення дій, пошук під час введення, клавішу **Delete** для видалення, а також **Ctrl/Command + S** для збереження.

## Встановлення значень змінних

Порожня змінна сама по собі не надто корисна. Щоб змінні працювали для вас, потрібно помістити в них дані. У FancyMenu це називається "встановленням значення змінної". 

Є два основні способи встановити значення змінної:

1. У вікні "Manage Variables" знайдіть змінну у списку, натисніть на неї, а потім натисніть **Set Value**. Введіть дані, які хочете зберегти.

2. Під час налаштування меню використовуйте дію [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable) для елемента [Button](./elements#button), [Slider](./elements#slider) або [Ticker](./elements#ticker).

Наприклад, створіть змінну з назвою `clicks` і додайте до кнопки дію [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable):

```
clicks:{"placeholder":"calc","values":{"expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

Ось як це працює:
1. Заповнювач [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) отримує поточне значення змінної `clicks`.
2. Заповнювач [**Calculator**](./placeholders#calculator-calc) бере це значення та додає до нього 1.
3. Результат знову зберігається у `clicks` за допомогою дії [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable).

Тож щоразу, коли натискають кнопку, значення змінної `clicks` збільшуватиметься на 1, фактично підраховуючи загальну кількість натискань.

## Використання змінних

Тепер, коли у вас є змінні, що містять дані, ви можете використовувати ці дані в різних частинах налаштування меню:

* [**Вимоги завантаження**](./conditions): Перевіряйте значення змінної, щоб керувати моментом появи елементів. Наприклад, показуйте елемент, коли `clicks` більше за 5, поєднавши [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) із заповнювачем [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable).

* **Заповнювачі**: Вставляйте змінну в текст за допомогою заповнювача [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable), наприклад `{"placeholder":"getvariable","values":{"name":"clicks"}}`.

* **Вкладені заповнювачі**: Ви можете використовувати заповнювач [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) усередині заповнювача [**Calculator**](./placeholders#calculator-calc).

* **Дії**: Змінні можуть створювати динамічну поведінку:
  - Використовуйте оператор **IF** у [скрипті дій](./action-scripts#what-are-statements) разом із [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) та заповнювачем [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable).
  - Поєднуйте заповнювач [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) із дією [**Copy Text to Clipboard**](./action-scripts#copy-text-to-clipboard-copytoclipboard).
  - Використовуйте змінні в дії [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui), щоб вибирати екран на основі збереженого прогресу або налаштувань.

## Приклади змінних

Ось кілька прикладів, які можуть надихнути вас на власні способи використання змінних:

1. **Рекорд**: Створіть змінну `highscore` і кнопку, яка встановлює для неї поточний рахунок гравця, якщо він вищий за наявне значення. Відображайте його за допомогою заповнювача [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable).

2. **Вибір рівня складності**: Створіть змінні для різних рівнів складності гри, наприклад `easy`, `medium` і `hard`. Використовуйте кнопки, щоб встановлювати змінну складності, і показуйте або приховуйте елементи залежно від вибраного рівня.

3. **Прогрес навчання**: Додайте змінні для відстеження прогресу гравця в навчанні, наприклад `tutorial_step`. Збільшуйте значення змінної після завершення кожного кроку та використовуйте вимоги завантаження, щоб поступово відкривати більше елементів меню.

## Збереження, область дії та сховище

Змінні спільні для поточного екземпляра Minecraft. Вони не розділяються за макетами, світами, серверами чи гравцями.

Значення зберігаються негайно у `<game-directory>/config/fancymenu/user_variables.db` і не втрачаються після перезапуску.

- **Reset on Launch** очищає цю змінну під час наступного запуску гри.
- [**Clear All Variables**](./action-scripts#clear-all-variables-fm-variable-clear_variables) видаляє всі збережені значення змінних.
- Імена чутливі до регістру. Використовуйте прості унікальні імена, наприклад `tutorial_step`.

Заповнювач [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) повертає `0`, якщо змінної із вказаним іменем не існує або якщо її збережене значення порожнє. Це значення за замовчуванням важливе під час порівнянь і обчислень у виразах калькулятора.

Дія [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable) використовує формат `variable_name:variable_value` і розділяє його за першою двокрапкою, тому значення може містити додаткові двокрапки.

Не зберігайте паролі, токени чи інші секретні дані у змінних FancyMenu. Це доступні для читання конфігураційні дані.
