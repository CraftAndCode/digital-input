# Цифровой ввод
```package
core
radio
microphone
proportionalFont=github:lwchkg/pxt-proportional-font
```

```template
basic.forever(function () {
})
```
```blocks

```
## Step 0 @showDialog
Привет! Сегодня мы узнаем, что такое электрические цепи и научимся считывать электрический сигнал с контактов Micro:bit.

## Step 1 @showDialog
### Электрические цепи
Электрической цепью называется несколько соединённых между собой устройств, по которым протекает электрический ток. Для того, чтобы цепь работала, она должна включать в себя источник питания (батарею, аккумулятор, или, в нашем случае, Micro:bit).
  
Простую электрическую цепь из источника питания и светодиода мы собирали [ранее](https://makecode.microbit.org/#tutorial:github:craftandcode/flashing-leds/ru). Как мы уже знаем, мы можем включать и выключать электрические цепи, соединённые с контактами Micro:bit с помощью блока ``||pins.цифровой: записать контакт||``.

```block
pins.digitalWritePin(DigitalPin.P0, 0)
```
## Step 2 @showDialog
### Цифровой ввод
Когда мы используем блок ``||pins.цифровой: записать контакт||``, указанный контакт работает в режиме ``цифрового вывода``, то есть выводит на подключенную электрическую цепь электрический сигнал.

Существует обратный режим, в котором контакты Micro:bit используются как датчики электрического сигнала и считывают, есть ли в цепи электрический ток. Этот режим называется режимом ``цифрового ввода``.

## Step 3 @showHint
### Считываем электрический сигнал
Для считывания электрического сигнала используют блок ``||pins.цифровой: читать контакт||``. При выполнении программы этот блок принимает значение ``1``, если сигнал есть и ``0``, если сигнала нет.
  
Найди этот блок во вкладке ``||pins.контакты||``.
```hint
Вот так можно вывести значение контакта 0 на экран:
```
```block
    basic.showNumber(pins.digitalReadPin(DigitalPin.P0))
```

## Step 4 @showHint
### Считываем электрический сигнал
Давай проверим всё, что узнали, на практике! Собери программу по образцу и загрузи в Micro:bit. Что ты видишь на экране? О чём это говорит?
```blocks
basic.forever(function () {
    basic.showNumber(pins.digitalReadPin(DigitalPin.P0))
})
```

## Step 7 @showHint
### Считываем электрический сигнал
Теперь, соедини проводами контакты ``0`` и ``3V``. Изменилось ли что-нибудь? Что это означает?
```hint
Твоя электрическая цепь будет выглядеть так:
```
![](https://github.com/CraftAndCode/team-sports/blob/master/image.png?raw=true)

## Step 8 @showHint
### Сигнализация
Теперь мы знаем, когда на контакте Micro:bit есть электрический сигнал, и когда он прерывается. Давай воспользуемся этим, чтобы запрограммировать простую сигнализацию!
  
При размыкании контактов ``0`` и ``3V`` включается сирена. Можно придумать способ, при котором цепь размыкается, когда открывается дверь.

```blocks
basic.forever(function () {
    if (pins.digitalReadPin(DigitalPin.P0) == 0) {
        music.playMelody("C C C5 C5 C C C5 C5 ", 120)
    } else {
        music.stopAllSounds()
    }
})

```
## Step 9 @showHint
### Теперь твой черёд!
Мы приготовили для тебя задание. Напиши программу, которая покажет на экране значок молнии, если на контакте ``1`` появится электрический сигнал.

Так же, ты можешь написать усложнённую версию программы, которая будет показывать на экране, какие из трёх контактов подключены.
```hint
```
![](https://github.com/CraftAndCode/team-sports/blob/master/GifLightning.gif?raw=true)
## Answers @showDialog
### Ответы: Задание
```blocks
basic.forever(function () {
    if (pins.digitalReadPin(DigitalPin.P1) == 1) {
        basic.showLeds(`
            . . # . .
            . # . . .
            # # # # .
            . . # . .
            . # . . .
            `)
    } else {
        basic.clearScreen()
    }
})
```
### Ответы: Усложнённое задание
```blocks
basic.forever(function () {
    if (pins.digitalReadPin(DigitalPin.P0) == 1) {
        basic.showNumber(0)
        basic.pause(500)
    } else {
        basic.clearScreen()
    }
    if (pins.digitalReadPin(DigitalPin.P1) == 1) {
        basic.showNumber(1)
        basic.pause(500)
    } else {
        basic.clearScreen()
    }
    if (pins.digitalReadPin(DigitalPin.P2) == 1) {
        basic.showNumber(2)
        basic.pause(500)
    } else {
        basic.clearScreen()
    }
})
```

## Step 10
Все задания завершены! Теперь ты знаешь, как использовать цифровой ввод для считывания электрических сигналов.