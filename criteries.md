# Критерии

## Базовые

### Задача

**Б1. Код соответствует техническому заданию проекта.**

Все обязательные пункты технического задания выполнены.

**Б2. При выполнении кода не возникает необработанных ошибок.**

При открытии диалогов, загрузки данных и работе с сайтом не возникает ошибок, программа не ломается и не зависает.

### Именование

**Б3. Названия переменных, параметров, свойств и методов начинаются со строчной буквы и записываются в нотации camelCase.**

Исключение составляют перечисления, они записываются в нотации PascalCase.

**Б4. В качестве имён переменных и свойств используются английские существительные.**

Сокращения в словах запрещены. Сокращённые названия переменных можно использовать, только если такое название широко распространено. Допустимые сокращения:

* xhr, для объектов XMLHttpRequest;
* evt для объектов Event и его производных (MouseEvent, KeyboardEvent и подобные);
* ctx для контекста канваса;
* i, j, k, l, для счётчика в цикле, j для счётчика во вложенном цикле и так далее по алфавиту;
* если циклов два и более, то можно не переиспользовать переменную i;
* cb для единственного колбэка в параметрах функции;
* img для именования переменной, содержащей ссылку на тег <img>;
* src для именования переменной, хранящей адрес, например изображения;
* err для обозначения объекта ошибок в конструкциях try...catch или колбэках.

Допустимо именовать переменные-предикаты — флаги или функции, которые возвращают булево значение — по схеме «is + признак». Например:

```
const loading = true; // правильно
const isLoading = true; // тоже правильно

function checkValueToNull(value) { // правильно
  return value === null;
}

function isNull(value) { // тоже правильно
  return value === null;
}
```

**Б5. Массивы названы существительными во множественном числе.**

**Неправильно:**

```
const age = [12, 40, 22, 7];
const name = ['Иван', 'Петр', 'Мария', 'Алексей'];

const wizard = {
  name: 'Гендальф',
  friend: ['Саурон', 'Фродо', 'Бильбо']
};
```

**Правильно:**

```
const ages = [12, 40, 22, 7];
const names = ['Иван', 'Петр', 'Мария', 'Алексей'];

const wizard = {
  name: 'Гендальф',
  friends: ['Саурон', 'Фродо', 'Бильбо']
};
```

**Обратите внимание**, что слово data — это множественное число от слова datum, поэтому его использование в качестве имени переменной для массива корректно.

**Б6. Название функции или метода содержит глагол.**

Название функции или метода должно быть глаголом и соответствовать действию, которое выполняет функция или метод. Например, можно использовать глагол get для функций и методов, которые что-то возвращают.

Исключения:

* Функции конструкторы.
* Функции обработчики или колбэки.

**Неправильно:**

```
const action = function (names) {
  names.forEach((name) => {
    console.log(name);
  });
};

const wizard = {
  name: 'Гендальф',
  action() {
    console.log('Стреляю файрболлом!');
  }
};

const randomNumber = () => Math.random();
```

**Правильно:**

```
const printNames = function (names) {
  names.forEach((name) => {
    console.log(name);
  });
};

const wizard = {
  name: 'Гендальф',
  shoot() {
    console.log('Стреляю файрболлом!');
  }
};

const getRandomNumber = () => Math.random();
```

**Б7. Названия констант (постоянных значений, известных до начала выполнения программы) написаны прописными (заглавными) буквами.**

Слова разделяются подчёркиваниями (UPPER_SNAKE_CASE), например:

```
const MAX_HEIGHT = 400;
const EARTH_RADIUS = 6370;
```

**Б8. Название классов, конструкторов и перечислений начинается с заглавной буквы. В названии используются английские существительные. Значения перечислений объявлены как константы.**

**Неправильно:**

