# Взаимодействие: alert, prompt, confirm

В этой части учебника мы разбираем "собственно JavaScript", без привязки к браузеру или другой среде выполнения.

Но, так как мы будем использовать браузер как демо-среду, нам нужно познакомиться по крайней мере с несколькими функциями его интерфейса, а именно: `alert`, `prompt` и `confirm`.


## alert

Синтаксис:

```js
alert(message);
```

Этот код отобразит окно в браузере и приостановит дальнейшее выполнение скриптов, до тех пор пока пользователь не нажмёт кнопку "OK".

Например:

```js run
alert("Hello");
```

Это небольшое окно с сообщением называется *модальным окном*. Понятие *модальный* означает, что пользователь не может взаимодействовать с интерфейсом остальной части страницы, нажимать на другие кнопки и т.д. до тех пор, пока взаимодействует с окном. В данном случае -- пока не будет нажата кнопка "OK".

## prompt

Функция `prompt` принимает два аргумента:

```js no-beautify
result = prompt(title, [default]);
```

Этот код отобразит модальное окно с текстом, полем для ввода текста и кнопками OK/Отмена.

`title`
: Текст для отображения в окне.

`default`
: Необязательный второй параметр, который устанавливает начальное значение в поле для текста в окне.

Пользователь может напечатать что-либо в поле ввода и нажать OK. Или отменить ввод нажатием на кнопку "Отмена" или нажав клавишу `key:Esc`.

Вызов `prompt` вернёт текст, указанный в поле для ввода, или `null` если ввод отменён пользователем.

Например:

```js run
let age = prompt('Сколько тебе лет?', 100);

alert(`Тебе ${age} лет!`); // Тебе 100 лет!
```

````warn header="Для IE: всегда устанавливайте значение по умолчанию"
Второй параметр не обязательный, но если не указать его, то Internet Explorer установить значение `"undefined"` в поле для ввода.

Запустите код в Internet Explorer и посмотрите на результат:

```js run
let test = prompt("Test");
```

Чтобы `prompt` хорошо выглядел в IE, рекомендуется всегда указывать второй параметр:

```js run
let test = prompt("Test", ''); // <-- для IE
```
````

## confirm

Синтаксис:

```js
result = confirm(question);
```

Функция `confirm` отображает модальное окно с текстом вопроса `question` и двумя кнопками: OK и Отмена.

Результат `true`, если нажата кнопка OK. В других случаях `false`.

Например:

```js run
let isBoss = confirm("Ты здесь главный?");

alert( isBoss ); // true если нажата OK
```

## Итого

Мы рассмотрели 3 функции браузера для взаимодействия с пользователем:

`alert`
: показывает сообщение.

`prompt`
: показывает сообщение и запрашивает ввод текста от пользователя. Возвращает напечатанный текст в поле ввода или `null`, если была нажата кнопка "Отмена" или `key:Esc` с клавиатуры.

`confirm`
: показывает сообщение и ждёт, пока пользователь нажмёт OK или Отмена. Возвращает `true`, если нажата OK и `false`, если нажата кнопка "Отмена" или `key:Esc` с клавиатуры.

Все эти методы являются модальными: останавливают выполнение скриптов и не позволяют пользователю взаимодействовать с остальной частью страницы до тех пор, пока окно не будет закрыто.

На все указанные методы распространяется два ограничения:

1. Расположение окон определяется браузером. Обычно окна находятся в центре.
2. Визуальное отображение окон зависит от браузера и мы не можем изменить их вид.

Такова цена простоты. Есть другие способы показать более приятные глазу окна с богатым функционалом для взаимодействия с пользователем, но если "навороты" не имеют значения, то данные методы работают отлично.
