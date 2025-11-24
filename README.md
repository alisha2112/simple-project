# simple-project)

Цей проєкт — це навчальна бібліотека утиліт, розроблена в рамках
Лабораторної роботи №2. Основна мета проєкту — демонстрація налаштування
професійного середовища розробки на Node.js та TypeScript, включаючи роботу
з `package.json`, конфігурацію лінтерів (ESLint), форматерів (Prettier),
Git-хуків (Husky) та впровадження семантичного версіонування (SemVer).

Бібліотека містить набір типізованих функцій для роботи з числами, рядками
та масивами, а також клас для логування, налаштований через змінні оточення.

## Інструкції з запуску

Встановлення залежностей:

```bash
npm install
```

Запуск демонстраційного сценарію (виконує код з src/demo.ts):

```bash
npm run demo
```

Збірка проєкту (генерує файли у папку dist/):

```bash
npm run build
```

Перевірка якості коду (типи, лінтер, форматування):

```bash
npm run typecheck
npm run lint
npm run format:check
```

## Огляд кроків еволюції

Розвиток проєкту відбувався поетапно з фіксацією версій згідно з SemVer :

- v0.1.0 - реалізовано базові функції add та capitalize з використанням типу any.
- v0.2.0 - any замінено на конкретні типи (number, string). Функціонал без змін.
- v0.3.0 - додано функцію formatNumber з використанням Type Alias для опцій.
- v0.4.0 - додано інтерфейс User та універсальну (generic) функцію groupBy.
- v0.5.0 - додано клас Logger, валідацію змінних оточення через zod та конфігураційний файл.
- v1.0.0 - стабілізація API. Заборонено any в ESLint, налаштовано exports у package.json.
- v2.0.0 (Breaking Change) - змінено сигнатуру функції add: тепер вона приймає масив чисел (number[]) замість двох аргументів.

## Приклади використання

1. add - обчислює суму чисел у масиві

```bash
import { add } from './index';
// Увага: у v2.0.0 приймає масив!
console.log(add([1, 2, 3])); // Результат: 6
```

2. capitalize - робить першу літеру рядка великою

```bash
import { capitalize } from './index';
console.log(capitalize('hello')); // Результат: "Hello"
```

3. formatNumber - форматує число з заданою точністю (точність за замовчуванням береться з .env)

```bash
import { formatNumber } from './index';
console.log(formatNumber(123.456, { precision: 2 })); // Результат: "123.46"
```

4. groupBy - групує масив об'єктів за вказаним ключем

```bash
import { groupBy, type User } from './index';

const users: User[] = [
  { id: 1, name: 'Alice' },
  { id: 2, name: 'Bob' },
  { id: 3, name: 'Alice' }
];

console.log(groupBy(users, 'name'));
// Результат: { 'Alice': [{...}, {...}], 'Bob': [{...}] }
```

5. Logger - клас для логування повідомлень залежно від налаштувань конфігурації

```bash
import { Logger } from './index';
// Рівень логування 'info', 'debug' або 'silent'
const logger = new Logger('info');
logger.info('System online');
```

## Конфігурація (.env)

Для налаштування параметрів бібліотеки створіть файл .env у корені проєкту.
Валідація здійснюється через бібліотеку zod.

| Ключ          | Тип            | Опис                                   | Дефолтне значення |
| ------------- | -------------- | -------------------------------------- | ----------------- |
| APP_PRECISION | integer (0-10) | Точність округлення для formatNumber   | 2                 |
| LOG_LEVEL     | string         | Рівень логування (silent, info, debug) | 'info'            |

Приклад .env:

```bash
APP_PRECISION=3
LOG_LEVEL=debug
```

## Посилання на релізи

0.1.0 - https://github.com/alisha2112/simple-project/tree/v0.1.0  
0.2.0 - https://github.com/alisha2112/simple-project/tree/v0.2.0  
0.3.0 - https://github.com/alisha2112/simple-project/tree/v0.3.0  
0.4.0 - https://github.com/alisha2112/simple-project/tree/v0.4.0  
0.5.0 - https://github.com/alisha2112/simple-project/tree/v0.5.0  
1.0.0 - https://github.com/alisha2112/simple-project/tree/v1.0.0  
2.0.0 - https://github.com/alisha2112/simple-project/tree/v2.0.0

## Скріншоти перевірок

### Крок 2:

![stage 2](images/stage_2_1.png)
![stage 2](images/stage_2_2.png)
![stage 2](images/stage_2_3.png)
![stage 2](images/stage_2_4.png)
![stage 2](images/stage_2_5.png)
![stage 2](images/stage_2_6.png)

### Крок 3:

![stage 3](images/stage_3_1.png)
![stage 3](images/stage_3_2.png)
![stage 3](images/stage_3_3.png)
![stage 3](images/stage_3_4.png)
![stage 3](images/stage_3_5.png)

### Крок 4:

![stage 4](images/stage_4_1.png)
![stage 4](images/stage_4_2.png)
![stage 4](images/stage_4_3.png)
![stage 4](images/stage_4_4.png)
![stage 4](images/stage_4_5.png)

### Крок 5:

![stage 5](images/stage_5_1.png)
![stage 5](images/stage_5_2.png)
![stage 5](images/stage_5_3.png)
![stage 5](images/stage_5_4.png)
![stage 5](images/stage_5_5.png)

### Крок 6:

![stage 6](images/stage_6_1.png)
![stage 6](images/stage_6_2.png)
![stage 6](images/stage_6_3.png)
![stage 6](images/stage_6_4.png)
![stage 6](images/stage_6_5.png)
![stage 6](images/stage_6_6.png)
![stage 6](images/stage_6_7.png)
![stage 6](images/stage_6_8.png)

### Крок 7:

![stage 7](images/stage_7_1.png)
![stage 7](images/stage_7_2.png)
![stage 7](images/stage_7_3.png)

### Крок 8:

![stage 8](images/stage_8_1.png)
![stage_8](images/stage_8_2.png)
![stage 8](images/stage_8_3.png)
![stage 8](images/stage_8_4.png)
![stage 8](images/stage_8_5.png)