```
// Функция-конструктор
const wizard = function (name, age) {
  this.name = name;
  this.age = age;
};

// Функция
const Fly = function (coordinate) {
  console.log(`Смотрите, я лечу вон туда ${coordinate}!`);
};

// Перечисление
const statusCodes = {
  ok: 200,
  notFound: 404,
  badRequest: 400,
};

// Перечисление
const STATUS_CODE = {
  Ok: 200,
  NotFound: 404,
  BadRequest: 400,
};
```

**Правильно:**

```
// Функция-конструктор
const Wizard = function (name, age) {
  this.name = name;
  this.age = age;
};

// Функция
const fly = function (coordinate) {
  console.log(`Смотрите, я лечу вон туда ${coordinate}!`);
};

// Перечисление
const StatusCode = {
  OK: 200,
  NOT_FOUND: 404,
  BAD_REQUEST: 400,
};
```

Названия функций, не являющихся конструкторами, должны начинаться со строчной буквы.

**Обратите внимание**, что не все объекты в коде проекта должны быть перечислениями. Например, допускается использование объектов в качестве словарей:

```
const priceTypeToRange = {
  low: 'до 200 ₽',
  medium: 'от 200 ₽ до 500 ₽',
  high: 'от 500 ₽',
};
```

### Форматирование и внешний вид.

**Б10. Список констант идёт перед основным кодом.**

Все константы выносятся в начало модуля. Перечисления, как набор констант, также выносятся.

**Б11. Код соответствует стилю оформления, принятому на проекте.**

Не возникает ошибок при проверке проекта ESLint.

### Мусор

**Б12. В итоговом коде проекта находятся только те файлы, которые были на момент создания репозитория, которые были получены в патчах, и файлы, созданные по заданию.**

В коде проекта нет файлов, модулей и частей кода, которые не используются, включая закомментированные участки кода.

**Б13. Версии используемых зависимостей зафиксированы в package.json.**

В списках зависимостей в файле package.json указаны точные версии используемых пакетов. Версия обязательно должна быть указана. Не допускается использование ^, * и ~.

### Модульность

**Б19. Все файлы JS представляют собой отдельные модули ES2015, а название модуля соответствует его содержимому и записано строчными (маленькими) буквами, слова разделены дефисами.**

Экспорт и импорт значений производится при помощи ключевых слов export и import. Сохранение в глобальную область видимости значений не допускается.

Разные логические части кода вынесены в отдельные файлы модулей. Имя файла модуля должно соответствовать его содержимому. Для того, чтобы избежать конфликтов имён в разных операционных системах, лучше применять наименее конфликтный способ именования файлов — строчными (маленькими) буквами через дефис. Например, если модуль называется GameView, то имя файла модуля должно быть game-view.js.

**Б20. Модули не экспортируют изменяющиеся переменные.**

Модуль не должен экспортировать переменную, значение которой может измениться в будущем.

**Неправильно:**

```
export let latestResult;
```

**Правильно:**

```
export const latestResult = loadLatestResult();
```

### Универсальность

**Б21. Код является кроссбраузерным и не вызывает ошибок в разных браузерах и разных операционных системах.**

При проверке этого критерия, необходимо удостовериться в правильной работе и отсутствии сообщений об ошибках в выполняемых скриптах только в последних версиях браузеров: Chrome, Firefox, Safari, Microsoft Edge (на движке Blink).

**Обратите внимание**, в Safari может не отображаться балун, реализованный с помощью Leaflet. Это не является ошибкой.

**Важно:** на Windows и Linux тестировать в Safari не нужно.

### Оптимальность

**Б23. Своевременный выход из цикла: цикл не работает дольше чем нужно.**

**Неправильно:**

```
apartments.forEach((apartment, index) => {
  if (index < 3) {
    render(apartment);
  }
});
```

**Правильно:**

```
for (let i = 0; i < Math.min(apartments.length, 3); i++) {
  render(apartments[i]);
}
```

### Безопасность

**Б26. Обработчики событий документа (document) добавляются и удаляются своевременно.**

