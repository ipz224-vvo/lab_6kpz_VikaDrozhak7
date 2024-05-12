# Банкомат

## Вступ

Цей проект представляє собою банківську систему, розроблену з використанням WPF (Windows Presentation Foundation) для графічного інтерфейсу користувача та ADO.NET для взаємодії з базою даних. Проект використовує ряд принципів програмування, технік рефакторингу та патернів проєктування для створення чистого, модульного та легко розширюваного коду.

## Функціонал

Цей проект включає в себе розробку банківської системи, яка надає користувачам можливість виконувати різні банківські операції:

1. **Автентифікація користувача**: Користувачі можуть вводити номер своєї картки та PIN-код для входу в систему. Ця функція реалізована в класі `MainWindow`.

2. **Перевірка балансу**: Користувачі можуть перевіряти баланс свого рахунку. Ця функція реалізована в класі `Menu`.

3. **Внесення готівки**: Користувачі можуть вносити готівку на свій рахунок. Ця функція реалізована в класі `tocount`.

4. **Виведення готівки**: Користувачі можуть знімати готівку зі свого рахунку. Ця функція реалізована в класі `withdraw`.

5. **Переказ коштів**: Користувачі можуть переказувати кошти зі свого рахунку на інший рахунок. Ця функція реалізована в класі `Transfer`.

## Процес запуску локально

1. Клонуйте цей репозиторій.
2. Відкрийте проект у Visual Studio.
3. Запустіть проект, натиснувши `Ctrl + F5`.

## Принципи програмування

Цей проект дотримується наступних принципів програмування:

1. **Принцип єдиного обов'язку (Single Responsibility Principle)**: Кожен клас в системі має лише одну відповідальність. Наприклад, клас `DatabaseHelper` відповідає лише за взаємодію з базою даних.

2. **Принцип відкритості/закритості (Open/Closed Principle)**: Система розроблена таким чином, що її можна легко розширювати без зміни існуючого коду. Наприклад, можна додати нові типи транзакцій, не змінюючи клас `AutomatedTellerMachine`.

3. **Принцип заміни Барбари Лісков (Liskov Substitution Principle)**: Система розроблена таким чином, що підтипи можуть замінювати їх базові типи без зміни коректності програми. Наприклад, `DepositCashStrategy` та `WithdrawCashStrategy` можуть замінювати `ITransactionStrategy`.

4. **Принцип розділення інтерфейсу (Interface Segregation Principle)**: Кожен клас використовує лише ті інтерфейси, які йому потрібні. Наприклад, клас `AutomatedTellerMachine` використовує інтерфейс `ITransactionStrategy`.

5. **Принцип залежності від абстракцій, а не від конкретних класів (Dependency Inversion Principle)**: Високорівневі модулі не залежать від низькорівневих модулів. Обидва типи модулів залежать від абстракцій. Наприклад, клас `AutomatedTellerMachine` залежить від абстракції `ITransactionStrategy`, а не від конкретних класів `DepositCashStrategy` та `WithdrawCashStrategy`.

## Техніки рефакторингу

Під час розробки цього проекту було використано наступні техніки рефакторингу:

1. **Видалення дублювання коду**: Було видалено дублювання коду шляхом використання методів та класів.

2. **Використання відповідних імен**: Всі класи, методи та змінні мають відповідні імена, які відображають їхню функцію.

3. **Використання винятків для обробки помилок**: Використовуються винятки для обробки помилок під час виконання операцій з базою даних.

4. **Використання інкапсуляції**: Дані класу захищені від прямого доступу ззовні, використовуючи приватні поля та властивості.

5. **Використання поліморфізму**: Використовується поліморфізм для виконання різних типів транзакцій.

## Патерни проєктування

Цей проект використовує наступні патерни проєктування:

1. **Патерн Стратегія (Strategy Pattern)**: Використовується для виконання різних типів транзакцій. Він включає в себе інтерфейс `ITransactionStrategy` та його реалізації `DepositCashStrategy` та `WithdrawCashStrategy`. Цей патерн дозволяє визначати сімейство алгоритмів, інкапсулювати кожен з них та робити їх взаємозамінними. Стратегія дозволяє алгоритм варіюватися незалежно від клієнтів, які його використовують.

2. **Патерн Спостерігач (Observer Pattern)**: Використовується для сповіщення про різні події, такі як успішна автентифікація, перевірка балансу тощо. Він включає в себе клас AutomatedTellerMachine, який генерує події. Спостерігач визначає залежність один-до-багатьох між об’єктами, так що коли один об’єкт змінює стан, всі його залежні отримують повідомлення та автоматично оновлюються.
3. **Патерн Одинак (Singleton Pattern)**: Використовується для створення єдиного екземпляра класу DatabaseHelper. Одинак гарантує, що клас має лише один екземпляр, і надає глобальну точку доступу до нього.
4. **Патерн Команда (Command Pattern)**: Цей патерн використовується для інкапсуляції запиту як об’єкта, дозволяючи вам параметризувати клієнтів з різними запитами, чергою або запитами та операціями. Він включає в себе інтерфейс ITransactionStrategy та його реалізації DepositCashStrategy та WithdrawCashStrategy.
5. **Патерн Частковий клас (Partial Class Pattern)**: Цей патерн використовується для розподілу одного класу на кілька файлів. Це корисно для керування великими класами. Він включає в себе клас AutomatedTellerMachine, який розподілений на кілька файлів.
6. **Патерн Шаблонний метод (Template Method Pattern)**: Цей патерн використовується в класах tocount, Transfer та withdraw. Він визначає основу операції і дозволяє підкласам змінювати деякі кроки операції без зміни її структури.
7. **Патерн Фабрика (Factory Method Pattern)**: Цей патерн використовується в класі Bank для створення нового екземпляра AutomatedTellerMachine. Він визначає інтерфейс для створення об’єкта, але дозволяє підкласам змінити тип створюваного об’єкта.
