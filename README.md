# Gerombo-Eq
Модуль эквалайзера для Android Studio

##### Содержание  
[ВВЕДЕНИЕ](#headers)  
[Варианты использования приложения](#emphasis)  
[Если вы разработчик](#dev)   
[Если вы пользователь](#user)  

<a name="headers"><h2>ВВЕДЕНИЕ</h2></a>
<p>Актуальность темы: Современные многофункциональные смартфоны уверенно вошли в наш быт. Это уже давно не просто телефон или устройство для общения – умные телефоны играют роль органайзера, фотокамеры, навигатора, мультимедийного развлекательного центра и т.д. Практически все пользователи используют смартфоны для прослушивания музыки. Это очень удобно – не нужно иметь при себе дополнительного гаджета, даже такого маленького как современный MP3 плеер. Просто подключив наушники и запустив соответствующее приложение, можно наслаждаться любимыми мелодиями со своего плейлиста, сохраненного в памяти устройства, или на облачном сервисе.

С помощью каких программных методов, а именно «Эквалайзер», можно повысить качество воспроизведения музыкальных файлов. Дело в том, что чаще всего для прослушивания музыки с помощью смартфона мы пользуемся наушниками. Значит, качество динамиков бывает разное в зависимости от модели наушников. Все остальное зависит от процессора устройства и используемых приложений. Для получения качественного звука нам потребуется эквалайзер, его задача исправить искажения динамиков и привести звук к эталонному состоянию или к состоянию более приятному для прослушивания отдельно взятому человеку (например, некоторым нравится большая громкость баса). Эквалайзер может быть как отдельное приложение или как модуль встроенный в аудио проигрыватель. В курсовом проекте будет рассмотрен процесс разработки модуля эквалайзера для встраивания в аудио приложения.</p>


<a name="emphasis"><h2>Варианты использования приложения</h2></a>

После запуска приложения будет открыто окно, содержащее тестовый аудиоплеер с возможностью выбора файла и паузы, также будет присутствовать кнопка для открытия модуля эквалайзера.  В верхней части экрана находится меню с пунктами: 

*	Import EQ settings – открывает диалоговое окно в котором надо выбрать импортируемый файл настроек. 
*	Export EQ settings – сохраняет настройки эквалайзера в память телефона по пути: /storage/emulated/0/GeromboEQ. 
*	Save EQ – открывает окно в котором предлагается пользователю сохранить текущие настройки в пользовательский пресет. 
*	Clear EQ – отчищает пользовательский пресет и обнуляет все полосы эквалайзера. 
*	About – открывает окно справки. область меню и рабочую область программы с расписанием.

В центре экрана расположены слайдеры для настройки уровня громкости на разных частотах, два всплывающих меню: меню с пользовательскими пресетами и меню со стандартными пресетами (Normal, Classical, Dance, Flat, Folk, Heavy Metal, Hip Hop, Jazz, Pop, Rock). Ниже располагается два аналоговых контроллера для управления громкостью басов и управления реверберацией.





<a name="dev"><h2>Если вы разработчик</h2></a>

Вам достаточно скачать папку с модулем Gerombo Eq, она называется "equalizer" и поместить в корень своего проекта.
После чего вам надо добачить зивисмость в Gradle:

```no-highlight
    implementation project(':equalizer')
```
Далее вам потребуется прописать 3 строчки в файл «MainActivity», после инициализации аудиопроигрывателя:

```no-highlight
    // EQ INIT start
        eqAudioSession = getAudioSessionId()    
        // Передача аудиосессии    
        SharedPrefEq.init(applicationContext)   
        // Инициализация модуля SharedPrefEq   
        loadEqualizerSettings()    
        // load Preferences
    // EQ INIT end
```
Для открытия окна модуля, можно написать обработчик кнопки события «OnClick»:

```no-highlight
    binding.buttonToEq.setOnClickListener {
        val intent = Intent(context, Eq::class.java);
        startActivity(intent);
    }
```
После чего ваш модулю экавалайзера подключен к приложению и готов работать.

<a name="user"><h2>Если вы пользователь</h2></a>