**Защита от memory-leak.** Количество обработчиков, подвешенных на глобальную область видимости, не должно возрастать. Например, если подвешивается обработчик, который следит за перемещением курсора по экрану, то он должен добавляться и удаляться в нужный момент. Случай, когда обработчик на document только добавляется, может свидетельствовать о проблеме бесконечного создания обработчиков и потенциальной утечке памяти.

**Защита от неправильного поведения интерфейса.** Например, на странице может существовать попап, который скрывается по нажатию клавиши ESC. Лучше для него удалять обработчик события нажатия на клавишу, если он не показан, потому что он может каким-то образом ломать поведение сайта: останавливать распространение, отменять поведение по умолчанию и так далее.

**Б27. Для вставки пользовательских строк (имён, фамилий и так далее) использован textContent.**

Защита от XSS-атак, а также изменения исходных данных, запутывание пользователя и прочее.

**Неправильно:** через innerHTML вставляются данные, которые невозможно полностью контролировать. Это может быть пользовательский ввод, который может содержать XSS.

```
const listItem = listItemTemplate.cloneNode(true);
listItem.querySelector('.title').innerHTML = user.fullName;
```

**Правильно:** через innerHTML вставляется код, который был создан программистом, поэтому сделать его вредоносным невозможно. innerHTML используется для лаконичного создания сложной разметки, но при этом в разметку не вставляются никакие внешние данные.

```
const listItemTemplate = '<li class="amenity"><i></i><a href="#"></a></li>';
list.innerHTML = listItemTemplate;
```

## Дополнительные

### Именование

**Д2. Переменные носят абстрактные названия и не содержат имён собственных.**

**Неправильно:**

```
const keks = {
  name: 'Кекс'
};
```

**Правильно:**

```
const cat = {
  name: 'Кекс'
};
```

**Д3. Название методов и свойств объектов не содержит название объектов.**

**Неправильно:**

```
const popup = {
  openPopup() {
    console.log('I will open popup');
  }
};

const wizard = {
  wizardName: 'Пендальф'
};
```

**Правильно:**

```
const popup = {
  open() {
    console.log('I will open popup');
  }
};

const wizard = {
  name: 'Пендальф'
};
};
```

**Д4. Именованные функции-обработчики событий названы в соответствии с правилами именования обработчиков.**

Для единственного обработчика или функции можно использовать callback или cb. Для именования нескольких обработчиков внутри одного модуля используется on или handler и описание события. Название обработчика строится следующим образом:

* on + (на каком элементе) + что случилось:

```
const onSidebarClick;
const onContentLoad;
const onWindowResize;
```

* (на каком элементе) + что случилось + Handler:

```
const sidebarClickHandler;
const contentLoadHandler;
const windowResizeHandler;
```

## Единообразие

**Д5. Все функции объявлены единообразно.**

При объявлении функций используются стрелочные функции. Для объявления методов объектов используется специальный синтаксис для методов.

Функция:

```
const getTheMeaningOfLive = () => {
  const result = 42;
  return result;
};
```

Метод:

```
const God = {
  createWorld() {
    return `Your world is ready!`;
  }
};
```

Конструктор:

```
class Planet {
  constructor(weight, mass) {
    this.weight = weight;
    this.mass = mass;
  }
}
```

Объявление функций как «функциональное выражение» либо как «функциональное объявление» допускается в случаях, когда нужно использовать контекст функции или поднятие (hoisting). Смешение этих двух стилей в рамках проекта не допускается: если нужен и контекст, и поднятие — используйте «функциональное объявление».

**Неправильно**, стили смешаны:

```
const doRegularThigns = () => {/* Рядовая функция */};

function doSomething () {/* Для поднятия и работы с this */}

const doSomethingElse = function () {/* Для работы с this */};
```

**Правильно**, для this используется только «функциональное выражение»:

