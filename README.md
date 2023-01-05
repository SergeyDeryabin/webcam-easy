
# Webcam Easy JS
[English Version](README_EN.md) | Русская версия

Это - javascript-библиотека для доступа к потоку веб-камеры и для съемки фотографий.

Вы можете легко добавить ее в виде модуля к вашему собственному приложению.

- Потоковая передача из веб-камеры на экран ПЭВМ или мобильного устройства
- Переключение:
    - передняя камера/камера обращенная на пользователя('user')
     или
     - задняя камера/камера обращенная от пользователя(окружение; 'enviroment')
- Сделать фотографию и загрузить ее в каталог/папку "Загрузки" на ПЭВМ или на мобильном устройстве.

## Живой демонстрационный пример
**[https://bensonruan.com/how-to-access-webcam-and-take-photo-with-javascript/](https://bensonruan.com/how-to-access-webcam-and-take-photo-with-javascript/)**

![webcam-easy-demo](https://bensonruan.com/wp-content/uploads/2020/04/webcam-easy-demo-ok.gif)

## Установка

#### Используйте клонирование через утилиту Git
``` shell
git https://github.com/bensonruan/webcam-easy.git
```

#### ИЛИ используйте менеджер пакетов NPM
[![NPM](https://nodei.co/npm/webcam-easy.png?compact=true)](https://nodei.co/npm/webcam-easy/)
``` в командной строке shell
npm install webcam-easy
```

## Использование

#### 1. Включайте тег скрипта в html в тег <head>.
```html
<script type="text/javascript" src="https://unpkg.com/webcam-easy/dist/webcam-easy.min.js"></script>
```
    или импортируйте в javascript-коде 
``` js
import Webcam from 'webcam-easy';
```


#### 2. Поместите элементы в HTML-файле
```html
<video id="webcam" autoplay playsinline width="640" height="480"></video>
<canvas id="canvas" class="d-none"></canvas>
<audio id="snapSound" src="audio/snap.wav" preload = "auto"></audio>
```

#### 3. Вызовите конструктор в javascript-коде
``` js
const webcamElement = document.getElementById('webcam');
const canvasElement = document.getElementById('canvas');
const snapSoundElement = document.getElementById('snapSound');
const webcam = new Webcam(webcamElement, 'user', canvasElement, snapSoundElement);
```

#### 4. Запуск камеры Webcam 
``` js
webcam.start()
   .then(result =>{
      console.log("webcam started");
   })
   .catch(err => {
       console.log(err);
   });
```

#### 5. Сделать фото
``` js
var picture = webcam.snap();
``` 

#### 6. Остановить камеру Webcam 
``` js
webcam.stop();
```

## Функции
- start(startStream) : начать передачу потока из веб-камеры 
  - получить разрешение от пользователя
  - получить всю информацию об устройствах ввода видео
  - выберить камеру на основе facingMode(режим обзора из камеры(Facing) 'user'(передняя камера/камера обращенная на пользователя) или 'enviroment'(задняя камера/камера обращенная от пользователя))
  - запустить поток(stream)
  
  startStream - дополнительный параметр, значение по умолчанию - истина true
      
- stop() : прекратить передачу потока из веб-камеры webcam
  
- stream() : начать передачу потока из веб-камеры к видео элементу 
  
- snap() : сделайте фотографию из веб-камеры
  
- flip() : изменить режим обзора(Facing) и выбранную камеру

## Свойства

- facingMode : режим обзора из камеры(Facing) 'user'(передняя камера/камера обращенная на пользователя) или 'enviroment'(задняя камера/камера обращенная от пользователя)
- webcamList : все доступные камеры на устройстве
- webcamCount : число доступных камер на устройстве 