```
const doRegularThigns = () => {/* Рядовая функция */};

const doSomething = function () {/* Для работы с this */};

const doSomethingElse = function () {/* Для работы с this */};
```

**Тоже правильно**, для this и поднятия используется только «функциональное объявление»:

```
const doRegularThigns = () => {/* Рядовая функция */};

function doSomething () {/* Для поднятия и работы с this */}

function doSomethingElse () {/* Для поднятия и работы с this */}
```

**Д6. Используется единый стиль именования переменных.**

Стиль именования переменных сохраняется во всех модулях, например:
не следует мешать обработчики содержащие Handler и on;
если переменные, которые хранят DOM-элемент, содержат слово Element или любое другое, но одно и то же везде.

**Неправильно:**

```
const popupMainElement = document.querySelector('.popup');
const sidebarNode = document.querySelector('.sidebar');
const similarContainer = popupMainElement.querySelector('ul.similar');
```

**Правильно:**

```
const popupMainElement = document.querySelector('.popup');
const sidebarElement = document.querySelector('.sidebar');
const similarContainerElement = popupMainElement.querySelector('ul.similar');
```

**Тоже правильно:**

```
const popupMainNode = document.querySelector('.popup');
const sidebarNode = document.querySelector('.sidebar');
const similarContainerNode = popupMainNode.querySelector('ul.similar');
```

## Корректность

**Д8. API встроенных функций и объектов используется правильно.**

Передаются корректные значения, которые ожидаются по спецификации.

**Неправильно:**

```
const isPressed = element.getAttribute('aria-pressed', false);
```

**Правильно:**

```
const isPressed = element.getAttribute('aria-pressed');
```

Потому что getAttribute принимает только один аргумент, два аргумента принимает метод setAttribute.

Встроенные методы массивов используются по назначению.

**Неправильно:**

```
let greeting = 'Привет';

wizards.map((wizard) => {
  greeting += `, ${wizard.name}`;
});

console.log(`${greeting}!`);
```

**Правильно:**

```
let greeting = 'Привет';

const names = wizards.map((wizard) => wizard.name);

console.log(`${greeting} ${names.join(', ')}!`);
```

## Избыточность

**Д13. В проекте не должно быть избыточных проверок.**

Например, если заранее известно, что функция всегда принимает числовой параметр, то не следует проверять его на существование.

**Неправильно:**

```
const isPositiveNumber = (myNumber) => {
  if (typeof myNumber === 'undefined') {
    throw new Error('Parameter is not defined');
  }

  return myNumber > 0;
};

isPositiveNumber(15);
isPositiveNumber(-30);
```

**Правильно:**

```
const isPositiveNumber = (myNumber) => myNumber > 0;

isPositiveNumber(15);
isPositiveNumber(-30);
```

**Д14. Отсутствует дублирование кода: повторяющиеся части кода переписаны как функции.**

При написании кода следует придерживаться принципа DRY.

**Д16. Отсутствуют лишние приведения и проверки типов.**

Если заранее известно, что в переменной число, то нет смысла превращать переменную в число parseInt(myNumber). Тоже касается и избыточной проверки булевой переменной.

**Неправильно:**

```
if (booleanValue === true) {
  console.log('It\'s true!');
}
```

**Правильно:**

```
if (booleanValue) {
  console.log('It\'s true!');
}
```

**Д18. Условия упрощены.**

Если функция возвращает булево значение, не используется if..else с лишними return.

**Неправильно:**

```
const isEqual = (firstValue, secondValue) => {
  if (firstValue === secondValue) {
    return true;
  } else {
    return false;
  }
};
```

**Правильно:**

```
const isEqual = (firstValue, secondValue) => firstValue === secondValue;
```

Там, где возможно, в присвоении значения вместо if используется тернарный оператор.

**Неправильно:**

```
let sex;
if (male) {
  sex = 'Мужчина';
} else {
  sex = 'Женщина';
}
```

**Правильно:**

```
const sex = male ? 'Мужчина' : 'Женщина';
```

Если при использовании условного оператора в любом случае возвращается значение, альтернативная ветка опускается

**Неправильно:**

```
const decide = (value, anotherValue) => {
  if (2 > 1) {
    return value;
  } else {
    // Много кода...
    return anotherValue;
  }
};
```

**Правильно:**

```
const decide = (value, anotherValue) => {
  if (2 > 1) {
    return value;
  }

  // Много кода...

  return anotherValue;
};
```

## Магия

**Д19. В коде не используются «магические значения», под каждое из них заведена отдельная переменная, названная как константа.**

**Неправильно:**

```
setTimeout(doIt, 1000);
```

**Правильно:**

```
// Определим константу
const TIMEOUT = 1000;
setTimeout(doIt, TIMEOUT);
```

## Оптимальность

**Д21. Поиск элементов по селекторам делается минимальное количество раз, после этого ссылки на элементы сохраняются.**

**Неправильно:**

```
for (let i = 0; i < Math.min(apartments.length, 3); i++) {
  const dialog = document.querySelector('.dialog');
  render(dialog, apartments[i]);
}
```

**Правильно:**

```
const dialog = document.querySelector('.dialog');

for (let i = 0; i < Math.min(apartments.length, 3); i++) {
  render(dialog, apartments[i]);
}
```

**Д23. Изменения применяются точечно.**

Например, при удалении классов с DOM-элемента, не производится попытка удалить все возможные классы, если можно убрать лишь тот, который действительно установлен на DOM-элементе в данный момент.

**Неправильно:**

```
const imageContainer = document.querySelector('.image-container');

const changeFilter = (filterName) => {
  imageContainer.classList.remove('filter-chrome', 'filter-sepia', 'filter-marvin', 'filter-phobos', 'filter-heat');
  imageContainer.classList.add(filterName);
};
```

**Правильно:**

```
const imageContainer = document.querySelector('.image-container');

let currentFilter;
const changeFilter = (filterName) => {
  if (currentFilter) {
    imageContainer.classList.remove(currentFilter);
  }
  imageContainer.classList.add(filterName);
  currentFilter = filterName;
};
```

## Сложность. Читаемость.

**Д24. Для каждого события используется отдельный обработчик.**

Одна функция не является обработчиком нескольких разных событий.

**Неправильно:**

```
const activationHandler = (evt) => {
  if (evt.key === 'Enter' || evt.type === 'click') {
    showPopup();
  }
};

button.addEventListener('click', activationHandler);
button.addEventListener('keydown', activationHandler);
```

**Правильно:**

```
const buttonClickHandler = () => showPopup();

const buttonKeydownHandler = (evt) => {
  if (evt.key === 'Enter') {
    showPopup();
  }
};

button.addEventListener('click', buttonClickHandler);
button.addEventListener('keydown', buttonKeydownHandler);
```

**Д25. Длинные функции и методы разбиты на несколько небольших.**

**Д26. Для работы с JS-коллекциями используются итераторы для массивов.**

Итераторы используются для трансформаций массивов — map, filter, sort и прочие. А также для обхода проблемы потери окружения в циклах — forEach.

Например:

```
elements.forEach((element) => {
  element.addEventListener('click', () => {
    console.log(element);
  });
});
```

**Д27. Оператор присваивания не используется как часть выражения.**

**Неправильно:**

```
imgGenerate(picArray = JSON.parse(data));
```

**Правильно:**

```
picArray = JSON.parse(data);
imgGenerate(picArray);
```

**Обратите внимание**, критерий не запрещает использовать параметры по умолчанию.

**Д28. Отсутствует дублирование обработчиков событий**

Если элемент интерфейса скрывается на время, при его появлении обработчики повторно не добавляются. При скрытии элемента удалять внутренние обработчики событий не нужно.
